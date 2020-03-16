# Covid-19 vs. Climate 

Will summer save us from coronavirus? 

The short answer is: statistically, yes! 

Much have been speculated about whether or not the high temperature of summer will bring about the end of the coronavirus madness as it has with other seasonal flu. Some believes it's true. Others have their doubts since there are so many mysteries about the coronavirus that are still unknown to us. To scope out a potential answer for this problem, this notebook looks at the relationship between the number of confirmed covid-19 cases in Italian and German regions and the temperature as well as humidity of these regions.  

Result: 
- A one-unit increase in temperature in Italian regions with above 15 degree Celcius and 75% humidity will lead to 65.86% decrease in the number of covid-19 cases in comparison to regions that are below this threshold
- A one-unit increase in humidity in Italian region with above 75% humidity and 15 degree Celsius will lead to 15.89% decrease in the number of covid-19 cases in comparison to regions that are below this threshold

Implication: 
- An understanding of factors that can reduce/increase the spread of the disease can help us to prepare and plan better for our socio-economic activities, based on weather and meteorological forecast;
- Knowing whether there is seasonality in the virus informs us when to best protect vulnerable groups in our society.  

Factors that might bias the model: 
- Lombardy is the epicenter of the diseases from where it spreads throughout the country. This has not been figured into the model; 
- Other confounding factors: since there are so many unknown unknowns about the coronavirus. It's hard to pinpoint all the ommitted variables that might bias this estimate. One example is the geographical shape of the country. Italy has a lean and long shape along which are large plains, valleys and mountains which might also be influencing the climate and how the virus spreads. A causal analysis to untangle these confounding variables from our model can help to  gauge the true estimates of how temperature and humidity is driving the number of cases;
- Other assumptions about the model: such as whether we can trust the data updated at the individual regional and state level.
