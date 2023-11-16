## Docker

Si vous avez déjà vu Docker, créez via docker un conteneur MySQL et importez le fichier `beer.sql` dans votre conteneur.

Si vous n'avez pas encore vu Docker, importez le fichier `beer.sql` dans votre base de données MySQL ou demandez à votre
formateur de vous aider ou de vous donner le docker-compose.

### Prérequis

- Vous devez avoir un dockerfile et un docker-compose.yml
- Vous ne devez pas utiliser de `bind mount` !
- Vous avez le droit d'utiliser un `volume`

## Etude du modèle

### Effectuez un reverse engineering du modèle

- Quelles sont les tables ?

### Il y a des mauvaises pratiques dans ce modèle, lesquelles ?

- Les noms ne sont pas bons
- Pas de majuscule,
- il faut des noms de table en minuscule

## Exercices

Réalisez les requêtes suivantes :

### Quels sont les tickets qui comportent l’article d’ID 500, afficher le numéro de ticket uniquement ?

```mysql
select NUMERO_TICKET
from ventes 
where ID_ARTICLE = 500

```

### Afficher les tickets du 15/01/2014.

```mysql
select ANNEE, NUMERO_TICKET, DATE_VENTE 
from ticket 
where DATE_VENTE = "2014-01-15"

```

### Afficher les tickets émis du 15/01/2014 et le 17/01/2014.

```mysql
select DATE_VENTE, ANNEE
from ticket 
where DATE_VENTE BETWEEN "2014-01-15"
AND "2014-01-17"

```

### Editer la liste des articles apparaissant à 50 et plus exemplaires sur un ticket.

```mysql
select * 
from ventes inner join article 
where QUANTITE >= 50

```

### Quelles sont les tickets émis au mois de mars 2014.

```mysql
select ANNEE, NUMERO_TICKET 
from ticket 
where month('1800-03-31') 
AND year('2014-08-12')

```

### Quelles sont les tickets émis entre les mois de mars et avril 2014 ?

```mysql
select ANNEE, DATE_VENTE
from ticket
where month(DATE_VENTE) in(3, 4)
and ANNEE = 2014

```

### Quelles sont les tickets émis au mois de mars et juin 2014 ?

```mysql
select ANNEE, DATE_VENTE
from ticket
where month(DATE_VENTE) in(3, 6) 
and ANNEE = 2014

```

### Afficher la liste des bières classée par couleur. (Afficher l’id et le nom)

```mysql
select ID_ARTICLE, NOM_ARTICLE
from article
inner join couleur
ORDER BY NOM_COULEUR

```

### Afficher la liste des bières n’ayant pas de couleur. (Afficher l’id et le nom)

```mysql
select ID_ARTICLE, NOM_ARTICLE, ID_Couleur
from article
where ID_Couleur is null

```