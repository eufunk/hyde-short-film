# HYDE

Cinematischer AI-Kurzfilm (Gothic/Psychological Horror, ca. 8 Minuten, Deutsch), lose inspiriert von Robert Louis Stevensons *Der seltsame Fall des Dr. Jekyll und Mr. Hyde*. Kein direktes Remake — im Fokus stehen Dualität, unterdrückte Wünsche, moralischer Verfall, Identitätsverlust und die Angst vor Kontrollverlust, übertragen auf ein modernes deutsches Setting.

**Weiterführende Dokus:** [ProjektGuide.md](ProjektGuide.md) (was liegt wo und wofür) · [HowTo.md](HowTo.md) (Schritt-für-Schritt-Anleitung für den Produktionsstart) · [Tools.md](Tools.md) (welche KI-Tools aktuell genutzt werden, Status)

## Fertige Sequenzen

### Sequenz 01 — „Die Tür"

📺 **[Video ansehen auf YouTube](https://youtu.be/owT0HCFpzfU)**

Die Eröffnungssequenz des Films, nach Kapitel 1 des Romans ("Die Geschichte von der Tür"). Notar Gabriel Utterson und sein Verwandter Richard Enfield gehen ihren gewohnten Abendspaziergang durch eine enge Gasse und bleiben vor einer unscheinbaren Stahltür stehen. Enfield erzählt zögernd, was er dort vor einigen Wochen nachts miterlebt hat: Ein kleiner, gehetzt wirkender Mann — Edward Hyde — kollidiert an einer Straßenkreuzung mit einem rennenden Mädchen, tritt im Weitergehen über sie hinweg, ohne auch nur nach unten zu blicken, und wird von aufgebrachten Passanten gestellt. Erst als er sich vor der Tür kurz umdreht, liegt sein Gesicht für einen Moment vollständig im Licht. Zurück in der Gegenwart nennt Enfield nur den Namen — die Verbindung zu Dr. Jekyll bleibt für Zuschauer und Figuren gleichermaßen unausgesprochen.

12 Shots, ca. 73 Sekunden. Details siehe [szenen/sequenz-01/](szenen/sequenz-01/).

| Edward Hyde | Gabriel John Utterson | Richard Enfield |
|---|---|---|
| ![Edward Hyde](showcase/sequenz-01/Edward%20Hyde.png) | ![Gabriel John Utterson](showcase/sequenz-01/Gabriel%20John%20Utterson.jpg) | ![Richard Enfield](showcase/sequenz-01/Richard%20Enfield.png) |

![Kollision an der Kreuzung](showcase/sequenz-01/Kollision.jpg)
*Der unabsichtliche Zusammenstoß an der Straßenkreuzung (Shot 06/07)*

## Projektstruktur

```
szenen/                    Eine Unterordner pro Sequenz
  sequenz-01/                 „Die Tür" — Eröffnung des Films. Utterson & Enfield, erste Hyde-Begegnung (nach Kap. 1). Jekyll wird hier noch nicht gezeigt.
    00-sequenzbeschreibung.md   Ort, Atmosphäre, Motive, Ton
    01-drehbuch.md               Szenenüberschrift, Handlung, Dialog
    02-shotlist.md                10–12 Einstellungen mit vollen Produktionsdetails
    03-bildprompts.md             AI-Bildprompts pro Shot
    04-videoprompts.md            AI-Videoprompts pro Shot
  sequenz-02/                 „Das Labor" — namenloser Mann (Jekyll) allein im Kellerlabor, keine Verbindung zu Hyde ausgesprochen
    00–04                        gleiches Schema wie Sequenz 01

charakterbibel/             Konsistenzbeschreibungen der Figuren (projektweit gültig)
  figuren-uebersicht.md       Besetzung: Rollen aus dem Roman, 5-Kern-Figuren-Entscheidung
  dr-henry-jekyll.md          Jekyll/Hyde — ein Darsteller, zwei Zustände (Hauptfigur)
  gabriel-utterson.md         Notar, erzählerischer Anker
  richard-enfield.md          Uttersons Verwandter, erster Zeuge von Hyde
  hastie-lanyon.md            Arzt, alter Freund Jekylls
  poole.md                    Butler (Stub)
  danvers-carew.md            Hydes Opfer (Stub)

schauplaetze/                Konsistenzbeschreibungen wiederkehrender Orte (projektweit gültig)
  institutsgebaeude.md        Institutsgebäude — Rückseite/Tür (Seq. 01) & Vorderseite (Seq. 02)

prompts/                    Wiederverwendbare, projektweite Prompt-Bausteine
  negative-prompts.md        Negative Prompts für Bild & Video
  gemini-workflow.md          Konkrete Anleitung: Prompts mit Gemini 2.5 Flash Image + Veo umsetzen

assets/                     Generierte Medien (kompletter Ordner nicht versioniert, siehe .gitignore)
  bilder/
  video/
  audio/
  renders/

showcase/                   Kuratierte Bilder für README & Co. — bewusst versioniert
  sequenz-01/
```

Neue Sequenzen folgen demselben Schema unter `szenen/sequenz-NN/`.
