# MySQL Queries Notes

## Table of Contents
- [Introduction](#introduction)
- [Basic Queries](#basic-queries)
  - [Selecting Data](#selecting-data)
  - [Inserting Data](#inserting-data)
  - [Updating Data](#updating-data)
  - [Deleting Data](#deleting-data)
- [Joins](#joins)
  - [Inner Join](#inner-join)
  - [Left Join](#left-join)
  - [Right Join](#right-join)
  - [Full Join](#full-join)
- [Aggregate Functions](#aggregate-functions)
  - [COUNT](#count)
  - [SUM](#sum)
  - [AVG](#avg)
  - [MIN and MAX](#min-and-max)
- [Subqueries](#subqueries)
- [Indexes](#indexes)
- [Stored Procedures](#stored-procedures)
- [Common Errors and Solutions](#common-errors-and-solutions)
- [Best Practices](#best-practices)

## Introduction
MySQL is a relational database management system (RDBMS) that uses structured query language (SQL) to manage and manipulate data. This document provides a collection of commonly used MySQL queries along with explanations and examples.

## Basic Queries

### Selecting Data
- **SELECT Operations**
```sql
SELECT * FROM DBName.table_name;

select column_1,column_2 FROM DBName.table_name;

select * from DBName.table_name where column_name="value";
```

### AND OR NOT Operation

- **AND Operations**
```sql
select column_1,column_2 from DBName.table_name WHERE column_x = "value_x" AND column_y="value_y";

Example:
select Name,Published, Categories, Type from outfitweb.`products-outfitmart` WHERE Type = "simple" AND Categories="Watches";
```
Return All the Row Where both the conditions are true Only.


- **OR Operations**
```sql
select column_1,column_2 from DBName.table_name WHERE column_x = "value_x" Or column_y="value_y";

Example:
select Name,Published, Categories, Type from outfitweb.`products-outfitmart` WHERE Type = "variation" or Categories="Watches";
```
Return All the Row Where one of them or both the conditions are true Only.


- **Not Operations**
```sql
select column_1,column_2 from DBName.table_name WHERE NOT column_x = "value_x" ;

Example: 
select Name,Published, Categories, Type from outfitweb.`products-outfitmart` WHERE not Type="simple";
```
Return All the Row Except the not conditioned.


## Like Operation

- **like Operations**
```sql
select * from DBName.table_name WHERE like "%search_word%";

Example:
select * from outfitweb.`products-outfitmart` where Name like "coas%";
```
Like Operator use to search where a data has something known key word. Use `%` before or after to addressing whether the search keyword has the anything before or after.

- `Exercise: Try Like Operator with NOT condition`


## Order by Operation

- **order by One Condition Operations**
```sql
select * from DBName.table_name order by column_1 asc;

Example:
select * from outfitweb.`products-outfitmart` order by `Regular price` asc;
```
Order By shows data in ascending or descending manner

- **order by Two Condition Operations**

```sql
select * from DBName.table_name order by column_1 asc, column_2 desc;

Example:
select * from outfitweb.`products-outfitmart` order by `Regular price` asc, Type desc;
```
It can be also use with more than one condition

- `Exercise: Try order by asc/desc Operations on sakila.payments Database`


## Limit Operation

- **Limit Operations**
```sql
select * from DBName.table_name order by column_1 asc limit "value";

Example:
SELECT * FROM sakila.film order by length asc limit 50;
```
Limit operation sets the limit for the output for example if i say `limit 100` it will show me the top 100 results.

- `Exercise: Limit operation with order by asc/desc`


## In Operation

- **In Options Operations**
```sql
select * from DBName.table_name where column_1 IN ("val_1","val_2");

Example:
SELECT * FROM sakila.city where country_id in ("44", "101"); 

```
In operation returns the output for selected values. Make sure to type values in `("val_1","val_2")` .


- **Not In Options Operations**

```sql
select * from DBName.table_name where column_1 NOT IN ("val_1","val_2");

Example:
SELECT * FROM sakila.city where country_id Not in ("44", "101"); 

```

- `Exercise: Try In operation with and operators`