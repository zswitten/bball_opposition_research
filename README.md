# bball_opposition_research

I had/have a theory that raw on/off defensive numbers make Zion Williamson look better on defense than he really is. The mechanism I have in mind: Zion is such a unique offensive talent that other teams are forced to play worse offensive players in order to stand a chance to guard him. Big hulking centers and the like. This effect should be stronger for Zion than for other great scorers like KD or Kawhi because those players' scoring is more defense-independent; they're tall enough that they can get their shot off against anyone. And also the players who guard them well tend to be other forwards, who are generally better shooters than the players who guard Zion the best (nonshooting centers).

I set out to prove this theory, and (spoiler alert) I wasn't able to find any evidence for it really. Despite that, I'm documenting my work to give myself closure, as a starting point in case anyone else wants to pick it up, and also because I learned a few fun facts.

To start, I scraped ORPM and DRPM, and minutes-played statistics from http://www.espn.com/nba/statistics/rpm/_/. I scraped statistics on how much each player has played against each other player using the pbpstats.com API. You can see the code for doing so, and for merging the two data sources, in [the notebook](https://github.com/zswitten/bball_opposition_research/blob/main/orpm_on_off_scrape_possessions.ipynb).

My thought was that compared to his teammates, and compared to other players in the league, Zion's opponents would have a higher minutes-weighted average DRPM, and lower ORPM. Instead, Zion was right in the middle for the starters; the average ORPM of opposing teams while he was on the court was higher than for his co-starters Brandon Ingram and Jonas Valanciunas, while being lower than fellow starters C.J. McCollum and Trey Murphy.

Here are the fun facts I learned/possible confounders.

- Starters (who are better than bench players) play more minutes against other teams' starters, who are better than bench players. This one I could have figured out without data just by thinking about it a little more.

- Relatedly, there's a very strong correlation between minutes played and both average DRPM of opponent (0.7) and your personal DRPM (0.64). However, the correlation for offense (both yours and your opponents') is much weaker (0.2, 0.14). It's kind of funny that the correlations are stronger with your opponents' stats than with your own.
<img src="https://github.com/zswitten/bball_opposition_research/blob/main/Screen%20Shot%202023-02-03%20at%206.19.47%20PM.png" width=50% height=50%>
<img src="https://github.com/zswitten/bball_opposition_research/blob/main/Screen%20Shot%202023-02-03%20at%206.19.57%20PM.png" width=50% height=50%>

- It's probably no surprise that the positions filled by larger players have higher DRPMS.
<img src="https://github.com/zswitten/bball_opposition_research/blob/main/avg_drpm_by_position.png" width=50% height=50%>
What was surprising to me is that while centers face the highest average DRPM, it goes size-backward after that, with PGs facing the second-highest. Perhaps this is due to many teams running their offenses through star point guards who play a lot of minutes.
<img src="https://github.com/zswitten/bball_opposition_research/blob/main/avg_opp_drpm_by_position.png" width=50% height=50%>
Meanwhile, below is the average ORPM by position; mostly it's the inverse of the DRPM except that centers are slightly better on offense than power forwards (Jokic and Embiid say hello).
<img src="https://github.com/zswitten/bball_opposition_research/blob/main/avg_orpm_by_position.png" width=50% height=50%>

- This analysis would be more precise if I controlled for strength of schedule. A sign of this is that all three of the Lakers "stars" (AD, LeBron, Russ) are in the top 10 for high opponent ORPMs which probably just means the Lakers have faced good offenses.
