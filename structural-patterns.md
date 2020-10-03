# Structural Patterns

## Strong Structural Patterns

### Bridge

It is a class combination i.e. shape and color. In the following table letters and numbers are defined as different class abstraction.<br>
|        | A     | B     |
| :------------- | :----------: | -----------: |
|  0 | A0   | B0    |
| 1   | A1 | B1 |

Contains first interface (main) and implementations. (Abstraction)<br>
Second interface and implementations which also contains the first one as reference. (Implementation)<br>
This way the both implementations as sub classes can be developed independently.
#### Structure
* Letter -> A<br>
* Letter -> B<br>
* Number -> 0 (has Letter)<br>
* Number -> 1 (has Letter)<br>

### Decorator

Attach a flexible additional responsibilities to an object dynamically.<br>
The Decorator Pattern is also known as Wrapper.
#### Structure
* ISomething -> ConcreteBaseA
* ISomething -> ConcreteBasetB
* ISomething -> AbstractDecorator (has also ISomething)
* AbstractDecorator -> ConcreteDecoratorA
* AbstractDecorator -> ConcreteDecoratorB
#### Behaviour
1. ConcreteDecoratorA(ConcreteDecoratorB(ConcreteBaseA)), ConcreteDecoratorA(ConcreteDecoratorB(ConcreteBaseB))

Where: number and order of decorator can be vary, at end base class is used.<br>
Since the structure is the same the same method is used for invoke the "decorations".<br><br>
Based on same interface.<br>
The pattern Bridge is based on different interfaces.<br>

## Medium Structural Patterns

### Adapter

It implemented method from the interface is (wrappes) using also the method of the reference or super class.
#### Structure
There are several different implementation of this pattern.<br>
1. It is realize with a class which implements interface and extends class. Its method of the interfaced in implemented wrapping the method of the class.<br>
2. It is realize with a class which implements interface and object reference. Its method of the interfaced in implemented wrapping the method of the object reference.<br><br>
Second one is recommended due to loose coupling.<br><br>
The object of the implementation is a main object here which used the funtionality from the extended or reference object.<br><br>
This pattern comes unconsciously when the class where this is used is extractred as interface and the method is part of the interface.<br>
The question is does this technical construct is always an adapter design pattern?

### Composite

Composite pattern is used where we need to treat a group of objects in similar way as a single object.<br>
Composite pattern composes objects in term of a tree structure to represent part as well as whole hierarchy.
#### Structure
Compose (has list if Compose).

### Flightweight

The flyweight pattern is a design pattern that is used to minimise resource usage when working with very large numbers of objects.<br><br>
Cache is used for this pattern.
#### Behaviour
1. getObjectFromCache - if object doesn't exsit create new one otherwise return the object.
2. Manipulate the necessary properties.
3. Use the object.

This pattern should be used if the shared state is legal, if the shared proerties still fitulls the recommendations (very similar or identical objects).<br><br>
Becuase it used cache it looks similar lie the prototype pattern.

### Proxy

In proxy pattern, a class represents functionality of another class. Proxies can improve efficiency and enhance functionality.
#### Structure
* Interface::do -> RealObject::do
* Interface::do -> ProxyObject::do (has RealObject) - if-condiiton is true then get/create RealObject use do-method
#### Behaviour
Client operated one ProxyObject<br><br>
Not only one but many methods can be used defined in the iterface.<br><br>
This pattern can be used as: Cache Proxy, Protection Proxy, Remote Proxy, Smart Proxy, Virtual Proxy.<br>
http://www.blackwasp.co.uk/Proxy.aspx

## Weak Structural Patterns

### Filter

This pattern filters collections by implemented criteria.
#### Structure
* Criteria::filter->Criteria1::filter
* Criteria::filter->Criteria2::filter
* Criteria::filter->Criteria3::filter
* Criteria1::filter(someList) // returns filtered collection

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
