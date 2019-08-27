
# Scala
Authors: Daniel Hinojosa

## What is Scala?

* Multi-paradigm programming language
  * Functional
    * Every function is an object and a value
    * Capable of anonymous and higher order functions
  * Object Oriented
    * Everything can considered an object, including integers, floats
    * Inheritance through mixins and subclasses

## Statically Typed Language

* Every value contains a type
* Expressive type system
* Types can be inferred
  * Cleaner
  * Less Physical Typing

<hr/>

## What are the advantages of Scala?

* JVM Based
* Highly Productive Language
* Expressive Language
* Concise Language
  * Type Inference
  * No `return` required
  * No semicolons (`;`) required
  * All methods `public` by default
  * Above all, highly functional!

<hr/>

## What are the disadvantages of Scala
* Higher learning curve, until function programming becomes more prominent
* Non-backwards compatibility
  * Below you see that there is a library version (2.5.2) 
    and there is a the scala version that it 
    is compiled for (2.12 & 2.11). Spark has the same versioning scheme.
    
![Backwards Compatibility](../images/non-backwards-compatibility.png)    

<hr/>

## `println` for printing


```scala
println("Scala is Awesome")
```


    Intitializing Scala interpreter ...



    Spark Web UI available at http://6e39fc3e73c4:4040
    SparkContext available as 'sc' (version = 2.4.3, master = local[*], app id = local-1562039360891)
    SparkSession available as 'spark'
    


    Scala is Awesome
    

<hr/>

## Creating classes
* The property names (e.g. `firstName`) come first before the type (e.g. `String`)
* The signature `(firstName:String, lastName:String, department:Department)` is the primary constructor
* The signature `(firstName:String, lastName:String, department:Department)` also corresponds to the fields inside the object
* Notice there is no `public` keyword
* Notice that one of the constructor parameters is of `Department` and department is declared _after_ `Employee`
* `Department` has one property `name` of type `String`



```scala
class Employee(firstName:String, lastName:String, department:Department)
class Department(name:String)
```




    defined class Employee
    defined class Department
    



<hr/>

## Instantiating the classes

In Scala we can instantiate the `Employee` using the `new` keyword and filling in the properties/fields


```scala
val emp = new Employee("Bertrand", "Russell", new Department("Toys"))
```




    emp: Employee = Employee@586acde4
    



<hr/> 

## Running the classes

Classes can be run as application by creating an `object` that contains a `main` method. 
The `main` method:
 * Accepts arguments as an `Array[String]` which is a Scala object that represents a Java array
 * `def` is method
 * `main` is the name of the method
 * `args` is the name of the `Array[String]` that can be referenced from with the `main` method
 * Housed inside an `object`

To compile, put these classes in either one file, or multiple files and compile with `scalac`. For example, if we place these classes in a file called _Entities.scala_ we would compile with the following console command.

  `scalac Entities.scala`
  
To run we would run the class using the command, keep in mind that `MyRunner` is the construct that we run.

  `scala MyRunner`


```scala
class Employee(firstName:String, lastName:String, department:Department)
class Department(name:String)
object MyRunner {
   def main(args:Array[String]) {
        println("Hello, Scala")
   }
}
```




    defined class Employee
    defined class Department
    defined object MyRunner
    



### So, what are those funky square brackets?

* Whenever you see `[` and `]` surrounding the type, that is the _parameterized type_
* The parameterized type is what a type of collection contains.
* For example, you just witnessed `Array[String]` which is _An Array of String_
* You will see tons of them in this class and with different containers / collections
* Some examples you will see are:
  * `List[A]`, where `A` will be some type
  * `Set[A]`, where `A` will be some type
  * `Map[K,V]` where `K` and `V` will be some possibly different types
  * `Option[A]` where `A` is will be some type
* For Spark, you will see types likes 
  * `Dataset[A]` where `A` will be some type 


## About `object`

* object is a singleton
* It is how we avoid `static`
* Scala doesn’t have the `static` keyword
* Reminder: All methods are public by default

Therefore the following is the same as `public static void main(String[] args)` in Java.


```scala
object MyRunner {
   def main(args:Array[String]) {
        println("Hello, Scala")
   }
}
```




    defined object MyRunner
    



## Using `App`

* Turns `object` into an executable program
* No need for a `main` method
* `args` can be referenced to the `Array[String]` of arguments


```scala
object MyRunner extends App {
  println("Hello, Scala")
}
```




    defined object MyRunner
    



<hr/>

## Packaging the classes

All classed can be placed into a `package` much like in java to organize classes:

```
package com.xyzcorp
class Employee(firstName:String, lastName:String, department:Department)
class Department(name:String)
object MyRunner {
   def main(args:Array[String]) {
        println("Hello, Scala")
   }
}
```

NOTE: We cannot run this in Jupyter notebook since it cannot recognize the `package`

<hr/>

## Packaging with containment

Packages in Scala can be done in a hierarchical manner. Notice that `xyzcorp` and `abccorp` are both a `package` and are embedded with in the `com` package.  That means that the `Employee` and `Department` classes are in the `com.xyzcorp` package and the `MyRunner` class is in the `com.abccorp` package.

```
package com {
  package xyzcorp {
    class Employee(firstName:String, lastName:String, department:Department)
    class Department(name:String)
  }
  package abccorp {
    object MyRunner {
      def main(args:Array[String]) {
        println("Hello, Scala")
      }
    }
  }
}
```

NOTE: We cannot run this in Jupyter notebook since it cannot recognize the package

## Quick Introduction to Collections

* We will cover Collections in it's own section, but for now, know some of the basics
* A `List` will be an ordered, indexed collection.


```scala
val list = List("Foo", "Bar", "Baz")
```

* A `Set` is an undordered collection with no duplicates


```scala
val set = Set(10, 40, 50, 30, 50)
```


    Intitializing Scala interpreter ...



    Spark Web UI available at http://fb98a64ea0b9:4042
    SparkContext available as 'sc' (version = 2.4.3, master = local[*], app id = local-1562351903636)
    SparkSession available as 'spark'
    





    set: scala.collection.immutable.Set[Int] = Set(10, 40, 50, 30)
    



* A `Map` is a collection of key and value pairs with easy lookup 
* The `->` makes a pair and all will be revealed when discussing collections


```scala
val map = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
```




    map: scala.collection.immutable.Map[Int,String] = Map(1 -> One, 2 -> Two, 3 -> Three)
    


