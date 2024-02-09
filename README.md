# An Evaluation of Crime in Los Angeles
------------
## Project Goals and Research Questions:
The purpose of this project was to examine features and predictors of different kinds of crime in Los Angeles since 2020. 
Our specific research questions are as follows:

	1. What is the structure of crime in Los Angeles? 
		a. Where are crimes most likely to occur?
		b. What kinds of crimes are most common?
		c. How frequent are arrests made for crimes?
		d. What demographics are most frequently victimized?
		e. In what kinds of locations (e.g., homes, public spaces, stores, etc.) are crimes most likely to occur?
	2. Are there any relationships between victim demographics and crime type?
	3. Are there any relationships between victim demographics and arrest likelihood?
	4. Can we accurately predict whether arrests are likely to occur or not from the available data?
	5. Can we accurately predict crime type (violent versus nonviolent) or not from the available data?



## Data Sources and Research Methods:
All of the data used in this project was provided from a database on data.gov. This particular database, which can be found in the link below, records reported crime and characteristics of each crime in the Los Angeles area since 2020. 

Due to the diverse set of research questions, this project uses a multimethod approach.Some of the questions are analyzed primarily using descriptive statistics and graphs. Others were analyzed using various inferential technqiues including regression analysis, chi squared, and supervised learning. 



## Data Extraction & Cleaning: 
Using the data sources above, the following files were important to the cleaning and extraction of the data:
- DataCleaning.ipynb
- cleaned_data.csv

Originally, the plan was to pull data out of the database as a csv file. But the csv file ended up being too big to upload to Github. So, instead, the data were initially pulled in from the JSON version of the API to the ipynb file. 
From there, the dataset was cleaned and reduced in size (columns that were not needed were removed). The output file included renamed columns, recoded variables, and only columns useful in analyses. The csv file, which was now small enough to upload to Github, is the output of that cleaning, and the main source of data for the project. 





## Analysis of Data:
### RQ1- 

This first question is a multipart question about the structure of crime data. Most of this analysis was done with data visualization in Tableau along with some discriptive analysis (done in the file DescriptiveAnalysis.ipynb). 
To address the second sub-question, we also used a combination of Tableau visualizations and descriptive analysis. We created a bar graph, showing the breakdown of crimes by crime type, and one of the maps described above, also has the crime locations color coordinated by crime type. 

To address the first sub-question, we created multiple crime maps using lattitude and longitude data in Tableau. These maps show the location of each crime, and are color coordinated to show other characteristics of the crime(e.g., location type, crime type, etc.). 
In addition to that, the percentage of crimes in each district were calculated. The district with the highest percentage of crimes was Central with 6.8% of all the crimes. However, no district showed a substantially larger percentage of the crimes with percentages ranging from 3.3% to 6.8%. 

To address the second sub-question, we also used a combination of Tableau visualizations and descriptive analysis. We created a bar graph showing the breakdown of crimes where an arrest was made versus was not made, and one of the maps described above, also has the crime locations color coordinated by crime type. 
Overwhelmingly, the most common type of crime was theft, amounting to 52.6% of all of the crime. The next most common and the most common violent crime was assault, which accounted for another 24.0%. So, collectively, those 2 crime types accounted for 3/4 of the crimes committed. 

To address the third sub-question, we exclusively used Tableau visualizations. We created a pie chart showing the breakdown of crimes by crime type, and one of the maps described above, also has the crime locations color coordinated by whether an arrest was made. 
Ultimately, arrest percentages were collectively low across the city, with only 9% of crimes ending in an arrest.

To address the fourth sub-question, we also used a combination of Tableau visualizations and descriptive analysis. We created 3 bar graphs, showing the breakdown of crimes by race, gender, and age group. In addition, the percentages of each and the average age were calculated in the ipynb file.
The most victimized group was Hispanics (30.5% of all victims). The age group most victimized was the 25-39 age group. However, looking at the average age suggests that the most common victim age would've been relativley close to 40 as the average age of victims overall was 39.6. 
Men were slightly more likely to be victims of crimes (41.1%) compared to women (36.6%). It should be noted that these percentages do not add up to 100% because of a large number of unidentifieds for this variable. 
   
To address the final sub-question, we also used a combination of Tableau visualizations and descriptive analysis. We created a bar graph, showing the breakdown of crimes by location type, and one of the maps described above, also has the crime locations color coordinated by location type. In addition, the percentages of each were calculated in the ipynb file.
The most common location type was in a public space (46.0%). The second most common location type was a residence (31.6%).



### RQ2- 
The second question is also a multipart question, looking at the relationships between demographics and arrest rates. The analyses for this question are located in the InferentialAnalysis.ipynb file. 
First, we examined gender as a predictor. To test this, we used a chi squared test, examining differences between men and women victimization and arrest rates. The results revealed a significant effect (χ2= 165.19, p<0.01). There was a slightly elevated arrest percentage of cases for women were victimes (10.10%) versus men (9.18%). 
Next, we examined race as a predictor. To test this, we used a chi squared test, examining differences between Caucasians and non-Caucasians victimization and arrest rates. The results revealed a significant effect (χ2= 117.67, p<0.01). There was a slightly elevated arrest percentage of cases for non-Caucasians were victimes (10.10%) versus Caucasians (9.18%). 
Finally, we examined age as a predicor. To test this, a dummy coded linear regression was used to with age predicting dummy coded yes:no arrests. Age significantly predicted arrests (r=-0.04, p<0.01). However, the statistical signficance of this is likely due to the excessive amount of data as a correlation of -0.04 is essentially a null relationship. 




### RQ3- 
The third question is also a multipart question, looking at the relationships between demographics and crime types. Because of the large number of distinct crime types, these were coded into violent versus non-violent crimes (code for this located in the DataCleaning.ipynb file). The analyses for this question are located in the InferentialAnalysis.ipynb file. 
First, we examined gender as a predictor. To test this, we used a chi squared test, examining differences between men and women victimization and crime type (either violent or nonviolent). The results revealed a significant effect (χ2= 1167.48, p<0.01). There was a slightly elevated percentage of cases of violent crime for women as victimes (42.75%) versus men (38.69%). 
Next, we examined race as a predictor. To test this, we used a chi squared test, examining differences between Caucasians and non-Caucasians victimization and crime type (either violent or nonviolent). The results revealed a significant effect (χ2= 20322.93, p<0.01). There was a substantially elevated percentage of cases of violent crime for non-Caucasians as victimes (45.87%) versus Caucasians (26.58%). 
Finally, we examined age as a predicor. To test this, a dummy coded linear regression was used to with age predicting dummy coded yes:no violent crime. Age significantly predicted arrests (r=-0.14, p<0.01). However, like the previous regression on age, the statistical signficance of this is likely due to the excessive amount of data as a correlation of -0.14 is essentially a still relatively small. 



### RQ4- 
The final two questions involve the use of logistic regression to attempt to predict various outcomes from all the data in the dataset. 
The first set of models attempted to predict arrest rates. These models are tested in the ipynb files ArrestLogistic, ArrestLogisticAlt, and ArrestLogisticAlt2. The initial model included area name, victim age, victim sex, victim race, crime type, and address type as predictors. That model yielded low accuracy (0.50). The model yielded relatively high precision, recall, and f1 scores for no arrest made cases (0.91, 1.00, and 0.95), but low scores for arrest made cases (0.56, 0.00, 0.00). 
Because of the low accuracy, 5 additional models were tested. 
- The first model was resampled.
- The next model dropped victim age (shown in RQ2 to be a low predictor) and area name (because of the large number of classifications).
- The next model used the model above with resampled data.
- The next model dropped address type in addition to the other two variables discussed above (because address type had a lot of variability in frequency). 
- The final model used the model above but with resampled data.

In the end, the best model was the first model with resampled data. However, even that yielded lower than desired accuracy (0.68). The model yielded relatively high precision and f1 scores(0.96 and 0.76), but a lower recall score for no arrest made cases (0.62). But for arrest made cases showed inconsistent numbers (0.17, 0.74, 0.27). 
Ultimately, the data in this dataset was not able to successfully predict arrest rate.



### RQ5- 
The second set of models attempted to predict violent versus non-violent crimes. These models are tested in the ipynb files ViolentCrimeLogisticRegression, ViolentCrimeAlt, and ViolentCrimeAlt2.The initial model included area name, victim age, victim sex, victim race, and address type as predictors. That model yielded low accuracy (0.62). The model yielded relatively inconsistent precision, recall, and f1 scores for both violent crime(0.58, 0.49, 0.53) and non-violent crime (0.68, 0.75, 0.71). 
Because of the low accuracy, 5 additional models were tested. 
- The first model was resampled.
- The next model dropped victim age (shown in RQ3 to be a low predictor).
- The next model used the model above with resampled data.
- The next model dropped address type and area name in addition to the other two variables discussed above (because of the same reasons discussed in RQ4). 
- The final model used the model above but with resampled data.

In the end, the best model was again the first model with resampled data. However, even that yielded lower than desired accuracy (0.64). The model yielded relatively inconsistent precision, recall, and f1 scores for both violent crime(0.54, 0.68, 0.60) and non-violent crime (0.72, 0.59, 0.65). 
Ultimately, the data in this dataset was not able to successfully predict violent crimes.



## Discussion:
In summary, we were able to describe some trends in the dataset that yielded potentially useful demographic and descriptive information about crime in Los Angeles. In addition, the inferential analyses performed did identify some individual predictors of both arrest rate and violent crime rate, most notably race and gender. 
However, the data set simply did not contain enough data to successfully predict arrest rate or violent crime with adequate accuracy.

If research on this topic was to continue, we could see if there are any other crime data sets from that area that might have mergable data. In addition, it would be interesting to look attempt to look at predictive relationships of some of the recoded variables (e.g., crime type, address type) on a more granular level. It could also be interesting to see if a neural network approach might yield better accuracy compared to the logistic regression approach that we used. 



## Navigation:
-Data Analysis Folder- Contains all of the ipynb files used to calculate descriptive and inferential analyses as well as the data file contained in the "Resources" folder. 
-Data Files Folder- Contains the ipynb file used to pull in and clean the data set as well as a finished data set and a codebook that was used to help recode data. 
-Images Folder- Contains a Powerpoint with all of the images created externally from Tableau to be used in the presentation, most notably the inferential analysis and supervised learning images. There are also image files in here saved from that Powerpoint.
-Project Planning and Reports- Contains the project overview that was created at the beginning of the project.
-Tableau Files Folder- Contains the Tableau workbook that holds our visualizations and final presentation (in the form of a story). 


