# jQuery-knowledge

**<font size="5">Using jQuery selesctos</font>**

**<font size="3">Selecting Nodes by Tag name</font>**


&nbsp;&nbsp;&nbsp;&nbsp;$('p') selects all ``` <p> ```  elements

&nbsp;&nbsp;&nbsp;&nbsp;$('a') selects all ``` <a> ``` elements

&nbsp;&nbsp;&nbsp;&nbsp;*To reference multiple tags, we use ```,```*

&nbsp;&nbsp;&nbsp;&nbsp;$('p, a, span') selects all paragraphs, anchors and span elements

**<font size="3">- Selecting Descendants</font>**

&nbsp;&nbsp;&nbsp;&nbsp;$('ancestor descendant') selects all of the descendants of the ancestor:

&nbsp;&nbsp;&nbsp;&nbsp;$('table tr')

&nbsp;&nbsp;&nbsp;&nbsp;selects all tr elements that are descendants of the table element.
&nbsp;&nbsp;&nbsp;&nbsp;Descendants are children, grandchildren, etc of the designated ancestor element.

**<font size="3">- Selecting by Element ID</font>**

&nbsp;&nbsp;&nbsp;&nbsp;<br/>``` $('#myID')``` selects <p id="myID"> element

**<font size="3">- Selecting by Class name</font>**

&nbsp;&nbsp;&nbsp;&nbsp;```$('a.myClass') <a class="myClass"></a>``` selects only ```<a>``` tags with class="myClass"

**<font size="2">- To modify css styles</font>**
 &nbsp;&nbsp;&nbsp;&nbsp; 
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

&nbsp;&nbsp;&nbsp;&nbsp;Or only focusing on div with these class names
```js
$('div.BlueDiv, div.RedDiv').css('border', '2px solid red');
```

**<font size="3">- Selecting nodes by Attribute Value</font>**

&nbsp;&nbsp;&nbsp;&nbsp;Use brackets to [attribute] to select based on  attribute name and/or attribute value:
```js
$('a[title]')
```
&nbsp;&nbsp;&nbsp;&nbsp;selects all ```<a>``` elements that have a title attribute.

```js
$('a[title="programmingInfo"]')
```
&nbsp;&nbsp;&nbsp;&nbsp;selects all ```<a>``` elements that have a "programmingInfo" title attribute value.


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
&nbsp;&nbsp;&nbsp;&nbsp;Selects all input elements including: input, select, textarea, button, image, radio...
```js
$(':input[type="radio"]')
```
&nbsp;&nbsp;&nbsp;&nbsp;Targets all radio button on the page.

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
&nbsp;&nbsp;&nbsp;&nbsp;Shows only the value of Card because it is the selected


&nbsp;&nbsp;&nbsp;&nbsp;You can assign a value as well to all the inputs
```js
$(':input').each(function() {
    var elem = $(this);
    alert(elem.val('Food')); // shows the value of each input
})
```

**<font size="3">- Additional selector features</font>**
```html
<div >This is my div</div>
```

```js
$('div:contains("my div")')
```

&nbsp;&nbsp;&nbsp;&nbsp;To set the background-color to the tr that are odd
```js
$('tr:odd').css('background-color', 'green');
```

&nbsp;&nbsp;&nbsp;&nbsp;To set the background-color to the tr that are even
```js
$('tr:even').css('background-color', 'yellow');
```

&nbsp;&nbsp;&nbsp;&nbsp;To set the background-color to the first child
```js
$('tr:first-child').css('background-color', 'blue');
```
**<font size="5">Interacting with the DOM</font>**

&nbsp;&nbsp;&nbsp;&nbsp;**<font size="3">- Iterating Through Nodes</font>**
```js
.each(function(index, Element)) 
```
&nbsp;&nbsp;&nbsp;&nbsp;is used to iterate through jQuery objects:
```js
    $('div').each(function(index){
        alert(index + '=' + $(this).text());
    });
```
&nbsp;&nbsp;&nbsp;&nbsp;Iterates through each div element and returns its index number and text

```js
    $('div').each(function(index, element){
        alert(index + '=' + $(element).text());
    });
```
&nbsp;&nbsp;&nbsp;&nbsp;<strong>Example</strong>
```html
<div id="OutputDiv"></div>
<div class="BlueDiv">
    <span>Blue div</span>
</div>
<div class="RedDiv">
    <span>Blue div</span>
</div>
```
```js
    var output = $('#OutputDiv');
    $('div.BlueDiv,div.RedDiv').each(function(index) {

        output.html(output.html() + "<br/>" + index + " " + $(this).text());
    });
```

A better way would be:
```js
    var html;
    $('div').each(function(index) {

        html += "<br/>" + index + " " + $(this).text();
    });
    var output = $('#OutputDiv');
    output.html;
```

&nbsp;&nbsp;&nbsp;&nbsp;**<font size="3">- Modifying DOM Object Properties</font>**

&nbsp;&nbsp;&nbsp;&nbsp; The this.propertyName statement can be used to modify an object's properties directly:
```js
$('div').each(function() {
    this.title = 'My index = ' + i;
})
```
&nbsp;&nbsp;&nbsp;&nbsp; Iterates through each div and modifies the title. If the property does not exists, it will be added.

&nbsp;&nbsp;&nbsp;&nbsp; **<font size="2">Accesing Attributes**</font>

&nbsp;&nbsp;&nbsp;&nbsp; Object attributes can be accessed using attr():
```js
var val = $('#CustomerDiv').attr('title');
```

&nbsp;&nbsp;&nbsp;&nbsp;Retrieves the value of the title attribute.

&nbsp;&nbsp;&nbsp;&nbsp; **<font size="2">Modifying attributes**</font>

&nbsp;&nbsp;&nbsp;&nbsp; .attr(attributeName, value) is the method used to access an object's attributes and modify the value:
```js
$('img').attr('title','My Image Title');
```

&nbsp;&nbsp;&nbsp;&nbsp;Changes the title attribute to a value of My Image Title.

&nbsp;&nbsp;&nbsp;&nbsp; **<font size="2">Modifying Multiple attributes**</font>

&nbsp;&nbsp;&nbsp;&nbsp; To modify multiple attributes, pass a JSON object containing name/value pairs:
```js
$('img').attr({
    title: 'My Image Title',
    style: 'border:2px solid black;'});
```

&nbsp;&nbsp;&nbsp;&nbsp;JSON object passed and used to change title and border.

&nbsp;&nbsp;&nbsp;&nbsp;<strong>Example</strong>
```js
$('div.BlueDiv,div.RedDiv').attr({
    title:'Some Title',
    style: 'font-size:14pt; background-color:yellow;'});
```

Another way to do with chaining:
```js
$('div.BlueDiv,div.RedDiv')
    .attr({
        title:'Some Title'
        }
    )
    .css('font-size', '14pt')
    .css('background-color', 'yellow');
```