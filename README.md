# Viantez Skills — League Coaching Agent Toolkit

[![skills.sh](https://skills.sh/b/viantez/skills)](https://skills.sh/viantez/skills)

Agent skills für League of Legends Coaching — entwickelt von Ian Töppel (Viantez). Ein Skill-Paket, das AI-Agents disziplinierte Coaching-Prozesse beibringt.

Adaptiert Matt Pococks Skills-Architektur (121K Stars) auf Coaching: Ein Skill = ein Failure Mode. Klein, adaptierbar, komponierbar.

## Quickstart (30-Sekunden)

```bash
npx skills@latest add viantez/skills
```

Dann im Agent:
- `/skill-grill-me` — Vor jeder Coaching-Session: kritisches Interview in 4 Phasen
- `/skill-context` — Fachglossar für Forge of Legends (Eskrima, Jungle-Phasen, Champion-Archetypen)
- `/skill-diagnose` — 5-Phase Disziplin für Spieler-Analyse (Reproduce → Hypothesen → Instrumentieren → Fix → Regression)
- `/skill-schueler-notes` — NOTES.md-System: Schüler-Präferenzen, Diagnosen und Fix-Historie tracken

## Skills

### Productivity

Skills für den Coaching-Workflow:

- **[skill-grill-me](./skills/productivity/skill-grill-me/SKILL.md)** — Kritisches Interview vor jeder Session. 10 Fragen in 4 Phasen (Problem-Scope → Data Readiness → Method Choice → Session Structure). Verhindert Blind-Sessions.

- **[skill-context](./skills/productivity/skill-context/SKILL.md)** — Fachglossar für Forge of Legends. Definiert Jungle-Phasen, Eskrima-Level 1-5, Champion-Archetypen. Reduziert Token-Verbrauch durch präzise Terminologie (Pococks CONTEXT.md-Prinzip).

- **[skill-diagnose](./skills/productivity/skill-diagnose/SKILL.md)** — Disziplinierte Diagnose für Spieler-Probleme. 5 Phasen: Feedback-Loop bauen → Reproduzieren → 3-5 Hypothesen ranken → Instrumentieren (ein Signal) → Fix + Regression bei nächster Session.

- **[skill-schueler-notes](./skills/productivity/skill-schueler-notes/SKILL.md)** — NOTES.md-System pro Schüler. Speichert Champion-Pool, bekannte Diagnosen, Fix-Historie, Lernstil und Präferenzen. Kontinuität über Sessions.

## Warum

Vier typische Failure Modes beim AI-Coaching, die diese Skills lösen:

1. **"Der Coach hat nicht verstanden was der Schüler braucht"** → `/skill-grill-me` erzwingt Diagnostic-First vor jeder Session.
2. **"Die Analyse ist zu oberflächlich"** → `/skill-diagnose` erzwingt reproduzierbare Hypothesen statt Bauchgefühl.
3. **"Ich hab vergessen was der Schüler letzte Woche gesagt hat"** → `/skill-schueler-notes` persistiert jede Diagnose.
4. **"Zu viele Wörter für einfache Konzepte"** → `/skill-context` gibt jedem Begriff eine klare Definition. Agent spart 20+ Wörter pro Konzept.

### Was es verhindert

| Skill | Verhindert |
|-------|-----------|
| skill-grill-me | Blind-Sessions ohne Diagnostic: einfach lostelefonieren statt vorher zu analysieren |
| skill-context | Token-Verschwendung & schwammige Begriffe ("irgendwie passiv" statt "Gank-Rate 50% unter Benchmark") |
| skill-diagnose | Bauchgefühl-Diagnose: "der ist einfach zu passiv" ohne reproduzierbaren Loop |
| skill-schueler-notes | Vergessene Schüler-Daten: "was war das nochmal mit dem Jarvan-Schüler?" |

## Lizenz

MIT — hack around, make them your own.
