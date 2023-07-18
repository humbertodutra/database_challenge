Average Life Expectancy Triggered Table

This repository contains a triggered table called "AverageLifeExpectancy" that calculates and maintains the average life expectancy for each continent based on the data from the "country" table.
Table Structure

"INSERT INTO `AverageLifeExpectancy` VALUES (72.99,'North America'),(67.44,'Asia'),(52.57,'Africa'),(75.15,'Europe'),(70.95,'South America'),(69.72,'Oceania'),(NULL,'Antarctica');"

The initial values ​​above were were calculated by averaging the lifeExpetancy column of each region:

    INSERT INTO world.AverageLifeExpectancy (LifeProm, Region)
    SELECT AVG(lifeExpectancy) AS LifeProm, continent AS Region
    FROM world.country
    GROUP BY continent;

The "AverageLifeExpectancy" table has the following structure:

    LifeProm: DECIMAL(10,2) - Represents the average life expectancy.
    Region: VARCHAR(255) - Represents the continent name.

Trigger Logic

The triggered table is updated automatically using triggers in response to INSERT, UPDATE, and DELETE operations on the "country" table.

    UpdateAverageLifeExpectancyOnInsert Trigger: After each INSERT operation on the "country" table, this trigger updates the average life expectancy for the corresponding continent in the "AverageLifeExpectancy" table.

    UpdateAverageLifeExpectancyOnUpdate Trigger: After each UPDATE operation on the "country" table, this trigger recalculates and updates the average life expectancy for the affected continent in the "AverageLifeExpectancy" table.

    UpdateAverageLifeExpectancyOnDelete Trigger: After each DELETE operation on the "country" table, this trigger recalculates and updates the average life expectancy for the affected continent in the "AverageLifeExpectancy" table.

Usage

To utilize the triggered table:

    Ensure that the "AverageLifeExpectancy" table is already created using the provided SQL code.
    Insert, update, or delete data in the "country" table.
    The triggered table will automatically update the average life expectancy values based on the corresponding changes in the "country" table.

Note: Ensure that the appropriate column names and table names are used in the triggers and SQL code, based on your specific database schema.
Important Considerations

    Ensure that safe update mode is properly configured on your MySQL server to prevent unintended updates.
    Take caution when modifying or deleting data, and always have appropriate backups in place before making any changes to your database.
    Regularly monitor the triggered table for accuracy and verify the results against the "country" table to ensure consistency.



