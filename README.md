# Week-4

#Week 4: dplyr package

#Task: Write the function to get a dataset from Base R: Titanic
#and give the dataframe a new name of your choice
#(hint: you will want your data to be a dataframe. Use the function: as.data.frame(Titanic))
data(Titanic)
as.data.frame(Titanic)
Iceberg <- Titanic
rm(Titanic)

#See the top rows of the data
#TASK: Write the function to see the top rows of the data
head(Icerberg)

#Install and call the package dplyr
#TASK: Write the functions to install and call dplyr
install.packages("dplyr")
library("dplyr")

#Let's just see the Survived and Sex columns
#Task: Write the function to 'select' the Survived and Sex columns 
#(hint: use the 'select' function)
Iceberg %>% select(Survived, Sex)

#Let's name the dataset with just the two columns, Survived and Sex
#TASK: Write the function to save the two columns as one new dataset
#and give it a name
new_Iceberg <- select(Iceberg, Survived, Sex)
#to Professor: just out of curiosity, would it work if I use Icerberg %>% new_Iceberg <- select(Iceberg, Survived, Sex)?

#Let's get rid of the Sex column in the new dataset created above
#TASK: Write the function that deselects the sex column
#(hint: use the 'select' function to not select a -column)
new_Iceberg %>% select(!c(Sex))

#Let's rename a column name
#TASK: Write the function that renames 'Sex' to 'Gender'
Iceberg %>% rename(Gender = Sex)

#Let's make a new dataframe with the new column name
#TASK: Write the function that names a new dataset that includes the 'gender' column
male_Iceberg <- select(Iceberg, Gender)

#Let's 'filter' just the males from our dataset
#TASK: Write the function that includes only rows that are 'male'
male_Iceberg %>% filter(Gender == male)

#Let's 'arrange' our data by gender (not the data you just filtered)
#TASK: Write the function to group the data by gender (hint: arrange())
Iceberg %>% arrange(Gender)

#Let's see how many people were examined in the dataset (total the frequency in the original dataframe)
#TASK: Sum the Freq column
#TASK: After you run it, write the total here:__2201__
total_freq <- sum(Iceberg$Freq)

#Since we have a males dataset, let's make a females dataset
#TASK: Write the function that includes only rows that are 'female'
female_Iceberg <- select(Iceberg, Gender)
female_Iceberg %>% filter(Gender == female)

#And now let's join the males and females
#TASK: Write the function that joins the male and female rows 
#(hint: try using 'union' or 'bind_rows')
bind_rows(male_Iceberg, female_Iceberg)

#Optional Task: add any of the other functions 
#you learned about from the dplyr package
#I can add new columns with mutate(). I'm going to add a new column calculating the ratio of Freq vs. total frequency
Iceberg %>% mutate(Freq / 2201)
