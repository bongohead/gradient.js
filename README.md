## Description
This file will allow you to create gradients with unlimited color stops, and to pull colors from values within the gradient range.

## Usage
Include gradient-min.js locally or through
```
  <script src="https://rawgit.com/cye131/gradient.js/master/gradient-min.js"></script>
```

##Examples

### Example 1: 2-color gradient with stops at 0 to 100
Create gradient map and store it in grMap variable.

**The first parameter of gradient.create should be an array of values where the gradient changes color (in increasing order), the second parameter the array of colors, and the third parameter the format of the colors of the previous parameter. Possible values for the third parameter include 'hex', 'rgb', and 'rgba'.**
```
var grMap = gradient.create(
  [0,100],
  ['#fff','#b3d9ff'],
  'hex'
);
```
Calculate colors the gradient resolves to at specific values:
```javascript
gradient.valToColor(0,grMap,'rgb'); //returns rgb(255,255,255)
gradient.valToColor(50,grMap,'rgba'); //returns rgba(217,236,255,1)
gradient.valToColor(50,grMap,'hex')'; //returns #d9ecff
```
Draw out the gradient:
```
for (var i=0;i<100;i+=2) {
  var color = gradient.valToColor(i,grMap,'hex');
  testdiv.innerHTML += '<div style="width:100%;height:3px;background-color:' + color + '"></div>';
}
```
![alt text](https://raw.githubusercontent.com/cye131/gradient.js/master/example-images/ex1.png)


