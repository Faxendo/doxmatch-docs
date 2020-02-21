# Tournois

## L'objet 'Tournoi'

> Exemple d'objet Tournoi

```json
{
  "id" : 1,
  "name" : "Tournament name",
  "match_count" : 0,
  "creation_date" : "2016-02-24 13:37:42"
}
```
Attribut | Description
-------- | -----------
id | L'identifiant unique du tournoi
name | Nom du tournoi
match_count | Nombre de matchs créés dans ce tournoi
creation_date | Date de création du tournoi

## Récupérer tous vos tournois

```shell
curl "https://api.doxmatch.net/v1/tournaments"
  -H "X-Auth-Session: yoursessioncode"
```

> Le résultat de cette commande sera un tableau de tournois :

```json
[
  {
    "id": 1,
    "name": "Test Tournament",
    "creation_date": "2016-02-18 19:37:54"
  },
  ...
]
```

Cette fonction permet de récupérer toute votre liste de tournois

### Requête HTTP

`GET https://api.doxmatch.net/v1/tournaments`

### Paramètres

Aucun paramètre n'est requis pour cette requête

## Récupérer un tournoi précis

```shell
curl "https://api.doxmatch.net/v1/tournament/1"
  -H "X-Auth-Session: yoursessioncode"
```

> Le résultat de cette commande sera un tournoi :

```json
{
  "id": 1,
  "name": "Test Tournament",
  "creation_date": "2016-02-18 19:37:54"
}
```

Cette fonction permet de récupérer un tournoi précis via son ID

### Requête HTTP

`GET https://api.doxmatch.net/v1/tournament/<ID>`

### Paramètres

Paramètre |  Description
--------- |  -----------
id | L'Identifiant unique de votre tournoi

## Créer un nouveau tournoi

```shell
curl "https://api.doxmatch.net/v1/tournament"
  -X POST
  -H "X-Auth-Session: yoursessioncode"
```

> Cette requête nécessite l'envoi d'un objet représentant le nouveau tournoi :

```json
{
  "name" : "New Tournament",
  "toornament" : toornament_id
}
```

> Le résultat de cette commande sera le nouveau tournoi créé :

```json
{
  "id": 2,
  "name": "New Tournament",
  "toornament_id": toornament_id,
  "creation_date": "2016-02-24 01:13:37"
}
```

Cette fonction vous permet de créer un nouveau tournoi

### Requête HTTP

`POST https://api.doxmatch.net/v1/tournament`

### Paramètres

Paramètre | Requis | Description
--------- | ------ | -----------
name | Oui | Le nom du tournoi
toornament | Non | L'identifiant Toornament, si utilisé

## Modifier un tournoi

```shell
curl "https://api.doxmatch.net/v1/toornament/1"
  -X PATCH
  -H "X-Auth-Session: yoursessioncode"
```

> Cette requête nécessite l'envoi d'un objet représentant le tournoi modifié :

```json
{
  "name" : "Edited Tournament",
  "toornament" : new_toornament_id
}
```

> Le résultat de cette commande sera le tournoi modifié :

```json
{
  "id": 2,
  "name": "Edited Tournament",
  "toornament_id": new_toornament_id,
  "creation_date" : "2016-02-24 01:13:37"
}
```

Cette fonction vous permet de modifier un tournoi existant.

### Requête HTTP

`PATCH https://api.doxmatch.net/v1/tournament/<ID>`

### Paramètres

Paramètre | Requis | Description
--------- | ------ | -----------
ID | Oui | Dans l'URL, identifiant du tournoi à modifier
name | Oui | Le nom du tournoi
toornament | Non | L'identifiant Toornament, si utilisé

## Supprimer un tournoi

```shell
curl "https://api.doxmatch.net/v1/toornament/1"
  -X DELETE
  -H "X-Auth-Session: yoursessioncode"
```

> Cette commande ne retourne qu'un code 200 si aucune erreur ne survient.

Cette fonction vous permet de supprimer un tournoi existant.

### Requête HTTP

`DELETE https://api.doxmatch.net/v1/tournament/<ID>`

### Paramètres

Paramètre | Description
--------- | -----------
ID | Dans l'URL, identifiant du tournoi à modifier