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

<img width="359" height="516" alt="image" src="https://github.com/user-attachments/assets/e9a4d30e-e37b-4082-a460-a0ab7d30e9cf" />


Next we compared streams with a boxplot per stream. Prices vary a lot: the Mrtop Carhartt show has a median of roughly $45 and reaches $180, while the yfvtg VTG Sweater show sits mostly under $10. Overall, sudden death items sell for more than auction items (a median of roughly $20 versus $10). This doesn’t hold for every stream, though. The Mrtop Premium Nike show (sudden death) is lower than the yfvtg $8 Workwear Pants show (auction). A streams average can also hide how many items sit behind it, which we look at in Task 4. We also recorded only 2 auction streams compared to 4 sudden death streams, so we can’t draw strong conclusions about format yet.

<img width="561" height="158" alt="image" src="https://github.com/user-attachments/assets/5d378988-458c-4a5c-b139-7d446e64c8d5" />


We then used a dropdown boxplot to compare clothing types with the ending bid. For all of the comparison types we did (Wear, Stainage, Size, Style, Type, and Bid Type) all of them except one had pretty normal results with each boxplot being similar. For type specifically, we can see that Jacket stands out. Their median is around $60 while every other type has a median under around $25. We didn’t expect type to matter that much so we were a bit surprised. Moreover, this is based on only 27 jackets. Looking closely, we can see that 4 out of the 5 items that are over $100 are jackets. This is most likely the reason why the average is so high compared to the others. The median is high because most jackets overall sold for more. 

<img width="166" height="397" alt="image" src="https://github.com/user-attachments/assets/934a34d8-be29-4b44-af0b-87f4dda3756a" />
<img width="170" height="397" alt="image" src="https://github.com/user-attachments/assets/79ce73e5-00e3-4430-9334-8ac2b593a9fb" />
<img width="169" height="370" alt="image" src="https://github.com/user-attachments/assets/a5ec3b2b-b2c2-4af8-a9d7-28ab72904e7e" />
<img width="173" height="387" alt="image" src="https://github.com/user-attachments/assets/04026d47-7996-4011-9ef5-756f500ec3a7" />
<img width="259" height="412" alt="image" src="https://github.com/user-attachments/assets/c5c55523-4982-40c5-966b-deea02b62595" />
<img width="1293" height="380" alt="image" src="https://github.com/user-attachments/assets/85d5a9f5-f2e8-4c2b-8a74-4ba64c5cb1c4" />









# Task 4: Implement visualization alternatives

The first direction we decided to do for task 4 was the heatmap of type by size. This direction answers our question of whether some clothing categories sell for more. We wanted to try it because it was one of our refined Assignment 1 sketches and we believed it would show interesting results. The attributes are Type, Size, Ending Bid (mean), and the count of items. Our marks are the rectangles, and the channels are horizontal position (size), vertical position (type), and color lightness for the mean ending bid, with the number in each cell showing the item count. What worked is that the Jacket row is clearly darker than the others, and the counts show where we have solid data, such as Crewneck in L and XL with 54 and 69 items. What did not work is that pants have waist-by-inseam sizes (like 30x30), which stretch the x-axis to dozens of columns with only a few items in each. Many other cells also have only 1 to 3 items, and the pale color range makes it hard to compare anything except jackets. We decided to modify this direction by grouping or separating the pants sizes and using a wider color range, and we plan to keep it as one of our main views.

<img width="631" height="113" alt="image" src="https://github.com/user-attachments/assets/e5152241-e54b-40a8-860a-5361d9d01935" />




The second direction we decided to do was comparing auctions and sudden death shows. This direction answers our question of whether the show format changes what items sell for. We tried it because it was one of our Assignment 1 sketches and we were curious about the differences between sudden death and auction streams. The attributes are Bid Type, stream, and Ending Bid (mean per stream). Our marks are points, and the channels are vertical position (stream average) and color (format). What worked was that we see that the sudden death dots sit mostly higher than auction dots (reinforces what we saw in our exploratory analysis where sudden death items sell for more than auction items). However what didn’t work for us was that we have no idea of how many items sit in each dot. An example that shows us this is that the $55 dot comes from a stream with fewer than 20 items. An average alone also hides the spread as we previously mentioned in task 3. We decided we are going to modify this visualization and refine it in task 5 and 6. 

<img width="158" height="352" alt="image" src="https://github.com/user-attachments/assets/c8da28fe-515b-431f-aba9-70cb85d02e37" />



The third direction we decided to do was how the ending bid changes as a show goes on. This direction answers our question of whether an auctioneer saves the best items for last and whether that depends on the show format. We tried it because it was one of our refined Assignment 1 sketches. The attributes are item order with each stream, Ending Bid, stream, and Bid Type. Our marks are lines, and channels are horizontal position (item number), vertical position (ending bid), and color (bid type). What worked was that we were able to successfully see starting and ending positions of streams the way we wanted. From the 2 auction lines, we see that there are no signs of prices climbing. On the other hand the sudden death lines seem very erratic. What didn’t work is that it is very hard to read with the multiple lines and only 2 types of colors. We decided to modify it and refine it in 5 and 6. 

<img width="338" height="285" alt="image" src="https://github.com/user-attachments/assets/de044eb6-1190-4e67-b5aa-e0a02991e493" />



# Task 5: Interaction and multiple views


We decided to keep our first direction (heatmap) as a single static view. All the information a reader needs is already there. We have color to show the mean ending bid and the number in each cell to show the item count. The point of the heatmap is to look for dark cells and judge how reliable each one is. For our second direction (auction versus sudden death dot plot), we decided to use multiple views. The dots show one average per stream, which isn’t enough on its own because we know an average hides the spread. So we add a boxplot to show the spread across all items grouped by show format. The boxplot doesn’t show which stream the items came from, but the dots do, so neither answers our question by itself and we show them side by side. They share the same color and categories, so they are easy to compare. We also added a small interaction: hovering over a dot shows which stream it is from and how many items it contains. For the third direction (line chart of price over the show) we were the most confused on what direction to do. We came up with three versions, color by format, color by stream with dashed lines for format, and small multiple views for each stream. After some thought, we think that all of them have their purpose, but the color by format and color by stream with dashes aren’t the best because in the end it is still cluttered for both. Moreover, we are planning on adding more streams (at least 2) by assignment 3 which makes us think that having multiple small static views is the best way to go. We will not do any interactions for direction 3 because we believe there isn’t a purpose of adding one. 


<img width="543" height="352" alt="image" src="https://github.com/user-attachments/assets/d45c89da-b42f-4647-a2dc-576af6883001" />


(color by stream with dashes)




<img width="784" height="368" alt="image" src="https://github.com/user-attachments/assets/04d93fdd-df88-4dd3-9f75-a4226e7ed2e8" />


(small multiple views for each stream)






# Task 6 Iterate and refine

We chose to iterate and refine our second direction. The first iteration we did was adding a channel. Our original version showed one dot per stream, with vertical position for the stream’s average ending bid and color for the stream type. The problem was that a dot gave no sense of how many items it came from. We proved this by showing that the highest sudden death dot came from a small stream but looked as important as an auction dot with over 100 items. We added size to each dot to show the number of items in the stream and added an interaction so that when the user hovers over a dot, it will show the stream name, average, and item count. We think size is a good channel to add because it will show how reliable each dot is at a glance. 
The second iteration we decided to do was to make it a multiple view. This is because even with size, a stream average hides how spread out the prices are, and it is pulled up by a few expensive items, as we saw in Task 3. We added a boxplot of all items grouped by show format next to the dots, so the median, spread and outliers are visible. We chose a second view over a new encoding because the two views answer different parts of the question. The dots show how streams compare with each other and which stream a result comes from, while the boxplot shows how individual item prices are spread within each bid type. One other tiny refinement we did that we mentioned in task 4 was that we removed pants from the heatmap, since we concluded they use a different size system (they still appear in our other visualizations). 

<img width="272" height="376" alt="image" src="https://github.com/user-attachments/assets/50ddba80-d04e-4e7c-9dcd-666c79d9ecd7" />


Refined visual for direction 2



<img width="337" height="238" alt="image" src="https://github.com/user-attachments/assets/426adfed-2b0e-4185-90a8-057dd3eb2b08" />


Refined visual for heat map






