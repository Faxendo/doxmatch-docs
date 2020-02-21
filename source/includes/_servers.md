# Serveurs

## L'objet 'Serveur'

> Exemple d'objet Serveur

```json
{
  "id" : 1,
  "name" : "Server name",
  "ip" : "172.16.13.37",
  "port" : "27015",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

Attribut | Description
-------- | -----------
id | L'identifiant unique du serveur
name | Nom du serveur
ip | Adresse IP de connexion au serveur
port | Port de connexion au serveur
rcon | Mot de passe RCon du serveur, nécessaire pour faire fonctionner le DoxMatch
password | Mot de passe d'accès au serveur

## Récupérer tous vos serveurs

```shell
curl "https://api.doxmatch.net/v1/servers"
  -H "X-Auth-Session: yoursessioncode"
```

> Le résultat de cette commande sera un tableau de serveurs :

```json
[
  {
    "id": 1,
    "name": "Test Server",
    "ip": "172.16.13.37",
    "port" : "27015",
    "rcon" : "mysuperrcon",
    "password" : "pcw"
  },
  ...
]
```

Cette fonction permet de récupérer toute votre liste de serveurs

### Requête HTTP

`GET https://api.doxmatch.net/v1/servers`

### Paramètres

Aucun paramètre n'est requis pour cette requête

## Récupérer un serveur précis

```shell
curl "https://api.doxmatch.net/v1/server/1"
  -H "X-Auth-Session: yoursessioncode"
```

> Le résultat de cette commande sera un serveur :

```json
{
  "id": 1,
  "name": "Test Server",
  "ip": "172.16.13.37",
  "port" : "27015",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

Cette fonction permet de récupérer un serveur précis via son ID

### Requête HTTP

`GET https://api.doxmatch.net/v1/server/<ID>`

### Paramètres

Paramètre |  Description
--------- |  -----------
id | L'Identifiant unique de votre serveur

## Créer un nouveau serveur

```shell
curl "https://api.doxmatch.net/v1/server"
  -X POST
  -H "X-Auth-Session: yoursessioncode"
```

> Cette requête nécessite l'envoi d'un objet représentant le nouveau serveur :

```json
{
  "name": "Test Server #2",
  "ip": "172.16.13.37",
  "port" : "27025",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

> Le résultat de cette commande sera le nouveau serveur créé :

```json
{
  "id": 2,
  "name": "Test Server",
  "ip": "172.16.13.37",
  "port" : "27025",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

Cette fonction vous permet de créer un nouveau serveur

### Requête HTTP

`POST https://api.doxmatch.net/v1/server`

### Paramètres

Paramètre | Requis | Description
--------- | ------ | -----------
name | Oui | Le nom du serveur
ip | Oui | L'adresse IP du serveur
port | Oui | Le port de connexion du serveur
rcon | Oui | Le mot de passe RCon du serveur
password | Non | Le mot de passe d'accès au serveur

## Modifier un serveur

```shell
curl "https://api.doxmatch.net/v1/server/2"
  -X PATCH
  -H "X-Auth-Session: yoursessioncode"
```

> Cette requête nécessite l'envoi d'un objet représentant le serveur modifié :

```json
{
  "name": "My Super Server",
  "ip": "172.16.13.37",
  "port" : "27025",
  "rcon" : "mysuperrcon",
  "password" : "pcw"
}
```

> Le résultat de cette commande sera le serveur modifié :

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

Cette fonction vous permet de modifier un serveur existant.

### Requête HTTP

`PATCH https://api.doxmatch.net/v1/server/<ID>`

### Paramètres

Paramètre | Requis | Description
--------- | ------ | -----------
ID | Oui | Dans l'URL, identifiant du serveur à modifier
name | Oui | Le nom du serveur
ip | Oui | L'adresse IP du serveur
port | Oui | Le port de connexion du serveur
rcon | Oui | Le mot de passe RCon du serveur
password | Non | Le mot de passe d'accès au serveur

## Supprimer un serveur

```shell
curl "https://api.doxmatch.net/v1/server/2"
  -X DELETE
  -H "X-Auth-Session: yoursessioncode"
```

> Cette commande ne retourne qu'un code 200 si aucune erreur ne survient.

Cette fonction vous permet de supprimer un serveur existant.

### Requête HTTP

`DELETE https://api.doxmatch.net/v1/server/<ID>`

### Paramètres

Paramètre | Description
--------- | -----------
ID | Dans l'URL, identifiant du serveur à modifier