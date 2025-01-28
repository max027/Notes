# Html
## tags
### output
The <output> tag is used to represent the result of a calculation (like one performed by a script).
```html
<input type="range" name="booking_people" id="booking_people" min="1" max="5" value="4" oninput="this.nextElementSibling.value=this.value">  
<output name="" for="booking_people">4</output>
```

### datalist
The <datalist> tag specifies a list of pre-defined options for an <input> element.
```html 
<label id="booking_location" for="booking_location">Locations</label>
<input id="booking_location" name="booking_location" list="locations">
<datalist id="locations">
<option value="downtown"></option>
<option value="uptown"></option>
</datalist>
```
# Css
* Browser window which is visible on screen is called viewport
* Display property specifies the display behavior (the type of rendering box) of an element.
## Css web layout
* Flexbox
* Grid
* Box



### Flexbox
* Flexbox is single-dimensional, which means you can align it either along a row or a column and it is set to row alignment by default.
* For the items present inside the flexbox container, the placement starts from the top-left corner moving along the main or horizontal axis
    - Alignment properties
        - justify-content. For item alignment on main axis.
        - align-items. For item alignment on cross axis.
        - align-self. For unique flex items on cross axis.
        - align-content. Used for packing flex lines and control over space.
        - flex-direction:This property is used to set the main axis, which is a ‘row’ by default. It basically means you are changing your ‘main’ axis from horizontal rows to vertical columns. 
        - gap:gap property can be used to create space between the items along the main axis.
        - flex-basis: sets initial size of element
        - flex-grow: sets how element will grow
        - flex-shrink: sets how element will shrink

### Grid
* A grid will allow you organize the various elements on your page. 
* grid-template-rows: none
    - This feature allows you configure your elements so that they are organized similarly to rows on a table.
* grid-template-columns: none
    - This feature allows you configure your elements but with this setting the elements are organized like columns on a table.

### Different css selectors
1. Element selector
2. Id selector
3. Class selector
4. Attribute selector
5. nth-of-type selector
6. nth-child  selector
7. star selector

### Specificity hierarchy
CSS has a set of rules that it uses to ‘score’ or assign a certain weight to selectors and this creates a specificity hierarchy. Based on the weights, there are four categories in this hierarchy: 
1. Inline styles 
2. IDs 
3. Classes, attributes, and pseudo-classes 
4. Elements and pseudo-elements 

guidelines and rules that become important especially in cases when the score for the different selectors is the same. Some of these are:
* Every selector will have a score and place in the hierarchy
* In the case of selectors with equal specificity, the latest or last written rule is the one that will be applied
* In general, ID selector should be applied in cases where you need to be certain about a rule 
* Universal selectors have zero specificity value

### Combination selector
1. Descendent selector
Description: Selects all elements (B) that are descendants (children, grandchildren, or further nested levels) of a specified element (A).

2. child selector
Description: Selects all elements (B) that are direct children of a specified element (A).

3. General sibling selector
Description: Selects all elements (B) that are siblings of a specified element (A) and come after it, not necessarily immediately.

4. Adjecant selector
Description: Selects the first element (B) that is immediately preceded by another element (A).

## Pseudo-classes
A CSS pseudo-class is a keyword added to a selector that lets you style a specific state of the selected element(s).
### Syntax
```css
selector:pseudo-element {
 property: value; 
}
```


