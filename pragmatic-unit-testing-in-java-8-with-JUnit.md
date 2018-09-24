# Pragmatic Testing

Keeping some notes & tips from the great book ofJeff Langr - [Pragmatic Unit Testing in Java 8 with JUnit](https://pragprog.com/book/utj2/pragmatic-unit-testing-in-java-8-with-junit)

## Part #2

**FIRST** Principles of Good Testing. **FIRST** term should remind the characteristics of quality tests. Write the unit tests before you write the corresponding code, descipline known as TDD
  * **[F]ast** tests, take few milliseconds at least to execute. 
  To keep the design clean you should minimize the dependencies on code that executes slow (from databases, files, network calls). If all your tests interact with code that ultimately always make a database call, all the tests will be slow. This happens because there is a distance between the database data and the expected data values in the test, so the test will be hard to follow. A solution might be e.g to use memory hash map with fake data and not look to a slow peristent store.
  * **[I]solate** your tests. Run one test at any time, in any order. Unit test don't depend on other unit tests, each can be independent if each test concentrates on a small amount of behavior.
When start adding a 2nd assert -> _"Does this assertion help to verify a single behavior or it represents a behavior that could be described with a new test method/name?"_. How to isolate code? _(is answered in later chapters)_
 * **[R]epeatable** tests produce the same results each time you run them, and are accomplished after isolating them from the external environment, which is not in your direct control. 
 * **[S]elf-validating**. Old way of using main() method to test, requires always to visually verify the output. JUnit does that work for you, tests either _pass_ or _fail_. Tests aren't tests, unless they assert that things went as expected. Automate the process __when__ & __how__ these tests run. _(In larger scale can be done with a tool like Jenkins, which watches your source repository and kicks a build/test process when it recognizes changes.)_
 * **[T]imely**. Direct your efforts to more troubled or dynamic spots in your system, only if the code reveals defects and need to be changed.

**What to test?** - __The right-BICEP__



## Part #3

**Refactoring to Cleaner Code** - transforming your code structure while retaining the existing functional behavior.
 * **Minimize the amount of duplication** - every piece of code duplicated increases the cost & risk to maintain it.
 * **Rename** - 


A unit test on it's own doesn't represent a complete end-to-end behavior but a small subset of that. 

Keeping some notes & tips from the great book of Jeff Langr - Pragmatic Unit Testing in Java 8 with JUnit



It's time to write a unit test when:

Just finished a feature and want to test if it works.
Document a change so that you and others later understand the choices you coded.
After making a change in an existent code and want to check the expected behavior.
Understand the current behavior of the code.
Want to know when third-party code no longer behaves as expected.
Optimize when the following problems shows up:
Tests that make little sense to follow.
Tests that fail sporadically.
Tests that don't prove anything.
Tests that don't sufficiently cover.
Small changes, break lots of tests.
Convoluted tests that jump through numerous setup hoops.

STEP 1 - How to start?
A good practice of test-driven development (TDD) to avoid bad, costly assumptions, is to start on failing your tests, to prove that they really are doing something.

Book-Club > 2018/09/24 > Pragmatic Unit Testing > Screen Shot 2018-09-18 at 09.50.07.png

STEP 2 - Follow with a (AAA) scenario -test case-
Arrange - First, we need to set up the state in order to do anything in the test.
Act -On-Execute the code we are trying to verify.

Assert - Compares the actual result with the expected value.

Book-Club > 2018/09/24 > Pragmatic Unit Testing > Screen Shot 2018-09-18 at 09.22.08.png



STEP 3 - Give consistent & meaningful names to your tests which would test behavior and NOT methods.

Here are some hints to tell stories with your names and code:
doingSomeOperationThaGeneratesSomeResult
someResultOccursUnderSomeCondition
Examples of the ATM domain:

Book-Club > 2018/09/24 > Pragmatic Unit Testing > Screen Shot 2018-09-24 at 11.24.52.png



Another way is to test with the given-when-then naming known as BDD (Behavior Driven Development).

givenSomeContextWhenDoingSomeBehaviorThenSomeResultOccurs - if this seems too long for you, then try the next one.
whenDoingSomeBehaviorThenSomeResultOccurs


STEP 4 - How to  build  right & correct unit tests? 
This section focuses on a series of mnemonics, a simple guideline to help the reader build better tests. Remember the following principles:
FIRST - How important is to write unit tests.
[F]ast - A test should take few milliseconds at least to execute.
[I]solated - Run one test at any time, in any order. Unit tests don't depend on other unit tests.

[R]epeatable - Return the same results each time you run them.
[S]elf-validating -Unit tests aren't tests, unless they assert that things went as expected.
[T]imely - Make unit test on time, don't skip or procrastinate.


Right-BICEP

Right - Write a test about the happy expected behavior.
[B]oundary Conditions - Write one test for every boundary condition.
[I]nverse Relationships - Call the methods in different order and check if you got the expected behavior.
[C]ross Checking - Look & check different parts of code/methods to verify the expected values.
[E]rror Conditions - Whenever there is a happy path, there is an unhappy path. Write tests that force errors to occur. Possible error scenarios could be ( running out of memory or disk space, sending email fails, network availability, etc)
[P]erformance -  Run performance tests separately and enough times from fast unit tests. Use tools for unit-level performance measurement.


CORRECT - How to write correct boundary conditions.

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





STEP 5 - How to  build high-quality unit tests? 
The author is giving some code examples how to deal with refactoring to cleaner code.







When to stop writing unit tests?
When the validation is done at that point that is introduced in the system, there is no need to validate every method that takes the field on as an argument. 







