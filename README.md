# Data modelling 
# Data-Modeling-with-Apache-Cassandra

Data modeling is a process used to analyze, organize, and understand the data requirements for a product or service. It creates the structure the data will live in and defines how things are labeled and organized, and also determines how data can and will be used. 

Data modeling can also be considered as a science of applying tested methodologies, making improvements and reproducing models, and an art of thinking outside the box to solve design problems, being creative since there is no standard solution and careful given that different data models have different costs. 
They are built around business needs and are living documents that evolve along with changing business needs. They play an important role in supporting business processes and planning IT architecture and strategy.

Data modelling basic processes. 

1. Analyze requirements of the domain to Identify entities and relationship- conceptual data model
2. Identify queries - workflow and access patterns(questions we want to ask of our data)
3. Specify the schema -logical data model (keyspaces, tables and columns)
4. Get something working - physical data model (actual code)
5. Optimize the model

This project demonstrates data modeling using apache cassandra, a nosql database that is built for high availability, scalability, and fault-tolerant systems, of a music streaming company thats wants to analyze what songs the users are listening to and are faced with challenges since the data resides in a directory of csv files on user activity on the app therefore no easy way to query the data to generate results

The purpose of the NoSQL database is to answer queries on song play data. The data model includes a table for each of the following queries:
1. Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4
2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'


# Data pre-processing, ETL pipeline, and data modeling
As mentioned earlier the data is currently stored as a collection of csv files partitioned by date. 
The ETL pipeline and data modeling are written in a single jupyter notebook, data_modeling_with_cassandra.ipynb.

The ETL copies data from the date-partitioned csv files to a single csv file event_datafile_new.csv which is used to populate the denormalized Cassandra tables optimised for the 3 queries above. The 3 tables in the model are named after the song play query they are created to solve:
1. session_songs includes artist, song title and song length information for a given sessionId and itemInSessionId.
2. event_log includes artist, song and user for a given userId and sessionId.
3. song_users includes user names for a given song.

The example queries are returned as pandas dataframes to facilitate further data manipulation. 




