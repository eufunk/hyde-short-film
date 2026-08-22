# Gemini-Workflow — Bild- und Videogenerierung

Konkrete Anleitung, wie die Prompts aus `szenen/*/03-bildprompts.md` und `04-videoprompts.md` mit **Gemini 2.5 Flash Image** ("Nano Banana") und **Veo** umgesetzt werden. Ergänzt [`HowTo.md`](../HowTo.md) um die tool-spezifischen Details.

**Hinweis zum aktuellen Werkzeugstand:** Der Video-Teil dieses Dokuments (Veo) ist die ursprünglich vorgesehene Anleitung. Tatsächlich für die Charaktertests genutzt wurde bisher **DeeVid AI**, dessen Budget aktuell aufgebraucht ist — siehe [`Tools.md`](../Tools.md) für den jeweils aktuellen Stand und die Suche nach einem Ersatz-Tool für die Sequenz-Shot-Produktion.

## Warum Gemini 2.5 Flash Image

Die Stärke gegenüber Midjourney/SDXL für dieses Projekt: Referenzbild-basierte Konsistenz ohne `--cref`-Syntax oder LoRA-Training. Ein Referenzbild wird in der Konversation gehalten, und Folgebilder werden explizit als "dieselbe Person, neue Szene" angefordert — genau das Problem, das in [figuren-uebersicht.md](../charakterbibel/figuren-uebersicht.md) als größte Hürde bei KI-generierten Filmen benannt wird.

## Referenzbild-Workflow (Charakterkonsistenz)

1. **Einmal pro Figur** ein Referenzbild erzeugen — Prompt aus der jeweiligen Charakterbibel zusammensetzen (Abschnitt "Physische Beschreibung" + "Kleidung"-Prompt-Fragment). Bei Jekyll/Hyde beide Zustände einzeln erzeugen (siehe [dr-henry-jekyll.md](../charakterbibel/dr-henry-jekyll.md)).
2. Dieses Bild **im selben Chat** behalten — nicht in einem neuen Chat weiterarbeiten, sonst geht der Referenzkontext verloren.
3. Für jeden Shot den Prompt aus `03-bildprompts.md` einfügen und voranstellen:
   > „Verwende exakt dieselbe Person wie im Referenzbild oben (gleiches Gesicht, gleicher Darsteller, gleiche Statur) — erzeuge keine andere Person. Generiere jetzt: [Shot-Prompt]"
4. Wirkt ein Ergebnis leicht daneben (z. B. Bartschatten falsch, Brille anders): **im selben Chat nachsteuern** ("anpassen: etwas weniger Bartschatten, alles andere identisch lassen") statt vollständig neu zu generieren. Das erhält die Konsistenz besser als ein Neustart.
5. Pro Figur eine eigene Chat-Konversation offen halten (z. B. ein Chat für Jekyll/Hyde, einer für Utterson, einer für Enfield), damit sich die Referenzbilder nicht gegenseitig überschreiben.

## Kein Negative-Prompt-Feld — inline anhängen

Gemini hat kein separates Negativfeld wie Midjourney (`--no`) oder SDXL. Diesen kompakten, positiv formulierten Block an **jeden** Prompt anhängen (verdichtet aus [negative-prompts.md](negative-prompts.md)):

> Stil: fotorealistisches, kinoreifes Filmstandbild, natürliche menschliche Anatomie, ein durchgehend konsistentes realistisches Gesicht, natürliches Licht, dezentes Filmkorn. Vermeiden: Cartoon- oder Anime-Stil, CGI-Monster- oder Prothetik-Effekte, leuchtende Augen, zusätzliche oder zufällige Personen im Hintergrund, Text, Wasserzeichen, Logo, überschärfte oder plastikartig wirkende Haut.

**Zusätzlich bei Hyde-Shots** anhängen:
> Derselbe Darsteller und dasselbe Gesicht wie im Jekyll-Referenzbild — der Unterschied wird ausschließlich über Körperhaltung, Ausdruck und Licht ausgedrückt, nicht über ein anderes Gesicht oder Monster-Make-up.

**Zusätzlich bei sensiblen Shots** (z. B. die Kind-Kollision in Sequenz 01, Shots 06–07) anhängen:
> Zeige keine grafische Gewalt, sichtbare Verletzungen oder Blut — deute den Moment über Bildausschnitt und Timing an, zeige ihn nie explizit.

## Von Bild zu Video: Veo

1. Fertiges Gemini-Bild als Referenz-/Startframe in Veo hochladen (Gemini-App „Video erstellen" bzw. Flow, oder Vertex AI).
2. Den passenden Prompt aus `04-videoprompts.md` unverändert als Bewegungsbeschreibung einfügen — diese Prompts beschreiben bewusst nur Bewegung/Veränderung, nicht das Bild selbst, weil das Startbild diese Information bereits liefert.
3. Erzeugten Clip in [`assets/video/`](../assets/video/) ablegen (von Git ignoriert, siehe [.gitignore](../.gitignore)).

## Praktischer Ablauf pro Shot (Kurzfassung)

```
1. Prompt aus 03-bildprompts.md kopieren
2. Im Referenz-Chat der Figur einfügen: Referenzbild-Hinweis + Shot-Prompt + Negative-Block
3. Ergebnis gegen Charakterbibel prüfen, bei Abweichung im selben Chat nachsteuern
4. Bild in Veo laden, passenden Prompt aus 04-videoprompts.md einfügen
5. Clip in assets/video/ speichern
```
