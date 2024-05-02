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
pubgm                    | PUBG Mobile                        | Global
freefire_sgmy            | Freefire SGMY                      | SGMY
freefire_global          | Freefire Global                    | Global
genshin                  | Genshin Impact                     | Global
tof                      | Tower of Fantasy                   | Global
mlbb                     | Mobile Legends                     | Global
mlbb_exclusive           | Mobile Legends Exclusive           | Global
mlbb_indo                | Mobile Legends                     | Indonesia
mlbb_exclusive_global    | Mobile Legends Exclusive Global    | All except Indonesian accounts
mlbb_global              | Mobile Legends Global              | Global
ragnarok_origin          | Ragnarok Origin                    | Global
bigo                     | Bigo Live Diamonds                 | Global
identityv                | Identity V                         | Global
brawlstars               | Brawl Stars                        | Global
clashofclans             | Clash of Clans                     | Global
clashroyale              | Clash Royale                       | Global
hayday                   | Hay Day                            | Global
nikke                    | GOV: Nikke                         | Global
maplestorym              | MapleStory M                       | Global
harry_potter_magic_awakened | Harry Potter: Magic Awaken      | Global
garena_undawn            | Garena Undawn                      | Global
honkai_star_rail         | Honkai Star Rail                   | Global
maplestoryr              | MapleStory R: Evolution            | Global
undawn_global            | Undawn Global                      | Global
arena_breakout           | Arena Breakout                     | Global
super_sus                | Super Sus                          | Global
mlbb_ru                  | Mobile Legends Russia              | Russia
mlbb_br                  | Mobile Legends Brazil              | Brazil
mlbb_special             | Mobile Legends Special             | Global
likee                    | Likee                              | Global
state_of_survival        | State of Survival                  | Global
zepeto                    | Zepeto                             | Global
black_clover_m_asia      | Black Clover M Asia                | Asia
pgr                      | Punishing Gray Raven               | Global
farlight84               | Farlight 84                        | Global
dbdl                     | Dead by Daylight Mobile            | Global
stumble_guys             | Stumble Guys                       | Global
bloodstrike              | Blood Strike                       | Global
whiteout_survival        | Whiteout Survival                  | Global
wor                      | Watcher of Realms                  | Global
dragonheir               | Dragonheir: Silent Gods            | Global
hatsune_miku             | Hatsune Miku                       | Global
metal_slug               | Metal Slug Awakening               | Global
sausage_man              | Sausage Man                        | Global
t3_arena                 | T3 Arena                           | Global
valorant_my              | Valorant Malaysia                  | Malaysia
growtopia                | Growtopia                          | Global
echocalypse              | Youzu Echocalypse                  | Global
lifeafter                | LifeAfter                          | Global
eve_echoes               | Eve Echoes                         | Global
onepunchworld            | One Punch Man World                | Global
teamfight_tactics        | Teamfight Tactics                  | Global
legends_of_runeterra     | Legends of Runeterra               | Global
dragon_raja              | Dragon Raja                        | Global
hok                      | Honor of Kings                     | Global
blockman_go              | Blockman Go                        | Global
lords_mobile             | Lords Mobile                       | Global
eggy_party               | Eggy Party                         | Global
dmc                      | Devil May Cry: Peak of Combat      | Global

