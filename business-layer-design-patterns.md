# Business Layer Design Pattern

## Business Delegate

### Introduction
The Business Delegate pattern is used to decouple the presentation layer from the business layer to minimize the number of requests between the client (presentation) and the business tiers.
### Structure
* IBusinessService -> ClassServiceA
* IBusinessService -> ClassServiceB
* ClassBusinessLookUp(operates with ServiceA, ServiceB)
* ClassBusinessDelegate (has BusinessLookUp, BusinessService)
* ClassClient (has BusinessDelegate)
### Behaviour
1. Create BusinessDelegate
   *-> Creates BusinessLookUp 
2. Set service to BusinessDelegate
3. Create Client
4. Invoke Client method process
   * -> BusinessDelegate::process
      * -> BusinessLookUp::getBusinessService (if-condition "servicetype")
         * <- return IBusinessService
      * -> IBusinessService::process();
### Source
* https://stackabuse.com/java-j2ee-design-patterns
### Notes
* Choose the apropriate service depend on the String "service type".
* Depend on the BusinessDelegate type state, which changes progressive, the corresponding service is used (returned).
   * ***The BusinessDelegate-type controlls the service selection.***
* Because of the if-conditon it looks simialr to the "Front Controller" pattern.

---

## Service Locator Pattern

### Introduction
A pattern often seen in Web Applications, the ***Service Locator pattern is used to decouple the Service Consumers and the concrete classes*** like DAO implementations.
### Structure
* IService -> ClassServiceA
* IService -> ClassServiceB
* ClassCache(has services)
* ClassInitialContext(operates with ServiceA, ServiceB)
* ClassLocator(has Cache, operates on InitialContext)
### Behaviour
1. Locator::getService
   * -> Cache::getService
       * <- return null - returns service if found, otherwie null.
   * -> if-condition false - furter process - return service if found otherwise process goes further.
   * -> Create InitialContext
   * -> InitialContext::lookup(serviceName)
       * <- return new IService - returns service if found otherwise null
   * -> Cache::getService(service)
   * ->return service
2. Service.execute()  
### Source
* https://stackabuse.com/java-j2ee-design-patterns
### Notes
* ***The pattern looks for the adequate service, saves it in cache storage to reduce the number of requests*** and therefore the strain on the server and provides the application with their instances.
* Gets services for some usage like invoking their "execute"-method.
   * On this process it is checked if it exists in cache, if not create and put it into cache for next time.

---

## Session Facade

### Introduction
You want to expose business components and services to remote clients.
### Structure
* IBusinessComponent -> ApplicationService
* IBusinessComponent -> BusinessObject
* IBusinessComponent -> DataAccessObject
* SessionFacade(has IBusinessComponents)
### Behaviour
1. Creates ApplicationService
2. Creates BusinessObject
3. Creates DataAccessObject
4. Creates SessionFacade with the objects
5. SessionFacade::getApplicationServicePropertyX
6. SessionFacade::getBusinessObjectPropertyY
7. SessionFacade::getDataAccessObjectZ
### Source
* http://www.corej2eepatterns.com/SessionFacade.htm
### Notes
* ***Facade pattern on enterprise level where the whole backend processing is behind the SessionFacade.***
* The implementation can be created with lookup/dispatcher/delegate instead of simple wrapping.

---

## Transfer Object

### Introduction
This pattern is used to transfer objects with lots of fields and parameters in one go. The Transfer Object pattern employs new objects, ***used only for transfer purposes***, usually passed to the DAO.
### Structure
* ClassTrasferPojo
* ClassBusinessObject(has TrasferPojos)
### Behaviour
1. Create BusinessObject
   * -> creates several TrasferPojo and adds them into the list
2. BusinessObject::getAllTrasferPojos() - iterate trough all elements
3. Change property - BusinessObject::getAllTrasferPojos().get(0).set("something")
4. BusinessObject::updateTrasferPojo - same as the step before but via the FacedeObject.
5. BusinessObject::getTrasferPojo(index) - for print purposes
### Source
* https://stackabuse.com/java-j2ee-design-patterns
### Notes
* ***These objects are serializable POJOs. They have fields, their respective getters and setters, and no other logic.***
