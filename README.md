# MIST4610 - Project 1 - Group 5

## Team Members
1. Caleb Rivers
2. Emmy Nguyen
3. Catherine Lusick
4. Diyaa Patel

## Scenario Description

This project models a music industry database designed to track artists, albums, songs, record labels, contracts, and revenue generated through streaming and unit sales. 

Managers can use the system to assess artist performance, identify high-performing genres and locations, and make strategic choices about talent acquisition, contract management, and marketing. 

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
