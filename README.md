# Midterm Project for Applied Statistics and Probability
Data science midterm project for Applied Statistics and Probability

http://applied-stats-midterm-jacobjzhang.c9users.io:8080/notebooks/Midterm%20Project.ipynb

## Idea Behind the Project
My girlfriend and I have been traveling a significant amount recently, and we've been fortunate enough to explore some diverse parts of the world. Perhaps because we are generally introverted, we've noticed that that we much prefer less-populated, quieter cities. The initial reasons we conjured up for this were the obvious ones: less traffic, more peaceful activities, and more space to reflect. However, large cities offer serene areas to relax as well, and I also noticed that the general well-being of residents in smaller cities were greater even when they were in busy areas (shopping plazas, town halls, etc.). 

With that, I developed the following question to answer: is there a correlation between the population size of a region and the well being of its residents? To utilize a quantitative approach to derive an answer, I gathered a few datasets and will set out to analyze them via the techniques we’ve learned in class, and see if having less people per square mile generally improves their livelihoods.

In reasoning about our approach, there a few assumptions to tackle. Firstly, the terms “well-being” and “happiness” are incredibly ambiguous and generally difficult thing to measure. As human beings, our moods and answers to the question "how do you feel?" vary considerably on a daily basis. I quickly realized that there was a twofold issue with using general "well-being"-- firstly, that data point is difficult to find, and secondly, that it would not lead to consistent, valuable results.

The other issue is that there was a scarcity of information for international regions. Not only was I unable to find consistent data to measure well-being in other countries, but I feared that cultural draws or aversions to the effects of increasing populations would introduce a variable I did not want.

A better approach then is to use a standard measurement of well-being that the academic community uses, namely the HDI or Human Development Index, and apply that on a micro level to only the US areas and populations for which we have sufficient data over. The wikipedia page (https://en.wikipedia.org/wiki/Human_Development_Index) defines it as “a composite statistic of life expectancy, education, and per capita income indicators, which are used to rank countries into four tiers of human development.” Our index will thus consider average income level, access to education, and access to healthcare in calculating a raw score for “local” well-being.

In trying to find data for answering the question, I found three tremendous datasets from the last (2012) American Economic Census that provide many points from which we can begin to analyze. They are as follows, all found at http://www.census.gov/econ/census/data/geo.html in different formats. One thing to note is that in terms of selecting the “level” of region to use, I chose to use "general metropolitan area" as opposed to “county”, “city”, “state”, or “zip”. It presented a happy medium of having sufficient data without being too granular, which would end up making the data unwieldy and difficult to clean up. At the zip and city levels, we’d need to manage over 30,000 rows of data points for each factor as opposed to under 10,000 for “general metropolitan area”.

The first of these data is a census of the number of educational establishments in an area. The dataset gives us information regarding the number of all educational establishments (university, training, etc.), as well as their revenues, expenses, and payroll. I chose to utilize this over measures of the “quality” of universities in a region. Our inherent assumption is that "access" to education is more important for the general population than quality. Using this business data with the addition of the region's population size, we'll be able to gain some valuable insights into how many educational options the average resident will have (which is key), as well as how much money is spent and how many paid educational employees there are.

We’ll be able to take the same approach with healthcare access. The US economic census for healthcare establishments in 2012 gave similar information to the educational census, revealing information about the businesses themselves (number of hospitals and general health care establishments, employee count, etc.) Again, access to health care establishments takes precedence over their quality in our well-being score. It is important to point out, however, that one confounding factor could be the role of health care insurance-- there may be more hospitals per person in Area A versus Area B, but residents in Area B may have better access due to universal health care policies. We may need to account for this by examining insurance rates in these regions as well.

The third aspect, regarding average income, required a different approach due to the confidentiality of wage information. I was able to attain statistics for all U.S. firms via a 2012 Survey of Business Owners. While not perfect because there is an inherent bias in the responses, because we are shooting for relativity rather than absolute data, this should not be an issue. The dataset comes with the number of all firms in a specified area, with their tallies on paid employees, their total sales and receipts, their annual payroll, and much more. This combination of information is powerful-- it will allow us to ascertain an average salary for the region, but also gives us additional statistics to dig into if we are curious. For example, it may also be valuable to see the number of paid employees relative to the population for any given region, so we can see how large a role relative unemployment plays.

Most of the challenges with cleaning and wrangling this data will come with aligning the data points to the proper region, and figuring out which factors can be left out. I believe that there will be enough information to properly answer the question, and hopefully gain some insights into regional well-being and how population size affects it.

# Table of Contents (Plan)
* Wrangle the data (one big CSV)
    1. Limit to all establishments to easily merge CSVs
    2. Demonstrate using Python

1. Examine the distribution and probability of income levels in these regions
    * Also, examine the nature of businesses and total revenue per person (is money going to employees vs. executives?)
2. Examine the distribution and probability of Educational Facilities
3. Examine the distribution and probability of Healthcare Facilities
4. Calculate the "HDI" for all regions
5. Sort, rank, median, and mode the regions
6. Calculate ratios with population and see which had the largest effect in HDI
7. Describe findings