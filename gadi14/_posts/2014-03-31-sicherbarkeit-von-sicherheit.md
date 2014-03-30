---
layout: 	post
title: 		Wie sichtbar soll Sicherheit sein?
tags: 		[Uni, gadi14, Gesellschaft]
published: 	true
---

Letzte Woche schrieb ich über Snowedens Talk auf der TED2014 Konferenz. Einen von ihm (und vielen anderen) besprochenen Punkt habe ich jedoch noch nicht erwähnt: Seine Forderung nach benutzerfreundlichen Tools zur sicheren Kommunikation.

*(Crosspost [meines vierten Artikels](http://tugll.tugraz.at/blog/view/41532/wie-sichtbar-soll-sicherheit-sein) aus dem Lehrveranstaltungs-Blog von [Gesellschaftliche Aspekte der Informationstechnologie](http://blog.2904.cc/2014/03/14/gadi14/).)*

Wir alle nutzen&nbsp;mittlerweile das Internet. Nicht nur auf unserem Laptop oder PC, sondern immer h&auml;ufiger auch am Smartphone. Ein gro&szlig;er Teil der digitalen Kommunikation erfolgt mittlerweile &uuml;ber mehr oder weniger sichere Kan&auml;le. Meist ist jedoch nur die Verbindung vom Ger&auml;t zum Server verschl&uuml;sselt (TLS/SSL/HTTPS), und das ist oft auch ausreichend. Die dadurch entstehende Sicherheit ist f&uuml;r User &uuml;blicherweise unsichtbar, und das ist wohl gut so.

Man denke jedoch an die Panik, die auftritt, wenn ein Browser einmal ein ung&uuml;ltiges HTTPS-Zertifikat meldet. Woher der Fehler kommt, was er bedeutet, und das er oft durch das Einstellen der richtigen Systemzeit leicht behoben werden k&ouml;nnte, ist den meisten Usern nicht bewusst. Genauso wenig wissen die wenigsten &uuml;berhaupt etwas von der Existenz der "Transport Layer Security", geschweige denn, was dieser Begriff eigentlich bedeutet. Das Problem beginnt wohl schon bei der Tatsache, dass die wenigsten wissen, wie Netzwerke &uuml;berhaupt funktionieren. So kommt es, dass es sich noch immer nicht wirklich herumgesprochen hat, wer eigentlich alles die Mail lesen k&ouml;nnte, die man da gerade aus dem Zug an seineN FreundIn schickt.

Aufkommendes Bewusstsein der Medien und Veranstaltungen wie die <a href="http://cryptoparty.at/">CryptoPart</a> (findet&nbsp;&uuml;brigens <a href="http://linuxtage.at/cryptoparty/"> diesen Freitag auf den <em>Grazer Linuxtagen</em></a> wieder statt) schaffen hier zwar vereinzelt Abhilfe, k&ouml;nnen aber bisher nicht die n&ouml;tige Masse erreichen.

Neben dem fehlenden grundlegenden&nbsp;Verst&auml;ndnis von digitaler Kommunikation und dem schwachen Sicherheitsbewusstsein mangelt es aber vor allem auch an einem: An benutzbaren Tools.

Im Gegensatz zu den meisten am Transport Layer arbeitenden Verschl&uuml;sselungen braucht man f&uuml;r viele Tools, insbesondere jenen, die eine Ende-zu-Ende Verschl&uuml;sselung sicherstellen, n&auml;mlich sowohl&nbsp;Kenntnis dieser Tools, als auch die F&auml;higkeit, sie zu benutzen.

Und so ist es an der "<em>Crypto-Community</em>", nicht nur neue, sichere Systeme zu schaffen, und Verschl&uuml;sselung endlich zum alternativlosen Standard zu erkl&auml;ren, sondern auch benutzbare Systeme.

Zwar haben die Aufdeckungen von Edward Snoweden in der Community und auf den Konferenzen f&uuml;r ein wenig Bewegung gesorgt, es ist jedoch immer noch viel zu tun.

Um abschlie&szlig;end auf den Titel dieses Posts zur&uuml;ckzukommen: ich glaube, dass die Implementierung von digitaler Sicherheit so&nbsp;unsichtbar wie m&ouml;glich sein soll, User aber dennoch die grundlegenden Prinzipien verstehen m&uuml;ssen. Insbesondere jene Bereiche, die (soziale) Interaktion erfordern, wie beispielsweise das Web of Trust.

So liegt es an uns TechnikerInnen, Tools zu bauen, die auch von jenen verwendbar sind, die keinen Abschluss in Informatik haben. Jabber-Clients mit eingebautem OTR und <a href="http://mailpile.is/">sichere Webmail-Systeme</a> k&ouml;nnen nicht alles gewesen sein.
