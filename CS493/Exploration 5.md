**

Dalton Shults

CS 493

Prof. Hall

5 May 2024

Exploration 5: Using MongoDB to Store API Data

1. In a sentence or two, how would you describe the difference between document databases and relational/SQL databases?
    

Relational Databases store data in tables and use the relational aspects of its data to organize it. You can combine the link between different data types into a table or use it for a lookup. For example, if every business has an owner, we can find every business’ owner by joining a table between the business table “where business_owner_id=owner_id.” Document databases, on the other hand, offer a much more flexible approach to data management as they do not enforce a schema. Instead, the data is organized in Key Value pairs and stored in a document. This flexibility allows for easy retrieval of data by querying the document with a Key to get the value stored, offering a more adaptable solution. 

2. What are the advantages of document databases over relational databases?
    

The main advantage of this approach is its flexibility. You can store data in any form if it conforms to the JSON syntax. I also find this method of database searches more intuitive because it operates similarly to a dictionary, and the JavaScript calls are easy to understand. So, I think the queries are easier to develop and implement because the syntax is easier to understand. Put simply, I believe that document-based databases are easier to deal with and manage as a developer. I could also see this flexibility making database migrations or changes much easier to deal with than in a relational database.

3. What are the advantages of relational databases over document databases?
    

One of the massive advantages I see is simply using a schema. The data will be in exactly the form it needs to be in. Otherwise, the DB will throw a fit. Personally, I really enjoy this safety measure because I don’t have to worry about my database object missing a field, like a business not having an assigned owner. As long as the field is set not to allow Null values, the value will never be missing or Null. This avoids having to build additional error handling into the code base to check and make sure that a field isn’t missing every time a query is made. This is a massive disadvantage of document-based databases. Honestly, the only real advantage of having a loose schema is you can do things that SQL won’t let you do, but sometimes there is a reason that it isn’t allowed; it could be the performance of queries, or just avoiding duplicated data. I could see how you could easily build a Document-based DB incorrectly, causing it to have slow query responses and even storing duplicates of the same data repeatedly. Overall, a relational database’s schema enforcement is something that I see as a huge advantage because then you aren’t relying on everyone on your team to format the data correctly. Think of a situation where someone misspells a collection name, and MongoDB creates an entirely new collection to store the new document there instead of informing them of the incorrect name, they have to figure out what happened. Then, when they try to find the document, it won’t be in the collection they expect it to be because it ended up in “busnesses.”

**