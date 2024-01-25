# HTML

# [[_Resources/Markup And Styling/index|CSS]]
## [[_Resources/Markup And Styling/css/index#Syntax and semantics|Syntax and semantics]]
| Syntax | Literals or Example | Syntax | Literals |
| ---- | ---- | ---- | ---- |
| [[at-rule\|At-rules]] | `@identifier (RULE) {}` | [[_Resources/Markup And Styling/css/syntax#CSS declarations\|CSS syntax - declarations]] | `:` |
| [[comments\|Comments]] | `/* Comment */` | [[_Resources/Markup And Styling/css/syntax#CSS declaration blocks \| CSS syntax - declaration blocks]] | `{}` |
| [[inheritance\|Inheritance]] | `em {border: inherit;}` | [[_Resources/Markup And Styling/css/syntax#CSS rulesets \| CSS syntax - rules and ruleset]] | starts with `@` |
| [[shorthand_properties\|Shorthand properties]] | `margin: 10px 5px 10px 5px;` | [[_Resources/Markup And Styling/css/syntax#CSS statements \| CSS syntax - statements]] | ends with `;` |
| [[css_functions\|CSS functional notations]] | `selector { property: function([argument]? [, argument]!); }` | [[value_definition_syntax#Component value combinators\|Value definition syntax - combinators]] | ` `,`&&`,`\|\|`,`\|`,`[ ]`, |
|  |  | [[value_definition_syntax#Component value multipliers\|Value definition syntax - multipliers]] | ` `, `*`, `+`, `?`, `{A,B}` ,`#` , `!` |

### Semantics
- [[cascade#Complete cascade order|Cascade order]] : The **cascade** is an algorithm that defines how user agents combine property values originating from different sources.
- [Descriptor](https://developer.mozilla.org/en-US/docs/Glossary/CSS_Descriptor): A **CSS descriptor** defines the characteristics of an [at-rule](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule). At-rules may have one or multiple descriptors. Each descriptor has:
	- A name, 
	- A value, which holds the component values, 
	- An `!important` flag, which in its default state is unset.
- [[specificity#Selector weight categories|Specificity]]: **Specificity** is the algorithm used by browsers to determine the [CSS declaration](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS#css_syntax) that is the most relevant to an element, which in turn, determines the property value to apply to the element.
- [[css_values_and_units#Distance units|CSS unit and value types]]: Every CSS declaration includes a property / value pair. 
## [[_Resources/Markup And Styling/css/index#Selectors|Selectors]]
| Basic selectors | Literals | Grouping selectors | Literals |
| ---- | ---- | ---- | ---- |
| [[universal_selectors]] | `*` | [[selector_list]] | `A, B` |
| [[type_selectors]] | `elementname` |  |  |
| [[class_selectors]] | `.classname` |  |  |
| [[id_selectors]] | `#idname` |  |  |
| [[attribute_selectors]] | `[attr=value]` |  |  |

## [[_Resources/Markup And Styling/css/index#Combinators|Combinators]], [[_Resources/Markup And Styling/css/index#Pseudo|Pseudo]]
| Combinators | Literals | Pseudo | Literals |
| ---- | ---- | ---- | ---- |
| [[next-sibling_combinator]] | `A + B` | [[pseudo-classes]] | `:` |
| [[subsequent-sibling_combinator]] | `A ~ B` | [[pseudo-elements]] | `::` |
| [[child_combinator]] | `A > B` |  |  |
| [[descendant_combinator]] | `A B` |  |  |
| [[column_combinator]] | `A \|\| B` (Experimental) |  |  |

## [[_Resources/Markup And Styling/css/index#DOM-CSS / CSSOM|DOM-CSS / CSSOM]]
| Major object types 1 | Major object types 2 | Important method |
| ---- | ---- | ---- |
| [`Document.styleSheets`](https://developer.mozilla.org/en-US/docs/Web/API/Document/styleSheets) | [`HTMLElement.style`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style) | [`CSSStyleSheet.insertRule()`](https://developer.mozilla.org/en-US/docs/Web/API/CSSStyleSheet/insertRule) |
| `styleSheets[i].cssRules` | `HTMLElement.style.cssText` (just style) | [`CSSStyleSheet.deleteRule()`](https://developer.mozilla.org/en-US/docs/Web/API/CSSStyleSheet/deleteRule) |
| `cssRules[i].cssText` (selector & style) | [`Element.className`](https://developer.mozilla.org/en-US/docs/Web/API/Element/className) |  |
| `cssRules[i].selectorText` | [`Element.classList`](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList) |  |
