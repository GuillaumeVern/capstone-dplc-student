# Premier anti-pattern

Utilisation de node:latest -> Vulnérabilité : 
- Non-deterministe, les mises à jours ne sont pas contrôlées et pourraient inclure des vulnérabilités

## Solution

Utilisation d'une version spécifique avec le moins de vulnérabilité possible

# Second anti-pattern

Utilisation de npm install sans arguments -> Vulnerabilitié : 
- npm install va installer les dépencences dev superflues en production et potentiellement vulnérables

## Solution

npm ci --omit=dev (Clean install sans les dépendences dev)

# Troisième anti-pattern

Copie complète avant l'installation des dépendances -> Bloat :
- npm install va re-télécharger les dépendences même sans changement et le cache Docker sera invalidé

## Solution

Copie de package*.json
npm ci réutilise le cache si les dépendances ne changent pas

# Quatrième anti-pattern

Dockerfile en superuser -> Vulnérabilité : 
- le Dockerfile peut créer un user pour restreindre ses privilèges sinon il sera superutilisateur

# Cinquième anti-pattern

Absence de .dockerignore -> Vulnérabilité + Bloat :
- Risque d'envoyer des fichiers temporaires, locaux voire secrets

## Solution

Ajout de .dockerignore


