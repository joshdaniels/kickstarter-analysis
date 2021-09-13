# Kickstarting with Excel

## Overview of Project

### Purpose
The purpose of this analysis Is to determine if, within Theater Campaigns there is existing correlation between Outcomes of campaigns and the launch date of campaigns.

Additionally, Within the campaign subcategory "Plays" can we determine if there is an existing correlation between Outcomes of campaigns and what the campaign goals are?

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
To begin, I created a pivot table using the Kickstarter dataset. I displayed the month the campaign was created in my Rows and the outcomes data in my columns. I filled in the values using the values of the outcome categories (Successful, Failed & Cancelled) as well as the total number of campaigns.

I filtered the table by Years the campaigns were created in and the Parent Category of campaigns. I filtered the table by only displaying the data from the campaigns that had a Parent Category of "Theater".

Next, I created a Pivot Chart from the Pivot Table and changed the chart type to "Line with Markers" to show the data in a linear fashion across the months of the year.



![Chart 1](https://github.com/joshdaniels/kickstarter-analysis/blob/main/Theater_Outcomes_vs_Launch.png)



Above, You can see the chart that was created from the Pivot table.

### Analysis of Outcomes Based on Goals
First I created a new sheet named "Outcomes Based on Goals". In that sheet i created a new table with the individual goal amounts ranging from Less than 1,000 to Greater than 50,000. I made columns to break out each outcome into Number Successful, Number Failed and Number Cancelled. Additionally I created a total number of projects columns and for each outcome a "percentage of" column.

Next, I needed to count the amount of Successfull, Failed and canceled. Using the COUNTIFS function in excel. In the function for each goal group and outcome type it returned 1 if the campaign met the criteria of the shared cell.

For example, if the campaign had a goal that was less than 1000 and also was successful. I also added a criteria in all functions to only count if the subcategory of the campaign was "Plays". as an example, The code looked like the following:

  =COUNTIFS(Kickstarter!D:D,">=10000",  Kickstarter!F:F, "successful",Kickstarter!R:R, "plays",Kickstarter!D:D,"<=14999", Kickstarter!F:F, "successful",Kickstarter!R:R, "plays")

Then once the right count was in the right cells, I created an additional column named "Total Projects". I used the SUM function to add all of the outcomes together for a certain goal group. As an example, The code looked like the following:

  =SUM(C5,D5,E5)

Next, For the percentages columns, I divided the number of each outcome by the total projects in each goal group  and multiplied that by 100. As an example, The code looked like the following:

  =C5/F5

I also formatted the cells in the percentage columns to be percentages with 0 decimal points.

Once the sheet was complete I created a Pivot table with the goal groups listed in rows and each percentage of each outcome type as a column. I filled in the table using the sum of the percentage for each outcome type that fell into each goal group.

Lastly I used the Pivot Table to create a Line graph displaying the Goal Thresholds data in dollars on the x-axis and the number of outcomes in percentages on the y-axis.

![ chart image 2](https://github.com/joshdaniels/kickstarter-analysis/blob/main/Outcomes_vs_Goals_v2.png) 

Above, You can see the chart that was created from the Pivot table.


### Challenges and Difficulties Encountered
while analyzing Outcomes Based on Launch Date I had a challenge when it came to displaying the months of the dates the campaigns were created. To overcome this I Grouped the dates into months.

While analyzing Outcomes based on Goals, It was challenging to get the COUNTIFS criteria just right. I overcame this by checking the syntax in the documentation and trial and error.

Admittedly, I reached the chart output several times before I got the data correct. The way I fixed this was honing in on the individual point of data on the chart that was incorrect and examining that cell for mistakes.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

Looking at the chart we can immediately observe a couple of things.

A)In early summer(May), The campaigns that were launched had the highest number of successes.

B)At the ending of the year(Dec), Campaigns saw a dramatic downtick in the number of successes.

- What can you conclude about the Outcomes based on Goals?

Observing the chart above, We can clearly see that It's easiest to successfully fund a "Plays" campaign with a much smaller goal.

It's also easier for a "Plays" campaign to fail in larger goal categories.
Everything in between the smaller and larger goal categories is fluctuating and we would Need to know more information about the "Plays" campaigns to determine what creates this.

- What are some limitations of this dataset?

During my analysis of Outcomes Based on Launch Date I observed that the data is limited in the following ways:

In October, There appears to be no cancelled campaigns. Is this a Zero? or a reporting Error?

Additionally the data is heavily based in the US market.

During my analysis of Outcomes Based on Goals I observed that the data is limited in the following ways:

There appears to be no cancelled campaigns. Is this a Zero? or a reporting Error?

- What are some other possible tables and/or graphs that we could create?


#### Outcomes Based on Launch:
To further my analysis and determine wether or not the spike we saw in May and the dip we saw in dec are in fact recurring patterns, I would like to break up the years data to show Year over Year comparisons.

I would also like to break out each subcategory into their own chart and see if patterns exist across subcategories within the Theater Parent Category.

Lastly I would like to group the countries into hemispheres. That way we could compare all of countries within their appropriate hemisphere to account for opposite seasonality that may muddy our analysis currently.

#### Outcomes Based on Goals
To further my analysis, I would like to add the number of backers and average donation values into the pit table and charts to see if there is a constant or average amount of donations that equal a higher value single donation in the successful campaigns in the higher goal groups.

I would also like to break out other subcategories within theater to determine the average successful campaign amount for the Category and see if "Plays" falls within this.
