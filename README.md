# Abgabe Perzeptive und Intuitive Benutzungsschnittstellen Übungen Gruppe 

Befüllen Sie zur erfolgreichen Abgabe die folgenden Punkte in README.md 


| Vorname                         | Name                         | Matrikelnummer |
|---------------------------------|------------------------------|----------------|
| Marvin | Fink| 83270|
| Nicolas| Bohn | 85595|
| Jasmin-Alexandra|Rose|78683|
| Lena| Reiser| 82349|
| Stefanie| Sauer | 88416|

### Tools + SDKs etc. used

| Tool    | Version    |
|---------|------------|
| Unity   | 2019.2.6f1 LTS |
| Azure Kinect Samples Master    | -.-.- |
| Body Tracking SDK    | 1.1.0 |
| Kinect SDK    | 1.4.1 |


## Kurzbeschreibung der Idee (~250 Wörter)

"Pop-the-bubble" ist eine interaktive, gestengesteuerte Mehrspieler-Installation, die für den Einsatz in öffentlichen Räumen wie Museen oder auf Events konzipiert ist. Das Spiel nutzt die Azure Kinect-Kamera, um die Medienkompetenz der Teilnehmer auf spielerische Weise zu fördern, indem sie lernen, zwischen echten und gefälschten Nachrichten zu unterscheiden.

Der Ablauf ist vollständig automatisiert: Ein ansprechendes Video lockt Passanten an. Sobald Personen den Spielbereich betreten, startet ein kurzes Erklärungsvideo. Anschließend beginnt eine Registrierungsphase, in der sich bis zu sechs Spieler in zwei Teams aufteilen, indem sie sich auf der linken oder rechten Seite des Spielfelds positionieren. UI-Elemente in Form von Ampeln geben den Spielern dabei direktes Feedback.

Im Hauptspiel werden den Teams verschiedene Nachrichtenbilder präsentiert. Die Spieler stimmen über deren Echtheit ab, indem sie sich körperlich nach vorne (Zustimmung) oder nach hinten (Ablehnung) bewegen. Jede Entscheidung wird in Echtzeit auf der persönlichen Ampel des Spielers angezeigt. Punkte werden auf Basis der Team-Mehrheitsentscheidung vergeben und am Ende der Runden angezeigt. Nach einer Ergebnispräsentation startet das System automatisch neu und ist bereit für die nächste Gruppe. Das Projekt schafft so eine intuitive und lehrreiche Gruppenerfahrung ganz ohne Controller.

## Teaser Video 

https://youtu.be/L6sPcAemzd8

### Kurzanleitung

Die Steuerung des gesamten Spiels erfolgt ausschließlich durch Körperbewegung. Es gibt keinerlei Tastatur- oder Controller-Eingaben (wie WASD oder Vive-Controller).

Team-Auswahl: In der Registrierungsphase wählen die Spieler ihr Team, indem sie sich physisch auf die linke oder rechte Seite des Spielbereichs stellen.

Abstimmung: Im Hauptspiel stimmen die Spieler über die angezeigten Nachrichten ab, indem sie einen Schritt nach vorne (Zustimmung) oder nach hinten (Ablehnung) machen. Ihre jeweilige Position auf der Tiefenachse (Z-Achse) wird von der Kinect erfasst und als Stimme gewertet.
 
## Projektstruktur

```
 C:.
└───YourGitProject
    │   README.md // Sie befinden sich hier
    │
    ├───01-working-files // alle projektrelevanten Files (Assets, Codes, Libraries). Achten Sie darauf nichts unnötiges zu Committen. Die Subfolder Struktur ist ihnen überlassen. Bitte wie hier mit Anmerkungen versehen.
    └───02-documentation // Bilder & Grafiken vom Aufbau, sowie eine Readme zum einstellen von unity
```

