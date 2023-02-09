# MongoDB

## Notes
### MongoDB schema design
* 3 Things to consider when designing a schema:
  * How to actually store the data
  * Query performance
  * Reasonable amount of hardware
* **Normalization**: Don't duplicate data.
* **One to one**: Prefer key value pairs
* **One to few**: Prefer embedding
* **One to many**: Prefer referencing
* **One to squillions**: Prefer reverse referencing
  * Don't treat the same as one to many since this is better for UNBOUNDED amounts of data.
  * Unspecified massive number. 
  * Reference the parents object on the child object (reverse reference)
* **Many to many**: Prefer two way referencing
  * Example: Users can have many todo items and todo items can have many
  * Each uer will point to their todo items
  * Each todo item will point to their owners (two way reference)
#### Outlier Patterns
Example: Someone very famous joins a social media platform.
In order for the application to handle all the amount of followers, there can be a flag on the user object that let's us know there is more work that needs to be done (i.e. maybe break up the amount of followers).
#### Schema Rules
* Rule 1: Favor embedding unless there's a compelling reason not to (like needing to access data on it's own)
* Rule 2: Avoid joins if they can be avoided but don't be afraid to use them if they make the schema design better.
* Rule 3: Arrays should never be unbound (one to squillions, do reverse referencing)
* Rule 4: Needing to access data on it's own is a compelling reason to not embed it
* Golden Rule: Design a schema on the unique needs of your application
#### Embedding
* Pros:
  * Retrieve all data with a single query
  * Avoid expense JOINs or $lookups
  * Update all data with a single atomic operation
* Cons:
  * Large docs === more overhead
  * 16 MB document size limit
#### Referencing
* Reference other documents in a document using a reference pointer (in same collection or other collection)
* Good use case for referencing is when you do not need the referenced data every single time you call the parent document
* Pros:
  * Smaller documents
  * Less likely to reach 16 MB limit
  * No duplication of data (dup'd data is not the end of the world in mongo)
  * Infrequently accessed data not accessed on every query
* Cons:
  * Two queries or $lookup required to retrieve all data


