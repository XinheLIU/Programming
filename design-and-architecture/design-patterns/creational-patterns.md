### Creational Patterns

Creational patternsdeal with the creation or cloning new objects.

Creational Patterns depends on the language to use. eg. JavaScript does not have classes, it encourages you to clone an object and expand \(called Prototype\) to meet the purpose of particular instances. Not all patterns are possible to use depending on the language.

#### Singleton

* Only one object of a class. 
* Provide Global Access to a class that is restricted to one instance 
* Count Instances or Use a UniqueInstance Flag to limit the creation
* Lazy Creation - getInstnce + private constructor 
* ```java
  Public class ExampleSingleton { // lazy construction   // the class variable is null if no instance is   // instantiated   Private static ExampleSingleton uniqueInstance = 
  null; 
  } 
  // lazy construction of the instance   Public static ExampleSingleton getInstance() { 
  Private ExampleSingleton() {
        ...
              if (uniqueInstance == null) {
                    uniqueInstance
  ExampleSingleton();
              }
        Return uniqueInstance;
        }
        ...
  }
  ```

#### Factory Method

* The Factory Methods is declared by Creator abstractly, concrete creators are obliged to implement
* the Method in concrete creator only operated on the general product, never concrete products
* separate creation from other behaviors

* ![](/assets/Factory Method.png)



#### Abstract Factory





