```mermaid
graph TD
    subgraph On-Premise
        A[IP Cameras] --> B(On-Premise Gateway/Direct Stream);
        B -->|RTSP Stream| C[Vertex AI Vision];
        E[Physical Access Control Hardware]
    end

    subgraph Google Cloud
        C -- Analysis Results (Face Embedding) --> D[Cloud Pub/Sub];
        D -- Triggers --> F[Cloud Function];
        F -- Reads --> G[Firestore/Cloud SQL (Authorized User Database)];
        F -- API Call --> E;
        C -- Stores Video Clips --> H[Cloud Storage];
    end

    style A fill:#d3d3d3,stroke:#333,stroke-width:2px
    style E fill:#d3d3d3,stroke:#333,stroke-width:2px
```
