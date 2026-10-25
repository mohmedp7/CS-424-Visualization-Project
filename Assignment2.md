# CS 424 Assignment 2

#### Aidan Pina
#### Mohmed Patel



# Task 1: Revisit your data and questions



### Domain Questions to Investigate From Assignment 1:

- Our domain questions in task 3 were as follows:

- What types/styles of items receive the most bids?

- How does an item's starting price relate to its final selling price?

- Are certain categories of clothing consistently sold for higher prices?

- How does the type of show affect the price an item sells for?


After reviewing our original domain questions and the data we collected we decided to continue focusing on how clothing categories, styles, starting bids, and auction types relate to final selling prices. The questions we originally picked are still relevant since our dataset contains information about individual clothing entries and their final auction prices. However, we realized that some of our original questions are more difficult to answer directly than others due to our lack of data or easily accessible data. For example, the questions that involve viewer numbers or number of bids placed we couldn't record easily so we lack that option in our data. This means we can't accurately measure how viewer counts or number of bids impact the final selling price. So we will focus on what we can reliably measure and have already measured like differences in ending bids across clothing types and styles while analyzing the relationship between bidding start to end prices and auction format variation.

We mentioned before that there is inconsistency in how clothing types and other categorical attributes were recorded. This time we decided to make it more concise and fully revise the method in which we measure those attributes. Certain items like zipups, quarterzips, and zipup hoodies were difficult to classify consistently due to overlapping characteristics similarly with jackets. To fix this we decided to standardize clothing categories with more inclusive rules to keep things consistent. We also decided to rewatch streams and add two new attributes that recorded wear and stain information to represent item condition. This is to add another direction of exploration into these used clothes shows and see if maybe there is another reason for price differences in starting and ending bids. We've also added 2 new shows in order to have more entries to allow for either a new pattern or more accurate pattern during exploration and visualization. Our analysis will also acknowledge that the dataset only covers a handful of streams and may not represent the entire used clothes marketplace





# Task 2: Prepare the data

Code: https://github.com/mohmedp7/CS-424-Visualization-Project/blob/1f17ddb4bfe6899ac92872ca538b82e844892593/pyCodeCleanScript

We implemented a data cleaning process that was relatively simple in Python using Pandas so that the dataset used in our visualizations can be generated properly from a CSV file. First we load in the original dataset with all of the new attributes properly entered, standardize column names, and remove empty rows/columns. The dataset had some unnecessary whitespace from recording errors so we removed that. We converted starting bids and ending bids to numeric values so they can be used in calculations while keeping other attributes as strings since they won't be used for any calculations. 

This code also did the standardization of categorical attributes that we discussed needed to happen in order to keep the data consistent and concise. This fix includes things like capitalization, spacing, and terminology. For example, variations of crewneck as an entry were grouped, zipup hoodies were classified as just hoodies, and any variations of jacket types were just labeled together as jackets. Joggers and shorts were too sparse in the dataset so we took a handful of entries and put them with pants. Style, bid type, wear, and stain labels were also standardized to make grouping and comparison easier. These transformations are reproducible and allow items with intentionally grouped descriptions to be analyzed together rather than be treated as separate unrelated entries/categories simply due to a difference in original recording.

The script also checks the cleaned data for missing values and negative bids in order to validate that there are no issues or improper values like an item selling for negative money. There is also a distinct count of clothing types in order to see whether the standardization of clothing types was properly done. There is a final and separate check that looks for exact duplicate rows which normally would be important in most other datasets however for ours in particular there will likely always be duplicates considering there is no unique key in our dataset like an ID number, tag number, or unique identifier. So many rows may be exactly the same but they will always represent a unique item being auctioned. These checks are to properly validate if the data is ready for visualizations. We will use the final cleaned data csv in order to create the visualizations in future tasks. 





# Task 3: Explore the data

We did a lot of simple analysis in task 2 because we believed it was important to do but not valuable to show in task 3. The first thing we looked at was how ending bids are distributed. Across the 530 items that had ending bids, the median was $14 and the mean was $19. We can also see that there are few expensive items so assume that they brought up the average. The items that did not sell were given an ending bid of $0 to account for failed auctions which will help when calculating the average revenue per item listed. This will allow us to compare categories based on both the prices of sold items and items that failed to sell.

Next we compared streams with a boxplot per stream. Prices vary a lot: the Mrtop Carhartt show has a median of roughly $45 and reaches $180, while the yfvtg VTG Sweater show sits mostly under $10. Overall, sudden death items sell for more than auction items (a median of roughly $20 versus $10). This doesn’t hold for every stream, though. The Mrtop Premium Nike show (sudden death) is lower than the yfvtg $8 Workwear Pants show (auction). A streams average can also hide how many items sit behind it, which we look at in Task 4. We also recorded only 2 auction streams compared to 4 sudden death streams, so we can’t draw strong conclusions about format yet.

We then used a dropdown boxplot to compare clothing types with the ending bid. For all of the comparison types we did (Wear, Stainage, Size, Style, Type, and Bid Type) all of them except one had pretty normal results with each boxplot being similar. For type specifically, we can see that Jacket stands out. Their median is around $60 while every other type has a median under around $25. We didn’t expect type to matter that much so we were a bit surprised. Moreover, this is based on only 27 jackets. Looking closely, we can see that 4 out of the 5 items that are over $100 are jackets. This is most likely the reason why the average is so high compared to the others. The median is high because most jackets overall sold for more. 


# Task 4: Implement visualization alternatives

The first direction we decided to do for task 4 was the heatmap of type by size. This direction answers our question of whether some clothing categories sell for more. We wanted to try it because it was one of our refined Assignment 1 sketches and we believed it would show interesting results. The attributes are Type, Size, Ending Bid (mean), and the count of items. Our marks are the rectangles, and the channels are horizontal position (size), vertical position (type), and color lightness for the mean ending bid, with the number in each cell showing the item count. What worked is that the Jacket row is clearly darker than the others, and the counts show where we have solid data, such as Crewneck in L and XL with 54 and 69 items. What did not work is that pants have waist-by-inseam sizes (like 30x30), which stretch the x-axis to dozens of columns with only a few items in each. Many other cells also have only 1 to 3 items, and the pale color range makes it hard to compare anything except jackets. We decided to modify this direction by grouping or separating the pants sizes and using a wider color range, and we plan to keep it as one of our main views.



The second direction we decided to do was comparing auctions and sudden death shows. This direction answers our question of whether the show format changes what items sell for. We tried it because it was one of our Assignment 1 sketches and we were curious about the differences between sudden death and auction streams. The attributes are Bid Type, stream, and Ending Bid (mean per stream). Our marks are points, and the channels are vertical position (stream average) and color (format). What worked was that we see that the sudden death dots sit mostly higher than auction dots (reinforces what we saw in our exploratory analysis where sudden death items sell for more than auction items). However what didn’t work for us was that we have no idea of how many items sit in each dot. An example that shows us this is that the $55 dot comes from a stream with fewer than 20 items. An average alone also hides the spread as we previously mentioned in task 3. We decided we are going to modify this visualization and refine it in task 5 and 6. 



The third direction we decided to do was how the ending bid changes as a show goes on. This direction answers our question of whether an auctioneer saves the best items for last and whether that depends on the show format. We tried it because it was one of our refined Assignment 1 sketches. The attributes are item order with each stream, Ending Bid, stream, and Bid Type. Our marks are lines, and channels are horizontal position (item number), vertical position (ending bid), and color (bid type). What worked was that we were able to successfully see starting and ending positions of streams the way we wanted. From the 2 auction lines, we see that there are no signs of prices climbing. On the other hand the sudden death lines seem very erratic. What didn’t work is that it is very hard to read with the multiple lines and only 2 types of colors. We decided to modify it and refine it in 5 and 6. 





