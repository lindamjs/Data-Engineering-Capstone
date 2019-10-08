### Step 1: Scope the Project and Gather Data

#### Scope 
Explain what you plan to do in the project in more detail. What data do you use? What is your end solution look like? What tools did you use? etc>

Scope - The project focuses on :
  (i)  Immigration data only for US. 
  (ii) Immigration data for a span of 4 years (2014-2018)

Data Sources
------------
1. immigration_data_sample.csv - This data set contains immigration information for visitors like - i94 ID, arrival_Date, departure_date,
visa_type, gender, birth_year, admsn_no, flight_no, airline

2. us-cities-demographics.csv - This data set contains the demographic information for US cities like - race, gender, ethnicity, total population, total number of males/females in the city etc 

3. airport-codes.csv - This data set contains the airport codes, airport name, type of airport,  region and country to which the airport belongs.


Data Model 
----------

Dimensions :
-----------
1. dim_airport  - Dimension table for airport codes ( PK - airport_code)

Columns
------
ident
name
country
region
co-ordinates

2. dim_city_demog - Dimension table for city demographics ( PK = city name) 

Columns
------
city
state
state_cd
median_Age
male_population
female_population
Race

3. dim_visitors - Dimension table with immigration data for US visitors ( PK = I94 admission num)

Columns
------
admn_num
visa_type
transport_mode
arr_Date
dep_date
birth_yr
gender
port_of_entry
age (calculated field)


Fact
----
4. fact_immigrations - Fact table which records the US visitors coming in by airport/cities.

The ETL Data Pipeline is built using Python commands and the Data Warehouse is built in AWS.
The data sources are staged into AWS S3 buckets, cleansed and loaded into Redshift database.

#### Describe and Gather Data 
Describe the data sets you're using. Where did it come from? What type of information is included? 

1. immigration_data_sample.csv - This data comes from the US National Tourism and Trade Office. The dataset contains international visitor arrival statistics by world regions and select countries, type of visa, mode of transportation, age groups, states visited (first intended address only), and the top ports of entry for select countries 

2. us-cities-demographics.csv - This dataset contains information about the demographics of all US cities and census-designated places with a population greater or equal to 65,000. This data comes from the US Census Bureau's 2015 American Community Survey

3. airport-codes.csv - This is a simple table of airport codes and corresponding cities. The airport codes may refer to either IATA airport code, a three-letter code which is used in passenger reservation, ticketing and baggage-handling systems, or the ICAO airport code which is a four letter code used by ATC systems and for airports that do not have an IATA airport code
