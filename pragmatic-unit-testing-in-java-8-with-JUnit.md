# Pragmatic Testing

Keeping some notes & tips from the great book ofJeff Langr - [Pragmatic Unit Testing in Java 8 with JUnit](https://pragprog.com/book/utj2/pragmatic-unit-testing-in-java-8-with-junit)

## Part #2 - Mastering Manic Mnemonics


**FIRST** Principles of Good Testing
  * FIRST - write the unit tests before you write the corresponding code - descipline known as TDD
  * **[F]ast** tests, take few milliseconds at least to execute. 
  To keep the design clean you should minimize the dependencies on code that executes slow (from databases, files, network calls). If all your tests interact with code that ultimately always make a database call, all the tests will be slow. This happens because there is a distance between the database data and the expected data values in the test, so the test will be hard to follow. A solution might be e.g to use memory hash map with fake data and not look to a slow peristent store.
  * **[I]solate** your tests. Run one test at any time, in any order. Unit test don't depend on other unit tests, each can be independent if each test concentrates on a small amount of behavior.
When start adding a 2nd assert -> _"Does this assertion help to verify a single behavior or it represents a behavior that could be described with a new test method/name?"_. How to isolate code? _(is answered in later chapters)_
 * **[R]epeatable** test is one that produces the same results each time you run it, and are accomplished after isolating them from the external environment, which is not in your direct control. 
 * **[S]elf-validating**. Old way of using main() method to test, requires always to visually verify the output. JUnit does that work for you, tests either _pass_ or _fail_. Tests aren't tests, unless they assert that things went as expected. Automate the process __when__ & __how__ these tests run. _(In larger scale can be done with a tool like Jenkins, which watches your source repository and kicks a build/test process when it recognizes changes.)_
