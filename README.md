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