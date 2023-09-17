# Bundesliga_players_analysis
This repo contains all the data analysis project files for the Bundesliga players 2023 dataset.

# Introduction
This README describes work done on the Bundesliga soccer player data set. Resources used include Python and associated packages Jupyter, matplotlib, Seaborn and scikit-learn. These packages all come as part of the Anaconda distribution of Python.
The analysis takes the form of a single Jupyter notebook of filename given above. To view this file, download it from this repository and start Jupyter notebook in the folder containing the file. Use the command Jupyter notebook on the command line.
Alternatively, view a static version of the notebook (by providing its GitHub url) using Jupyter Nbviewer.
The Bundesliga soccer player dataset is available on Kaggle. To gain access to the dataset, visit this link https://www.kaggle.com/datasets/oles04/bundesliga-soccer-player and download the dataset to your local machine. 
All images intended for inclusion in this README are located in the images subdirectory of this repository.

# Bundesliga soccer player dataset
The Bundesliga Players dataset provides a comprehensive collection of information on every player in the German Bundesliga football league. From renowned goalkeepers to talented defenders, this dataset offers an extensive range of player details including their names, full names, ages, heights, nationalities, places of birth, prices, maximum prices, positions, shirt numbers, preferred foot, current clubs, contract expiration dates, dates of joining the clubs, player agents, and outfitters. 
The goal of this project is analyze the dataset and extract information about the German Bundesliga first division.

# Descriptive Statistics
The dataset has a shape of (515, 17) meaning it contains 515 rows and 17 columns. Checking more information about the dataset, we can see more information about each column and their datatype.
![Shape](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/88be313b-2acb-49d9-b8e2-f4f6f1e470aa) ![Info](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/c51ad9de-193a-42e8-8c6c-cf9842e4a225)

 The dataset had a lot of missing data for both the categorical and numerical columns which I handled using different methods like removal of column or filling missing values with, mean, mode or median of the column.
I used seaborn’s heatmap to get a visual of all missing data in each column of our dataset and we can see that the full_name and outfitter columns have a lot of missing data.
 ![Heatmap_missn_values](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/8bfd48f6-2c9f-45b6-8995-06f1416b3161)
Pandas describe() can provide a quick summary of the numerical columns in the data set as outlined in the notebook. From this summary, we can say that,
1.	The Average age of players in the dataset is 25 years old.
2.	The average height of players in the dataset is 1.84 meters.
3.	The average price of players in the dataset is 8.48 million.
4.	The youngest and oldest players and 17 and 39 years of age respectively.
5.	The tallest and shortest players are 2 meters and 1.68 meters respectively.
6.	The most expensive and cheapest players are valued at 120 million and 25 thousand respectively.
![describ_dataset](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/268a5dc4-1996-45a9-aea3-cf4622538e30)


# Data Cleaning - Handling missing values
The full_name column is very similar to the name column. Its is just the name column without players middle names. Since we have the name column without missing values, we can drop the full_name column from our dataset.
To handle the missing values in the place_of_birth column, we fill the missing data with the mode of the most common place_of_birth in each nationality on our dataset.
PRICE AND MAX PRICE COLUMN - These columns have 5 missing values we need to fill. We will group the age column and fill the missing values with the average price and max price of players in same age group.
The foot column has 3 categories, left, right and both. The missing data will be determined by the most common foot used in every player position.
For the outfitter column, the missing data is replaced with “not available” as we are assuming the the players do not have kit sponsors.
The missing data for player_agent are replaced with “Himself”. We are assuming players without agents are representing themselves.

# Technologies used
•	Python
•	Jupyter, Pandas
•	Seaborn, Matplotlib

# Exploratory Analysis
The dataset contains the data of players who play both in the Bundesliga first division and other divisions. Our analysis will focus on the player data for the first division.
The dataset represents players from 28 unique teams in the Germany(first division and other division). We have 18 teams from the first division and 10 teams from other division
![Clubs_division](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/846fbed5-bfae-473d-9c5b-6c366afdd8da)

    # Findings
1.	Each club in the first division has an average of 27 players with FC Augsburg, FC Schalke 04 and TSG Hoffenheim having the highest number of players, 31 each.
![players_per_club](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/47a87da7-59ca-4eed-a1c3-e6efd7c5f7d5)

2.	The age distribution of players in the first division peaked between the ages of 23 to 25 years. The age of players is approximately normally distributed. From the Dist plot, we can see a specific shape called a 'bell curve.' This curve means that most people have ages close to the average, and as we move away from the average in either direction, the number of people with those ages decreases. In the first division, as expected, majority of players below 20 are prospect and are still being groomed to play in the first division. Also, as players grow older, nature takes its turn on them and they can't compete at the top-level week in week out. So as they age, they retire from the game.
![age_distribution](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/194832d8-5279-4865-8a80-44019f1c2aa8)
![Q-Q plot](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/6885f540-785f-4d2c-91a0-92a164d5346f)


4.	Frankfurts, Makoto Hasabe is the oldest player in the first division at age 39 while 6 players occupy the yougest players spot at age 17 each.
![Oldest_per_position](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/db1ffa58-1dee-472d-acfc-66e6761d1277)

6.	Goalkeepers occupy 38% of the oldest players in each club, which signifies that they have high longetivity that other positions of the field.
![Oldest_per_club](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/04c02fb3-1008-4ead-9a83-a98d75a4e107)

8.	The average age of player by their position in the first division is still below 30 which is impressive. This shows the league has low rate of retirement due to age in the future. The goalkeeping department has the highest average age of players at 27 years while the left midfield position has the lowest average age at 23.
 ![Player_agegroup](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/bbcb80de-c394-4972-930d-c7d72cc53763) ![Av_age_club](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/30302a58-9ebd-4949-9b39-70c9d08a1f6b)


10.	The tallest player in the bundesliga is Florian Schock, a goalkeeper who plays for VfB Stuttgart. Interstingly, VfB Stuttgart have the tallest goalkeeper, centre defender and center forward in the Bundesliga.
 ![Players_height](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/0293ab7d-d5a6-4921-a211-fc9c569ec21c)

12.	In the first division, the Goalkeepers have the highest average hieght of just over 1.9metres. This is expected as goalkeepers are expected to tall enough to protect the goal post. The second tallest in the first division are the central defenders, also expected that a central defender has enough aerial presence to protect the defense from aerial balls. The third tallest are the Centre forwards. This suggests that, most teams in the division depend on attackers that are good in the air and wingers that can float in crosses into the opposition's goal to create chances.
 ![Av_height_position](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/fb76ab1d-04d5-49a0-8839-e0edaa289fd2)


14.	Over 45% of the players in the first division are from Germany while foriegners are below 10% with French players occupying 7% of the total players in the division. Shows that the league invests more in home grown players than foriegn players.
![players_country](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/61fb5c36-3a99-405d-96f9-c48a9c13fbba)

16.	It is no surprise that the top 5 clubs in the division have the most valuable players in the division with Jude Bellingham of B. Dortmund being the most valuable player in the league. German gaints, Bayern munich have 5 players, while liepzig, frankfurt and leverkuzeen complete the top 10 in the league.
 ![Top_valuable_players](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/4a0cd262-381b-40bf-b77d-1be5f05a2413)

18.	For the valuble players in every football position in the league, bayern dominate by having the most valuble players in 7 positions in the league.
 ![Valuable_by_position](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/b4c8ac83-e68d-46f5-ad83-340185ced3ee)

20.	Bayern munich also dominate when it comes to the average value of players in each club with an average value of 35 million
    ![Av_player_value_club](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/3a6ff749-9a16-4678-ae6a-d3262b50d5db)

21.	In terms of the average value of players by their position, the Second striker role in attack has the highest value with just over 17.5 million. Goalkeepers have the least average value in the league with an average of around 2.3 million.
![Av_player_value_position](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/67911f2f-daa0-4a41-bd65-41e9160c9351)

23.	We have 181 different agencies that manage the players in the first division of the german league with the ROOF agency managing the highest number of players in the league (30).
 ![Top_agency_count](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/4accda53-c281-49a3-8bcf-8e6893095cb1) ![ROOF_mangment_club](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/aaed3a2f-2fab-4a4d-83c6-760ac1498ede)


25.	For Sport360 Agency, they manage the second highest number of players in the first division, a total of 27 players across the division. They have 5 players in Hertha BSC which is the highest number in a club. 18% of their player base in the first division.![Sporty_management](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/80cf1a2c-3f6f-4c29-89f2-151a0f20d10b)


26.	While most of the players in the first division do not have a sponsor (over 60% of the players). Adidas, Nike and Puma are the top sponsors with Adidas sponsoring around 16% of the players in the league, Nike 12% and puma 8% with the remaining 2% sponsored by Under Armour, Uhlsport, HashtagOne, New Balance and Mizuno.
 ![Top_kit_sponsors](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/0f7bbed3-1844-4e03-8af4-cb22f486e921)

28.	Adidas has its highest player sponsorship in Bayern Munich, having 11 players in the club signed to them. Nike has its highest player sponsorship in Hertha BSC, TSG Hoffenheim and Bor. Dortmund, having 6 players each in the club signed to them. Puma has its highest player sponsorship in Bor. M'gladbach, having 6 players in the club signed to them.
 ![AdidAS_top_clubs](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/5f545c9a-ac9f-4107-8e99-1e9b87179e78) ![Nike_top_clubs](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/9bad6d3c-8c85-435e-b65b-717e9443ba04) ![puma_top_clubs](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/9f760e10-b98a-41fc-ae8a-45739318a52e)


30.	In the year 2022, a total of 166 players joined the first division being the highest number of players in the last decade. From the year 2009 the chart shows a positive slope year on year which shows how much the first division has improved in the last decade.![players_joined_ina_year](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/260c119a-0fa4-4ce4-ba22-1d0eef0d4144) ![value_players_ina_year](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/2b1af06c-b26a-4db4-af7f-55577edcb908)


31.	In 2022, Schalke 04 has the highest number of players who joined the club with a total of 15 players while 12 joined Hertha BSC and 11 joined FC Koln ![number_players_joined_club](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/387d8600-33f1-4fea-81ee-e446920fe66a)

32.	Also, in 2022, the league signed the highest number of players in the centre back position, a total of 35 players signed while a total of 34 centre forwards were signed in the same year.![number_players_joined_position](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/038b06c3-8b9d-451b-9a5c-d38673e0f3f3)

33.	In terms of the value of players signed, in 2017, the league signed players with an average value of almost 20 million making it the year with the highest in terms of the average value of players joined. ![value_players_ina_year](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/99d7c07f-506c-4c03-8c4e-45faf5dbc21e)


34.	From the chart, most of the current players in the league have contracts expiring in the year 2024 and 2025. The average age of players that fall in this category are between 25 -35 years old. While for players with contracts expiring after 2025, we can see a normal distribution of ages between 23 and 28 years old. ![players_contract_expiry](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/0369fce7-fe99-4a45-9201-805ae646881b) ![age_distribution_player_after2025](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/27646531-0428-431c-b39c-b4ae18afa955)


35.	For players, who have their contracts expiring after 2025 and are 30 years and above, we have 4 players in this category with three of them in the goalkeeping position and a Defender - Right back.
36.	Thomas Mueller and Tony Jantschke are the longest serving players in the first division having being in Bayern munich and Bor. M'gladbach for 15 years.![longest_serving_players](https://github.com/Kayode-Abereowo/Bundesliga_players_analysis/assets/46594267/5b421ab8-a9cd-4389-8efd-e348a5817625)




