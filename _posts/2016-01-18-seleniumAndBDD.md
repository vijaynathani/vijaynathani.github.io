---
layout: post
title: BDD with Selenium by Testers
date: 2016-01-18
---
I conducted a training on BDD and Selenium in Chennai. The participants wanted to used Cucumber to describe their tests and they were writing the tests using Selenium in Java.
Even though I conducted this training, I found following issues with this approach:

* The tests were being written mostly by testers. Testing business domain functionality by writing tests in Selenium is extremely tedious, slow, error-prone and almost unmaintainable. Yet I see this smell in many projects. While developing, everyone is in a hurry; so TDD (test driven development) is skipped. After the project is done, some manager wants automated tests. Testers are hired. These testers cannot write tests in Java at Unit level (function and class level); so they are told to write tests using Selenium. Just because something is cheap does not mean that is useful.
* It would have been much better to use Groovy and Geb instead of Java and Selenium Java library. The code would have been more compact, readable and maintainable.
* Some participants were using excel sheets to pass the data. Most of the time data should be present in .feature file of Cucumber, not is separate excel sheets. Keeping data in separate excel sheet is a smell that unnecessary data is being passed. This will make the test difficult to understand and maintain.


I would recommend

* BDD be used with ONLY along with TDD.
* Nearly 80% of tests should be at unit level. These should primarily test the business domain functionality.
* Less than 5% of the tests should be at UI (user interface like Selenium) level. These should primarily test the flow of information. BDD tool like Cucumber is usually not needed.
* Remaining about 15% tests can be written at integration level. BDD tool like Cucumber will be useful, if BDD is done during development.
* Prefer to write tests for Java code using Groovy. While using Groovy, prefer Geb libary to writing code directly against Selenium.

Happy BDDing.
