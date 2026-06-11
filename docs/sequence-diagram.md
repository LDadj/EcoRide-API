# Diagramme de séquence — EcoRide API

Illustration de la requête `POST/api/v1/route`.

```mermaid

sequenceDiagram
    participant Client
    participant EcoRide API
    participant API météo
    participant API de transport

    Client->>EcoRide API: POST /api/v1/route
    EcoRide API->>EcoRide API: Controle d'accès (API Key) 
    EcoRide API->>API météo: Request - données météo
    API météo-->>EcoRide API: Response - Conditions climatiques
    EcoRide API->>API de transport: Request - options de transport
    API de transport-->>EcoRide API: Response - Options de transport
    EcoRide API-->>Client: 201 Created
```