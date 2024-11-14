---
layout: post
title: Composition vs. Inheritance in React with TypeScript: Understanding the Differences
date: 2024-11-14 09:00:00
---
# Composition vs. Inheritance in React with TypeScript: Understanding the Differences

In React, developers often use **Composition** and **Inheritance** to organize and reuse code, especially in building complex UIs. React’s component-based structure makes **Composition** the preferred method for creating reusable and maintainable components, while **Inheritance** is generally used sparingly. In this article, we’ll explain the differences between Composition and Inheritance in React and show examples in TypeScript.

## What is Composition?

**Composition** is a pattern where components are combined together to create more complex UIs. Instead of inheriting behavior, components receive data and functionality as props, making them more flexible and reusable. React promotes composition over inheritance because it allows developers to build isolated and modular components.

### Example of Composition

Let’s create a simple `Card` component that can accept any content through `children`. This component can then be used to display any custom data passed as its child:

```typescript
import React from 'react';

type CardProps = {
  children: React.ReactNode;
};

const Card: React.FC<CardProps> = ({ children }) => {
  return <div className="card">{children}</div>;
};

const ProfileCard: React.FC = () => (
  <Card>
    <h2>Jane Doe</h2>
    <p>Software Developer</p>
  </Card>
);

export default ProfileCard;
```

In this example, Card acts as a generic wrapper, and we use children to inject custom content. This is a common use of composition in React, where ProfileCard adds specific content to Card.

### Advantages of Composition

- **Flexibility:** Components are reusable and can accept any type of content.
- **Single Responsibility:** Each component can have a focused purpose.
- **Customizability:** Individual components can be tailored with props and children.

## What is Inheritance?

Inheritance allows a class or function to inherit properties and methods from another class. In object-oriented programming, inheritance is a powerful way to reuse code, but in React, it often results in tightly coupled components, which can make them difficult to maintain and reuse in different contexts. React’s recommendation is to avoid inheritance for components in favor of composition.

### Example of Inheritance

Here’s how inheritance would look using TypeScript and ES6 classes in React. Let’s create a base Button component that IconButton extends:

```typescript
import React from 'react';

class Button extends React.Component<{ label: string }> {
  render() {
    return <button className="btn">{this.props.label}</button>;
  }
}

class IconButton extends Button {
  render() {
    return (
      <button className="btn">
        <span className="icon">⭐</span>
        {this.props.label}
      </button>
    );
  }
}

export default IconButton;
```

In this example, IconButton inherits from Button, adding an icon before the label. While this approach works, it is often less flexible than composition and not the recommended approach in React.

### Drawbacks of Inheritance

- **Tight Coupling:** Inheritance creates dependencies between components.
- **Reduced Reusability:** Components become harder to use in new contexts.
- **Complexity:** Code becomes harder to track and maintain.

## Why React Favors Composition Over Inheritance

React is built around Composition as a core principle because it offers flexibility, reusability, and easier testing. By combining small, self-contained components, developers can build complex interfaces in a modular way, avoiding the downsides of inheritance.

### Using Composition to Extend Functionality

To better illustrate the benefits of composition, let’s refactor the Button example from above. Instead of using inheritance, we’ll use composition to add an icon dynamically.

```typescript
Copy code
import React from 'react';

type ButtonProps = {
  onClick: () => void;
  children: React.ReactNode;
};

const Button: React.FC<ButtonProps> = ({ onClick, children }) => (
  <button className="btn" onClick={onClick}>
    {children}
  </button>
);

type IconButtonProps = {
  icon: React.ReactNode;
  label: string;
  onClick: () => void;
};

const IconButton: React.FC<IconButtonProps> = ({ icon, label, onClick }) => (
  <Button onClick={onClick}>
    <span className="icon">{icon}</span> {label}
  </Button>
);

export default IconButton;
```
In this example, IconButton uses composition to include an icon within Button, making it more flexible without modifying the Button component directly.

## When to Use Composition vs. Inheritance in React

Use Composition When:

- **You need flexibility:** Composition allows for combining components in various ways.
- **Customizable behavior:** It’s easier to modify a single component without affecting its dependents.
- **Clear separation of concerns:** Each component has its own specific function.

Use Inheritance When:
- **Extending utility classes (rare in React):** Only if absolutely necessary.
- **Specific hierarchy:** If a component truly shares a base class structure (though composition is still often preferable).

## Summary

React strongly advocates for Composition over Inheritance to build reusable, isolated, and flexible components. Composition allows developers to build complex UIs by combining simpler parts, aligning well with React’s declarative design.

### Key Points

- **Composition enables flexible component structures, making it ideal for UI development in React.**
- **Inheritance is less common and generally avoided in React, as it leads to tighter coupling and reduced reusability.**
- **Favoring composition results in components that are easier to read, understand, and maintain.**
- **By understanding these patterns, you’ll be able to design more scalable and maintainable React applications.**
