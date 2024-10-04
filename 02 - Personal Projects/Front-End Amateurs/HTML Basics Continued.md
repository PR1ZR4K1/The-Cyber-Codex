2024/09/27 02:51
Status: #idea
Tags: [[HTML Basics]]

# Introduction to HTML and Tailwind CSS


## Common HTML Elements

HTML provides a wide range of elements, each serving a specific purpose. Here are some of the most commonly used elements, including those with semantic meaning:

### Structural Elements

1. `<div>`: A generic container for flow content.
2. `<span>`: A generic inline container.

### Semantic Structural Elements

3. `<header>`: Represents introductory content, typically a group of introductory or navigational aids.
4. `<nav>`: Represents a section of a page that links to other pages or to parts within the page.
5. `<main>`: Represents the dominant content of the body of a document.
6. `<article>`: Represents a self-contained composition in a document, page, application, or site.
7. `<section>`: Represents a standalone section of a document, which doesn't have a more specific semantic element to represent it.
8. `<aside>`: Represents a portion of a document whose content is only indirectly related to the main content.
9. `<footer>`: Represents a footer for its nearest sectioning content or sectioning root element.

### Text Content

10. `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`: Heading elements.
11. `<p>`: Represents a paragraph.
12. `<ul>`: Represents an unordered list of items.
13. `<ol>`: Represents an ordered list of items.
14. `<li>`: Represents a list item.

### Inline Text Semantics

15. `<a>`: Creates a hyperlink to web pages, files, email addresses, or anything else a URL can address.
16. `<strong>`: Indicates strong importance, seriousness, or urgency for its contents.
17. `<em>`: Marks text that has stress emphasis.
18. `<code>`: Displays its contents styled in a fashion intended to indicate that the text is a short fragment of computer code.

### Image and Multimedia

19. `<img>`: Embeds an image into the document.
20. `<video>`: Embeds a media player for video playback.
21. `<audio>`: Embeds sound content in documents.

### Table Content

22. `<table>`: Represents tabular data.
23. `<tr>`: Defines a row of cells in a table.
24. `<td>`: Defines a cell of a table that contains data.
25. `<th>`: Defines a cell as header of a group of table cells.

### Forms and Input

26. `<form>`: Represents a document section containing interactive controls for submitting information.
27. `<input>`: Used to create interactive controls for web-based forms.
28. `<button>`: Represents a clickable button.
29. `<label>`: Represents a caption for an item in a user interface.
30. `<textarea>`: Represents a multi-line plain-text editing control.

### Semantic Usage Example

Here's an example of how these semantic elements might be used together:

```html
<body>
  <header>
    <h1>My Website</h1>
    <nav>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>
  
  <main>
    <article>
      <h2>Article Title</h2>
      <p>This is the main content of the article.</p>
      <section>
        <h3>Section Heading</h3>
        <p>This is a section within the article.</p>
      </section>
    </article>
    
    <aside>
      <h3>Related Links</h3>
      <ul>
        <li><a href="#">Link 1</a></li>
        <li><a href="#">Link 2</a></li>
      </ul>
    </aside>
  </main>
  
  <footer>
    <p>&copy; 2024 My Website. All rights reserved.</p>
  </footer>
</body>
```

Using semantic elements not only provides structure to your HTML but also improves accessibility and SEO. It helps search engines and assistive technologies understand the structure and content of your web pages.





---
# References

- [[HTML Basics]]