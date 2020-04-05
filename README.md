# Atividade 2 - Pós DataScience - NoSQL - NEO4J

1. ativar o ambiente
```
# docker-compose up neo4j-server
```

use a flag -d se quiser que rode em segundo plano.

Foi retirada a senha através da variável de ambiente no _docker-compose.yaml_ para testes facilitados.

Verificando a documentação de apoio, assume-se que deve ser usada a informação _:play intro-neo4j-exercise_ como modelo de dados para os exercícios.


## Exercício 1- Retrieving Nodes 

1. Retrieve all nodes from the database.
2. Examine the data model for the graph.
3. Retrieve all Person nodes.
4. Retrieve all Movie nodes. 


## Exercício 2 – Filtering queries using property values 

1. Retrieve all movies that were released in a specific year.
2. View the retrieved results as a table.
3. Query the database for all property keys.
4. Retrieve all Movies released in a specific year, returning their titles.
5. Display title, released, and tagline values for every Movie node in the graph.
6. Display more user-friendly headers in the table


## Exercício 3 - Filtering queries using relationships 

1. Display the schema of the database.
2. Retrieve all people who wrote the movie Speed Racer.
3. Retrieve all movies that are connected to the person, Tom Hanks.
4. Retrieve information about the relationships Tom Hanks had with the set of movies retrieved earlier.
5. Retrieve information about the roles that Tom Hanks acted in. 


## Exercício 4 – Filtering queries using WHERE clause 

1. Retrieve all movies that Tom Cruise acted in. 
2. Retrieve all people that were born in the 70’s. 
3. Retrieve the actors who acted in the movie The Matrix who were born after 1960. 
4. Retrieve all movies by testing the node label and a property. 
5. Retrieve all people that wrote movies by testing the relationship between two nodes. 
6. Retrieve all people in the graph that do not have a property. 
7. Retrieve all people related to movies where the relationship has a property. 
8. Retrieve all actors whose name begins with James. 
9. Retrieve all all REVIEW relationships from the graph with filtered results. 
10. Retrieve all people who have produced a movie, but have not directed a movie. 
11. Retrieve the movies and their actors where one of the actors also directed the movie. 
12. Retrieve all movies that were released in a set of years. 
13. Retrieve the movies that have an actor’s role that is the name of the movie. 


## Exercício 5 – Controlling query processing 

1. Retrieve data using multiple MATCH patterns. 
2. Retrieve particular nodes that have a relationship. 
3. Modify the query to retrieve nodes that are exactly three hops away. 
4. Modify the query to retrieve nodes that are one and two hops away. 
5. Modify the query to retrieve particular nodes that are connected no matter how many hops are required. 
6. Specify optional data to be retrieved during the query. 
7. Retrieve nodes by collecting a list. 
9. Retrieve nodes as lists and return data associated with the corresponding lists.
10. Retrieve nodes and their relationships as lists. 
11. Retrieve the actors who have acted in exactly five movies. 
12. Retrieve the movies that have at least 2 directors with other optional data. 

## Exercício 6 – Controlling results returned 

1. Execute a query that returns duplicate records. 
2. Modify the query to eliminate duplication. 
3. Modify the query to eliminate more duplication. 
4. Sort results returned. 
5. Retrieve the top 5 ratings and their associated movies. 
6. Retrieve all actors that have not appeared in more than 3 movies. 


## Exercício 7 – Working with cypher data  

1. Collect and use lists. 
2. Collect a list. 
3. Unwind a list. 
4. Perform a calculation with the date type. 


## Exercício 8 – Creating nodes 

1. Create a Movie node. 
2. Retrieve the newly-created node. 
3. Create a Person node. 
4. Retrieve the newly-created node. 
5. Add a label to a node. 
6. Retrieve the node using the new label. 
7. Add the Female label to selected nodes. 
8. Retrieve all Female nodes. 
9. Remove the Female label from the nodes that have this label. 
10. View the current schema of the graph. 
11. Add properties to a movie. 
12. Retrieve an OlderMovie node to confirm the label and properties. 
13. Add properties to the person, Robin Wright. 
14. Retrieve an updated Person node. 
15. Remove a property from a Movie node. 
16. Retrieve the node to confirm that the property has been removed. 
17. Remove a property from a Person node. 
18. Retrieve the node to confirm that the property has been removed. 


## Exercício 9 – Creating relationships  

1. Create ACTED_IN relationships.
2. Create DIRECTED relationships. 
3. Create a HELPED relationship. 
4. Query nodes and new relationships. 
5. Add properties to relationships. 
6. Add a property to the HELPED relationship. 
7. View the current list of property keys in the graph. 
8. View the current schema of the graph. 
9. Retrieve the names and roles for actors. 
10. Retrieve information about any specific relationships.
11. Modify a property of a relationship. 
12. Remove a property from a relationship. 
13. Confirm that your modifications were made to the graph. 


## Exercício 10 – Deleting nodes and relationships  

1. Delete a relationship. 
2. Confirm that the relationship has been deleted.
3. Retrieve a movie and all of its relationships. 
4. Try deleting a node without detaching its relationships. 
5. Delete a Movie node, along with its relationships. 
6. Confirm that the Movie node has been deleted. 
