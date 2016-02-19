# SQLite Examples

# Learning Objectives
This exercise will aid you in learning and understanding:

- How to perform a basic SQL SELECT query
- Provide a brief introduction to SQL functions, like COUNT
- How to sort and filter records using ORDER and GROUP BY
- Querying across multiple tables with JOIN

# Getting Started

1. Install the Firefox plugin, [SQLite Manager](https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/), if you haven't already
2. Download the [Income Survey](https://github.com/jtyocum/sqlexamples/blob/master/income_survey.sqlite) database

# Overview of SQL's SELECT statement

## The Basic SELECT Statement

With a SELECT statement, you tell the database what you want, and where you want to get it from.

The following example, tells the database we want to __SELECT__ all the columns (*) __FROM__ the survey table;

```
SELECT * FROM survey;
```

## The WHERE Clause

A basic SELECT statement simply grabs some columns and returns their values. The WHERE clause enables you to filter the data being returned.

Like our last example, we'll __SELECT__ all the columns __FROM__ the survey table. However, we only want records WHERE the age is greater than 55.

```
SELECT * FROM survey WHERE age > 55;
```

## The ORDER BY Clause

The ORDER BY clause sorts the records using by putting the values within a column in ASCending or DESCending order.

Just like previously, we'll __SELECT__ all the columns __FROM__ the survey table. And, we only want records __WHERE__ age is greater than 55. Now, we want them __ORDER__ed __BY__ their moincome (monthly income) in __DESC__ending order.

```
SELECT * FROM survey WHERE age > 55 ORDER BY moincome DESC;
```

## COUNTing Function

The COUNT function enables you to COUNT the number of records that match some condition.

Unlike previous examples, we aren't SELECTing a column. In this case, we'll __SELECT__ a __COUNT__ of all records __FROM__ the survey table __WHERE__ age is greater than 55.

```
SELECT COUNT(*) FROM survey WHERE age > 55;
```

## The GROUP BY Clause

The GROUP BY clause groups records together based on a common value. For example, you could GROUP BY age.

In this example, we'll __SELECT__ the age column, and __COUNT__ the records' age column __FROM__ the survey table. The records are __GROUP__ed __BY__ age, and __ORDER__ed __BY__ age;

The result of this query? A list of each age, and a COUNT of how many survey respondents have that age.

```
SELECT age,COUNT(age) FROM survey GROUP BY age ORDER BY age;
```

## JOINing Other Tables

Up till this point, all of the examples utilized one database table. With JOIN, you can query across multiple tables, and produce a single output. In order for JOIN to work, each table needs a shared identifier.

In our example database, the *respondents* table contains an id column. Each record in that table has a unique id number, which was assigned sequentially. In the *survey* table, there is a rid column which contains those same id numbers. Thus, we can JOIN the tables using those two columns.

To start, we'll __SELECT__ all the columns __FROM__ the survey table. Then __JOIN__ it with the respondents table __ON__ the rid and id columns.

```
SELECT * FROM survey JOIN respondents ON rid = id;
```

Sometimes SELECTing all the columns will result in an output which isn't easy to read. And, when you JOIN other tables, the order of the columns may not make sense.

So let's __SELECT__ the fname, lname, gender, age, and moincome columns __FROM__ the survey table. And, __JOIN__ the respondents table __ON__ the rid and id columns.

```
SELECT fname,lname,gender,age,moincome FROM survey JOIN respondents ON rid = id;
```

# Test Your Knowledge

As you've seen in the examples, you can combine various SQL functions, clauses, and keywords to produce desired results.

## SELECting Columns

From the respondents table, select only the fname, and lname columns.

## ORDERing BY Monthly Income

From the survey table, select the age, gender, and moincome columns. Order the records (rows) by the Monthly Income (moincome) column in ascending order.

## JOIN Both Tables

Select the fname, lname, age, and moincome columns from both tables. Order the records by the lname column in descending order.
