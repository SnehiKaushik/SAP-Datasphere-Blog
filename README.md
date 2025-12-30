# SAP-Datasphere-Blog
SAP Datasphere with SAC using Business Data Cloud Platform - Blog 

Sharing a simple and practical way to build a Geo Map using SAP Datasphere and SAP Analytics Cloud, in case it helps anyone working on geo-based analysis.

# Step-by-step: Building a Geo Map using SAP Datasphere + SAC

Sharing a simple and clean approach to create Geo Maps using SAP Datasphere (DSP) and SAP Analytics Cloud (SAC), in case it helps anyone working on geo-based analysis.


<img width="516" height="491" alt="image" src="https://github.com/user-attachments/assets/04b3c8c2-399d-41f0-8204-7df917506400" />


# Step 1: Create the Country Dimension (DSP)
Create a Country Dimension View.Think of this view as your master data for geography.


<img width="1064" height="615" alt="image" src="https://github.com/user-attachments/assets/2151777e-ba1e-402b-869f-ac2f9ccb5e18" />


Create a Location attribute of data type ST_GEOMETRY. This option is available only in views with semantic type set as "DIMENSION" — other view types do not allow to create location dimension to futher use it in the GEO MAP in SAC.


<img width="1962" height="947" alt="image" src="https://github.com/user-attachments/assets/06cac671-6116-40fe-a994-56f1fb1de16e" />


Table should have fields for Latitude and Longitude fields to the dimension.These are mandatory to derive location information.

<img width="2210" height="1355" alt="image" src="https://github.com/user-attachments/assets/1d261f97-51f4-42e0-9ad6-21522c07bafa" />


📌 This step is essential because SAC Geo Maps require a GEO–Location attribute, and that attribute can only be created from a Dimension view with valid latitude and longitude values.


# Step 2: Associate the Country Dimension with the Fact View

Open your Fact View that contains transactional or aggregated measures such as Sales or Marketing Spend. Ensure the fact view has a Country field that matches the Country key in the Country Dimension (same values and data type).Create an Association from the Fact View to the Country Dimension using the Country field.

<img width="928" height="611" alt="image" src="https://github.com/user-attachments/assets/ed1f3cd4-6490-41ff-a2e5-d3e887efc69a" />


Do the mapping on country field, Save and deploy the Fact View.


<img width="780" height="682" alt="image" src="https://github.com/user-attachments/assets/a5d1323d-b001-4641-8a4d-f75afbea081b" />



📌 This association allows the fact data to inherit the geo semantics from the Country Dimension, enabling SAC to correctly plot measures on a Geo Map using location information.



# Step 3: Create the Geo Map in SAP Analytics Cloud (SAC)

In SAC, create a new story and select the Analytical Model created in SAP Datasphere as the data source.Add a Geo Map widget to the story. 
Add layer, in this example we are using bubble type for layering.


<img width="1374" height="621" alt="image" src="https://github.com/user-attachments/assets/6caa85cf-28ac-4a59-8341-179cf08eb1f4" />



In the SAC Geo Map, the Location Dimension is set to the GEO–Location field coming from the Country dimension. Bubble size is driven by Sales, allowing SAC to automatically aggregate values at country level. Bubble color is controlled by Market Classification, making it easy to visually distinguish markets based on business logic derived in Datasphere.

<img width="713" height="1299" alt="image" src="https://github.com/user-attachments/assets/5235b8b7-0a13-45a3-ae6f-0525c23148b4" />



THANKS! I HOPE THIS BLOG WAS HELPFULL. 

DROP A LIKE FOR MORE :) 



