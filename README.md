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
