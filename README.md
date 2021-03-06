Group One Documentation - State Population Vs Wage 

NAMES:
Thomas Westerkamp
Melissa Mongrella 
Domenic Padulo 
Lauren Stredler

EXTRACT:
Data sources:
● Our group used two CSV files to compare the U.S. minimum wage to the census population by state in 2019.
The two data sources were pulled from Kaggle.
	•	2019 Census Population Data by State: https://www.kaggle.com/peretzcohen/2019-census-us-population-data-by-state
	•	US Minimum Wage by State from 1968 to 2020: https://www.kaggle.com/lislejoem/us-minimum-wage-by-state-from-1968-to-2017

TRANSFORM:
● We renamed the:
	• Minimum Wage CSV file by removing the spaces
	• Population data CSV file by shortening to make the name easier to import into Pandas 
● The CSV files were imported using Pandas
● We created a filtered data frame using specific columns
	• The following columns were dropped because they did not provide additional information that was useful:
		• 2019 Census Population Data by State: Lat Coordinate of Capital, Long Coordinate of Capital
		• US Minimum Wage by State from 1968 to 2020: State.Minimum.Wage.2020.Dollars, Federal.Minimum.Wage, Federal.Minimum.Wage.2020.Dollars, Effective.Minimum.Wage, Effective.Minimum.Wage.2020.Dollars, CPI Average, Department.Of.Labor.Uncleaned.Data
		• In addition, we only kept data from the year 2019
● The following columns were renamed:
	• 2019 Census Population Data by State: STATE was renamed to state; POPESTIMATE2019 was renamed to population_estimate
	• US Minimum Wage by State from 1968 to 2020: State.Minimum.Wage was renamed to state_minimum_wage and Year variable was changed to _year in order for Postgres to not automatically assign it a function and to differentiate it as the name of one of our columns.
● We converted our State variables in both data frames from objects to strings before we merged the two dataframes. Once they were merged, the State variable reverted back to an object. We also did this to the Year variable. 


LOAD:
● We made the database connection to Postgres and loaded the merged dataframe into the database. 
● Our team was most comfortable with the Postgres platform and chose to use it. We also preferred that the visuals provided in Postgres are similar to that of Jupyter Lab and could therefore make easier comparisons. 
● We had difficulties with names matching in Postgres versus Jupyter Lab and had to make some adjustments; this mostly happened when joining the tables.  

TABLES:
● Matching tables were created in Postgres and joined on the State variable
