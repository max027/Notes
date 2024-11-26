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
        - flex:
