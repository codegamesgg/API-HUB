Replenishing mobile games via the CodeGames occurs as follows:

1. API Integration: 
To start working with the CodeGames API, your company must go through the registration and verification process. This includes verifying legitimacy and compliance requirements. 
Upon successful verification, you'll receive access to API keys, enabling you to utilize various platform functions.

2. API Requests: 
The API supports various types of requests for handling replenishments, including retrieving a list of available games, verifying user identifiers, obtaining the reseller's balance, executing top-ups, and tracking order statuses. 
Python code examples demonstrate how to use these requests:
Getting a list of available games: Perform a GET request to /codegames_games_available to retrieve a list of games that can be replenished through your account.
Replenishing a game account: A POST request to /codegames_merchant_topup_api allows you to submit data for replenishment, including the user identifier, game, and desired amount.

3. Checking order status: 

A POST request to /track_order to check the status of a completed order.
Handling responses: The API returns JSON responses, which may indicate successful execution of the request (e.g., code 200) or various errors (e.g., code 403 for invalid requests or code 400 for data errors).
Access to the CodeGames Top-up API is granted only after your company has been successfully verified and compliance requirements have been confirmed. 
This ensures the security and reliability of interaction between your systems and our API."

Available mobile games for top-up by login (By UID):

Game Code                | Game Name                          | Geo Availability
-------------------------|------------------------------------|-----------------
pubgm                    | Top up PUBG Mobile                        | Global
freefire_sgmy            | Top up Freefire SGMY                      | SGMY
freefire_global          | Top up Freefire Global                    | Global
genshin                  | Top up Genshin Impact                     | Global
tof                      | Top up Tower of Fantasy                   | Global
mlbb                     | Top up Mobile Legends                     | Global
mlbb_exclusive           | Top up Mobile Legends Exclusive           | Global
mlbb_indo                | Top up Mobile Legends                     | Indonesia
mlbb_exclusive_global    | Top up Mobile Legends Exclusive Global    | All except Indonesian accounts
mlbb_global              | Top up Mobile Legends Global              | Global
ragnarok_origin          | Top up Ragnarok Origin                    | Global
bigo                     | Top up Bigo Live Diamonds                 | Global
identityv                | Top up Identity V                         | Global
brawlstars               | Top up Brawl Stars                        | Global
clashofclans             | Top up Clash of Clans                     | Global
clashroyale              | Top up Clash Royale                       | Global
hayday                   | Top up Hay Day                            | Global
nikke                    | Top up GOV: Nikke                         | Global
maplestorym              | Top up MapleStory M                       | Global
harry_potter_magic_awakened | Top up Harry Potter: Magic Awaken      | Global
garena_undawn            | Top up Garena Undawn                      | Global
honkai_star_rail         | Top up Honkai Star Rail                   | Global
maplestoryr              | Top up MapleStory R: Evolution            | Global
undawn_global            | Top up Undawn Global                      | Global
arena_breakout           | Arena Breakout                     | Global
super_sus                | Top up Super Sus                          | Global
mlbb_ru                  | Top up Mobile Legends Russia              | Russia
mlbb_br                  | Top up Mobile Legends Brazil              | Brazil
mlbb_special             | Top up Mobile Legends Special             | Global
likee                    | Top up Likee                              | Global
state_of_survival        | Top up State of Survival                  | Global
zepeto                    | Top up Zepeto                             | Global
black_clover_m_asia      | Top up Black Clover M Asia                | Asia
pgr                      | Top up Punishing Gray Raven               | Global
farlight84               | Top up Farlight 84                        | Global
dbdl                     | Top up Dead by Daylight Mobile            | Global
stumble_guys             | Top up Stumble Guys                       | Global
bloodstrike              | Top up Blood Strike                       | Global
whiteout_survival        | Top up Whiteout Survival                  | Global
wor                      | Top up Watcher of Realms                  | Global
dragonheir               | Top up Dragonheir: Silent Gods            | Global
hatsune_miku             | Top up Hatsune Miku                       | Global
metal_slug               | Top up Metal Slug Awakening               | Global
sausage_man              | Top up Sausage Man                        | Global
t3_arena                 | Top up T3 Arena                           | Global
valorant_my              | Top up Valorant Malaysia                  | Malaysia
growtopia                | Top up Growtopia                          | Global
echocalypse              | Top up Youzu Echocalypse                  | Global
lifeafter                | Top up LifeAfter                          | Global
eve_echoes               | Top up Eve Echoes                         | Global
onepunchworld            | Top up One Punch Man World                | Global
teamfight_tactics        | Top up Teamfight Tactics                  | Global
legends_of_runeterra     | Top up Legends of Runeterra               | Global
dragon_raja              | Top up Dragon Raja                        | Global
hok                      | Top up Honor of Kings                     | Global
blockman_go              | Top up Blockman Go                        | Global
lords_mobile             | Top up Lords Mobile                       | Global
eggy_party               | Top up Eggy Party                         | Global
dmc                      | Top up Devil May Cry: Peak of Combat      | Global

