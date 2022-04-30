---
layout: post
title: Decorator Pattern
published: false
---

>Decorators are used to add new behavior to an object, **dynamically**, **at runtime**, without changing the underlying code.

1. Creating a subclass is how you extend the functionality of your code (i.e. add new behavior) at compile time
2. Using decorators is how you extend the functionality of your code at runtime

Say you want to write a logger. It takes a message and outputs it to one of the following targets - cmd, file, email, db. 

The first solution that would come to anybody's mind is to create a Logger interface and write four classes that implement it - 
* Logger
    * CmdLogger
    * FileLogger
    * EmailLogger
    * DbLogger

Suddenly a wild new expectation appears. Before writing the message, your system should convert it to one of the following formats - json, xml or yaml. And this doesn't have to be an expectation that arises in the future, it can be present from the get-go itself. In either case, the most obvious solution that comes to mind is subclassing each of the above classes-

* Logger
    * CmdLogger
        * CmdJsonLogger
        * CmdXmlLogger
        * CmdYamlLogger
    * FileLogger
        * FileJsonLogger
        * FileXmlLogger
        * CmdYamlLogger
    * EmailLogger
        * EmailJsonLogger
        * EmailXmlLogger
        * EmailYamlLogger
    * DbLogger
        * DbJsonLogger
        * DbXmlLogger
        * DbYamlLogger


Why is this not a good solution?

Class Explosion - What if you had ten targets and five output formats? Would you have written 10x5=50 classes?

But that's a logictical problem. The core issue lies deeper. 

Core issue - Your class structure does not fundamentally mirror the structure of the problem. 

 
 