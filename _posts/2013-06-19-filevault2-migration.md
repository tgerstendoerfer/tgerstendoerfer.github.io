---
layout: post
title: System FileVault 2 auf neue Disk migrieren
---

Vor ein paar Tagen (als die Disk I/O Performance mal wieder zum unglücklichwerden war) hab ich mich entschlossen, mein 2010er MacBook Pro mit einer SSD aufzuwerten und gestern war nun Zeit, das Teil einzubauen.

## Ist ja ganz einfach…

Sollte ja ganz einfach sein: Mac auf, alte Disk raus, SSD rein, Mac zu, System zurückspielen, happy! Soweit die Theorie. Nun verschlüssle ich die Disks allerdings mit FileVault&nbsp;2, und soweit mir bekannt ist kann man bei der Installation das System mit den alten Daten nicht direkt auf eine verschlüsselte Disk schreiben.
Stattdessen sieht der von Apple vorgesehene Prozess in etwa so aus:

1. (Time Machine) Backup erstellen
2. Disks austauschen
3. OS X Installation starten und angeben, dass der Rechner vom Time Machine Backup (oder der alten System-Disk) wiederhergestellt werden soll.
4. Nach erfolgreicher Installation File Vault&nbsp;2 einschalten, woraufhin die ganze Disk verschlüsselt wird.

Das tönt ja eigentlich machbar und ganz vernünftig. Die Daten landen zwar in Schritt #3 unverschlüsselt auf der Disk, in Schritt #4 wird jedoch jeder Block verschlüsselt und überschrieben. Zumindest bei einer "normalen" Harddisk. Bei SSDs jedoch hat das Betriebssystem keine Kontrolle darüber, wie die Daten abgelegt werden, folglich kann man auch nicht davon ausgehen, dass alle unverschlüsselten Daten überschrieben werden.
Paranoid? Vielleicht. Doch wenn ich meine Disk schon verschlüssle, dann will ich es auch richtig tun, ohne dass Plaintext-Schnipsel irgendwo rumliegen.

## Die Idee

Kann ja nicht so schwierig sein. Anstatt das alte System mit allen Anwendungen und Daten gleich während der Installation zu übertragen, installiere ich halt das System neu (mit einem anderen Passwort), aktiviere FileVault&nbsp;2, und kopiere meine Daten erst danach auf die inzwischen verschlüsselte Disk. Für etwas gibt es ja den Migration Assistant.

Gesagt, getan, Betriebssystem drauf, FileVault&nbsp;2 ein, rund eine Stunde gewartet bis alles verschlüsselt ist, Migration Assistant gestartet — und die Erinnerung, dass dieser den Rechner als eine neue Installation behandelt und deshalb einige Einstellungen nicht übernimmt. Ich möchte jedoch meinen Rechner wiederherstellen, einfach auf einer neuen Disk!

## Plan B

Ich baue die alte Disk in ein externes Gehäuse ein, schliesse dieses an, drücke beim Booten die Option-Taste um vom alten System zu starten und kopiere dieses mit [SuperDuper](http://www.shirt-pocket.com/SuperDuper/) auf das neue System. Und erinnere mich wieder weshalb ich die meisten externen Laufwerke mit Fire Wire anschliesse: USB&nbsp;2 ist einfach sehr, sehr langsam.

Na dann Zeit, die Wäsche zu machen, Besorgungen zu erledigen, und zu schwimmen.

## Nicht so schnell!

Irgendwann sind alle Daten übertragen, das System läuft ganz gut, ausser [Dropbox](https://www.dropbox.com) funktioniert alles ohne mich frisch anzumelden. Lightroom ist mit über 100'000 Fotos im Katalog noch immer langsam, jedoch deutlich schneller zuvor. Gut.

Irritierend ist jedoch, dass beim Starten des Systems zwei Login-Schirme angezeigt werden, und dass der erste (zum entschlüsseln des Systems) Passwortänderungen nicht übernimmt.

Die meisten Anleitungen, die ich im Internet fand empfehlen in solchen Situationen, FileVault&nbsp;2 zu deaktivieren und anschliessend wieder zu aktivieren.
Doch das ist ja exakt, was ich von Anfang an vermeiden wollte!

Schliesslich erinnere ich mich jedoch an [fdesetup(8)](http://developer.apple.com/library/mac//documentation/Darwin/Reference/ManPages/man8/fdesetup.8.html) und kann das Problem schnell lösen: OS&nbsp; weist jedem Benutzer eine UUID zu und verwendet diese intern. Und beim kopieren der Installation auf die frisch verschlüsselte Disk hat das "Boot-Login" nichts von den neuen (alten) Benutzer-IDs mitgekriegt. Nun genügt es mittels `fdesetup remove name` den alten Benutzer zu entfernen und mittels `fdesetup add -usertoadd name` den neuen Benutzer einzutragen.
Und schon muss man sich nur einmal anmelden, und Passwortänderungen werden ebenfalls automatisch übernommen.