# Description
This is a no-frills JS library to allow users to create gradients with unlimited color stops, and to pull colors from values within the gradient range.

# Usage
Include gradient-min.js locally or through
```
  <script src="https://rawgit.com/cye131/gradient.js/master/gradient-min.js"></script>
```


# Examples

Also on https://jsbin.com/somapih/edit?html,js,output

### Example 1: 2-color gradient with stops at 0 to 100

First create a gradient map variable using the function `gradient.create(arrayOfStops,arrayofColors,inputColorType)`.

```javascript
var grMap = gradient.create(
  [0,100], //array of color stops
  ['#fff','#b3d9ff'], //array of colors corresponding to color stops
  'hex' //format of colors in previous parameter - 'hex', 'htmlcolor', 'rgb', or 'rgba'
);
```
You can then calculate colors the gradient resolves to at specific values. Use the function `gradient.valToColor(value,gradientMap,'outputColorType')`.

Possible values for the third parameter of `gradient.valToColor` include 'hex', 'rgb', and 'rgba'.

```javascript
gradient.valToColor(0,grMap,'rgb'); //returns rgb(255,255,255)
gradient.valToColor(50,grMap,'rgba'); //returns rgba(217,236,255,1)
gradient.valToColor(50,grMap,'hex'); //returns #d9ecff
```
Drawing the gradient:
```javascript
for (var i=0;i<100;i+=2) {
  var color = gradient.valToColor(i,grMap,'hex');
  testdiv.innerHTML += '<div style="width:100%;height:3px;background-color:' + color + '"></div>';
}
```
![alt text](https://raw.githubusercontent.com/cye131/gradient.js/master/example-images/ex1.png)

---

### Example 2: 4-color gradient from -50 to 150 using HTML color names (List of available color names from [w3schools](https://www.w3schools.com/cssref/css_colors.asp))

Create gradient map variable:
```javascript
var grMap = gradient.create(
  [-50,10,75,150],
  ['darkgreen','lightblue', 'white','khaki'],
  'htmlcolor'
);
```
Calculating colors the gradient resolves to at specific values:
```javascript
gradient.valToColor(-13,grMap,'rgb'); //returns rgb(107,172,142)
gradient.valToColor(50,grMap,'rgba'); //returns rgba(223,240,245,1)
gradient.valToColor(50,grMap,'hex'); //returns #dff0f5
```
Drawing the gradient:
```javascript
for (var i=-50;i<150;i+=5) {
  var color = gradient.valToColor(i,grMap,'hex');
  testdiv.innerHTML += '<div style="width:100%;height:2px;background-color:' + color + '"></div>';
}
```
![alt text](https://raw.githubusercontent.com/cye131/gradient.js/master/example-images/ex2.png)

### Example 3: 8-color gradient from -1 to 1 with semi-transparent RGBA inputs

Create gradient map variable:
```javascript
var grMap = gradient.create(
  [-1,-0.5,-0.15,0,0.3,0.5,0.8,1],
  ['rgba(5,0,255,1)','rgba(0,132,255,.8)','rgba(0,212,255,.6)','rgba(0,255,204,.5)','rgba(253,255,53,.4)','rgba(255,160,0,.5)','rgba(255,50,0,.8)','rgba(255,0,122,1)'],
  'rgba'
);
```
Drawing the gradient:
```javascript
for (var i=-1;i<1;i+=0.10) {
  var color = gradient.valToColor(i,grMap,'rgba');
  testdiv.innerHTML += '<div style="width:100%;background-color:' + color + '">'+
                         '<span style="font-size:x-small">' + 
                            'value: ' + i.toFixed(1) + ' | hex: ' + color +
                         '</span>' + 
                       '</div>';
}
```
![alt text](https://raw.githubusercontent.com/cye131/gradient.js/master/example-images/ex3.png)

