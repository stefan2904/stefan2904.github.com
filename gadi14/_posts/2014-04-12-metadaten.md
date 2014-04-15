---
layout: 	post
title: 		Metadaten?
tags: 		[Uni, gadi14, Gesellschaft]
published: 	true
---

Was sind eigentlich diese Metdaten, von denen alle reden?

*(Crosspost [meines fünften Artikels](http://tugll.tugraz.at/blog/view/41828/alles-meta-oder-was) aus dem Lehrveranstaltungs-Blog von [Gesellschaftliche Aspekte der Informationstechnologie](http://blog.2904.cc/2014/03/14/gadi14/).)*

Metadaten sind erstmal nur <strong>Daten, die andere Daten beschreiben</strong>. Der Name eines Dokuments geh&ouml;rt beispielswei&szlig;e zu den offensichtlichsten Metadaten. Er beschreibt eine Datei (gibt ihr einen Namen), ist aber nicht Teil der Daten selbst.

## Unsichtbare Daten?
Weniger sichtbare Metadaten sind unter anderem die <strong>EXIF-Daten</strong>. In einer digitalen Bilddatei "versteckt" geben sie unter anderem Auskunft &uuml;ber den Entstehungszeitpunkt des Bildes und die verwendete Kamera. In Zeiten von Smartphone-Foto findet sich in den EXIF-Daten jedoch oft noch etwas anderes: Ist das GPS aktiviert (und das Smartphone nicht&nbsp;anderweitig konfiguriert), werden die GPS-Koordinaten des Entstehungsortes in den Metadaten gespeichert. 

Die wenigsten sind sich wohl bewusst, dass sie durch das Ver&ouml;ffentlichen solcher Bilder auch die EXIF-Daten mit ver&ouml;ffentlichen, und so einiges preisgeben. EXIF-Daten sind jedoch auch sehr n&uuml;tzlich und sinnvoll, wenn es darum geht, (meist) gr&ouml;&szlig;ere Mengen von Bildern zu organisieren (oder auf einer Karte zu verzeichnen, wie es zum Beispiel der Bild-Hoster flickr vollautomatisch tut).

Gegen die meisten dieser Metadaten kann man sich im Bedarfsfall "<strong>sch&uuml;tzen</strong>", in dem man diese von der eigentlichen Datei entfernt. Was f&uuml;r viele jetzt paranoid scheinen mag, ist f&uuml;r AktivistInnen oft lebensnotwendig. (Im mobilen Bereich sind hier &uuml;brigens <a href="https://guardianproject.info/apps/">die Apps vom <strong>Guardian Project</strong></a> zu empfehlen.)

## Notwendige Metadaten?
Die Metadaten, um die es in den momentanen Diskussionen in Artikeln rund um "den NSA Skandal" oder "Snowden's Enth&uuml;llungen" geht, sind aber andere: Metadaten, die eine Verbindung beschreiben, sogenannte <strong>Verbindungsdaten</strong>.

Verbindungsdaten sind einerseits deswegen so interessant, weil sie oft mehr &uuml;ber eine Person (und deren soziales Netzwerk) aussagen, als die eigentlichen Daten.&nbsp;Andrerseits sind sie&nbsp;wesentlich leichter maschinell auszuwerten, da sie ja f&uuml;r Maschinen bestehen. Weiteres sind sie viel schwerer zu verstecken, da f&uuml;r sie eine technische Notwendigkeit besteht.

Ein <strong>Beispiel</strong>: Die Daten einer E-Mail sind der Text und eventuelle Anh&auml;nge. Zu den notwendigen Metadaten dieser E-Mail geh&ouml;rt zumindest die Empf&auml;nger-Adresse. (Meist werden jedoch auch noch Absender-Adresse, Betreff, und weitere technisch bedingte Header dazugez&auml;hlt.) Im Prozess der &Uuml;bermittlung der Mail von Absender-Server an Empf&auml;nger-Server k&ouml;nnen diese Metadaten zwar sicher &uuml;bertragen werden (TLS, vorausgesetzt openSSL ist gepacht), es entstehen jedoch neue Metadaten: Die Verbindung von Server zu Server muss auch irgendwie beschrieben werden. Und dies l&auml;sst sich technisch bedingt nicht so leicht verstecken.

Ein <strong>analoges Beispiel</strong> verdeutlicht diese Problematik weiter: man kann einer Person zwar einen Brief schicken, ohne das die Post wei&szlig;, was man geschrieben hat. Man kann jedoch nicht verhindern, dass jemand mitbekommt, DASS diese Person einen Brief bekommt (und eventuell auch nicht, von wem er stammt).

Ein weiteres interessantes (und gut beschriebenes) <strong>Beispiel zur Anwendung</strong> stammt von&nbsp;<a href="https://twitter.com/kjhealy">Kieran Healy</a>, welcher <a href="http://kieranhealy.org/blog/archives/2013/06/09/using-metadata-to-find-paul-revere/">mit Hilfe von Metadaten aus dem 18. Jahrhundert eine Person ausfindig gemacht hat</a>.

## Anonym trotz Metadaten?
Das <a href="https://netzfreiheit.org/2014/04/08/presseaussendung-zu-den-verstrickungen-der-nsa-mit-oesterreichischen-behoerden/">Interesse von Beh&ouml;rden aller L&auml;nder</a> (was speichert wohl die <strong>Vorratsdatenspeicherung</strong>) best&auml;tigt die Bedeutung von Metadaten weiter.

Im digitalen Raum schaffen&nbsp;<strong><span>Anonymisierungsnetzwerke</span></strong> wie <a href="https://www.torproject.org/">Tor</a> und <a href="http://geti2p.net/">i2p</a> zwar Abhilfe, aber auch nur eingeschr&auml;nkt. Eine Antwort auf diese Problematik kann also wiederum wohl nur eine Kombination aus Bewusstsein, technischem&nbsp;Verst&auml;ndnis und politischem Willen sein.

