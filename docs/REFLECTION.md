I think AI has helped me to understand alot more than I came into this assignment knowing.
The little things that come with handling exceptions and edge cases are things that I didn't get to into depth with in my last programming class we only had about a week of work with exceptions.
I think AI has made me a better programmer. 
I also think that the AI analysis questions were very helpful in guiding my thinking and making sure that I was considering all possible scenarios. 
I ran into a couple of scenarios where I was using the AI to help me with an exception, it made 3 other ones come up but after a little while we figured it all out.
On my own the amount of time that would have taken me to figure out all the edge cases and exceptions would have been much longer.
Overall, I think this assignment has been a great learning experience, I am grateful for the opportunity to work with AI in this way.
Before taking this class teachers didn't want us to use AI, but now I see how it can be a valuable tool for learning and improving our coding skills.
I beleive it is important to be able to learn to use AI appropriately and efficiently.

AI analysis questions and answers:
What happens if we try to get the first 2 elements from a list with only 1 element?
If we try to get the first 2 elements from a list with only 1 element, we would need to throw an exception, we would recieve EmptyCollectionException. Using the . limit(2) says it doesnt want to recieve more than 2 elements. It will still generate 1 without a crash.
How should we handle the case where no odd numbers exist in topTenUniqueOdd()?
It would create an empty list, If we wanted to throw an exception we would throw InvalidDataException, so it would have a display.
What's the best way to handle null elements within a collection?
The .filter(Objects::nonNull) is the best way to handle null elements within a collection, it will filter out all null values and only return non-null values.
Should average() return null, throw an exception, or return a special value for empty collections?
Using InvalidDataException would be the best way to handle empty collections in average(), it would throw an exception and display a message that the collection is empty and cannot calculate an average. The average returns a double, so returning null would be a failure that would return NullPointerException.
How can we make our exception messages more informative for debugging?
We could include the method name, the input values that caused the exception, and a clear description of the error in our exception messages.
What performance considerations should we have for large collections?
According to Claude, The sorted() is a costly operation, so we should avoid it if possible. We should also consider using parallel streams for large collections to improve performance.
Also the TopTen and topTenUniqueOdd both sort the list before limiting to 10, if it was millions of elements you would want to do it after the number.
How can we make our methods more testable and maintainable?
Using Protected instead of private allows the test to to inject data directly which is what I think was the point of this project, to be able to use exception test. If we wanted to do a bigger design we would want to inject using a conductor which you could avoid manipulation using the exceptions.