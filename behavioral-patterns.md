# Behavioural Patterns

## Core/Real Behaviour Patterns

### Chain of Responsibility

#### Introduction
The chain of responsibility pattern is a design pattern that defines a linked list of handlers, each of which is able to process requests. When a request is submitted to the chain, it is passed to the first handler in the list that is able to process it.
#### Structure
* AbstractClass (has AbstractClass "next", invokes as next if condition is not met) -> ClassA
* AbstractClass (has AbstractClass "next", invokes as next if condition is not met) -> ClassB
* AbstractClass (has AbstractClass "next", invokes as next if condition is not met) -> ClassC
#### Behaviour
1. objA.next(objB)
2. objB.next(objC)
3. objA.execute(); // process or pass - execute or next.
#### Source
* http://www.blackwasp.co.uk/ChainOfResponsibility.aspx
* https://www.tutorialspoint.com/design_pattern/chain_of_responsibility_pattern.htm
* https://www.javatpoint.com/chain-of-responsibility-pattern
* https://refactoring.guru/design-patterns/chain-of-responsibility/java/example
* https://sourcemaking.com/design_patterns/chain_of_responsibility/java/2
#### Notes
* As the name suggests, the chain of responsibility pattern creates a chain of receiver objects for a request. This pattern decouples sender and receiver of a request based on type of request.
* The design pattern promotes loose coupling by allowing a series of handlers to be created in a linked list or chain.
* The If-ElseIf-Else idiom is shown with this behaviour.
* Is it up to the programmer/problem what it should be implemented in the condition and under which circumstances the next object in the chain is invoked.
* Technical similarities: Decoration patterns has also chain call but it is a one unit as structure, here you can just exit the chain.
* ***Chained objects are passing the data from one link to another until the all links are processed or some of them consumed the process and breaked it and returned the value or changed state of some object.***

### Command

#### Introduction
The command pattern is a design pattern that enables all of the information for a request to be contained within a single object. The command can then be invoked as required, often as part of a batch of queued commands with rollback capabilities.
#### Structure
* BaseClass(do1, do2) - Receiver
* InterfaceOrder::execute -> DoOrder1(has BaseClase)::execute - wrapp BaseClass::do1
* InterfaceOrder::execute -> DoOrder2(has BaseClase)::execute - wrapp BaseClass::do2
* Invoker
#### Behaviour
1. (ListOfOrders) Add the order to the list. Execute later together with other commands.
2. (ListOfOrders) Add the order to the list and execute it.
3. The invoker wraps the commands.
#### Source
* http://www.blackwasp.co.uk/Command.aspx
* https://www.tutorialspoint.com/design_pattern/command_pattern.htm
* https://www.javatpoint.com/command-pattern
* https://refactoring.guru/design-patterns/command/java/example
* https://sourcemaking.com/design_patterns/command/java/1
#### Notes
* Command pattern is a data driven design pattern that enables all of the information for a request to be contained within a single object.
* The command can then be invoked as required, often as part of a batch of queued commands with rollback capabilities.
* The order is an interface which is implemented for any order. They orders are based on the methods of the base class.
* The Orders are not more but claserization of the methods of the base class.
* Centralazie functionality like "save text", can be used from button or other element.
* ***The command pattern is based on the reciever class which can be also named as base class. Based on its properties command classes are defined and used to execute the setter/getter of the properties.***

### Mediator

#### Introduction
The mediator pattern is a design pattern that promotes loose coupling of objects by removing the need for classes to communicate with each other directly. Instead, mediator objects are used to encapsulate and centralise the interactions between classes.
#### Structure
* IMediator::method0()-> ConcreteMediator::method0() // setter/getter on all Concrete Colleague classes
* ColleagueBase(has a Mediator m) -> ColleagueA (can call m.method0())
* ColleagueBase(has a Mediator m) -> ColleagueB (can call m.method0())
* ConcreteMediator::method0()
#### Behaviour
1. Mediator m is created
2. ColleagueA(m) cA is created, m.setCA(cA)
3. ColleagueB(m) cB is created, m.setCA(cB)
4. The methods od the Colleagues can be invoked and the data should go trough the mediator.
#### Source
* http://www.blackwasp.co.uk/Mediator.aspx
* https://www.baeldung.com/java-mediator-pattern
* https://www.tutorialspoint.com/design_pattern/mediator_pattern.htm
* https://www.javatpoint.com/mediator-pattern
* https://refactoring.guru/design-patterns/mediator/java/example
* https://sourcemaking.com/design_patterns/mediator/java/2
#### Notes
* The mediator pattern is a design pattern that promotes loose coupling of objects by removing the need for classes to communicate with each other directly.
* Instead, mediator objects are used to encapsulate and centralise the interactions between classes.
* Any Colleague need to have the mediatorObj.
* On other side the mediatorObj (ConcreteMediator) has to contain the references of the Colleagues.
* Should the Mediator need to be singleton?
* Technical similarities: It looks very similar to observer pattern.
* ***Any data flow should get through the mediator class, thats why any of other classes have reference of the mediator and the mediator has references of them.***

### Observer

#### Introduction
The observer pattern is a design pattern that defines a link between objects so that when one object's state changes, all dependent objects are updated automatically. This pattern allows communication between objects in a loosely coupled manner.
#### Structure
* Subject(has list of IObserver, method "notifyAll" - intrates trough the IObserver::update)<br>
* IObserver(has Subject, method "update")
* IObserver -> ObserverA
* IObserver -> ObserverB
* IObserver -> ObserverC
#### Behaviour
1. New Subject
2. Create the Observer with the subject object as parameter and add this observer into the list of subjects.
3. Setting the state in Subject invoked notifyAll.
#### Source
* http://www.blackwasp.co.uk/Observer.aspx
* https://www.tutorialspoint.com/design_pattern/observer_pattern.htm
* https://www.javatpoint.com/observer-pattern
* https://refactoring.guru/design-patterns/observer/java/example
* https://sourcemaking.com/design_patterns/observer/java/1
* https://sourcemaking.com/design_patterns/observer/java/2
#### Notes
* ***The observer pattern is a design pattern that defines a link between objects so that when one object's state changes, all dependent objects are updated automatically.***
* This pattern from the interface/class relation point of view looks very similar to the mediator pattern.
* To use this pattern in Java you can the implementation from util package:
   * interface java.util.Observer
   * public class java.util.Observable
* Technical similarities: It looks very similar to mediator pattern.

### Visitor

#### Introduction
The visitor pattern is a design pattern that separates a set of structured data from the functionality that may be performed upon it. This promotes loose coupling and enables additional operations to be added without modifying the data classes.
#### Structure
* InterfaceElement(::accept(Visitor)) -> ConcreteElementA - lightWeight classes withou much functionallity
* InterfaceElement(::accept(Visitor)) -> ConcreteElementB
* InterfaceElement(::accept(Visitor)) -> ConcreteElementC
* InterfaceVisitor(visitMethod for any concrete Visitor) -> Visitor1 - where the functionallity is implemented
* InterfaceVisitor(visitMethod for any concrete Visitor) -> Visitor2
#### Behaviour
1. Initialize Elements as List.
2. Define Visitors
3. Iterate trough the elements and invoke the accept with the Visitors.
#### Source
* http://www.blackwasp.co.uk/Visitor.aspx
* https://www.tutorialspoint.com/design_pattern/visitor_pattern.htm
* https://refactoring.guru/design-patterns/visitor/java/example
* https://sourcemaking.com/design_patterns/visitor/java/1
* https://sourcemaking.com/design_patterns/visitor/java/3
* https://sourcemaking.com/design_patterns/visitor/java/4
#### Notes
* The visitor pattern is a design pattern that separates a set of structured data from the functionality that may be performed upon it.
* This promotes loose coupling and enables additional operations to be added without modifying the data classes.
* ***The logic is placed in the visitor and operates on the element which invoked the accept(Visitor) method. Any visitor implements elements specific methods for visting which means the number of the different methods is the same as for the different element types***


## Algorithm Behaviour Patterns

### Interpreter

#### Introduction
The interpreter pattern is a design pattern that is useful when developing domain-specific languages or notations. The pattern allows the grammar for such a notation to be represented in an object-oriented fashion that can easily be extended.
#### Structure
* Interface::interpret(context) -> TerminalExoression::interpret(context)
* Interface::interpret(context) -> NonTerminalExoression1::interpret(context)
* Interface::interpret(context) -> NonTerminalExoression2::interpret(context)
#### Source
* http://www.blackwasp.co.uk/Interpreter.aspx
* https://www.tutorialspoint.com/design_pattern/interpreter_pattern.htm
* https://www.javatpoint.com/interpreter-pattern
* https://sourcemaking.com/design_patterns/interpreter/java/2
#### Notes
* ***Interpreter pattern provides a way to evaluate language grammar or expression.***
* This pattern involves implementing an expression interface which tells to interpret a particular context.
* This pattern is used in SQL parsing, symbol processing engine etc.

### Strategy

#### Introduction
The strategy pattern is a design pattern that allows a set of similar algorithms to be defined and encapsulated in their own classes. The algorithm to be used for a particular purpose may then be selected at run-time according to your requirements.
#### Structure
* IStartegy(::calculation) -> Algorithm1
* IStartegy(::calculation) -> Algorithm2
* IStartegy(::calculation) -> Algorithm2
#### Behaviour
1. Create Client.
2. Use Algorithm class by purpose.
#### Source
* http://www.blackwasp.co.uk/Strategy.aspx
* https://www.tutorialspoint.com/design_pattern/strategy_pattern.htm
* https://www.javatpoint.com/strategy-pattern
* https://refactoring.guru/design-patterns/strategy/java/example
* https://sourcemaking.com/design_patterns/strategy/java/1
#### Notes
* ***This pattern is used to summarize algorithm classes which have identlcal entry point.***
* The choosing algorithm can be encapsulated into the object creation method as part of the factory pattern.

### Template Method

The template method pattern is a design pattern that allows a group of interchangeable, similarly structured, multi-step algorithms to be defined.<br>
Each algorithm follows the same series of actions but provides a different implementation of the steps.
#### Structure
* AbstractClass(::severalMethods)<br>
* AbstractClass -> Algorithm1<br>
* AbstractClass -> Algorithm2<br>
* AbstractClass -> Algorithm3<br><br>
#### Behaviour
1. Use the propriate calculcations by choosing the related Algorith class.

## State Behaviour Patterns

### Memento

Memento pattern is used to restore state of an object to a previous state.
#### Structure
* Memento(set/get State) - State storage unit.
* Originator(hasMemeto - saveStateToMemento/getStateFromMemento, get/set State)
* CarteTaker(has lists of Memento, add, get)
#### Behaviour
1. State structure needs to be same in both classes.
2 Originator on saveStateToMemento creates new Memmento with its current state and returns it.
2 Originator on getStateFromMemento sets the state from Memento as argument to Orginator.

### Null Object

Design where "nothing will come of nothing".<br>
The Null object pattern is a design pattern that simplifies the use of dependencies that can be undefined. This is achieved by using instances of a concrete class that implements a known interface, instead of null references.
#### Structure
* AbstractClass -> ConcreteClass
* AbstractClass -> NullClass
* ClientClass(List<AbstractClass>)::get -> if nothing found then return NullClass.

### State

The state pattern is a design pattern that allows an object to completely change its behaviour depending upon its current internal state. <br>
By substituting classes within a defined context, the state object appears to change its type at run-time.
#### Structure
* ContextClass(has State)<br>
* IState (has method defined which behave differently in the implemnetations)<br>
* IState -> StateA<br>
* IState -> StateB<br>
* IState -> StateC<br><br>
#### Behaviour
1. Create ContextClass with init State.
2. Invoke State1::doMetho(Context) changes state.
3. Invoke State2::doMetho(Context) changes state.
4. Invoke State3::doMetho(Context) changes state.

On any different state invoking the same method from the context would have different output.<br>

## Other Behaviour Patterns

### Iterator

The iterator pattern is a design pattern that provides a means for the elements of an aggregate object to be accessed sequentially without knowledge of its structure.<br>
This allows traversing of lists, trees and other structures in a standard manner.<br><br>
Straightforward solution:
#### Structure
* Interface Interator<br>
   * public boolean hasNext();
   * public Object next();
* Interface Container
   * public Iterator getIterator();
* Container -> ClassWithCollection
   * getIterator returned InnerIterator()
   * private class InnerIterator implements hasNext()/next()
#### Behaviour   
* Client
   * initialize - ClassWithCollection objWithCollection
   * iterate - for(Iterator iter = objWithCollection.getIterator(); iter.hasNext();)
