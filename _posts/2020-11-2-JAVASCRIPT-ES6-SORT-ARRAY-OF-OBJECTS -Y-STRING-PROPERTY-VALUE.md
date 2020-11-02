---
layout: post
title: JAVASCRIPT SORT ARRAY OF OBJECTS BY STRING PROPERTY VALUE
---


/**
 * 👽 Author: https://www.linkedin.com/in/sifat-haque/
 * ✅ Task: Sort array of objects by string property value
 */

const characters = [
  {
    name: "Levi",
    animeName: "Attack On Titan",
  },
  {
    name: "Edward Elric",
    animeName: "Fullmetal Alchemist",
  },
  {
    name: "Ichigo Kurosaki",
    animeName: "Bleach",
  },
];

characters.sort((a, b) => a.name.localeCompare(b.name));

console.log(characters)

