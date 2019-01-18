# Overview - Pragmatic Unit Testing in Java 8 with JUnit

[Pragmatic Unit Testing in Java 8 with JUnit](https://pragprog.com/book/utj2/pragmatic-unit-testing-in-java-8-with-junit) was written by Jeff Langr with Andy Hunt and Dave Thomas. 



In this book, the authors intentions are to demonstrate that unit tests are quite simple; the real problems that complicate unit testing and introduce expensive complexity, are a result of poorly-designed, untestable code. 

Unit-testing has many benefits, but also requires discipline, concentration, and some extra effort overall. This book helps developers that are new to unit-testing or that were holding out because of those obstacles. The authors gently guide the reader using handy step-by-step instructions. You will discover pragmatic tips which will direct you to clean, easy-to-maintain, loosely coupled, and reusable APIs, that won’t damage your and co-developers’ brain.

Furthermore, veteran developers that are already test-infected and are using unit testing in their everyday work, can learn about mnemonics the authors suggest. They can also see how to organize their tests in tricky test scenarios.

If you agree with the authors guidelines (which we did) then this is a very good book to recommend it to your team. In the end you will all profit by establishing the same standards about more robust, easier to maintain and extendable code. We've got no doubt at all, that everyone would find a favorite section about unit testing in this book.



__Overview__

The first part of the book is a presentation of JUnit principles and gets the reader started if they are not familiar with testing.

Later, in the second part the author is giving real examples and reasons how to structure and organize your thoughts in order to write better tests. Experienced developers will find the section with helpful acronyms very interesting, a practical way to remember how to design quality tests.

The third part addresses more complicated examples and simplifies them through refactoring and removing complexity through mocking objects.

In the last part context tests are created in, such as test driven development (TDD) principles, databases, multithreading and working with tests in a project team.



__Content__

__Introduction__

The author quickly summarizes that testing matters, because it's an integral fundamental part of coding nowadays.

__Part 1: Unit-Testing Foundations__

Simple examples are demonstrated to get the reader started and how to best organize the thoughts of what to test. 

Chapter 1:  Building Your First JUnit

At first the author describes all the different reasons why it's important to automate tests. Primarily for faster feedback and to document what your code does.

A good practice of test-driven development (TDD) to avoid bad, costly assumptions, is to start on failing your tests, to prove that they really are doing something.



Chapter 2:  Getting Real with JUnit

This part is focusing more to understand what exactly to test and how exactly to structure your test code with the original, -classic-style version of JUnit. A starting point what to test is to look at loops, if statement, and complex conditionals. After that, consider data variants and how they would affect evaluation of the conditionals in the code.

Chapter 3:  Digging Deeper into JUnit Assertions

This chapter shows a newer way, more expressive style, known as Junit's Hamcrest assertions which will follow in the rest parts of the book. The idea behind this approach is to assertThat Something Is Equal To Another Something. The first argument of assertThat() static method is the actual expression, the value we want to verify and the second argument is a matcher. JUnit Hamcrest matchers let you:

Verify the type of an object
Verify that two object references represent the same instance
Combine multiple matchers, requiring that all or any of the matchers succeed
Verify that a collection contains or matches an element
Verify that a collection contains all of several items
Verify that all elements in a collection conform to a matcher
The next step is to get comfortable how they work.

Chapter 4:  Organizing Your Tests

Follow with a (AAA) scenario -test case- for better structure of JUnit's tests with the Hamcrest approach:

Arrange - First, we need to set up the state in order to do anything in the test.
Act -On-Execute the code we are trying to verify.

Assert - Compares the actual result with the expected value.





Give consistent & meaningful names to your tests which would test behavior and NOT methods.

Here are some hints to tell stories with your names and code:

doingSomeOperationThaGeneratesSomeResult
someResultOccursUnderSomeCondition


Examples of the ATM domain:





Another way is to test with the given-when-then naming known as BDD (Behavior Driven Development).

givenSomeContextWhenDoingSomeBehaviorThenSomeResultOccurs - if this seems too long for you, then try the next one.
whenDoingSomeBehaviorThenSomeResultOccurs


__Part 2: Mastering Manic Mnemonics__
The author suggests to optimize when the following problems shows up:

Tests that make little sense to follow.
Tests that fail sporadically.
Tests that don't prove anything.
Tests that don't sufficiently cover.
Small changes, break lots of tests.
Convoluted tests that jump through numerous setup hoops.
This section focuses on a series of mnemonics, a simple guideline to help the reader build  right & correct unit tests.

Chapter 5:  FIRST Properties of Good Tests
First, how important is to write unit tests:

[F]ast - A test should take few milliseconds at least to execute.
[I]solated - Run one test at any time, in any order. Unit tests don't depend on other unit tests.

[R]epeatable - Return the same results each time you run them.
[S]elf-validating -Unit tests aren't tests, unless they assert that things went as expected.
[T]imely - Make unit test on time, don't skip or procrastinate.
Chapter 6:  What to Test: The  Right-BICEP
The Right-BICEP provides hints to ask the right questions about what to test:

Right - Write a test about the happy expected behavior.
[B]oundary Conditions - Write one test for every boundary condition.
[I]nverse Relationships - Call the methods in different order and check if you got the expected behavior.
[C]ross Checking - Look & check different parts of code/methods to verify the expected values.
[E]rror Conditions - Whenever there is a happy path, there is an unhappy path. Write tests that force errors to occur. Possible error scenarios could be ( running out of memory, sending email fails, network availability, etc)
[P]erformance -  Run performance tests separately and enough times from fast unit tests. Use tools for unit-level performance measurement.
Chapter 7: Boundary Conditions: The CORRECT Way
 How to write correct boundary conditions. You shouldn't only test the happy path in your application but also consider all the different ways your code can fail.



[C]onformance - Does the value conform to an expected format? 

- Validating formatted string data such as email addresses, phone numbers, account numbers and filenames might involve a lot of rules. Focus on the rules for each report data or complex structures data.

[O]rdering - Is the set of values ordered or unordered as appropriate? 

- After sorting objects, check if an element is in the right ascending/descending order as expected.

[R]ange - Is the expected value within reasonable minimum or maximum values?

- Determine what invariants exist for the implementation specifics. In case of array, the tracked size of the array must match the count of non-null values, etc.

[R]eference - Does the code reference anything external that is not of direct control of the code? 

- Consider references outside its scope, external dependencies and they change the state that occur as a result.

[E]xistence - Does the value exist? 

- Make sure that nothing breaks when testing with plenty of zeros, nulls, empty strings, and other trappings.

[C]ardinality - Are there enough values? 

- Tests should cover conditions of 0, 1, and N elements.

[T]ime - Is everything happening in the right order or time? 

- Consider timezones, threads access the same object at the same time. Guaranteed failure is to write tests that depend on the system clock, etc.



__Part 3: The Bigger Design Picture__

A good practice that would lead the quality of code to clarity, conciseness, flexibility in design to minimize the maintenance and maximize understanding is certainly the refactoring. 

Chapter 8:  Refactoring to Cleaner Code
Principles of refactoring:

Rename -  whether it is a class, method, or variable of any sort. Good names imply clarity in code.
Extracting duplication - occurrences of small bits of code to a single method.
Extract method - isolate the complexity of the assignment by extracting it to separate method.
Find better homes for methods - move them to classes that are relevant.
Move private methods - to a new class and use a public behavior.
Here is an example code from the book, before & after refactoring:



Chapter 9: Bigger Design Issues
Someone would claim that after refactoring the above mentioned example, the time is quadrupled executing the matches() method. The answer is:  As long as the performance isn't an immediate problem, then invest in keeping the code clean instead of wasting time with premature optimization efforts. 



What is the problem with the above new approach after refactoring?

The answer is:  The above solution violates the Single Responsibility Principle (SRP) of object oriented design which tells that there should be just one reason why a class changes. Refactor more and more, as long as there is no object oriented design principle violated. One hint is to define the different responsibilities that the class  has and split them in different new classes.

Any idea how exactly to refactor and re-implement the above approach?

Well, let's define the different responsibilities and figure out how can be changed. The class Profile has two responsibilities:

Tracks information about a profile. 
Determines whether and to what extents a set of criteria matches a profile.
So, the author splits the two responsibilities, and creates a second class named MatchSet which allows to isolate the code related to matching. The Profile code from which it came gets simpler as well. After moving the related code to the new class, make sure that there are no other side effects in the code and the objects have a purpose in the class. In this case, a Profile doesn’t have a single score; it only has a score in conjunction with an attempt to match on criteria. So the score is moved to MatchSet class. In the next step, the author realizes that the way that handles the answers is not the best possible. He decides to isolate the storage of answers to a class named AnswerCollection. To conclude, the way to go is by analyzing the potential scenarios, refactor incrementally, and run the tests with each small change.

Chapter 10: Bigger Design Issues
Using mocks to break dependencies:

Replace troublesome behavior with stubs - returning hard coded value for the testing purposes
Use dependency injection - pass the stub to a ClassName instance or inject it via a constructor on the ClassName.
Other ways of injection - use setters instead of constructor, or override factory methods, or use tools for that purpose.


The next step would be to transform the created stub into a mock pattern known as when(...).thenReturn(...) that introduces a single-line act, and a single assert. Mocks are useful when it comes to write more than a second test using the same mock, it really shrinks the amount of code the programmer need to write.

Chapter 11: Refactoring Tests

Remove try/catch blocks and replace them by throwing a IO Exception
Two or three lines of code that implement a single concept - find a way to distill them to a single clear assert statement in the test, etc.


Part 4: The Bigger Unit-Testing Picture

In the last part of the book we come back to testing but we don't look at what makes unit-tests good, but how to obtain them. 

Chapter 12: Test Driven Development (TDD)

To introduce TDD the authors go quickly over the red-green-refactor cycle:

Write a test that fails.

Get the test to pass.

Clean up any code added or changed in the prior two steps.


An important aspect is that your new production code in step 2 should only add as little as possible code to make the test pass. This sometimes means that you only fake proper behavior until another test forces you to write the proper business logic.
Next they build the previously explained Profile class from scratch while using TDD. It's a nice touch they end up with a different design than the previous ProfileMatcher, MatchSet solution.

The authors emphasize "always watch your tests fail first", to make sure your tests actually test what you think (this is essentially the red phase of the TDD cycle). 

As with the other code examples there are plenty of accompanying comments to guide you through the process. It's useful as a simulation of a co-worker giving you a "feel" for the technique. The tricky part of TDD isn't the basic idea but the practice and the small problems you encounter. In their process they realize one part should be moved from Profile to a new class Answer, which then first gets its own unit-test. When they realize they have too many similar sounding test method names they split up tests for the same unit into two test classes. That way they can also make the method names simpler because part of the context is encoded in the class names.

Another tricky part of TDD is how to choose the size of the steps of each cycle or how long to spend on refactoring. One of the crucial selling points of TDD is the flow of the TDD cycle that force you into a rhythm and reduce the times your stuck on some coding problem. Even though we said we should only write a simple next test and only add the fewest code to make it pass, in practice you sometimes try larger steps simply because you're too sure it'll be easy. The authors suggest to give yourself a maximum of roughly ten minutes for the whole cycle. If you've reached that time limit you should simply throw away all the code since the last cycle and try again. Recently there was an interesting blog article on Hacker News suggesting a similar approach "test && commit || revert" that reverts your code if you make your tests fail unexpectedly - although their approach also gives up the crucial red phase.

Chapter 13: Testing Some Tough Stuff
Here the authors explain how to write tests that aren't easily covered with unit tests. As examples they mention database access and multi-threaded code.

For both problems they suggest to use prepared well-tested components that already do the heavy lifting for you and otherwise isolate the special multi-threading or database setup to another class. Then you can test the actual business logic and only write a basic test for the extra context.

If that's not enough they give a concrete simple integration test example that covers resetting the database to a known state before each test. Fortunately with Spring Boot you can use the excellent @DataJpaTest, which already does this and some more things for you. 

Chapter 14: Testing on a Project

The last chapter is about testing in a team. They emphasize that it's important everybody in a team agrees on what and how to test. They suggest to set explicit testing standards to define:

*  Definition of Done and when tests should be written
*  Naming of test classes and method
*  If you want to follow the BDD style Arrange, Act, Assert code blocks
*  Which assertion library to use (I would suggest AssertJ or Hamcrest)
*  Which mock library to use (mockito seems pretty good IMHO)
*  How do you define the border between unit tests and integration tests in you team?
*  How much code coverage do you roughly want to achieve?


Lastly they quickly go over a couple of best practices that generally help:

* a CI server
* code reviews
* pair programming

__Conclusion__

In one way or another, after digging through this book, you are definitely surprised by how pragmatic the author is in some real test case scenarios. Sometime he decides to break the rules to give you an impression how you strive for the optimum but not waste effort by slavishly following a rule. 

He initiates paradigms on where exactly to prioritize assumptions and how to structure test cases, which are enough to introduce you to the unit-testing field and improve the quality of your software. His guidelines and intuitions help you a lot when trying to design clean, maintainable code - "Übersichtlich" in German.

As any other book, is not perfect, and there are still incomplete parts on topics such as TDD, integration tests and test coverage, which are not covered in depth. Yet, this is a very good incentive to explore more about the topics uncovered and a drive for us to continually improve our unit‑testing skills.





