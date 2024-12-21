---
title: 'using-graphics'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I include images in a LaTeX document?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Demonstrate how to include images in a LaTeX document.
- Show how to position images manually / automatically in a LaTeX document.

::::::::::::::::::::::::::::::::::::::::::::::::

## The Graphicx Package

In order to use graphics in our document, we'll need to use the `graphicx` package, which adds the
`\includegraphics` command to LaTeX. We'll add this to the preamble of our document:

```latex
\usepackage{graphicx}
```

We can now include several types of images in our document, including:

- JPEG
- PNG
- PDF
- EPS

### Uploading Images to Overleaf

In order to incorporate an image into our document, we'll need to upload it to Overleaf. We can do
this by clicking on the "Upload" icon on the upper left corner of the Overleaf editor:

![](fig/06-using-graphics/overleaf-upload.png){alt='The upload icon in Overleaf.'}

We can then either drag and drop the image into the upload window or click on the "Select files"
button to choose the image from our computer.

For the purposes of this lesson, we'll use the following image:

![](fig/06-using-graphics/example-image.png){alt='Our example image.'}

Once you have uploaded the image, you should see it in the "Files" section of the Overleaf editor:

![](fig/06-using-graphics/overleaf-uploaded-image.PNG){alt='The uploaded image in Overleaf.'}

## Including an Image in a LaTeX Document

Now that we have our image uploaded, we can include it in our document using the `\includegraphics`
command:

```latex
\includegraphics{example-image.png}
```

Your document should now look like this:

![](fig/06-using-graphics/document-with-image.PNG){alt='Our document with an included image.'}

::: callout

If you just want to see how an image might look in your document without having to upload one, you
can use the filepath `example-image` in the `\includegraphics` command. This will display a
image in your document that you can replace later.

:::

### Adjusting the appearance of the image

We can adjust the appearance of the image by passing options to the `\includegraphics` command. For
example, we can specify the height of the image:

```latex
\includegraphics[height=4cm]{example-image.png}
```

![](fig/06-using-graphics/document-with-small-image.PNG){alt='Our document with a smaller image.'}

::: callout

Some other possible options from the `graphicx` package include:

- `width`: the width of the image
- `scale`: the scaling factor of the image
- `angle`: the angle of rotation of the image
- `clip`: whether to clip the image to its bounding box
- `trim`: trim the image by a specified amount
- `draft`: display a box instead of the image

:::

### Positioning the image

We can place the image inside of an environment to help position it in the document. Let's try
placing the `\includegraphics` command inside of a `\begin{center}` and `\end{center}` environment:

```latex
\begin{center}
  \includegraphics[height=2cm]{example-image.png}
\end{center}
```

You should see that the image is now centered on the page:

![](fig/06-using-graphics/document-with-centered-image.PNG){alt='Our document with a centered image.'}

## "Floating" Images

It's often the case that images need to "float" around the document as new text is added or removed.
this is called a "floating" image. Images are normally included as floats so that we don't end up
with large gaps in the document.

To make an image float, we can use the `figure` environment:

```latex
\begin{figure}
  \centering
  \includegraphics[height=2cm]{example-image.png}
\end{figure}
```

When we render the document, we can see that, even though we placed the image at the end of the
document, it appears at the top of the page:

![](fig/06-using-graphics/document-with-floating-image.PNG){alt='Our document with a floating image.'}

::: callout

You might have noticed that instead of using the `\begin{center}` and `\end{center}` environment,
we used the `\centering` command inside of the `figure` environment. This is because the `figure`
environment is a floating environment, and the `\centering` command is the recommended way to
center content inside of a floating environment.

:::

### Controlling the Position of a Floating Image

We can pass parameters to the `figure` environment to control the position of the floating image:

- `h`: Place the float "here" (where it appears in the code)
- `t`: Place the float at the "top" of the page
- `b`: Place the float at the "bottom" of the page
- `p`: Place the float on a "page" by itself

It is also possible to combine these options. For example, to place the float here if possible, but
otherwise at the top of the page, we can use the `ht` option:

```latex
\begin{figure}[ht]
  \centering
  \includegraphics[height=2cm]{example-image.png}
\end{figure}
```

### Adding a Caption

We can add a caption to our image by using the `\caption` command inside of the `figure` environment:

```latex
\begin{figure}
  \centering
  \includegraphics[height=2cm]{example-image.png}
  \caption{This is a caption for our image.}
\end{figure}
```

When we render the document, we can see that the caption appears below the image:

![](fig/06-using-graphics/document-with-floating-image-caption.PNG){alt='Our document with a floating image.'}

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Can you do it?

What is the output of this command?

```r
paste("This", "new", "lesson", "looks", "good")
```

:::::::::::::::::::::::: solution

## Output

```output
[1] "This new lesson looks good"
```

:::::::::::::::::::::::::::::::::


## Challenge 2: how do you nest solutions within challenge blocks?

:::::::::::::::::::::::: solution

You can add a line with at least three colons and a `solution` tag.

:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- Use `.md` files for episodes when you want static content
- Use `.Rmd` files for episodes when you need to generate output
- Run `sandpaper::check_lesson()` to identify any issues with your lesson
- Run `sandpaper::build_lesson()` to preview your lesson locally

::::::::::::::::::::::::::::::::::::::::::::::::

