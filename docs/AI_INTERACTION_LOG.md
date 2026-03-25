I used Claude 4.6 The first Question I asked was "I was just given this project to do, these are the instructions can you help me out? Fork and Clone
* Download the template from __https://github.com/UltimateSandbox/project-3-initial.git__
1. AI-Enhanced Analysis Phase
    * For each method, use an AI assistant to analyze the test code
    * Ask the AI to identify potential edge cases and exception scenarios
    * Request suggestions for robust implementation approaches
2. Implementation with Exception Handling
    * In the GentlyDownTheStream class, read the TODO comments
    * Examine the corresponding test in GentlyDownTheStreamTest
    * Implement methods with proper exception handling and validation
    * Each method should include appropriate null checks and edge case handling
3. AI Code Review
    * After implementing each method, use AI tools to review your code
    * Ask for optimization suggestions and potential improvements
    * Validate exception handling approaches
4. Testing and Validation
    * You have 10 methods to complete (including exception handling variants)
    * All unit tests must pass, including new exception-focused tests
    * Run additional edge case tests to ensure robustness".
    Claude responded with a step by step breakdown of the assignment.
   Then asked me to paste the GentlyDownTheStream Files and went over the exceptions and explained them to me.
      
"Here's a breakdown of every method I implemented and the key decisions made:
sortedFruitsFirstTwo()
Sorts the fruits list alphabetically then uses .limit(2) to grab the first two. The EmptyCollectionException is re-thrown directly (without wrapping) so the caller sees the specific exception type — a pattern used consistently throughout.
commaSeparatedListOfFruits()
Uses Collectors.joining(", ") to produce the comma-separated string. After joining, there's a guard against an unexpectedly empty result string (possible if all elements were null and got filtered out).
reverseSortedVeggies()
Uses Comparator.reverseOrder() — exactly what the TODO comment recommended — with null filtering before sorting.
reverseSortedVeggiesInUpperCase()
Chains .sorted(Comparator.reverseOrder()) followed by .map(String::toUpperCase). Order matters here: sort first, then uppercase — doing it the other way would sort by the uppercased value instead.
topTen()
Sorts descending with Comparator.reverseOrder() then .limit(10). Works correctly even if the list has fewer than 10 elements since limit() is non-throwing when the stream is shorter.
topTenUnique()
Adds .distinct() before sorting. Placing distinct() before sorted() is more efficient — it reduces the number of elements the sort has to handle.
topTenUniqueOdd()
Filters odd numbers with n % 2 != 0, then chains distinct(), sorted(reverseOrder()), and limit(10).
average()
Uses the existing safeAverage() helper which returns an OptionalDouble. The isPresent() check handles the edge case where all values are null and the stream is empty — avoiding a NoSuchElementException on .getAsDouble()"

At First me and Claude had a little bit of trouble with some of the exceptions, fixing one problem would cause another which I would go to the error message and see if I could figure out what was wrong.
If I couldnt figure it out I asked Claude for help and it would figure out a solution to pass both cases giving me problems.

The messages were "java: exception com.example.streams.InvalidDataException is never thrown in body of corresponding try statement"
"java.lang.AssertionError:
Expecting actual throwable to be an instance of:
com.example.streams.EmptyCollectionException
but was:
com.example.streams.InvalidDataException: Failed to sort fruits: Fruits collection cannot be empty
at com.example.streams.GentlyDownTheStream.sortedFruits(GentlyDownTheStream.java:39)
at com.example.streams.GentlyDownTheStreamTest$ExceptionHandlingTests.lambda$shouldHandleEmptyCollections$0(GentlyDownTheStreamTest.java:196)
at org.assertj.core.api.ThrowableAssert.catchThrowable(ThrowableAssert.java:63)
...(82 remaining lines not displayed - this can be changed with Assertions.setMaxStackTraceElementsDisplayed)
at com.example.streams.GentlyDownTheStreamTest$ExceptionHandlingTests.shouldHandleEmptyCollections(GentlyDownTheStreamTest.java:197)
at java.base/java.lang.reflect.Method.invoke(Method.java:565)
at java.base/java.util.ArrayList.forEach(ArrayList.java:1604)
at java.base/java.util.ArrayList.forEach(ArrayList.java:1604)
at java.base/java.util.ArrayList.forEach(ArrayList.java:1604)"
"java.lang.AssertionError:
Expecting actual throwable to be an instance of:
com.example.streams.InvalidDataException
but was:
com.example.streams.EmptyCollectionException: Integer values collection cannot be empty
at com.example.streams.GentlyDownTheStream.validateCollection(GentlyDownTheStream.java:209)
at com.example.streams.GentlyDownTheStream.average(GentlyDownTheStream.java:185)
at com.example.streams.GentlyDownTheStreamTest$ExceptionHandlingTests.lambda$shouldHandleDivisionByZeroInAverage$0(GentlyDownTheStreamTest.java:214)
...(83 remaining lines not displayed - this can be changed with Assertions.setMaxStackTraceElementsDisplayed)
at com.example.streams.GentlyDownTheStreamTest$ExceptionHandlingTests.shouldHandleDivisionByZeroInAverage(GentlyDownTheStreamTest.java:215)
at java.base/java.lang.reflect.Method.invoke(Method.java:565)
at java.base/java.util.ArrayList.forEach(ArrayList.java:1604)
at java.base/java.util.ArrayList.forEach(ArrayList.java:1604)
at java.base/java.util.ArrayList.forEach(ArrayList.java:1604)
Process finished with exit code -1"
Every time Claude would come back up with a solution and a new problem until the end.
The end result was that I was able to pass all the tests and understand the exceptions and edge cases much better than I did before starting the assignment.