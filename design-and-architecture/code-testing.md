### Model Checking

* Systematic check of system;s state model in all its possible states
* check all various states of software to try and identify any errors, by simulating different events that would change the states and variables of software
  * deadlock: system cannot continue while two tasks are  waiting for some resource
* State Model: abstract state machine can be in one of any states
* Phase1: **modeling phase** - model description using the same programming languages as the system
  * sanity checks: check simple errors
* Phase2: **running phase**-how model conforms to the desired properties in the modeling phase
* Phase3: **Analyze Phase**. Check violations. \(counterexamples\) - model checkers should provide description of violations in the system, so to analyze how they occurred. 



