MLB Pitchers Before and After the "Sticky Stuff" Ban During the 2021 MLB Season

This is a project I did with one partner for my Linear Models (MATH 351) class I took during the Fall 2021 semester. We both are big fans of the MLB and at the time there was a big 
scandal during the previous season involving pitchers utilizing illegal substances to gain an advantage through handling the ball better and thus having better control of their pitches.

Our research question was aimed at further investigating the impact that this ban had on the performance of MLB pitchers throughout the season. We really wanted to know how much of a 
hold sticky substances had on pitchers. Our hypothesis is that pitchers will have worse stats after the ban, because enough guys were using these substances that it will show in the data. 

We gathered our data set from the baseball statistics website FanGraphs. This website is a hub for all stats regarding baseball. The website also allows you to get stats before and after a date 
which was very important to us. We were able to gather data on qualified pitchers from before and after June 21st (the date of the ban), on separate sheets which made it very easy to compare. 
A “qualified” pitcher is any pitcher who threw 1 inning per team game played. This is a very common MLB qualification that makes it so that someone with only 10 innings pitched
cannot be compared to someone with 100 innings pitched because that would not be fair. For the “before” data, we selected the dates from opening day until June 21st, 
and for the after data we selected from June 21st to the end of the season. We also had to delete any pitchers that did not meet the innings pitched criteria before and after, 
because we only wanted pitchers that did both so we could compare the stats. This left us with 48 total pitchers who were included in our data set.

We felt that the metric xFIP was best suited for our dependent variable. xFIP is a stat that stands for expected fielding independent pitching. This means the stat is the expected runs a pitcher will allow, independent of fielding. 
This stat is best used to see how pitchers performed before and after the ban because it gets rid of anything having to do with the defense, which can vary dramatically from team to team. 
With this stat, a pitcher with 5 year olds on defense, will be judged on the same scale as someone with 8 MLB all stars on defense. 

This is the xFIP equation: 
<img width="995" alt="Screen Shot 2024-09-12 at 11 10 59 PM" src="https://github.com/user-attachments/assets/7db95e5c-5896-4ff8-8e22-7159ed230622">

Now that we had our dependent variable we had to chose potential regressors to include in our model. We decided to make our own "delta" versions of common pitching statistics 
to better represent the change for each pitcher from before to after the ban. Ulitametly, we chose 6 potential regressors for our model:

Change in HR/9 - home runs given up per 9 innings pitched

Change in K/9 - number of strikeouts per 9 innings pitched

Change in BB/9 - number of walks per 9 innings pitched 

Change in GB% - percent of balls hit that are ground balls 

Change in HR/FB% - percent of fly balls that are home runs

Change in BABIP - opposing batter average disregarding strikeouts

We then ran single variable linera models for each of these potential regressors to better understand the potential impact these statistics may have. 
This resulted in the following residual plots:

<img width="1020" alt="Screen Shot 2024-09-12 at 11 16 14 PM" src="https://github.com/user-attachments/assets/fabf3d70-2a30-467f-b237-42dfb8f098e4">


We then did forward selection to find the best model which was:
`dxfip ~ dK/9 + dBB/9 + dGB% + dHR/9 + dHR/FB%`
We double checked this with backwards elimination which resulted in the same exact model. This shows 5/6 of our initial regressors were significant enough for use in the model. 
Change in BABIP was removed or not added to the model with both forward and backwards selection
After we had this model we checked the model using Mallow’s CP to make sure it was the best model and we found a CP of 5.236 which is very close to the (m+1) score of 6 
that you want the CP to be close to, which means it is the best model. This model also had an adjusted R2 of 0.9227 which is very good. This R2 value means our model explains 92.27% of the change in xFIP.

Here is the summary table of our model:

<img width="401" alt="Screen Shot 2024-09-12 at 11 22 15 PM" src="https://github.com/user-attachments/assets/1702edc9-7cbe-404d-b6b8-3afa6e79c5ca">

The largest absolute estimate was change in HR/9 which makes sense when thinking about this situation because the equation for xFIP heavily weights home runs because they are bad for pitchers.
All of the values are small in general because they are all rates or ratios, a small increase in these stats, means a lot in terms of baseball.

We then did residual analysis of the model. First we ran the studentized residual. We found that the residuals plotted against the fitted values were evenly distributed and 
there was no cone shape going on. They were evenly spread about the horizontal axis 0. This all means that is likely a good model. We then looked at a normal qq plot.
The points are roughly linear even though the line of best fit is a little strange, but we thought this still represented our model as being quality.
<img width="975" alt="Screen Shot 2024-09-12 at 11 59 40 PM" src="https://github.com/user-attachments/assets/f82f54d3-a9f9-4a8d-b720-619bdece1da2">

We then wanted to look at influence diagnostics. We ran “Cook’s distance” on our model and found that using the cutoff of unity, we had no points that were greater than or equal to 1. 
However, using Belsley’s cutoff of .095, we had 3 observations over this at .178, .162, and .149. These three observations could be influential, but we think they are not very influential because they are still pretty small. 
These three pitchers are Kyle Hendricks, Tarik Skubal, and Rich Hill who were three guys we struggled to fit the model well with because they are all extremely unique pitchers 
in that they throw very slow and give up a significant amount of home runs, but still had very good stats overall in terms of K/9 and BB/9 and HR/9. 
We also ran DFFITS on our model and found that none were near the suggested cutoff of 2, with our largest in magnitude being 1.107. Overall, looking at the 
influential/ leverage points, we think the model is still very strong because only 3 points stood out, and they only stood out when using the more extreme method of the three we used, and even then, they barely stood out. 


- Conclusion
  
We believe that our findings were statistically significant. The estimates in our model all had a p value well below zero meaning they were all significant.
The estimates in our model all pointed towards an increase in xFIP, and we found that on average, xFIP went up .08. 14 of our 48 pitchers saw an increase in xFIP greater than .3,
which is a very significant increase. An increase of .3 takes a pitcher from league average, to poor on the xFIP scale. Our model shows that this group of pitchers got worse
at every single stat related to xFIP. Strikeouts as a group went down, walks went up, home runs went up, ground balls went down and HR to FB % went down. All of these changes
point towards pitchers being significantly worse after the ban of sticky substances and all of these changes explain why xFIP got worse, showing that our hypothesis was correct.
It is impossible to say for sure if these pitchers who saw decreases were cheating, but all of the changes in their stats could be explained by a lack of grip on the ball
due to the ban of sticky substances. These changes could also be from pitchers having an excellent season before the ban, and an average one after. The changes could also
be explained from just general fatigue as the season wears on. However, based on our evidence, there is a strong case that some pitchers were indeed cheating.
We believe if we got another sample of the same size we would have similar results because this group of pitchers is about as unique as it gets in terms of age, experience, and pitching style.

Data - https://www.fangraphs.com/leaders.aspx?pos=all&stats=pit&lg=all&qual=y&type=8&season=2021&month=1000&season1=2021&ind=0&team=0&rost=0&age=0&filter=&players=0&startdate=2021-04-01&enddate=2021-06-21
