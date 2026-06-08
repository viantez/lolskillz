---
name: diagnose-viantez
description: "Disziplinierte Diagnose für Spieler-Probleme. Reproduce → Hypothesen → Instrumentieren → Fix → Regression. Verhindert ‚du bist zu passiv‘-Oberflächlichkeit und erzwingt reproduzierbare Analyse vor der Intervention."
tags: [viantez, coaching, diagnose, debug, spieler-analyse]
related_skills:
  - viantez-grill-me
  - forge-of-legends-context
  - viantez-schueler-notes
---

# /diagnose für Viantez — Spieler-Analyse nach Pococks 5-Phasen

## Wann anwenden

- Ian sagt "Schüler hat Problem mit [Champion/Phase/Makro]"
- Ian hat ein Replay/VOD aber sagt "weiß nicht genau was das Problem ist"
- Nach einer Session soll die Ursache dokumentiert werden
- Vor dem Bau eines Session-Plans (Alternative zu /grill-me wenn das Problem schon klar scheint)

## Prinzip

**Keine Intervention ohne Diagnose.** Pococks /diagnose-Skill hat 5 Phasen. Wir adaptieren:
1. **Feedback-Loop bauen** — wie reproduzieren wir das Problem?
2. **Reproduzieren** — das Problem in Aktion sehen
3. **Hypothesen** — 3-5 mögliche Ursachen
4. **Instrumentieren** — gezielte Prüfung (ein Signal auf einmal)
5. **Fix + Regression** — Lösung + nächste Session prüft ob es hält

## Phase 1 — Feedback-Loop bauen

**Das ist der Hardskill.** Ohne reproduzierbares Signal kein Debug.

Der Feedback-Loop für League-Coaching: Ein Weg, das Problem des Schülers kontrolliert zu beobachten. Nicht ein Spiel — sondern ein Setup, das das Problem zuverlässig zeigt.

### Loop-Typen (nach absteigender Qualität):

1. **VOD-Vergleich** — Schüler problematisches Spiel vs. Schüler gutes Spiel vs. Pro-Spiel gleicher Champion. Diff zeigen.
2. **Practice-Tool-Replay** — Schüler macht die Übung (z.B. erste Clear, Ward-Platzierung, Combo) 5× im Practice Tool. Zeit/Werte tracken.
3. **Live-Beobachtung** — Du siehst zu (via Screen-Share/Stream). Notierst Fehler. Watches 2+ Games.
4. **OP.GG/UGG-Read** — Statistik alleine reicht für Makro-Fehler (CS/min, Ward-Score, Death-Timings, KDA+). Nicht für Mechanik.
5. **Selbst-Report** — Schüler beschreibt was passiert. Schwächster Loop (Verzerrung). Nur wenn VOD/OP.GG nicht verfügbar.

**Loop-Design-Fragen:**
- Zeigt der Loop das Problem SO an wie der Schüler es erlebt? (Oder ein anderes Problem?)
- Ist der Loop deterministisch genug? (1 Spiel Zufall, 5 Spiele = Muster)
- Wie schnell können wir den Loop ausführen? (10min Practice-Tool > 40min VOD-Suche)

### Wann der Loop gut genug ist

- **Makro-Fehler:** 3-5 OP.GG/UGG Screenshots + 1 VOD
- **Mechanik-Fehler:** 1 VOD mit Schüler-Perspektive + 3× Practice-Tool desselben Combos
- **Mindset:** 2-3 komplette VODs + Schüler-Selbst-Reflection

**Wenn kein Loop möglich:** Stopp. "Wir haben zu wenig Daten für eine Diagnose. Optionen:
- Mehr Spiele sammeln (5+)
- Schüler-VOD aufnehmen lassen
- Live-Session ohne Diagnose (Risiko: Zeitverschwendung)"

## Phase 2 — Reproduzieren

Loop läuft. Problem muss SICHTBAR sein.

**Checkliste:**
- [ ] Das Signal im Loop entspricht dem, was der Schüler beschreibt (nicht ein anderes Problem)
- [ ] Das Problem ist in 2+ Spielen/Übungen sichtbar (kein Einzelfall)
- [ ] Du kannst es einem anderen Coach beschreiben: "In Minute 3:20 hat er X gemacht, was zu Y führte"

**Wenn nicht reproduzierbar:**
- "Problem tritt nicht konsistent auf" → vielleicht Tilt oder Matchup-spezifisch
- "Nur in einem Spiel gesehen" → nicht genug Daten → zurück zu Phase 1
- "Schüler sagt Problem X, VOD zeigt Problem Y" → Widerspruch klären

## Phase 3 — Hypothesen (3-5 Stück)

**Erstelle 3-5 falsifizierbare Hypothesen, BEVOR du eine testest.**

Format für jede Hypothese:
```
Wenn <Ursache>, dann <beobachtbare Konsequenz>.
Beleg: <was im VOD/OP.GG dafür spricht>
Test: <was müsste der Schüler anders machen um zu zeigen ob es stimmt>
Level: <Mikro/Makro/Mental>
```

**Hypothesen-Kategorien:**
- **Makro:** Pathing-Entscheidung, Objective-Priorität, Lane-Management
- **Mikro:** Mechanik, Combos, Movement, Timing
- **Mental:** Tilt, Decision-Fatigue, Erwartungsmanagement
- **Wissen:** Matchup-Unkenntnis, Itemization, Wave-State-Verständnis

**Beispiel für Low-ELO Schüler "stirbt zu oft als Jungler":**

1. **Pathing-Hypothese:** "Wenn er seine Route nicht an Matchups anpasst, dann ist er zum falschen Zeitpunkt auf der falschen Seite." → Test: VOD-Check ob er immer gleiche Route spielt
2. **Ward-Hypothese:** "Wenn er nicht in den Jungle des Gegners wardet, dann sieht er Ganks nicht kommen." → Test: Ward-Score + Placement-Check
3. **Tilt-Hypothese:** "Wenn er nach einem Missplay aggressiver statt defensiver spielt, dann ist es ein Tilt-Problem." → Test: Death 2+ passiert immer innerhalb von 3 Minuten nach Death 1
4. **Champion-Hypothese:** "Wenn er Jarvan spielt aber wie Nidalee patht, dann fällt er im Midgame ab." → Test: Clear-Zeit + Gank-Timing mit Champion-Archetyp vergleichen

## Phase 4 — Instrumentieren

**Ein Signal auf einmal testen.** Nicht alle Hypothesen gleichzeitig.

### Methoden je Hypothese:

**Makro-Hypothese testen:**
- VOD-Rückspulfenster auf die strittige Minute (3:20, 7:00, 12:00)
- Frage: "Was hat er in diesem Frame gesehen? Wusste er wo der Enemy-Jungle war?"
- Wenn Nein: Ward-Problem oder Map-Awareness-Problem
- Wenn Ja: Entscheidungsfehler (Mental/Erfahrung)

**Mikro-Hypothese testen:**
- Combos im Practice Tool 5× wiederholen lassen
- Zeit messen: Target-Dummy-Schaden nach 2s, 5s, 10s
- Compare: Schülerzeit vs. deine Benchmark
- Wenn >20% Abweichung: Mechanik-Problem

**Mental-Hypothese testen:**
- Tilt-Check: Stirbt er nach Fehlern aggressiv oder defensiv?
- Time-Buckets: Erste Death 0-5min, 5-10min, 10-15min
- Wenn Deaths sich häufen → Tilt. Wenn gleichmäßig → Skill-Gap
- Extra-Indikator: Chat (pings flame? mute?) + Recall-Verhalten (recalled in unsicherer Position?)

**Mindset-Hypothese testen:**
- Frage: "Was hast du in dieser Situation gedacht?" — Antwort offenbart Frame-of-Mind
- Wenn "ich dachte ich kann ihn killen" → Overconfidence / Risk-Bias
- Wenn "ich wusste nicht was ich machen soll" → Knowledge-Gap
- Wenn "ich wusste es war falsch aber hab's trotzdem gemacht" → Mental Block / Impuls

### Tagging-Regel:
Markiere jeden Fund mit `[DIAG-<hypothese-kurz>]` — späteres Cleanup wird ein Grep. Sonst verlierst du den Überblick über 4 gleichzeitige Analysen.

## Phase 5 — Fix + Regression

### Fix-Formel für jede bestätigte Hypothese:

**Wenn es ein Makro-Fehler war:**
- Session-Fokus: "Dein Pathing ist zu starr. Wir arbeiten an einer Regel: Vor jedem Gank checkst du (1) Lane-State (2) Summoners (3) Enemy-Jungle."
- **Coaching-Level:** Bewusstsein für den Fehler schaffen (Level 1→2)
- Übung: 3 Spiele mit dieser Check-Liste spielen

**Wenn es ein Mikro-Fehler war:**
- Session-Fokus: "Deine Nidalee-Combo braucht 1.2s länger als nötig. Practice Tool: 20× Speer→Cougar→Execute drill."
- **Coaching-Level:** Wiederholung bis Automatismus (Level 2→3)
- Übung: 5× Practice-Tool pro Tag für 3 Tage

**Wenn es Mental/Tilt war:**
- Session-Fokus: "Du tilst nach Deaths. Regel: Nach jedem Death nimmst du 5s Pause. Check: Atmen, nächster Play, Tilt-Check."
- **Coaching-Level:** Selbsterkenntnis (Level 1→2)
- Keine Mechanik-Änderungen in derselben Session — Mental UND Mechanik gleichzeitig ist zu viel

**Wenn es Knowledge-Gap war:**
- Session-Fokus: "Du weißt nicht was dein Champion in diesem Matchup machen soll. Wir gehen 3 Common-Matchups durch." 
- **Coaching-Level:** Verständnis (Level 1→2)
- Übung: Matchup zum nächsten Mal selbst analysieren lassen (schreibt 3 Sätze), dann Review

### Regression — Prüft ob der Fix hält

**Nächste Session:**
- Wir wiederholen Phase 2 (Reproduzieren) mit dem Loop von Phase 1
- Frage: "Ist das Signal besser oder weg?"
- Wenn besser: Fix arbeitet → nächstes Coaching-Level
- Wenn gleich: Fix nicht tief genug → Phase 3 (neue Hypothesen)
- Wenn schlimmer: Falsche Diagnose → zurück zu Phase 1

**Regressionstest-Formel:**
```
Problem: [Original-Signal]
Hypothese: [Bestätigte Ursache]
Fix: [Was geändert wurde]
Ergebnis: [Signal in Folgesession: ✓ besser / = gleich / ✗ schlimmer]
Nächster Schritt: [Level aufbauen / neue Hypothese / anderen Skill fokussieren]
```

## Output einer Diagnose-Session

Nach Abschluss aller 5 Phasen:

```
## Diagnose-Bericht: [Schüler] — [Champion] — [Rang]

**Loop:** [VOD/OP.GG/Practice-Tool — wie War der Feedbck aufgebaut?]
**Reproduktion:** [✓ Problem sichtbar in N Spielen]
**Hypothesen:** 3-5 mit (bestätigt / verworfen) Label
**Bestätigte Ursache:** [Makro/Mikro/Mental/Knowledge — genau ein Satz]
**Fix:** [Session-Fokus + Übung]
**Coaching-Level:** [Start → Ziel]
**Nächste Session:** [Regressionstest planen]
```

## Nicht-Tun

- **Keine "du bist zu passiv"-Diagnose** — sag stattdessen "Deine Gank-Rate in den ersten 10 Minuten ist 0,4/min bei einem Champion der 0,8/min haben sollte. Das ist 50% unter Benchmark."
- **Keine 6 Fixes in einer Session** — ein Problem, eine Übung, ein Takeaway
- **Keine Diagnose ohne Loop** — wenn Phase 1 nicht sauber ist, Phase 3 nicht starten
- **Kein "mach einfach mehr X"** — ohne zu sagen WIE das geht
- **Keine Mechanik-Änderungen Mental-Talk-Sessions** — vermischen nicht
