Allowing cross-origin use of images and canvas
==============================================

HTML provides a [`crossorigin`](element/img#crossorigin) attribute for
images that, in combination with an appropriate
[CORS](https://developer.mozilla.org/en-US/docs/Glossary/CORS) header,
allows images defined by the [`<img>`](element/img) element that are
loaded from foreign origins to be used in a [`<canvas>`](element/canvas)
as if they had been loaded from the current origin.

See [CORS settings attributes](attributes/crossorigin) for details on
how the `crossorigin` attribute is used.

Security and tainted canvases
-----------------------------

Because the pixels in a canvas\'s bitmap can come from a variety of
sources, including images or videos retrieved from other hosts, it\'s
inevitable that security problems may arise.

As soon as you draw into a canvas any data that was loaded from another
origin without CORS approval, the canvas becomes **tainted**. A tainted
canvas is one which is no longer considered secure, and any attempts to
retrieve image data back from the canvas will cause an exception to be
thrown.

If the source of the foreign content is an HTML [`<img>`](element/img)
or SVG
[`<svg>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg)
element, attempting to retrieve the contents of the canvas isn\'t
allowed.

If the foreign content comes from an image obtained from either as
[`HTMLCanvasElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement)
or
[`ImageBitMap`](https://developer.mozilla.org/en-US/docs/Web/API/ImageBitmap),
and the image source doesn\'t meet the same origin rules, attempts to
read the canvas\'s contents are blocked.

Calling any of the following on a tainted canvas will result in an
error:

- Calling
    [`getImageData()`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData)
    on the canvas\'s context
- Calling
    [`toBlob()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/toBlob),
    [`toDataURL()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/toDataURL)
    or
    [`captureStream()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/captureStream)
    on the [`<canvas>`](element/canvas) element itself

Attempting any of these when the canvas is tainted will cause a
`SecurityError` to be thrown. This protects users from having private
data exposed by using images to pull information from remote websites
without permission.

Storing an image from a foreign origin
--------------------------------------

In this example, we wish to permit images from a foreign origin to be
retrieved and saved to local storage. Implementing this requires
configuring the server as well as writing code for the website itself.

### Web server configuration

The first thing we need is a server that\'s configured to host images
with the
[`Access-Control-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin)
header configured to permit cross-origin access to image files.

Let\'s assume we\'re serving our site using
[Apache](https://httpd.apache.org/). Consider the HTML5 Boilerplate
[Apache server configuration file for CORS
images](https://github.com/h5bp/server-configs-apache/blob/main/h5bp/cross-origin/images.conf),
shown below:

[xml]

```xml
<IfModule mod_setenvif.c>
  <IfModule mod_headers.c>
    <FilesMatch "\.(avifs?|bmp|cur|gif|ico|jpe?g|jxl|a?png|svgz?|webp)$">
      SetEnvIf Origin ":" IS_CORS
      Header set Access-Control-Allow-Origin "*" env=IS_CORS
    </FilesMatch>
  </IfModule>
</IfModule>
```

In short, this configures the server to allow graphic files (those with
the extensions \".bmp\", \".cur\", \".gif\", \".ico\", \".jpg\",
\".jpeg\", \".png\", \".svg\", \".svgz\", and \".webp\") to be accessed
cross-origin from anywhere on the internet.

### Implementing the save feature

Now that the server has been configured to allow retrieval of the images
cross-origin, we can write the code that allows the user to save them to
[local
storage](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API),
just as if they were being served from the same domain the code is
running on.

The key is to use the [`crossorigin`](element/image#crossorigin)
attribute by setting
[`crossOrigin`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/crossOrigin)
on the
[`HTMLImageElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement)
into which the image will be loaded. This tells the browser to request
cross-origin access when downloading the image data.

#### Starting the download

The code that starts the download (say, when the user clicks a
\"Download\" button), looks like this:

[js]

```js
function startDownload() {
  let imageURL =
    "https://cdn.glitch.com/4c9ebeb9-8b9a-4adc-ad0a-238d9ae00bb5%2Fmdn_logo-only_color.svg?1535749917189";
  let imageDescription = "The Mozilla logo";

  downloadedImg = new Image();
  downloadedImg.crossOrigin = "anonymous";
  downloadedImg.addEventListener("load", imageReceived, false);
  downloadedImg.alt = imageDescription;
  downloadedImg.src = imageURL;
}
```

We\'re using a hard-coded URL (`imageURL`) and associated descriptive
text (`imageDescription`) here, but that could easily come from
anywhere. To begin downloading the image, we create a new
[`HTMLImageElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement)
object by using the
[`Image()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/Image)
constructor. The image is then configured to allow cross-origin
downloading by setting its `crossOrigin` attribute to `"Anonymous"`
(that is, allow non-authenticated downloading of the image
cross-origin). An event listener is added for the
[`load`](https://developer.mozilla.org/en-US/docs/Web/API/Window/load_event)
event being fired on the image element, which means the image data has
been received. Alternative text is added to the image; while `<canvas>`
does not support the `alt` attribute, the value can be used to set an
`aria-label` or the canvas\'s inner content.

Finally, the image\'s
[`src`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/src)
attribute is set to the URL of the image to download; this triggers the
download to begin.

#### Receiving and saving the image

The code that handles the newly-downloaded image is found in the
`imageReceived()` method:

[js]

```js
function imageReceived() {
  const canvas = document.createElement("canvas");
  const context = canvas.getContext("2d");

  canvas.width = downloadedImg.width;
  canvas.height = downloadedImg.height;
  canvas.innerText = downloadedImg.alt;

  context.drawImage(downloadedImg, 0, 0);
  imageBox.appendChild(canvas);

  try {
    localStorage.setItem("saved-image-example", canvas.toDataURL("image/png"));
  } catch (err) {
    console.error(`Error: ${err}`);
  }
}
```

`imageReceived()` is called to handle the `"load"` event on the
`HTMLImageElement` that receives the downloaded image. This event is
triggered once the downloaded data is all available. It begins by
creating a new [`<canvas>`](element/canvas) element that we\'ll use to
convert the image into a data URL, and by getting access to the
canvas\'s 2D drawing context
([`CanvasRenderingContext2D`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D))
in the variable `context`.

The canvas\'s size is adjusted to match the received image, the inner
text is set to the image description, then the image is drawn into the
canvas using
[`drawImage()`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/drawImage).
The canvas is then inserted into the document so the image is visible.

Now it\'s time to actually save the image locally. To do this, we use
the Web Storage API\'s local storage mechanism, which is accessed
through the
[`localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
global. The canvas method
[`toDataURL()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/toDataURL)
is used to convert the image into a data:// URL representing a PNG
image, which is then saved into local storage using
[`setItem()`](https://developer.mozilla.org/en-US/docs/Web/API/Storage/setItem).

See also
--------

- [Using Cross-domain images in WebGL and Chrome
    13](https://blog.chromium.org/2011/07/using-cross-domain-images-in-webgl-and.html)
- [HTML Specification - the `crossorigin`
    attribute](https://html.spec.whatwg.org/multipage/embedded-content.html#attr-img-crossorigin)
- [Web Storage
    API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)

© 2005--2023 MDN contributors.\
Licensed under the Creative Commons Attribution-ShareAlike License v2.5
or later.\
https://developer.mozilla.org/en-US/docs/Web/HTML/CORS_enabled_image>>
