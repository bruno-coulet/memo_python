caractères spéciaux en regex : 
`.` et `-`
Il faut les échapper en les précédant d'un antislash `\`  :
` \.` et `\-`  pour `\` et `.`

## Table des symboles Regex

| Symbole         | Fonction                                                                                              | Exemple correspondant                |
| --------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------ |
| \|              | OU logique (alternance)                                                                               | `chat\|chien` → "chat" ou "chien"    |
| `( )`           | Regroupement / capture de groupe<br>uniquement ce qui est explicitement entre les parenthèse          | `(ab)+` → correspond à "abab"        |
| `[ ]`           | Classe de caractères                                                                                  | `[abc]` → "a", "b" ou "c"            |
| `[A-Z]`         | Lettre majuscule                                                                                      | Correspond à "A", "B", ..., "Z"      |
| `[a-z]`         | Lettre minuscule                                                                                      | Correspond à "a", "b", ..., "z"      |
| `[0-9]`         | Un chiffre entre 0 et 9                                                                               | Correspond à "8"                     |
| `[A-Za-z]+`     | Suite de lettres (majuscules ou minuscules)                                                           | "HelloWorld"                         |
| `[A-Za-z.\- ]+` | Lettres, tiret, point et espace                                                                       | "My-Website.com"                     |
| `\d`            | Un chiffre (`[0-9]`)                                                                                  | `\d+` → "2025" dans "Juillet 2025"   |
| `\w`            | Caractère alphanumérique ou `_` (`[a-zA-Z0-9_]`)                                                      | `\w+` → "user_123"                   |
| `\s`            | Caractère d’espace (tab, espace, saut de ligne)                                                       | `\s+` → "   " ou "\n"                |
| `\S`            | est l’inverse de `\s` :<br>**tout sauf** ces caractères  <br>    lettres, chiffres, ponctuation, etc. |                                      |
| `+`             | 1 occurrence ou plus du motif                                                                         | `a+` → "aaaa"                        |
| `*`             | 0 occurrence ou plus                                                                                  | `ba*` → "b", "ba", "baaa"            |
| `?`             | 0 ou 1 occurrence (optionnel)                                                                         | `colou?r` → "color" ou "colour"      |
| `.`             | N’importe quel caractère (sauf saut de ligne)                                                         | `a.c` → "abc", "a7c"                 |
| `^`             | Début de chaîne                                                                                       | `^Bonjour` → "Bonjour tout le monde" |
| `$`             | Fin de chaîne                                                                                         | `fin$` → "à la fin"                  |
| (a\|b\|c)       | "a", "b", ou "c" (équivalent à `[abc]`)                                                               | `(ab)+` → "abab"                     |
| (\s+\|,)        | Un ou plusieurs espaces **ou** une virgule                                                            | Match `"  "` ou `","`                |



|Fonction|Où cherche-t-elle ?|Extrait un match si...|
|---|---|---|
|`re.match()`|Seulement au **début**|Le motif est **au tout début**|
|`re.search()`|**N’importe où** dans la chaîne|Le motif est **présent quelque part**|

`re.match(r"abc", "abcdef") `  ✅ trouve "abc" au début → Match
`re.match(r"abc", "123abc")`  ❌ "abc" n’est pas au début → None

###  `re.sub()`
 Cette fonction substitue les occurrences d'un motif dans une chaîne de caractères par une valeur de remplacement spécifiée :

```python
re.sub(motif, remplacement, chaîne[, count, flags])
```
