# sql-exploration
A collection of exploratory exercises to improve SQL skills.

## Basic Syntax and Query Design

### `01-animals_db`

#### Create a Database
To create a database in pgAdmin, follow these steps:

1. In the pgAdmin editor, right-click `PostgreSQL 15` on the left-hand side panel.

2. From the menu, hover `Create` to instantiate a new database.

3. Enter `animals_db` as the database name. Make sure the owner is set as the default `postgres`, and then click Save.

#### Create a Table
- `01-create_tables.sql` contains a sample table creation script with several different data types.

#### Insert Values
- `02-insert_values.sql` contains a sample record insertion script that demonstrates basic data entry.

#### Query All Records
- `03-query_all_records.sql` contains the most basic full-table query script.
- `03-query_all_records_results.csv` shows the query results.

#### Filtered Query
- `04-filtered_query.sql` contains a query script that retrieves only some fields from records that meet several criteria.
- `04-filtered_query_results.csv` shows the query results.

#### Delete, Recreate and Populate Tables
- `05-delete_create_tables_with_primary_keys.sql` contains a script that demonstrates how to drop a table, recreate it with a sequential primary key, and populate it.
- `05-query_all_with_primary_key_results.csv` shows the results of those actions.

#### Updating, Deleting and Bulk Importing Data
- `06-dave_query.sql` contains a filtered query script.
- `06-dave_query_results.csv` contains the results of that query.
- `07-update_record.sql` contains a script that demonstrates how to update records that meet particular criteria.
- `07-update_record_query_results.csv` conains the results of a query meant to visualize the effects of the above.
- `08-drop_duplicate.sql` demonstrates deleting a record based on a unique ID.
- `08-drop_duplicate_query_results.csv` conains the results of a query meant to visualize the effects of the above.
- `09-create_table_fauna_vertebrate.sql` creates a new, unpopulated table.
- `10-insert_values_fauna_vertebrate.sql` populates the new table.
---

### `02-city_info`

#### Procedure
1. Create a new database in pgAdmin named `city_info`.
2. Using the query tool, create an empty table named `cities`. Be sure to match the data types!
3. Insert data into the new table. The result should match the following image.

    ![cities_table.png](images/cities_table.png)
    
    city<br>character varying (30) | state<br>character varying (30) | population<br>integer |
    |----|----|----|
    | Alameda | California | 79177 |
    | Mesa | Arizona | 496401 |
    | Boerne | Texas | 16056 |
    | Anaheim | California | 352497 |
    | Tucson | Arizona | 535677 |
    | Garland | Texas | 238002 |

4. Query the table to recreate the image below.

    ![cities_only.png](images/cities_only.png)
    
    | city<br>character varying (30) |
    |----|
    | Alameda |
    | Mesa |
    | Boerne |
    | Anaheim |
    | Tucson |
    | Garland |
    
#### Additional Exploration
1. Filter the table to view only cities in Arizona.

2. Filter the table to view only cities with a population of less than 100,000.

3. Filter the table to view California cities with a population of less than 100,000.

##### Notes
* The first and second `Additional Exploration` tasks use a [`WHERE` clause](https://www.tutorialspoint.com/sql/sql-where-clause.htm) to filter the original query.
* The third `Additional Exploration` task uses an [`AND` clause](https://www.tutorialspoint.com/sql/sql-and-or-clauses.htm).
---

### `03-programming_db`

#### Procedure
1. Create a new database named `programming_db`.

2. Create the `programming_languages` table using the following image.

    ![programming_languages.png](images/programming_languages.png)

    | id<br>integer | language<br>character varying (20) | rating<br>integer |
    |----|----|----|
    | 1 | HTML | 95 |
    | 2 | JS | 99 |
    | 3 | JQuery | 98 |
    | 4 | MySQL | 70 |
    | 5 | MySQL | 70 |

3. Query the table to return the rows containing MySQL, and then delete one of the duplicates.

4. Insert a few more rows of data for additional programming languages by adding the `language` and `rating` of your choice to the `programming_languages` table.

5. Change the name of the JS language to JavaScript.

6. Change the rating for HTML to 90.

### Additional Exploration
1. Create a Boolean column named `expert` that has a default value of `true` in the `programming_languages` table.
---

### `04-miscellaneous_db`

#### Procedure
1. Open the `soft-attributes.csv` CSV file from the `resources` folder to analyze the data.

2. Using the column headers and data types from the CSV file, write the table schema to create a new table in the `miscellaneous_db` database called `movie_words_comparison`.

3. Import the data from the `soft-attributes.csv` file in the `resources` folder.

4. Create a query that collects all rows where `Home Alone (1990)` is in the `reference_title` column.

5. Create a query that collects all rows where the rater is within the 10-15 range.

6. Create a query that searches for the words `artsy` and `heartfelt` in the `soft_attribute` column.

#### Additional Exploration
1. Create a query that will collect all rows with a reference title of `Batman (1989)` and a soft attribute of `scary`.
2. Create a query that will collect all rows with a rater within the 30-40 range and has a reference title of `Home Alone (1990)` and a soft attribute of `artsy`.
---

### 05-CRUD
An exploration of CRUD operations (Create, Read, Update, Delete) on data provided by Berkeley Data Science Bootcamp.

#### Procedure
1. Create a new database named `Malaysia` in pgAdmin.
2. Create two new tables in the `Malaysia` database by copying the code provided in `schema.sql` into a new query window in pgAdmin.
3. Using the Import/Export tool, import the data from `mys_road_accidents.csv` into the `road_accidents` table, and then import the data from `mys_accidents_by_state.csv` into the `accidents_by_state` table.
4. In the `road_accidents` table, find the row that has a `road_crashes` value of 0 and note:

    * the year
        - 2017
    * the number of `road_deaths`
        - 6,740
    * the names of the other two columns have missing data (0 values)
        - `Road_Crashes`
        - `Serious_Injury`
    
5. In the `accidents_by_state` table, delete all rows for years that do not have data missing from the `road_accidents` table.
6. In the `accidents_by_state` table, in a single SQL query, find the [Sum](https://www.w3schools.com/sql/sql_count_avg_sum.asp) of each of the three columns with missing data, as well as `road_deaths`, and rename the summed columns with their original column name using `AS`. Compare the sum of `road_deaths` from these results with the value from the `road_accidents` table. If they do not match, the other values will also be incorrect.
7. Once the `road_deaths` values match up, note the values for the three columns with missing data, and update the `road_accidents` table with this new information.

#### Additional Exploration
1. Delete all rows from `accidents_by_state` and re-import the data from `mys_accidents_by_state.csv`. If you import the data again without deleting the rows, you will have duplicated data.

2. Without deleting any rows, calculate the sum of `road_crashes`, `road_deaths`, `serious_injury`, and `slight_injury` for a subsequent year, and add those values plus the year to the `road_accidents` table.
---

### `06-commodities_db`
An exploration of the five primary types of joins that can be used with PostgreSQL:
* `INNER JOIN` returns records that have matching values in both tables.
* `LEFT JOIN` returns all records from the left table and the matched records from the right table.'
* `RIGHT JOIN` returns all records from the right table and the matched records from the left table.
* `CROSS JOIN` returns records that match every row of the left table with every row of the right table. This type of join has the potential to make very large tables.
* `FULL OUTER JOIN` places null values within the columns that do not match between the two tables, after an inner join is performed.

1. Create a database called `commodities_db` with two tables, `names` and `commodity`. Then populate the tables with data from the `.csv` files provided in the `resources` directory.

2. Perform an `INNER JOIN` on the two tables.

3. Perform the same operation, using aliases.

---

### `07-bird_banding_db`
When information could unintentionally be duplicated, data is often stored in separate tables with reference to an `id`. In this dataset, most of the unique identifiers are labeled `code`. This activity uses various joins to uncover more about North American bird banding. 

#### Procedure
1. Create a new database named `bird_banding_DB`, and create eight new tables with pgAdmin named `bird_bands`, `age`, `band_type`, `bird_status`, `country_state`, `event_type`, `extra_info` and `sex`.
2. Perform joins that will generate the following outputs:
* Basic Information Table:
    | | band<br>character varying | event_date<br>character varying | species_name<br>character varying | age_description<br>character varying | sex_description<br>character varying |
    |----|----|----|----|----|----|
    | 1 | B06814289038 | 5/22/02 | Warbling Vireo | After Hatching Year | Unknown |
    | 2 | B06834226076 | 2/5/97 | White-eyed Vireo | After Hatching Year | Unknown |
    | 3 | B06834537033 | 9/28/01 | Red-eyed Vireo | After Hatching Year | Unknown |
    | 4 | B06834538078 | 9/6/01 | Red-eyed Vireo | Hatching Year | Unknown |
    | 5 | B06834760300 | 2/8/96 | La Sagra's Flycatcher | After Hatching Year | Unknown |
    | 6 | B06834762078 | 12/8/95 | La Sagra's Flycatcher | Unknown | Unknown |
    | 7 | B06834824074 | 2/9/96 | Yellow-bellied Flycatcher | After Hatching Year | Unknown |
    | 8 | B07033377537 | 2/26/19 | Yellow-bellied Flycatcher | Second Year | Unknown |
    | 9 | B07033378413 | 12/20/18 | Yellow-bellied Flycatcher | Hatching Year | Unknown |
    | 10 | B07033378577 | 12/5/18 | Yellow-bellied Flycatcher | Unknown | Unknown |
    
* Extended Information where sex is not unknown:</br>
    | | band<br>character varying | event_date<br>character varying | species_name<br>character varying | band_type_description<br>character varying | bird_status_description<br>character varying | age_description<br>character varying | sex_description<br>character varying |
    |----|----|----|----|----|----|----|----|
    | 1 | B07324722072 | 6/22/15 | Bahama Swallow | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Hatching Year | Female |
    | 2 | B07383058128 | 7/15/13 | Black-capped Vireo | aluminum\butt-end (toll-free /web address) | Normal wild bird. | Hatching Year | Male |
    | 3 | B07383058283 | 7/12/13 | Black-capped Vireo | aluminum\butt-end (toll-free /web address) | Normal wild bird. | Hatching Year | Male |
    | 4 | B07404371540 | 3/18/14 | Black-whiskered Vireo | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Second Year | Female |
    | 5 | B07423509254 | 9/9/11 | Vermilion Flycatcher | aluminum\butt-end toll free | Normal wild bird. | After Hatching Year | Male |
    | 6 | B07463640300 | 4/3/11 | Northern Rough-winged Swallow | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Hatching Year | Female |
    | 7 | B07463640387 | 4/3/11 | Northern Rough-winged Swallow | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Hatching Year | Male |
    | 8 | B01924380221 | 2/13/06 | Tropical Kingbird | aluminum\butt end | Normal wild bird. | After Second Year | Male |
    | 9 | B01974875034 | 4/7/00 | Gray Kingbird | aluminum\butt end | Normal wild bird. | After Hatching Year | Female |
    | 10 | B07514549034 | 3/29/11 | Tropical Kingbird | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Second Year | Male |
    | 11 | B08623850540 | 1/11/75 | Yellow-bellied Flycatcher | aluminum\butt end | Normal wild bird. | Second Year | Male |
    | 12 | B08623850863 | 2/12/75 | Least Flycatcher | aluminum\butt end | Normal wild bird. | After Hatching Year | Female |
---

### `08-rentals_db`

#### Procedure
Any insights not provided in the body below are provided as `.csv` output files in the `rental_db` directory. 

Items 1–19 are explorations of the `ORDER BY` and `GROUP BY` functionalities. Items 20–

1. Create a database titled `rentals_db`.

2. Create tables `actor`, `address`, `city`, `country`, `customer`, `customer_list`, `film`, `film_actor`, `inventory`, `payment`, `rental`, `staff`, `store`.

3. Select everything from the film table.

4. Count the number of `film_id`s in the `film` table. Use aliasing.

5. Group by `rating` and aggregate the `film_id` count.

6. Find the average rental duration. Use aliasing.

7. Group by rental duration and find the average rental rate within each group.

8. Find minimum rate per rental duration group.

9. Find maximum rate per rental duration group.

10. Find the average cost to rent a film in the stores.

11. Find the average rental cost of films by rating.
    - On average, what film rating is the cheapest to rent?
        - G – $2.8888764044943820
    - What rating is the most expensive?
        - PG – $3.0518556701030928

12. How much would it cost to replace all films in the database?
    - If counting each film only once – $19984.00
    - If counting entire inventory across both stores – $92,621.19

13. How much would it cost to replace all films in each ratings category?
    - If counting each film only once:
        - PG-13 – $4549.77
        - R – $3945.05
        - G - $3582.22
        - NC-17 – $4228.90
        - PG – $678.06
    - If counting entire inventory across both stories:
        - PG-13 – $21052.82
        - R – $18498.96
        - G – $16185.09
        - NC-17 – $19128.56
        - PG – $17755.76

14. Extreme movie lengths:
    - How long is the longest movie in the database?
        - 46 minutes
    - How short is the shortest movie?
        - 185 minutes

15. Select the average length of movies by rental rate. Round the results to use only two decimal places. Order by descending values. Limit results to 5.

    | Rental Rate | Film Length |
    |----|----|
    | 2.99 | 117.19 |
    | 4.99 | 115.82 |
    | 0.99 | 112.91 |

16. Determine the count of actor first names with the names ordered in descending order.

17. Determine the average rental duration for each rating rounded to two decimals. Order these in ascending order.

    | Rating | Avg Rental Duration |
    |--------|---------------------|
    | R | 4.77 |
    | G | 4.84 |
    | PG-13 | 5.05 |
    | PG | 5.08 |
    | NC-17 | 5.14 |

18. Determine the top ten average replacement costs for movies, ordered by their length.

    | Length | Avg Replacement Cost |
    |--------|----------------------|
    | 177 | 28 |
    | 133 | 26 |
    | 131 | 26 |
    | 60 | 25 |
    | 57 | 25 |
    | 164 | 25 |
    |46 | 24 |
    |150 | 24 |
    |56 | 24 |
    | 71 | 24 |

19. Get country counts from the `city` table.

20. Retrieve inventory information for the film 'EARLY HOME' first using a brute-force retrieval approach, and then using subqueries for a more elegant solution.
    | inventory_id | film_id | store_id | last_update |
    |--------------|---------|----------|-------------|
    | 1206 | 268 | 2 | 2006-02-15 10:09:17 |
    | 1207 | 268 | 2 | 2006-02-15 10:09:17 |

21. List the names and ID numbers of cities that are in the following list: `Qalyub`, `Qinhuangdao`, `Qomsheh`, `Quilmes`.

22. Display the districts in the above list of cities.

23. Create a view that monitors the total sales from each store, which is something a company executive would want to look up often.

24. Write a query to get the number of copies of a film title that exist in the inventory. Use a subquery instead of a join. Create a view named `title_count` and query the newly created view to find all the titles that have 7 copies.

  | | title<br>character varying (255) | Number of Copies<br>bigint |
  |----|----|----|
  | 1 | AFFAIR PREJUDICE | 7 |
  | 2 | ALADDIN CALENDAR | 7 |
  | 3 | ALAMO VIDEOTAPE | 7 |
  | 4 | ALASKA PHANTOM | 7 |
  | 5 | AMISTAD MIDSUMMER | 7 |
  | 6 | ARACHNOPHOBIA ROLLERCOASTER | 7 |
  | 7 | ARIZONA BANG | 7 |
  | 8 | ARMAGEDDON LOST | 7 |
  | ... | ... | ... |
  | 116 | WRONG BEHAVIOR | 7 |

25. Find the number of customers who rented BLANKET BEVERLY
    - 12

26. Using subqueries, identify all actors who appear in the film ALTER VICTORY in the `pagila` database.

| first_name | last_name |
|------------|-----------|
| REESE | KILMER |
| JADA | RYDER |
| ANGELA | WITHERSPOON |
| OPRAH | KILMER |

27. Using subqueries, display the titles of films that the employee Jon Stephens rented to customers.

#### Additional Exploration

1. Using the city and country tables, determine the count of countries in descending order.

2. Using subqueries, find the first and last names of customers who reside in cities that begin with the letter *Q*.

## Data Normalization

Data normalization standards can be summarized as follows:

- First Form Normalization
    - Each field in a table row row should contain a single value
    - Each row is unique

- Second Form Normalization
    - Be in first normal form
    - Single Column for Primary Key that identifies the table uniquely

- Third Form Normalization
    - Be in second normal form
    - Contain non-transitively dependent columns



_A summary of available functions can be found in the Postgres documentation on [aggregate functions](https://www.postgresql.org/docs/9.5/functions-aggregate.html)._