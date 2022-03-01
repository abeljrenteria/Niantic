### Question 1
Suppose this data is a SQL table called ‘PokemonStats’. In an SQL dialect you are most comfortable with, find the top 3 Pokemon in terms of total stats of each type (primary type, Type_1). Your answer should include: 1) the SQL dialect you are using; 2) The SQL query used to answer this question; 3) The returned result.

1) PostgreSQL
2) 
```sql
SELECT * FROM (
	SELECT name, type_1, total, ROW_NUMBER() OVER (PARTITION BY type_1 ORDER BY total DESC) AS primary_type_rank
	FROM PokemonStats) ranks
where primary_type_rank <= 3;
```
3)
| name      | type_1 | total | primary_type_rank |
| ----------- | ----------- | ----------- | ----------- |
| Genesect    | Bug         | 600         | 1           |
| Volcarona   | Bug         | 550         | 2           |
| Yanmega     | Bug         | 515         | 3           |
| Yveital     | Dark        | 680         | 1           |
| Darkrai     | Dark        | 600         | 2           |



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
