---
name: skill-schueler-notes
description: "NOTES.md-System nach Matt Pococks Vorbild — speichert Schüler-Präferenzen, Diagnosen, Fix-Historie und verbesserungswürdige Muster pro Schüler. Ermöglicht Kontinuität über Sessions hinweg."
tags: [viantez, coaching, notes, schüler-tracking]
---

# Viantez Schüler-Notes (NOTES.md-System)

## Wann anwenden

- Ian hat eine Session mit einem neuen Schüler abgeschlossen
- Ian bereitet eine Folgesession vor und sagt "der [Name] kommt wieder"
- Nach einer Diagnose (diagnose-viantez) das Ergebnis persistieren
- Ian fragt "was war das nochmal mit [Schüler]?"
- Vor /grill-me für Bestandsschüler: "Check ob NOTES existiert → lad Daten"

## Prinzip

Pococks NOTES.md speichert pro Projekt: User-Präferenzen + Teaching Notes + "Don't Forget" Items.

Wir speichern pro **Schüler** eine Markdown-Datei unter `forge-of-legends/schueler/<schueler-name>.md`.

Struktur:
```
/forge-of-legends/schueler/
├── notes-template.md      (Vorlage, anpassbar)
├── _index.md              (Übersicht aller Schüler + Status)
├── player1.md
├── player2.md
...
```

## NOTES.md Vorlage (pro Schüler)

Kopiere diese Struktur bei jedem neuen Schüler:

```markdown
# Schüler: [Name/In-Game-Name]
**Letzte Session:** [Datum]
**Nächste Session:** [Datum oder "offen"]
**Rang:** [Aktueller Rang]
**Hauptrollen:** [Jungle / Mid / Top / ...]
**Champion-Pool:** [Champ1, Champ2, Champ3]
**Paket:** [3h / 5h / 10h / Einzelsession]
**Status:** [Aktiv / Pausiert / Abgeschlossen]

## Bekannte Probleme / Diagnosen

### [Datum] — [Session-Typ, z.B. Erstsitzung / VOD-Review]
- **Loop:** [Wie war der Feedback-Loop aufgebaut?]
- **Bestätigte Ursache:** [Makro/Mikro/Mental/Knowledge]
- **Fix:** [Was in der Session besprochen]
- **Ergebnis:** [Stand heute]
- **Tipp für nächste Session:** [Wichtigste Erkenntnis]

### [Datum] — Weitere Sessions...
(Format wiederholen)

## Champion-spezifische Notes

### [Champion-Name]
- **Stärken:** [Was der Schüler gut kann]
- **Schwächen:** [Was immer wieder schiefgeht]
- **Übungen gegeben:** [Practice-Tool-Übungen]
- **Matchup-Notes:** [Besondere Matchups merken]

## Präferenzen & Persönlichkeit

- **Lernstil:** [Visuell (VOD) / Praktisch (Live) / Theoretisch (Konzepte)]
- **Kritikfähigkeit:** [Nimmt direktes Feedback an vs. braucht sanftere Einleitung]
- **Selbstreflexion:** [Erkennt eigene Fehler? Oder sucht Schuld extern?]
- **Ziele:** [Was will der Schüler erreichen? Rang? Champion-Beherrschung? Spaß?]

## Kommunikations-Notizen

- [Schüler bevorzugt Discord vs. DM]
- [Spricht er von sich aus Probleme an?]
- [Wie oft meldet er sich zwischen Sessions?]

## Was ICH (der Coach) besser machen kann

- [Selbstkritik: Was hast du in der letzten Session nicht gut gemacht?]
- [Auf welcher Eskrima-Stufe habt ihr gearbeitet und war das realistisch?]
```

## _index.md — Übersicht aller Schüler

```markdown
# Viantez Schüler — Übersicht
*Stand: [Datum]*

| Schüler | Rang | Champion-Pool | Paket | Status | Letzte Session | Nächste Session |
|---------|------|---------------|-------|--------|----------------|-----------------|
| [Name]  | [Rang] | [Champs] | [Paket] | [Aktiv/...] | [Datum] | [Datum] |

## Nachverfolgung

### Diese Woche fällig:
- [ ] [Name] — [Session-Typ] — [Fokus]
- [ ] [Name] — [Session-Typ] — [Fokus]

### Offene Hausaufgaben:
- [ ] [Name] — [Aufgabe + Deadline]
```

## Workflow

### Neuer Schüler:
1. `schueler/note-template.md` kopieren → `schueler/<ig-name>.md`
2. Basis-Daten ausfüllen (Rang, Champion-Pool, Paket)
3. `_index.md` updaten

### Nach jeder Session:
1. Diagnoseprotokoll aus diagnose-viantez in `### [Datum]` eintragen
2. Champion-spezifische Notes updaten (was hat funktioniert, was nicht)
3. Nächste Session in `_index.md` planen

### Vor Folgesession:
1. `schueler/<ig-name>.md` laden
2. Tipp für nächste Session + bekannte Probleme lesen
3. /grill-me starten (oder direkt Session planen wenn genug bekannt ist)

## Integration mit diagnose-viantez

Nach Phase 5 (Fix + Regression) einer Diagnose:
- **Regressionsergebnis** direkt in die Schüler-Notes schreiben
- **Fix-Erfolg** tracken: "Fix X in Session Y besprochen, in Session Z: ✓ gehalten"
- Ermöglicht Mustererkennung: "Schüler A und B hatten beide das gleiche Pathing-Problem → könnte linked sein"

## Nicht-Tun

- **Keine Notizen schreiben während der Session** — danach. Sonst verpasst du was der Schüler sagt
- **Keine Werturteile** — "ist dumm" notieren wir nicht. "Versteht Wave-Management nicht → Knowledge-Gap"
- **Keine zu langen Einträge** — max 500 Zeichen pro Session-Update. Sonst wird nie gelesen
- **Keine veralteten Infos** — wenn Schüler neuen Champion spielt, Champion-Pool updaten
