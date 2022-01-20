Prologue: If you look up the noun mock in the dictionary you will find that one of the definitions of the word is something made as an imitation.

<b>
Mocking is primarily used in unit testing. An object under test may have dependencies on other (complex) objects. To isolate the behavior of the object you want to replace the other objects by mocks that simulate the behavior of the real objects. This is useful if the real objects are impractical to incorporate into the unit test.

In short, mocking is creating objects that simulate the behavior of real objects.
</b>

At times you may want to distinguish between mocking as opposed to stubbing. There may be some disagreement about this subject but my definition of a stub is a "minimal" simulated object. The stub implements just enough behavior to allow the object under test to execute the test.

A mock is like a stub but the test will also verify that the object under test calls the mock as expected. Part of the test is verifying that the mock was used correctly.

To give an example: You can stub a database by implementing a simple in-memory structure for storing records. The object under test can then read and write records to the database stub to allow it to execute the test. This could test some behavior of the object not related to the database and the database stub would be included just to let the test run.

If you instead want to verify that the object under test writes some specific data to the database you will have to mock the database. Your test would then incorporate assertions about what was written to the database mock.