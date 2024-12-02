# cognigy_demo
The bot is meant to guide the process of a sales store.
It will greet the user, capture his/her name and ask for a transaction type.

Transactions / intentions handled are: **Buying, selling, returning an item and managing wrong input.**
The product to buy/sell can be captured in the initial messages, saving extra steps if unnecesary. 

## Wrong input handling
After the greeting, if the user messages an intention that's out of the scope, it will return a "Did not understand" message and restart the workflow

## Buying
If the user stated the item already it will promp a confirmation message.
If the product has not been declared already, will ask for it.
Once the product is identified, it will connect with a **JSON file** which contains the price information, which is captured in context.
The price and the name storaged in context are retrieved as a confirmation message.

## Selling
If the user stated the item already it will promp a confirmation message with the product name.
If the product has not been declared already, will ask for it.
Once the product is identified, it will connect with a **SQL data base** which contains the price information, so the product name is used to query the table and return the price which is captured in context.
A message with a link to terms and conditions is displayed and the information of the price captured in context
A Yes/No question is displayed confirming both the price and the product captured in context.
If Yes, the details on the product and price are sent to an Agent through a *Agent Assist Card* node
If No, the conversation finishes with a good bye message

## Return
A **Text with buttons** question is prompted with 2 options: change address, return product.
Then using an **SQL query** using the captured name, will look for the last item buyed by the customer.
A confirmation message returns with the details of the last product.
If return product, it will ask for the reason of change. Then a confirmation message with details of the returning process comes back, including the product details captured in context.
If change of address a Text question will return asking for details of the new address.
Another **SQL query** will display the last address added and a Yes/No question will confirm if the change is needed.
If No, the process finishes. If yes, a Text question captures the new address. A **Commit SQL query** is send to the DB and a confirmation message is prompted
