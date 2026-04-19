# Netlify 404 Fix

Die Domain zeigt auf Netlify, aber Netlify liefert „Page not found“. Die wahrscheinlichste Ursache war nicht DNS, sondern der Publish Directory.

Im Repository liegen die Webseiten-Dateien unter:

```text
public/index.html
public/forms/copilot/index.html
public/forms/postproduktion/index.html
```

Damit Netlify nicht aus dem Repository-Root ausliefert, muss `netlify.toml` enthalten:

```toml
[build]
  publish = "public"
```

Nach Commit/Deploy bitte in Netlify zusätzlich prüfen:

```text
Site configuration → Build & deploy → Build settings → Publish directory
```

Dort sollte entweder `public` stehen oder die Einstellung aus `netlify.toml` übernommen werden.

Danach:
1. Clear cache and deploy site
2. Domain prüfen
3. Form Detection prüfen
4. je eine Testsubmission absenden
