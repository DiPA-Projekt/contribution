# Willkommen im DiPA-Projekt

[Anschreiben/Abstract]

## Code of Conduct

Wir wollen ein tolles Projekt vorantreiben und dabei anständig miteinander umgehen. Daher bitten wir alle Mitwirkenden, sich an die [Vereinbarung über Verhaltenskodex](./CODE_OF_CONDUCT.md) zu halten.

## GitHub Packages einrichten

Alle unsere Artefakte in **GitHub Packages** können von allen über einen **GitHub-Account** unabhängig ob sie Mitglied in der Organisation "DiPA-Projekt" **heruntergeladen** werden.

### GitHub Personal Access Token anlegen

Gehen Sie in Ihre persönlichen GitHub-Einstellungen und erstellen Sie sich einen Personal Access Token mit dem Recht von der Registry lesen zu dürfen.

Link: https://github.com/settings/tokens

![image](https://user-images.githubusercontent.com/6279703/111908499-cb273980-8a59-11eb-85d5-5630c5c8e4bd.png)

### Maven

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

### NPM

Geben Sie folgenden Befehl ein, um den GitHub Personal Access Token für NPM zu setzen und die NPM-Registry für DiPA einzustellen.

**Einstellen des Autorisierungstoken:**
```bash
npm config set //npm.pkg.github.com/:_authToken PERSONAL_GITHUB_ACCESS_TOKEN
```

**Einstellen der NPM-Registry für DiPA-Packages:**
```bash
npm config set @dipa-projekt:registry https://npm.pkg.github.com
```

## Beiträge 

Beiträge von Nicht-Teammitgliedern sind willkommen. Aus Sicherheitsgründen bitten wir Euch, Änderungen und Verbesserungen per Fork einzubringen.
