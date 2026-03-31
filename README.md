# MIST4610 - Project 1 - Group 5

## Team Members
1. Caleb Rivers
2. Emmy Nguyen (https://github.com/emmyn1)
3. Catherine Lusick (https://github.com/cl95728)
5. Diyaa Patel

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

## Queries 

### Simple Queries 
1. Show all the albums for a specific artist
2. Which songs are hte most popular based on streaming?
3. Which albums have sold above 9,000,000 streams?
4. Which hip hop feature has the most streams?
5. Which record label has released the most albums (mine)

### Complex Queries
1. Where should we look for new talents? (Which location generates the most revenue)
2. Do pre or post 2000s albums generate the most sales?
3. Which record label has released the most albums?
4. Which artists have more total album sales than the average total sales of all artists? mine)
5. Whhich locations have a city name that ends with "ville" (REGEX)
6. Display producers who have never worked on a song in the Hip Hop genre (NOT EXISTS)


## Database Information
Name of the database: al_Group_21482_G5
