--Life expectancy healthcare data 2000-2015
SELECT * FROM final-bootcamp-project-380314.health_data.sql_final3 LIMIT 2939;
--Identify total death per 1000 children
SELECT under_five_deaths AS children_death FROM `final-bootcamp-project-380314.health_data.sql_final3`;
-- What are the shooling rate by country?
SELECT DISTINCT country, schooling FROM `final-bootcamp-project-380314.health_data.sql_final3`
ORDER BY 2 asc;
--What are the country life expectancy?
SELECT DISTINCT country, life_expectancy FROM `final-bootcamp-project-380314.health_data.sql_final3`
ORDER BY 2 desc;
--Retrieve country where life expectancy is superior or equal to 85
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy =85;
--Retrieve country where life expectancy is superior equal to 85
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >=85;
--Retrieve country where life expectancy is different to 85
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy !=85;
--Retrieve country where life expectancy is greater than 80, BMI is less 25
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >80 AND BMI<25;
--Retrieve country where life expectancy is greater than 80, BMI is less than 25 and infant death not 1
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >80 AND BMI<25 AND infant_deaths !=1;
--Retrieve country where life expectancy is greater than 50, or adult mortality greater than 50 per 1000 population
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >50 OR adult_mortality >50;
--Retrieve country where life expectancy is greater than 60, or adult mortality less than 60 per 1000 population
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy <60 OR adult_mortality <60;
--Retrieve country where status is not developed
SELECT country, status, FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE NOT status = "Developed";
--Retrieve country where life expectancy is greater than 50, and BMI smaller than 25 and status is not developed
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >50 AND BMI<25 AND status != "Developed";
--Retrieve country where life expectancy is greater than 60, and BMI smaller than 25 and status is not developed: 466
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >60 AND BMI<25 AND status != "Developed";
--Retrieve country where life expectancy is greater than 70, and BMI smaller than 25 and status is not developed:177
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >70 AND BMI<25 AND status != "Developed";
--Retrieve country where life expectancy is greater than 80, and BMI smaller than 25 and status is not developed:7
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE life_expectancy >80 AND BMI<25 AND status != "Developed";
--Retrieve the different life expectancy between 2000 and 2005
SELECT country, status, children_deaths, HIV_AIDS, FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE children_deaths !=0 AND status != "Developed" OR HIV_AIDS !=0
order by 3 DESC;
--Using ggregate functions in sql
--What is the total poplution of the data set
SELECT SUM(population)
 FROM `final-bootcamp-project-380314.health_data.sql_final3`
 WHERE year=2015
 GROUP BY country;
 -- Select the average life expectancy in the data set: 70 years
SELECT AVG(life_expectancy) 
 FROM `final-bootcamp-project-380314.health_data.sql_final3`
 WHERE year=2010;
 -- the average mortality rate of children under 5 in the data set_31.61/1000
SELECT AVG(under_five_deaths) 
 FROM `health_data.sql_final3`
 WHERE year=2015;
 --Retrieve all countries, BMI and life expectantancy values
 SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
 WHERE country LIKE "U%";
 --SELECT country,year, FROM `final-bootcamp-project-380314.health_data.sql_final2`
 --Check the null values in each column: life expectancy:10
 SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
 WHERE life_expectancy IS NULL;
-- IN column country, life_expectancy, adult_mortality,under_five_deaths,BMI, infant_deaths and population
SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
 WHERE country IS NULL OR life_expectancy IS NULL OR adult_mortality IS NULL OR under_five_deaths IS NULL OR BMI IS NULL OR infant_deaths IS NULL OR GDP IS NULL OR population IS NULL;

 --Retrieve the column where there is no null value:1649
 SELECT * FROM `final-bootcamp-project-380314.health_data.sql_final3`
 WHERE country IS NOT NULL AND life_expectancy IS NOT NULL AND adult_mortality IS NOT NULL AND under_five_deaths IS NOT NULL AND BMI IS NOT NULL AND infant_deaths IS NOT NULL AND GDP IS NOT NULL AND population IS NOT NULL AND income_composition_of_resources IS NOT NULL AND alcohol IS NOT NULL AND percentage_expenditure IS NOT NULL AND hepatitis_B IS NOT NULL AND measles IS NOT NULL AND polio IS NOT NULL AND total_expenditure IS NOT NULL AND diphtheria IS NOT NULL AND HIV_AIDS IS NOT NULL AND thinness_1_to_19_years IS NOT NULL AND thinness_5_to_9_years IS NOT NULL AND total_expenditure IS NOT NULL;
 --result with no null value give 1649 rows, from 1938, this is almost half of the data so we will consider retrieving just the data of interest.
 -- Clean the data that I will use for visualization, first drop some column of low interest

 -- create a new colum for children under 5 deaths that was HIV_AIDS death(under 4 years old) and under five deaths
 SELECT *, infant_deaths+under_five_deaths AS children_death
  FROM `final-bootcamp-project-380314.health_data.sql_final3`
  WHERE infant_deaths+under_five_deaths IS NOT NULL;
  -- Find the children total immunisation rate
   SELECT *, ROUND((polio+diphtheria+hepatitis_B)/3, 2)AS  children_immunisation, ROUND((HIV_AIDS+under_five_deaths)/2, 2) AS children_deaths
  FROM `final-bootcamp-project-380314.health_data.sql_final3`
  WHERE polio+diphtheria+hepatitis_B IS NOT NULL OR HIV_AIDS+under_five_deaths IS NOT NULL;
--subquery, find country that have an average bmi of 45: 6 countries
SELECT * 
FROM `final-bootcamp-project-380314.health_data.sql_final3`
WHERE BMI = 45;
--find the children death accross all country in 2015: 183 countries out of 192 with valus in children deaths in 2015

SELECT *, ROUND(children_deaths+under_five_deaths, 2) AS total_children_death
  FROM `final-bootcamp-project-380314.health_data.sql_final3`
  WHERE infant_deaths+under_five_deaths IS NOT NULL AND year = 2015;

--count all countries from cleaned data = 132
SELECT COUNT (DISTINCT country) AS Unique_Countries FROM `health_data.cleaned_data`
--count all country after cleaning = 193
SELECT COUNT (DISTINCT country) AS Unique_Countries FROM `final-bootcamp-project-380314.health_data.sql_final3`;
--SELECT COUNT (DISTINCT country) AS Unique_Countries FROM `health_data.sql_cleaned`
SELECT country, AVG(population) AS mean_population
  FROM `final-bootcamp-project-380314.health_data.sql_final3`
  GROUP BY country
