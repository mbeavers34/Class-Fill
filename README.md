# Class-Fill
Predict how many students will be in a given class based on the previous semester.

#Program overview:
This program predicts the number of students that will be in AUT-052-5006 based on the number of students in AUT classes from the previous semester. AUT-052 was just a random class for auto majors in the 2nd semester. 

There is still a lot of automation to be done as this program moves to predicting all of the classes in the 2nd semester instead of just one.

The majority of the program was cleaning and organizing the data. 
- Read each sheet of the excel file (12 total).
- Get rid of EXCO, EXCL, columns and stdcnt blank data rows.
- Convert stdcnt to integer.
- Create dataframes and transpose (rows to columns, columns to rows).
- Combine the 12 datframes into 6 rows. The 6th row isn't used yet as the data form this fall semester 2022 isn't complete.
- Change NaN's (classes not offered) to zeros. 
- Create a list of required Auto classes. Compare this list to the classes that were offered (column names) and drop any that aren't == to classes on the list.
- Test train split at test_size = .125 (no random value so I could get a different X,y each time) Poor man’s cross validation?</ul>

I ran a straight Linear regression Model for a baseline. With 2019 and 2020 significantly departing from normal enrollment I considered removing that data after the model prediction turned out marginal at best.

For my next model I used Pipeline([('features', PolynomialFeatures(degree = 3)), ('model', LinearRegression())]) with Permuation Importance.
It seemed to be predicting the class size perfectly.
I collected the data from several runs of both models and the Pipeline was correct every time.
At this point I didn't see any reason to run any other models.
The seaborn scatter diagram shows the results of the test runs. 

Conclusion: The PolynomialFeatures, LinearRegression, Pipeline using permutation importance can accurately predict the students in AUT-052 based on the previous semester students. It will be of great interest to see if this model can accurately predict the remain 2nd semester classes as well.

The program needs lots of automation to be able to simply add the class list and have it print out the results.
