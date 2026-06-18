# First basic prompt, on new empty directory. sonet 4.6, high. no plan. took less than a minute:

create a basic server backend in node JS, simulating a bookstore. The port is 3456. no error handling is needed. no front end. no logging, no special skill. make it quick and simple. it will have 3 endpoints:

Creates a new book in the system: POST /book | body: json with title, author, price and year. it will return book object with id (integer, 1, 2, 3...)
get existing book by ID: GET /book?id=<id> | it will return the matching book object
delete a book by ID: DELETE /book?id=<id> | it will return the book object that was deleted

# Now add a feature using planning mode or superpowers: 


I want to add a new feature: filtering.
create an endpoint allowing to filter according to book properties. all filtering is optional.
ask me clarification questions as much needed