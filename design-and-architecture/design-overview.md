Object Oriented Design is using objects to make your code **organized, flexible and reusable.**

### Design Overview

* Requirements - conditions and capabilities must be implemented, starting point of design
  * functional requirement-correctness
  * Nonfunctional requirements - reusability, flexibility and maintainability, speed, momory resources, efficiency
* Software development process
  * **Conceptual Design**
    * communicated through conceptual mock-ups, illustrates major **components **and connections, components **responsibilities **
    * component- a discrete part that has a particular role or function \(Responsibilities\). Usually can be implemented separately. 
    * Class, Responsibility Collaborator\(CRC\) : list out responsibilities and collaborators. Used in **prototyping and simulation. **
    * User Stories - As a, I want to\_, so that\_
  * **Technical Design**
    * specifies how responsibilities are met, detailed design of each components
    * Technical Diagrams - Specify components and connections 
  * Implementation
* Trade-off: to achieve a balance between quality attributes 
  * quality attributes: performance, convenience, security, maintainability, etc
  * Context and Consequence: eg. amount of data, data usage, speed
  * What is "good enough"
  * Redesign and Re-architecture

### Type of Objects

* **Entity Objects**: usually knows its own attributes, how to modify themselves and rules in how to do so. 
* **Boundary Objects**: Objects which sits at boundary between systems. Deals with another system - user, another software and internet. eg. Interface, User Interface
* **Control Objects**: responsible for coordination, objects that performs control on other objects. 

### Object-Oriented Modeling Principles

* Abstraction
  * Should follow the rule of least astonishment: essential attributes and behaviors/responsibilities should be captured with no surprises. 
* Encapsulation
  * ability to bundle data and behaviors together. 
  * ability to expose \(interface\)
  * ability to restrict access
  * data integrity and security: prevent data to be broken
  * changeable implementation \( implementation and interface separated\)
  * black box thinking to achieve and abstraction barrier
* Decomposition
  * combine parts/divide into parts.
  * "has a" relationship
  * **Association: **loose relationship of interaction between two objects \(not affecting existence\) 
  * **Aggregation: **"has a" relationship where the whole part belongs to another object, existence not affected
  * **Composition:  **strong "has a" relationship: existence of the object affect: part cannot exist without a whole
* Generalization
  * separate generalized and specialize 
  * Inheritance: "is a" relationship
    * Java does not support multiple inheritance\(but has interface inheritance\), C++ does \(may cause data ambiguity\) 
  * polymorphism

### Evaluation Standards

* Coupling and Cohesion
  * **Module: **program units containing classes and methods, system is a combination of various modules. A good design means all modules are easily connected and reusable
  * **Coupling:** if a module can be easily connected \(**loosely coupled vs. tightly coupled**\) to other modules
    * Degree: the number of connections between a module and others. Ideally small.
    * Ease: how obvious the connections are-should not need to understand implementation details
    * Flexibility: How interchangeable modules are. \(should easily be improved/extend/replace\)
  * **Cohesion**: clarity of responsibilities \(high cohesion vs low cohesion\). Should be encapsulated to a single purpose. 
    * should not need to break the encapsulation to under
* Separation of Concerns: all concerns/subproblems carefully considered and addressed separately
  * Use abstraction, encapsulation, decomposition, generalization
  * Modularity: allows programmers to reuse and build up individual classes without affecting others. 
* Information Hiding
  * rule of thumb: things might change -like implementation details, should be hidden
  * interface and encapsulation
  * access modifiers
* Conceptual Integrity: design and implementation should be consistent
  * communication
  * code review
  * design principles and **design patterns**
  * well-defined design or architecture
  * unifying concept
  * core group that accepts each commit to code base
* Generalization Principles
  * Inheritance: Liskov Substitution Principle: a subclass can replace a superclass if and only if, it does not change the functionality of superclass 
  * Consider using decomposition or inheritance 

### Useful Tool-UML\(unified Modeling Language\) Diagram

* UML Class Diagram
* UML Sequence Diagram
  * role, message, activation, actors\(people\)
  * “lifeline"
  * retun data
  * can contain other sequence diagram
  * loops and else
* UML State Diagram
  * state \(state name, variables, activities\)
  * Activities
    * Entry Activities, Exit activities, do activities
  * transitions
  * termination



