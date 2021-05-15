### Three Pillars of Good HTML and CSS

#### 1. Responsive design
- Fluid layout
- Media queries
- Responsive images
- Correct units
- Desktop-first vs. Mobile-first

#### 2. Maintainable and scalable code
- Clean
- Easy to understand
- Growth
- Reusable
- How to organize files
- How to name classes
- How to structure HTML

#### 3. Web performance
- Less HTTP requests
- Less code
- Compress code
- Use CSS preprocessor
- Less images
- Compress images

### What is Cascade? (C in CSS)
Process of combining different stylesheets and resolving conflicts between different CSS rules and declarations, when more than one rule applies to a certain element.
They are decided by:

#### Importance
1. User `!important` declarations
2. Author `!important` declarations
3. Author declarations
4. User declarations
5. default browser declarations

#### Specificity (when importance is the same)
1. inline styles
2. IDs
3. Classes, pseudo-classes, attribute
4. Elements, pseudo-elements

#### Source Order (when specificity is the same)
- The last declaration in the code will override all other declarations and will be applied.

### Cascade and Specificity
- CSS declared with `!important` have the highest priority
  - BUT only use `!important` as last resort. It's better to use correct specificities -- more maintainable code!
- Inline styles will always have priority over styles in external stylesheets
- A selector that contains 1 ID is more specific than one with 1000 classes
- A selector that contains 1 class is more specific than one with 1000 elements
- The universal selector `*` has no specificity value (0, 0, 0, 0)
- Rely more on **specificity** than on the **order** of selector
  - BUT rely on order when using 3rd-party stylesheets -- always put your author stylesheet last

### How CSS Values are Processed
1. Declared value (author declarations) 
2. Cascaded value (after the cascade)
3. Specified value (default, if there's no cascaded value)
4. Computed value (converting relative values to absolute)
5. Used value (final calculations based on layout)
6. Actual value (browser and device restrictions)

### How CSS is Parsed
Is there a cascaded value?
- Yes: Specified value = cascaded value
- No: Is the property inherited? (specific to each property)
  - Yes: Specified value = computed value of parent element
  - No: Specified value = initial value (specific to each property)

### CSS Inheritance
- Properties related to text are inherited, e.g. `font-family`, `font-size`, `color`
- The computed value of a property is what gets inherited, **not** the declared value
- Inheritance of a property only works if no one declares a value for that property
- The `inherit` keyword forces inheritance on a certain property
- The `initial` keyword resets a property to its initial value

### Inheritance vs. Selection (via [Udemy QA Section](https://www.udemy.com/course/advanced-css-and-sass/learn/lecture/8274436#questions/6010626))
When you choose something like:
```css
body {
  font-family: Verdana;
}
```
This is inheritance. It flows down. Each child inherits the properties of its parent. It doesn't create new instances of the different definitions in the selector.

If you added this:
```css
* {
  font-family: Arial;
}
 
body {
  font-family: Verdana;
}
```
You would think that because body comes after the `*`, it would would override the previous selector. It doesn't, though.

What is happening is that actual definitions override inheritance. The `*` creates a new selector for each element, making it a more specific selector for each element than inheritance from body.

For instance, if you were to use:
```css
body { 
  box-sizing: border-box; 
}
```
You would still have to use the `*` selector in conjunction with the body selector, because you need to select all of the `:before` and `:after` pseudo-elements. 

As a theoretical comparison:

**body**

- Applies style properties to body element.

- Elements within body may inherit the property values. Some properties default to `inherit`.

- Style declarations that match an element within body can override the inherited style.

**The Universal Selector `*`** (all elements)

- Applies style properties to all individual elements.

- Replaces inherited style properties, and default 'initial values'. Blocks inheritance.

- Other, more specific css selectors that match an element will replace the style properties applied by `*`.

Check out [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors) for more info.

### The Visual Formatting Model
- Definition: Algorithm that calculates boxes, and determines the layout of these boxes for each element in the render tree, so it can determine the final layout of the page.
- Dimensions of boxes: the box model
- Box type: `inline`, `block`, and `inline-block`
- Pisitioning scheme: floats and positioning
- Stacking contexts
- Other elements in the render tree, e.g. siblings, parents
- Viewing size, dimentions of images, etc

### The Think - Build - Architect Mindset
- **Think**: Think about the layout of your webpage/web app before writing code.
- **Build**: Build your layout in HTML and CSS with a consistent srtucture for naming classes.
- **Architect**: Create a logical architecture for your CSS with files and folders.

### THINK Component-Driven Design
- **Modular building blocks** that make up interfaces
- Held together by the **layout** of the page
- **Reusable** across a project and between different projects
- **Independent**, allowing us to use them anywhere on the page

### BUILD BEM System
- BEM: **B**lock **E**lement **M**odifier
  - Block: standalone component that is meaningful on its own
  - Element: part of a block that has no meaning on its own
  - Modifier: a different version of a block or element

```css
.block {}
.block__element {}
.block__element--modifier {}
```
Example:
```css
.recipe {}
.recipe__btn {}
.recipe__btn--round {}
```

### ARCHITECT The 7-1 Pattern
- 7 different folders for partial Sass files
- 1 main Sass file to import all other files into a compiled CSS stylesheet

The 7 folders:
```
base/
components/
layout/
pages/
themes/
abstracts/
vendors/
```

### Inline vs. Inline-block vs. Block
*Reference: [Samantha Ming Pictorials](https://www.samanthaming.com/pictorials/css-inline-vs-inlineblock-vs-block/)*

- Inline: 
  - does NOT start on a new line and only takes up as much width as its content
  - any height and width properties will have no effect
  - elements with default `inline` property: 
    - `span`
    - `a`
    - `img`
  - formatting tags that are inherently `inline`:
    - `em`
    - `strong`
    - `i`
    - `small`
- Inline-block:
  - essentially the same thing as inline, where it doesn’t start on a new line
  - BUT you can set height and width values
- Block:
  - starts a new line and takes up the whole width
  - you can set height and width values
  - elements with default `inline` property: 
    - `div`
    - `h1`
    - `p`
    - `li`
    - `section`

### Responsive Design Principles
- Fluid Grids and Layouts
  - use `%` rather than `px` for all layout-related lengths
- Flexible/Responsive Images
  - ensures that they adapt nicely to the current viewport
- Media Queries
  - use breakpoints to create different versions of the website for different widths

### Operators for Specific Selectors
- To select all `span` inside `p` tag:
```css
p span {
  color: yellow;
}
```
- To select `span` element only one level (i.e. first children) under `p` tag:
```css
p > span {
  color: yellow;
}
```
- To select only the first adjacent/neighboring element:
```css
p + span {
  color: yellow;
}
```
- To select ALL adjacent/neighboring elements:
```css
p ~ span {
  color: yellow;
}
```
- Use `*` to select **all** attributes that include the word "google":
```css
a[href*="google"] {
  color: orange;
}
```
- Use `^` to select attributes that begins with the word "https":
```css
a[href^="https"] {
  color: orange;
}
```
- Use `$` to select attributes that ends with the word ".com":
```css
a[href$=".com"] {
  color: orange;
}
```
- Use `~` to select attributes that contain **exactly** the word "google":
```css
a[href~="google"] {
  color: orange;
}
```


### Pseudo-classes vs. Pseudo-elements
- Pseudo-classes:
  - predefined keywords that are used to select an element based on its
**state**, or to target a specific child
  - start with a single colon, e.g. `:active`, `:checked`, `:disabled`, `:not()`, `:nth-child()`
- Pseudo-elements:
  - used to style a specific part of an element
  - start with a double colon, e.g. `::before`, `::after`

### Bits and Pieces
- [currentColor](https://css-tricks.com/currentcolor/): Use this value to indicate you want to use the value of color for other properties that accept a color value: borders, box shadows, outlines, or backgrounds
```css
div { 
  color: red; 
  border: 5px solid currentColor;
  box-shadow: 0 0 5px solid currentColor;
}
```
- [<details>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/details) tags in HTML: Creates an accordion. Must be used with `<summary>`
```html
<details>
    <summary>Details</summary>
    Something small enough to escape casual notice.
</details>
```
- Flexbox: growing and shrinking
  - There are two important sizes when dealing with Flexbox: the **minimum content size**, and the **hypothetical size**.
  - The minimum content size is the smallest an item can get without its contents overflowing.
  - Setting `width` in a flex row (or `height` in a flex column) sets the **hypothetical** size. It isn't a guarantee, it's a suggestion.
  - `flex-basis` has the same effect as `width` in a flex row (`height` in a column). You can use them interchangeably, but `flex-basis` will win if there's a conflict.
  - `flex-grow` will allow a child to consume any excess space in the container. It has no effect if there isn't any excess space.
  - `flex-shrink` will pick which item to consume space from, if the container is too small. It has no effect if there *is* any excess space.
  - `flex-shrink` can't shrink an item below its minimum content size. If all the items are below their minimum content size, this property has no effect.
  - `flex: 1` will assign `flex-grow: 1`, but it will also set `flex-basis: 0%`. It won't affect the default value for `flex-shrink`, which is `1`.
  - You can pass up to **3 values** to the `flex` shorthand, if you'd like to also tweak `flex-shrink` (2nd value) and `flex-basis` (3rd value).
  - Since `flex-basis` is a synonym for `width` in a flex row, we're effectively shrinking each child to have a “hypothetical width” of 0px, and then distributing all of the space between each child.
  - Shorthand gotcha: 
    - When we use the `flex` shorthand, we set `flex-basis` to `0`, and this value will override any `width` you set.
    ```css
    .item {
      flex: 1;
      width: 200px;
    }
    ``` 
    - To avoid this problem, it's best to use the `flex` shorthand with `flex-basis`:
    ```css
    .item {
      flex: 1 1 200px;
    }
    ``` 
  - Additional Resources from [CSS-Tricks](https://css-tricks.com/understanding-flex-grow-flex-shrink-and-flex-basis/)
- Flexbox vs. other layout modes
  - When there is a conflict between layout modes, **positioned** layout almost always wins (e.g. `position: fixed;`).
  - An exception to this rule is relative positioning, but it's kind of a special case.
    - If you give a flex child relative positioning, that element is technically being rendered in two different layout modes, but they're compatible; the element is first laid out inside the flex container, and then transposed using top/left/right/bottom by positioned layout.
  - `z-index` typically only works on an element using "positioned" layout (relative, absolute, fixed, or sticky), but there is one exception: the children of a `display: flex` parent can also use `z-index`. This will cause the element to create a stacking context.

- [clamp](https://blog.bitsrc.io/css-clamp-the-responsive-combination-weve-all-been-waiting-for-f1ce1981ea6e): CSS `clamp()` offers the best of CSS `min()` and CSS `max()` combined. CSS `clamp()` essentially clamps a value between an upper and lower bound. `clamp()` enables selecting a middle value within a range of values between a defined minimum and maximum. It takes three parameters: a minimum value, a preferred value, and a maximum allowed value.
