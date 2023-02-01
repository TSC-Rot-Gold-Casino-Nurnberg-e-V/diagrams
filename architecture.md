# Architecture
![](architecture.drawio.svg)

## Beschreibung

### Backend
- Das Backend wird auf dem cloud server Railway gehostet.
- Auf Railway befinden sich zwei Container - headless CMS Strapi und PostgreSQL Datenbank
- In Strapi wird der Content und der Inhalt für individuelle Seiten gepflegt.
- Strapi bietet eine REST API an, welche zur Datenabfrage für die Generierung von (statischen) Seiten genutzt wird.

### Frontend
- Das Frontend wird auf dem cloud server Vercel gehostet.
- Mit dem Framework NextJS werden statische Seiten unter Verwendung des CMS Contents per API Abfrage generiert und auf Vercel abgespeichert.


## Vorteile
### Headless CMS
- **Trennung von Frontend und Backend**: Ein Headless CMS trennt die Verwaltung des Inhalts von der Darstellung, was Flexibilität und Skalierbarkeit ermöglicht. 
- **Bessere Performance**: Da die Seiten statisch generiert sind und beim Aufrufen der Seite kein API Call ausgelöst wird, ist die Ladezeit schneller und die Webseite reaktionsschneller.
- **Sicherheit**: Da das Frontend und Backend getrennt sind, ist die Sicherheit erhöht, da Angriffe auf das Frontend das Backend nicht beeinträchtigen können.

### Static Site Generation
- **Geschwindigkeit**: Static Sites lassen sich schnell ausliefern, da sie aus HTML, CSS und JavaScript bestehen und keine Serveranfragen notwendig sind. 
- **Sicherheit**: Static Sites sind weniger anfällig für Hackerangriffe, da sie keine Datenbanken oder dynamischen Server-Prozesse benötigen. 
- **Kosteneinsparungen**: Static Sites benötigen keine teuren Serverressourcen, da sie einfach auf einem Content Delivery Network (CDN) bereitgestellt werden können. 
- **Einfache Pflege**: Static Sites sind einfach zu pflegen und zu aktualisieren, da sie aus statischen Dateien bestehen und keine komplexen Serverkonfigurationen benötigen.