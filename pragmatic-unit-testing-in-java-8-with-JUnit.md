# Part #2 - Mastering Manic Mnemonics


FIRST Principles of Good Testing
  * FIRST - write the unit tests before you write the corresponding code - descipline known as TDD
  * [F]IRST - [F]ast tests, take few milliseconds at least to execute. 
  To keep the design clean you should minimize the dependencies on code that executes slow (from databases, files, network calls). If all your tests interact with code that ultimately always make a database call, all the tests will be slow. This happens because there is a distance between the database dataand the epected datavalues in the test, the test will be hard to follow. A solution might be e.g to use memory hash map with fake data and not look to a slow peristent store.
             
