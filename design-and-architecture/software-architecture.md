## Software Architecture

Software architectureis the fundamental design of an entire software system. It defines what elements are included in the system, what function each element has, and how each element relates to one another. It is the big picture or overall structure of the whole system—how everything works together.

Key factors for consideration

* Purpose of the system
* Audience or Users of the system
* qualities that are of most importance to users
* Where the system run

It aims to build a system that easier to maintain, reuse and adapt. Improve the productivity of team, evolution for software, enhance quality in the software

#### Stakeholders

The people who are an interest of software at hand. The aim is to benefit them in some way.

### Kruchten's 4+1 View Model

* **Logical View**: focus on functionality \(what a system does to satisfy the purpose the client desires\)
  * functional requirements
* **Process View**: how well the software executes, using the characteristics like the efficiency of the system or interaction of subprocesses. Performance and Scalability
  * non-functional requirements
* **Development View**: implementation considerations such as the structure of the software. \( Programming languages of the system heavily influence this structure and therefore places constraints on the development\)
  * details of development
  * scheduling, budgets, work assignments
  * hierarchical software structure and project management
* **Physical View**: The software will have physical components that interact and need to be deployed. How deployment affects the system works
  * above three nodes need to be mapped to different nodes of hardware of the running system
* **Scenarios**: Outline uses cases or tasks required by the end users. Help to detail the four views. 
  * each scenario has a script to describe the sequence of interactions between objects and processes.

### Relationship to Organizational Structure

#### Conway's Law

* A software system will tend to take a form that is congruous to the organization that produced it
* its always a good practice the architecture design first the group the teams accordingly

#### Product Line or Product Family

* one way to promote code-reuse is to group products together
* product line
  * lower development costs per product
  * user experience similar
  * reduce time to market
* should examine
  * commonalities
  * variations
  * product specifics
  * ![](/assets/Product-Line.png)
* The development separate into
  * Domain Engineering - develop commonalities and variations \("infrastructure"\)
    * Responsible for **Reference Architecture**
      * designed with the needs of the software
      * capability of variation \(allow different features\)
    * techniques to realize variations
      * Adaptation Technique. 
        * A component has one implementation, but supplies interface to change or add on it. 
        * can be adapted through settings in a configuration file, but adding new methods or overriding existing ones
        * ![](/assets/Adaptation.png)
      * Replacement Technique 
        * A default component can be replaced with alternatives to realize variations. \(default can be gap\)
        * ![](/assets/Replacement.png)
      * Extension Technique
        * a common interface is provided for all variations of a systems
        * called extensions, add-ons or plugins. 
        * ![](/assets/Extension.png)
  * Application Engineering - Actual Development of the Product. \("instantiating" the product\)
    * to **realize variations**



