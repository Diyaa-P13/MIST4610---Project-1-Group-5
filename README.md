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

The database includes entities like Artist, Album, Song, Record Label, Contract, Producer, and Sales.

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
2. Which hip top feature has the most streams
3. Which record label has released the most albums
4. ?

### Complex Queries
1. Top 5 artists by revenue
2. Artists with contracts ending soon
3. Best location for new talent
4. Do pre or post 2000 albums generate the most sales
5. Which artists have more total album sales than the average total sales of all artists
6. ?

## Database Information
Name of the database: al_Group_21482_G5
