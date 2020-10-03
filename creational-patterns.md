#Creational Patterns

##Abstract Factory

This pattern can also be called Factory of Factory of Factory ... of Object pattern.
It returnes Factory (see next pattern description) which create Object.

##Factory

Class with mehtod which returns new created object of some type. The retrun value can also be generalazed object, therefore as retrun value interface can be declared.
Also parameter for an if-condition can be passed for runtime object type decision.

##Singleton

Only the one and alowed object is created from the class.

##Builder

Example: new ObjectBuider.addProperty1("some").addProperty2("some").build();
Creational pattern where the properties can be add and concatinated on the builder object and as last method the creational "build" is invoked. New object with the wished type is returned.
Example for this kind of usage is the StringBuilder.
Usually makes sence when the object has many properties and not all need to be overwritten at object creation.

##Prototype

This pattern is used when creation of object directly is costly. For example, an object is to be created after a costly database operation.
For this pattern cache is used where any object type has its presenter. On get-from-cache the own clone()-method is inviked and clone object are returned and used.

This pattern is very similar to the Flightweight pattern to me because of the usage if cache and shared state

##Object Pool

It is used to reuse the object that are expensive to create such a connections to DB.
Therefore the implementatiob needs to be thread safe which means concurrency programming techiques are used for the implementation.
Object pool design pattern is essentially used in Web Container of the server for creating thread pools and data source pools to process the requests.
