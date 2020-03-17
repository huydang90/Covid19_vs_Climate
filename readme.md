<p align="center">
<b><a href="#hypothesis">Hypothesis</a></b>
|
<b><a href="#data-collection">Data Collection</a></b>
|
<b><a href="#data-processing">Data Processing</a></b>
|
<b><a href="#modelling">Modelling</a></b>
|
<b><a href="#results-and-interpretation">Results and Interpretation</a></b>
|
<b><a href="#analysis">Analysis</a></b>
|
<b><a href="#implications">implications</a></b>
|
<b><a href="#potential-issues-and-model-improvement">Potential issues and model improvement</a></b>
|
<b><a href="#acknowledgements">Acknowledgements</a></b>
</p>

# Covid-19 vs. Climate 

### Will summer save us from coronavirus? 

The short answer is: Statistically, maybe! 

Much have been speculated about whether or not the high temperature of summer will bring about the end of the coronavirus madness as it has with other seasonal flu. Some believes it's true. Others have their doubts since there are so many mysteries about the coronavirus that are still unknown to us. To scope out a potential answer for this problem, this notebook looks at the relationship between the number of confirmed Covid-19 cases in Italian and German regions and the temperature as well as humidity of these regions.  

![alt text](https://raw.githubusercontent.com/huydang90/Covid19_vs_Climate/master/figures/comparison.png)

Visually, we can see that regions with lower temperature and higher humidity seems to fare better in terms of the number of Covid-19 cases. 

## Hypothesis: 

- For Italy, regions with temperature higher than 15 degree Celsius and 75% humidity encounters less spread of covid-19 cases than others. 

- A research recently undertaken found a striking similarity between the temperature and humidity between regions that have major coronavirus outbreaks. They are located along the same temperature zone in the northern hemisphere. It includes outbreak epicenters such as China’s central province of Hubei, South Korea, Japan, Iran, Northwestern America and Northern Italy. It is found that the places share an average temperature of 5°C to 11°C (41°F to 52°F) and 47% to 79% humidity.

- Our hypothesis, therefore, is that area with average temperature and humidity level higher than these regions will see a decrease in the spread of the virus. 

- After experimentation, I have set the threshold of temperature at 15 degree Celcius and humidity at 75% humidity. You can toggle with the temperature and humidity parameters to identify the suitable climate conditions for your hypothesis, based on the country of your analysis. These numbers will be subtracted from the max value of temperature and the overall humidity during the day of Italian and German regions in the modelling analysis.


## Data Collection: 

- Italian cases data: [GediDigital](https://lab.gedidigital.it/gedi-visual/2020/coronavirus-i-contagi-in-italia/)
- German cases data: [MorgenPost](https://interaktiv.morgenpost.de/corona-virus-karte-infektionen-deutschland-weltweit/?fbclid=IwAR04HlqzakGaNssQzbz4d8o8R3gz0C910U8tvfYlBT6P0lVJJvHfk9uS2rc)
- Weather data: temperature, humidity and wind is collected from [Meteoblue](https://www.meteoblue.com/) and [Time and Date](https://www.timeanddate.com/) for the capitals of the regions in question, as an approximation of the regions themselves; 


## Data processing: 

- The number of confirmed coronavirus cases (our dependent/response variable) will be log-transformed to make it follow a normal distribution as per the assumption of statistical analysis, since the original data is skewed highly in selected states. 

## Modelling: 

- Naive OLS estimate is utilized for simplicity and ease of interpretation; 

**Model 1 for Infected cases**: log (Number of cases on Mar 16) = α(T emperature − 15C) + β(Humidity − 75%) + \epsilon 

**Model 2 for Growth rate**: log (Cases on Mar 16/ Cases on Mar 3) = α(T emperature − 15C) + β(Humidity − 75%) + \epsilon

- For expansion of research, more complex models with proper causal analysis controlling for confounding variables should be created to capture the true effect of temperature and humidity on the spread of coronavirus cases.  

## Results and Interpretation: 

####For Italy: 
- R-squared shows that the model can explain for about 27-34% of variations in the number of coronavirus cases, which is expected, considering there are many other factors influencing the spread of the disease; 
- A one-unit increase in temperature in Italian regions with above 15 degree Celcius and 80% humidity will lead to 67.14% decrease in the number of covid-19 cases in comparison to regions that are below this threshold;
- A one-unit increase in humidity in Italian region with above 75% humidity and 15 degree Celsius will lead to 16.26% decrease in the number of covid-19 cases in comparison to regions that are below this threshold.
![alt text](https://raw.githubusercontent.com/huydang90/Covid19_vs_Climate/master/figures/infected_cases.png)


####For Germany: 
- A one-unit increase in temperature in German regions with above 16 degree Celcius and 75% humidity will lead to 42.15% decrease in the number of covid-19 cases in comparison to regions that are below this threshold;
- A one-unit increase in humidity in German region with above 75% humidity and 16 degree Celsius will lead to 15.26% decrease in the number of covid-19 cases in comparison to regions that are below this threshold.
- In Germany case, however, the effect is not statistically significant (see Analysis)

## Analysis: 
- Lombardy is the epicenter of the diseases from where it spreads throughout the country. It will, naturally, have more cases than other regions. 
- Similarly, Bavaria, Baden-Wuerttemberg and North Rhine-Westphalia regions in Germany were the first to detect coronavirus cases and are currently being affected more heavily than others. These regions also have their temperature hover around 15 degree Celcius. 
- Therefore, the estimate of the model in this case would be biased heavily against these samples. 

## Implications: 
- An understanding of factors that can reduce/increase the spread of the disease can help us to prepare and plan better for our socio-economic activities, based on weather and meteorological forecast;
- Knowing whether there is seasonality in the virus informs us when to best protect vulnerable groups in our society;
- It is a wise option for lockdown and social distancing until temperature rises to help reducing the number of infected cases further in synergy with the summer effect.  

## Potential issues and model improvement: 
- **Limited number of observations**;
- **Collinearity** between temperatures and humidity: 100% humidity at 8 degree Celsius is the equivalent of 28.5% at 30 degree Celsius, meaning when temperature is high, absolute humidity (real humidity) increases by an order of magnitude;
- **Other metrics** than R-squared to capture the causal impact 
- **Confounding factors**: since there are so many unknown unknowns about the coronavirus, it's hard to pinpoint all the ommitted variables that might bias this estimate. One example is the spatial autocorrelation in the data. Italy has a lean and long shape along which are large plains, valleys and mountains which might also be influencing the climate and how the virus spreads. A causal analysis to untangle these confounding variables from our model can help to  gauge the true estimates of how temperature and humidity is driving the number of cases;
- **Data issues**: such as whether we can trust the data updated at the individual regional and state level.

## Acknowledgement: 

This analysis is inspired by the theoretical framework of Covid19 Seasonality established in [Temperature and Latitude Analysis to Predict Potential Spread and Seasonality for COVID-19
](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3550308) by M. Sajadi et al. and analysis by [Giang Le](https://github.com/kinhtetaichinh). 
