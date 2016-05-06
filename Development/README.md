## KSP Deutsch Patch Entwicklung
In diesem Ordner findet ihr alles was ihr braucht um am KDP aktiv mitzuwirken.
Bitte beachtet, dass ihr, solltet ihr bei der Entwicklung mithelfen, Schreibzugang zu diesen
Dateien habt. Bitte seit vorsichtig, damit sie andere genauso nutzen k�nnen wir ihr.

### Logs
Im Ordner `Logs/` findet ihr die exportierten Texte des Spiels, sortiert nach Szenen in denen sie auftauchen.
Orientiert euch bei euren �bersetzungen bitte daran und verzichtet ersteinmal darauf die Texte ingame abzuschreiben.

### �bersetzungsdateien
Der KDP benutzt das [LanguagePatches-Framework](https://github.com/LanguagePatches/LanguagePatches-Framework), entwickelt von
@ThomasKerman und @simon56modder. Es erlaubt uns, die Texte, die das Interface von KSP benutzt mit unseren eigenen Versionen zu 
ersetzen. Diese Informationen werden aus Dateien mit der Dateiendung `.cfg` aus dem `GameData/` Ordner geladen. Diese Dateien m�ssen
die folgende Grundstruktur haben:
```LANGUAGEPATCHES
{
	// Hier kommen die �bersetzungen hin
	// + anderer Kram
}
```
Der Inhalt der `LANGUAGEPATCHES` Sektion muss die folgende Struktur haben:
```TRANSLATION
{
	text = foo // Originaler Text aus den Log Dateien
	translation = bar // �bersetzte Version
	scene = MAINMENU // Optional, �bersetzt den Text nur in der angegebenen Szene.
}
```
Die `TRANSLATION` Sektionen k�nnen �ber mehrere Dateien verteilt sein, sie m�ssen nur alle die selbe Grundstruktur aufweisen.

### Regular Expressions
Die Werte in den `TRANSLATION` Sektionen sind nicht blo� rohe Daten, es sind [Regular Expressions](https://de.wikipedia.org/wiki/Regul�rer_Ausdruck), auch Regex genannt.
Regex ist eine Sprache, die es uns erlaubt nach Textsequenzen zu scannen und diese zu extrahieren. Dadurch wird es m�glich, Teile von dynamischen Texten, also Texten
die sich ver�ndern (eine Datumsanzeige z.B.) zu �bersetzen. Hier ein Beispiel was man mit Regex machen kann:
``` TRANSLATION
{
	text = Year (\d*), Day (\d*) - (\d*)h, (\d*)m
	translation = Jahr @1, Tag @2 - @3h, @4m
}
```
@1, @2 usw. stehen dabei f�r die Werte die aus dem Originaltext extrahiert wurden. Solltet ihr schonmal mit regex gearbeitet haben, f�hlt euch frei diese Texte in Angriff zu nehmen.
Da allerdings alles ein Regul�rer Ausdruck ist, m�sst ihr bestimmte Signale dieser Sprache "unsch�dlich" machen, mit dem Buchstaben `\`. Das sind z.B. ., +, $, ^, ?, (, ), [, ], |, und \.
Wenn ihr Hilfe braucht, schreibt einfach Thomas P. eine Nachricht, ich sehe mir euren Text dann an.

### Bugs
Wenn ihr Fehler im Patch erkennt, schaut bitte zuerst nach ob ihr die letzte Version von Patch und LanguagePatches-Framework habt. Sollte der Fehler dann immernoch
auftreten, �ffnet bitte ein Ticket im Issue Tracker dieses Repositories, und wir sehen uns das an.

### Alles Andere
F�hr alles andere, sei es Fragen zu �bersetzungen, oder zu GitHub, stehen wir euch (fast) immer zur Verf�gung. Fragt einfach nach.