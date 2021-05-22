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
