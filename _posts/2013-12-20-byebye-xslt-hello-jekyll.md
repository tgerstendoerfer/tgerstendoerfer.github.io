---
layout: post
title: Goodbye XSLT, Hello Jekyll
---

Die ersten Versionen dieser Website waren handgeschrieben, bis mir die
Verwaltung etwas über den Kopf wuchs und ich vor etwas über 10 Jahren
mein eigenes XML/XSLT-basiertes Web-Publishingsystem entwickelte und in
den darauffolgenden Jahren ständig verbesserte.
Im Laufe der Entwicklung lernte ich sehr viel über XSLT, verschiedene
Make-Varianten, Build-/Deploy-Pipelines, Content Management und Web
Publishing im allgemeinen.
Die Seiten wurden dabei stets lokal (auf dem Build-Server) generiert,
einerseits um die Abhängigkeit von der Server-Konfiguration so klein
wie möglich zu haben, andererseits weil das Buildsystem so praktisch
beliebig kompliziert sein kann ohne die Antwortzeiten zu beeinträchtigen,
und schliesslich weil ich gar keine dynamischen Inhalte hatte.

Dieses immer komplexere System machte es sehr einfach, neue Inhalte
hinzuzufügen. Doch je beschäftigter ich in Studium und Beruf war, desto
mehr veralteten die bestehenden Sachen. Hilfreiche Tipps und Tools für
Windows NT 4 machten spätestens unter Windows XP keinen Sinn mehr.
Auch merkte ich, dass mir bestimmte Themen auf englisch besser von der
Hand gingen, und andere auf deutsch, und die jeweils übersetzte Version
den Inhalt nicht wirklich klar rüberbrachte.
Vor die Wahl gestellt, entweder veraltete Inhalte weiterzuverbreiten,
sie frisch aufzubereiten, oder sie zu löschen, entschied ich mich für
die Radikalkur und löschte einen Grossteil der Seiten:
Fort mit den Fotogalerien (schliesslich hatte ich Flickr), weg mit
dem Design-Portfolio (schliesslich war ich nun Softwareentwickler),
weg mit veralteten Tools und Tipps.
Übrig blieben eigentlich nur mein CV, ein paar Fotos und ein bisschen
Text — und das XML-Publishingsystem, denn es funktionierte ja.
Auch wenn mittlerweile rund dreimal soviele Quelltext- wie HTML-Dateien
vorhanden waren.

In letzter Zeit fragte ich mich jedoch immer häufiger, ob ich diesen
Funktionsumfang überhaupt brauche. So ist es zwar schön, dass mein CV
in einem XML-Format semantisch definiert wurde, und ich daraus per
XSLT sowohl die HTML- als auch RTF- und Plain-Text-Versionen erzeugte
(und am InDesign-Export zu arbeiten begonnen hatte).
Andererseits hatte ich seit Jahren keine Plain-Text mehr verschickt,
das Layout in RTF war sehr von der Word-Version und den
Drucker-Einstellungen abhängig, und inzwischen können mit modernen
Browsern gedruckte HTML-Seiten durchaus mit in InDesign gesetztem
Text mithalten.

Nachdem ich auf diesen Seiten (gerstendoerfer.ch) bereits erste
Erfahrung mit <a href="http://jekyllrb.com">Jekyll</a> gesammelt hatte,
war für mich klar, dass es an der Zeit war,
<a href="http://gerstendoerfer.com">gerstendoerfer.com</a> nicht nur
in Bezug auf Inhalt und Design zu überdenken sondern auch hinter den
Kulissen aufzuräumen und mein XML-Publishingsystem durch Jekyll zu
ersetzen.

Zu diesem Zeitpunkt bestand meine Website aus eigentlich vier Seiten:
Homepage mit Fotos, About-Seite mit Text über mich, und der Lebenslauf
auf deutsch und englisch.
Daneben hatten sich allerdings etliche Fotogalerien, Hilfs-Skripts,
Tools und weiss was alles sonst noch breitgemacht.
Also galt es in einem ersten Schritt, zu schauen was alles so herumliegt,
und ob es überhaupt noch von Nutzen ist.
Die Galerien von den ersten Jahren des
<a href="http://www.bandxaargau.ch">bandXaargau Schülerbandfestival</a>
beispielsweise lud ich auf den Server des Projekts und richtete permanente
Umleitungen (301) ein.
<a href="http://gerstendoerfer.ch/above/">ABOVE</a> ist nun auf GitHub.
Andere löschte ich ersatzlos.

Wie bei anderen Softwareprojekte auch ersetzte ich ein Subsystem nach
dem anderen, hatte aber ständig eine *deploybare* Website, deren Inhalt
ich nach belieben anpassen und publizieren konnte.
Und wie bei anderen Sofwareprojekten hat sich dieses Vorgehen sehr
bewährt, und so ist meine Website mittlerweile hinter den Kulissen
deutlich schlanker und wartbarer geworden.

Und so kann ich mich nun um das eigentlich Wichtige kümmern:
Meine Fotos besser zu präsentieren!
