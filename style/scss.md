# File Structure

At all times our goal is modular, flat code with an emphasis on re-use. 

* One file = one concern
* If a file is taller than two screen-heights (400~600 lines), reconsider your structure
* Each SCSS file should have a corresponding template file - `header.twig` should correspond with `header.scss`. In the even that `menu.twig` is included in `header.twig`, there should still be a `menu.scss` to style the menu.


# BEM

Our standard naming convention is based on the [BEM](http://bem.info) (Block-Element-Modifier) methodology with the following additional rules, many of which are simple common sense. 

* Styling via ID is never acceptable, the `#` character has no place in our SCSS
* In general, avoid using tag names in classes. Markup such as `<section class="intro__section">` or `<div class="home__div">` is redundant and the name becomes meaningless in the event that the element type is changed during development. The exception to this rule can be `nav`. Classnames should not assume association with an element type, yet they should be descriptive. Global navigation could be named `<nav class="global-nav">` since `<nav class="global">` is not descriptive enough. 
* Nesting BEM elements within BEM elements is OK and is better than over-nesting beneath a namespace. This helps us avoid naming tricks that are essentially BEM but in logic not much different from deeply-nested CSS. 




