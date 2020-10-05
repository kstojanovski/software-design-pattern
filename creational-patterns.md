# Creational Patterns

## Abstract Factory

### Introduction
The abstract factory pattern is a design pattern that allows for the creation of groups of related objects without the requirement of specifying the exact concrete classes that will be used. One of a number of factory classes generates the object sets.
### Source
* http://www.blackwasp.co.uk/AbstractFactory.aspx
### Notes
* This pattern can also be called ***Factory of Factory of Factory ... of Object*** pattern.
* It returnes Factory (see next pattern description) which create Object.

## Factory

### Introduction
The factory method pattern is a design pattern that allows for the creation of objects without specifying the type of object that is to be created in code. A factory class contains a method that allows determination of the created type at run-time.
### Source
* http://www.blackwasp.co.uk/FactoryMethod.aspx
### Notes
* Class with **create**-mehtod which ***returns new created object***. The retrun value can also be generalazed object, therefore as return declaration an interface is declared.
* Also parameter for an if-condition can be passed for runtime object type decision.

## Singleton

### Introduction
The singleton pattern is a design pattern that is used to ensure that a class can only have one **concurrent** instance. Whenever additional objects of a singleton class are required, the previously created, single instance is provided.
### Source
* http://www.blackwasp.co.uk/Singleton.aspx
### Notes
* Only **the one and alowed object is created** from the class.
* The thread safe implementation of this pattern needs to be used.

## Builder

### Introduction
The builder pattern is a design pattern that allows for the step-by-step creation of complex objects using the correct sequence of actions. The construction is controlled by a director object that only needs to know the type of object it is to create.
### Behaviour
* `new ObjectBuider.addProperty1("some").addProperty2("some").build();`
### Source
* http://www.blackwasp.co.uk/Builder.aspx
### Notes
* This pattern should be used when the ***object has many properties***, also when ***not all properties need to be initialized at object creation***.
* Creational pattern where the properties can be add and concatinated on the builder object and as last method the creational "build" is invoked. New object with the wished type is returned.
* Example for this kind of usage is the StringBuilder.

## Prototype

### Introduction
The prototype design pattern is a design pattern that is used to instantiate a class by copying, or cloning, the properties of an existing object. The new object is an exact copy of the prototype but permits modification without altering the original.
### Source
* http://www.blackwasp.co.uk/Prototype.aspx
### Notes
* This pattern is used when ***creation of object directly is costly***. For example, an object is to be created after a costly database operation.
* For this pattern ***cache is used where any object type has its presenter***. On get-from-cache the own clone()-method is invoked and ***clone object are returned and used***.
* This pattern is very similar to the Flightweight pattern to me because of the usage if cache and shared state.

## Object Pool

### Introduction
Object pooling can offer a significant performance boost; it is most effective in situations where the cost of initializing a class instance is high, the rate of instantiation of a class is high, and the number of instantiations in use at any one time is low.
### Source
* https://sourcemaking.com/design_patterns/object_pool
### Notes
* It is used to reuse the object that are expensive to create such a connections to DB.
* Therefore the implementatiob needs to be thread safe which means concurrency programming techiques are used for the implementation.
* Object pool design pattern is essentially used in Web Container of the server for creating thread pools and data source pools to process the requests.
