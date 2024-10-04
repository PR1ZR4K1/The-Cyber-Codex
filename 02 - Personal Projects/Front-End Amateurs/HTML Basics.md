2024/09/27 02:49
Status: #idea
Tags: [[HTML Basics]]

# Introduction to HTML and Tailwind CSS

## What is HTML?

HTML (HyperText Markup Language) is the standard markup language for creating web pages. It describes the structure of a web page using a series of elements. These elements tell the browser how to display the content.

### Basic HTML Structure

A simple HTML document looks like this:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Web Page</title>
</head>
<body>
    <h1>Welcome to My Web Page</h1>
    <p>This is a paragraph of text.</p>
</body>
</html>
```

- The `<!DOCTYPE html>` declaration defines this document as HTML5
- The `<html>` element is the root element of an HTML page
- The `<head>` element contains meta information about the document
- The `<body>` element defines the document's body, which contains all the visible contents

## What is CSS?

CSS (Cascading Style Sheets) is used to style and layout web pages. It describes how HTML elements should be displayed on screen, paper, or in other media.

## Introduction to Tailwind CSS

Tailwind CSS is a utility-first CSS framework that allows you to build custom designs without leaving your HTML. Instead of writing custom CSS, you apply pre-existing classes directly in your HTML.

### Key Features of Tailwind CSS:

1. Utility-First: Provides low-level utility classes to build custom designs.
2. Responsive: Easily create responsive layouts using responsive variants.
3. Customizable: Tailor the framework to your design needs through configuration.

### Basic Usage

To use Tailwind, you add classes to your HTML elements. For example:

```html
<div class="bg-blue-500 text-white p-4 rounded-lg">
  <h2 class="text-xl font-bold mb-2">Hello, Tailwind!</h2>
  <p class="text-sm">This is a sample component using Tailwind CSS classes.</p>
</div>
```

In this example:
- `bg-blue-500` sets a blue background color
- `text-white` sets white text color
- `p-4` adds padding
- `rounded-lg` rounds the corners
- `text-xl` and `text-sm` set font sizes
- `font-bold` makes text bold
- `mb-2` adds margin to the bottom

Tailwind CSS allows you to rapidly build custom user interfaces without writing custom CSS, making it an efficient tool for both beginners and experienced developers.





---
# References

- [[HTML Basics Continued]]