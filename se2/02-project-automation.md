# Project Automation

**Goals**

You can
- [x] explain reasons for build automation
- [x] explain concepts of build automation
- [x] explain continuous integration (CI) as SE discipline

**Definition**
- [Build automation](http://en.wikipedia.org/wiki/Build_automation) is the process of automating the creation of a software build instead of manually invoking the compiler.
- [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) (CI) means having an automated process build your software continuously as developers check in code. In addition to performing compile steps, this is also a great opportunity to run automated *code quality checks*.
- [Continuous Delivery](https://en.wikipedia.org/wiki/Continuous_delivery) (CD) is a combination of the previous steps where the software builds are also deployed to a system, ensuring that the software can be reliably released at any time.


## 1. Build automation

### 1.1. Why using build automation? 

**Developer Activities**
* Compile
* Unit test
* Package / bundle
* Integration test
* Deploy

In small projects, developers will often manually invoke the build process. This is not practical for larger projects, where it is very hard to keep track of what needs to be built, in what sequence and what dependencies there are in the building process. Using an automation tools allows the build process to be more consistent.

Advantages:
* Reduce the repetitive tasks
* A necessary pre-condition for continuous integration and continuous testing
* Improve product quality
* Minimize "bad builds"
* Independence of any IDE
* Reproducable results
* Have history of builds and releases in order to investigate issues
* Save time and money - because of the reasons listed above.

### 1.2. Build Script

**:white_check_mark: Pros**

* **Automated**, non-interactive process
* Repeatable
* Independent of your IDE
* Time-consuming taks can be scheduled

**:x: Cons**

* Automated, **non-interactive** process
* Maintenance and extension is difficult
* Most likely plattform-dependent (.sh, .bat)

---
**Wish list**
* Single command builds (CRISP)
  - Complete
  - Repeatable
  - Informative
  - Schedulable
  - Portable
* Flexibility (run individual tasks)
* Performance
* Extensibility

> Solution => Build Tool

### 1.3. Build Tool

specialized system that manages the build process

features:
* Dependency mangaement
* Optimizaions
  * parallelization of build tasks
  * Incremental compilation (recompile changed sources)
  * Incremental builds (only run changed targets)
* Customization
  * LESS processing, js minification/optimization
  * Integration testing: server setup / teardown

#### 1.3.1. Imperative Build Tools

* Developer explicitly defines the DAG (Directed Acyclic Graph). 
* Targets are implemented using a scripting / programming language or a specialized domain-specific language (DSL).
* Usually rely on external dependency managers

**Examples**
* Make-family
  - GNU Make (C/C++) - first version developed in 1976 at Bell Labs
  - Jake (JavaScript)
  - MSBuild (.NET)
* 2000: Ant
  - Portable XML-based scripting language
* 2003: Rake

**:white_check_mark: Pros**

* very powerful and flexible

**:x: Cons**

* Build definitions tend to be complex and verbose (i.e. explicit compiler invocations)
* Difficult to reuse build logic
* "Copy-pase" is a common pattern

#### 1.3.2. Declarative Build Tools

Developer **declares** what he would like to have as the result.

**Examples**
- Apache Maven
- Gradle

**Apache Maven**

First prototype: 2001, Maven 1.0 launched in 2004

Concepts:
* Declarative (XML-based) - Developer describes the build results
* "Convention over configuration"
* Predefined lifecycles = DAG (compile, test, package, install, deploy)
* Predefined directory tree ==> consistent across project
* Automated dependency resolution

**:white_check_mark: Pros**

* More consise => shorter build-files
* Reusable build-logic (plugins)
* Automated dependency management

**:x: Cons**

* Less general and flexible than "imperative" tools
* Impose a somewhat rigid project/file structure