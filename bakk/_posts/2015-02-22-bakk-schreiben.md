---
layout: 	post
title: 		Bachelor-Arbeit schreiben …
tags: 		[Uni, bakk, Tech]
published: 	true
---

Nachdem der [Praxis-Teil](http://jpg.2904.cc) meiner Bachelor-Arbeit seit Dezember abgeschlossen ist, ich den Theorie-Teil (also das Schreiben der eigentlichen Arbeit) auf Grund von dazugekommenem Aufwand aber bisher vernachlässigt habe, wurde es nun Zeit für eine etwas intensivere Beschäftigung damit. 

# Was ist "die Frage"?

Da es sich bei meiner Bakk-Arbeit nicht um eine wissenschaftliche Arbeit im engeren Sinne handelt, sondern um die Implementierung eines bereits existierenden Protokolls ([dem openPGP Standard](https://tools.ietf.org/html/rfc4880)), ergab sich naturgemäß auch keine "wissenschaftliche Frage", über die ich hätte schreiben können. 

Primärer Grund, warum ich erst so spät mit dem Schreiben durchstarte, ist also die Unklarheit, worüber ich eigentlich schreiben soll. Selbst hatte ich mir die Latte hoch gelegt - vielleicht zu hoch. Von Anfang an war mit klar, dass ich keine simple Übersetzung des Standards oder einen Report über meine Implementierung abliefern wollte.

Geplant, aber dann mehr oder weniger schnell verworfen, waren so einige Schwerpunkte. Unter anderem geplant war eine Evaluierung aller in openPGP verwendeten Algorithmen und deren Parameter, schließlich ist der Standard doch schon ein paar Jahre alt. (Das machen jetzt aber [eh andere](https://www.ibr.cs.tu-bs.de/theses/schuerm/openpgp-evaluation.html?lang=en).) Eine andere Überlegung war eine (mehr oder weniger Literatur-)Arbeit über den aktuellen Stand von E-Mail Verschlüsselung zu schreiben. Das meiste davon hätte jedoch den Rahmen einer Bachelor-Arbeit gesprengt. (Zumindest gibt's nun eine Liste an potentiellen Themen für Paper.)

# Aktueller Plan

Nach einigen Recherchen, vielen studierten [Papers](https://github.com/stefan2904/bakk-thesis/blob/master/mendeley.bib), [Vorträgen](https://events.ccc.de/congress/2014/Fahrplan/events/6021.html), Mailinglisten-Threads & [Blog-Posts](https://delicious.com/stefan2904/openpgp) und ein [paar](http://chille.at/) [inspirierenden](http://nicolas.braud-santoni.eu/) [Gesprächen](http://petergrassberger.at/) hat sich dann im Zuge der letzten Wochen ein **Plan** entwickelt, den ich in den letzten Nächten verfeinert (und [teilweise schon grob umgesetzt](https://github.com/stefan2904/bakk-thesis)) habe:

## Abstract

Die Funktion dieses Kapitels ist weitestgehend geregelt. 
Ein kurzer Überblick, was von dieser Arbeit zu erwarten ist.
Über Ergebnisse werde ich halt weniger zu berichten haben.

Der genaue Text wird jedoch erst kurz vor Abschluss der Arbeit geschrieben. ;-)

## Introduction

Eine genauere Einführung in das Feld (asynchrone ende-zu-ende Verschlüsselung), das Protokoll (openPGP) und die Arbeit selbst. Vor allem ein Überblick, was in welchem Kapitel passiert.


## Preliminaries

Eine Auflistung und kurze Erklärung der in der Arbeit verwendeten so wie für die Imlementierung benötigten Techniken, Technologien und Standards. 

Wie weit ich auf Kryptographische Primitiven und Algorithmen eingehen werde, ist mir noch nicht klar. Prinzipiell würde ich hier aber gerne den Unterschied von symmetrischer- zu asymmetrischer-Kryptographie erläutern, da das für openPGP wichtig ist. 

Außerdem ist es naheleitend, kurz digitale Signaturen bzw. Zertifikate zu erklären. Ein weiterer Fixpunkt werden die verwendeten Technologien sein, also Java und vor allem die [IAIK-JCE](https://jce.iaik.tugraz.at/).

Da ich zum Veranschaulichen der openPGP-Prinzipien auch auf vergleichbare Systeme (wie S/MIME bzw. X.509) zurückgreifen werde, überlege ich noch, diese hier auch kurz vorzustellen.

## openPGP

Nachdem alle Basics geklärt sind, geht es in diesem Kapitel um die Einführung in den openPGP Standard. Vor allem möchte ich hier die durch den Standard abgedeckten Prinzipien erläutern und erklären, wie openPGP diese löst.

Vorrangig betrifft das also [die Sache mit der Sym-/Asym-Kombination](http://blog.2904.cc/2014/03/18/Java-Privacy-Guard), Confidentiality/Integrity/Authentication so wie Key-Zertifizierung bzw. das Web of Trust.

## The openPGP Message Format

Nachdem im vorherigen Kapitel alle wichtigen Prinzipien und Konzepte erklärt wurden, geht es in diesem Kapitel um die etwas detailliertere Umsetzung im Standard. 

Vorrangig möchte ich hier die interne Struktur einer openPGP "Message" erklären, die Aufteilung in Packets erläutern so wie anhand von wichtigen Packet-Kompositionen das Prinzip veranschaulichen, ohne jedoch eine Kopie des Standards abzuliefern.

Plan B ist, dieses Kapitel mit dem vorherigen zu verschmelzen. Laut derzeitigem Plan hätte ich die prinzipielle Erklärung und die technische Umsetzung jedoch gerne getrennt. Mal schauen wie sich das ausgeht ...

## Java Privacy Guard

Das Kapitel über die praktische Arbeit. Das wohl schwierigste Kapitel. 

Prinzipieller Plan für dieses Kapitel ist einerseits eine Erläuterung der für meine Implementierung entworfenen Architektur, und andererseits ein paar allgemeine Worte zur Umsetzung von openPGP in Java. Vorrangig geht es um die Abbildung der im Standard beschriebenen Daten-Strukturen.

Als Ergänzung plane ich noch ein paar kurze Beispiele zur Veranschaulichung der Verarbeitung dieser Daten-Strukturen in Java, da dies den Haupt-Aufwand meiner Implementierung dargestellt hat.

Abschließend werde ich wohl noch ein paar Worte über den Zusammenhang zwischen meiner Implementierung, der IAIK-JCE und der Java Crypto Architecture verlieren.

## Concerns & Conclusion

Obwohl das eigentlich schon den Rahmen der theoretischen Arbeit sprengt habe ich für dieses Kapitel eine Zusammenfassung von Bedenken bzgl. Sicherheit und Benutzbarkeit geplant. 

Zwar werde ich wie gesagt keine eigene Evaluierung durchführen, aber eine kurze Zusammenfassung in Form von Literaturquellen ist geplant. For allem das Thema (Un-)Benutzbarkeit halte ich in dem Umfeld für wichtig, auch wenn ich da nicht wirklich der Experte bin.

Abschließende Worte für die Conclusion der Arbeit müssen sich noch finden.

# Herausforderungen

Die größte Herausforderung ist wohl das Schreiben eines längeren wissenschaftlichen Textes an sich. Da man im Informatik-Studium (anders als beispielsweise in geistes- und sozialwissenschaftlichen-Studien) keine Seminararbeiten schreiben muss, und auch sonst quasi keinerlei wissenschaftliche Schreib-Praxis hat (und die freiwillig angebotene [Schreibstube](https://kcposch.wordpress.com/2014/10/29/writing-about-writing-and-thinking-about-thinking/) verpasst), finde zumindest ich mich regelmäßig beim einen-Satz-15-mal-Umschreiben wieder. Für das definitiv schnellere fließend-schreiben-und-später-drüber-Iterieren Verfahren fehlt da wohl noch die Praxis. 

(Der ursprüngliche Plan, mit diesem Blog Schreib-Praxis zu sammeln, ist bisweilen aus Zeit- und Perfektionismus-Gründen nicht aufgegangen.)

Neben der Unsicherheit, worüber man bei solch einer Implementierungs-orientierten Arbeit im theoretischen Teil eigentlich schreiben soll, hatte ich anfangs vor allem die Schwierigkeit, das richtige Level für die Erklärungen zu finden. Prinzipiell sollte es zumindest für höhersemestrige Studierende eines Informatik-Bachelors möglich sein, alles allein durch Lesen der Arbeit zu verstehen. An manchen Stellen hat es sich dann jedoch doch etwas seltsam angefühlt, die für IT-Security-Interessierte allgegenwärtigen Konzepte einführend zu erklären. Dieses Problem hat sich jedoch bisher durch das Preliminaries-Kapitel gut lösen lassen. 

Wie gut mir das alles gelungen ist werden wir noch sehen. ;-)

# Feedback, please!

Die Arbeit ist zwar mittlerweile schon zu fortgeschritten, um alles über den Haufen zu werfen, und der Fokus ist auch eher fix. Solltet ihr dennoch Feedback haben, nur her damit! :-)

 <!-- ![openPGP, Diagramm (cc-by-sa) by me](http://2904.cc/blogimg/bakk/PGP.png) -->