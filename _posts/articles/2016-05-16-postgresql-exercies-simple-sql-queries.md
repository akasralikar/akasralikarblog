---
title: PostgreSQL Exercies Simple SQL Queries
excerpt: "In this article I am going to explain basic SQL queries with examples. I would be covering various use cases and present article in form of exercise with answers and brief discussion."
tags: [postgresql]
comments: true
featured: true
author: Anirudha Kasralikar
date: 2016-05-08 11:27:43
modified: 2016-05-11 01:27:43
https://pgexercises.com/questions/basic/
---

This post deals with various PostgreSQL Exercises. You can find lot of information online on Database management systems but it seems that there is not much content which helps learning in more structured fashion. I hope you find below approach it helpful.

{% include toc.html %}

You can find below exercises that deals with basics of SQL. If you are totally new to SQL then you can start by reading book [Learning SQL](http://shop.oreilly.com/product/9780596007270.do "Learning SQL"){:target="_blank"} or if you prefer learning online then series at [Learn code the hard way](http://sql.learncodethehardway.org/book/ "Learn code the hard way"){:target="_blank"} is good place to start. 

## Simple SQL Queries

### Fetch all data from given table
{% highlight sql %}
SELECT 
  * 
from 
  table;
{% endhighlight %}

### Fetch specific columns from given table
{% highlight sql %}
SELECT 
  column_1, 
  column_2 
FROM
  table;
{% endhighlight %}

### Decide which rows are fetched
{% highlight sql %}
SELECT
  * 
FROM 
  table 
WHERE
  ( boolean conditional check like column_1 > 0 );

SELECT 
  * 
FROM 
  table 
WHERE
  ( conditional check ) 
  [conditional operator like AND / OR] ( conditional check );
{% endhighlight %}
 
### String searches
{% highlight sql %}
SELECT 
	*
FROM
	table
WHERE
	column LIKE '%string_to_search%';
{% endhighlight %}

### Searching against different possible values
{% highlight sql %}
SELECT 
	*
FROM
	table
WHERE
	column IN ( value_1, value_2, value_3 );
{% endhighlight %}

### Arrange results into various streams
{% highlight sql %}
SELECT
	column_1, 
	CASE 
		WHEN ( boolean conditional check like column_1 > 0 ) 
		THEN 'IF '
		ELSE 'ELSE '
	END AS cost
FROM
	table;
{% endhighlight %}

### Comparing dates
{% highlight sql %}
SELECT
  *
FROM
	table
WHERE
	table >= '05/16/2016'; -- Usually when column is of type date
	OR table > '2012-05-16'; -- Usually when column is of type date or timestamp
	OR table >= '2012-05-16 00:00:00'; -- Usually when column is of type date or timestamp
{% endhighlight %}

### Removing duplicate records
{% highlight sql %}
SELECT 
	DISTINCT column
FROM
	table;
{% endhighlight %}

### Ordering results
{% highlight sql %}
SELECT 
	*
FROM
	table
ORDER BY
  column -- ( ASC / DESC )
{% endhighlight %}

### Limiting records from result
{% highlight sql %}
SELECT 
	*
FROM
	table
LIMIT 100;
{% endhighlight %}

### Combining results from multiple queries
{% highlight sql %}
SELECT column_1 FROM table_1
UNION
SELECT column_2 FROM table_2;
{% endhighlight %}

### Calling aggregate functions
{% highlight sql %}
SELECT 
	MAX(column) 
FROM 
	table;
{% endhighlight %}

{% highlight sql %}
SELECT 
  column_1,
  column_2,
  column
FROM
  table
WHERE
  column = ( SELECT MAX(column) FROM table );
{% endhighlight %}

## Joins and Subqueries

### Retrieve date
{% highlight sql %}
SELECT 
	t_1.column
FROM
	table_1 AS t_1 
	JOIN table_2 AS t_2 ON ( t_1.id = t_2.id );
{% endhighlight %}

### Work out the start times of bookings for tennis courts
{% highlight sql %}

{% endhighlight %}

### Produce a list of all members who have recommended another member
{% highlight sql %}

{% endhighlight %}

### Produce a list of all members, along with their recommender
{% highlight sql %}

{% endhighlight %}

### Produce a list of all members who have used a tennis court
{% highlight sql %}

{% endhighlight %}

### Produce a list of costly bookings
{% highlight sql %}

{% endhighlight %}

### Produce a list of all members, along with their recommender, using no joins.
{% highlight sql %}

{% endhighlight %}

### Produce a list of costly bookings, using a subquery
{% highlight sql %}

{% endhighlight %}

