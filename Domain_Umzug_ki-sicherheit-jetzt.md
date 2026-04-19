# Domain-Umzug auf fragebogen.ki-sicherheit.jetzt

## Neue Zieladresse

Projektübersicht:

```text
https://fragebogen.ki-sicherheit.jetzt/
```

Direktlinks:

```text
https://fragebogen.ki-sicherheit.jetzt/forms/copilot/
https://fragebogen.ki-sicherheit.jetzt/forms/postproduktion/
```

## Netlify-Schritte

1. Netlify → Site → Domain management → Production domains.
2. Neue Domain/Subdomain hinzufügen:
   ```text
   fragebogen.ki-sicherheit.jetzt
   ```
3. DNS-Hinweis von Netlify prüfen.
4. Beim DNS-Provider der Domain `ki-sicherheit.jetzt` einen CNAME setzen:
   ```text
   Host: fragebogen
   Ziel: <deine-netlify-site>.netlify.app
   ```
5. Nach DNS-Verifizierung SSL/HTTPS in Netlify prüfen.
6. Wenn die neue Domain funktioniert, als Primary Domain setzen.
7. Optional: alte Subdomain `fragebogen.hohl.rocks` als Domain Alias behalten und per `netlify.toml` auf die neue Domain weiterleiten.

## Wichtig

`fragebogen.ki-sicherheit.jetzt` ist eine Subdomain. Dafür ist normalerweise ein CNAME-Eintrag passend. Der genaue Zielwert ist die Netlify-Default-Domain deines Projekts, also etwa:

```text
<site-name>.netlify.app
```

Bitte nicht pauschal auf eine IP setzen. IP-/A-Records sind vor allem für Apex-Domains relevant, nicht für diese Subdomain.

## Nach dem Deploy testen

```text
https://fragebogen.ki-sicherheit.jetzt/
https://fragebogen.ki-sicherheit.jetzt/forms/copilot/
https://fragebogen.ki-sicherheit.jetzt/forms/postproduktion/
https://fragebogen.ki-sicherheit.jetzt/danke/
```

Dann je eine Testsubmission absenden und prüfen:

- Netlify Forms erkennt weiterhin:
  - `copilot-integration-v1`
  - `postproduktion-ki-v1`
- Mail-Benachrichtigung geht direkt an `wolf@hohl.rocks`
- `chatgpt_summary` ist enthalten
- `individual_notes` ist enthalten
- Autosave funktioniert im Browser

## Versandtext kurz

```text
Hallo zusammen,

ich bereite gerade zwei pragmatische KI-Pilotprojekte vor und brauche dafür eure Einschätzung.

Bitte startet über diese Projektübersicht:

https://fragebogen.ki-sicherheit.jetzt/

Dort findet ihr beide Teilprojekte:
1. Office-KI mit Microsoft Copilot
2. Lokale Postproduktions-KI im Büro

Beides ist geplant. Wer zu beiden Themen etwas sagen kann, kann gern beide Fragebögen ausfüllen.

Danke euch – das hilft sehr, damit wir schnell zu einer belastbaren Entscheidung kommen.
```
