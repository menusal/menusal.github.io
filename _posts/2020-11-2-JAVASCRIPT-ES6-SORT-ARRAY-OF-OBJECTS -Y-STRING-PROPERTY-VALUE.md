---
layout: post
title: JAVASCRIPT SORT ARRAY OF OBJECTS BY STRING PROPERTY VALUE
date: 2020-06-18 12:00:00
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

