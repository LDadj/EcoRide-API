# Référence API — EcoRide v2.1.0

Base URL : `http://localhost:8000`

---

## Authentification

Toutes les routes (sauf `/health`) nécessitent le paramètre de query `api_key`.

```
?api_key=secret_token_3a
```

---

## GET /health

Vérifie la disponibilité du service.

**Requête :**
```http
GET /health HTTP/1.1
Host: localhost:8000
```

**Réponse 200 :**
```json
{
  "status": "healthy",
  "timestamp": 1718100000.123
}
```

---

## POST /api/v1/route

Retourne une recommandation de transport.

**Requête :**
```http
POST /api/v1/route?api_key=secret_token_3a HTTP/1.1
Host: localhost:8000
Content-Type: application/json

{
  "user_id": "string",
  "city": "string",
  "destination": "string"
}
```

**Champs de la requête :**

| Champ         | Type   | Requis | Description                         |
|---------------|--------|--------|-------------------------------------|
| `user_id`     | string | ✅     | Identifiant de l'utilisateur        |
| `city`        | string | ✅     | Ville de départ                     |
| `destination` | string | ✅     | Destination souhaitée               |

**Réponse 200 :**
```json
{
  "recommended_transport": "string",
  "estimated_time_minutes": 0,
  "weather_condition": "string",
  "carbon_footprint_g": 0.0
}
```

**Champs de la réponse :**

| Champ                      | Type   | Description                                  |
|----------------------------|--------|----------------------------------------------|
| `recommended_transport`    | string | Mode de transport recommandé                 |
| `estimated_time_minutes`   | int    | Durée estimée du trajet en minutes           |
| `weather_condition`        | string | Météo au départ (`Pluie`, `Nuageux`, `Soleil`) |
| `carbon_footprint_g`       | float  | Émissions CO₂ estimées en grammes            |

**Codes d'erreur :**

| Code | Body                                           | Cause                            |
|------|------------------------------------------------|----------------------------------|
| 401  | `{"detail": "Clé API invalide ou manquante"}`  | `api_key` absent ou incorrect    |
| 503  | `{"detail": "Service météo indisponible"}`     | Timeout ou erreur service météo  |

---

## Valeurs retournées par ville

| Ville       | Météo simulée | Trafic simulé |
|-------------|---------------|---------------|
| Paris       | Pluie         | Saturé        |
| Lyon        | Nuageux       | Fluide        |
| Autres      | Soleil        | Fluide        |
