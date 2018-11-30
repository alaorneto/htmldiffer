# htmldiffer
Javascript library to highlight the content difference between two HTML block.

This project is a fork of the excelent [**htmldiff.js**](https://github.com/tnwinc/htmldiff.js/blob/master/src/htmldiff.coffee), written in CoffeeScript, with some adjustments, the biggest one being it don't ignore HTML img tags, so that it can mark changed images as deletions or insertions.

# Usage

First, you sould import the javascript file.

```
<script src="htmldiffer.js"></script>
```

Then, you can compare your HTML blocks.

```
var original = `
    <p>First paragraph.</p>
    <ul>
        <li>Item A</li>
        <li>Item B</li>
        <li>Item C</li>
    </ul>
    <img src='previous.jpg'>
    <span>This is some interesting text.</span>
`;

var modified = `
    <p>First paragraph.</p>
    <ul>
        <li>Item A</li>
        <li>Item B</li>
        <li>Item D</li>
    </ul>
    <img src='next.jpg'>
    <span>This is some new text.</span>
`;

var output = htmldiffer(original, modified);
```

You can then style the insertions and deletions using CSS.

```
ins {
    background-color: rgb(210, 253, 206);
}

ins img {
    border-color: rgb(210, 253, 206);
}

del {
    background-color: #ffdddd;
}

del img {
    border-color: #ffdddd;
```

The output variable will have the following content.

```
<p>First paragraph.</p>
<ul>
    <li>Item A</li>
    <li>Item B</li>
    <li>Item <del>C</del><ins>D</ins></li>
</ul>
<del><img src="previous.jpg"></del>
<ins><img src="next.jpg"></ins>
<span>This is some <del>interesting</del><ins>nice</ins> text.</span>
  
```
