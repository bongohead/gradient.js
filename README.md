##### Table of Contents  
[Description](#description)  
[Usage](#usage)  
[Basic Example](#example-1-2-color-gradient-with-stops-at-0-to-100)  
[Example with HTML Color Names](#example-2-4-color-gradient-from--50-to-150-using-html-color-names-list-of-available-color-names-from-w3schools)  
[Example with negative gradient values and semi-transparent RGBA inputs](#example-3-8-color-gradient-from--1-to-1-with-semi-transparent-rgba-inputs)  
[Example working with SVG elements](#example-4-working-with-svg)  
[Example #2 with SVG elements](#example-5-another-svg-example)



# Description
A vanilla JS tool to allow users to create gradients with unlimited color stops, and to pull colors from values within the gradient range. Especially useful for dynamically assigning datapoint-specific colors when working with JS dataviz tools.

# Usage
Include gradient-min.js locally or through
```
  <script src="https://rawgit.com/cye131/gradient.js/master/gradient-min.js"></script>
```


# Examples

**Also on https://jsbin.com/somapih/edit?html,js,output**

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


### Example 4: Working with SVG

Create SVG diamond:
```javascript
  var svg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
  svg.setAttribute('width','200');
  svg.setAttribute('height','200');
  testdiv.appendChild(svg);
  
  //SVG 'd' attribute for paths to create a diamond shape
  var d0 ='M100,0 L200,100 100,200 0,100Z';
  
  //Define gradient
  var grMap = gradient.create(
    [0,10,30,40,50,70,80,90,100],     ['rgba(5,0,255,1)','rgba(0,132,255,.8)','rgba(0,212,255,.6)','rgba(0,255,204,.5)','rgba(253,255,53,.4)','rgba(255,160,0,.5)','rgba(255,50,0,.8)','rgba(255,0,122,1)','rgba(255,255,255,1)'],
    'rgba'
  );
  
  
  //Draw SVG
  for (var i=0;i<=100;i+=1) {
    var color = gradient.valToColor(i,grMap,'rgba');
    
    var path = document.createElementNS('http://www.w3.org/2000/svg', 'path');
    var d = 'M100,'+i.toString()+' L'+(200-i).toString()+',100 100,'+(200-i).toString()+' '+i.toString()+',100Z';
    console.log(d);
    path.setAttribute('d','M100,'+i.toString()+' L'+(200-i).toString()+',100 100,'+(200-i).toString()+' ' + i + ',100Z');
    path.setAttribute('fill',color);
    svg.appendChild(path);
    
    //Add animation
    path.innerHTML = '<animate attributeName="d" from="'+d+'" to="'+d0+'" dur="30s" fill="freeze" repeatCount="indefinite" />';
  }
```
Result:  
https://cye131.github.io/gradient.js/example-images/example.html#ex4


### Example 4: Another SVG Example
```
  //Create SVG container
  var svg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
  svg.setAttribute('width','200');
  svg.setAttribute('height','200');
  testdiv.appendChild(svg);
  
  //Create outer diamond
  var d0 ='M100,0 L200,100 100,200 0,100Z';
  
  //Define gradient
  var grMap = gradient.create(
    [0,10,30,40,50,70,80,90,100],
    ['rgba(5,0,255,1)','rgba(0,132,255,.8)','rgba(0,212,255,.6)','rgba(0,255,204,.5)','rgba(253,255,53,.4)','rgba(255,160,0,.5)','rgba(255,50,0,.8)','rgba(255,0,122,1)','rgba(255,255,255,1)'],
    'rgba'
  );
  
  
  //Draw SVG
  for (var i=0;i<=100;i+=1) {
    var color = gradient.valToColor(i,grMap,'rgba');
    
    var path = document.createElementNS('http://www.w3.org/2000/svg', 'path');
    var d = 'M100,'+i.toString()+' L'+(200-i).toString()+',100 100,'+(200-i).toString()+' '+i.toString()+',100Z';
    path.setAttribute('d','M100,'+i.toString()+' L'+(200-i).toString()+',100 100,'+(200-i).toString()+' ' + i + ',100Z');
    path.setAttribute('fill',color);
    path.setAttribute('id',i);
    svg.appendChild(path);
    
    var dur = ((i/1000+0.0001).toFixed(4)).toString() + 's';
    console.log(dur);
    path.innerHTML = '<animateTransform attributeType="xml" attributeName="transform" type="rotate" from="0 100 100" to="360 100 100" dur="'+dur+'" additive="sum" repeatCount="indefinite" />';
    //Add animation
  
  }

  var interval = setInterval(randomColors, 100);
  function randomColors() {
    var n = Math.random();
    n = Math.floor(n*100);
    var randColorIndex = Math.floor(Math.random() * 100);
    var newColor = gradient.valToColor(randColorIndex,grMap,'rgba');
    document.getElementById(n).setAttribute('fill',newColor);
    
    for (var i=1;i<=100;i++) {
      if (randColorIndex + i > 100 || n + i > 100) break;
      newColor = gradient.valToColor(randColorIndex+i,grMap,'rgba');
      document.getElementById(n+i).setAttribute('fill',newColor);
    }
    
  }
```

Result:  
https://cye131.github.io/gradient.js/example-images/example.html#ex5
