2023/09/26 13:39
Status: #idea
Tags:

# Virtual DOM

React maintains a lightweight in-memory cache, the Virtual DOM, where it keeps a representation of the UI. When changes occur, React first performs operations on the Virtual DOM, then it uses a diffing algorithm to identify what changed, and finally, it efficiently updates the actual DOM, minimizing direct manipulation of the DOM and improving performance.





---
# References
