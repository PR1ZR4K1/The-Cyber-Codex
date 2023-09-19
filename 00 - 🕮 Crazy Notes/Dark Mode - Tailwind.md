2023/09/12 09:42
Status: #idea
Tags: [[Tailwind CSS]]

# Dark Mode - Tailwind

Dark mode is a first-class feature of many operating systems. Tailwind includes a `dark` variant that lets you style your site differently when dark mode is enabled.

## How to Enable

It’s important to note that because of file size considerations, ***the dark mode variant is not enabled in Tailwind by default***.

To enable it, set the `darkMode` option in your `tailwind.config.js` file to `media`:

module.exports.darkMode = 'media'

## Defaults

The dark mode colors will be used by default if the user's operating system has dark mode enabled.

## How to Toggle Dark Mode Manually

Use `class` strategy instead of `media` strategy:

module.exports.darkMode = 'class'

Now instead of `dark:{class}` classes being applied based on `prefers-color-scheme`, they will be applied whenever `dark` class is present earlier in the HTML tree.




---
# References

- https://v2.tailwindcss.com/docs/dark-mode