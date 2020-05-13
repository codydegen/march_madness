# march_madness

## Intro
This is a program to simulate March Madness so high-value teams can be identified for the purposes of creating the optimal bracket.  Visualizations of the results for brackets for the March Madness Simulations are shown. Depending on the size of the pool entered, you can hopefully make some informed decisions on whether to go for a high-variance strategy (i.e., pick an out-of-left-field winner, make some savvy underdog picks) or just play it safe (pick a high seed to win, generally err on the side of less chaos).

Current build can be found [here](https://cd-march-madness.herokuapp.com/).

## Technologies
* Written in [Python](https://www.python.org/)
* [Sqlite](https://www.sqlite.org/index.html) for database storage
* [selenium](https://www.selenium.dev/), [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) for web scraping
* [pandas](https://pandas.pydata.org/) for data analysis
* [Dash](https://plotly.com/dash/), [plotly](https://plotly.com/) for data visualization
* [Heroku](https://www.heroku.com/) for hosting

## Getting started
* Find the deployed website at http://cd-march-madness.herokuapp.com/
* Or run locally by
  * install python3
  * pip install -r requirements.txt --user
  * python -m app
  * See further documentation on workflow [here](/workflow.md) 

## Methodology
To start, I feel like there are three key things that you need to know in order to fill out a good bracket.

* Knowing who the best teams are

Of course, seeds are the obvious answer here, but there are many different advanced analytics models that we can use to help us identify under and over seeded teams.  My favorite to use is the one put forward by [538](https://projects.fivethirtyeight.com/2020-march-madness-predictions/).

* Knowing about how well you have to do to win
  * do you need to take big swings or just do pretty well?  This helps decide whether you want to take a risk on the winter or just pick one of the top few teams and hope that you can ride out the rest with better early bracket picks.
  
* Knowing who other people are picking

The purpose here is to leverage what we know about other people to pick some teams that may be undervalued by the general public and avoid teams that are overvalued. I used the ["Who picked Whom"](http://fantasy.espn.com/tournament-challenge-bracket/2019/en/whopickedwhom) data from ESPN but there are likely other sources that would work equally well. A few ways this plays out:
  * there's an 8-9 or 7-10 matchup that analytics say is going to be a coin toss, but the public is heavily favoring one side of it.  Picking the other side of that matchup is an easy way to carve out a small advantage.
  * You're in a pool with a lot of people who are fans of a specific team in the tournament. No matter how good or bad that team is, people are to be picking them to go much further than they should be.  You can exploit that by picking a relatively early exit for that team.

## To-Do
* Add other entries to table
* Determine whether choosing explicit entries or calculating based on entire group is better
* Improve bracket output
* add selected bracket to other histograms
* Long-term:
  * knowing who the best teams are
    * enhance model to update elo after early round wins (Low priority)
  * knowing who other people are picking
    * compare expected points versus who picked percentage
    * estimate homer factor (Low priority)
  * implement unit testing ( should be high-priority but this project is going on for so long that it'll probably end up not happening )