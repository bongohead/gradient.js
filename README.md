## Demo

You can use the [editor on GitHub](https://github.com/cye131/gradient.js/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.


### Example 1
<a class="jsbin-embed" href="https://jsbin.com/togipupovu/embed"> on jsbin.com</a><script src="https://static.jsbin.com/js/embed.min.js?4.1.4"></script>
```
testdiv.innerHTML += '<h4>2-color gradient with stops at 0 to 100</h4>'
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
