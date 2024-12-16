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
Description:
Temps:
Taille:

# Q13:  Proposition 2
Description:
Temps:
Taille:

# Q14:  Proposition 3
Description:
Temps:
Taille:

# Q15:  Proposition 4
Description:
Temps:
Taille: