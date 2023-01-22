# Content Flow

This sequence diagram displays the process starting with the content creation until the consumption by the user.

```mermaid
sequenceDiagram
    actor Content Admin
    participant CMS (Strapi)
    participant DB (PostgeSQL)
    participant Frontend (NextJS)
    actor User
    
    note right of Frontend (NextJS): NextJS build process

    Content Admin->>CMS (Strapi): create new content
    activate CMS (Strapi)
    CMS (Strapi)->>DB (PostgeSQL): save data
    activate DB (PostgeSQL)
    DB (PostgeSQL)-->>CMS (Strapi): data saved
    deactivate DB (PostgeSQL)
    deactivate CMS (Strapi)
    Content Admin->>CMS (Strapi): publish new content
    activate CMS (Strapi)
    CMS (Strapi)->>Frontend (NextJS): trigger build process (via webhook)
    deactivate CMS (Strapi)
    activate Frontend (NextJS)
    rect rgb(255, 245, 173)
    Frontend (NextJS)->>CMS (Strapi): fetch new content
    activate CMS (Strapi)
    CMS (Strapi)->> DB (PostgeSQL): get data
    activate DB (PostgeSQL)
    DB (PostgeSQL)-->> CMS (Strapi): return data
    deactivate DB (PostgeSQL)
    CMS (Strapi)-->>Frontend (NextJS): return new content
    deactivate CMS (Strapi)
    Frontend (NextJS)->>Frontend (NextJS): generate new static html file (SSG)
    end
    deactivate Frontend (NextJS)
    User->>Frontend (NextJS): request new content
    activate Frontend (NextJS)
    Frontend (NextJS)-->>User: return html file with new content
    deactivate Frontend (NextJS)
```
