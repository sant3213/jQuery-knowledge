# jQuery-knowledge

**<font size="5">Selecting Nodes by Tag name</font>**

**- Selecting by Tag name**

$('p') selects all ``` <p> ```  elements

$('a') selects all ``` <a> ``` elements

*To reference multiple tags, we use ```,```*

$('p, a, span') selects all paragraphs, anchors and span elements

**<font size="3">- Selecting Descendants</font>**

$('ancestor descendant') selects all of the descendants of the ancestor:

$('table tr')

selects all tr elements that are descendants of the table element.
Descendants are children, grandchildren, etc of the designated ancestor element.

**<font size="3">- Selecting by Element ID</font>**

``` $('#myID')``` selects <p id="myID"> element

**<font size="3">- Selecting by Class name</font>**

```$('a.myClass') <a class="myClass"></a>``` selects only ```<a>``` tags with class="myClass"

**<font size="2">- To modify css styles</font>**
```html
<div class="BlueDiv">
    <span>Blue div</span>
</div>
```
```js
$('.BlueDiv').css('border', '2px solid red');
```
To apply only to div tags with class BlueDiv
```js
$('div.BlueDiv').css('border', '2px solid red');
```
To apply only to span tags with class BlueDiv
```js
$('span.BlueDiv').css('border', '2px solid red');
```

To apply it to multiple classes
```html
<div class="BlueDiv">
        <span>Blue div</span>
</div>
<div class="RedDiv">
        <span>Red div</span>
</div>
```
```js
$('.BlueDiv, RedDiv').css('border', '2px solid red');
```

Or only focusing on div with these class names
```js
$('div.BlueDiv, div.RedDiv').css('border', '2px solid red');
```

**<font size="3">- Selecting nodes by Attribute Value</font>**

Use brackets to [attribute] to select based on  attribute name and/or attribute value:
```js
$('a[title]')
```
selects all ```<a>``` elements that have a title attribute.

```js
$('a[title="programmingInfo"]')
```
selects all ```<a>``` elements that have a "programmingInfo" title attribute value.


```html
<input id="LastNameTextBox" type="text" />
```
```js
$('input[type="text"]')
```

**<font size="3">- Selectin input Elements</font>**

```js
$(':input')
```
Selects all input elements including: input, select, textarea, button, image, radio...
```js
$(':input[type="radio"]')
```
Targets all radio button on the page.

```js
$(':input').each(function() {
    var elem = $(this);
    alert(elem.val()); // shows the value of each input
})
```
```html
<select id="sel">
    <option value="Sant">Sant</option>
    <option value="Card" selected="true">Card</option>
</select>
```
Shows only the value of Card because it is the selected


You can assign a value as well to all the inputs
```js
$(':input').each(function() {
    var elem = $(this);
    alert(elem.val('Food')); // shows the value of each input
})
```