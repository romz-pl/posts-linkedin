# Modularization of legacy code

## Modular programming: What is it?

Modular programming, as defined by Wikipedia, is a method of computer programming that divides an IT system into separate, interchangeable modules, each of which has all the components necessary to perform a particular function. 


## What does the module contain?

+ The module consists of two components: the interface and the implementation. 
+ The functionality of the module is defined by its interface. 
+ The implementation of the module interface depends on how the module is used. 
+ Both the system user (client) and the person implementing the module (module provider) benefit greatly from splitting the module into interface and implementation. 


## What is legacy code?

Legacy code is an outdated program with the following characteristics 
+ It is about 30 years old, with a spaghetti-like code structure. 
+ It lacks documentation or has outdated, inadequate documentation. 
+ The people who worked on it are either no longer with the company or have been reassigned to other projects. 
+ There is a lack of comprehensive information about how the system works and its underlying assumptions. 


## How do you get better code quality?

If new functionality can be added to the system quickly, cheaply, and without breaking existing functionality, we say that the code quality is good. Decomposing the system into modules, or implementing code modularization, is one (and possibly the only) way to improve the quality of legacy code. 


## The result of modularization is what?

+ As a result of modularization, code is divided into libraries that contain logically separate pieces of code. 
+ The resulting libraries can be autonomous and independent of each other. 
+ Suppose the libraries are viewed as nodes in a graph, and the connections between the libraries are viewed as edges in the graph. Then, after modularization, the libraries form a directed dependency graph, i.e., the graph without cycles. 
+ When the dependency graph is cycle-free, the system is easier to maintain and extend. 
+ Strong dependencies between libraries are indicated by a cycle in the trace graph. 
+ Cycles in the trace graph should be avoided at all costs. 


## Why is modularization beneficial?

+ The code after modularization is much easier to maintain because the process breaks the code into smaller, often independent components that are easier to review. 
+ Modularization makes it easier to develop the code and add new features, mainly because it divides the code into libraries. 
+ It is easier to re-code the feature after modularization because the process of dividing the code into libraries provides relevant information about the dependencies in the code, which is very helpful when making decisions about future changes to the code. 
+ Modularization reduces the cost of onboarding a new employee. Because it takes less time for a new employee to become familiar with the system, costs are reduced. 
+ Modularization divides the system into sections, allowing the system to be sold separately. 
+ A modular system allows you to divide the group of programmers who maintain the whole system into teams working on a particular library. Dividing the group into teams allows them to gain a deeper understanding of the maintained part of the system. 
+ Modularization makes it possible to focus on tests within a library, which simplifies test maintenance and reduces development costs. 
+ Modularization removes unnecessary dependencies between files, usually caused by over-inclusion of files using the preprocessor directive. Removing these unnecessary dependencies reduces compilation and build time. 


## What are the assumptions of modularization?

+ The basic assumption of modularization is that the system has identical functionality before and after modularization, and that interfaces in classes have not been changed. It is only after modularization that steps are taken to change or refactor the code. Dividing the modernization (reconstruction) of the code into two stages (where the first stage is modularization) allows us to avoid introducing errors to a greater extent. 
+ It is preferable to integrate the modularized code with the continuous integration system used to build and test the code. 
+ Modularization does not block simultaneous development of the system. 
+ The modularization process is significantly impeded if global variables or singletons are used in the implementation, which introduce strict global dependencies between classes.


## How is modularization performed?

+ Modularization is performed on the existing system, i.e. the alternative version of the system is not built. 
+ The first stage of modularization is to define the most basic classes that will create a library (module). Once the module has been created, it is activated and used in the system. 
+ The next modularization steps involve selecting classes that use only modularized libraries and integrating them into the system. Thus the system is transformed in a modularized systematic way. 


## References 
+ M. Fowler, Refactoring: Improving the Design of Existing Code, 2018
+ A. Volkhover, Become an Awesome Software Architect: Book 1: Foundation, 2019
+ J. F. F. Dooley, Software Development, Design and Coding: With Patterns, Debugging, Unit Testing, and Refactoring, 2017
+ R. N. Taylor, N. Medvidovic, E. M. Dashofy, Software Architecture: Foundations, Theory, and Practice, 2009
+ R. C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship, 2008
+ K. Henney, 97 Things Every Programmer Should Know: Collective Wisdom From The Experts, 2010
+ R. S. Pressman, B. Maxim, Software Engineering: A Practitioner's Approach, 2014
+ J. Humble, D. Farley, Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation, 2010
+ P. Smith, Software Build Systems: Principles and Experience, 2011
+ I. Crnkovic, M. Larsson, Building Reliable Component-Based Software Systems, 2002
+ C. Szyperski, Component Software: Beyond Object-Oriented Programming, 2002
+ K.-K. Lau, Component-Based Software Development: Case Studies, 2004
+ M. Feathers, Working Effectively with Legacy Code, 2004




```
#Cpp
#SoftwareEngineering
#LegacyCode
#Refactoring
#CleanCode
```

![Modularization of legacy code](./img.png)
