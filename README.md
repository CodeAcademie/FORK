### LES ROUTES À UTILISER :

---
#### I. INSCRIPTION - CONNEXION - DECONNEXION

* #### Requête d'inscription :  /user/add (POST) (inscription, soit l'ajout d'un nouvel utilisateur)
    >*  **Paramètres envoyés**
    ```
    {
            "login" : "nomUser",
            "mail" : "mailUser",
            "password" : passwordUser
            // password => 8 caractères
    }
    ```

    >* **Réponses retournées**    
    ```
    {
            "status" : OK,
            "id" : idIdentifiantSession
    } or
    {
            "status": KO,
            "error" : "Retour message"
            // cas n°1 : nomUser déjà dans la BD
            // cas n°2 : mailUser déjà dans la BD
            // cas n°3 : passwordUser < 8 caractères
            // cas n°4 : Error lors de l'ajout dans BD
    }
    ```


* #### Requête d'authentification :  /login (POST) (Demande une authentification en tant que session d’administration)
    >*  **Paramètres envoyés**
    ```
    {
            "mail" : "mailUser",
            "password" : passwordUser
    }
    ```

    >* **Réponses retournées**    
    ```
    {
            "status" : OK
            "id": idIdentifiantSession
    } or

    {
            "status" : KO,
            "error" : "Retour message"
            // cas : Erreur lors de l'authentification de session
    }
    ```


* #### Requête de déconnexion :   /logout (GET) (Demande la révocation d’une clé d’API)
    >*  **Paramètres envoyés**
    ```
    {
            "session_id" : idD'identifiantSession
    }
    ```

    >* **Réponses retournées**    
    ```
    {
            "status" : OK
    } or

    {
            "status" : KO,
            "error" : "Retour message"
            // cas : Erreur lors de la déconnexion de session
    }
    ```



---
#### II. SUPRESSION

* #### Requête de supression de compte :  /user/delete/{id} (DELETE) (Supprime l’utilisateur avec l’id {id}. Supression en cascade des post-its liés)
    >*  **Paramètres envoyés**
    ```
    {
             "session_id" : idD'identifiantSession
    }
    ```

    >* **Réponses retournées**    
    ```
    {
            "status" : OK,
    } or
    {
            "status" : KO,
            "error" : "Retour message"
            // cas : Erreur lors de la supression du compte
    }
    ```



---
#### III.  POST-ITS

* #### Requête d'ajout de post-it :  /sticky/add (ajout d'un nouveau pense-bête)
    >*  **Paramètres envoyés**
    ```
    {
        "title" : "nomPost", (obligatoire)
        "contenu" : "contenuPost", (obligatoire)
        "color" : nomColorPost, (obligatoire)
        "session_id" : idD'identifiantSession
    }
    ```

    >* **Réponses retournées**    
    ```
    {
            "status" : OK,
            "id" : idPost (obligatoire)
            "title" : "titrePost", (obligatoire)
            "contenu" : "contenuPost", (obligatoire)
            "color" : nomColorPost
            // si il y a ajout d'une couleur d'importance
    } or
    {
            "status": KO,
            "error" : "Retour message"
            // cas n°1 : il manque un champ obligatoire
            // cas n°2 : Error d'ajout de post-it
    }
    ```


* #### Requête pour afficher les post-its :  /stickys (GET) Renvoie la liste des post-its existants
    >*  **Paramètres envoyés**
    ```
    {
        "session_id" : idD'identifiantSession
    }
    ```

    >* **Réponses retournées**    
    ```
    "sticky": [
        {
             "id": idPost,
             "titre": "titrePost",
             "date": "05/08/2017",
             "contenu": "contenuPost",
             "color": nomColorPost
        },
        {
            "id": idPost,
            "titre": "titrePost",
            "date": "05/08/2017",
            "contenu": "contenuPost",
            "color": "orangeRed"
        },
        {
            "id": idPost,
            "titre": "titrePost",
            "date": "05/08/2017",
            "contenu": "contenuPost",
            "color": "oliveDrab"
        },
        {
            "id": idPost,
            "titre": "titrePost",
            "date": "05/08/2017",
            "contenu": "contenuPost",
            "color": "gold"
        },
        {
            "etc"
        }     
    ]
    ```


* #### Requête de supression de post-it :  /sticky/delete/{id} (supression d'un pense-bête et de son contenu)
    >*  **Paramètres envoyés**
    ```
    {
        "id" : idPost,
        "session_id" : idD'identifiantSession
    }
    ```

    >* **Réponses retournées**    
    ```
    {
            "status" : OK,
    } or
    {
            "status": KO,
            "error" : "Retour message"
            // cas : Error de supression de post-it
    }
    ```
