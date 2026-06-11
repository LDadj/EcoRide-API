## EcoRide API | Version 2.1.0

Bienvenue dans la documentation de l'API EcoRide, votre solution de mobilité durable. Cette API vous permet d'obtenir des recommandations de transport écologiques basées sur votre localisation et votre destination. Que vous soyez à Paris, Lyon ou dans une autre ville, EcoRide vous guide vers les options de transport les plus vertes disponibles.

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![FastAPI](https://img.shields.io/badge/FastAPI-005571.svg?style=for-the-badge&logo=fastapi)
![Version](https://img.shields.io/badge/version-2.1.0-green)


### Table des matières


### Pré-requis

- pip
- Python **3.10+**


### Installation
1. Clonez le dépôt :

```bash
git clone https://github.com/EcoRide/EcoRide-API.git
```
2. Accédez au répertoire du projet :

```bash
cd EcoRide-API
```
3. Installez les dépendances :

```bash
pip install -r requirements.txt
```
### Lancement de l'API
```bash
python main.py

uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

L'application sera accessible à l'adresse suivante : `http://localhost:8000`

### Exemple d'utilisation de l'API
```bash
# Requêtage pour Paris
curl -X POST "http://localhost:8000/api/v1/route" \
  -H "Content-Type: application/json" \
  -H "api_key: secret_token_3a" \
  -d '{"user_id": "u1", "city": "Paris", "destination": "Montmartre"}'

# Requêtage pour Lyon
curl -X POST "http://localhost:8000/api/v1/route" \
  -H "Content-Type: application/json" \
  -H "api_key: secret_token_3a" \
  -d '{"user_id": "u2", "city": "Lyon", "destination": "Part-Dieu"}'
```
### Endpoints
#### GET /health
- Description : Vérifie la santé de l'API.
- Réponse : 200 OK
#### POST /api/v1/route
- Description : Obtenir des recommandations de transport écologiques.
- Paramètres :
  - `user_id` (string, requis) : Identifiant de l'utilisateur.
  - `city` (string, requis) : Ville de départ (ex: Paris, Lyon).
  - `destination` (string, requis) : Destination finale.
- Réponse : 200 OK avec les recommandations de transport.


**Codes de retour :**

| Code| Signification |
|-----|--------------------------------------|
| 200 | Recommandation retournée avec succès |
| 401 | Clé API invalide ou manquante |
| 503 | Service météo externe indisponible |


### Structure du projet

```
EcoRide-API/
├── main.py
├── requirements.txt
├── README.md
├── CHANGELOG.md
└── docs/
     ├── api-reference.md
     └── sequence-diagram.md 
```

### Voir les changelog
Voir [CHANGELOG.md](CHANGELOG.md) pour l'historique complet des versions.

### Author
© Foidjou DAUMARD