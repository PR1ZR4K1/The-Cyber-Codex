2024/10/04 12:03
Status: #idea
Tags:

# Lesson Plan: From HTML Basics to React Components

**Duration:** 1 hour

## Objectives:
By the end of this lesson, students will be able to:
1. Understand how HTML elements create the structure of a web page
2. Create a simple webpage using nested HTML elements
3. Recognize the concept of "boxes within boxes" in web design
4. Understand the basics of JSX/TSX and how it relates to HTML
5. Create simple React functional components

## I. Introduction (5 minutes)
- Recap of previous lesson on HTML elements and their semantic meanings
- Introduce the concept of "boxes within boxes" in web design

## II. Building a Simple Webpage (20 minutes)
- Live coding: Create a simple personal profile page using HTML
- Emphasize the nesting of elements to create structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Profile</title>
</head>
<body>
    <header>
        <h1>John Doe</h1>
        <p>Web Developer</p>
    </header>
    <main>
        <section>
            <h2>About Me</h2>
            <p>I'm a passionate web developer with 5 years of experience.</p>
        </section>
        <section>
            <h2>Skills</h2>
            <ul>
                <li>HTML</li>
                <li>CSS</li>
                <li>JavaScript</li>
                <li>React</li>
            </ul>
        </section>
    </main>
    <footer>
        <p>Contact: john@example.com</p>
    </footer>
</body>
</html>
```

- Discuss how each element is a "box" containing other "boxes" or content

## III. Visualizing the Box Structure (10 minutes)
- Use browser developer tools to highlight the box model of different elements
- Demonstrate how changing padding, margin, and border affects the layout

## IV. Introduction to JSX/TSX (15 minutes)
- Explain what JSX/TSX is and how it relates to HTML
- Demonstrate how the HTML structure translates to JSX in React

```jsx
function ProfilePage() {
  return (
    <div>
      <header>
        <h1>John Doe</h1>
        <p>Web Developer</p>
      </header>
      <main>
        <section>
          <h2>About Me</h2>
          <p>I'm a passionate web developer with 5 years of experience.</p>
        </section>
        <section>
          <h2>Skills</h2>
          <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
            <li>React</li>
          </ul>
        </section>
      </main>
      <footer>
        <p>Contact: john@example.com</p>
      </footer>
    </div>
  );
}
```

- Highlight the similarities and differences between HTML and JSX

## V. Creating React Functional Components (15 minutes)
- Introduce the concept of components as reusable pieces of UI
- Refactor the profile page into smaller components

```jsx
function Header({ name, title }) {
  return (
    <header>
      <h1>{name}</h1>
      <p>{title}</p>
    </header>
  );
}

function SkillsList({ skills }) {
  return (
    <ul>
      {skills.map(skill => <li key={skill}>{skill}</li>)}
    </ul>
  );
}

function ProfilePage() {
  const skills = ['HTML', 'CSS', 'JavaScript', 'React'];
  
  return (
    <div>
      <Header name="John Doe" title="Web Developer" />
      <main>
        {/* ... */}
        <section>
          <h2>Skills</h2>
          <SkillsList skills={skills} />
        </section>
      </main>
      <footer>
        <p>Contact: john@example.com</p>
      </footer>
    </div>
  );
}
```

- Discuss how components allow for better organization and reusability of code

## VI. Wrap-up and Q&A (5 minutes)
- Recap the journey from basic HTML to React components
- Address any questions from students
- Preview the next lesson on styling components






---
# References
