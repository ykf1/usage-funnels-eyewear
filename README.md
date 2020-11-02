# usage-funnels-eyewear

This is a codecademy project using SQL to analyse purchase funnels for a designer eyewear company based on fictional data. The data provided are namely: 'survey', 'quiz', 'home_try_on' and 'purchase'. I have attached the code used in this project and the output results in an Excel file in this repository. The objective is to find out whether or not customers who get more pairs to try on at home will be more likely to make a purchase.

The purchase funnel is:

Take the Style Quiz → Home Try-On → Purchase the Perfect Pair of Glasses

A potential customer will take the quiz, and based on the results, the company will deliver x number of pairs of eyeglasses to the customer's home to try-on, and the customer can decide whether to make a purchase or not.

Before we start on analysing the test, I will first do a quick analysis on the survey and the responses.

The designer eyewear company has a Style Quiz that has the following questions:
1. What are you looking for?
2. What is your fit?
3. Which shapes do you like?
4. Which colors do you like?
5. When was your last eye exam?

The users’ responses are stored in the table 'survey'.

By obtaining the sum of responses for each survey question, I managed to calculate the percentage of responses for each question. It appears that questions 1, 2 and 4 have higher completion rates of over 95%, while questions like 'which shapes do you like' and 'when was your last exam?' was answered less frequently at 80% and 75% respectively.

I next looked at the common results of the survey (stored in table 'quiz') and analysed the survey responses with respect to style, fit and shape of eyeglasses preferred by the survey responders. For style, 47% favoured Women's style while 43% favoured Men's style. For fit, there is significant preference for Narrow (41%) and Medium (31%) while less for Wide (20%). For shape, there is again significant preference for Rectangular (40%) and Square (33%) while less for Round (18%) and No preference (10%).

Eyeglasses purchases are stored in the table 'purchase'. I next looked at the breakdown of purchases made by style and model_name. Based on the results, we can tell the popularity of the various models for both Men's and Women's styles.

Finally, we are going to analyse the company's purchase funnel. Again, the purchase funnel is:

Take the Style Quiz → Home Try-On → Purchase the Perfect Pair of Glasses

A potential customer will take the quiz, and based on the results, the company will deliver x number of pairs of eyeglasses to the customer's home to try-on, and the customer can decide whether to make a purchase or not.

During the Home Try-On stage, we will be conducting an A/B Test:

    50% of the users will get 3 pairs to try on
    50% of the users will get 5 pairs to try on

The objective is to find out whether or not users who get more pairs to try on at home will be more likely to make a purchase.

The data will be distributed across three tables: 'quiz' (the survey quiz responses), 'home_try_on' (customers who received 3 or 5 pairs), 'purchase' (customers who make purchases) The code uses LEFT JOIN's to combine the three tables based upon user_id. If there is data under the 'home_try_on' or 'purchase' columns, we will give a value of 1 else 0. This is because if there is no data, i.e. Null value, then the customer did not proceed to home try-on or made a purchase and the data is not found in the corresponding tables. 

I then computed overall conversion rates by aggregating across all rows and compare conversion from quiz→home_try_on and home_try_on→purchase. Out of 1000 potential customers, 750 (or 75%) tried the eyeglasses at home, and 495 (or 66% from the 750) made a purchase.

We can also calculate the difference in purchase rates between customers who had 3 pairs to try-on with ones who had 5. Using similar code as above but with GROUP BY on 'number_of_pairs', we obtained a result of 79% conversion for customers who made a purchase from home try-on with 5 pairs of eyeglasses compared to 53% conversion for customers who made a purchase from home try-on with 3 pairs of eyeglasses. 

The results show that sending more pairs of eyeglasses for home-try on can significantly increase the likelihood of a potential customer purchasing a pair of eyeglasses.

