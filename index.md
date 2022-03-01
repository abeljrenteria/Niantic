## Abel Renteria <br>
abeljrenteria@gmail.com | [Linkedin](https://linkedin.com/in/abeljrenteria) | [Github](https://github.com/abeljrenteria)

<br>

### Question 1
Suppose this data is a SQL table called ‘PokemonStats’. In an SQL dialect you are most comfortable with, find the top 3 Pokemon in terms of total stats of each type (primary type, Type_1). Your answer should include: 1) the SQL dialect you are using; 2) The SQL query used to answer this question; 3) The returned result.

1) PostgreSQL. 
2) SQL Query. 
```sql
SELECT * FROM (
	SELECT name, type_1, total, ROW_NUMBER() OVER (PARTITION BY type_1 ORDER BY total DESC) AS primary_type_rank
	FROM PokemonStats) ranks
where primary_type_rank <= 3;
```
3) Outputed Table. 

| name         | type_1     | total | primary_type_rank |
|--------------|------------|-------|-------------------|
| "Genesect"   | "Bug"      | 600   | 1                 |
| "Volcarona"  | "Bug"      | 550   | 2                 |
| "Yanmega"    | "Bug"      | 515   | 3                 |
| "Yveltal"    | "Dark"     | 680   | 1                 |
| "Darkrai"    | "Dark"     | 600   | 2                 |
| "Hydreigon"  | "Dark"     | 600   | 3                 |
| "Rayquaza"   | "Dragon"   | 680   | 1                 |
| "Reshiram"   | "Dragon"   | 680   | 2                 |
| "Zekrom"     | "Dragon"   | 680   | 3                 |
| "Thundurus"  | "Electric" | 580   | 1                 |
| "Raikou"     | "Electric" | 580   | 2                 |
| "Zapdos"     | "Electric" | 580   | 3                 |
| "Xerneas"    | "Fairy"    | 680   | 1                 |
| "Florges"    | "Fairy"    | 552   | 2                 |
| "Togekiss"   | "Fairy"    | 545   | 3                 |
| "Lucario"    | "Fighting" | 525   | 1                 |
| "Mienshao"   | "Fighting" | 510   | 2                 |
| "Conkeldurr" | "Fighting" | 505   | 3                 |
| "Ho-Oh"      | "Fire"     | 680   | 1                 |
| "Volcanion"  | "Fire"     | 600   | 2                 |
| "Heatran"    | "Fire"     | 600   | 3                 |
| "Tornadus"   | "Flying"   | 580   | 1                 |
| "Noivern"    | "Flying"   | 535   | 2                 |
| "Noibat"     | "Flying"   | 245   | 3                 |
| "Giratina"   | "Ghost"    | 680   | 1                 |
| "Dusknoir"   | "Ghost"    | 525   | 2                 |
| "Chandelure" | "Ghost"    | 520   | 3                 |
| "Shaymin"    | "Grass"    | 600   | 1                 |
| "Virizion"   | "Grass"    | 580   | 2                 |
| "Tangrowth"  | "Grass"    | 535   | 3                 |
| "Groudon"    | "Ground"   | 670   | 1                 |
| "Landorus"   | "Ground"   | 600   | 2                 |
| "Rhyperior"  | "Ground"   | 535   | 3                 |
| "Regice"     | "Ice"      | 580   | 1                 |
| "Articuno"   | "Ice"      | 580   | 2                 |
| "Vanilluxe"  | "Ice"      | 535   | 3                 |
| "Arceus"     | "Normal"   | 720   | 1                 |
| "Slaking"    | "Normal"   | 670   | 2                 |
| "Regigigas"  | "Normal"   | 670   | 3                 |
| "Crobat"     | "Poison"   | 535   | 1                 |
| "Nidoqueen"  | "Poison"   | 505   | 2                 |
| "Nidoking"   | "Poison"   | 505   | 3                 |
| "Lugia"      | "Psychic"  | 680   | 1                 |
| "Mewtwo"     | "Psychic"  | 680   | 2                 |
| "Cresselia"  | "Psychic"  | 600   | 3                 |
| "Diancie"    | "Rock"     | 600   | 1                 |
| "Tyranitar"  | "Rock"     | 600   | 2                 |
| "Terrakion"  | "Rock"     | 580   | 3                 |
| "Dialga"     | "Steel"    | 680   | 1                 |
| "Metagross"  | "Steel"    | 600   | 2                 |
| "Jirachi"    | "Steel"    | 600   | 3                 |
| "Palkia"     | "Water"    | 680   | 1                 |
| "Kyogre"     | "Water"    | 670   | 2                 |
| "Manaphy"    | "Water"    | 600   | 3                 |
<br>

### Question 2
Imagine a new Pokemon game where you are only allowed to collect ONE type of Pokemon. Similar to other Pokemon games, your goal is to have the strongest battlers and defenders for battles and raids. Which type will you pick? Why? 
<br>
```sql
SELECT type_1, 
	ROUND(AVG(Attack + Sp_Atk + Defense + Sp_Def)) AS Avg_Total_Attack_Defense, 
	ROUND(AVG(Attack + Sp_Atk)) AS Avg_Total_Attack, 
	ROUND(AVG(Defense + Sp_Def)) AS Avg_Total_Defense
FROM PokemonStats
GROUP BY type_1 ORDER BY Avg_Total_Attack_Defense DESC LIMIT 5;
```

| type_1     | avg_total_attack | avg_total_attack | avg_total_defense |
|------------|------------------|------------------|-------------------|
| "Dragon"   | 347              | 185              | 162               |
| "Steel"    | 346              | 147              | 199               |
| "Rock"     | 321              | 149              | 173               |
| "Ghost"    | 301              | 149              | 152               |
| "Fire"     | 300              | 166              | 134               |

<br>

### Question 3
If you want to predict whether the Pokemon is a legendary Pokemon (a.k.a. predict the field isLegendary using other fields), which models would you use? List your top 3 models with pros and cons for each one.
<br><br>
In this case, to predict whether a Pokemon is a legendary Pokemon would require the use of a Classification ML Algorithm. Below is the list of which models could be implemented. 


### Question 4
Pick one model and implement it in a language you are most comfortable with (preferably Python or R). Please do not use the ‘Catch_Rate’ field (if you are Pokemon fan you know why :). What is your in-sample classification accuracy and what fields did you end up using?

Your answer should include: 1) The code of implementing the model (incl. feature processing, model fitting and cross validating); 2) The formula/description of your final model along with the accuracy number. 3) In addition to the code and the model specification, if you choose to submit a presentation/ dashboard as part of your writeup, you can present your results in any way you like. 

