# StevenX

Application web — réseau social (prototype).  
Ce dépôt contient le code source d'une application web sociale développée en PHP. Ce README fournit une présentation, des instructions d'installation, d'exécution et de contribution ainsi que des conseils de déploiement. Adaptez les sections "Installation" et "Commandes" selon le framework choisi (Laravel, Symfony, ou PHP natif).

## Statut
En cours de développement — WIP. Dernière mise à jour : 2026-01-21.

## Vue d'ensemble
StevenX est une application web de type réseau social visant à fournir des fonctionnalités classiques telles que :
- inscription / authentification des utilisateurs
- profils utilisateurs
- publication de posts (texte / médias)
- commentaires et mentions
- système de "like" / réactions
- gestion des relations (follow / unfollow)
- administration basique

Remarque : le dépôt est en PHP (langage principal). La structure exacte (framework, organisation) doit être précisée dans le dépôt — mettez à jour ce README si vous utilisez Laravel, Symfony, ou un micro-framework.

## Arborescence (extrait)
- `README.md` — ce fichier.
- `php essaie/` — dossier présent dans la racine (contenu de test / essais PHP).
- Autres fichiers et dossiers (ex : `composer.json`, `public/`, `src/`, `routes/`, `config/`, `tests/`) attendus mais à confirmer/ajouter selon l'implémentation.

## Prérequis
- PHP 8.0+ recommandé (ajustez selon exigences)
- Composer (gestionnaire de dépendances PHP)
- Serveur web : Apache ou Nginx (ou usage du serveur PHP intégré pour développement)
- Base de données : MySQL / MariaDB / PostgreSQL / SQLite selon configuration
- Extensions PHP courantes : pdo, pdo_mysql (ou pdo_pgsql), mbstring, openssl, json, fileinfo

## Installation (générique)
1. Cloner le dépôt :
   ```bash
   git clone https://github.com/SHADOW-007-Hunter/StevenX.git
   cd StevenX
   ```
2. Installer les dépendances (si `composer.json` présent) :
   ```bash
   composer install
   ```
3. Configurer l'environnement :
   - Copier le fichier d'exemple `.env.example` si présent :
     ```bash
     cp .env.example .env
     ```
   - Éditer `.env` et renseigner les variables (base de données, clé d'application, configuration mail, etc.)

4. Préparer la base de données :
   - Si le projet utilise des migrations (ex. Laravel / autre) :
     ```bash
     php artisan migrate --seed
     ```
     ou la commande équivalente pour votre framework.
   - Sinon, importer le fichier SQL fourni (le cas échéant) :
     ```bash
     mysql -u user -p database_name < schema.sql
     ```

5. Lancer le serveur en mode développement :
   - Pour PHP natif :
     ```bash
     php -S localhost:8000 -t public
     ```
   - Pour Laravel :
     ```bash
     php artisan serve
     ```

6. Ouvrir : http://localhost:8000

Remplacez les commandes ci-dessus par celles correspondant au framework réel du projet.

## Configuration importante
- Gestion des fichiers uploadés : vérifier les répertoires `storage/` ou `public/uploads/` et appliquer les permissions nécessaires.
- Clé d'application (APP_KEY) : générer et stocker en sécurité.
- Configuration mail pour notifications / reset de mot de passe.

## Utilisation (scénarios usuels)
- Création d'un compte et connexion
- Publication d'un post (texte / image)
- Interagir avec d'autres utilisateurs (commentaires, likes, follow)
- Recherche et exploration de profils

(Précisez ici des exemples d'URL d'API ou d'interface si votre projet expose une API REST/GraphQL.)

## Tests
- Si des tests sont présents (PHPUnit, Pest, etc.) :
  ```bash
  ./vendor/bin/phpunit
  ```
- Rédigez et exécutez des tests unitaires et d'intégration pour couvrir les principales fonctionnalités sociales.

## Développement
- Branching model suggéré :
  - `main` : branche stable / déployée
  - `develop` : intégration continue des fonctionnalités
  - branchs feature : `feature/nom-fonctionnalite`
- Bonnes pratiques :
  - Utiliser des migrations pour la BD
  - Créer des seeds pour données de test
  - Documenter les endpoints API
  - S'assurer d'une politique de validation et d'assainissement des entrées (sécurité)

## Sécurité
- Valider et nettoyer toutes les entrées utilisateurs (XSS, injection SQL)
- Stocker les mots de passe de façon sécurisée (bcrypt / Argon2)
- Configurer HTTPS en production
- Limiter la taille des fichiers uploadés et vérifier les types MIME

## Déploiement (exemples)
- Hébergement partagé / VPS / conteneur :
  - Déployer le code, installer dépendances via Composer
  - Configurer le serveur web (Nginx/Apache) pour pointer sur `public/` (ou dossier équivalent)
  - Exécuter migrations et clear caches (selon framework)
- Option conteneur : construire une image Docker incluant PHP-FPM, Nginx, Composer, et la base de données séparée.

## Contribution
Merci pour votre intérêt ! Pour contribuer :
1. Forkez ce dépôt.
2. Créez une branche feature : `git checkout -b feature/ma-fonctionnalite`
3. Faites vos changements et tests.
4. Ouvrez une Pull Request décrivant les changements.
5. Respectez les conventions de codage et ajoutez des tests quand possible.

Ajoutez un fichier CONTRIBUTING.md si vous souhaitez des règles détaillées.

## Issues & Support
- Ouvrez une issue pour signaler un bug ou proposer une fonctionnalité.
- Fournissez des étapes de reproduction, logs et environnement.

## Licence
Aucune licence définie actuellement dans le dépôt. Il est conseillé d'ajouter une licence (ex. MIT) si vous souhaitez rendre le projet libre. Exemple rapide : `LICENSE` avec MIT.

## Auteurs / Contact
- Propriétaire du dépôt : SHADOW-007-Hunter  
Pour toute question, ouvrez une issue ou contactez le mainteneur via son profil GitHub.

---

Notes finales :
- Ce README est volontairement générique pour couvrir des implémentations PHP variées. Si vous me confirmez le framework (ex. Laravel, Symfony, ou projet PHP sans framework), je peux adapter ce README pour inclure commandes exactes, configuration d'exemples `.env`, scripts composer, spécificités de déploiement et sections API détaillées.
