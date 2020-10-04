# Presentation Layer Design Patterns

## Intercepting Filter

### Introduction
**Post and pre request processing** is done within the filter.
The exist in the form of Filter Chain include multiple filters, or simply exist as one Filter.
### Structure
* IFilter -> ClassFilter1
* IFilter -> ClassFilter2
* ClassTarget "Request"
* FilterChain(has filters, Target)
* FilterManger(has FilterChain)
* Client(has FilterManger)
### Behaviour
1. Create FilterManager with new Target, creates FilterChain in constructor.
2. Adding new Filter to the FilterChain of the FilterManager
3. Crate Client and set the FilterManger.
4. Client::sendsReqest -> FilterManager::filterRequest -> FilterChain::execite (forEachFilter::execute; target::execute)
### Source
* https://stackabuse.com/java-j2ee-design-patterns
### Notes
* Nevertheless, they run checks on authorization, authentication, supported browsers, whether the request path violates any constraints and restrictions etc.

---

## Front Controller

### Introduction
Upon sending a request, the Front Controller is the first controller it reaches.
Based on the request, it decides which controller is the most adequate to handle it, after which it passes the request to the chosen controller.
### Structure
* ClassMainView
* ClassSecondView
* ClassDispatcher(has both views)
* FrontController(has ClassDispatcher)
### Behaviour
1. Create FrontController
   * -> creates its Dispacher
      * -> created its both views
2. Invoke the method FrontController::dispatchRequest 
   * -> Dispacher::dispatch (if-condition) 
      * -> ClassMainView::showView or ClassSecondView::showView
### Source
* https://stackabuse.com/java-j2ee-design-patterns
### Notes
* The Front Controller is most often used in Web Applications in the form of a Dispatcher Servlet.
* The **if-condition** does do the **dispaching** by its evaluation.

---

## View Helper

### Introduction
The View Helper pattern separates the static view from the dynamic processing such as JSPs based on the business model data.
### Structure
* ClassModel
* ClassViewHelper(has{adapts} Model)
* ClassViewHelper -> ClassJavaBean
* ClassViewHelper -> ClassCustomTag
* ClassViewHelper -> ClassTagFile
* ClassView(has ViewHelper)
* ClassClient(has ClassView)
### Behaviour
* Create Model
* Create JavaBean with the Model
* Create CustomTag with the Model
* Create TagFile with the Model
* Create View with List of Helpers with the objects.
* For given view component check the Helper and adjust the content from the model.
   * -> .i.e. CustomTag::processing("<fancy>SomeTest</fancy>") 
      * -> Model::getName
   * <- ("<bold>John Doe</bold>")
### Source
* https://www.oreilly.com/library/view/spring-5-design/9781788299459/612c5796-5133-4742-98c9-6679457eb481.xhtml
* https://sites.google.com/a/sanjeevonline.com/technology/tutorials/corej2eepatterns/presentation-tier-patterns/view-helper
### Notes
* Many exampels were related to JSP custom tag processing.
* After recognition of the concrete processing class based on the ViewHelper the processing of the dynamic conntent is done.

---

## Composite Entity

### Introduction
The Composite Entity pattern represents a graph of objects, which when updated, triggers an update for all the dependent entities in the graph.
### Structure
* ClassModel1
* ClassModel2
* ClassCoarseGrained(has Model 1 and 2)
* ClassCompositeEntity(has CoarseGrained)
* Client(has CompositeEntity)
### Behaviour
1. Create Client c
   * -> Creates CompositeEntity 
      * -> CoarseGrainedObject 
         * ->ClassModel1
            * ->ClassModel2
2. c.setData("model1Data", "model2Data")
   * -> CompositeEntity::setData
      * -> CoarseGrained::setData
         * -> Model1::setData, Model2::setData
3. c.print()		 
   * -> CompositeEntity::getData
      * -> CoarseGrained::getData
         * <- return String[]{Model1::getProperty, Model2::getProperty}
### Source
* https://stackabuse.com/java-j2ee-design-patterns
### Notes
* This pattern bounds the dependend entities and executes some operation on them in the same step like:
   * writing to them.
   * reading from them.
* Poor flexibility when exending the number of the entities, because the data provider classes have to be modifed.
