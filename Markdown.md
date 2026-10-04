# CS 424 Assignment 1

#### Aidan Pina
#### Mohmed Patel

# Task 1: Observation and data collection plan

We decided to do data collection of an online auctioning app where people/companies will livestream and show the camera items/objects and people will be allowed to bid on them against others. We found this interesting because we enjoy thrifting vintage clothes and checking out big events like ThriftCon, IllinoisVintageFest, and Thrift2Death. So being able to buy thrifted clothing or other items online allows us to do one of our hobbies from the comfort of our own home without any drawbacks. We also have a lot of experience buying from the app over the past year and have spent more money than we should have.

### Initial Domain Questions to Investigate:

How does the number of viewers affect the final selling price of an item?

What types/styles of items receive the most bids?

How does an item's starting price relate to its final selling price?

Are certain categories of clothing consistently sold for higher prices?

How does the type of show affect the price an item sells for?

For this project, one observation is one piece of clothing sold during a Whatnot livestream. We watched streams live on the app from home over about a week and a half. For each item, we recorded the channel name and its follower count, the clothing type, the size, the starting bid, and the ending bid. On streams where it was possible, we also recorded the show format (auction or sudden death), the style (printed, embroidered, or blank), and the position of the brand symbol. We chose these attributes because we thought they could affect what a viewer would bid, and because they were the ones we could capture reliably in the few seconds each item is on screen.

To capture meaningful variation rather than a single snapshot, we deliberately watched streams that sold different things. One stream mostly sold Nike, another mostly Carhartt, and others sold a mix, so the data covers different clothing types, sizes, price levels, and sellers. We first planned to watch just one auctioneer, but realized that its regular viewers might know what to look for, which would make prices reflect one community and not the app more broadly (bias), so we spread our viewing across several auctioneers. To keep our recording consistent, we watched one stream together first to agree on how to record each attribute, then each watched multiple streams on our own. One part of our collection that we failed to capture was brand. This was because it was rarely named and auctioneers moved on within seconds, so we dropped it.

### Initial Data Dictionary

| Attribute  | Type	 | Description| Example |
| -------------|:-------------:|:-------------: |:-------------:|
|Channel Name |Categorical |The name of the auction channel/ seller|youthforeverwholesale |
|Style        |Categorical |The apparel style|Embroidered|
|Size         |Categorical |The size of the clothing |2XL |
|Starting Bid |Quantitative|The starting price of the clothing|5 |
|Ending Bid   |Quantitative|The final selling price of the clothing|180 |
|Type         |Categorical |The type of clothing|Crewneck |



# Task 2: Pilot and data collection

When we first started collecting the data and recording our attributes, we found that it was hard because of the speed some of the auctioneers were going. It definitely took a couple tries to collect all the attributes we wanted in the time frame that one piece of clothing was shown. One observation that was difficult to classify was the type of clothing. This was because it wasn’t mentioned half the time what kind of clothes it was. Additionally, if the auctioneer did mention what type of clothing it was, we believed it was actually something else. An example we can give is a hoodie with a zipper that the auctioneer said was just a hoodie. In order to keep everything consistent and concise,what we did was that we classified the piece of clothing to what we believed it was regardless of what the auctioneer said. We both had a general idea of what we wanted for this assignment so we did not have any different interpretations of attributes. An attribute that we wanted was brand. However it was very hard to figure out what brand each piece of clothing actually was. In the end we decided to remove that attribute. Every attribute we planned on adding was necessary except for brand. After doing the pilot, we realized we could answer a question that we previously did not think about. That question was “How does the number of viewers affect the final selling price of an item?” Because of the pilot, we are adding additional attributes (show title and bid type).

### Revised Data Dictionary

| Attribute  | Type	 | Description| Example |
| -------------|:-------------:|:-------------: |:-------------:|
|Channel Name |Categorical |The name of the auction channel/ seller|Youthforeverwholesale (yf.vtg), Mrtop Merchandise (Mrtop) |
|Style        |Categorical |The apparel style|Embroidered (EM), Printed (P), Blank (B)|
|Size         |Categorical |The size of the clothing |Small (S), Medium (M), Large (L), X-Large (XL), 2 X-Large (2XL), etc|
|Starting Bid |Quantitative|The starting price of the clothing|5|
|Ending Bid   |Quantitative|The final selling price of the clothing|100, 90, 30, 32, 0|
|Type         |Categorical |The type of clothing|Windbreaker, Jacket, Hoodie, Crewneck, etc|
|Show Title   |Categorical |Title of the livestream|VTG Sweater Show, Nike Show, Premium Sports Show|
|Bid Type     |Categorical |Type of auctioning in the stream |Auction or Sudden Death (SD)|  



# Task 3: Data description and domain questions

The dataset we collected is done per channel/livestream currently and is split by stream. All the streams watched and collected were clothing streams but they varied by type whether it was jackets, sweaters, or pants and there were also subtypes included. Each stream varied by size and length of the show but all attributes were applicable across all streams. This includes size of clothing (Categorical), stream name (Categorical), style (Categorical), clothing type (Categorical), starting bid (Quantitative), and ending bid (Quantitative). Overall everything was tough to record because most shows run items on a timer meaning we had only a few seconds to either remember or record all attributes while also monitoring several things per frame. This means that individual brands per show are unrealistic to record unless the shows themselves state the brand for the viewers.

During the streams we chose to capture size, stream title, style, clothing type, starting bid, and ending bid while we lost individual brand information, wear level/flaws, comments/activity, and prebid information on items that were prelisted. We decided making an item its own individual row was most appropriate especially for later visualization use since it would be easier to create graphs and charts if the data was easily split by shows or some other metric that repeats often. We chose to record everything the way it was displayed in the app so the starting/ending bid stayed quantitative/numerical since they were dollar amounts while everything else like style, type, size were categorical strings that could be abbreviated or easily typed.


Based on the data’s current state the most plausible domain questions would be:


- What types/styles of items receive the most bids?

Many different types and styles which could provide insight on what sways an item's price. 

* How does an item's starting price relate to its final selling price?

This could be compared if we add a few more streams with various starting prices but similar items.
* Are certain categories of clothing consistently sold for higher prices?

With so many categories of clothing especially in the vintage world it would be very easy to decipher a trend or pattern.
* How does the type of show affect the price an item sells for?

Visualizing price trend lines or caps based on the stream's bid type could easily present whether sudden death or auction produces more money.

# Task 4: Task abstractions

Translating the original and refined domain questions into abstract tasks helped us learn what we want to get out of the data rather than visualizations we can do. Our question of certain categories of clothes selling for higher prices becomes the abstract task of comparing ending bid values across clothing categories. Similarly for the question about types of shows impacting the price an item sells for helps to determine the relationship between bidding prices and time limits.Some of the other questions like the correlation between number of viewers and bid price are less possible because recording viewers at all times isn't feasible due to having to manually collect the data per item in such a short timespan. This is why we are now shifting our focus toward attributes that were consistently collected like size, style, type, starting bid, ending bid, and stream name or things that can easily split the data like stream type or stream channel. A main thing abstracting helped with is realizing it's more efficient to compare categories and identify patterns/relationships/trends rather than being tunnel visioned on a specific chart before understanding the task.

# Task 5:



<img width="621" height="189" alt="image" src="https://github.com/user-attachments/assets/b92a47d1-398c-43d0-99b3-2e8b5b996390" />

We wanted to create a visualization that shows many types and size combinations.  It addresses the question about whether certain categories sell for higher prices. This visual is a heatmap with clothing type as rows and size as columns (note that these are not all the clothing types for example purposes). Each cell shade shows the average ending bid with a lower bid being a lighter color and a higher bid being a darker color. The marks are areas (cells) and the channel is color. We believe it’s good for scanning areas of interest across each combination. Right now it’s hard to show the lighter and darker colors so if we do code this it’ll look a lot better. We also realize that a certain combination might have only 1 item that meets that criteria which could skew the results. We will refine this one so it shows the number of items of each combination. This differs from our other sketches by showing 2 categorical attributes and it also being a heatmap. 


<img width="458" height="341" alt="image" src="https://github.com/user-attachments/assets/cf4517a3-8af7-46a8-93b4-4f6a706a040a" />

We wanted to create a simple sketch that could answer which categories sell higher. Each bar is one clothing type. The bar lengths show an average ending bid from $0 to max. The marks are lines and the channels are vertical length and horizontal position. What worked well was that it’s easy to read and shows a quick rank. It might not work well because it is not that informative and it doesn’t show how many items are in each category. It's different from our other sketches because it gives one number per category and it is a bar chart. 

<img width="623" height="371" alt="image" src="https://github.com/user-attachments/assets/3fb243ec-0147-4d82-af09-e1b9d5482939" />

This sketch was motivated by us wanting to know the difference between auction and sudden death. It answers our domain question about how the type of show affects price. The y-axis is the average ending bid and our x-axis is split into 2 groups: Auction and Sudden death. Each dot is one stream. The marks are the point and the channels are vertical position and color. What this does well is that it could clearly tell us if auction or sudden death format streams have better bids. What doesn’t really work/ a problem is that we don’t have many points (currently working towards watching more streams and adding to this visualization). This is different from other sketches because it compares directly with other streams instead of items. 

<img width="622" height="496" alt="image" src="https://github.com/user-attachments/assets/2cb8ec5a-641a-4b0f-af73-09fe59fce3b5" />

Our motivation for this visualization was that we wanted to see the amount bidded as a show goes on and see if an auctioneer leaves the best for last and also if the stream being auction or sudden death relates to it. This visual relates to our domain question on how the type of show affects price. The x-axis shows each item from beginning to end (this is how we recorded the information so we think it’s possible). The y-axis is the ending bid. The mark is the line and the channels are vertical and horizontal positions. What works well is that it is good at showing the overall direction of bids as the show goes on. What doesn’t work well is that this only shows one line (which is one stream) which is limited and doesn’t give us a lot of information (we will refine this one). It differs from the other sketches by it showing a trend over time which we didn’t really do with the others. 

<img width="623" height="439" alt="image" src="https://github.com/user-attachments/assets/93005acf-15f9-4b9c-b300-381b0bb4c64b" />

This visualization was motivated by us wanting to see if clothes starting at different bids made a difference to its final price. This visual relates to our domain question of starting vs final price. The x-axis groups items by starting bid and each boxplot shows the spread of ending bids for that group. The marks are boxes and the channels are horizontal and vertical positions. It works well by potentially showing that items with similar starting bids can end up at very different prices. What doesn’t work well is that we don’t have anything that shows the number of items for each boxplot and we only have a few starting bids (working on finding more and getting more variety into this visual). This differs from other sketches because it shows boxplots (distributions). 


<img width="624" height="331" alt="image" src="https://github.com/user-attachments/assets/20cfa3fe-0ea7-44c5-8f99-c4afd220e878" />

We wanted to see which style comes with which type to answer our domain question of which  types/styles of items receive the most bids. Each bar is a clothing type with the length of the bar showing how many items total each type has. Additionally each bar is split into printed, embroidered, and blank. The amount shaded in shows how many items of a particular clothing type has that style. The marks are the bars with the channels being the length and color. What worked well is that this visualization shows how items are distributed clearly. However this graph does seem pretty limiting so hopefully we can fix that as we work on this project more. As mentioned before this sketch is different from others by showing how style (print, embroidered, and blank) are distributed which we haven’t shown in other visualizations. 

### Refined Sketches

After discussing each visualization, we decided to refine our heatmap and line chart.

<img width="621" height="191" alt="image" src="https://github.com/user-attachments/assets/f4d96aa1-48e5-4c75-a24f-fced4162509e" />

For the refined heat map, it still addresses the question about whether certain categories sell for higher prices. The only difference is that now for each cell we included the count of each item. The attributes used in this visualization are clothing type, size, average ending bid, and count of items in each cell. The marks are cells and the channels are vertical/horizontal position and color. What we want someone to learn with this refinement is for example a dark cell with a count of 1 or 2 tells us the bid is based on very little data, while a dark cell with a count of 15 is much more trustworthy. From this visualization, someone should be able to see which clothing types and sizes sell for the most, judge how reliable each cell is, and notice gaps in our data.  

<img width="624" height="250" alt="image" src="https://github.com/user-attachments/assets/253046a9-a4fd-4afb-8045-6198ec18ea75" />

For our refined line chart, we updated the original single-line chart into a multi-line chart that compares the two show formats. This addresses our question about how the type of show affects the price an item sells for. The attributes used are item order within a stream on the x-axis, ending bid on the y-axis, and stream format. Each line represents one stream, and its color shows the format: red for auction and blue for sudden death. The marks are lines, and the channels are vertical/horizontal position and color. Adding all the streams makes it very easy to compare against auction vs auction, sudden death vs sudden death, and auction vs sudden death. Someone using this visualization could learn whether prices climb as a show goes on, whether one format reaches a higher ceiling, and how much variation there is between streams of the same format. 


# Task 6: Summarizing

Our domain questions in task 3 were as follows:

* What types/styles of items receive the most bids?

* How does an item's starting price relate to its final selling price?

* Are certain categories of clothing consistently sold for higher prices?

* How does the type of show affect the price an item sells for?



The charts we currently have in mind for our visualizations are as follows:

* Heatmap based on size, type, and bid price
* Barplot based on type and average bid price
* Scatterplot based on average bid price with auction compared to sudden death
* Line chart based on final bid price and item number
* Boxplot comparing summary statistics of varying starting prices
* Barplot split by clothing type and showing frequency of style

We looked at a lot of options for visualizations, some of which were extremely ambitious at the beginning because we wanted to pack as much information as possible into a singular design. This included charts that contained 6 attributes and all possible cell values where the x axis was the start bid incrementing to the final bid while the y axis was $0 to the highest price recorded while having a line chart split by category of clothing which would have led to over 300 lines in a single chart. That is an idea that needed to be scrapped due to it being visual clutter and data vomit with no real story telling. So we shifted our attention to less is more and thought of valuable attributes and trends we could display that would provide more thoughtful insight while maintaining a digestible visual. This brought the majority of our current chart ideas like a line chart representative of the trendline showing if final bid price increases or decreases the more items that are sold or the scatterplot that simply places average bid price on a grid comparing auction style shows to sudden death style shows. That shift in ideas also sparked other methods of displaying old goals, the heat map was a more probable method of displaying the majority of available data in one visualization because it includes most attributes while still being easy to understand and follow. That tedious process also led to the large variety we have within our design options with some other sample ones we have on hold because these current few visualizations can cover all domain questions quite well. We have comparisons for Sudden Death vs Auction, graphs grouped by clothes category to explore price distribution, and a large selection/frequency of clothes styles/types to recognize patterns in buyers and sellers. Our domain questions and design ideas are quite strong because they cover all domain aspects while also not being repetitive graphs but unfortunately there is some overlap between visualization ideas. That is a weakness of our design ideas because overlap means less exploration and data usage but it is also due to a weakness of the data collected. Our data doesn't contain brands or wear/flaws which could be crucial to price patterns or buyer patterns and if our data was able to include that then more visualizations would be possible as well as our current ones being able to provide more insight about what drives the prices in these shows.


# Task 7: Collaboration process

Our group is only 2 people so communication and collaboration was extremely easy, communication was handled simply over text. When the assignment was released at first we came up with a plan to divide and collect the data by watching the livestreams we would normally watch but instead of just buying and watching as usual we would also be recording the data necessary. We each watched a few streams and only recorded the ones that we believed could hold value and keep the data consistent which was vintage clothing. We used the same categorization system and guidelines to put certain items in certain boxes when things were vague or ambiguous when auctioned off. In terms of collaboration on the github and sketches/artifacts, we completed the sketches together in person since they needed to be hand drawn and did all task related work together over a discord call using google docs. We unfortunately did not realize that in the deliverables it is stated to use github to keep track of collaboration and contributions until we had already finished everything and were ready to convert it to a markdown and submit. All tasks and contributions were done equally and in any of the areas where someone did more work, the other would take on more work in a different area to even the difference. This included the odd number of tasks and the odd number of tables in the data collection. Throughout the process of our collaboration we faced no challenges and managed to compromise or agree on the distribution of work and decisions of meetings. This also includes collaboration prior to starting the project documents like brainstorming potential data ideas, interests in common, and possible visualization goals.
