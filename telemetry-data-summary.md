Telemetry Data Summary
======================

The telemetry.json file contains an array of TelemetryData objects, each of which
has a different structure based on its type. You can find the type of a TelemetryData
object looking at its "type" field. Below are the descriptions of the various
TelemetryData types and the structure of their "dataObject" field.

RoundEvent
-----------------------------

``type="Structures.RoundEvent"``

Variable    	  | Type | Description                               
--------------- | ---- | ----------------------------------------- 
time            | int  | timestamp telling when the event happened 
matchID         | str  | ID of the match                           
externalMatchID | str  | empty string                              
userID          | str  | UID of the player                         
round           | int  | round in which the event happened         
character       | int  | ID of the Champion                        
type            | str  | type of the event                         
value           | int  |                                           
timeIntoRound   | int  | time from the beginning of the round      


UserRoundSpell
--------------------------------

``type="Structures.UserRoundSpell"``

Variable     | Type | Description
------------ | ---- | -----------------------------------------
time         | int  | timestamp telling when the event happened
accountId    | str  | UID of the player
matchID      | str  | ID of the match
round        | int  | round in which the event happened
character    | int  | ID of the Champion
typeId       | int  | ID of the type of event
sourceTypeId | int  |
scoreType    | str  | "ENERGY_RECEIVED","DAMAGE_RECEIVED",...
value        | int  |


DeathEvent
--------------------------------

``type="Structures.DeathEvent"``

Variable        | Type | Description
--------------- | ---- | -----------------------------------------
time            | int  | timestamp telling when the event happened
matchID         | str  | ID of the match
externalMatchID | str  | empty string
userID          | str  | UID of the player


MatchReservedUser
-----------------------------------

``type="Structures.MatchReservedUser"``

Variable            | Type | Description
------------------- | ---- | -------------------------------------------
time                | int  | timestamp telling when the event happened
accountId           | str  | UID of the player
matchID             | str  | ID of the match
serverType          | str  | Type of the match (eg. "QUICK3V3")
characterLevel      | int  | level of the Champion selected
teamId              | str  | ID of the team
totalTimePlayed     | int  | time the user has played the game for
characterTimePlayed | int  | time the user played with selected champion
character           | int  | ID of the Champion
team                | int  | team of the player in the match, 1 or 2
rankingType         | str  | "RANKED" or "UNRANKED"
mount               | int  | ID of the equipped mount
attachment          | int  | ID of the equipped weapon
outfit              | int  | ID of the equipped outfit
emote               | int  | ID of the equipped victory pose
legue               | int  | League of the player
division            | int  | Division of the player
divisionRating      | int  | rating points inside the division
seasonId            | int  | number of season of the match


QueueEvent
-------------------------------------------------------

``type="com.stunlock.service.matchmaking.avro.QueueEvent"``

Variable              | Type           | Description
--------------------- | -------------- | -----------------------------------------
time                  | int            | timestamp telling when the event happened
userId                | str            | UID of the player
teamId                | str            | ID of the team
sessionId             | str            | ID of the session
season                | int            | number of season of the match
eventType             | str            | "MATCH"
timeJoinedQueue       | str            | timestamp telling when ready was pressed
timeInQueue           | float          | time in queue
character             | int            | ID of the Champion
characterArchetype    | int            | 2 = melee, 4 = ranged, 8 = support
queueTypes            | str[]          | queue types (eg. "QUICK3V3UNRANKED")
limitMatchmakingRange | bool           | strict matchmaking
regionSamples         | RegionSample[] | ping in selected servers
preferredRegion       | str            | preferred region
rankingType           | str            | "RANKED" or "UNRANKED"
legue                 | int            | League of the player
division              | int            | Division of the player
divisionRating        | int            | rating points inside the division
teamSize              | int            | team size
teamMembers           | int[]          | team members*
placementGamesLeft    | int            | placement games left
matchID               | str            | ID of the match
matchRegion           | str            | match region
teamSide              | int            | team in the match, 1 or 2
autoMatchmaking       | bool           |


RegionSample
-----------------------------------

Variable  | Type | Description
--------- | ---- | -----------------------
region    | str  | "eu_west", "spain", ...
latencyMS | int  | latency (ping) in MS


TeamUpdateEvent
-------------------------------------------------------

``type="com.stunlock.battlerite.team.TeamUpdateEvent"``

Variable               | Type  | Description
---------------------- | ----- | -----------------------------------------
time                   | int   | timestamp telling when the event happened
season                 | int   | number of season of the match
teamId                 | str   | ID of the team
matchID                | str   | ID of the match
externalMatchID        | str   | empty string
userIDs                | str[] | IDs of the players
mode                   | str   | "RANKED" or "UNRANKED"
league                 | int   | current League of the player
prevLegue              | int   | previous League of the player
prevDivision           | int   | previous Division of the player
division               | int   | current Division of the player
prevDivisionRating     | int   | current rating points inside the division
divisionRating         | int   | previous rating points inside the division
prevWins               | int   | wining streak before the match
wins                   | int   | winning streak after the match
prevlosses             | int   | loosing streak before the match
losses                 | int   | loosing streak after the match
rankingChangeType      | str   |
prevPlacementGamesLeft | int   | placement games left berfore the match
placementGamesLeft     | int   | placement games left after the match
matchRegion            | str   | match region


ServerShutdown
--------------------------------

``type="Structures.ServerShutdown"``

Variable        | Type | Description
--------------- | ---- | -----------------------------------------
time            | int  | timestamp telling when the event happened
matchID         | str  | ID of the match
externalMatchID | str  | empty string
matchTime       | int  | duration of the match
reason          | str  | reason


RoundFinishedEvent
-------------------------------------

``type="Structures.RoundFinishedEvent"``

Variable        | Type          | Description
--------------- | ------------- | -----------------------------------------
time            | int           | timestamp telling when the event happened
matchID         | str           | ID of the match
externalMatchID | str           | empty string
round           | int           | number of round, starts from 0
roundLength     | int           | duration of the round
winningTeam     | int           | winning team
playerStats     | PlayerStats[] | player stats


MatchFinishedEvent
--------------------

``type="Structures.MatchFinishedEvent"``

Variable        | Type  | Description
--------------- | ----- | -----------------------------------------
time            | int   | timestamp telling when the event happened
teamOneScore    | int   | number of rounds won by team 1
teamTwoScore    | int   | number of rounds won by team 2
matchLength     | int   | length of the match
matchID         | str   | ID of the match
externalMatchID | str   | empty string
leavers         | int[] | IDs of the leavers*
region          | str   | region (eg. "eu_east")


MatchStart
-----------------------------

``type="Structures.MatchStart"``

Variable        | Type | Description
--------------- | ---- | -----------------------------------------
time            | int  | timestamp telling when the event happened
matchID         | str  | ID of the match
externalMatchID | str  | empty string
version         | str  | Patch the match is played in
type            | str  | "QUICK3V3", "QUICK2V2"
mapID           | str  | ID of the map
teamSize        | int  | team size
region          | str  | region (eg. "eu_east")
