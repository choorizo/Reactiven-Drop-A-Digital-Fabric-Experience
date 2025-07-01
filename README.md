# Reactive-Drop-A-Digital-Fabric-Experience
Projektdokumentation 
eine Arbeit von Cristina,Fernandez, Laura Khoury, Joris Lustenberger


Reactive Drop – A Digital Fabric Experience


Konzeption
Reactive Drop ist ein interaktives Visual-Projekt, das als performative Erweiterung der Modemarke TRACK13 konzipiert wurde. Ziel war es, ein statisches Designbild (PNG) über einen Beamer auf eine Wand zu projizieren und dieses in Echtzeit auf äussere Einflüsse reagieren zu lassen. Die Reaktion erfolgt über zwei wesentliche Inputs: die Position und Bewegung der Hand im Raum sowie das Frequenzspektrum eines Musikstücks.

Der visuelle Output verbindet organische, fliessende Effekte mit konkreten Gestaltungsentscheidungen, die sowohl ästhetisch ansprechend als auch performativ steuerbar sind. So entsteht eine immersive Umgebung, in der Design, Bewegung und Sound verschmelzen.

Umsetzung & Prozess

Das Projekt wurde vollständig in TouchDesigner umgesetzt. Die Arbeit gliederte sich in drei zentrale Phasen:

1. Netzwerkaufbau:
   - Strukturierung des Netzwerks mit modularen Abschnitten für Input, Verarbeitung und Output.
   - Aufbau einer stabilen Kameraeingabe mit MediaPipe TOX für Handtracking.
   - Integration des Audioanalysepfads zur Steuerung der Bildhelligkeit.

2. Signalverarbeitung:
   - Handpositionen wurden über CHOPs in Positionsdaten umgewandelt.
   - Audio wurde über analyze2 und math3 in steuerbare Amplitudenwerte übersetzt.

3. Visuelle Effekte:
   - Farbänderung (HSVAdjust) basierend auf Handposition.
   - Bildverzerrung (Dent TOP) mit dynamischem Zentrum.
   - Radialer Blur-Effekt abhängig von Handposition.
   - Helligkeitsveränderung über Level TOP, gesteuert durch Musikintensität.

3. Gestalterische und Technische Entscheidungen
- PNG als Ausgangsbild: Hohe Auflösung, klare Farbflächen und kräftige Kontraste, passend zum Branding von TRACK13.
- Farbsteuerung über HSVAdjust: gezielte Nutzung des Hue-Offsets zur direkten Veränderung der Bildwirkung.
- Dent-Effekt: eingesetzt für organische Verformungen mit direkter räumlicher Reaktion auf Nutzer:innen.
- Radial Blur: zur Erzeugung eines visuell auffälligen Effekts, der sich um die Hand zentriert.
- Audioanalyse: in Echtzeit gekoppelt an die Helligkeit, um Sound visuell erfahrbar zu machen.
- Feedback-Strukturen: Für fliessende Übergänge und weiche Bewegungsmuster.
- Lag-CHOPs: zur Glättung von abrupten Handbewegungen und angenehmer Visual-Dynamik.


Anleitung zur Reproduktion
1. Starte TouchDesigner und öffne die Projektdatei (.toe).
2. Stelle sicher, dass die Kamera korrekt angeschlossen ist und das MediaPipe TOX (Hands) funktioniert.
3. Überprüfe die Handtracking-Komponente (hand_tracking, select1, select3). Diese steuern:
   - HueOffset im HSVAdjust.
   - Center des Dent TOPs.
   - Center des radialBlur TOPs.
4. Lade eine WAV-Datei in audiofilein1. Der Pfad kann angepasst werden.
5. Die Audioverarbeitung erfolgt über analyze2 → lag1 → math3 → null14.
   → Exportiere den Wert auf Level1.brightness.
6. Achte auf die Verbindung zwischen PNG_CREATIVE_Tshirtv01 → Level1 → transform1 → dent1 & radialBlur1 → comp1 → out1.
7. Output erfolgt über out1 in ein Window TOP.
8. Stelle im Window TOP den gewünschten Monitor ein (Beamer oder externer Bildschirm).
9. Aktiviere den Perform Mode (linke obere Ecke im Output-Fenster), um den Vollbildmodus zu starten.
10. Für reibungslose Wiedergabe TOX-Dateien ggf. lokal einbinden.



Das Projekt wurde so aufgeteilt:

Cristina:
- Gestaltung des PNG-Designs (Farben, Komposition, Kontrast)
- Entwicklung des Radial Blur und Feedback-Designs
- Testdurchläufe mit verschiedenen Visual-Stilen

Laura:
- Einrichtung von MediaPipe Hands und CHOP-Strukturen
- Konfiguration von Export Expressions für Level TOP
- Audioanalyse und Routing in TouchDesigner

Joris:
- Aufbau des TouchDesigner Netzwerks mit Fokus auf CHOP/TOP-Integration
- Perform Mode Setup, Fensterzuweisung, Live-Test mit Beamer
- Dokumentation, Netzwerkstrukturierung und Debugging

Learnings:
- Export Expressions wie op(‚null1‘)[‚chan1‘] müssen präzise gesetzt werden.
- MediaPipe benötigt manchmal manuelles Aktivieren und Pfadanpassungen.
- CHOP Navigation ist entscheidend für stabile visuelle Reaktionen.
- Die Kombination von Blur, Feedback und Dent liefert sehr organische Ergebnisse.
- Sound als Steuerungselement für visuelles Empfinden ist extrem wirkungsvoll.

Es hat uns sehr Spass gemacht dieses Projekt zu realisieren und werden es sicher an einem Event von TRACK13 umsetzen.

Cristina Fernandez, Laura Khoury, Joris Lustenberger
