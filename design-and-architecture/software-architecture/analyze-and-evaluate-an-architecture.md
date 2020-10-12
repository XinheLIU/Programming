### Quality Attributes

Modern systems need to be able to focus on a wide range of problems, not just technical issues. It should concern both **functional **and **non-functional **requirements.

It sets line for design patterns and principles in order to ensure conceptual **integrity **and **consistency** throughout.

Attributes:

#### From a development perspective

* Maintainability
  * system is capable of undergoing changes
* Reusability
* Flexibility
  * adapt to requirement change
* Testability
  * how easy it is to demonstrate errors through executable tests
* Modifiability
  * ability for system to cope with changes
* Conceptual Integrity
  * consistency

#### From a user perspective

* Availability
  * amount of time system is available 
  * measured by uptime \(recover from issues and errors\)
* Interoperability
  * understand communication and share with external systems
  * understand interface and exchange information
* Security
* Performance
  * throughput and latency in response to user commands and events
  * price per unit of performance
* Usability
  * functions can be learned and used by the users
  * easy for user to complete the task

Attributes should be objective and quantifiable.

There is no good or bad about architecture, the most important thing is appropriateness. Up-to-date detailed documentation of a system is very important. The documentation keeps a design cohesive.

#### Design process guidelines

* recognizing the importances of quality attributes and prioritizing them for each system being designed. Quality attributes should be kept up-to-date. Tradeoffs and details of how a system will meet the qualities should be noted
* Involving a technical lead. \(help to identify any implementations that may pose a challenge
* Taking a design approach from the perspective of different groups of stakeholders

#### **Structural rules to sure conceptual integrity**

* have well-designed subsystems that are assigned responsibilities based on design principles
* Having a consistent implementation of functions across the entire system
* Having a set of rules on how resources are used. \(Memory, bandwidth, threads that system have access to\)

### Analyzing and Evaluating

**Quality attribute scenarios** to measure the quality attributes

* **General Scenario**: used to characterize any system
* **Concrete Scenario**: used to characterize specific systems.

They both have

* Stimulus source
* Stimulus: condition that will cause a system to respond
* Environment: mode of system when it receives the stimulus. eg
  * normal
  * staring up
  * shutting down
  * recovering from failure for distributed computing system
* Artifact: Part of system that is affected by the stimulus.
  * system server
  * system process
* Response: how artifact will behave as a result of receiving the stimulus.eg
  * error handling
  * updating system logs
  * dispatching security alerts, 
  * changing the current environments
  * notify users
* A response measure: metric used to quantify the response so that the quality attribute can be measured. Should be quantitative and objective. eg.
  * probability of failure,
  * response time
  * repair time
  * average system load
  * time to restart

### Architecture Trade-off Analysis Method\(ATAM\)

From CMU. One way to implement scenarios in analysis and evaluation of the entire architecture.

Participants

* Evaluation Team
  * Designers. 
  * Peers. 
    * \(part of the project, not involved in design\)
  * Outsiders
* Project Decision Makers
  * project managers, clients, product owners, software architects, technical leads
* Architecture Stakeholders
  * who want the architecture to successfully address the business needs
    * end users, developers, support staff

Process

* business drivers identify a need or a problem
* business drivers and system architecture determine the quality attributes
* make design decitions
* combine these together to create quality attribute scenarios
* scenarios are analysed
  * trade-offs
  * sensitivity points
  * non-risk scenarios
  * risk scenarios
    * each categorized into "risk themes" 

![](/assets/ATAM.png)

Steps

1. Present the ATAM
   1. context, evaluations, expectations, procedures, outputs, addresses any concerns 
2. present the business drivers
   1. problems and goals
3. present the architecture
   1. time, cost, difficulties
4. identify the architectual approaches
   1. analyze the documentation and notes from presentations and ask questions
5. create quality attribute tree
   1. maps the **architecturally significant requirements\(ASR\)s** for each quality attribute.
   2. break down the overall utility of the system into quality attributes, which are refined into **attribute refinements. \(more specific\)**
   3. ![](/assets/quanlity attribute tree.png)
6. Analyze the architectural approaches
   1. using prioritized ASRs from utility tree, examine the architecture and determine how it addresses each ASR.
   2. identify **risk, non-risk scenarios, sensitivity points, trade-offs**
   3. reveals capability of the system and consequences of design decisions
7. Brainstorm and prioritize scenarios
   1. should have** good alignment **with utility tree
8. Re-analyze the architectural approaches
   1. recreate the utility tree using the top five to ten scenarios priortized in step 7.
9. present the results
   1. group risk scenarios together with risk themes. 



