---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
 

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction


Welcome to SuredBits' API documentation. This API allows you to query sports data, including teams, players, games, scores, and statistics.

Currently, our API supports NFL and NBA data.

## Format 

Requests are structured as follows:

http://api.suredbits.com/sport/version/searchParameter/subParameters## 

## Weekly Update 

The NFL API is updated weekly on Tuesdays at 1800 UTC to reflect week-to-week changes.

## Example

An example request to find Tom Brady of the New England Patriots:

> <code>http://api.suredbits.com/nfl/v0/players/brady/tom</code>;

```json
[
  {
    "weight": 225,
    "profileId": 2504211,
    "gsisName": "T.Brady",
    "uniformNumber": 12,
    "fullName": "Tom Brady",
    "height": 76,
    "lastName": "Brady",
    "firstName": "Tom",
    "birthDate": "8/3/1977",
    "profileUrl": "http://www.nfl.com/player/tombrady/2504211/profile",
    "status": "Active",
    "team": "NE",
    "playerId": "00-0019596",
    "position": "QB",
    "yearsPro": 17,
    "college": "Michigan"
  }
]
```

## Mailing List

We will publish <a href="https://medium.com/@SuredBits">blog posts</a> and <a href="https://twitter.com/SuredBits">tweet</a> when we release updates to the API, but you can also join our mailing list to be notified directly of any updates!

<form action="//suredbits.us12.list-manage.com/subscribe/post?u=6d2301935be3bfea5b7f29e4c&amp;id=16dc8b6ffb" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate="novalidate">
     <div id="mc_embed_signup_scroll">
    <h2>Join our mailing list to be the first to know our API is updated!</h2>
 <div class="indicates-required"><span class="asterisk"><em></em></span></div><em>
 </em><div class="mc-field-group"><em>
    <label for="mce-EMAIL">Email Address  <span class="asterisk"></span></label></em>
 
    <input type="email" value="" name="EMAIL" class="required email" id="mce-EMAIL" aria-required="true">
 </div>
    <div id="mce-responses" class="clear">
        <div class="response" id="mce-error-response" style="display:none"></div>
        <div class="response" id="mce-success-response" style="display:none"></div>
    </div>    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
     <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_6d2301935be3bfea5b7f29e4c_16dc8b6ffb" tabindex="-1" value=""></div>
     <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
     </div>
 </form>

<script type="text/javascript" src="//s3.amazonaws.com/downloads.mailchimp.com/js/mc-validate.js"></script>

# NFL

## Current Info
Return the current status of the NFL season.

Includes the current week, season type (Preseaspn, Regular, Postseason), and the last time the API was updated.

<table class="docutils">
                            <thead>
                            <tr>
                                <th>Resource</th>
                                <th>Example</th>
                            </tr>
                            </thead>
                            <tbody>
                            <tr>
                                <td>/info/</td>
                                <td>
                                    <a rel="noopener noreferrer" target="_blank" href="http://api.suredbits.com/nfl/v0/info/">
                                        http://api.suredbits.com/nfl/v0/info/
                                    </a>
                                </td>
                            </tr>
                            </tbody>
                        </table>
```json
{
  "seasonYear": 2017,
  "lastRosterDownload": "20180603T151844.638Z",
  "week": "NflWeek17",
  "version": "8",
  "seasonType": "Regular"
}
```

## Games
> Sample Data for Games 

```json
[{
  "gsisId": "2017123115",
  "seasonYear": 2017,
  "startTime": "20171231T212500.000Z",
  "timeInserted": "20170803T145501.334Z",
  "dayOfWeek": "Sunday",
  "gameKey": "57489",
  "finished": true,
  "homeTeam": {
    "scoreQ3": 7,
    "turnovers": 1,
    "scoreQ2": 0,
    "score": 24,
    "team": "SEA",
    "scoreQ1": 7,
    "scoreQ4": 10
  },
  "timeUpdate": "20180603T004736.984Z",
  "awayTeam": {
    "scoreQ3": 3,
    "turnovers": 0,
    "scoreQ2": 10,
    "score": 26,
    "team": "ARI",
    "scoreQ1": 10,
    "scoreQ4": 3
  },
```

Search NFL games by team, year, and/or week.

<a href="http://api.suredbits.com/nfl/v0/games">http://api.suredbits.com/nfl/v0/games</a>

### Keywords
Keywords  | Type  | Description
--------- | ----- | -----------
<span style="color:red"> *team* </span>	  | String | The Team ID <a href="../team/#team-id-table">(Refer to this table of teams and their teamIDs.)</a>
<span style="color:red"> *year*	</span> | Integer | Year of Play
<span style="color:red"> *rank* </span>     | Integer | Week of play (ex. '6' for Week 6)

Usage   | Description  |   Example
---------- | ------------ |  --------- 
/games	| All games for current week | 	<a href="http://api.suredbits.com/nfl/v0/games">http://api.suredbits.com/nfl/v0/games</a>
/games/team |	All games for a given team for the current week. | <a href="http://api.suredbits.com/nfl/v0/games/min">http://api.suredbits.com/nfl/v0/games/min</a>
/games/team/year/ | All games for a given team in a given year. (Regular season only) | <a href="http://api.suredbits.com/nfl/v0/games/min/2015">http://api.suredbits.com/nfl/v0/games/min/2015</a>
/games/team/year/week | A single game a given team played in a given year in a given week. | <a href="http://api.suredbits.com/nfl/v0/games/min/2014/15">http://api.suredbits.com/nfl/v0/games/min/2014/15</a>
/games/year | All games played for a given year. | <a href="http://api.suredbits.com/nfl/v0/games/2016">http://api.suredbits.com/nfl/v0/games/2016</a?
/games/year/week | All games played for a given week in a given year. | <a href="http://api.suredbits.com/nfl/v0/games/2016/1">http://api.suredbits.com/nfl/v0/games/2016/1</a>


## Players
> Example: Tom Brady

```json

[{
  "weight": 225,
  "profileId": 2504211,
  "gsisName": "T.Brady",
  "uniformNumber": 12,
  "fullName": "Tom Brady",
  "height": 76,
  "lastName": "Brady",
  "firstName": "Tom",
  "birthDate": "8/3/1977",
  "profileUrl": "http://www.nfl.com/player/tombrady/2504211/profile",
  "status": "Active",
  "team": "NE",
  "playerId": "00-0019596",
  "position": "QB",
  "yearsPro": 19,
  "college": "Michigan"
}]
```

Search NFL players by last or full name.

<a href="http://api.suredbits.com/nfl/v0/players/">http://api.suredbits.com/nfl/v0/players/</a>

Names must be an exact match, including periods or apostrophes, but capitalization isn't required.

For example, search by last name only, "brady" will return Tom Brady, but "brad" will not.

<aside class="warning"> Searching by full name, "green/a.j." will return "A.J. Green", but "aj" will not. The periods are imperative.</aside>



Usage | Description | Example 
-------- | ----------- | -------
/players/lastName | Search players by last name | <a href="http://api.suredbits.com/nfl/v0/players/brady">http://api.suredbits.com/nfl/v0/players/brady</a>
/players/lastName/firstName | Search players by last and first name | <a href="http://api.suredbits.com/nfl/v0/players/brady/tom">http://api.suredbits.com/nfl/v0/players/brady/tom</a>


## Team
> Sample Roster Data

```json
[{
  "weight": 218,
  "profileId": 2559252,
  "gsisName": "",
  "uniformNumber": 1,
  "fullName": "Kyle Sloter",
  "height": 76,
  "lastName": "Sloter",
  "firstName": "Kyle",
  "birthDate": "2/7/1994",
  "profileUrl": "http://www.nfl.com/player/kylesloter/2559252/profile",
  "status": "Active",
  "team": "MIN",
  "playerId": "00-0033672",
  "position": "QB",
  "yearsPro": 2,
  "college": "Northern Colorado"
}, {
  "weight": 197,
  "profileId": 2505552,
  "gsisName": "T.Newman",
  "uniformNumber": 23,
  "fullName": "Terence Newman",
  "height": 70,
  "lastName": "Newman",
  "firstName": "Terence",
  "birthDate": "9/4/1978",
  "profileUrl": "http://www.nfl.com/player/terencenewman/2505552/profile",
  "status": "Active",
  "team": "MIN",
  "playerId": "00-0022045",
  "position": "DB",
  "yearsPro": 16,
  "college": "Kansas State"
},
```

Search NFL team information by team ID.

<a href="http://api.suredbits.com/nfl/v0/team/">http://api.suredbits.com/nfl/v0/team/</a>

Usage | Description | Example 
-------- | ----------- | -------
/team/teamID/roster | Find a team's current roster | <a href="http://api.suredbits.com/nfl/v0/team/min/roster">http://api.suredbits.com/nfl/v0/team/min/roster</a>
/team/teamID/schedule | Find a team's schedule for the current season | <a href="http://api.suredbits.com/nfl/v0/team/min/schedule">http://api.suredbits.com/nfl/v0/team/min/schedule</a>


### Team ID Table
TeamID	| City & Name | TeamID | City & Name
-------- | ----------- | ------ | ---------
ARI	| Arizona Cardinals	| LA   | Los Angeles Rams
ATL	| Atlanta Falcons	| MIA  | Miami Dolphins
BAL	| Baltimore Ravens	| MIN | Minnesota Vikings
BUF	| Buffalo Bills	NE	| NE  | New England Patriots
CAR	| Carolina Panthers	| NO | New Orleans Saints
CHI	| Chicago Bears	NYG	| NYG | New York Giants
CIN	| Cincinnati Bengals	| NYJ	| New York Jets
CLE	| Cleveland Browns	| OAK	| Oakland Raiders
DAL	| Dallas Cowboys	| PHI	| Philadelphia Eagles
DEN	| Denver Broncos	| PIT	| Pittsburgh Steelers
DET	| Detroit Lions	SD	| SD   | San Diego Chargers
GB	| Green Bay Packers	| SEA	| Seattle Seahawks
HOU	| Houston Texans	| SF	| San Francisco 49ers
IND	| Indianpolis Colts	| TB	| Tampa Bay Buccaneers
JAC	| Jacksonville Jaguars	| TEN	| Tennessee Titans
KC	| Kansas City Chiefs	| WAS	| Washington Redskins


## Stats 
Search NFL player stats in a given game for a given player.

Omitting a footballStat will return all statistics.

<a href="http://api.suredbits.com/nfl/v0/stats/footballStat/gameID/playerID">http://api.suredbits.com/nfl/v0/stats/footballStat/gameID/playerID</a>

<a href="http://api.suredbits.com/nfl/v0/stats/footballStat/lastName/firstName/year/week">http://api.suredbits.com/nfl/v0/stats/footballStat/lastName/firstName/year/week</a>

You can find a <a href="../players/">player's playerID</a> and a <a href="../games/">game's gameID</a> using this API.

Optional - specify a seasonType (for season stats and game by name):

- "reg" = Regular season

- "post" = Postseason

- "pre" = Preseason

<a href="http://api.suredbits.com/nfl/v0/stats/footballStat/lastName/firstName/year/week/seasonType">http://api.suredbits.com/nfl/v0/stats/footballStat/lastName/firstName/year/week/seasonType</a>

<aside class="notice"> SeasonType will always default to Regular season unless a different seasonType is specified.</aside>


### Keywords
Keywords | Type	| Description
-------- | ---- | ------------
<span style="color:red"> *passing* </span>	| String | Searches passing statistics.
<span style="color:red"> *rushing* </span>	| String | Searches rushing statistics.
<span style="color:red"> *receiving* </span> | String | Searches receiving statistics.
<span style="color:red"> *defensive* </span> | String | Searches defensive statistics.

### Game - By ID
Find a player's single-game statistics with a given gameID and playerID.

Can specify a statType, or leave blank, to return all statistics.


## Passing Stats by Player
> Passing Stats by Player

```json
{
  "sack": 2,
  "cmp": 21,
  "passingTwoPointAttemptMade": 0,
  "cmpAirYds": 185,
  "passingTwoPointAttempt": 0,
  "passingInt": 0,
  "passingTds": 1,
  "att": 31,
  "sackYds": -17,
  "inCmpAirYds": 133,
  "passingTwoPointAttemptMissed": 0,
  "inCmp": 10,
  "passingYds": 254
}
```
<a href="http://api.suredbits.com/nfl/v0/stats/passing/2016101604/00-0027973">http://api.suredbits.com/nfl/v0/stats/passing/2016101604/00-0027973</a>


## Rushing Stats by Player 
```json
{
  "rushingTwoPointAttemptMissed": 0,
  "fumblesLost": 0,
  "rushingTwoPointAttemptMade": 0,
  "rushingYds": 111,
  "tds": 3,
  "rushingTwoPointAttempt": 0,
  "loss": 0,
  "attempt": 22,
  "lossYds": 0
}
```
<a href="http://api.suredbits.com/nfl/v0/stats/rushing/2016101700/00-0032187">http://api.suredbits.com/nfl/v0/stats/rushing/2016101700/00-0032187</a>

## Receiving Stats by Player	
```json
{
  "receivingTwoPointAttemptMade": 0,
  "fumblesLost": 1,
  "receivingTwoPointAttemptMissed": 0,
  "yacYds": 128,
  "tds": 2,
  "rec": 8,
  "target": 10,
  "receivingYds": 222,
  "receivingTwoPointAttempt": 0
}
```
<a href="http://api.suredbits.com/nfl/v0/stats/receiving/2016101606/00-0031235">http://api.suredbits.com/nfl/v0/stats/receiving/2016101606/00-0031235</a>


## Defensive Stats by Player 
```json
{
  "tackleLoss": 0,
  "recoveredFumbles": 0,
  "fgBlk": 0,
  "assistedTackles": 2,
  "recoveredFumbleYds": 0,
  "tackleLossYards": 0,
  "qbHit": 0,
  "miscTds": 0,
  "defenseInt": 0,
  "miscYds": 0,
  "extraPointBlock": 0,
  "defenseSack": 0,
  "intTds": 0,
  "punkBlk": 0,
  "recoveredFumbleTD": 0,
  "tacklePrimary": 0,
  "defenseSackYds": 0,
  "tackle": 2,
  "safety": 0,
  "passDef": 0,
  "intYds": 0,
  "forcedFumbles": 0
}
```

<a href="http://api.suredbits.com/nfl/v0/stats/defensive/2016102400/00-0029620">http://api.suredbits.com/nfl/v0/stats/defensive/2016102400/00-0029620</a>

## Game - By Name

```json
[{
  "sack": 0,
  "cmp": 19,
  "passingTwoPointAttemptMade": 0,
  "cmpAirYds": 121,
  "passingTwoPointAttempt": 0,
  "passingInt": 0,
  "passingTds": 2,
  "att": 26,
  "sackYds": 0,
  "inCmpAirYds": 50,
  "passingTwoPointAttemptMissed": 0,
  "inCmp": 7,
  "passingYds": 222
}]
```

Find a player's single-game statistics with a player's name and year/week of the game.

Can specify a statType, or leave blank, to return all statistics.


## Season - By ID
```json
{
  "defense": {
    "tackleLoss": 0,
    "recoveredFumbles": 0,
    "fgBlk": 0,
    "assistedTackles": 0,
    "recoveredFumbleYds": 0,
    "tackleLossYards": 0,
    "qbHit": 0,
    "miscTds": 0,
    "defenseInt": 0,
    "miscYds": 0,
    "extraPointBlock": 0,
    "defenseSack": 0,
    "intTds": 0,
    "punkBlk": 0,
    "recoveredFumbleTD": 0,
    "tacklePrimary": 0,
    "defenseSackYds": 0,
    "tackle": 1,
    "safety": 0,
    "passDef": 0,
    "intYds": 0,
    "forcedFumbles": 0
  },
  "rushing": {
    "rushingTwoPointAttemptMissed": 0,
    "fumblesLost": 0,
    "rushingTwoPointAttemptMade": 0,
    "rushingYds": 15,
    "tds": 0,
    "rushingTwoPointAttempt": 0,
    "loss": 0,
    "attempt": 1,
    "lossYds": 0
  },
  "fumbles": {
    "fumblesForced": 0,
    "fumblesLost": 0,
    "fumbleRecoveredYds": 0,
    "fumblesTotal": 0,
    "fumblesRecovered": 0,
    "fumblesOutOfBounds": 0,
    "fumbleRecoveredTds": 0,
    "fumblesNotForced": 0
  },
  "kickReturn": {
    "fairCatch": 0,
    "kickRetYds": 0,
    "kickRetTds": 0,
    "kickRetRet": 0,
    "kickRetTouchBack": 0,
    "kickRetOutOfBounds": 0
  },
  "passing": {
    "sack": 0,
    "cmp": 0,
    "passingTwoPointAttemptMade": 0,
    "cmpAirYds": 0,
    "passingTwoPointAttempt": 0,
    "passingInt": 0,
    "passingTds": 0,
    "att": 0,
    "sackYds": 0,
    "inCmpAirYds": 0,
    "passingTwoPointAttemptMissed": 0,
    "inCmp": 0,
    "passingYds": 0
  },
  "receiving": {
    "receivingTwoPointAttemptMade": 0,
    "fumblesLost": 0,
    "receivingTwoPointAttemptMissed": 0,
    "yacYds": 486,
    "tds": 3,
    "rec": 88,
    "target": 148,
    "receivingYds": 1444,
    "receivingTwoPointAttempt": 0
  },
  "playerId": "00-0027944",
  "kicking": {
    "fgb": 0,
    "fgmYds": 0,
    "kickingYds": 0,
    "allYds": 0,
    "kickingInside20": 0,
    "fgm": 0,
    "recovery": 0,
    "xpb": 0,
    "recoveryTds": 0,
    "kickingTouchback": 0,
    "xpMade": 0,
    "fgMissed": 0,
    "xpa": 0,
    "fga": 0,
    "fgMissedYds": 0,
    "xpMissed": 0,
    "kickingTotal": 0,
    "downed": 0
  },
  "punting": {
    "puntReturnFair": 0,
    "puntingYds": 0,
    "puntingTotal": 0,
    "puntReturnTouchback": 0,
    "puntingInside20": 0,
    "puntReturnTds": 0,
    "puntReturnDowned": 0,
    "blk": 0,
    "puntReturnTotal": 0,
    "puntReturnOutOfBounds": 0,
    "puntingTouchback": 0,
    "puntReturnYards": 0
  }
}
```

Find a player's season statistics with a given gameID and playerID.

Returns all statistics, regardless of position.

Can specify a year (2009-2015), or leave blank for the current season (2016).

## Season - By Name 
```json
[{
  "defense": {
    "tackleLoss": 0,
    "recoveredFumbles": 0,
    "fgBlk": 0,
    "assistedTackles": 0,
    "recoveredFumbleYds": 0,
    "tackleLossYards": 0,
    "qbHit": 0,
    "miscTds": 0,
    "defenseInt": 0,
    "miscYds": 0,
    "extraPointBlock": 0,
    "defenseSack": 0,
    "intTds": 0,
    "punkBlk": 0,
    "recoveredFumbleTD": 0,
    "tacklePrimary": 0,
    "defenseSackYds": 0,
    "tackle": 1,
    "safety": 0,
    "passDef": 0,
    "intYds": 0,
    "forcedFumbles": 0
  },
  "rushing": {
    "rushingTwoPointAttemptMissed": 0,
    "fumblesLost": 0,
    "rushingTwoPointAttemptMade": 0,
    "rushingYds": 15,
    "tds": 0,
    "rushingTwoPointAttempt": 0,
    "loss": 0,
    "attempt": 1,
    "lossYds": 0
  },
  "fumbles": {
    "fumblesForced": 0,
    "fumblesLost": 0,
    "fumbleRecoveredYds": 0,
    "fumblesTotal": 0,
    "fumblesRecovered": 0,
    "fumblesOutOfBounds": 0,
    "fumbleRecoveredTds": 0,
    "fumblesNotForced": 0
  },
  "kickReturn": {
    "fairCatch": 0,
    "kickRetYds": 0,
    "kickRetTds": 0,
    "kickRetRet": 0,
    "kickRetTouchBack": 0,
    "kickRetOutOfBounds": 0
  },
  "passing": {
    "sack": 0,
    "cmp": 0,
    "passingTwoPointAttemptMade": 0,
    "cmpAirYds": 0,
    "passingTwoPointAttempt": 0,
    "passingInt": 0,
    "passingTds": 0,
    "att": 0,
    "sackYds": 0,
    "inCmpAirYds": 0,
    "passingTwoPointAttemptMissed": 0,
    "inCmp": 0,
    "passingYds": 0
  },
  "receiving": {
    "receivingTwoPointAttemptMade": 0,
    "fumblesLost": 0,
    "receivingTwoPointAttemptMissed": 0,
    "yacYds": 486,
    "tds": 3,
    "rec": 88,
    "target": 148,
    "receivingYds": 1444,
    "receivingTwoPointAttempt": 0
  },
  "playerId": "00-0027944",
  "kicking": {
    "fgb": 0,
    "fgmYds": 0,
    "kickingYds": 0,
    "allYds": 0,
    "kickingInside20": 0,
    "fgm": 0,
    "recovery": 0,
    "xpb": 0,
    "recoveryTds": 0,
    "kickingTouchback": 0,
    "xpMade": 0,
    "fgMissed": 0,
    "xpa": 0,
    "fga": 0,
    "fgMissedYds": 0,
    "xpMissed": 0,
    "kickingTotal": 0,
    "downed": 0
  },
  "punting": {
    "puntReturnFair": 0,
    "puntingYds": 0,
    "puntingTotal": 0,
    "puntReturnTouchback": 0,
    "puntingInside20": 0,
    "puntReturnTds": 0,
    "puntReturnDowned": 0,
    "blk": 0,
    "puntReturnTotal": 0,
    "puntReturnOutOfBounds": 0,
    "puntingTouchback": 0,
    "puntReturnYards": 0
  }
}]
```

Find a player's regular-season statistics by their name.

Returns all statistics, regardless of position.

Can specify a year (2009-2015), or leave blank for the current season (2016).

# NBA
## Games
Search NBA games by team, year, month or day.

Currently only 2015-16 and 2016-17 games are available.

http://api.suredbits.com/nba/v0/games

## Keywords
Keywords | Type | Description
-------- | ---- | ----------
<span style="color:red"> *team* </span> | string | The Team ID 
<span style="color:red"> *year* </span> | Integer | Year of play


## Usage

Resource | Description | Example 
--------- | ---------- | ------
/games | All regular-season games for the current day. | <a href="http://api.suredbits.com/nba/v0/games">http://api.suredbits.com/nba/v0/games</a>
/games/year | All regular-season games in the given year. The year provided is the year in which the season started. Ex. To search the 2015-16 season, provide 2015 as the year. | <a href="http://api.suredbits.com/nba/v0/games/2016">http://api.suredbits.com/nba/v0/games/2016</a>
/games/year/month | All games played in the month of a year. | <ahref="http://api.suredbits.com/nba/v0/games/2017/1">http://api.suredbits.com/nba/v0/games/2017/1</a>
/games/year/month/day | The games played on a specific date, given a year, month and day. | <a href="http://api.suredbits.com/nba/v0/games/2017/1/29">http://api.suredbits.com/nba/v0/games/2017/1/29</a>
/games/team | The game played for a given team today. Nothing returned if the team doesn't play today. | <a href="http://api.suredbits.com/nba/v0/games/phi">http://api.suredbits.com/nba/v0/games/phi</a>
/games/team/year/ | All games for a given team in a given year. The year provided is the year in which the season started. Ex. To search the 2015-16 season, provide 2015 as the year. | <a href="http://api.suredbits.com/nba/v0/games/phi/2015">http://api.suredbits.com/nba/v0/games/phi/2015</a>
/games/team/year/month | All games for a given team in a month in a year. | <a href="http://api.suredbits.com/nba/v0/games/phi/2017/1">http://api.suredbits.com/nba/v0/games/phi/2017/1</a>
/games/team/year/month/day | The game played by a team given a year, month and day. Returns nothing if the team didn't play that day. | <a href="http://api.suredbits.com/nba/v0/games/phi/2017/1/29">http://api.suredbits.com/nba/v0/games/phi/2017/1/29</a>
/games/team/seasonphase | The games for the given team during the given season phase this year.	| <a href="http://api.suredbits.com/nba/v0/games/sas/post">http://api.suredbits.com/nba/v0/games/sas/post</a>
/games/team/seasonphase/year | The games for the given team during the given season phase and year. | <a href="http://api.suredbits.com/nba/v0/games/sas/post/2016">http://api.suredbits.com/nba/v0/games/sas/post/2016</a>
/games/seasonphase  | The games for the given season phase for this year. | <a href="http://api.suredbits.com/nba/v0/games/post">http://api.suredbits.com/nba/v0/games/post</a>
/games/seasonphase/year | The games for the given season phase for the given year. | <a href="http://api.suredbits.com/nba/v0/games/post/2016">http://api.suredbits.com/nba/v0/games/post/2016</a>




## Team ID Table

Team ID | City & Name 
------- | ----------
ATL |	Atlanta Hawks	
BKN |	Brooklyn Nets	
BOS |	Boston Celtics	
CHA |	Charlotte Hornets	
CHI |	Chicago Bulls	
CLE |	Cleveland Cavaliers	
DAL |	Dallas Mavericks	
DEN |	Denver Broncos	
DET |	Detroit Pistons	
GSW |	Golden State Warriors	
HOU |	Houston Rockets	
IND |	Indiana Pacers	
LAC |	Los Angeles Clippers	
LAL |	Los Angeles Lakers	
MEM |	Memphis Grizzlies	
MIA |	Miami Heat
MIL |	Milwaukee Bucks
MIN |	Minnesota Timberwolves
NOP |	New Orleans Pelicans
NYK |	New York Knicks
OKC |	Oklahoma City Thunder
ORL |	Orlando Magic
PHI |	Philadelphia 76ers
PHX |	Phoenix Suns
POR |	Portland Trail Blazers
SAC |	Sacramento Kings
SAS |	San Antonio Spurs
TOR |	Toronto Raptors
UTA |	Utah Jazz
WAS |	Washington Wizards


## Players
Search NBA players by team.

http://api.suredbits.com/nba/v0/players

## Keywords 
Keywords | Type | Description
--------- | ---------- | ------
<span style="color:red"> *team* </span>	| string | The Team ID

## Usage 

Resource | Description | Example 
-------- | ---------- | ---------
/players | All current, rostered players in the NBA. | <a href="http://api.suredbits.com/nba/v0/players">http://api.suredbits.com/nba/v0/players</a>
/players/teamID	| All current players on a given NBA team. | <a href="http://api.suredbits.com/nba/v0/players/phi">http://api.suredbits.com/nba/v0/players/phi</a>
/players/lastName | Searches players by their last name. | <a href="http://api.suredbits.com/nba/v0/players/james">http://api.suredbits.com/nba/v0/players/james</a>
/players/lastName | Searches players by their first and last name. | <a href="http://api.suredbits.com/nba/v0/players/james/lebron">http://api.suredbits.com/nba/v0/players/james/lebron</a>


## Stats

## Stats 
Search NBA player game and season statistics by a player's ID or name.

Currently, it's only possible to search active player statistics for the 2015-16 and 2016-17 seasons.

http://api.suredbits.com/nba/v0/stats

## Usage - Stats By Id
Resource | Description  | Example 
--------- | ----------  |-------
/stats/playerID/gameID | Search for a player's game stats given his playerID and a gameID. | Ex: LeBron James (ID 2544) in Dec 7 game vs. NYK (ID 21600327) <a href="http://api.suredbits.com/nba/v0/stats/2544/21600327">http://api.suredbits.com/nba/v0/stats/2544/21600327</a>
/stats/playerID/year | Search for a player's stats in a given year by his playerID. | Ex: LeBron James (ID 2544) 2016 stats <a href="http://api.suredbits.com/nba/v0/stats/2544/2016">http://api.suredbits.com/nba/v0/stats/2544/2016</a>



## Usage - Stats by Name 
Resource | Description | Example
-------- | ----------- | -------
/stats/lastName/firstName | Search for a player's current season statistics given his name. | LeBron James stats for current season (2016-17) <a href="http://api.suredbits.com/nba/v0/stats/james/lebron">http://api.suredbits.com/nba/v0/stats/james/lebron</a>
/stats/lastName/firstName/year | Search for a player's statistics given his name and a year. If no year is given, the current season stats are returned. | LeBron James stats for 2015-16 season. <a href="http://api.suredbits.com/nba/v0/stats/james/lebron/2015">http://api.suredbits.com/nba/v0/stats/james/lebron/2015</a>
/stats/lastName/firstName/seasonphase | Search for a player's statistics during the given season phase of this year | Lebron Jame's stats for postseason this year. <a href="http://api.suredbits.com/nba/v0/stats/james/lebron/post">http://api.suredbits.com/nba/v0/stats/james/lebron/post</a>
/stats/lastName/firstName/seasonphase/year | Search for a player's statistics during the given season phase of 2017 | Lebron Jame's stats for postseason this year. <a href="http://api.suredbits.com/nba/v0/stats/james/lebron/post/2017">http://api.suredbits.com/nba/v0/stats/james/lebron/post/2017</a>
/stats/lastName/firstName/year/month | Search for a player's statistics in a given calendar year and month. | Joel Embiid for Rookie of the Month January 2017. <a href="http://api.suredbits.com/nba/v0/stats/embiid/joel/2017/1">http://api.suredbits.com/nba/v0/stats/embiid/joel/2017/1</a>





Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

