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



### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/abeljrenteria/Niantic/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
