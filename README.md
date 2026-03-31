# MIST4610 - Project 1 - Group 5

## Team Members
1. Caleb Rivers
2. Emmy Nguyen (https://github.com/emmyn1)
3. Catherine Lusick (https://github.com/cl95728)
4. Diyaa Patel (https://github.com/Diyaa-P13/MIST4610---Project-1-Group-5.git)

## Project Description

The purpose of this database is to represent a music group that releases songs and albums from various artists signed to different subsidiary record labels. This project models a music industry database designed to track artists, albums, songs, record labels, contracts, and revenue generated through streaming and unit sales, with artists as the primary entity since their products provide the source of revenue. Managers can use the system to assess artist performance, identify high-performing genres and locations, and make strategic choices about talent acquisition, contract management, and marketing. By querying the database, our team seeks to demonstrate that our database is dependable and valuable for assisting the executive team in understanding the present operations of the music group, while also confirming its capability to support decisions regarding the firm's future. 

## Data Model



## Explanation of Data Model 

The database includes entities like Artist, Artist Group, Album, Song, Producer, Song Producer, Producer, Record Label, Location, Total Units, Streams Total, and Sales.

Record Label represents the subsidiary for what each artist is signed to. Its purpose is being the child table of location, since a location could include multiple record labels. There are also other attributes, like the album's unique identifier, its name, the city where it is based, and the year it was established. 

Location represents the relevant areas that contain producers, record labels, and artists. Because none of these entities can have more than one location, the entity has no foreign keys. 

- Each Artist has a single Record Label and a single Location
- An Artist may put out more than one Album
- There are several Songs on each Album
- Songs generate streaming data through the Stream Total table
- Unit Total and Sales tables are how albums make money
- A junction table links Producers to Songs

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

Query 1 retrieves album names and release dates for a specific artist by filtering the Album table using the artist’s ID. It provides a simple view of the artist’s discography. This query gives management quick access to an artist’s portfolio of work and track their release history. Understanding an artist’s output is important for planning future releases and activities. It also provides an idea of an artist’s content production and an overview of their career progression. 




2. Which songs are the most popular based on streaming?

Query 2  retrieves song titles and their total stream counts by joining the Song and Stream Total tables. It ranks songs in descending order and returns the top 10 most-streamed tracks. This query allows management to have a better understanding of which songs are currently the most popular among listeners. High streaming numbers indicate strong audience engagement and can guide the company’s promotion decisions. The results can also be utilized to maximize revenues from streaming platforms. 



3. Which albums have sold above 9,000,000 streams?

Query 3 retrieves album names and total units sold by joining Album and Unit Total tables. It filters for albums exceeding 9,000,000 units and orders them from highest to lowest sales. This query helps management identify which albums are performing well in terms of sales volume. By focusing on high-selling albums, the label can prioritize its resources for the successful projects. This insight can guide future investment strategies and production decisions.



 
4. Which hip hop feature has the most streams?




5. Which record label has released the most albums

This query calculates the total number of albums released by each record label by joining the Album, Artist, and Record Label tables. It organizes the data by record label and counts the number of albums linked to each label, and then it arranges the results in descending order. This query assists management in determining which record labels are generating the most albums. Being able to identify which label is effectively, provides insight into overall label performance and market presence. This data can help make decisions about investments, resource distribution, and collaborations with successful labels.




6. Where should we look for new talents? (Which location generates the most revenue)




7. Do pre or post 2000s albums generate the most sales?




8. Which record label has released the most albums?




9. Which artists have more total album sales than the average total sales of all artists?

This query calculates the total album sales for each artist by joining the Artist, Album, and Unit total tables. By comparing, each artist’s total sales to the average total sales across all artists using a subquery, it returns only those artists whose sales are higher than the average. This query assists management in determining artists who are exceeding average sales performance. These insights can help make decisions regarding marketing spending, resource distribution, contract extensions, and focusing on top-performing artists within the company.


10. Which locations have a city name that ends with "ville" (REGEX)





11. Display producers who have never worked on a song in the Hip Hop genre (NOT EXISTS)




## Table for Queries


## Database Information
Name of the database: al_Group_21482_G5
