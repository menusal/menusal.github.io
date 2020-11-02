---
layout: post
title: JAVASCRIPT SORT ARRAY OF OBJECTS BY STRING PROPERTY VALUE
---


 ``` javasctipt
const characters = [
  {
    name: "A",
    content: "A content",
  },
  {
    name: "C",
    content: "C content",
  },
  {
    name: "D",
    content: "D content",
  },
];

characters.sort((a, b) => a.name.localeCompare(b.name));

console.log(characters)
```

