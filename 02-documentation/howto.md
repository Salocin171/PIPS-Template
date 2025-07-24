# Dein Unity-Projekt: Fake News Erkennungsspiel

Willkommen beim Fake News Erkennungsspiel! Dieses Projekt wurde entwickelt, um Spieler auf spielerische Weise für das Erkennen von echten und gefälschten Nachrichten zu sensibilisieren, indem es Kinect-Interaktionen nutzt.

Diese `README.md` Datei führt dich durch die Schritte, um das Spiel in Unity einzurichten und zu starten.

---

## Inhaltsverzeichnis

1.  [Voraussetzungen](#1-voraussetzungen)
2.  [Projekt einrichten](#2-projekt-einrichten)
    * [2.1 Neues Unity-Projekt erstellen](#21-neues-unity-projekt-erstellen)
    * [2.2 Dateien importieren](#22-dateien-importieren)
    * [2.3 Externe Bibliotheken (Kinect Azure SDK)](#23-externe-bibliotheken-kinect-azure-sdk)
3.  [Szenen konfigurieren](#3-szenen-konfigurieren)
    * [3.1 Szenenübersicht](#31-szenenübersicht)
    * [3.2 `AttractScene` konfigurieren](#32-attractscene-konfigurieren)
    * [3.3 `PlayerRegistrationScene` konfigurieren](#33-playerregistrationscene-konfigurieren)
    * [3.4 `MainGameScene` konfigurieren](#34-maingamescene-konfigurieren)
    * [3.5 `OffboardingScene` konfigurieren](#35-offboardingscene-konfigurieren)
4.  [Assets hinzufügen](#4-assets-hinzufügen)
    * [4.1 Bilder (News Sprites)](#41-bilder-news-sprites)
    * [4.2 Videos](#42-videos)
    * [4.3 Sound (Hintergrundmusik)](#43-sound-hintergrundmusik)
    * [4.4 UI-Elemente](#44-ui-elemente)
5.  [Projekt testen und bauen](#5-projekt-testen-und-bauen)
6.  [Bekannte Probleme & Fehlerbehebung](#6-bekannte-probleme--fehlerbehebung)

---

## 1. Voraussetzungen

Bevor du beginnst, stelle sicher, dass du Folgendes installiert hast:

* **Unity Hub & Unity Editor:** Empfohlen ist Unity 2019.2.x LTS.
* **Azure Kinect SDK:** Du benötigst die Treiber und das SDK für deine Azure Kinect Kamera. Installiere es von der offiziellen Microsoft-Website. https://github.com/microsoft/Azure-Kinect-Sensor-SDK/blob/develop/docs/usage.md
* **Azure Kinect Body Tracking SDK:** Ebenfalls von der offiziellen Microsoft-Website herunterladen und installieren. https://www.microsoft.com/en-eg/download/details.aspx?id=102901
* **Visual Studio (mit Unity-Entwicklungslast):** Für die Bearbeitung der C#-Skripte.
* **Text Mesh Pro:** Normalerweise in Unity enthalten, aber falls nicht, importiere es über `Window > TextMeshPro > Import TMP Essential Resources`.


https://www.youtube.com/watch?v=PGsxP6Yoq9I&ab_channel=Corrie
---

## 2. Projekt einrichten

### 2.1 Neues Unity-Projekt erstellen

1.  Öffne **Unity Hub**.
2.  Klicke auf **"New project"**.
3.  Wähle ein **"3D Core"** Template.
4.  Gib einen aussagekräftigen **"Project Name"** (z.B. `FakeNewsGame`) und einen **"Location"** an.
5.  Klicke auf **"Create project"**.

### 2.2 Dateien importieren

Sobald das neue Projekt geöffnet ist:

1.  Navigiere im Unity-Editor zum `Assets`-Fenster (unten links).
2.  Erstelle die folgenden Ordnerstrukturen im `Assets`-Ordner:
    * `Assets/Scripts`
    * `Assets/Scenes`
    * `Assets/Resources/FakeNews`
    * `Assets/Resources/FakeNewsFeedback`
    * `Assets/Resources/RealNews`
    * `Assets/Resources/RealNewsFeedback`
    * `Assets/Videos`
    * `Assets/Audio`
    * `Assets/Prefabs`
    * `Assets/Textures/UI`
    * `Assets/TextMeshPro` (Dieser Ordner wird erstellt, wenn du TextMeshPro Essential Resources importierst)

3.  Kopiere alle bereitgestellten `.cs`-Skriptdateien in den `Assets/Scripts`-Ordner deines Unity-Projekts.
    * `AttractSceneController.cs`
    * `BackgroundData.cs`
    * `BackgroundDataProvider.cs`
    * `BackgroundMusicManager.cs`
    * `Body.cs`
    * `Constants.cs`
    * `CustomColors.cs`
    * `GameResultData.cs`
    * `GetPelvisPosition.cs`
    * `KinectController.cs`
    * `NewsController.cs`
    * `PlayerGameData.cs`
    * `PlayerRegistrationController.cs`
    * `SkeletalTrackingProvider.cs`
    * `OffboardingController.cs`

### 2.3 Externe Bibliotheken (Kinect Azure SDK)

Die Kinect-Integration erfordert spezielle Unity-Pakete.

1.  **Herunterladen des Azure Kinect Unity Pakets:**
    * Lade das aktuelle Azure Kinect Unity-Paket (z.B. `Azure-Kinect-Samples-Unity-X.X.X.zip`) von der offiziellen Microsoft Azure Kinect GitHub-Seite herunter: [https://github.com/microsoft/Azure-Kinect-Samples/releases](https://github.com/microsoft/Azure-Kinect-Samples/releases)
    * Entpacke die ZIP-Datei. Du findest darin eine `.unitypackage`-Datei (z.B. `AzureKinectUnity.unitypackage`).

2.  **Importieren in Unity:**
    * Gehe in Unity zu `Assets` > `Import Package` > `Custom Package...`
    * Navigiere zu der entpackten `.unitypackage`-Datei und wähle sie aus.
    * Ein Fenster öffnet sich mit allen zu importierenden Assets. Stelle sicher, dass **alle** Elemente ausgewählt sind.
    * Klicke auf **"Import"**.

---

## 3. Szenen konfigurieren

Du benötigst vier Hauptszenen für das Spiel: `AttractScene`, `PlayerRegistrationScene`, `MainGameScene` und `OffboardingScene`.

### 3.1 Szenenübersicht

1.  Gehe zu `File > New Scene`. Wähle "Basic (Built-in)". Speichere die Szene unter `Assets/Scenes/AttractScene.unity`.
2.  Wiederhole dies für:
    * `Assets/Scenes/PlayerRegistrationScene.unity`
    * `Assets/Scenes/MainGameScene.unity`
    * `Assets/Scenes/OffboardingScene.unity`

3.  **Build Settings:**
    * Gehe zu `File > Build Settings...`
    * Ziehe deine Szenen in dieser Reihenfolge in die "Scenes In Build"-Liste:
        1.  `AttractScene`
        2.  `PlayerRegistrationScene`
        3.  `MainGameScene`
        4.  `OffboardingScene`
    * Schließe die Build Settings.

### 3.2 `AttractScene` konfigurieren

Diese Szene spielt ein Loop-Video ab und startet ein Erklärvideo, wenn ein Spieler erkannt wird.

1.  Öffne die Szene `AttractScene.unity`.
2.  Erstelle ein leeres GameObject: `GameObject > Create Empty`. Benenne es `AttractSceneController`.
3.  Ziehe das Skript `AttractSceneController.cs` auf dieses GameObject im Inspector.
4.  Füge dem `AttractSceneController` GameObject eine **Video Player** Komponente hinzu: `Add Component > Video > Video Player`.
5.  Konfiguriere im Inspector des `AttractSceneController`:
    * **Video Player:** Ziehe die `Video Player`-Komponente von diesem GameObject in den `Video Player`-Slot des Skripts.
    * **Loop Video:** Ziehe hier dein Loop-Hintergrundvideo rein (siehe [4.2 Videos](#42-videos)).
    * **Explanation Video:** Ziehe hier dein Erklärvideo rein (siehe [4.2 Videos](#42-videos)).
    * **Player Registration Scene Name:** Stelle sicher, dass dies auf `PlayerRegistrationScene` gesetzt ist.
6.  **Kamera:** Stelle sicher, dass die Kamera in der Szene richtig positioniert ist, um das Video anzuzeigen. Es kann hilfreich sein, eine UI Canvas mit einem Raw Image zu verwenden, das durch den Video Player gerendert wird.

### 3.3 `PlayerRegistrationScene` konfigurieren

Diese Szene dient der Registrierung der Spieler und ihrer Teamzuweisung.

1.  Öffne die Szene `PlayerRegistrationScene.unity`.
2.  Erstelle ein leeres GameObject: `GameObject > Create Empty`. Benenne es `PlayerRegistrationController`.
3.  Ziehe das Skript `PlayerRegistrationController.cs` auf dieses GameObject.
4.  Füge dem `PlayerRegistrationController` GameObject eine **Video Player** Komponente hinzu (für den Hintergrund).
5.  Konfiguriere im Inspector des `PlayerRegistrationController`:
    * **Background Video Player:** Ziehe die `Video Player`-Komponente von diesem GameObject in den Slot.
    * **Background Video Clip:** Ziehe hier ein passendes Hintergrundvideo rein.
    * **Main Game Scene Name:** Stelle sicher, dass dies auf `MainGameScene` gesetzt ist.
    * **Player Prefab:** Erstelle ein einfaches 3D-Objekt (z.B. eine Kugel) als Prefab im Ordner `Assets/Prefabs`. Benenne es z.B. `PlayerVisual`. Ziehe dieses Prefab in den Slot.
    * **Left Team Parent / Right Team Parent:** Erstelle leere GameObjects in der Szene (z.B. `LeftTeamVisuals` und `RightTeamVisuals`), um die visuellen Darstellungen der Spieler zu gruppieren. Ziehe sie in die Slots.
    * **Left Players Count Text / Right Players Count Text:** Erstelle UI TextMeshPro-Textfelder für die Anzeige der Spieleranzahl pro Team. Ziehe sie in die Slots.
    * **Left Team Score Text / Right Team Score Text:** Auch hier TextMeshPro-Textfelder für die temporäre Anzeige von Punkten während der Registrierung.
    * **Start Game Button:** Füge einen Button in dein UI ein und ziehe ihn hierher. Weise im Button-Event `OnClick()` die Funktion `PlayerRegistrationController.StartGame()` zu.
    * **Player Status Texts (Array):** Erstelle 6 TextMeshPro-Textfelder (oder mehr, je nach maximaler Spielerzahl) für die individuellen Spielerstatus-Anzeigen und ziehe sie in das Array.
    * **Ampel Parents Left/Right:** Erstelle 3 (oder mehr) leere GameObjects pro Seite (z.B. `AmpelLeft1`, `AmpelLeft2`, `AmpelLeft3` und `AmpelRight1`, `AmpelRight2`, `AmpelRight3`) und ziehe diese in die jeweiligen Arrays. In diese Eltern-Objekte werden später die Ampel-Icons (Grau, Grün, Gelb, Rot) als Kinder eingefügt und je nach Status ein- oder ausgeblendet.

### 3.4 `MainGameScene` konfigurieren

Dies ist die Hauptszene, in der das Spielgeschehen stattfindet.

1.  Öffne die Szene `MainGameScene.unity`.
2.  Erstelle ein leeres GameObject: `GameObject > Create Empty`. Benenne es `NewsController`.
3.  Ziehe das Skript `NewsController.cs` auf dieses GameObject.
4.  Füge dem `NewsController` GameObject eine **Video Player** Komponente hinzu (für den Hintergrund).
5.  Konfiguriere im Inspector des `NewsController`:
    * **News Image Element:** Erstelle ein UI `Image` GameObject (z.B. `NewsDisplay`) und ziehe es hierher. Dies zeigt die Nachrichtenbilder an.
    * **Timer Text Element:** Erstelle ein UI TextMeshPro-Textfeld (z.B. `TimerDisplay`) und ziehe es hierher.
    * **Round Text Element:** Erstelle ein UI TextMeshPro-Textfeld (z.B. `RoundDisplay`) und ziehe es hierher.
    * **Links Punkte Text / Rechts Punkte Text:** Erstelle UI TextMeshPro-Textfelder (z.B. `LeftScoreDisplay`, `RightScoreDisplay`) und ziehe sie hierher.
    * **NEU: Left Team Name Text / Right Team Name Text:** Erstelle zwei neue UI TextMeshPro-Textfelder (z.B. `LeftTeamNameDisplay`, `RightTeamNameDisplay`) und ziehe sie hierher. Diese müssen im `NewsController.cs` Skript als `public TextMeshProUGUI` deklariert sein.
    * **Ampel Icons (Arrays):** Ziehe die entsprechenden `GameObject`s oder Prefabs für deine grünen, gelben und roten Ampel-Icons in die jeweiligen Arrays. Stelle sicher, dass die Ampel-Icons als Kindobjekte in den `Ampel Parents Left` und `Ampel Parents Right` GameObjects vorhanden sind (z.B. `AmpelLeft1` hat Kinder `GrayIcon`, `GreenIcon`, `YellowIcon`, `RedIcon`).
    * **Ampel Parents Left / Right:** Ziehe die gleichen `AmpelLeft1`, `AmpelLeft2`, `AmpelLeft3` und `AmpelRight1`, `AmpelRight2`, `AmpelRight3` GameObjects aus der Szene hierher.
    * **Fake News Folder Name / Real News Folder Name:** Stelle sicher, dass diese auf `FakeNews` und `RealNews` (oder wie immer deine Ordner in `Resources` heißen) gesetzt sind.
    * **Background Video Player:** Ziehe die `Video Player`-Komponente von diesem GameObject in den Slot.
    * **Zone Green/Yellow/Red Max Z:** Passe diese Werte an die tatsächlichen Entfernungen (Z-Achse) an, in denen Kinect Spieler als "grün", "gelb" oder "rot" (Zustimmung/Unsicherheit/Ablehnung) erkennen soll. Diese Werte sind in Metern von der Kamera gemessen. **WICHTIG:** Kalibriere diese sorgfältig mit deiner Kinect-Hardware.

### 3.5 `OffboardingScene` konfigurieren

Diese Szene zeigt die Spielergebnisse an.

1.  Öffne die Szene `OffboardingScene.unity`.
2.  Erstelle ein leeres GameObject: `GameObject > Create Empty`. Benenne es `OffboardingController`.
3.  Ziehe das Skript `OffboardingController.cs` auf dieses GameObject.
4.  Füge dem `OffboardingController` GameObject eine **Video Player** Komponente hinzu (für den Hintergrund).
5.  Konfiguriere im Inspector des `OffboardingController`:
    * **Winning Team Name Text / Winning Score Text:** Erstelle UI TextMeshPro-Textfelder (z.B. `WinnerNameDisplay`, `WinnerScoreDisplay`) und ziehe sie hierher.
    * **Background Video Player:** Ziehe die `Video Player`-Komponente von diesem GameObject in den Slot.
    * **Background Video Clip:** Ziehe hier ein passendes Hintergrundvideo rein.
    * **Attract Scene Name:** Stelle sicher, dass dies auf `AttractScene` gesetzt ist.

---

## 4. Assets hinzufügen

Alle Assets, die du im Spiel anzeigen möchtest, müssen in den dafür vorgesehenen Ordnern platziert werden.

### 4.1 Bilder (News Sprites)

1.  **News Bilder:**
    * Kopiere deine Bilder, die als "Fake News" angezeigt werden sollen (z.B. `FakeNews01.png`, `FakeNews02.jpg`), in den Ordner `Assets/Resources/FakeNews`.
    * Kopiere deine Bilder, die als "Real News" angezeigt werden sollen (z.B. `RealNews01.png`, `RealNews02.jpg`), in den Ordner `Assets/Resources/RealNews`.
2.  **Feedback Bilder:**
    * Für jedes News-Bild solltest du ein entsprechendes Feedback-Bild haben. Benenne diese Feedback-Bilder so, dass sie zum News-Bild passen, aber im entsprechenden Feedback-Ordner liegen und z.B. das "_0" im Namen entfernt wurde (wie es im Skript `NewsController.cs` unter `DisplayFeedbackImage()` gehandhabt wird).
    * Beispiel: Wenn du `FakeNews/FakeNews_01.png` hast, sollte das Feedback-Bild `FakeNewsFeedback/FakeNews1.png` oder `FakeNewsFeedback/FakeNews1.png` heißen. Das Skript erwartet `FakeNewsFeedback/FakeNews1`.
    * Kopiere diese in `Assets/Resources/FakeNewsFeedback` und `Assets/Resources/RealNewsFeedback`.
    * **WICHTIG:** Stelle sicher, dass die `Texture Type` deiner Bilder im Inspector auf `Sprite (2D and UI)` gesetzt ist.

### 4.2 Videos

1.  Kopiere deine `.mp4` oder `.mov` Videodateien in den Ordner `Assets/Videos`.
2.  Ziehe die entsprechenden Videos in die `Video Player`-Slots der Controller in den jeweiligen Szenen (siehe [3.2 AttractScene](#32-attractscene-konfigurieren), [3.3 PlayerRegistrationScene](#33-playerregistrationscene-konfigurieren), [3.4 MainGameScene](#34-maingamescene-konfigurieren), [3.5 OffboardingScene](#35-offboardingscene-konfigurieren)).

### 4.3 Sound (Hintergrundmusik)

1.  Kopiere deine Audio-Dateien (z.B. `.mp3`, `.wav`) in den Ordner `Assets/Audio`.
2.  Erstelle in deiner ersten Szene (z.B. `AttractScene`) ein leeres GameObject und benenne es `BackgroundMusicManager`.
3.  Ziehe das Skript `BackgroundMusicManager.cs` auf dieses GameObject.
4.  Ziehe deinen Hintergrundmusik-Clip in den `Background Music Clip`-Slot im Inspector des `BackgroundMusicManager`.
5.  Stelle sicher, dass `Loop Music` angehakt ist, wenn die Musik wiederholt werden soll.
6.  Da `BackgroundMusicManager` ein Singleton ist, wird es automatisch über Szenenwechsel hinweg bestehen bleiben (Dank `DontDestroyOnLoad`).

### 4.4 UI-Elemente

Überall dort, wo im Inspector ein `TextMeshProUGUI` oder `Image` Slot vorhanden ist, musst du die entsprechenden UI-Elemente in deiner Szene erstellen und in diese Slots ziehen.

* `GameObject > UI > Image` für Bilder.
* `GameObject > UI > Text - TextMeshPro` für Texte.

**WICHTIG für Ampel-Icons:**
Die Ampel-Icons (Grün, Gelb, Rot, Grau) sollten als Kind-Objekte der `Ampel Parents Left`/`Right` GameObjects in der `MainGameScene` strukturiert sein.
Beispiel:
* `AmpelLeft1` (GameObject)
    * `GrayIcon` (Image mit dem grauen Ampel-Sprite)
    * `GreenIcon` (Image mit dem grünen Ampel-Sprite)
    * `YellowIcon` (Image mit dem gelben Ampel-Sprite)
    * `RedIcon` (Image mit dem roten Ampel-Sprite)
Stelle sicher, dass in den `Project Settings > Editor > Asset Serialization` der `Mode` auf **`Force Text`** und unter `Version Control` der `Mode` auf **`Visible Meta Files`** gesetzt ist. Dies ist entscheidend für Git.

---

## 5. Projekt testen und bauen

1.  **Teste das Spiel in Unity:**
    * Starte das Spiel in Unity, indem du in der `AttractScene` auf Play drückst.
    * Überprüfe, ob die Kinect korrekt initialisiert wird, Spieler erkannt werden, die Registrierung funktioniert, das Main Game startet und die Punkte korrekt berechnet werden.

2.  **Baue das Spiel (Build):**
    * Gehe zu `File > Build Settings...`
    * Wähle die gewünschte Plattform (z.B. `PC, Mac & Linux Standalone`).
    * Wähle deine Architektur (z.B. `x86_64` für 64-Bit-Systeme).
    * Klicke auf `Build`.
    * Wähle einen Ordner, in dem die ausführbare Datei erstellt werden soll.

---

## 6. Bekannte Probleme & Fehlerbehebung

* **Kinect nicht gefunden / Initialisierungsfehler:**
    * Stelle sicher, dass die Azure Kinect Kamera korrekt an den PC angeschlossen ist und die Treiber installiert sind.
    * Überprüfe, ob das Azure Kinect SDK und das Body Tracking SDK korrekt installiert sind.
    * Starte den PC neu.
    * Überprüfe im Unity Console-Fenster auf Fehlermeldungen vom `KinectController`.

* **Spieler werden nicht erkannt / Ampeln bleiben grau:**
    * Überprüfe die `Zone Green/Yellow/Red Max Z` Werte im `NewsController` Inspector. Sie müssen an den Abstand der Spieler zur Kamera angepasst werden. Teste dies mit tatsächlichen Spielern.
    * Stelle sicher, dass die `KinectController.cs` und `GetPelvisPosition.cs` Skripte aktiv und korrekt konfiguriert sind und Events feuern.
    * Prüfe, ob die `PlayerRegistrationController` alle Spieler korrekt mit `BodyId`s registriert hat und diese an `PlayerGameData` übergibt.

* **Bilder/Videos werden nicht angezeigt:**
    * Überprüfe die Pfade in den `Resources`-Ordnern und die Namen im Skript `NewsController.cs` (`fakeNewsFolderName`, `realNewsFolderName`).
    * Stelle sicher, dass die `Texture Type` deiner Bilder im Inspector auf `Sprite (2D and UI)` gesetzt ist.
    * Überprüfe, ob die entsprechenden `Image`- und `Video Player`-Komponenten in den Szenen den richtigen Slots im Inspector zugewiesen sind.

* **TextMeshPro Fehler:**
    * Falls du Fehlermeldungen bezüglich TextMeshPro erhältst, gehe zu `Window > TextMeshPro > Import TMP Essential Resources` und importiere die benötigten Ressourcen.

* **"NullReferenceException" im Unity Console:**
    * Diese Fehler treten auf, wenn ein Skript versucht, auf ein Objekt zuzugreifen, das nicht zugewiesen wurde (z.B. ein UI-Element im Inspector nicht in den Slot gezogen wurde). Überprüfe die Fehlermeldung genau, sie zeigt dir, welches Skript und welche Zeile betroffen ist. Gehe dann zu dem entsprechenden GameObject im Inspector und weise die fehlenden Referenzen zu.

---

Viel Erfolg beim Aufbau deines Fake News Erkennungsspiels!
