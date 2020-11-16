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

#### Specificity
1. inline styles
2. IDs
3. Classes, pseudo-classes, attribute
4. Elements, pseudo-elements

#### Source Order
- The last declaration in the code will overrise all other declarations and will be applied.

### Cascade and Specificity
- CSS declared with `!important` have the highest priority
- BUT use only `!important` as last resort. It's better to use correct specificities -- more maintainable code!
- Inline styles will always have priority over styles in external stylesheets
- A selector that contains 1 ID is more specific than one with 1000 classes
- A selector that contains 1 class is more specific than one with 1000 elements
- The universal selector `*` has no specificity value (0, 0, 0, 0)
- Rely more on **specificity** than on the **order** of selector
- BUT rely on order when using 3rd-party stylesheets -- always put your author stylesheet last
