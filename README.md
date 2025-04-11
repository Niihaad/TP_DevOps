# 🎮 Jeu de Traduction Français → Anglais

Ce projet est un jeu interactif où l'utilisateur doit traduire des mots du français vers l'anglais. Si la réponse est correcte, un message d'encouragement s'affiche et un nouveau mot est proposé. En cas d'erreur, l'utilisateur peut réessayer.

##  Fonctionnalités

 Sélection aléatoire d'un mot en français.  
 Vérification de la réponse saisie par l'utilisateur.  
 Affichage d'un message en cas de succès ou d'échec.  
 Interface simple et responsive avec un design agréable.  

##  Technologies utilisées

- HTML  
- CSS  
- JavaScript (vanilla)  

##  Installation et Lancement

1. **Cloner le projet**  
   ```bash
   git clone https://github.com/Niihaad/TP_DevOps.git
   ```
2. **Accéder au dossier du projet**  
   ```bash
   cd DevOps
   ```
3. **Ouvrir le fichier HTML dans un navigateur**  
   - Double-clique sur `index.html`  
   - Ou utilise Live Server si tu es sous VS Code  

## cas de succès && cas de fail
![image](https://github.com/user-attachments/assets/4838ab4a-0556-4582-8336-e973af9cc8c4)
![image](https://github.com/user-attachments/assets/ec6d394d-1133-44dd-a29f-b55f2b834453)


---
**Intégration Continue et Déploiement Automatique (CI/CD)**

Ce projet utilise GitHub Actions pour automatiser les tâches de vérification et de déploiement du site à chaque mise à jour du code.
Emplacement du workflow

Le fichier de configuration du workflow se trouve dans :
         .github/workflows/ci.yml

tapes du pipeline CI

Chaque fois qu’un push est effectué sur la branche master , le pipeline s'exécute automatiquement avec les étapes suivantes :

    Récupération du code source
    Le workflow commence par cloner le dépôt à l’aide de actions/checkout.

    Vérification de l’historique Git
    Il affiche le statut actuel du dépôt (git status) et les 5 derniers commits (git log), ce qui aide au suivi.

    Configuration de Git
    Un utilisateur Git temporaire est configuré afin de permettre la création et le push de tags depuis le workflow.

    Étape de build simulée
    Comme le projet est un site statique (HTML/CSS/JS), aucune compilation n’est nécessaire. Un simple echo est utilisé pour représenter cette étape.

    Vérification de la présence de index.html
    Le workflow vérifie que le fichier index.html est bien présent dans le dossier public/. Si ce fichier est manquant, l’exécution échoue.

    Création automatique de tags
    À chaque mise à jour sur master, un tag Git de la forme v1.0.X est automatiquement généré et poussé sur le dépôt (où X est le numéro d’exécution GitHub).

Déploiement sur GitHub Pages

Après les vérifications, un deuxième job exécute le déploiement automatique du site via GitHub Pages :

    Le code est à nouveau cloné.

    Les Pages GitHub sont configurées.

    Les fichiers du dossier ./public sont empaquetés en tant qu’artifact.

    L’outil de déploiement publie les fichiers sur GitHub Pages.

Résultat

À la fin du pipeline, le site est mis à jour automatiquement et accessible à l’adresse suivante :
https://niihad.github.io/TP_DevOps/
---

**Utilisation avec Docker**

Une image Docker peut être utilisée pour déployer le jeu localement via un serveur web léger (nginx). 
Création de l'image Docker : Pour créer l'image Docker de notre projet, nous devons d'abord créer un fichier nommé Dockerfile dans le répertoire principal du projet avec le contenu suivant :
     
     # Utilisation d' une image légère de nginx
     FROM nginx:alpine
     
     # Copie tous les fichiers du projet (index.html) dans le dossier par défaut de nginx
     COPY . /usr/share/nginx/html
     
     # Expose le port 80 pour que Nginx serve l'application
     EXPOSE 80

Construction de l'image Docker : Une fois le fichier Dockerfile créé, on doit ouvrir un terminal dans le répertoire du projet et on va exécuter la commande suivante pour construire l'image Docker :

    docker build -t mon-image-nginx .
    
Cette commande crée une image Docker avec le nom mon-image-nginx à partir du Dockerfile.

Lancement du conteneur Docker : Après avoir créé l'image, nous pouvons lancer un conteneur Docker pour exécuter notre projet avec la commande suivante :
    
      docker run -d -p 8080:80 mon-image-nginx

Cela va lancer le conteneur en arrière-plan et mapper le port 80 du conteneur au port 8080 de notre machine locale. Nous pouvons accéder à notre application via l'URL http://localhost:8080.
     

---
Déploiement

Le projet a été déployé avec succès sur GitHub Pages. Vous pouvez tester le jeu en cliquant sur le lien suivant :

(https://niihaad.github.io/TP_DevOps/)

 Développé par **NIHAD ELBARI**  


