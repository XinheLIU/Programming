### Behavior Patterns

Behavioural patternsfocus on how objects distribute work, and describe how each object does a single cohesive function. Behavioural patterns also focus on how independent objects work towards a common goal. It also focus on the interaction with the system

#### Template Method Pattern

* defines an alrogrithms steps generally, concerned with the assignment of responsibilities
* Common parts on a templates, different parts as abstract method, when there is a change in algorithm, we only need to change one place
  * "final" in Java - cannot be overwritten by other places

#### Chain of Responsibilities Pattern

* Sequence of Handlers
  * ![](/assets/ChainofResponsibilities.png)
* decouples the sender and receiver by giving more than object a change
* used for filtering, classify, etc
* ![](/assets/ChainOfResponsibilities_UML.png) 

#### State Pattern

* Objects Change behavior when their current state changes
* used when need to change internal state at run time or simplify methods with long conditions
* ![](/assets/State.png)

#### Command Pattern

* encapsulates a request as an object
* invoker is an object invokes the command objects to complete whatever task it is suppose to do
* ![](/assets/Command.png)
* Place commands in a queue - can redo or undo
* ![](/assets/Command_UML.png)
* easy to add or modify functionalities
* allows the logic to be pulled from the interface

#### Observer Pattern

* A Subject keeps a list of observers. Observers reply on the subject to inform them of changes to the state of the object. 
* Subject superclass could also have subclasses implement the Observer interface. 
* ![](/assets/Observer.png)
* ![](/assets/Observer_UML.png)

#### 

#### Mediator Pattern

* Pairwise interactions become hard to matintain
* A centralized mediator to interact with objects, manage interactions
* ![](/assets/Mediator.png)
* Could be implemented as an observer pattern where each colleague is a subclass of observable class

#### 

#### Model-View-Controller \(MVC\) Patterm

* for data-security
* model : keeps important data, mey be updated, referenced\(entity object\)
* view: page that user see, based on interaction with the model\(boundary object\)
* controller: business logic lives. Users may submit and get information\(control object\)
* uses the separation of concerns 
* ![](/assets/MVC.png)



