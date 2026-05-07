# Surf'n'Turf – Entscheidungsbaum für Gruppenurlaube

Ein interaktives Baumdiagramm, mit dem ihr im Team Urlaubsentscheidungen trefft.
Jeder Knoten ist eine Frage, jede Antwort ein neuer Zweig — Stimmen werden
direkt am Diagramm und in der Gesamtanalyse sichtbar.

**Live-Demo:** _trag deine Netlify-URL hier ein, sobald deployed_

## Features

- 🌊 Verzweigtes Baumdiagramm — Klick auf eine Antwort = neue Folgefrage
- 🗳️ Direkte Abstimmung an jeder Option, mit Live-Balken
- 📊 Gesamtanalyse unten rechts mit Stats und Top-Antworten
- 🔗 Komplett in der URL gespeichert — Link teilen = Stand teilen
- 💾 Lokaler Cache via `localStorage`
- 🎨 Hand-styled, kein Framework, keine Build-Tools

## Stack

Single-File-App. Kein Backend, kein Build-Step.
Reines HTML/CSS/JS in [`index.html`](./index.html).

## Lokal öffnen

Einfach die Datei im Browser öffnen:

```
open index.html
```

## Auf Netlify deployen

### Option 1: GitHub-Verknüpfung (empfohlen)

1. Repo auf GitHub pushen
2. Auf [app.netlify.com](https://app.netlify.com) → **Add new site** → **Import an existing project**
3. GitHub auswählen und dieses Repo verbinden
4. Build-Settings: **leer lassen** (kein Build nötig), Publish-Directory: `.`
5. Deploy klicken — fertig.

Jeder `git push` deployed automatisch neu.

### Option 2: Drag & Drop

Datei direkt auf [app.netlify.com/drop](https://app.netlify.com/drop) ziehen.

## Bedienung

| Aktion | Wie? |
|---|---|
| Frage / Antwort editieren | Reintippen |
| Abstimmen | Auf Option klicken |
| Stimme zurücknehmen | `−` Icon (erscheint beim Hover) |
| Verzweigung erstellen | `⎘` Icon (erscheint beim Hover) |
| Knoten verschieben | Am Kopfbereich ziehen |
| Canvas pannen | Leeren Bereich ziehen |
| Zoomen | Mausrad oder Buttons unten links |
| Ansicht zentrieren | `⊡` im Header |
| Stand teilen | `⤴ Teilen` → Link an Kollegen |

## Datenmodell

Komplett in der URL als Base64-JSON:

```js
{
  nodes: {
    [id]: {
      id, parentId, edgeLabel,
      question: string,
      options: [{ id, text, votes }],
      x, y
    }
  },
  rootIds: [string]
}
```

## Lizenz

MIT
