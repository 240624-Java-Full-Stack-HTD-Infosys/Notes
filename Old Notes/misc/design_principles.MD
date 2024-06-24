# Week 1 Java Review Notes



## SOLID: (OOP guiding principles)  

The Single-responsibility principle: "There should never be more than one reason for a class to change." In other words, every class should have only one responsibility. When we say "change" here we are talking about changing the state. We can say, a class should have only one reason to exist.

The Open–closed principle: "Software entities should be open for extension, but closed for modification." Instead of changing the original, we extend (inherit from) it and modify the child class.
  
The Liskov substitution principle: "Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it." See also design by contract. This is referring to "subtype polymorphism", using a reference of an ancestor type to store, return, or pass an object of a descendant type. You should be able to use the descendant anywehere the ancestor would be valid.
  
The Interface segregation principle: "Clients should not be forced to depend upon interfaces that they do not use." If an interface has behaviors X, Y, and Z, and we have a class which will implement behavior X but doesn't need Y or Z, it's likely these behaviors should be segregated into multiple interfaces. That way our concrete class doesn't have Y, and Z which it doesn't need.
  
The Dependency inversion principle: "Depend upon abstractions, not concretions." Instead of making dependencies concrete classes, depend upon the abstract parent class which sets out the contract the concrete class fulfills, this way we can swap out one implementation for a different one easily.
  
Dependency Injection (not to be confused with code injection, a security vulnerability) - instead of creating a dependency within a 
class, or as part of the constructor, that dependency is created elsewhere and is passed as a parameter in a method (usually 
the constructor).
  
Loose Coupling (opposite of tight coupling) - This is the idea that encapsulations should depend upon other encapsulations as little as possible, and those dependencies should be easy to change without causing a cascade of modifications to many other encapsulations. Tightly coupled code is difficult to refactor. Losely coupled code is much easier. Things like Dependency Injection, Liskov Substitution, and Dependency Inversion lead us to losely coupled code.
  

Eager vs Lazy
Eager - To create the necessary resources as early as possible. Pay the cost early so it's ready on demand, and notice any bugs right away.
Lazy - To create necessary resources as late as possible, on-demand. If a resource is never actually needed, you never have to pay that cost.
