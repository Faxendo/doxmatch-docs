# Authentification

> Pour récupérer votre SessionCode, il est nécessaire de fournir votre AuthKey et AuthSecret

```shell
curl "https://api.doxmatch.net/v1/login"
  -H "X-Auth-Key: yourauthkey"
  -H "X-Auth-Secret: yourauthsecret"
```

> Une fois votre SessionCode récupéré, vous pouvez le transmettre dans vos requêtes

```shell
curl "api_endpoint"
  -H "X-Auth-Session: yoursessioncode"
```

L'API DoxMatch utilise une méthode d'authentification en deux étapes.

En premier, vous devez vous connecter à l'API en fournissant votre AuthKey et AuthSecret (que vous pouvez générer sur votre panel) via les Headers `X-Auth-Key` et `X-Auth-Secret`

`GET https://api.doxmatch.net/v1/login`

L'action `login` vous renverra un SessionCode, valable pendant 1 heure et uniquement depuis le serveur qui l'a demandé. Vous pouvez transmettre votre SessionCode via le Header `X-Auth-Session` 

<aside class="notice">
Par mesure de sécurité, le <code>SessionCode</code> n'est valable qu'une heure, et uniquement depuis le serveur d'origine de la demande !
</aside>