# Other Patterns

## MVC
### Introduction
Model-View-Controller
### Structure
* Model m - POJO
* View::print(m.property1, m.property2)
* Controllrt(has Model and View)
### Behaviour
1. Create Model object
2. Create View object
3. Create Controller with the Model and View objects
4. Invoke Controller::updateView (invokes View::print)
5. Change the Moodel state
6. Invoke Controller::updateView (invokes View::print)
### Source
* https://stackabuse.com/java-j2ee-design-patterns
### Notes
* Other MVC examples would be also useful to have.
* What is the big difference between MVC and MVVM, not only on abstraact level but also technically based on example.

## Generics Pattern
### Introduction

This pattern is introduces in the java generics tutorial as part of the excercise solution.
Since it can be seen as common approach it is a software pattern in OO languages who support generics.

### Behaviour
* Typ 1
  * Interface with a generic type parameter `MyInterface<T>`. 
  * Class which imlements the interface with concrete type parameter `class MyConcreteClass implements MyInterface<Integer>`.
* Typ 1
  * Abstract class with a generic type parameter `AbstractClass<T>`.
  * Class which extends the abstrac class with concrete type parameter `class MyConcreteClass extends AbstractClass<Integer>`.

### Source
* https://docs.oracle.com/javase/tutorial/java/generics/
* https://docs.oracle.com/javase/tutorial/java/generics/QandE/generics-questions.html
* https://docs.oracle.com/javase/tutorial/java/generics/QandE/generics-answers.html

### Notes
* This approach is never mentioned to be a pattern.
* It is very common used in relation with generics.
* The source of its existense is the Oracle tutorial about generics.
* It can be combined with other software design patterns like the Adapter pattern.
