# Amazon-Sales
![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Amazon-South.png)
##### Photo Source: Google

## About Amazon
Amazon is an American multinational technology company focusing on e-commerce, cloud computing, online advertising, digital streaming, and artificial intelligence . It has been referred to as “one of the most influential economic and cultural forces in the world”, and is one of the world’s most valuable brands. Amazon takes care of everything from shipping and pricing to customer service and returns.

![](https://github.com/blessingekwere/Amazon-Sales/blob/main/360_F_410720864_QABliQkezbGAnVLOh2mS7AYG14onQ9ih.jpg)
##### Photo Source: Google

## About the Data
This dataset has the data of 1K+ Amazon product’s ratings and reviews as per their details listed on the official website of Amazon. The data was downloaded from Kaggle in a comma separated value format (csv) and it has 16 columns and 1465 rows. The columns which are:

* product_id — Product ID
* product_name — Name of the Product
* category — Category of the Product
* discounted_price — Discounted Price of the Product
* actual_price — Actual Price of the Product
* discount_percentage — Percentage of Discount for the Product
* rating — Rating of the Product
* rating_count — Number of people who voted for the Amazon rating
* about_product — Description about the Product
* user_id — ID of the user who wrote review for the Product
* user_name — Name of the user who wrote review for the Product
* review_id — ID of the user review
* review_title — Short review
* review_content — Long review
* img_link — Image Link of the Product
* product_link — Official Website Link of the Product
The link to the dataset can be found [here](https://www.kaggle.com/datasets/karkavelrajaj/amazon-sales-dataset)

## Objective of the Project
The Objective of this project is to perform an exploratory data analysis, discover insights and trends in the data that will be used to make informed decisions and make recommendations based on the data if necessary.

## Tools Used
The tool used for this project are Power Query Editor and Power BI

## Observation with the Data
After downloading the data, there were few observations I made about the data. Some of them were:

* Incorrect formatting of columns

* Inconsistent spacing

* The dataset had no date, which means it covers an unspecified period of time

* The dataset had some special and unprintable characters

* The dataset contained some irrelevant columns which will not be useful for analysis

## Data Cleaning
As mentioned earlier, I used Power Query editor and Power Query for this project.

Before starting out any project, the purpose of cleaning data cannot be over-emphasized. Knowing that from my observations which I listed earlier, there were quite a number of things that had to be done on the data to make it fit for use for further actions or analysis, I had to clean the data.

![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(331).png)
##### Power BI launch page


To start, I launched Power BI, proceeded to the ‘get data’ command in Power BI. Then I chose the Text/CSV format to import the data into Power Query Editor

![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(332).png)
##### Importing the data as Text/CSV


The data was loaded to power query editor, and then I proceeded to the cleaning by clicking on the transform button.

![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(333).png)
##### Loaded data in Power BI


Since I will be needing the category column for my analysis and it needed to be cleaned and formatted properly. I had to split the category column into two new columns namely primary and secondary category using a delimiter.


![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(334).png)
##### Splitting the category column


![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(335).png)
##### The category column(s) after splitting


![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(337).png)
##### The category column(s) after splitting which some were later removed


After splitting the columns and renaming them, I discovered that the ‘primary category’ and ‘secondary category’ were without proper spacing and had special characters. The ‘&’ symbol was replaced with ‘and’ using the replace value command. And also the columns were cleaned using the trim command and spaced properly.


![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(338).png)
##### Cleaning the primary and secondary columns using the replace value command


Proceeding to the discount price and actual price columns , I noticed that the value was in Indian Rupee (₹) which I need to change to US dollars ($) using the current exchange rate since the date is for an unspecified period of time. But before then, I had to remove the Indian Rupee (₹) using the replace value command and formatted it to fixed decimal data type.


![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(339).png)
##### Discounted_Price and Actual_Price columns with Indian Rupee(₹) which were later removed


I proceeded to carrying out the conversion by using the custom column command in the add column tab. As earlier mentioned, I used the current exchange rate which is ₹1 is equal to $ 0.012, I simply multiplied each column by 0.012 and renamed them respectively, repositioned the new added columns and dropped the other ones.

![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(339).png)
![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(340).png)
##### Converting Discounted_Price column


After dropping the other discounted_price and actual_price columns which were replaced with the newly converted columns, I went further to the rating column.

The rating column had two null values which I replaced them with zero. I then decided to add an additional column and name it rating_scale of 1 to 5 since I will be needing that for my analysis. To do that, I used the conditional column. For my rating scale, ratings <=1 were classified as Very Dissatisfied, ratings <=2 were classified as Dissatisfied, ratings <=3 were classified as Neither Satisfied nor Dissatisfied, ratings <=4 were classified as Satisfied else other ratings were classified as Very Satisfied.


![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Screenshot%20(342).png)
Using conditional column to add the rating_scale column

After the data cleaning, I decided to drop some columns that will not be useful in my analysis. The columns I dropped were ‘User_id’, ‘User_name’, ‘review_id’, review_title, ‘img_link’ and ‘product_link’. I also dropped row 1280 because it had an errorneous data that could not be resolved. So finally I was left with 11 rows and 1464 columns to be used for my exploration and analysis.


## Analysis
In order to be able to analyze my cleaned data property and get meaningful insights from it. I decided to use the new measures to command to get new measures which which either serve as a metric or be combined with other functions using DAX to perform some calculations and give insight to the data. Some of the measures I incorporated into this analysis were:

* Loss Margin: This is the ratio that represents a loss percentage of a selling price. It is calculated by dividing the loss by the selling price and then multiplying it by 100.

* Loss: This is the difference between the actual price and discounted price.

* Review: This is the sum of rating count

* Products: This is the count of products that were sold within the unspecified period that the data covers.

## Visualization
After creating the measures and going through the data to ensure that all was fine. I proceeded to the report tab of Power BI to visualize the data.
![](https://github.com/blessingekwere/Amazon-Sales/blob/main/Amazon%20Sales%20new%201_page-0001.jpg)
##### Amazon Sales Dashboard

Kindly Click [here](https://app.powerbi.com/groups/me/reports/3cadeebd-6bcf-4658-a583-67f5bb4725a9/ReportSection) to interact with the report

## Insight

* For the secondary category, amazon incurred more losses from sales of home theatre and TV video because of it’s discounts. The home theatre and TV video which also falls under electronics in primary category were mostly sold, hence making electronics to be product that the company incurred losses within this unspecified period.

* Considering the discount price by percentage in the primary category, electronics products enjoyed 68.79% discount, followed by home and kitchen products which enjoyed 22.84% discount and then computer and accessories products which enjoyed 8.37% discount.

* In the secondary category products, Home theatre and TV video had a total discounted price of 252,890, followed by mobile accessories with 172, 290.

* According to the rating scale, 78.43% of customers were very satisfied with their purchases, while 21.57% of customers were satisfied and 0.01% of customers were neither satisfied nor dissatisfied with their purchases. Which means no customer was dissatisfied. This also implies that amazon’s of giving its customers satisfaction and value for their money has been achieved.

## Recommendation
Having gone through the amazon sales data for the unspecified period of time and analyzed it, it is amazing to say that customer satisfaction has been attained but then it is of great necessity that the cost and pricing options must be reviewed by the company to ensure that it achieves profitability while continuing to satisfy it’s customers and giving them value for their money.

Thank you so much for reading this article.

Your comments, suggestions and recommendations will be highly appreciated. :blush:
