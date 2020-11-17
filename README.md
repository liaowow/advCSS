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

#### Specificity (when same importance)
1. inline styles
2. IDs
3. Classes, pseudo-classes, attribute
4. Elements, pseudo-elements

#### Source Order (when same specificity)
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

### How CSS Values are Processed
1. Declared value (author declarations) 
2. Cascaded value (after the cascade)
3. Specified value (default, if there's no cascaded value)
4. Computed value (converting relative values to absolute)
5. Used value (final calculations based on layout)
6. Actual value (browser and device restrictions)

### How CSS is Parsed
1. Is there a cascaded value?
- Yes: Specified value === cascaded value
- No: Is the property inherited? (specific to each property)
  - Yes: Specified value === computed value of parent element
  - No: Specified value === initial value (specific to each property)

### CSS Inheritance
- Properties related to text are inherited, e.g. `font-family`, `font-size`, `color`
- The computed value of a property is what gets inherited, **not** the declared value
- Inheritance of a property only works if no one declares a value for that property
- The `inherit` keyword forces inheritance on a certain property
- The `initial` keyword resets a property to its initial value