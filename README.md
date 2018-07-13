## Description
This file will allow you to create gradients with unlimited color stops, and to pull colors from values within the gradient range.

### Usage
Include gradient-min.js locally or through
```
  <script src="https://rawgit.com/cye131/gradient.js/master/gradient-min.js"></script>
```


### Example 1 - 2-color gradient with stops at 0 to 100
```
//Create gradient map and store it in grMap variable
var grMap = gradient.create(
  [0,100],
  ['#fff','#b3d9ff'],
  'hex'
);
//Calculate colors the gradient resolves to at specific values
testdiv.innerHTML += '<ol><li>Get the color at 0 in RGB: ' + gradient.valToColor(0,grMap,'rgb')+ '</li>' +
                     '<li>Get the color at 50 in RGBA: ' + gradient.valToColor(50,grMap,'rgba')+ '</li>' +
                     '<li>Get the color at 90 in Hex: ' + gradient.valToColor(50,grMap,'hex')+ '</li></ol>';

testdiv.innerHTML += '<span>Draw the full gradient:</span>';
for (var i=0;i<100;i+=2) {
  var color = gradient.valToColor(i,grMap,'hex');
  testdiv.innerHTML += '<div style="width:100%;height:3px;background-color:' + color + '"></div>';
}

![alt text](https://raw.githubusercontent.com/cye131/gradient.js/master/example-images/ex1.png)
```

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/cye131/gradient.js/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
