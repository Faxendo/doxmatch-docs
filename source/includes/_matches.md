# Matchs

## L'objet 'Match'

> Exemple d'objet Match

```json
{
  "id" : 1,
  "server" : { object Server },
  "tournament" : { object Tournament },
  "map" : "de_dust2",
  "team1" : "Team Alpha",
  "team2" : "Team Bravo",
  "score1" : 10,
  "score2" : 13,
  "switched_side" : 1,
  "match_cfg" : "match",
  "match_mr" : 15,
  "overtime_cfg" : null,
  "overtime_mr" : null,
  "status" : {
    "id" : 20,
    "class" : "primary",
    "text" : "En jeu - Side 2"
  }
}
```

Attribut | Description
-------- | -----------
id | L'identifiant unique du match
server | L'objet "Serveur" représentant le serveur sur lequel ce match est joué
tournament | L'objet "Tournoi" représentant le tournoi auquel ce match appartient
map | Le nom de la map jouée sur ce match
team1 | Le nom de l'équipe actuellement en CT
team2 | Le nom de l'équipe actuellement en T
score1 | Score actuel de l'équipe CT
score2 | Score actuel de l'équipe T
switched_side | Détermine si les équipes ont été inversées depuis le paramétrage initial (utilisé en interne pour Toornament)
match_cfg | Nom du fichier de configuration contenant les règles du match
match_mr | Nombre de round joués à chaque side
overtime_cfg | Si un overtime est nécessaire, nom du fichier de configuration contenant les règles de l'overtime
overtime_mr | Si un overtime est nécessaire, nombre de round joués à chaque side d'overtime
status | Objet représentant le statut actuel du match

## Récupérer tous vos matchs

```shell
curl "https://api.doxmatch.net/v1/matches"
  -H "X-Auth-Session: yoursessioncode"
```

> Le résultat de cette commande sera un tableau de matchs :

```json
[
  }
    "id" : 1,
    "server" : { object Server },
    "tournament" : { object Tournament },
    "map" : "de_dust2",
    "team1" : "Team Alpha",
    "team2" : "Team Bravo",
    "score1" : 10,
    "score2" : 13,
    "switched_side" : 1,
    "match_cfg" : "match",
    "match_mr" : 15,
    "overtime_cfg" : null,
    "overtime_mr" : null,
    "status" : {
      "id" : 20,
      "class" : "primary",
      "text" : "En jeu - Side 2"
    }
  },
  ...
]
```

Cette fonction permet de récupérer toute votre liste de matchs

### Requête HTTP

`GET https://api.doxmatch.net/v1/matches`

### Paramètres

Aucun paramètre n'est requis pour cette requête

## Récupérer un serveur précis

```shell
curl "https://api.doxmatch.net/v1/match/1"
  -H "X-Auth-Session: yoursessioncode"
```

> Le résultat de cette commande sera un match :

```json
{
  "id" : 1,
  "server" : { object Server },
  "tournament" : { object Tournament },
  "map" : "de_dust2",
  "team1" : "Team Alpha",
  "team2" : "Team Bravo",
  "score1" : 10,
  "score2" : 13,
  "switched_side" : 1,
  "match_cfg" : "match",
  "match_mr" : 15,
  "overtime_cfg" : null,
  "overtime_mr" : null,
  "status" : {
    "id" : 20,
    "class" : "primary",
    "text" : "En jeu - Side 2"
  }
}
```

Cette fonction permet de récupérer un match précis via son ID

### Requête HTTP

`GET https://api.doxmatch.net/v1/match/<ID>`

### Paramètres

Paramètre |  Description
--------- |  -----------
id | L'Identifiant unique de votre match

## Créer un nouveau match

```shell
curl "https://api.doxmatch.net/v1/match"
  -X POST
  -H "X-Auth-Session: yoursessioncode"
```

> Cette requête nécessite l'envoi d'un objet représentant le nouveau match :

```json
{
  "name": "Test Server #2",
  "ip": "172.16.13.37",
  "port" : "27025",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

> Le résultat de cette commande sera le nouveau match créé :

```json
{
  "id" : 2,
  "server" : null,
  "tournament" : null,
  "map" : "de_dust2",
  "team1" : "Team Charlie",
  "team2" : "Team Delta",
  "score1" : 0,
  "score2" : 0,
  "switched_side" : 0,
  "match_cfg" : "match",
  "match_mr" : 15,
  "overtime_cfg" : null,
  "overtime_mr" : null,
  "status" : {
    "id" : 20,
    "class" : "primary",
    "text" : "En jeu - Side 2"
  }
}
```

Cette fonction vous permet de créer un nouveau match

### Requête HTTP

`POST https://api.doxmatch.net/v1/match`

### Paramètres

Paramètre | Requis | Description
--------- | ------ | -----------
team1 | Oui | Le nom de l'équipe en CT
team2 | Oui | Le nom de l'équipe en T
match_cfg | Non | Le nom du fichier de configuration contenant les règles du match
match_mr | Non | Le nombre de rounds joués à chaque side
overtime_cfg | Non | Le nom du fichier de configuration contenant les règles de l'overtime
overtime_mr | Non | Le nombre de rounds à chaque side d'overtime
server_id | Non | L'identifiant du serveur à utiliser
map_id | Non | L'identifiant de la map sur laquelle jouer
tournament_id | Non | L'identifiant du tournoi dans lequel est joué ce match

## Modifier un match

```shell
curl "https://api.doxmatch.net/v1/match/2"
  -X PATCH
  -H "X-Auth-Session: yoursessioncode"
```

> Cette requête nécessite l'envoi d'un objet représentant le match modifié :

```json
{
  "name": "My Super Server",
  "ip": "172.16.13.37",
  "port" : "27025",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

> Le résultat de cette commande sera le match modifié :

```json
{
  "id" : 2,
  "name": "My Super Server",
  "ip": "172.16.13.37",
  "port" : "27025",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

Cette fonction vous permet de modifier un match existant.

### Requête HTTP

`PATCH https://api.doxmatch.net/v1/match/<ID>`

### Paramètres

Paramètre | Requis | Description
--------- | ------ | -----------
ID | Oui | Dans l'URL, identifiant du serveur à modifier
name | Oui | Le nom du serveur
ip | Oui | L'adresse IP du serveur
port | Oui | Le port de connexion du serveur
rcon | Oui | Le mot de passe RCon du serveur
password | Non | Le mot de passe d'accès au serveur

## Supprimer un match

```shell
curl "https://api.doxmatch.net/v1/match/2"
  -X DELETE
  -H "X-Auth-Session: yoursessioncode"
```

> Cette commande ne retourne qu'un code 200 si aucune erreur ne survient.

Cette fonction vous permet de supprimer un match existant.

### Requête HTTP

`DELETE https://api.doxmatch.net/v1/match/<ID>`

### Paramètres

Paramètre | Description
--------- | -----------
ID | Dans l'URL, identifiant du match à modifier