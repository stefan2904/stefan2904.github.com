---
layout: 	post
title: 		Java Privacy Guard?
tags: 		[Uni, back, Tech]
published: 	true
---

Thema meiner Bachelor-Arbeit, welche ich seit Ende Feber dieses Jahres am [Institut für Angewandte Informationsverarbeitung und Kommunikationstechnologie](http://iaik.tugraz.at) (IAIK) schreibe, ist **openPGP**. Da ich versuchen werde, diese Arbeit nach dem [Open Science](http://openscienceasap.org/open-science/) Prinzip  durchzuführen, werde ich in diesem Blog ab und zu davon berichten.

Konkret geht es bei meinem Projekt um die Implementierung des [RFC 4880](https://tools.ietf.org/html/rfc4880) in Java mit Hilfe des [IAIK-JCE](http://jce.iaik.tugraz.at/), der Crypto-Bibliothek des IAIK. Aus naheliegenden Gründen habe ihr für dieses Projekt den Arbeitstitel *Java Privacy Guard* gewählt.

# RFC 4880

openPGP ist der aus der Verschlüsselungs- und Signatur-Software PGP entstandene Standard für den Aufbau von "PGP Nachrichten", welcher in [RFC 4880](https://tools.ietf.org/html/rfc4880) definiert ist. Bekannteste Implementierung von openPGP ist neben dem erwähnten kommerziellen PGP (mittlerweile im Besitz von Symantec) vor allem das freie [GnuPG](http://www.gnupg.org/). Alle openPGP-Implementierungen sind zueinander kompatibel, sofern sie auf der gleichen Version des Standards basieren. 

## Public-Key-Kryptographie …

openPGP arbeitet auf Basis von Public-Key-Kryptographie. Um einer Person beispielsweise eine openPGP-verschlüsselte Datei zu senden benötigt man also deren Public-Key (meiner ist [hier](http://2904.cc/stefan.asc) zu finden). Diese Person benötigt zum Entschlüsseln der Datei wiederum einen Private-Key (zu dem niemand sonst Zugang haben darf). Zusammen ergeben ein Public-Key und dessen zugehöriger Private-Key ein sogenanntes Schlüsselpaar (*Keypair*).

## … ist nicht alles

Public-Key-Kryptographie hat jedoch zwei große Nachteile: Einerseits ist sie meist [langsam](http://crypto.stackexchange.com/a/591/12582), andererseits müssten Daten, die an mehrere Personen übermittelt werden (was bei E-Mail regelmäßig vorkommt) mehrmals Übertragen werden (jeweils mit einem anderen Public-Key verschlüsselt).
Anders als oft geglaubt verschlüsselt eine openPGP-Implementierung die Daten daher nicht mit dem erwähnten Public-Key. Vielmehr werden die eigentlichen Daten mit einem jedes mal neu (zufällig) generierten Schlüssel symmetrisch verschlüsselt. Nur dieser (symmetrische) Schlüssel wird mit dem Public-Key verschlüsselt und muss im Bedarfsfall mehrmals übertragen werden.

![openPGP, Diagramm (cc-by-sa) by me](http://2904.cc/blogimg/bakk/PGP.png)

Unter einer "PGP Nachricht" (im Sinne des RFC 4880) versteht man also nicht nur die eigentliche (verschlüsselte und/oder signierte) Datei, sondern auch die Schlüssel oder eine Signatur. RFC 4880 definiert den Aufbau solcher "Nachrichten" (daher der Titel *OpenPGP Message Format*).

Im Zuge dieser Definitionen legt openPGP auch fest, [welche Algorithmen](https://tools.ietf.org/html/rfc4880#section-9) für die Verschlüsselung und Signatur eingesetzt werden können. Die Algorithmen selbst sind jedoch weder im openPGP-Standard spezifiziert (sondern in eigenen RFCs) noch Teil meines Projects (da schon im IAIK-JCE implementiert).

# Status

Um den Beginn der Bachelor-Arbeit etwas zu erleichtern, gab es vom IAIK aus das Angebot, die ersten 2 Wochen am Institut zu verbringen, welches ich sehr gerne angenommen habe. Dank örtlicher Nähe zu meinem Betreuer (und anderer KollegInnen) und dem universitären Umfeld konnte ich schnell loslegen. Erster, bereits nach eineinhalb Wochen erreichter "Milestone", war das Einlesen von mit GnuPG generierten (RSA) Keys, was meine zeitlichen Einschätzungen etwas übertroffen hat.

Nächster Schritt ist das Schreiben von weiteren Unit-Tests und das Implementieren weiterer Algorithmen. Außerdem sollte es nicht mehr lange dauernd, bis mit den eingelesenen Keys auch Daten entschlüsselt werden können. Abschließend soll es noch möglich sein, Keypairs zu generieren und natürlich Nachrichten zu verschlüsseln so wie zu signieren.

Weitere Features werden sich im Rahmen der Bachelor-Arbeit wohl nicht ausgehen, da ich abschließend noch die eigentliche Arbeit darüber schreiben muss, was auch Zeit kosten wird. Es gibt jedoch einige mögliche Erweiterungen außerhalb der Bachelor-Arbeit:

Eine davon ist das Integrieren eines PGP-Keystores in die Java Crypto Architektur (JCA) bzw. eine Evaluierung, ob das möglich ist oder Sinn macht. Außerdem wäre ein PGP-Crypto-Provider naheliegend.

Weitere potenzielle Erweiterungen sind neben einem eigenen Keyserver eine Integration des Bürgerkarten-Systems, was jedoch momentan nicht mehr als ein früher Gedanke ist.
