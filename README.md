# markdown-gallery
Converts a list of images into gallery mark-up so you can easily create a gallery without complex markdown (or custom) code and use CSS to control how it appears.

## How to use

##### 1. Write your list in markdown

Create a list of images (linked or unlinked) in markdown, either unordered or ordered, e.g.

```
* ![Image 1](http://example.com/image1.jpg)
* [![Image 2](http://example.com/image2.jpg)](http://example.com/image2_full.jpg)
* ![](http://example.com/image3.jpg)
```

Which will get convered to HTML like this:

```
<ul>
    <li><img src="http://example.com/image1.jpg" alt="Image 1"></li>
    <li><a href="http://example.com/image2_full.jpg"><img src="http://example.com/image2.jpg" alt="Image 2"></a></li>
    <li><img src="http://example.com/image3.jpg" alt></li>
</ul>
```

##### 2. Include the md-gallery file

Include the `md-gallery.js` file in the page (or add it your header/footer):

`<script src="path/to/md-gallery.js"></script>`

##### 3. Call the function

You then call it using:

```
<script>
    md_gallery();
</script>
```

## Result

When called, the script will search for lists that contain only images, linked images or a mixture of both and convert the HTML to something like this (based on the HTML above and the options used):

```
<div class="gallery gallery-cols-3">
    <figure>
        <img src="http://example.com/image1.jpg" alt="Image 1">
        <figcaption>Image 1</figcaption>
    </figure>
    <figure>
        <a href="http://example.com/image2_big.jpg"><img src="http://example.com/image2.jpg" alt="Image 2">
        <figcaption>Image 2</figcaption></a>
    </figure>
    <figure>
        <img src="http://example.com/image3.jpg" alt="">
    </figure>
</div>
```

## Options

There are a number of options you can use to control the final code generated:

### list_type
**default:** ul

This tells the script which type of list to search for. It works with either unordered lists (`ul`) or ordered lists (`ol`).

### class_name
**default:** gallery

The name of the class added to the tag that wraps around the figure elements generated for each image, which allows you to style the generated gallery.

### tag_type
**default:** div

The type of tag to wrap the figure elements with, which allows you to control how the block appears.

#### Example

Calling the function with the following options:

```
<script>
	md_gallery({
		'list_type':'ul',
		'class_name':'example',
		'tag_type':'article'
	});
</script>
```

Would generate the following output:

```
<article class="example gallery-cols-3">
    <figure>
        <img src="http://example.com/image1.jpg" alt="Image 1">
        <figcaption>Image 1</figcaption>
    </figure>
    <figure>
        <a href="http://example.com/image2_big.jpg"><img src="http://example.com/image2.jpg" alt="Image 2">
        <figcaption>Image 2</figcaption></a>
    </figure>
    <figure>
        <img src="http://example.com/image3.jpg" alt="">
    </figure>
</article>
```
