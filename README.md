# MIST4610 - Project 1 - Group 5

## Team Members
1. Catherine Lusick (https://github.com/cl95728)
2. Emmy Nguyen (https://github.com/emmyn1)
3. Caleb Rivers (https://github.com/CRivers2805/MIST_4610_21482_G5_CMR)
4. Diyaa Patel (https://github.com/Diyaa-P13/MIST4610---Project-1-Group-5.git)

## Project Description

The purpose of this database is to represent a music group that releases songs and albums from various artists signed to different subsidiary record labels. This project models a music industry database designed to track artists, albums, songs, record labels, contracts, and revenue generated through streaming and unit sales, with artists as the primary entity since their products provide the source of revenue. Managers can use the system to assess artist performance, identify high-performing genres and locations, and make strategic choices about talent acquisition, contract management, and marketing. By querying the database, our team seeks to demonstrate that our database is dependable and valuable for assisting the executive team in understanding the present operations of the music group, while also confirming its capability to support decisions regarding the firm's future. 

## Data Model

<img width="610" height="609" alt="Screenshot 2026-03-31 at 11 45 10 AM" src="https://github.com/user-attachments/assets/94599c69-c22a-4616-bd59-91f27dc95c18" />

## Explanation of Data Model 

The database includes entities like Artist, Artist Group, Album, Song, Producer, Song Producer, Producer, Record Label, Location, Total Units, Streams Total, and Sales.

Record Label represents the subsidiary for what each artist is signed to. Its purpose is being the child table of location, since a location could include multiple record labels. There are also other attributes, like the album's unique identifier, its name, the city where it is based, and the year it was established. 

Location represents the relevant areas that contain producers, record labels, and artists. Because none of these entities can have more than one location, the entity has no foreign keys. A location's state, city, and ZIP code is represented in the model. 

The Artist is the core entity and has the most amount of relations with other entities in the database. The attributes of an artist include their unique idenitifier, stage and legal name, the date of their first album release, age, and foreign keys connecting them to location and record label because record labels and locations can have multiple artists. 

The Album is a grouping of songs released at one time, and are used to fulfill contracts by the artists. Albums have their unique identifier, and are described by their name and release date. They have foreign keys linking them to artist and units sold because artists can have multiple albums, and multiple albums can have the same amount of units sold. 

Albums are composed of songs, which is also an essential entity in our model. Songs serve as the core product in the form of streams (along with physical vinyl sales), and are essential in determining revenue metrics. Each song has a unique identifier, which is a combination of artist ID, album ID, and the track number of the song. Other attributes include the song name, runtime, genre, and maturity rating, each essential features that can affect the revenue of a track. Foreign keys compose of album ID and stream total, as an album has many songs, and multiple songs can have the same amount of streams. 
 
Artist Group represents the associative entity between songs and artists, as an artist can have many songs, and an undeniably have many songs, and a song can also have many artists working on it. To accurately model this relationship, we implemented a three-way composite primary key, with each row having a unique combination of group ID, artist ID, and song ID. The only other attribute that is attributed to this entity is group name, which describes each artist that works on a song in one cell. 
 
In addition to an artist, each song also has a producer that composes the instrumentals and mixes the track. Producer is modeled similarly to artist, with producer ID, producer name, and producer age as it’s independent attributes, and location ID as its foreign key 
 
Similarly to artists, a producer can work on many songs, and a song can also be composed by many producers. As such, another associative entity, song producer, was made to represent this relationship. The only attributes are its three-way composite primary key consisting of song producer ID, producer ID, and song ID 
 
The Unit Total Entity was created to represent the amount of physical media (i.e. vinyl and CDs) that an album sells throughout its lifetime. This entity is composed of its unique identifier, the total quantity of units that an album has sold, and a foreign key linking the table to sales, which will be expanded upon below. 
 
Streams is another avenue for an artist to generate revenue, so this is also modeled in its own entity. However, unlike being related to albums like units total, streams is related to songs, since people can stream songs individually and do not have to listen to an entire album for a stream to register. Streams include a unique identifier, the total quantity of streams generated, and the foreign key linking this entity to sales. 
 
Lastly, but perhaps most essential, is sales. This is the table that holds the revenue generated from both units sold and streams. Although a relatively simple table, sales offer the most critical data that is found in the database, and can offer the most insight as to what direction the firm needs to move in. Despite only consisting of a unique identifier and the revenue generated by each distribution channel, it is used in many of our queries to determine which artists prove to be most valuable. 

## Data Dictionary

### Artist Table 
| Column Name | Data Type | Description | 
|------------|----------|------------| 
| artistID | INT | Unique identifier for each artist | 
| legalName | VARCHAR | Artist's legal name |  
| stageName | VARCHAR | Artist's stage name | 
| debutDate | INT | Year that artist debuted |  
| artistAge | INT | Current age of the artist |  
| locationID | INT | References the artist's location |  
| recordLabelID | INT | Foreign key referencing the record label associated with the artist | 
 

### Artist Group 
| Column Name | Data Type | Description | 
|------------|----------|------------| 
| groupID | INT | Unique identifier for a collaboration group involving multiple artists on a song | 
| artistID | INT | Foreign key referencing an artist participating in the group |  
| songID | INT | Foreign key referencing the song associated with the group collaboration |  
| groupName | VARCHAR | Name of the artist group or collaboration |  
 

### Location 
| Column Name | Data Type | Description | 
|------------|----------|------------| 
| locationID | INT | Unique identifier for each location |  
| state | VARCHAR | State abbreviation where the location is based |  
| city | VARCHAR | City name of the location |  
| zipCode | INT | ZIP code associated with the location |  
 

### Contract 
| Column Name | Data Type | Description | 
|------------|----------|------------| 
| contractID | INT | Unique identifier for each contract |  
| startDate | DATE | Date the contract begins |  
| endDate | DATE | Date the contract ends |  
| royaltyRate | DECIMAL | Percentage of revenue paid to the artist |  
| advanceAmount | DECIMAL | Upfront payment given to the artist |  
| albumQty | INT | Number of albums required under the contract |  
| artistID | INT | Foreign key referencing the artist associated with the contract |  
 

### Record Label 
| Column Name | Data Type | Description | 
|------------|----------|------------| 
| recordLabelID | INT | Unique identifier for each record label |  
| labelName | VARCHAR | Name of the record label |  
| hqCity | VARCHAR | City where the laebl is headquartered |  
| yearFounded | INT | Year the record label was established |  
| locationID | INT | Foreign key referencing the location of the record label |  
 

### Album  
| Column Name | Data Type | Description | 
|------------|----------|------------| 
| albumID | INT | Unique identifier for each album |  
| albumName | VARCHAR | Name/title of the album |  
| releaseDate | DATE | Date of the album was released |  
| artistID | INT | Foreign key referencing the artist who created the album |  
| unitsSoldID | INT | Foreign key referencing the units sold record associated with the album |  
 

### Song  
| Column Name | Data Type | Description | 
|------------|----------|------------| 
| songID | INT | Unique identifier for each song | 
| songTitle | VARCHAR | Title of the song |  
| songDuration | VARCHAR | Duration of the song in minutes and seconds |  
| songGenre | VARCHAR | Genre classification of the song |  
| explicit | VARCHAR | Indicates whether the song contains explicit content (Yes/No) | 
| trackNumber | INT | Position of the song within the album |  
| albumID | INT | Foreign key referencing the album the song belongs to |  
| streamTotalID | INT | Foreign key referencing the total streaming data for the song |  
 

### Producer 
|Column Name | Data Type | Description | 
|------------|----------|------------| 
| producerID | INT | Unique identifier for each producer |  
| producerName | VARCHAR | Name of the music producer |  
| producerAge | INT | Age of the producer |  
| locationID | INT | Foreign key referencing where the producer is based in |  
 

### Song Producer  
|Column Name | Data Type | Description | 
|------------|----------|------------| 
| songProducerID | INT | Unique identifier for each song-producer relationship | 
| producerID | INT | Foreign key referencing the producer associated with the song |  
| songID | INT | Foreign key referencing the song associated with the producer |  
 

### Sales 
|Column Name | Data Type | Description | 
|------------|----------|------------| 
| salesID | INT | Unique identifier for each sales record |  
| revenueAmount | DECIMAL | Total revenue generated from sales |  

## Queries 

1. Show all the albums for a specific artist

<img width="372" height="341" alt="Screenshot 2026-03-31 at 11 47 00 AM" src="https://github.com/user-attachments/assets/904d0f75-0346-45c5-8eae-00b35ae1b9ec" />

Query 1 retrieves album names and release dates for a specific artist by filtering the Album table using the artist’s ID. It provides a simple view of the artist’s discography. This query gives management quick access to an artist’s portfolio of work and track their release history. Understanding an artist’s output is important for planning future releases and activities. It also provides an idea of an artist’s content production and an overview of their career progression. 

2. Which songs are the most popular based on streaming?

<img width="514" height="364" alt="Screenshot 2026-03-31 at 11 48 15 AM" src="https://github.com/user-attachments/assets/9fb79f32-e58b-44d0-80f5-d7d6cf102f0b" />

Query 2 retrieves song titles and their total stream counts by joining the Song and Stream Total tables. It ranks songs in descending order and returns the top 10 most-streamed tracks. This query allows management to have a better understanding of which songs are currently the most popular among listeners. High streaming numbers indicate strong audience engagement and can guide the company’s promotion decisions. The results can also be utilized to maximize revenues from streaming platforms. 

3. Which albums have sold above 9,000,000 streams?

<img width="438" height="379" alt="Screenshot 2026-03-31 at 11 49 08 AM" src="https://github.com/user-attachments/assets/e973b018-4cd9-4a3c-a1f6-21c1c3fadaf2" />

Query 3 retrieves album names and total units sold by joining Album and Unit Total tables. It filters for albums exceeding 9,000,000 units and orders them from highest to lowest sales. This query helps management identify which albums are performing well in terms of sales volume. By focusing on high-selling albums, the label can prioritize its resources for the successful projects. This insight can guide future investment strategies and production decisions.
 
4. Which hip hop feature has the most streams?

<img width="633" height="300" alt="Screenshot 2026-03-31 at 11 50 58 AM" src="https://github.com/user-attachments/assets/de97068d-e7ce-441f-89a4-87a12201ea11" />

This query is meant to identify which hip hop group feature generates the largest number of streams. Some groups have multiple collaborations, so for more accurate results, the total streams earned by each group are divided by the number of songs they have in the database. As shown in the results, J Cole and Trey Songz have garnered the most streams per song, so it would be wise to get both artists back into the studio to produce another hit. Additionally, JID’s features make up most of the top 50%, so he seems to work well with other artists. Lastly, Kendrick Lamar’s features tend to lack streams, so maybe the label should encourage him to stick to solo work. 

5. Where should we look for new talents? (Which location generates the most revenue)

<img width="546" height="336" alt="Screenshot 2026-03-31 at 11 52 16 AM" src="https://github.com/user-attachments/assets/7f9a1b45-5d09-4371-b94d-d8ce4a4c36aa" />

This query is meant to give insight on which cities generate the most revenue per artist. By joining many tables across the database, we can attach revenue values to all of the locations in our database. Additionally, dividing by artist creates less skewed data, as the cities with more artists will not be overrepresented. As seen in the results, Chapel Hill, Duluth, Houston, and Charleston have shown massive returns for their respective artists, so perhaps the culture and connections these artists can create in their cities can allow for similar artists from their area to develop and follow in their footsteps. Therefore, more resources should be given to talent scouts and local development in those areas. 

6. Do pre or post 2000s albums generate the most sales?

<img width="631" height="298" alt="Screenshot 2026-03-31 at 11 53 17 AM" src="https://github.com/user-attachments/assets/b7ef1888-3f3d-4822-9334-8771b2b58fd2" />

This query displays the dichotomy of the revenue generated from albums before and after the year 2000. By using the UNION command, we can observe both calculations side by side. REGEXP was used to distinguish between albums made before and after the turn of the millennium. The results state that pre-2000s albums still have generated more money per album on average than post 2000s albums. This should alert management that they need to keep these albums available for purchase and to not phase them out. It would also be wise to renew contracts of artists that made music in the 1900s, as they not only drove up sales, but they have a positive reputation amongst the public. This isn’t to say that newer artists should not be prioritized, as their sales numbers are very close to those of the older albums, however management should not ignore the lasting impact that older works have created. 

7. Which record label has released the most albums?

<img width="381" height="365" alt="Screenshot 2026-03-31 at 11 54 13 AM" src="https://github.com/user-attachments/assets/ebf51dae-4ae5-4b6b-8524-a415cf00037e" />

This query calculates the total number of albums released by each record label by joining the Album, Artist, and Record Label tables. It organizes the data by record label and counts the number of albums linked to each label, and then it arranges the results in descending order. This query assists management in determining which record labels are generating the most albums. Being able to identify which label is effectively, provides insight into overall label performance and market presence. This data can help make decisions about investments, resource distribution, and collaborations with successful labels.

8. Which artists have more total album sales than the average total sales of all artists?

<img width="573" height="261" alt="Screenshot 2026-03-31 at 11 55 08 AM" src="https://github.com/user-attachments/assets/e16dd246-b769-4725-94ef-c41de50c7d96" />

This query calculates the total album sales for each artist by joining the Artist, Album, and Unit total tables. By comparing, each artist’s total sales to the average total sales across all artists using a subquery, it returns only those artists whose sales are higher than the average. This query assists management in determining artists who are exceeding average sales performance. These insights can help make decisions regarding marketing spending, resource distribution, contract extensions, and focusing on top-performing artists within the company.


9. Which locations have a city name that ends with "ville" (REGEX)?

<img width="389" height="250" alt="Screenshot 2026-03-31 at 11 55 42 AM" src="https://github.com/user-attachments/assets/2f3bb348-976d-4680-9969-cdc29801e541" />

This query was created to pull a list of all cities in the Location table that ends with the letters "ville". To make the list clean and easy to read, I used a Regular Expression to find the pattern and grouped the results by city. This query helps filter through the location data more effectively. Instead of scrolling through rows of data, this helps identify specific areas based on their name. 

10. Display producers who have never worked on a song in the Hip Hop genre (NOT EXISTS)

<img width="365" height="227" alt="Screenshot 2026-03-31 at 11 55 53 AM" src="https://github.com/user-attachments/assets/cab4e401-7ade-4b19-b429-baddf7f38aee" />


Query 10 is designed to find the names of producers in the Producer table who have never been associated with a "Hip Hop" song. To do this, I used a NOT EXISTS subquery to filter anyone linked to that specific genre. For every producer, the subquery checks the Song Producer table to see if they are linked to any song labeled 'Hip Hop'. If the subquery finds any match, NOT EXISTS becomes false, and that producer is excluded. This logic can be used to isolate producers who work exclusively in other genres like Country or Pop. It’s a great way to find a music producer whose specialty does not fall in Hip Hop. 

## Table for Queries

| Feature                   | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |  
|---------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------| 
| Multiple Table Join       |         |    X    |    X    |    X    |    X    |    X    |    X    |    X    |         |     X    | 
| Subquery                  |         |         |         |         |         |         |         |    X    |         |          | 
| GROUP BY                  |         |         |         |         |    X    |         |    X    |    X    |         |          | 
| GROUP BY with HAVING      |         |         |         |    X    |         |         |         |         |         |          | 
| Multi-condition WHERE     |         |         |    X    |         |         |         |         |         |         |          | 
| Built - in Functions      |         |    X    |    X    |    X    |    X    |    X    |    X    |    X    |         |          | 
| REGEXP                    |         |         |         |         |         |    X    |         |         |    X    |          |  
| NOT EXISTS                |         |         |         |         |         |         |         |         |         |     X    | 
| WHERE Clause              |    X    |         |         |    X    |         |    X    |         |         |         |          | 
| Basic SELECT              |    X    |         |         |    X    |    X    |    X    |         |         |         |          | 
| Union                     |         |         |         |         |         |    X    |         |         |         |          | 

## Database Information
Name of the database: al_Group_21482_G5
