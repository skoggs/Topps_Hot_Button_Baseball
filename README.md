# Hot_Button_Baseball
An Excel worksheet of statistical analysis for a forgotten Topps card game.

# Introduction
Topps Hot Button baseball is a collectible card game published by Topps in 2005 and designed by [Scott Balaban](http://www.scottbalaban.com/index.htm). Although it had some
interesting ideas behind it, the product is considered a [commercial failure](https://sportscollectorsdigest.com/cards/kaplan-baseball-cards-needed-overhaul). Aside from contents
from the starter kit, the cards are therefore fairly difficult to come by. This would have made this document quite a challenge to put together. Luckily, nicksang, cynicalbuddha,
and several others have scanned and uploaded the entire base set which can be found [here](https://www.tcdb.com/ViewSet.cfm/sid/9795/2005-Topps-Hot-Button).Their work enabled me
to enter and analyze the data of the 140 player cards for this pet project. That brings us to what I am doing here. I love overanalyzing card games, obscure or not, and the level of advanced baseball analysis out there means we can do a reasonably
accurate and in-depth analysis of it. (Shout out to the [Showdown Card Bot](https://github.com/mgula57/mlb_showdown_card_bot) which had this as a key feature.). 

# Methodology
The ultimate purpose of this model is to use the characteristics of each player's card and project them onto an approximate full season of of results. This enables me to evaluate
the ability of individual cards relative to real life player performance. To do so, I take a runs based approach. Each outcome on a player card has an estimated effect on a team's
run total, which are evaluated on a [Linear Weights Table](https://library.fangraphs.com/principles/linear-weights/). I then multiply these outcome effects by the chances of each
one occuring and by a selected number of plate appearances/batters faced. 600 plate appearances are chosen for an approximate full season for hitters and 900 batters faced for
an approximate full season for pitchers. After run production is calculated (or prevention in the case for pitchers), they are converted to WAR/Wins Above Replacement through a
division of 10. Finally, each player's WAR is adjusted to achieve an approximate average of 2 throughout the player pool.

As far as baseball analytics go, this is all relatively straightforward. However, the Hot Button Baseball hardware does complicate things a bit in that the probability of each
player outcome is undisclosed. The game's manual hints that each outcome is not equally likely to happen ("results listed as the top occur more often than the results listed at
the bottom". To approximate these odds, I took a sample of 500 lights on the hardware and assigned a chance to each of the game's light. Even with a sample as high as 500, there
is bound to be a slight deviation for my experimental odds, but my hope is that this is accurate enough for the purposes of this analysis.

# Special Abilities
One thing you will notice in my batter/pitcher specific spreadsheets are WAR evaluations based on Special abilities. Indeed, there are separate ratings that disregard special
abilities and include special abilities which are each adjusted to have an average of 2 WAR. Since special abilities are optional, they are theoeretically beneficial or ignored,
so players with weak special abilities have comparatively low WAR.

Now, about the mechanics of the special abilities. Special abilities give each player a different set of 10 outcomes to play around with, and most of them work the same way. 
You declare right before the plate appearance whether you want to use the special ability or not. If you do, you use the special ability side for that plate appearance. 
Many special abilities are restricted to once per inning, including all pitcher abilities and the (quite strong) "Power Surge" batter ability. For player evaluation, it is assumed
that they are used as often as possible if they are beneficial in a vacuum. For example, J.T. Snow's "Make Contact" ability is assumed to be always used since its outcomes are
generally preferably to his normal outcomes, and there is no limit to the use of "Make Contact". However, since Lance Berkman's "Power Surge" ability is limited to once per inning,
his evaluation is based on the assumption that only 3 "Power Surge" users are used in a lineup and that sometimes you will not be able to use the ability.

There is one ability that works completely differently from all the others: the "Steal" ability. This can only be used immediately after the player with the ability reaches base.
"Steal" is quite interesting for two reasons. First, all opponent's lights count for a successful stolen base attempt, giving the ability a flat 50% increase in success rate. 
Second, it enhances instead of replaces the player's "normal" outcomes, which makes it a quite handy buff for players with an estimated success rate of 80%+. 

Speaking of success rate, this is a box in the spreadsheet that shows about how often that ability will be successful. Most of the results of special abilities are binary, in that
they are basically either successful or not. This makes the run values of special abilities a bit more of an approximation than normal abilities, but it did save me some typing
and make the sheet less cluttered!

# Observations

While Hot Button Baseball is an interesting design and makes an attempt to simulate 2004 player performances, I did find some very notable discrepancies when disseminating the date:

First: elite relief pitchers are extremely strong in this game since no stamina system is baked into the system. This is more of a feature than a bug to simplify game flow,
but it does have some odd effects like Eric Gagne being basically being superior to Randy Johnson.

Second: while the "Hot Ratings" featured on the cards do a reasonable job estimating player performance, the alorithm really dropped the ball on certain ones. Certain players
rated in the 60's like J.T. Snow and Ken Griffey Jr. are actually way ahead of the curve, while Ken Percival stands out as particularly mediocre despite a score of 90. It's
unknown if this is a flaw in the algorithm or something that kids were supposed to figure out for themselves with experience.

Third: the "Power Surge" ability is absurd in this game and enables players with a high "Power Surge" success rate% to considerably overperform. Key culprits of this phenomenon
are Hot Button MVP candiate Lance Berkman as well as players overlooked via "Hot Rating" like Sammy Sosa and Ken Griffey Jr.. It is also worth noting that the top 12 players
in this game that overperform compared to their 2004 MLB stats are all "Power Surge" users.

Finally: While some players' outcomes do a good job reflecting their 2004 stats, many are not even when special abilities are not taken into account. Many solid 2004 MLB pitchers
like Kerry Wood just perform terribly in this game no matter how many batters they face, while middling batters like Luis Castillo perform far below replacement level.

# Conclusion

Hot Button Baseball is a game that looks simple on the surface but has a lot of statistical depth behind it. Its gameplay makes it a little bit dubious as a simulation of the 2004 
MLB season, but its quirks help make it unique. It may be mostly forgotten, but it should also be remembered as one of only a few attempts at a Baseball CCG/collectible card game.
With that in mind, its whole existence truly is a bit of a contradiction, but I believe that just made it all the more interesting to examine. 








