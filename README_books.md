# Cognigy demo (Bookstore)
* The bot is meant to support a bookstore. 
* Transactions / intentions handled are: **Listing available genres, Finding a book in storage, providing store details and managing wrong input.**
* The book to be found can be captured in the initial messages, saving extra steps if unnecesary. 
* After done with the process, it will ask if more help is needed and re direct accordingly.

## Wrong input handling
After the greeting, if the user messages an intention that's out of the scope, it will return a "Did not understand" message and restart the workflow

## Listing available genres
* A **GET HHTP Request** is done to get the list of books and their details. Which are storage in the Context
* A **TypeScript code** is used to retrieve the data from the context, get the list of unique genres and assign the result to the context
* A message with the list of genres available is displayed

The user is asked if they need extra help and is redirected to the beggining if Yes or the workflow ends if No

## Finding a book in storage
* A **GET HHTP Request** is done to get the list of books and their details. Which are storage in the Context
* An **If Node** detects if the book has been mentioned already.
  If yes, adds the name of the books to the context
  If no, asks for the book and assign the answer to the context
* After the book to look is captured in context, an **TypeScript code** is used to check if the book to be found matches with the existing books in * storage *JSON data* and sends the result to a variable in context
* An **If Node** retrieves the variable from the Code detecting if the book has been found.
  If yes, a confirmation message is displayed
  If no, a message with a link is displayed

* The user is asked if they need extra help and is redirected to the beggining if Yes or the workflow ends if No

## Providing store details
* If the intent of the user matches with location or hours of the store.
* A **dummy SQL** looks for the information in the DB
* A **Say** message is displayed with the store details
* The user is asked if they need extra help and is redirected to the beggining if Yes or the workflow ends if No
