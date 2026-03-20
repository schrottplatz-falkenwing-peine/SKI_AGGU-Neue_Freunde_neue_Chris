# 🤖 AGENTS.md — KI-Agenten-Anweisungen

> Dieses Dokument beschreibt, wie KI-Agenten (z. B. Claude, GPT, Codex) dieses Repository verstehen, erweitern und pflegen sollen. Es definiert Workflows, Qualitätsstandards und strikte Regeln für automatisierte Beiträge.

---

## 🎯 Projektziel (für Agenten)

Dieses Repository sammelt **alle verfügbaren, verifizierbaren Informationen** über den deutschen Rapper **Ski Aggu** (bürgerlich: August Jean Diederich, \*03.11.1997 in Berlin). Der Fokus liegt auf:

1. **Vollständigkeit** der Diskografie (alle Releases, alle Tracks)
2. **Evidenzbasierung** (jede Aussage benötigt eine Quellenangabe)
3. **Aktualität** (neue Releases sollen zeitnah eingetragen werden)
4. **Konsistenz** der Dateistruktur und des Formats

---

## 📋 Inhaltsverzeichnis

- [Aufgabentypen](#aufgabentypen)
- [Qualitätsregeln](#qualitätsregeln)
- [Verzeichnisstruktur & Formatvorlagen](#verzeichnisstruktur--formatvorlagen)
- [Quellen-Hierarchie](#quellen-hierarchie)
- [Verbotene Aktionen](#verbotene-aktionen)
- [Workflows](#workflows)
- [Songtext-Richtlinien](#songtext-richtlinien)
- [Bekannte Datenquellen](#bekannte-datenquellen)

---

## Aufgabentypen

Ein Agent kann mit folgenden Aufgaben betraut werden:

### A — Neue Release einpflegen
Neue Single, Album oder Feature-Auftritt dokumentieren.

**Input:** Release-Name, Datum, Plattform-URL  
**Output:** Neue Datei(en) im richtigen Unterverzeichnis  
**Pflichtfelder:** Datum, Label, Features, Produzent (falls bekannt), Chartdaten (falls vorhanden), Quellenangabe

### B — Chartdaten aktualisieren
Aktuelle oder historische Chart-Platzierungen nachtragen.

**Input:** Titel, Land (DE/AT/CH), Höchstplatzierung, Anzahl Chartwochen  
**Output:** Aktualisierte Zeile in `charts/single_charts.md` oder `charts/album_charts.md`  
**Pflichtfelder:** Datum der Charteintragung, Quelle (offizielle Charts-Website)

### C — Songtext verlinken
Songtexte nicht kopieren, sondern auf lizenzierte Quellen verlinken.

**Input:** Songtitel  
**Output:** Markdown-Datei in `lyrics/` mit Metadaten und Link zu Genius/AZLyrics

### D — Biografische Information ergänzen
Neues Faktum (Interview-Aussage, Award, Konzert) hinzufügen.

**Input:** Faktum, Quelle, Datum  
**Output:** Eintrag in der entsprechenden Datei unter `biography/` oder `press/`

### E — Qualitätsprüfung
Bestehende Einträge auf fehlende Quellen, Tippfehler und Formatfehler prüfen.

**Output:** Pull-Request-Kommentar oder Liste in `docs/changelog.md`

---

## Qualitätsregeln

> **Alle Regeln sind bindend. Kein Eintrag ohne Quelle.**

### R-01 — Evidenzpflicht
Jede sachliche Aussage **muss** mit mindestens einer Quellenangabe versehen sein. Format:

```markdown
> Quelle: [Seitenname](URL), abgerufen am YYYY-MM-DD
```

### R-02 — Datumsformat
Alle Datumsangaben im ISO-Format: `YYYY-MM-DD`

```markdown
✅ 2022-12-01
❌ 01.12.2022
❌ Dezember 2022
```

### R-03 — Dateinamen
Kleinbuchstaben, Bindestriche, kein Leerzeichen, kein Sonderzeichen:

```
✅ 2022_party-sahne.md
❌ Party Sahne.md
❌ 2022_party_sahne (mit Umlauten).md
```

### R-04 — Titelschreibweise
Songtitel und Albumtitel werden **exakt wie vom Künstler veröffentlicht** geschrieben, inklusive Kleinbuchstaben, Sonderzeichen und Emojis im Fließtext. In Dateinamen werden Sonderzeichen nach R-03 normalisiert.

```markdown
✅ Album: "denk mal drüber nach…"    (Original-Schreibweise im Text)
✅ Datei: 2023_denk-mal-drueber-nach/ (normalisiert im Dateisystem)
```

### R-05 — Keine Spekulation
Unbestätigte Informationen (Gerüchte, Social-Media-Posts ohne offizielle Bestätigung) dürfen **nicht** ohne explizite Kennzeichnung eingetragen werden:

```markdown
> ⚠️ UNBESTÄTIGT: [Beschreibung] — Quelle: [URL], Stand: YYYY-MM-DD
```

### R-06 — Keine Songtexte im Repository
Songtexte dürfen **nicht vollständig** in das Repository kopiert werden (Urheberrecht). Erlaubt sind:
- Links zu Genius.com, AZLyrics.com oder ähnlichen Plattformen
- Kurze Zitate (max. 2 Zeilen) mit Quellenangabe für analytische Zwecke

### R-07 — Strukturkonsistenz
Jeder neue Release erhält eine eigene Datei. Die Ordnerstruktur ist einzuhalten. Keine neuen Top-Level-Verzeichnisse ohne Genehmigung durch Maintainer.

### R-08 — Changelog-Pflicht
Jede Änderung wird in `docs/changelog.md` eingetragen:

```markdown
## YYYY-MM-DD
- [Agent/Person]: [Aktion] — [Datei] — Quelle: [URL]
```

---

## Verzeichnisstruktur & Formatvorlagen

### Vorlage: Single-Datei

Pfad: `discography/singles/YYYY/YYYY-MM-DD_titel.md`

```markdown
# [Songtitel]

| Feld | Wert |
|------|------|
| **Typ** | Single |
| **Veröffentlichungsdatum** | YYYY-MM-DD |
| **Label** | jungeratze / UMG |
| **Features** | [Künstlername] (falls vorhanden) |
| **Produzent(en)** | [Name] (falls bekannt) |
| **Album** | [Albumtitel] / Standalone |
| **Laufzeit** | MM:SS |

## Chartplatzierungen

| Land | Höchstplatzierung | Chartwochen | Auszeichnung |
|------|-------------------|-------------|--------------|
| 🇩🇪 DE | # | — | — |
| 🇦🇹 AT | # | — | — |
| 🇨🇭 CH | # | — | — |

## Links

- **YouTube (Official Video):** [Link]
- **Spotify:** [Link]
- **Genius (Lyrics):** [Link]

## Quellen

- [Quellenname](URL), abgerufen am YYYY-MM-DD
```

---

### Vorlage: Album-Info-Datei

Pfad: `discography/albums/YYYY_albumtitel/album_info.md`

```markdown
# [Albumtitel]

| Feld | Wert |
|------|------|
| **Typ** | Studioalbum / Mixtape |
| **Veröffentlichungsdatum** | YYYY-MM-DD |
| **Label** | jungeratze / UMG |
| **Format(e)** | Digital, Vinyl (Farbe) |
| **Anzahl Tracks** | # |
| **Gesamtlaufzeit** | MM:SS |
| **Barcode (Vinyl)** | [falls bekannt] |

## Chartplatzierungen

| Land | Höchstplatzierung | Chartwochen | Auszeichnung |
|------|-------------------|-------------|--------------|
| 🇩🇪 DE | # | — | — |
| 🇦🇹 AT | # | — | — |
| 🇨🇭 CH | # | — | — |

## Rezensionen

| Medium | Wertung | Datum | Link |
|--------|---------|-------|------|
| laut.de | 4/5 | YYYY-MM-DD | [Link] |
| plattentests.de | — | YYYY-MM-DD | [Link] |

## Quellen

- [Quellenname](URL), abgerufen am YYYY-MM-DD
```

---

### Vorlage: Tracklist-Datei

Pfad: `discography/albums/YYYY_albumtitel/tracklist.md`

```markdown
# Tracklist: [Albumtitel]

> Quelle: [Quellen-URL], abgerufen am YYYY-MM-DD

| # | Titel | Features | Produzent | Laufzeit | Single-VÖ |
|---|-------|----------|-----------|----------|-----------|
| 1 | Titel | feat. X | Prod. Y | MM:SS | YYYY-MM-DD / — |
| … | … | … | … | … | … |
```

---

### Vorlage: Feature-Eintrag

Pfad: `discography/features/features_list.md`

```markdown
| Datum | Titel | Hauptkünstler | Ski Aggus Rolle | Album des Hauptkünstlers | Charts DE | Quelle |
|-------|-------|---------------|-----------------|--------------------------|-----------|--------|
| YYYY-MM-DD | [Titel] | [Künstler] | feat. / Gastauftritt | [Album] | #X | [URL] |
```

---

## Quellen-Hierarchie

Agenten sollen Quellen in folgender Priorität verwenden:

| Priorität | Quelle | Verwendung |
|-----------|--------|------------|
| 1 | Offizielle Websites (universal-music.de, offizielle Social Media) | Primärquelle für Releases |
| 2 | Wikipedia DE mit Belegen | Biografisches, Charts |
| 3 | MusicBrainz, Discogs | Technische Release-Daten |
| 4 | Offizielle Charts (offiziellecharts.de, austriancharts.at, hitparade.ch) | Chartdaten |
| 5 | laut.de, plattentests.de, hiphop.de | Rezensionen & Kontextinformationen |
| 6 | Genius.com | Songtexte (nur verlinken, nicht kopieren) |
| 7 | Watson, Tagesspiegel, Zeit Online | Interviews, Pressezitate |

❌ **Nicht verwenden:** Fansites ohne Quellenangabe, Reddit, TikTok-Kommentare

---

## Verbotene Aktionen

Ein Agent darf **niemals**:

- [ ] Songtexte vollständig in das Repository kopieren
- [ ] Aussagen ohne Quellenangabe eintragen
- [ ] Albumcover oder Fotos in das Repository hochladen (Urheberrecht)
- [ ] Persönliche Informationen (Wohnadresse, private Beziehungen) eintragen
- [ ] Spekulationen als Fakten darstellen
- [ ] Bestehendes Quellenverzeichnis löschen oder überschreiben
- [ ] Dateien außerhalb der definierten Verzeichnisstruktur anlegen
- [ ] Chartdaten ohne Angabe des Erhebungszeitraums eintragen

---

## Workflows

### Workflow 1: Neue Single eintragen

```
1. Quelle(n) identifizieren (offizielle Ankündigung, Streaming-Plattform)
2. Dateiname bestimmen: discography/singles/YYYY/YYYY-MM-DD_[normalisierter-titel].md
3. Vorlage ausfüllen (alle Pflichtfelder)
4. Falls Single zu einem Album gehört: tracklist.md des Albums aktualisieren
5. charts/single_charts.md aktualisieren (auch wenn noch keine Charts vorhanden: Zeile anlegen)
6. docs/changelog.md aktualisieren
7. README.md-Tabellen aktualisieren (falls Top-Single)
```

### Workflow 2: Neues Album eintragen

```
1. Offizielle Ankündigung verifizieren
2. Verzeichnis anlegen: discography/albums/YYYY_[albumtitel]/
3. album_info.md anlegen (Vorlage)
4. tracklist.md anlegen (alle Tracks mit verfügbaren Metadaten)
5. lyrics/-Verzeichnis anlegen: lyrics/albums/YYYY_[albumtitel]/
6. Für jeden Track eine Lyrics-Datei mit Genius-Link anlegen
7. charts/album_charts.md aktualisieren
8. README.md Album-Tabelle aktualisieren
9. docs/changelog.md aktualisieren
```

### Workflow 3: Feature-Auftritt dokumentieren

```
1. Track verifizieren (Hauptkünstler, Erscheinungsdatum)
2. features/features_list.md: neue Zeile eintragen
3. Falls Charts-Platzierung: charts/single_charts.md aktualisieren
4. docs/changelog.md aktualisieren
```

### Workflow 4: Periodicsche Qualitätsprüfung

```
1. Alle Einträge ohne Quellenangabe identifizieren (grep für fehlende "Quelle:"-Tags)
2. Alle veralteten URLs auf Erreichbarkeit prüfen
3. Wikipedia-Diskografie-Seite auf neue Einträge prüfen
4. MusicBrainz auf neue Releases prüfen
5. Bericht in docs/changelog.md erstellen
```

---

## Songtext-Richtlinien

Da Songtexte urheberrechtlich geschützt sind, gelten folgende Regeln:

### Erlaubt ✅
```markdown
## Songtext

> **Offizieller Songtext:** [Genius – "Party Sahne"](https://genius.com/Ski-aggu-party-sahne-lyrics)

### Analytische Kurznotizen
- Thema: Nachtleben, Berlin-Wilmersdorf
- Sprachstil: Wortwitz, Gen-Z-Humor, Berliner Slang
- Referenzen: [Kotti (Kottbusser Tor), Wilmersdorf]
- Produzenten-Sample: basiert auf "Jerk It Out" von Caesars (2002)
```

### Verboten ❌
```markdown
## Songtext (VERBOTEN)
Vers 1:
[Vollständiger Songtext...]
```

---

## Bekannte Datenquellen

### Offizielle Quellen
| Plattform | URL | Inhalte |
|-----------|-----|---------|
| Universal Music DE | https://www.universal-music.de/ski-aggu/ | Offizielle Releases |
| Spotify | https://open.spotify.com/artist/[ID] | Streaming, Tracklists |
| YouTube (Kanal Aggu31) | https://www.youtube.com/@Aggu31 | Musikvideos mit Erscheinungsdatum |

### Enzyklopädische Quellen
| Plattform | URL | Inhalte |
|-----------|-----|---------|
| Wikipedia DE | https://de.wikipedia.org/wiki/Ski_Aggu | Biografie, Diskografie |
| Wikipedia DE Diskografie | https://de.wikipedia.org/wiki/Ski_Aggu/Diskografie | Vollständige Diskografie mit Charts |
| MusicBrainz | https://musicbrainz.org/artist/f1d46f29-34fd-4cd5-959f-0a213e1f1d8e | Release-Metadaten |
| Discogs | https://www.discogs.com/de/artist/12874346-Ski-Aggu | Vinyl-Releases, Tracklists |

### Charts-Quellen
| Land | URL |
|------|-----|
| 🇩🇪 Deutschland | https://www.offiziellecharts.de |
| 🇦🇹 Österreich | https://austriancharts.at/showinterpret.asp?interpret=Ski+Aggu |
| 🇨🇭 Schweiz | https://hitparade.ch/artist/Ski-Aggu |

### Presse & Kritik
| Medium | URL |
|--------|-----|
| laut.de | https://laut.de/Ski-Aggu |
| plattentests.de | https://www.plattentests.de |
| hiphop.de | https://hiphop.de |
| Genius (Lyrics) | https://genius.com/artists/Ski-aggu |

---

## Versionierung dieses Dokuments

| Version | Datum | Änderung |
|---------|-------|----------|
| 1.0 | 2026-03-20 | Initiales Dokument erstellt |

---

*Dieses Dokument ist für KI-Agenten und menschliche Beitragende gleichsam bindend.*
