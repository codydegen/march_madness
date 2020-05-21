# March Madness Simulator

## Intro
March Madness Simulator was developed to examine picking strategies for different pool sizes to help you make more informed decisions when filling out a bracket.

[animation showcase](\assets\images\animation.gif)

Find the brackets that windmills consistently, use examples to identify under picked teams, and learn how to stack the odds in your favor.

Current build can be found [here](https://cd-march-madness.herokuapp.com/).

## Getting Started
* Find the deployed website at http://cd-march-madness.herokuapp.com/
* Additional features can be accessed by cloning the repository and running it locally. These features include:
  * Increase the number of entries or simulations
  * Run using women's March Madness data
  * Run using a different scoring system (ESPN Bracket Challenge's scoring system used by default)
* To run locally, do the following:
  * Clone the repository to your workstation
  * Ensure that Python 3.8.2 is installed
  * Run `pip install -r requirements.txt --user` 
  * Run `python -m app`
  * Open on [127.0.0.1:8050](http://127.0.0.1:8050/)
  * Further reading can be found [here](/further_reading.md) 

## How it Works
A pool of brackets is selected randomly from a database extracted from [ESPN's Tournament Challenge website](http://fantasy.espn.com/tournament-challenge-bracket/).Additional brackets are algorithmically generated and can act as benchmarks to the brackets entered into the pool. Three algorithmically generated brackets are provided:
* "most_valuable_teams" is generated using [538's Power Rating to estimate the best teams](https://projects.fivethirtyeight.com/2019-march-madness-predictions/) overall.
* "most_popular_teams" is generated using [data from ESPN](http://fantasy.espn.com/tournament-challenge-bracket/2019/en/whopickedwhom) on who the most popular teams are.
* "chalk" is generated by picking the highest seed in every matchup.

The games themselves are simulated thousands of times using a rough approximation of the methodology found [here](https://fivethirtyeight.com/methodology/how-our-march-madness-predictions-work-2/). The score and placing in the group for each entry is saved for every simulation, and the total percentage of time that a given entry comes in first or second, the percentage of time and entry falls in a given quartile, and the average placing over every simulation is recorded and shown. Individual brackets can be viewed, and a histogram of the final placements and final scores can be shown. If desired, you can run an analysis using only a subset of the results, if you want to see how the same brackets would do in a smaller pool, or with fewer simulations.

## Technologies
* Written in [Python](https://www.python.org/)
* [Sqlite](https://www.sqlite.org/index.html) for database storage
* [selenium](https://www.selenium.dev/), [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) for web scraping
* [pandas](https://pandas.pydata.org/) for data analysis
* [Dash](https://plotly.com/dash/), [plotly](https://plotly.com/) for data visualization
* [Heroku](https://www.heroku.com/) for hosting

## To-Do
* Immediate:
  * The project is complete for now, once 2021 rolls around, I may revisit to add some additional features.
* Long-term:
  * Enhance algorithm to develop bracket
    * Utilize who picked data to identify under-picked teams (Compare expected points versus picked percentage)
    * Enhance model to update elo after early round wins
  * Make output more user-friendly
    * Allow live input of entry
    * Allow entry or group import
    * Retain selected brackets when running subgroup analysis
    * Allow hot swapping between model inputs (swap between men's and women's natively, scoring system, increase number simulations or entries)
    * Show table of placings of each team
  * Allow for algorithmic creation of dummy brackets using who picked data
  * Structural:
    * Implement unit testing
    * Host database off-site to allow for larger data sets