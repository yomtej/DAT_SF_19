#Answers to Homework 1

##Question 1
**Using chipotle.tsv in the data subdirectory:**

###i. Look at the head and the tail, and think for a minute about how the data is structured. What do you think each column means? What do you think each row means? Tell me! (If you`re unsure, look at more of the file contents.)


1.	Download chipotle.tsv from github:
	Type `git clone https://github.com/yomtej/DAT_SF_19.git`

2.	Change directory into the folder where chipotle.tsv is:
	Type `cd DAT_SF_19/data`

3.	To see the head of the file:
	Type `head chipotle.tsv`

4.	To see the tail:
	Type `tail chipotle.tsv`

5.	Meaning of columns:

	Row | Meaning
	--- | ---
	order_id | unique identifier of each order
	quantity | the number of items ordered within that specific order
	item_name | name of item ordered
	choice_description | any custom requests or amendments to the item ordered
	item_price | cost of the order item


###ii. How many orders do there appear to be?

Using the command:
`sort -n chipotle.tsv | tail -n1 | cut -f1`

This shows that there are **1834 orders** assuming that the order_id is showing the number of orders made

###iii. How many lines are in the file?

`wc -l chipotle.tsv`

**4623 lines**

###iv. Which Burrito is more popular - Chicken or Steak?

Number of Chicken Burritos:

`cut -f3 chipotle.tsv | grep -i "chicken Burrito" | wc -l`
**553 Chicken Burritos**

Number of Steak Burritos:

`cut -f3 chipotle.tsv | grep -i "steak Burrito" | wc -l`
**368 Steak Burritos**

Chicken Burritos is more popular

###v. Do chicken burritos more often have black beans or pinto beans?

Number of Pinto Beans:

`cut -f3,4 chipotle.tsv | grep -i "Chicken Burrito" | grep -i "pinto beans" | wc -l `
**105 Pinto Beans**

`cut -f3,4 chipotle.tsv | grep -i "Chicken Burrito" | grep -i "black beans" | wc -l`
**282 Black Beans**

Black Beans is more popular

##Question 2
*Make a list of all of the CSV or TSV files in the DAT7 repo (using a single command). Think about how wildcard characters can help you with this task.*

`find . -name '*\.[ct]sv'`

##Question 3
*Count the number of occurrences of the word `dictionary` (regardless of case) across all files in the DAT7 repo*

`grep -ir "dictionary" . | wc -l`

There are 5 occurences


##Question 4
Use the the command line to discover something "interesting" about the Chipotle data. The advanced commands below may be helpful to you!

**Top 10 Items**

`cut -f3 chipotle.tsv | sort| uniq -c | sort -n -r | head -n5`

Item | Number
---- | ----
Chicken Bowl | 726
Chicken Burrito | 553
Chips and Guacamole | 479
Steak Burrito | 368
Canned Soft Drink | 301


**Least Popular Item:**

`cut -f3 chipotle.tsv | sort| uniq -c | sort -n -r | tail -n1`

Carnitas Salad

**Soda By Popularity**

`cut -f3-4 chipotle.tsv | grep -E "Canned|Drink" |cut -f2 | sort | uniq -c | sort -nr`

Soda | Number of Orders
---- | ----
Diet Coke | 134
Coke | 123
Sprite | 77
Lemonade | 33
Coca Cola | 26
Nestea | 20
Dr. Pepper | 18
Mountain Dew | 15
Diet Dr. Pepper | 13


**Most Popular Salsa Base**

`cut -f4 chipotle.tsv | cut -f1 -d, |grep -i "salsa"| sort | uniq -c | sort -nr`

Salsa Base | Number of Orders
------- | -------
Fresh Tomato Salsa | 1035
Roasted Chili Corn Salsa | 447
Tomatillo Red Chili Salsa | 316
Tomatillo Green Chili Salsa | 224
Fresh Tomato Salsa (Mild) | 215
Tomatillo-Red Chili Salsa (Hot) | 142
Roasted Chili Corn Salsa (Medium) | 118
Fresh Tomato Salsa (Mild) | 104
Tomatillo-Green Chili Salsa (Medium) | 62
... | ...


















