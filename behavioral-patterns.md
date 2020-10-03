# Behavioural Patterns

## Core/Real Behaviour Patterns

### Chain of Responsibility

As the name suggests, the chain of responsibility pattern creates a chain of receiver objects for a request. This pattern decouples sender and receiver of a request based on type of request.<br>
The design pattern promotes loose coupling by allowing a series of handlers to be created in a linked list or chain.<br><br>
The If-ElseIf-Else idiom is shown with this behaviour.

#### Structure
* AbstractClass (has AbstractClass "next", invokes as next if condition is not met) -> ClassA
* AbstractClass (has AbstractClass "next", invokes as next if condition is not met) -> ClassB
* AbstractClass (has AbstractClass "next", invokes as next if condition is not met) -> ClassC
#### Behaviour
* objA.next(objB)
* objB.next(objC)
* objA.execute(); // process or pass - execute or next.

Is it up to the programmer/problem what it should be implemented in the condition and under which circumstances the next object in the chain is invoked.<br><br>
**Technical similarities**: Decoration patterns has also chain call but it is a one unit as structure, here you can just exit the chain.

### Command

Command pattern is a data driven design pattern that enables all of the information for a request to be contained within a single object.<br>
The command can then be invoked as required, often as part of a batch of queued commands with rollback capabilities.<br><br>
The order is an interface which is implemented for any order. They orders are based on the methods of the base class.<br><br>
#### Structure
* BaseClass(do1, do2) - Receiver
* InterfaceOrder::execute -> DoOrder1(has BaseClase)::execute - wrapp BaseClass::do1
* InterfaceOrder::execute -> DoOrder2(has BaseClase)::execute - wrapp BaseClass::do2
* Invoker
#### Behaviour
1. (ListOfOrders) Add the order to the list. Execute later together with other commands.
2. (ListOfOrders) Add the order to the list and execute it.
3. The invoker wraps the commands.

The Orders are not more but claserization of the methods of the base class.<br>
Centralazie functionality like "save text", can be used from button or other element.<br>

### Mediator

The mediator pattern is a design pattern that promotes loose coupling of objects by removing the need for classes to communicate with each other directly.<br>
Instead, mediator objects are used to encapsulate and centralise the interactions between classes.<br><br>
Any Colleague need to have the mediatorObj.<br>
On other side the mediatorObj (ConcreteMediator) has to contain the references of the Colleagues.<br><br>
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

Should the Mediator need to be singleton?<br>
**Technical similarities**: It looks very similar to observer pattern.

### Observer

The observer pattern is a design pattern that defines a link between objects so that when one object's state changes, all dependent objects are updated automatically.<br><br>
#### Structure
* Subject(has list of IObserver, method "notifyAll" - intrates trough the IObserver::update)<br>
* IObserver(has Subject, method "update")
* IObserver -> ObserverA<br>
* IObserver -> ObserverB<br>
* IObserver -> ObserverC<br><br>
#### Behaviour
1. New Subject
2. Create the Observer with the subject object as parameter and add this observer into the list of subjects.
3. Setting the state in Subject invoked notifyAll.

This pattern from the interface/class relation point of view looks very similar to the mediator pattern.<br>
To use this pattern in Java you can the implementation from util package:<br>
* interface java.util.Observer <br>
* public class java.util.Observable

**Technical similarities**: It looks very similar to mediator pattern.

### Visitor

The visitor pattern is a design pattern that separates a set of structured data from the functionality that may be performed upon it.<br>
This promotes loose coupling and enables additional operations to be added without modifying the data classes.
#### Structure
* InterfaceElement(::accept(Visitor)) -> ConcreteElementA - lightWeight classes withou much functionallity
* InterfaceElement(::accept(Visitor)) -> ConcreteElementB
* InterfaceElement(::accept(Visitor)) -> ConcreteElementC
* InterfaceVisitor(visitMethod for any concrete Visitor) -> Visitor1 - where the functionallity is implemented
* InterfaceVisitor(visitMethod for any concrete Visitor) -> Visitor2
#### Behaviour
1. Initialize Elements as List.
2. Define Visitors<br>
3. Iterate trough the elements and invoke the accept with the Visitors.<br><br>

The logic is placed in the visitor and operates on the element which invoked the accept(Visitor)

## Algorithm Behaviour Patterns

### Interpreter

Interpreter pattern provides a way to evaluate language grammar or expression. This type of pattern<br>
This pattern involves implementing an expression interface which tells to interpret a particular context.<br>
This pattern is used in SQL parsing, symbol processing engine etc.<br><br>
#### Structure
* Interface::interpret(context) -> TerminalExoression::interpret(context)
* Interface::interpret(context) -> NonTerminalExoression1::interpret(context)
* Interface::interpret(context) -> NonTerminalExoression2::interpret(context)

### Strategy

he strategy pattern is a design pattern that allows a set of similar algorithms to be defined and encapsulated in their own classes.<br>
The algorithm to be used for a particular purpose may then be selected at run-time according to your requirements.<br><br>
#### Structure
* IStartegy(::calculation) -> Algorithm1
* IStartegy(::calculation) -> Algorithm2
* IStartegy(::calculation) -> Algorithm2
#### Behaviour
1. Create Client.
2. Use Algorithm class by purpose.

**My style**: The choosing algorithm can be encapsulated into the object creation method as part of the factory pattern.

### Template Method

The template method pattern is a design pattern that allows a group of interchangeable, similarly structured, multi-step algorithms to be defined.<br>
Each algorithm follows the same series of actions but provides a different implementation of the steps.<br><br>
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
The Null object pattern is a design pattern that simplifies the use of dependencies that can be undefined. This is achieved by using instances of a concrete class that implements a known interface, instead of null references.<br><br>
#### Structure
* AbstractClass -> ConcreteClass
* AbstractClass -> NullClass
* ClientClass(List<AbstractClass>)::get -> if nothing found then return NullClass.

### State

The state pattern is a design pattern that allows an object to completely change its behaviour depending upon its current internal state. <br>
By substituting classes within a defined context, the state object appears to change its type at run-time.<br><br>
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
