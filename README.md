# Atividade 2 - Pós DataScience - NoSQL - NEO4J

1. ativar o ambiente
```
# docker-compose up neo4j-server
```

use a flag -d se quiser que rode em segundo plano.

Foi retirada a senha através da variável de ambiente no _docker-compose.yaml_ para testes facilitados.

Verificando a documentação de apoio, assume-se que deve ser usada a informação _:play movie-graph_ como modelo de dados para os exercícios.


## Exercício 1- Retrieving Nodes 

1. Retrieve all nodes from the database.
```
$ MATCH (node) RETURN node
```

2. Examine the data model for the graph.
![todos os nós](images/all_nodes.PNG)

3. Retrieve all Person nodes.
```
$ MATCH (node:Person) RETURN node
```

4. Retrieve all Movie nodes. 
```
$ MATCH (node:Movie) RETURN node
```


## Exercício 2 – Filtering queries using property values 

1. Retrieve all movies that were released in a specific year.
```
$ MATCH (node:Movie {released: 1999}) RETURN node
```

2. View the retrieved results as a table.
![filmes de 1999 como tabela](images/1999_movies_as_table.PNG)

3. Query the database for all property keys.
```
$ CALL db.propertyKeys
```

4. Retrieve all Movies released in a specific year, returning their titles.
```
$ MATCH (node:Movie {released: 1999}) RETURN node.title
```

5. Display title, released, and tagline values for every Movie node in the graph.
```
$ MATCH (node:Movie {released: 1999}) RETURN node.title, node.tagline, node.released
```

6. Display more user-friendly headers in the table
```
$ MATCH (node:Movie {released: 1999}) RETURN node.title AS `Título`, node.tagline AS `Subtítulo`, node.released AS `Lançado em`
```


## Exercício 3 - Filtering queries using relationships 

1. Display the schema of the database.
```
$ CALL db.schema.visualization()
```

2. Retrieve all people who wrote the movie Speed Racer.
```
$ MATCH (p:Person)-[rel:WROTE]->(m:Movie {title: 'Speed Racer'}) RETURN p, rel, m
```

3. Retrieve all movies that are connected to the person, Tom Hanks.
```
$ MATCH (p:Person {name: 'Tom Hanks'})-[rel]->(m:Movie) RETURN p, rel, m
```

4. Retrieve information about the relationships Tom Hanks had with the set of movies retrieved earlier.
```
$ MATCH (p:Person {name: 'Tom Hanks'})-[rel]->(m:Movie) RETURN p.name, type(rel), m.title
```

5. Retrieve information about the roles that Tom Hanks acted in. 
```
$ MATCH (p:Person {name: 'Tom Hanks'})-[rel:ACTED_IN]->(m:Movie) RETURN p.name, type(rel), m.title
```


## Exercício 4 – Filtering queries using WHERE clause 

1. Retrieve all movies that Tom Cruise acted in. 
```
$ MATCH (p:Person {name: 'Tom Cruise'})-[r:ACTED_IN]->(m:Movie) RETURN p, r, m
```

2. Retrieve all people that were born in the 70’s. 
```
$ MATCH (p:Person) WHERE 1970 <= p.born <= 1979 RETURN p
```

3. Retrieve the actors who acted in the movie The Matrix who were born after 1960. 
```
$ MATCH (p:Person)-[r:ACTED_IN]->(m:Movie {title: 'The Matrix'}) WHERE p.born >= 1960 RETURN p, r, m
```

4. Retrieve all movies by testing the node label and a property. 
```
$ MATCH (m:Movie {released: 1999}) WHERE m.title STARTS WITH 'The ' RETURN m
```

5. Retrieve all people that wrote movies by testing the relationship between two nodes. 
```
$ MATCH (p:Person)-[r]->(m:Movie) WHERE type(r) = 'WROTE' RETURN p, r, m
```

6. Retrieve all people in the graph that do not have a property. 
```
$ MATCH (p:Person) WHERE NOT exists(p.city) RETURN p
```

7. Retrieve all people related to movies where the relationship has a property. 
```
$ MATCH (p:Person)-[r]->(m:Movie) WHERE exists(r.rating) RETURN p
```

8. Retrieve all actors whose name begins with James. 
```
$ MATCH (p:Person)-[r]->(m:Movie) WHERE p.name STARTS WITH 'James' RETURN p
```

9. Retrieve all all REVIEW relationships from the graph with filtered results. 
```
$ MATCH (p:Person)-[r]->(m:Movie) WHERE type(r) = 'REVIEWED' RETURN r
```

10. Retrieve all people who have produced a movie, but have not directed a movie. 
```
$ MATCH (p:Person)-[r:PRODUCED]->(m:Movie) WHERE NOT exists( (p)-[:DIRECTED]->(m) ) RETURN p
```

11. Retrieve the movies and their actors where one of the actors also directed the movie. 
```
$ MATCH (p:Person)-[r:ACTED_IN]->(m:Movie) WHERE exists( (p)-[:DIRECTED]->(m) ) RETURN p, r, m
```

12. Retrieve all movies that were released in a set of years. 
```
$ MATCH (m:Movie) WHERE m.released in [1999,1990] RETURN m
```

13. Retrieve the movies that have an actor’s role that is the name of the movie. 
```
$ MATCH (p:Person)-[r:ACTED_IN]->(m:Movie) WHERE m.title in r.roles RETURN p, r, m
```


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
