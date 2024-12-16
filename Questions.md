# Q1 : Décrire ce que renvoie la méthode qui liste les questions ?
Réponse:
La méthode qui liste les questions renvoie une liste d'objets JSON, où chaque objet représente une question. Chaque question contient :

- Un id unique.
- Une liste de translations, indiquant la question traduite en différentes langues, chaque traduction ayant un attribut language pour spécifier la langue et un attribut value pour le texte de la question.
- Un objet catgory (probablement une faute pour "category"), qui contient une liste de translations pour les noms de catégorie en plusieurs langues, avec les mêmes attributs (language et value).

# Q2 : Décrire ce que renvoie la méthode qui liste les propositions d'une question ?
Réponse:
La méthode qui liste les propositions d'une question (pour un id donné) renvoie une liste d'objets JSON, où chaque objet représente une proposition associée à cette question. Chaque proposition contient :

- Un id unique pour la proposition.
- Une liste de translations, qui sont les traductions de la proposition en différentes langues (avec les attributs language et value).
- Un objet question, qui contient les informations sur la question associée, y compris :
    +Un id unique pour la question.
    +Une liste de translations pour le texte de la question dans différentes langues.
    +Une catégorie (catgory), avec ses traductions dans différentes langues.

# Q3 : Décrire ce que renvoie la méthode qui évalue des réponses ?
Réponse:
La méthode qui évalue des réponses renvoie une valeur numérique indiquant le score ou la validité des réponses données.

- L'entrée est une liste d'objets JSON contenant les identifiants (id) des propositions sélectionnées.
- La réponse est un entier :
    + 0 indique que les réponses ne sont pas correctes.
    + Une autre valeur pourrait être retournée si les réponses sont correctes ou partiellement correctes (non visible dans cet exemple).

# Q4 : Quelle est la valeur de la RSS utilisée par l'api quarkus en mode JVM ?
Réponse:
La valeur de la RSS (Resident Set Size) utilisée par l'API Quarkus en mode JVM est 211232 K

# Q5: Quel est le temps et la taille de la réponse  de la méthode qui liste les questions
Temps:27.065719s
Taille: 883 bytes

# Q6: Quel est le temps et la taille de la réponse  de la méthode qui liste les propositions d'une question
Temps:12.509577s
Taille: 609 bytes

# Q7: Quel est le temps et la taille de la réponse  de la méthode qui évalue les réponses
Temps: 0.015451s
Taille: 1 byte

# Q8 : Empreinte mémoire en mode natif ?
Réponse:
La commande ps montre une empreinte mémoire (RSS) de 2304 KB en mode natif pour le processus Quarkus.

# Q9: Temps et  taille  réponse   liste les questions
Temps: 21.479436s
Taille: 883 bytes

# Q10: Temps et  taille  réponse  liste des propositions
Temps: 11.891815s
Taille: 609 bytes

# Q11: Temps et  taille  réponse  évaluation les réponses
Temps: 0.001805s
Taille: 1 bytes

# Q12:  Proposition 1
Description: L'activation du cache Hibernate permet de réduire les requêtes répétitives à la base de données en stockant les résultats en mémoire pour une réutilisation ultérieure. Cela améliore les performances des requêtes sur les entités fréquemment utilisées, comme les `Question` et `Proposal`.
Avant l'activation du cache :
    Endpoint : /quizz/questions
    Temps de réponse : 21.47s
    Taille de la réponse : 883 bytes

    Endpoint : /quizz/questions/1/proposals
    Temps de réponse : 12.50s
    Taille de la réponse : 609 bytes

    Endpoint : /quizz/proposals/evaluate
    Temps de réponse : 0.015s
    Taille de la réponse : 1 byte

Après l'activation du cache :
    Endpoint : /quizz/questions
    Temps de réponse : 16.89s (-21%)
    Taille de la réponse : 883 bytes

    Endpoint : /quizz/questions/1/proposals
    Temps de réponse : 11.78s (-5.7%)
    Taille de la réponse : 609 bytes

    Endpoint : /quizz/proposals/evaluate
    Temps de réponse : 0.017s (+13%)
    Taille de la réponse : 1 byte

# Q13:  Proposition 2
Description: Le service de traduction ajoutait une latence importante en raison des appels REST externes et augmentait la taille des réponses JSON. En supprimant ce service, les données renvoyées sont limitées aux informations essentielles, ce qui améliore drastiquement les performances.
 Avant suppression :
1. Endpoint : `/quizz/questions`
   - Temps de réponse : **16.89s**
   - Taille de la réponse : **883 bytes**

2. Endpoint : `/quizz/questions/1/proposals`
   - Temps de réponse : **11.78s**
   - Taille de la réponse : **609 bytes**

3. Endpoint : `/quizz/proposals/evaluate`
   - Temps de réponse : **0.017s**
   - Taille de la réponse : **1 byte**

 Après suppression :
1. Endpoint : `/quizz/questions`
   - Temps de réponse : **0.514s** (-96.96%)
   - Taille de la réponse : **256 bytes** (-71%)

2. Endpoint : `/quizz/questions/1/proposals`
   - Temps de réponse : **0.021s** (-99.82%)
   - Taille de la réponse : **191 bytes** (-68.65%)

3. Endpoint : `/quizz/proposals/evaluate`
   - Temps de réponse : **0.042s** (+147%, mais toujours négligeable).
   - Taille de la réponse : **1 byte** (inchangé).

# Q14:  Proposition 3
Description: Dans la méthode `listProposals`, une boucle était utilisée pour filtrer les propositions en mémoire après une requête SQL. Ce filtrage est superflu, car la clause `find("question.id", questionId)` assure déjà le bon résultat.
 Avant l'optimisation :
1. Endpoint : `/quizz/questions`
   - Temps de réponse : **0.514s**
   - Taille de la réponse : **256 bytes**

2. Endpoint : `/quizz/questions/1/proposals`
   - Temps de réponse : **0.051s**
   - Taille de la réponse : **191 bytes**

 Après l'optimisation :
1. Endpoint : `/quizz/questions`
   - Temps de réponse : **0.367s** (-28.6%)
   - Taille de la réponse : **256 bytes** (inchangé)

2. Endpoint : `/quizz/questions/1/proposals`
   - Temps de réponse : **0.021s** (-58.8%)
   - Taille de la réponse : **191 bytes** (inchangé)

# Q15:  Proposition 4
Description: Supprimer les imports inutilisés 
Temps: 0.001632s
Taille: 1 bytes