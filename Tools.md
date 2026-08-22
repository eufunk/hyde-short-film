# Tools — HYDE

Hält fest, welche KI-Tools für die Produktion tatsächlich genutzt werden, mit aktuellem Status. Ergänzt [gemini-workflow.md](prompts/gemini-workflow.md) (Anleitung, wie ein Tool konkret genutzt wird) und [HowTo.md](HowTo.md) (Produktionsreihenfolge) um den Werkzeugstand — diese Datei ändert sich am häufigsten von allen dreien.

## Aktuell genutzte Tools

| Tool | Einsatzzweck | Status | Notizen |
|---|---|---|---|
| **Gemini 2.5 Flash Image** ("Nano Banana") | Referenzbilder für Figuren (Jekyll/Hyde, Utterson, Enfield, Lanyon) | Aktiv genutzt | Ein Chat pro Figur, Referenzbild-Workflow siehe [gemini-workflow.md](prompts/gemini-workflow.md) |
| **DeeVid AI** | Testvideos für Figuren + Shot-Produktion (Sequenz 01) | Aktiv genutzt | Unterstützt Dialog direkt im Prompt (echte Lippensynchronisation zu gesprochenen Zeilen) — nützlich für Dialog-Shots. Bei Shots **ohne** gewollten Dialog muss "kein Sprechen, Mund bleibt geschlossen" explizit als Hauptanweisung vorangestellt werden, sonst wird teils trotzdem gesprochen. |

## Ursprünglich vorgesehen, bisher nicht eingesetzt

- **Veo** — in [gemini-workflow.md](prompts/gemini-workflow.md) als Bild-zu-Video-Tool dokumentiert, tatsächlich aber bisher nicht genutzt (DeeVid kam stattdessen für die Charaktertests zum Einsatz). Bleibt als Option, z. B. über Vertex AI, falls dort Budget verfügbar ist.

## Alternativen in der Hinterhand (falls DeeVid-Budget erneut ausgeht)

DeeVid wird aktuell wieder aktiv für die Sequenz-Shot-Produktion genutzt (siehe oben). Diese Rangliste bleibt als Reserve stehen, falls das Budget erneut aufgebraucht ist oder ein Shot mit DeeVid nicht zufriedenstellend gelingt.

**Rangliste (extern erhalten, aktualisiert — ersetzt die vorherige Fassung):**

| Rang | Tool | Referenz → Video | Charakter-Konsistenz | Kosten/Test | Einschätzung |
|---|---|---|---|---|---|
| 🥇 | Kling 3.0 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 🟢/🟡 | Erste Wahl testen |
| 🥈 | Vidu | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 🟢 | Sehr guter günstiger Test |
| 🥉 | Hailuo | ⭐⭐⭐⭐½ | ⭐⭐⭐⭐ | 🟢/🟡 | Sehr interessant |
| 4 | PixVerse | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 🟢/🟡 | Gut für viele Experimente |
| 5 | Runway | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 🔴 | Qualität top, aktuell zu teuer |
| 6 | Luma | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 🟡 | Gut, aber nicht erste Wahl |
| 7 | Pika | ⭐⭐⭐½ | ⭐⭐⭐ | 🟢/🟡 | Eher für kreative Effekte |
| 8 | Veo | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 🔴 | Sehr stark, für 90-s-Film teuer |

**Einordnung für dieses Projekt:**
- **Kling 3.0** ist jetzt Erste-Wahl-Testkandidat — starke Konsistenz-Werte bei günstigem bis mittlerem Kostenniveau, passt gut zum begrenzten Budget nach dem DeeVid-Ausfall.
- **Vidu** als güns­tigster Kandidat mit Spitzenwerten eignet sich besonders für die erste Testrunde (siehe [HowTo.md](HowTo.md) Schritt 4, Stiltest an 1–2 Shots), bevor Budget in teurere Tools fließt.
- **Hailuo** und **PixVerse** sind gute Kandidaten für viele günstige Experimentierdurchläufe — z. B. mehrere Prompt-Varianten eines Shots durchprobieren, bevor final generiert wird.
- **Runway** und **Veo** liefern laut Einschätzung die höchste Qualität, sind für den aktuellen Umfang (24 Shots über zwei Sequenzen, ca. 90 s) aber als zu teuer eingestuft — Kandidaten für einzelne Schlüsselshots (z. B. Sequenz 01 Shot 10 "Erstes klares Gesicht"), falls später Budget dafür da ist, nicht für die Breite.
- **Luma** und **Pika** eher Nische (Atmosphäre bzw. kreative Effekte) als Hauptkandidat für dieses Projekt.
- Bei **allen** Tools vor dem ersten produktiven Einsatz kurz prüfen: erzwingt es bei erkannten Gesichtern einen Talking-Avatar-/Lip-Sync-Modus (siehe DeeVid-Erfahrung oben)? Das war der einzige echte Stolperstein bisher.

**Praktischer Vorschlag:** Mit **Vidu** oder **Kling 3.0** an 1–2 Testshots aus [HowTo.md](HowTo.md) Schritt 4 starten (günstig, hohe Konsistenz), Runway/Veo als möglichen Upgrade-Pfad für einzelne Schlüsselshots im Hinterkopf behalten.

## Hinweis zur Pflege

Sobald ein neues Tool getestet oder fest gewählt wird: hier eintragen (Zweck, Status, Eigenheiten des Tools). Wird es zum neuen Haupt-Video-Tool, zusätzlich [gemini-workflow.md](prompts/gemini-workflow.md) aktualisieren — die ist aktuell noch auf Veo als Zieltool ausgelegt.
