# ProjektGuide — HYDE

Diese Datei erklärt, was im Projekt wo liegt und wofür es gedacht ist. Sie ergänzt die kurze Strukturübersicht in [README.md](README.md) um Kontext, Zusammenhänge und den aktuellen Arbeitsstand. Bei Unsicherheit: erst hier nachschlagen, dann die verlinkten Dateien öffnen.

## 1. Was ist das für ein Projekt?

**HYDE** ist ein cinematischer AI-Kurzfilm (Gothic/Psychological Horror, ca. 8 Minuten, Deutsch), lose adaptiert nach Robert Louis Stevensons *Der seltsame Fall des Dr. Jekyll und Mr. Hyde*. Setting: modernes Leipzig. Die Roman-Figuren (Jekyll, Hyde, Utterson, Enfield, Lanyon, Poole, Carew) werden mit ihren Originalnamen übernommen, aber in die Gegenwart übertragen — siehe [charakterbibel/figuren-uebersicht.md](charakterbibel/figuren-uebersicht.md) für die Begründung.

Der Film wird sequenzweise entwickelt: Jede Sequenz bekommt einen eigenen Unterordner unter [szenen/](szenen/) mit fünf Dateien, die aufeinander aufbauen (siehe Abschnitt 3).

## 2. Ordner auf einen Blick

| Ordner | Zweck |
|---|---|
| [szenen/](szenen/) | Eine Sequenz = ein Unterordner. Enthält Beschreibung, Drehbuch, Shotlist, Bild- und Videoprompts. |
| [charakterbibel/](charakterbibel/) | Konsistenzbeschreibungen aller Figuren — projektweit gültig, wird bei jedem Auftritt einer Figur referenziert. |
| [schauplaetze/](schauplaetze/) | Wie `charakterbibel/`, aber für wiederkehrende Orte statt Figuren. |
| [prompts/](prompts/) | Prompt-Bausteine, die für den ganzen Film gelten, nicht nur eine Sequenz (aktuell: Negative Prompts). |
| [assets/](assets/) | Ablage für generierte Bilder/Videos/Audio/Renders. Wird von Git ignoriert (siehe [.gitignore](.gitignore)) — nur die Ordnerstruktur bleibt über `.gitkeep`-Dateien erhalten. |

## 3. `szenen/` — wie eine Sequenz aufgebaut ist

Jeder Sequenzordner (z. B. [szenen/sequenz-01/](szenen/sequenz-01/)) enthält fünf Dateien in fester Reihenfolge — jede baut auf der vorherigen auf:

1. **`00-sequenzbeschreibung.md`** — Ort, Zeit, Wetter, Kurzbeschreibung, zentrale Motive, Ton/Referenzfilme. Der Einstiegspunkt, um zu verstehen, worum es in der Sequenz geht, ohne das ganze Drehbuch zu lesen.
2. **`01-drehbuch.md`** — Die Szene im klassischen Drehbuchformat: Szenenüberschriften, Regieanweisungen, Dialog. Figuren werden bei ihrem ersten Auftritt in GROSSBUCHSTABEN eingeführt (Drehbuchkonvention), Sprecher-Cues vor Dialogzeilen ebenso.
3. **`02-shotlist.md`** — Die Sequenz zerlegt in einzelne Einstellungen (10–14, je nach Komplexität). Pro Shot: Dauer, Kameraperspektive, Kamerabewegung, Bildbeschreibung, Licht, Umgebung, Handlung, Dialog, Sounddesign.
4. **`03-bildprompts.md`** — Ein AI-Bildprompt (Deutsch) pro Shot, referenziert auf die passenden Charakter-/Schauplatzbeschreibungen. Enthält konstante Style-Suffixe, damit alle Shots einer Sequenz optisch zusammenpassen.
5. **`04-videoprompts.md`** — Ein AI-Videoprompt (Deutsch) pro Shot, baut auf dem jeweiligen Bildprompt als Startframe auf, beschreibt nur die Bewegung/Veränderung im Zeitverlauf.

**Aktueller Stand:**
- [szenen/sequenz-01/](szenen/sequenz-01/) „Die Tür" — Filmeröffnung. Utterson & Enfield, erste Hyde-Begegnung nach Kapitel 1 des Romans. Jekyll wird hier **nicht** gezeigt oder erwähnt.
- [szenen/sequenz-02/](szenen/sequenz-02/) „Das Labor" — ein namenloser Mann (in der Produktion als Jekyll geführt) experimentiert nachts an sich selbst. Keine ausgesprochene Verbindung zu Hyde.
- Weitere Sequenzen folgen demselben Schema unter `szenen/sequenz-03/` usw. Die Reihenfolge der Sequenznummern entspricht der Reihenfolge im fertigen Film.

## 4. `charakterbibel/` — wer ist wer

Ziel: Jede Figur soll über alle generierten Bilder/Videos hinweg gleich aussehen. Diese Dateien werden in den Bildprompts referenziert statt die Beschreibung jedes Mal neu zu erfinden.

| Datei | Figur | Status |
|---|---|---|
| [figuren-uebersicht.md](charakterbibel/figuren-uebersicht.md) | — (Meta-Dokument) | Besetzungsentscheidung: welche Romanfiguren übernommen werden, warum auf 5 Kernfiguren reduziert wurde, Rollenverteilung |
| [dr-henry-jekyll.md](charakterbibel/dr-henry-jekyll.md) | Jekyll / Hyde (Hauptfigur) | Vollständig — inkl. eigenem Abschnitt zur Hyde-Präsenz (ein Darsteller, zwei Zustände) |
| [gabriel-utterson.md](charakterbibel/gabriel-utterson.md) | Utterson | Vollständig |
| [richard-enfield.md](charakterbibel/richard-enfield.md) | Enfield | Vollständig |
| [hastie-lanyon.md](charakterbibel/hastie-lanyon.md) | Lanyon | Stub — Rolle/Beziehungen definiert, physische Beschreibung offen |
| [poole.md](charakterbibel/poole.md) | Poole | Stub |
| [danvers-carew.md](charakterbibel/danvers-carew.md) | Carew | Stub |

**Stub** bedeutet: Die Figur ist inhaltlich eingeplant, aber noch nicht in einer Sequenz aufgetreten. Die physische Beschreibung wird ergänzt, sobald ihre erste Sequenz geschrieben wird — nicht vorher, damit das Aussehen zur tatsächlichen Inszenierung passt.

## 5. `schauplaetze/` — wiederkehrende Orte

Gleiches Prinzip wie die Charakterbibel, nur für Orte. Aktuell eine Datei:

- [institutsgebaeude.md](schauplaetze/institutsgebaeude.md) — das Gründerzeit-Institutsgebäude in Leipzig. Wichtig: Die Tür aus Sequenz 01 und Jekylls Labor aus Sequenz 02 gehören zum **selben Gebäude** (Rückseite vs. Vorderseite) — ein bewusstes visuelles Easter Egg, das im Film nie ausgesprochen wird. Diese Datei hält fest, welcher Ort in welcher Sequenz zuerst auftaucht und wie die Lichtkontinuität zwischen beiden gehalten wird.

## 6. `prompts/` — projektweite Prompt-Bausteine

- [negative-prompts.md](prompts/negative-prompts.md) — was die Bild-/Videogenerierung vermeiden soll, in vier Blöcken: allgemein (kein Cartoon-/Monster-Look, keine Kontinuitätsfehler), sensible Inhalte (z. B. die Kind-Kollision in Sequenz 01 — angedeutet, nie explizit), Video-spezifisch (Bewegungsartefakte), figurenspezifisch (Jekyll/Hyde). Gilt für **alle** Sequenzen, wird nicht pro Sequenz neu geschrieben.
- [gemini-workflow.md](prompts/gemini-workflow.md) — konkrete Anleitung, wie die Bild-/Videoprompts mit **Gemini 2.5 Flash Image** (Referenzbild-Chat für Charakterkonsistenz) und **Veo** (Bild-zu-Video) umgesetzt werden, inkl. fertigem Negative-Block zum Anhängen (Gemini hat kein separates Negativfeld).

## 7. `assets/` — wohin generierte Dateien kommen

Vier Unterordner: `bilder/`, `video/`, `audio/`, `renders/`. Hier werden die tatsächlich generierten Ergebnisse abgelegt, wenn die Prompts aus `szenen/*/03-bildprompts.md` und `04-videoprompts.md` in einem AI-Tool ausgeführt werden. Der Inhalt dieser Ordner wird von Git ignoriert (siehe [.gitignore](.gitignore), Abschnitt "HYDE — projektspezifisch") — nur die Ordnerstruktur selbst bleibt über `.gitkeep`-Dateien im Repo sichtbar.

## 8. Workflow: eine neue Sequenz anlegen

1. Ordner `szenen/sequenz-NN/` anlegen (fortlaufende Nummer = Position im fertigen Film)
2. `00-sequenzbeschreibung.md` schreiben — Ort, Zeit, Wetter, Kurzbeschreibung, Motive, Ton
3. `01-drehbuch.md` — Szene ausformulieren, dabei bestehende Figuren/Orte aus `charakterbibel/` und `schauplaetze/` wiederverwenden statt neu zu erfinden
4. `02-shotlist.md` — Sequenz in Einstellungen zerlegen
5. `03-bildprompts.md` / `04-videoprompts.md` — pro Shot je einen Prompt, mit Verweis auf die passende Charakterbibel-Datei statt die Beschreibung auszuschreiben
6. Falls eine neue Figur oder ein neuer Ort auftaucht: neue Datei in `charakterbibel/` bzw. `schauplaetze/` anlegen (oder bestehenden Stub ausfüllen) und in [README.md](README.md) sowie hier in Abschnitt 4/5 eintragen

## 9. Wichtige Kontinuitätsregeln (projektweit)

- **Ein Darsteller für Jekyll/Hyde.** Nie als zwei verschiedene Gesichter behandeln — siehe [dr-henry-jekyll.md](charakterbibel/dr-henry-jekyll.md).
- **Die Jekyll-Hyde-Verbindung bleibt unausgesprochen**, bis eine dafür vorgesehene spätere Sequenz sie herstellt. Bei jeder neuen Sequenz vorher prüfen, ob sie versehentlich zu früh zu viel verrät.
- **Namen nur zeigen, wenn es die jeweilige Sequenz erlaubt** — in Sequenz 02 z. B. wird "Jekyll" bewusst nirgends sichtbar geschrieben oder ausgesprochen.
- **Alle Prompts und Dokumente sind auf Deutsch** (auf Wunsch umgestellt). Frühere Fassungen nutzten für Bild-/Videoprompts Englisch, da aktuelle AI-Tools damit oft zuverlässigere Ergebnisse liefern — bei schwachen Ergebnissen lohnt sich testweise die Rückübersetzung eines einzelnen Prompts ins Englische, statt das ganze Projekt umzustellen.
- **Negative Prompts aus [prompts/negative-prompts.md](prompts/negative-prompts.md) gelten immer**, unabhängig davon, ob eine Sequenz sie einzeln erwähnt.

## 10. Offene Punkte

- Physische Beschreibungen für Lanyon, Poole, Carew fehlen noch (folgen bei ihrem jeweiligen ersten Auftritt)
- Wann/wie die Jekyll-Hyde-Verbindung im Film konkret enthüllt wird, ist noch nicht als eigene Sequenz ausgearbeitet
- Sequenz 03 und folgende sind noch nicht geschrieben
