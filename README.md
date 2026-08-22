# HYDE

Cinematischer AI-Kurzfilm (Gothic/Psychological Horror, ca. 8 Minuten, Deutsch), lose inspiriert von Robert Louis Stevensons *Der seltsame Fall des Dr. Jekyll und Mr. Hyde*. Kein direktes Remake — im Fokus stehen Dualität, unterdrückte Wünsche, moralischer Verfall, Identitätsverlust und die Angst vor Kontrollverlust, übertragen auf ein modernes deutsches Setting.

**Weiterführende Dokus:** [ProjektGuide.md](ProjektGuide.md) (was liegt wo und wofür) · [HowTo.md](HowTo.md) (Schritt-für-Schritt-Anleitung für den Produktionsstart) · [Tools.md](Tools.md) (welche KI-Tools aktuell genutzt werden, Status)

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

assets/                     Generierte Medien (nicht versioniert, siehe .gitignore)
  bilder/
  video/
  audio/
  renders/
```

Neue Sequenzen folgen demselben Schema unter `szenen/sequenz-NN/`.
