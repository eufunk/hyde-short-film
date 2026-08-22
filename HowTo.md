# HowTo — Produktionsablauf HYDE

Praktische Schritt-für-Schritt-Anleitung: Wie man mit dem vorhandenen Material (Drehbücher, Shotlists, Prompts, Charakter-/Schauplatzbibeln) tatsächlich anfängt zu produzieren. Ergänzt [ProjektGuide.md](ProjektGuide.md) (was liegt wo) um die Reihenfolge der Arbeitsschritte (was tue ich zuerst).

**Kernregel:** Nicht direkt bei Sequenz 01 komplett durchgenerieren. Zuerst Figuren und Ort als Referenzbilder fixieren — sonst fällt erst nach zwölf generierten Shots auf, dass eine Figur in jedem Bild anders aussieht.

## Schritt 1 — Tool-Entscheidung

**Festgelegt:** Bild-KI = **Gemini 2.5 Flash Image** ("Nano Banana"), Video-KI = **Veo**. Grund: Referenzbild-basierte Charakterkonsistenz direkt in der Konversation, ohne `--cref`-Syntax (Midjourney) oder eigenes LoRA-Training (SDXL/ComfyUI). Details und exakte Prompt-Formulierung dafür stehen in [prompts/gemini-workflow.md](prompts/gemini-workflow.md) — Schritt 2 und 5 unten verweisen direkt darauf.

Die Prompts in den `03-bildprompts.md`-Dateien bleiben bewusst tool-neutral geschrieben (funktionieren also auch mit Midjourney/SDXL/Runway/Kling, falls das Tool später wechselt) — `gemini-workflow.md` ergänzt nur, wie sie konkret in Gemini eingesetzt werden.

## Schritt 2 — Charakter-Referenzbilder erzeugen (eigentlicher Startpunkt)

Aus den Charakterbibeln je 3–4 Bilder generieren: frontal, 3/4-Profil, Profil, optional Ganzkörper. **Vorgehen in Gemini:** siehe [prompts/gemini-workflow.md](prompts/gemini-workflow.md), Abschnitt "Referenzbild-Workflow" — Bild im selben Chat halten, Folgebilder darauf referenzieren.

- [charakterbibel/dr-henry-jekyll.md](charakterbibel/dr-henry-jekyll.md) — **beide Zustände testen:** normale Jekyll-Haltung *und* die Hyde-Beschreibung aus dem Abschnitt "Edward Hyde". So zeigt sich früh, ob "ein Darsteller, zwei Zustände" mit Gemini glaubhaft funktioniert — bevor eine ganze Sequenz darauf aufgebaut wird.
- [charakterbibel/gabriel-utterson.md](charakterbibel/gabriel-utterson.md)
- [charakterbibel/richard-enfield.md](charakterbibel/richard-enfield.md)

Diese Bilder sind der visuelle Anker für alle folgenden Shots. Für jede Figur einen eigenen Gemini-Chat offen halten, damit sich die Referenzbilder nicht gegenseitig überschreiben.

## Schritt 3 — Schauplatz-Referenzbild

Ein Bild vom Institutsgebäude aus [schauplaetze/institutsgebaeude.md](schauplaetze/institutsgebaeude.md) generieren — Fassade (Ort A) und Gasse/Tür (Ort B). Gleicher Grund wie bei den Figuren: erst den Ort fixieren, dann erst die Shots, die ihn zeigen.

## Schritt 4 — Stiltest an 1–2 Shots

Nicht sofort alle Shots einer Sequenz durchgenerieren. Erst zwei exemplarische Shots testen, z. B. aus [szenen/sequenz-01/03-bildprompts.md](szenen/sequenz-01/03-bildprompts.md):

- Shot 01 (Establishing)
- Shot 10 (Hydes Gesicht — Schlüsselmoment)

Passen Look, Licht, Stimmung zum gewünschten Ton? Falls nicht: Style-Suffix am Anfang der Datei anpassen — **erst danach** in die Fläche gehen.

## Schritt 5 — Sequenz 01 Shot für Shot

Für jeden Shot (aktuell 12 in Sequenz 01, siehe [02-shotlist.md](szenen/sequenz-01/02-shotlist.md)) — genauer Ablauf inkl. Prompt-Bausteinen in [prompts/gemini-workflow.md](prompts/gemini-workflow.md), Abschnitt "Praktischer Ablauf pro Shot":

1. Bildprompt aus `03-bildprompts.md` in Gemini generieren, dabei auf die Referenzbilder aus Schritt 2/3 zurückgreifen (Referenzbild-Hinweis voranstellen, Negative-Block anhängen)
2. Ergebnis gegen die Charakterbibel prüfen, bei Abweichung im selben Chat nachsteuern statt neu generieren
3. Das fertige Bild als Startframe in Veo laden, den passenden Prompt aus `04-videoprompts.md` als Bewegungsbeschreibung einfügen
4. Clip in [assets/video/](assets/video/) speichern

## Schritt 6 — Sounddesign

Die Sounddesign-Spalte in `02-shotlist.md` als Einkaufsliste nutzen (Regen, Schritte, Wind, Stille …). Als Library-Sounds, Foley oder KI-Audio-Tools — parallel zu Schritt 5 oder danach.

## Schritt 7 — Schnitt

Clips in der in der Shotlist festgelegten Reihenfolge und Dauer zusammensetzen (DaVinci Resolve, Premiere, CapCut o. Ä.).

## Schritt 8 — Gegenprüfen

Fertige Sequenz gegen [prompts/negative-prompts.md](prompts/negative-prompts.md) und die jeweilige Charakterbibel prüfen. Wo weicht ein Shot vom Referenzgesicht, der Kleidung oder dem Ort ab — neu generieren statt hinnehmen.

## Schritt 9 — Nächste Sequenz

Erst wenn Sequenz 01 steht: Sequenz 02 (siehe [szenen/sequenz-02/](szenen/sequenz-02/)) genauso durchgehen, Schritte 4–8.

## Kurzfassung

```
1. Tools: Gemini 2.5 Flash Image (Bild) + Veo (Video) — siehe prompts/gemini-workflow.md
2. Charakter-Referenzbilder (Jekyll + Hyde, Utterson, Enfield), je eigener Gemini-Chat
3. Schauplatz-Referenzbild (Institutsgebäude)
4. Stiltest an 1–2 Shots
5. Sequenz 01: Gemini-Bild → Veo-Video, Shot für Shot
6. Sounddesign
7. Schnitt
8. Gegenprüfen (Negative Prompts + Charakterbibel)
9. Sequenz 02, dann weitere Sequenzen — Schritte 4–8 wiederholen
```
