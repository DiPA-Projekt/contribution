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

### GitHub Packages einrichten

Alle unsere Artefakte in **GitHub Packages** können von allen über einen **GitHub-Account** unabhängig ob sie Mitglied in der Organisation "DiPA-Projekt" **heruntergeladen** werden.

#### GitHub Personal Access Token anlegen

Gehen Sie in Ihre persönlichen GitHub-Einstellungen und erstellen Sie sich einen Personal Access Token mit dem Recht von der Registry lesen zu dürfen.

Link: https://github.com/settings/tokens

![image](https://user-images.githubusercontent.com/6279703/111908499-cb273980-8a59-11eb-85d5-5630c5c8e4bd.png)

#### Maven

Legen Sie eine `settings.xml` im `~/.m2` Verzeichnis an oder ergänzen Sie es entsprechend.

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <activeProfiles>
    <activeProfile>github-packages</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github-packages</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo1.maven.org/maven2</url>
          <releases>
			<enabled>true</enabled>
		  </releases>
          <snapshots>
		    <enabled>true</enabled>
		  </snapshots>
        </repository>
        <repository>
          <id>github-packages</id>
          <name>GitHub - DiPA-Projekt</name>
          <url>https://maven.pkg.github.com/dipa-projekt/projektassistent-openapi</url>
          <releases>
			<enabled>true</enabled>
		  </releases>
          <snapshots>
		    <enabled>true</enabled>
		  </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>
  <servers>
    <server>
      <id>github-packages</id>
      <username>HIER_GITHUB_BENUTERNAME_EINTRAGEN</username>
      <password>HIER_IHREN_GITHUB_PERSONAL_ACCESS_TOKEN_EINTRAGEN</password>
    </server>
  </servers>
</settings>
```

#### NPM

Geben Sie folgenden Befehl ein, um den GitHub Personal Access Token für NPM zu setzen und die NPM-Registry für DiPA einzustellen.

**Einstellen des Autorisierungstoken:**
```bash
npm config set //npm.pkg.github.com/:_authToken PERSONAL_GITHUB_ACCESS_TOKEN
```

**Einstellen der NPM-Registry für DiPA-Packages:**
```bash
npm config set @dipa-projekt:registry https://npm.pkg.github.com
```

## Architektur

DiPA ist eine Webanwendung, die der Client-Server-Architektur entspricht. DiPA ist somit modulweise betrachtet immer in folgende
drei Komponenten unterteilt:

- Client (Frontend), SPA/PWA, JavaScript/TypeScript
- API (OpenAPI)
- Server (Backend), Java Spring Boot

### API-Design mit OpenAPI

Sobald eine Client-Server-Kommunikation für ein Module von DiPA erforderlich wird, sollte gemäß der Architektur mit dem API-Design
in einem separaten API-Modul begonnen werden.
Hierzu ist es lediglich notwendig die YAML-Dateien entsprechend der OpenAPI-Spezifikation ohne einschränkende Validierungsregeln im
Zusammenhang mit dem fachlichen Kontekt zu definieren.

Sobald ein Release des API-Design erstellt wurde, wird sowohl ein NPM- als auch ein Maven-Paket im GitHub-Packages (z.B.
[Hub-API(https://github.com/orgs/DiPA-Projekt/packages?repo_name=hub-openapi)]) zur Wiederverwendung bereitgestellt. Anschließend
kann das Client- und Server-Modul die entsprechende API-Modul als Abhängigkeit einbinden und ausimplementieren.

### Client als SPA/PWA

Der DiPA-Client ist in TypeScript und unter zur Zuhilfenahme eines SPA-Frameworks geschrieben. Zum Entwickeln wird der Tool-Stack der generischen CLI
[@leanup/cli](https://www.npmjs.com/package/@leanup/cli) verwendet. Sie ermöglicht das gleichartige Entwickeln mit den etablierten Tools unter einer
einheitlichen Referenzarchitektur unabhängig vom Framework selbst. Darüber hinaus definiert die Referenzarchitektur, wie mit welchem Anwendungscodeteilen
für die Qualitätssicherung umgegangen wird. Durch den Einsatz der [@leanup/cli](https://www.npmjs.com/package/@leanup/cli) soll ein standardisiertes und
fokusiertes Entwickeln gefördert werden.


### Server mit Spring Boot

Der dem DiPA-Server ist eine Java Spring Boot Anwendung und implementiert u.a. die API, Validierung und Businesslogik der Backend-Seite.

## Entwicklung

Die Einrichtung oder Konfiguration der jeweiligen DiPA-Module ist immer der im Repository liegenden README.md zu entnehmen und auch dort zu dokumenieren.
