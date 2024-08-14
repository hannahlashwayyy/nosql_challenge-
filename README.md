# nosql_challenge-

NoSQL_setup_starter file 
I began by importing my JSON file into MongoDB, naming my database and collection in accordance w/ homework instructions. Followed standard starting procedures of importing neccesary depedencies and created an instance of MongoClient then double checked that database 'uk_foods' was created, assigned it to a variable, then double checked that the collection 'establishments' existed and made sure that it contained the data in my json file.

To update my database with the new Penang Flavor restaurant, I created a dictionary using the information provided in the HW instructions and using 'insert_one' I added it to my collection 'establishments'. I used the 'find_one' function with my query to double check that the restaurant and information was added to my collection correctly. I then created a query that looked for the busines type ID for Restaurants/Cafes/Canteens and with that information, I updated the Business type ID for Penang Flavors because it did not originally include a Business Type ID. I then used the 'find_one' function again to double check that the data was updated correctly. 

Given that there was no interest in looking at restaurants in Dover, I queried all documents that had Dover as their Local Authority name and used 'delete_many' to drop all the documents, double checked that all the documents were dropped with 'count_documents' and finally used 'find_one' function again to ensure that the rest of the documents are still in my database.

I used the 'update_many' function in a few cases - first to convert the latitude and longitude from string to decimal, and then to convert the rating value from string to integer, that is, after I updated the Rating Value to nullify any ratings that were not 1 through 5. I used the 'find_one' one final time to double check that the latitude/longitude/rating value were all their correct datatype. 


NOSQL_analysis_starter file 
Followed the same standard starting steps as in my first file then I began my exploratory analysis. 

For my first query, I looked at establishments with a hygiene score of 20 and used the 'count_documents' and 'find_one' functions to count the total number of documents matching my query and then printing the first document that matched it. I used pretty print and an f-string to give a title to what the total count represented to viewer, and then to more clearly print the info in the first document. I converted this query to a Pandas dataframe, used another f-string to more clearly indicate the total number of rows in dataframe and used '.head(10)' to print the first ten rows of the dataframe. 

For my second query, I looked at establishments with a rating greater than or equal to 4 within London. I used regex functions as a part of my query as advised by the homework because in the database London is not called London but rather 'City of London Corporation' and by using regex, it let me look for any Local Authorities that at least had 'London' included in part of its name. I followed the same steps in my first query using 'count_documents' and 'find_one' to count the total number of documents and then print the first document that matched it. Again following suit with my first query, I used pretty print and an f-string to give a title to what the total count represented to viewer, and then to more clearly print the info in the first document. Again, I converted this second query to a Pandas dataframe, and used another f-string to more clearly indicate the total number of rows in dataframe and used '.head(10)' to print the first ten rows of the dataframe. 

For query three, I began by defining a degree seach to '0.01' and set my lat/long values to the location of Penang Flavors before beginning my actual query which included setting the rating value to 5. This let me look for establishments in the closest proximity to Penang Flavors. I defined the 'sort' of my query to sort by hygiene score from worst to best and then set a limit to only query the 5 closest restaurants. I printed my query and then converted it to a Pandas dataframe. 

For my fourth and final query, I actually created a pipeline with two individual queries, first querying all establishments with a hygiene score of 0, then querying the Local Authority Names and adding a 'count' to count the number of establishments within each Local Authority that held a hygiene score of 0, and from there, sorted all the Local Authorities that had establishments with a hygiene score of 0 in order from highest to lowest counts of establishments. I defined my pipeline and used the 'aggregate' function to print the results of my pipeline. I used pretty print and an f-string to give a title to what the total count represented to viewer, and then to more clearly print the first 10 results. I converted the pipeline to a Pandas dataframe and used another f-string to more clearly indicate the total number of rows in dataframe and used '.head(10)' to print the first ten rows of the dataframe. 





