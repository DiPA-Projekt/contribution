# Architektur und Entwicklung

Das OpenSource-Projekt (OSS) **DiPA** wird auf GitHub entwickelt und ist für jeden frei zugänglich.

## Einleitung

Für die Entwicklung von DiPA und deren Module verwenden wir ebenfalls stets freie Werkzeuge. Hierdurch wird allen die Beteiligung
am DiPA-Projekt ermöglicht, die Interesse haben mitzugestalten und Neues kennenzulernen.

## Entwicklungsumgebung einrichten

- GitSCM (https://git-scm.com/)
- Node.js (https://nodejs.org/de/download/)
- Java (OpenJDK)
- Editor
  - **Visual Studio Code** (https://code.visualstudio.com/) und
  - **IntelliJ IDEA Community Edition** (https://www.jetbrains.com/de-de/idea/download/)
- Command line interface
  - Entweder (Git-)**Bash** oder
  - **Cmder** (https://cmder.net/) oder
  - **Powershell**

## Architektur

DiPA ist eine Webanwendung, die der Client-Server-Architektur entspricht. DiPA ist somit modulweise betrachtet immer in folgende
drei Komponenten unterteilt:

- Client (Frontend), SPA/PWA, JavaScript/TypeScript
- API (OpenAPI)
- Server (Backend), Java Spring Boot

### API-Design mit OpenAPI
Sobald eine Client-Server-Kommunikation für ein Module von DiPA erforderlich wird, sollte gemäß der Architektur mit dem API-Design
in einem separaten API-Modul begonnen werden.
Hierzu ist es lediglich notwendig die YAML-Dateien entsprechend der OpenAPI-Spezifikation und dem fachlichen Kontekt zu definieren.
Sobald ein Release des API-Design erstellt wurde, wird sowohl ein NPM- als auch ein Maven-Paket im GitHub-Packages (z.B.
[Hub-API(https://github.com/orgs/DiPA-Projekt/packages?repo_name=hub-openapi)]) zur Wiederverwendung bereitgestellt.

### Client als SPA/PWA
Der DiPA-Client ist in TypeScript und unter zur Zuhilfenahme eines SPA-Frameworks geschrieben. Zum Entwickeln wird der Tool-Stack der generischen CLI
[@leanup/cli](https://www.npmjs.com/package/@leanup/cli) verwendet. Sie ermöglicht das gleichartige Entwickeln mit den etablierten Tools unter einer
einheitlichen Referenzarchitektur unabhängig vom Framework selbst. Darüber hinaus definiert die Referenzarchitektur, wie mit welchem Anwendungscodeteilen
für die Qualitätssicherung umgegangen wird. Durch den Einsatz der [@leanup/cli](https://www.npmjs.com/package/@leanup/cli) soll ein standardisiertes und
fokusiertes Entwickeln gefördert werden.


### Server mit Spring Boot
