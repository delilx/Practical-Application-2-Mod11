# Practical-Application-2-Mod11
Files for PCMLAI  Assignment 11.1 ("What drives the price of a car?")

## Description of files in repository
* 'vehicles.csv' --the database containing information on used vehicles (features include id, price, year, odometer, region, manufacturer, model, condition, VIN, and others)
* 'assignmentmod11_DelilMartinez.ipynb' -- Jupyter Notebook containing the code for the project
* 'Mod11Report_DMartinez.docx' -- Word document with report of findings
* 'Mod11Report_DMartinez.pdf' -- PDF version of the Word document with report of findings (for accessibility)

**Link to Jupyter Notebook:** https://github.com/delilx/Practical-Application-2-Mod11/blob/main/assignmentmod11_DelilMartinez.ipynb 


# What Drives the Price of a Car?

## Summary of Findings
The task at hand in this project was to make use of a database with information about used vehicles to gain understanding of the elements that affect their prices. 

### Initial observations
•	The set contains valuable information that can sensibly be considered to be a factor in the market's determination of prices for used vehicles, such as type of vehicle, manufacturer, model, year, and condition, to name a few. The total number of columns in the set is 18 (including an 'id' column that identifies the record).
•	The size of the dataset is quite overwhelming, with almost half a million rows; however, there is a very large number of missing values in the set, reducing the usable sample significantly.

### Preprocessing
Notable steps taken in order to proceed with the analysis:
•	Attention was restricted to vehicles manufactured after year 2000, as anything older is considered a classic/vintage/collectible vehicle, which constitute a separate category and require a separate analysis.
•	Duplicates were eliminated from the set (using information on vehicles’ VIN where available, or looking for exact matches otherwise).
•	Samples with reported prices of less than $1000 or considered in “salvage” condition were also eliminated, as were samples with prices over $300,000 (assuming these are true values, vehicles with such prices should be analyzed separately).
•	Among the categorical features in the set, the type of vehicle turned out to be informative of vehicles’ prices, so samples where this entry was missing were also eliminated.
•	A transformation was applied to the prices to adjust for skewness. This is accounted for in all the resulting models.

### Results
Among 15 models fitted and tested, the optimal model is given by a linear regression for the natural logarithm of prices as a function of the vehicle's mileage (through 'odometer' feature), its age (defined as 2024 minus the vehicle's feature 'year'), and 
dummy variables for the categorical variables luxury level of the manufacturer (an artificial feature created to classify the manufacturer's names) and the type of vehicle.  
The resulting model produces and **adjusted $R^2$ value of 0.6893**, which conveys a measure of the proportion of the variability in the response feature (ln of prices) that is captured by the model.

Specific details about this and the rest of the models analyzed can be found in the accompanying Word document and Jupyter notebook.


### Main Findings:
1.	Obviously, newer vehicles fetch higher resale prices than older ones.
2.	All ultraluxury brands of vehicles produce high selling prices. When possible, dealers should hold these in inventory as they tend to have high prices associated with them.
3.	Trucks, pickups and offroad vehicles are good assets for dealers’ inventories, as they are associated with high prices.
4.	At the opposite end of the spectrum: hatchbacks, sedans, minivans,  wagons and even SUVs tend to associate with lower prices, as suggested by the factors that are all less than one in the table.
5.	Coupes, vans and convertibles, not surprisingly, are better if they are from luxury manufacturers than if they are not; the same is true for convertibles.
6.	In hindsight, while "Harley-Davidson" was detected as a label in the manufacturer feature and not in type, it would have been better to code these samples as "motorcycle" type, overriding whatever entry was present in the set. This would have made the results of the analysis more sensible. Nonetheless, since Harley-Davidson is considered a luxury brand of motorcycles, we can presume that having them in a used car dealership would also be desirable. 

