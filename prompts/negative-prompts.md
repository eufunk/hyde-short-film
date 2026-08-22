# Negative Prompts — projektweit

Diese Negative Prompts gelten für **alle** Bild- und Videogenerierungen im gesamten Film HYDE, nicht nur Sequenz 01. Ziel: fotorealistischer, hochwertiger psychologischer Horrorfilm-Look, kein typisches „KI-Video"-Erscheinungsbild.

## Allgemein (Bild & Video)

```
Cartoon, Anime, Illustration, Gemälde, Zeichnung, 3D-Render-Look, Videospielgrafik, Comicstil, Fantasy-Ästhetik, CGI-Monster, übertriebenes Horror-Make-up, Prothetik, leuchtende Augen, übernatürliches Kreaturendesign, übersättigte Farben, Neon-Horrorlicht, Rot/Grün-Genre-Beleuchtung, Gore, Blutspritzer, Jumpscare-Bildaufbau, zusätzliche Personen im Hintergrund, zufällige Passanten, Menschenmenge, nicht spezifizierte weitere Figuren, Text, Wasserzeichen, Untertitel, Logo, Bildunterschrift, UI-Elemente, Zeitstempel, Signatur

deformierte Hände, zusätzliche Finger, verwachsene Finger, zusätzliche Gliedmaßen, verzerrte Anatomie, verformtes Gesicht, asymmetrische Augen, plastikartige Hauttextur, wächserne Haut, puppenhaftes Gesicht, Uncanny-Valley-CGI-Gesicht, unpassende Gesichtszüge zwischen Einstellungen, wechselnde Frisur, wechselnde Kleidung zwischen Einstellungen, wechselndes Alter zwischen Einstellungen, inkonsistente Brille, inkonsistenter Ehering, inkonsistente Platzierung der Gesichtsnarbe

unscharf, niedrige Auflösung, wenig Detail, überbelichtet, unterbelichtet, flaches Licht, hartes unmotiviertes farbiges Licht, Tageslicht in einer Nachtszene, sichtbares modernes Smartphone, sofern nicht im Skript vorgesehen, anachronistische Requisiten, Produktplatzierung, Markenlogos, Stockfoto-Optik, generische Bürobeleuchtung, Studiohintergrund, Greenscreen-Kanten, künstliche Bokeh-Artefakte, übermäßige chromatische Aberration, überschärfte Kanten
```

## Zusätzlich bei Gewalt gegen Kinder oder andere sensible Inhalte (z. B. Sequenz 01)

```
grafische Gewaltdarstellung, sichtbare Verletzung, Blut, Nahaufnahme des Aufpralls, ausbeuterischer Bildaufbau, Verweilen auf dem Kind, Zeitlupe der Kollision, überlange Einstellungsdauer im Moment des Kontakts
```

Grundsatz: Der Vorfall wird immer angedeutet, nie explizit gezeigt — kurzer Schnitt vor/nach dem Kontaktmoment, Fokus auf Reaktion der Umstehenden statt auf die Handlung selbst.

## Zusätzlich für Video (Bewegung & Kontinuität)

```
schnelle, unruhige Kamerabewegung, Wackelkamera, Whip Pan, unmotivierter Zoom, verschmelzendes Gesicht, zerfließende Gesichtszüge, wechselnde Identität zwischen Frames, zuckende Gliedmaßen, unnatürlicher Gehzyklus, teleportierende Objekte, inkonsistente Beleuchtung zwischen Frames, Frame-Interpolations-Artefakte, verzerrender Hintergrund, Loop-Glitch, unrealistische Flüssigkeitssimulation, übertriebene Zeitlupe, unnatürliche Blinzelrate, ausdrucksloser Blick, roboterhafte Kopfbewegung
```

## Figuren-spezifisch (Dr. Henry Jekyll)

```
anderes Gesicht als Referenz, jüngeres Erscheinungsbild, andere Frisur, Bart, Tattoos, farbige Kontaktlinsen, legere Kleidung, zerrissene Kleidung, Verletzungs-Make-up, übermäßiger Schweiß, übertriebener Angstausdruck, comichafter Bösewicht-Ausdruck, fehlender Ehering, fehlende Brille, andere Brillenform, andere Mantelfarbe
```

## Zusätzlich für Edward Hyde (Erweiterung, keine Ersetzung der obigen Blöcke)

Hyde bleibt fotorealistisch und eindeutig menschlich — siehe [dr-henry-jekyll.md](../charakterbibel/dr-henry-jekyll.md#edward-hyde--dieselbe-figur-andere-präsenz). Diese Liste schließt zusätzlich jede Art von übernatürlichem oder monströsem Design aus, das bei generischen "Hyde"/"Mr. Hyde"-Prompts leicht hineinrutscht:

```
Monster, Dämon, Vampir, Zombie, Werwolf, Hörner, Reißzähne, Krallen, leuchtende Augen, übernatürliches Wesen, groteskes Gesicht, extreme Deformität, übertriebene Falten, Horror-Make-up, Fantasy-Kostüm, monströser Körper, muskulöser Körper, riesenhafter Mann, übertrieben böses Grinsen, künstliches Gesicht, übertrieben dramatischer Ausdruck, anderer Darsteller als das Jekyll-Referenzbild, langer Mantel, knielange oder längere Mantelform, Trenchcoat, Jackett mit Ärmeln, Sakko, Rennen, Sprinten, wildes oder chaotisches Laufen
```

## Hinweis zur Anwendung

Bei Tools mit separatem „Negative Prompt"-Feld (Midjourney `--no`, SDXL, Runway) direkt einfügen. Bei Tools ohne dediziertes Negativfeld (z. B. Gemini — siehe [gemini-workflow.md](gemini-workflow.md)) die Formulierungen positiv umkehren und in den Hauptprompt integrieren (z. B. „durchgehend konsistentes Gesicht, realistische Anatomie, natürliches Licht" statt der Negation).
