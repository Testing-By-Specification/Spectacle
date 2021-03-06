# Testing-By-Specification

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

Test-spec is a collection of general purpose Cucumber steps (implemented in Groovy).

By design, Gherkin features have dual purpose: 

* they are being a specification for some feature under development

* they are being a set of instructions for a functional test that could be executed automatically 

Test-spec focuses on improving the second part.


**Run examples**
```
  gradlew testspec -Dfeatures=features/Command.feature
  gradlew testspec -Dfeatures=features/Core.feature
  gradlew testspec -Dfeatures=features/Database.feature
  gradlew testspec -Dfeatures=features/Rest.feature
```

**Run examples: in-browser on different grids**
```
gradlew testspec -Dfeatures=features/web/WebSearch.feature -Dbrowser=firefox
gradlew testspec -Dfeatures=features/web/WebSearch.feature -Dbrowser=chrome
gradlew testspec -Dfeatures=features/web/WebSearch.feature -Dbrowser=localhost:chrome

gradlew testspec -Dfeatures=features/web/WebSearch.feature -Dbrowser=amazonfarm:anyOs-firefox
gradlew testspec -Dfeatures=features/web/WebSearch.feature -Dbrowser=saucelabs:Windows_7-chrome-101
```

## Before Running On Mac

```
   $ cd /project-dir/bin/
   $ xattr -d com.apple.quarantine chromedriver
```

## What does test-spec solve?

Traditionally, in large organizations software had been tested manually by dedicated QA teams.
While it has some merits, this approach suffers from serious limitations, 
main one is being - inability to speed up testing phase after a certain point. 
As application grows larger, it requires more time to perform manual testing on every release cycle.
To keep the quality of the product up, regression testing is required before each release.

One obvious solution to this situation is to hire more manual QA testers.
Beside the fact that it's expensive, after the team grows to a certain point, 
you'll start seeing diminishing returns on each added QA team member.
Even with more QAs hired, large applications still take considerable amount of time to test,
which prolongs release cycles. 

Another solution to this problem is automation of functional testing.
Here comes the dilemma though: test automation _is_ software development.
But your manual QA testers - as a rule - are not.  
Teams that came to decision to automate, implement it differently:

* some try to train QAs to become programmers

* others hire programmers to do automation

This is where Test-spec can help. Test-spec enabled QAs to automate functional test scenarios _without becoming "full-blown" programmers_. Of course it can also be used by developers, as it simply saves time that developers would spend otherwise on implementing Cucumber glue code.


## Functionality

Test-spec makes testing easier by implementing commonly used operation by encapsulating them into Cucumber steps.
Eventually test-spec will do:

* web testing:
    * entering values into input fields, 
    * clicking on web page element,
    * checking web page content
* making REST calls
* querying DB (to validate outcome of some operation)
* working with files
    * check content
    * create a files based on a template
* sending JMS messages
* execute external scripts
* execute user code as extension of the framework, 
* while still allowing users to create their own custom steps 
