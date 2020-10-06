# Structural Patterns

## Strong Structural Patterns

### Bridge

#### Introduction
The bridge pattern is a design pattern that separates the abstract elements of a class from its technical implementation. This provides a cleaner implementation of real-world objects and allows the implementation details to be changed easily.
#### Structure
* Letter -> A
* Letter -> B
* Number -> 0 (has Letter)
* Number -> 1 (has Letter)
#### Source
* http://www.blackwasp.co.uk/Bridge.aspx
* https://www.javatpoint.com/bridge-pattern
* https://refactoring.guru/design-patterns/bridge/java/example
#### Notes
|    |  A  | B  |
| :- | :-: | -: |
| 0  | A0  | B0 |
| 1  | A1  | B1 |
* It is a class combination i.e. shape and color. In the following table letters and numbers are defined as different class abstraction.
* Contains first (main) interface and implementations (***Abstraction***).
* Second interface and implementations which also contains the first one as reference (***Implementation***).
* This way the both implementations as sub classes can be developed independently.

### Decorator

#### Introduction
The decorator pattern is a design pattern that extends the functionality of individual objects by wrapping them with one or more decorator classes. These decorators can modify existing members and add new methods and properties at run-time.
#### Structure
* ISomething -> ConcreteBaseA
* ISomething -> ConcreteBasetB
* ISomething -> AbstractDecorator (has also ISomething)
* AbstractDecorator -> ConcreteDecoratorA
* AbstractDecorator -> ConcreteDecoratorB
#### Behaviour
1. ConcreteDecoratorA(ConcreteDecoratorB(ConcreteBaseA)), ConcreteDecoratorA(ConcreteDecoratorB(ConcreteBaseB))
   * Where: number and order of decorator can be vary, at end base class is used.
#### Source
* http://www.blackwasp.co.uk/Decorator.aspx
* https://www.javatpoint.com/decorator-pattern
* https://refactoring.guru/design-patterns/decorator/java/example
* https://sourcemaking.com/design_patterns/decorator/java/3
#### Notes
* ***Object of an concrete base class is created mostly inner in the nested structure creation but invoked as first object and it is used as base object for all other objects (decorators) which are decorating the base more and more as they are nested.***
* Attach a flexible additional responsibilities to an object dynamically.
* The Decorator Pattern is also known as Wrapper.
* Because the structure is the same at all objects the same method is used for invoke the "decorations".
* This pattern is based on same interface.
* The pattern Bridge is based on different interfaces.

## Medium Structural Patterns

### Adapter

#### Introduction
The adapter pattern is a design pattern that is used to allow two incompatible types to communicate. Where one class relies upon a specific interface that is not implemented by another class, the adapter acts as a translator between the two types.
#### Structure
There are several different implementation of this pattern.:
1. ***It is realize with a class which implements interface and extends class. The implemented interface method wrapps the method from the super class.***
2. ***It is realize with a class which implements interface and object reference. The implemented interface method wrapps the method from the object reference.***
* Second approach is recommended due to loose coupling.
#### Source
* http://www.blackwasp.co.uk/Adapter.aspx
* https://www.javatpoint.com/adapter-pattern
* https://refactoring.guru/design-patterns/adapter/java/example
#### Notes
* It implemented method from the interface is (wrappes) using also the method of the reference or super class.
* The object of the implementation is a main object here which used the funtionality from the extended or reference object.
* This pattern comes unconsciously when the class where this is used is extractred as interface and the method is part of the interface.
* The question is does this technical construct is always an adapter design pattern?

### Composite

#### Introduction
The composite pattern is a design pattern that is used when creating hierarchical object models. The pattern defines a manner in which to design recursive tree structures of objects, where individual objects and groups can be accessed in the same manner.
#### Structure
* Compose (has list of Compose objects).
#### Source
* http://www.blackwasp.co.uk/Composite.aspx
* https://www.javatpoint.com/composite-pattern
* https://refactoring.guru/design-patterns/composite/java/example
* https://sourcemaking.com/design_patterns/composite/java/3
* https://sourcemaking.com/design_patterns/composite/java/2
#### Notes
* Composite pattern is used where we need to treat a group of objects in similar way as a single object.
* ***Composite pattern composes objects in term of a tree structure to represent part as well as whole hierarchy.***

### Flightweight

#### Introduction
The flyweight pattern is a design pattern that is used to minimise resource usage when working with very large numbers of objects. When creating many thousands of identical objects, stateless flyweights can lower the memory used to a manageable level.
#### Structure
* Cache is used for this pattern.
#### Behaviour
1. getObjectFromCache - if object doesn't exsit create new one otherwise return the object.
2. Manipulate the necessary properties.
3. Use the object.
#### Source
* http://www.blackwasp.co.uk/Flyweight.aspx
* https://www.javatpoint.com/flyweight-pattern
* https://refactoring.guru/design-patterns/flyweight/java/example
#### Notes
* ***The flyweight pattern is a design pattern that is used to minimise resource usage when working with very large numbers of objects.***
* This pattern should be used if the shared state is legal, if the shared proerties still fitulls the recommendations (very similar or identical objects).<br><br>
* Becuase it used cache it looks similar lie the prototype pattern.

### Proxy

#### Introduction
The proxy pattern is a design pattern that creates a surrogate, or placeholder class. Proxy instances accept requests from client objects, pass them to the underlying object and return the results. Proxies can improve efficiency and enhance functionality.
#### Structure
* Interface::do -> RealObject::do
* Interface::do -> ProxyObject::do (has RealObject) - if-condiiton is true then get/create RealObject use do-method
#### Behaviour
1. Client operated one ProxyObject
#### Source
* http://www.blackwasp.co.uk/Proxy.aspx
* https://www.javatpoint.com/proxy-pattern
#### Notes
* ***Instead wokring on real objects the proxy is used***
* In proxy pattern, a class represents functionality of another class. Proxies can improve efficiency and enhance functionality.
* Not only one but many methods can be used defined in the iterface.
* ***This pattern can be used as: Cache Proxy, Protection Proxy, Remote Proxy, Smart Proxy, Virtual Proxy.***

## Weak Structural Patterns

### Filter

#### Introduction
Filter pattern or Criteria pattern is a design pattern that enables developers to filter a set of objects using different criteria and chaining them in a decoupled way through logical operations. This type of design pattern comes under structural pattern as this pattern combines multiple criteria to obtain single criteria.
#### Structure
* Criteria::filter->Criteria1::filter
* Criteria::filter->Criteria2::filter
* Criteria::filter->Criteria3::filter
* Criteria1::filter(someList) // returns filtered collection
#### Source
* https://www.tutorialspoint.com/design_pattern/filter_pattern.htm
#### Notes
* ***This pattern filters collections by implemented criteria.***

### Facade

Facade pattern hides the complexities of the system and provides an interface to the client using which the client can access the system.<br>
It hides the classes of the subsistem trough its existence.
#### Structure
* Subsystem (Package)
* ClassA, ClassB, ClassC
* ClassFacade uses ClassA, ClassB, ClassC.
#### Behaviour
Either you have public method which fully uses their functionality<br>
ClassFacade::do -> (ClassA::everyMethod, ClassB::everyMethod, ClassC::everyMethod)<br>
or many methods which bundle the methods of the Subclasses.<br>
ClassFacade::doHorizontal -> (ClassA::doOne, ClassB::doOne, ClassC::doOne)<br>
ClassFacade::doVertical -> (ClassA::doOne, ClassA::dOther)<br>

### Private Class Data

Separate data from methods that use it. Providing new type of final - final after constructor.
#### Structure
BaseClass - in contructor init the DataClass from the arguments. DataClass is declated final.<br>
DataClass with private proerties, setters and getters.<br><br>
I can not see it the momen the real benfit of this construct.
