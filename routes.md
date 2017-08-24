####LES ROUTES À UTILISER :

* #### Requête d'ajout user :  /user/add (POST) (Ajoute un nouvel utilisateur à l’application)
* #### Requête de supression user :  /user/delete/{id} (DELETE) (Supprime l’utilisateur avec l’id {id}. Les dépenses dont cet utilisateur est le payeur ou le seul concerné seront automatiquement supprimées)
* #### Requête pour consulter tous les users :  /users (GET) (Renvoie la liste de tous les utilisateurs)
* #### Requête d'authentification :  /login (POST) (Demande une authentification en tant que session d’administration)
* #### Requête de déconnexion :   /logout (GET) (Demande la révocation d’une clé d’API)
* #### Requête pour consulter les post-its :  /stickys (GET) Renvoie la liste des post-its existants
* #### Requête d'ajout de post-it :  /sticky/add (ajout d'un nouveau pense-bête)
* #### Requête d'ajout de post-it :  /sticky/delete/{id} (supression d'un pense-bête)
