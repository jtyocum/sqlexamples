# SQLite Examples

[SQLite Manager](https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/)

# The Basic SELECT Statement

With a SELECT statement, you tell the database what you want, and where you want to get it from.

The following example, tells the database we want to SELECT all the columns (*) FROM the survey table;

```
SELECT * FROM survey;
```

# The WHERE Clause

A basic SELECT statement simply grabs some columns and returns their values. The WHERE clause enables you to filter the data being returned.

Like our last example, we'll SELECT all the columns FROM the survey table. However, we only want records WHERE the age is greater than 55.

```
SELECT * FROM survey WHERE age > 55;
```

# The ORDER BY Clause

The ORDER BY clause sorts the records using by putting the values within a column in ASCending or DESCending order.

Just like previously, we'll SELECT all the columns FROM the survey table. And, we only want records WHERE age is greater than 55. Now, we want them ORDERed BY their moincome (monthly income) in DESCending order.

```
SELECT * FROM survey WHERE age > 55 ORDER BY moincome DESC;
```

# COUNTing Function

The COUNT function enables you to COUNT the number of records that match some condition.

Unlike previous examples, we aren't SELECTing a column. In this case, we'll SELECT a COUNT of all records FROM the survey table WHERE age is greater than 55.

```
SELECT COUNT(*) FROM survey WHERE age > 55;
```

# The GROUP BY Clause

The GROUP BY clause groups records together based on a common value. For example, you could GROUP BY age.

In this example, we'll SELECT the age column, and COUNT the records' age column FROM the survey table. The records are GROUPed BY age, and ORDERed BY age;

The result of this query? A list of each age, and a COUNT of how many survey respondents have that age.

```
SELECT age,COUNT(age) FROM survey GROUP BY age ORDER BY age;
```

# JOINing Other Tables

Up till this point, all of the examples utilized one database table.

```
SELECT * FROM survey JOIN respondents ON rid = id;
```
