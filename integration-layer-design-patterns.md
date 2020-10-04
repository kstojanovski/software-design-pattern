# Integration Layer Design

## Data Access Object

### Introduction
The Data Access Object pattern, most often shortened to DAO is a pattern in which ***objects are dedicated to the communication with the Data Layer***.
### Structure
* ClassPojo
* IClassPojoDao -> ClassPojoDaoImpl(has Pojos)
### Behaviour
1. Create PojoDaoImpl
   * -> create several Pojo and adds them into the list
2. PojoDaoImpl::getAllPojos() - iterate trough all elements   
3. Other methods of the DAO interfaces can be invoked. Like the Transfer object
### Source
* https://stackabuse.com/java-j2ee-design-patterns/#dataaccessobjectpattern
### Notes
* These objects often instantiate "SessionFactories" for this purpose and handle all of the logic behind communicating with the database.
* The standard practice is to create a DAO interface, followed by a concrete class implementing the interface and all methods defined in it.
* Looks very similar to the transfer object pattern.

---

## Web Service Broker

### Introduction
You want to provide access to one or more services using XML and web protocols.
### Structure
* ClassBusinessService
* WebServiceBroker(has/operates BusinessService) -> POJOBroker
* WebServiceBroker(has/operates BusinessService) -> SessionBeanJAXBroker
* WebServiceBroker(has/operates BusinessService) -> POJOJAXBroker
* EnpointProcessor(has WebServiceBroker)
### Behaviour
1. Create BusinessService
2. Create POJOBroker
3. Create SessionBeanJAXBroker
4. Create POJOJAXBroker
5. Create EndpointProcessor
6. EndpointProcessor::request - decide which broker to invoke next - depends on the incoming protocol
   * -> SessionBeanJAXBroker::doSomething
      * -> BusinessService::doSomething
### Source
* http://www.corej2eepatterns.com/WebServiceBroker.htm
### Notes
* The EnpointProcessor takes the request, extracts it and forwards it to the web broker.
* More complicated implementation will be with list of brokers that are accessed through lookup.
* ***Layer between the end-point and the business service which knows many protocols but uses only the apropriate one for communication between both sides***.
