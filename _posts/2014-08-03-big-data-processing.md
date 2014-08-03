---
layout: 	post
title: 		Wie verteilt man eigentlich Datenverarbeitung?
tags: 		[Tech]
published: 	true
---

Da ich mich letztes Semester im Zuge [einer Lehrveranstaltung](https://www.spsc.tugraz.at/courses/EW) und auch [darüber hinaus](https://www.coursera.org/course/ml) mit Machine Learning beschäftigt habe, war es naheliegend, mich auch im Sommer mit ***Daten*** zu beschäftigen. 

Nach dem Absolvieren [einiger Kurs](https://www.coursera.org/specialization/jhudatascience/) zum Thema "*Data Science*" bin ich (mal wieder) bei einer Frage gelandet, die ([nicht nur](http://techblog.netflix.com/2014/02/distributed-neural-networks-with-gpus.html)) mich seit längerem begleitet: Wie verteilt man eigentlich Arbeit auf mehrere Rechner?

Obwohl mir Antworten zu dieser Frage sowohl auf der Uni als auch bei anderen Recherchen bereits begegnet sind, hatte ich in meinen bisherigen Projekten nicht wirklich Gelegenheit, diese auszuprobieren geschweige denn produktiv einzusetzen. Im Zuge der Recherche bin ich dann schnell mal bei **[MapReduce](https://en.wikipedia.org/wiki/MapReduce)** und kurz darauf bei **[Apache Hadoop](https://en.wikipedia.org/wiki/Apache_Hadoop)** gelandet, mit dem ich mich letzte Woche ein wenig auseinandergesetzt habe. 

*(Dieser Artikel ist ein persönlicher Erfahrungsbericht und kein Tutorial; beinhaltet somit wohl nicht viel Information, die nicht auch andernorts besser aufbereitet zu finden ist.)*

## Apache Hadoop

Hadoop ist ein Framework für verteilte Software. Es regelt sowohl die Verteilung von Daten auf mehrere Rechner (Hadoop Distributed File System, HDFS) als auch die Verarbeitung dieser Daten mittels Ausführen von Software auf diesem Cluster (MapReduce). Da es sich um ein Framework handelt ist die eigentliche MapReduce-Programmlogik nicht Teil von Hadoop. Des weiteren gibt es einige Erweiterungen so wie auf Hadoop aufbauende Projekte, wie Datenbanken (zB [Apache HBase](https://hbase.apache.org/)) und Data-Warehouse ([Apache Hive](https://hive.apache.org/)) so wie Systeme zur einfacheren Konfiguration oder zum Monitoring.

Zur Einordnung: [Facebook's Hadoop-Cluster](http://de.scribd.com/doc/103621762/Big-Data-Whiteboard-082212) war 2012 über 100PB groß und 105TB davon waren mittels Hive in 30 Minuten scannbar.

## MapReduce

MapReduce ist ein Google-intern entwickeltes und 2004 [publiziertes](http://research.google.com/archive/mapreduce.html) Programmiermodell zur *verteilten* Verarbeitung von *großen* (Tera- bis Petabyte) Datenmengen. 

Das (vereinfachte) **Prinzip** dahinter: Die zu verarbeitenden Daten werden auf mehrere Rechner aufgeteilt (zB in einem Hadoop-Cluster oder mit Google's verteiltem Dateisystem). Jeder Rechner behandelt die ihm zugeordnete Teilmenge (*Map*-Schritt). Am Ende werden die erzeugten Daten gesammelt und an einem Punkt kombiniert (*Reduce*-Schritt). [Bin mir noch nicht sicher, ob das ein einfaches oder ein geniales Prinzip ist. Wohl beides.]

Sobald man den Datenverarbeitungsprozess also in Map- und Reduce-Programm aufgeteilt hat, ist der Vorgang vollautomatisch parallelisierbar. Das Management-Framework (zB Hadoop) nimmt einfach den Datensatz, teilt ihn in *n* Teile und weißt die Teilsets *n* Clustern zu. Anschließend wird auf allen *n* Clustern das Map-Programm gestartet. (In Amazon's Cloud geht dank [Elastic MapReduce](https://aws.amazon.com/de/elasticmapreduce/) sogar das starten & konfigurieren der einzelnen Rechner automatisch.)

### Ein Beispiel

Gegeben sei ein (sehr langer) Text. Gefragt ist, wie oft ein Wort in dem Text vorkommt. Gesucht ist also ein [Häufigkeitswörterbuch](https://de.wikipedia.org/wiki/Frequenzw%C3%B6rterbuch).

Von der Programmlogik her nicht besonders kompliziert:

{% highlight python %}
dict = {}
for word in text:
	if word in dict:
		dict[word] += 1
	else:
		dict[word] = 1
{% endhighlight %}

Das Ergebnis ist in diesem Fall (Python) ein [Dictionary](https://docs.python.org/2/tutorial/datastructures.html#dictionaries), also eine Liste von Key-Value-Pairs mit den vorkommenden Wörtern als Keys und der Anzahl wie oft ein Wort vorkommt als Value:

{% highlight python %}
…
'Systeme': 1, 
'wie': 4, 
'das': 3, 
'Frage': 2, 
'Hadoop': 3,
…
{% endhighlight %}

Dieses Beispiel wird in Tutorials häufig gewählt, da sich die Programmlogik sehr einfach aufteilen lässt. Das Beispiel ist sogar so einfach, dass der oben angeführte Code schon dem Mapper-Programm entspricht. Jeder Rechner berechnet also von seinem Teilset an Wörtern ein Häufigkeitswörterbuch. 

Im Anschluss muss der Master-Rechner, auf dem das Reducer-Programm läuft, nur noch alle diese Häufigkeitswörterbücher kombinieren (aufsummieren) und ein gemeinsames erstellen. Auch das ist in diesem Fall nicht besonders kompliziert: 

{% highlight python %}
reducerSet = {}

for setToAdd in mapperSets:
	for word, count in setToAdd.iteritems():
		if word in reducerSet:
			reducerSet[word] += count
		else:
			reducerSet[word] = count
{% endhighlight %}

Als Erweiterung wäre übrigens auch dieser Schritt parallelisierbar: Man kann mehrere Reduce-Rechner erstellen und zwischen Map- und Reduce- Schritt eine sogenannten *Partition Function* einbauen, welche jedem Reducer dann nur mehr "seine" Datensätze zuordnet. Im konkreten Beispiel könnte man für jedes Wort einen eigenen Reducer erstellen und jedem davon nur die Häufigkeiten "seines" Wortes zum aufsummieren zuweisen. (Für ein Häufigkeitswörterbuch ist das wohl wenig sinnvoll, für andere Anwendungsfälle aber manchmal schon.)

### Neues Paradigma?

Die Frage, ob das MapReduce Programmiermodell (immerhin schon 10 Jahre alt) ein neues Paradigma in der verteilten Verarbeitung großer Daten ist/war, kann ich momentan nicht beurteilen. Vor allem als Alternative zu bewährten relationalen Datenbanken scheint es aber zumindest für einige Anwendungsfälle eine Option. Die am [englischen Wikipedia-Artikel zu MapReduce](https://en.wikipedia.org/wiki/MapReduce#Criticism) aufgeführte Kritik von 2 Informatikern hierzu ist aber nachvollziehbar. Vor allem die Tatsache, dass man mit einem relationalen Datenbanksystem genauso MapReduce implementieren kann (zB Map-Schritt als Query auf mehreren Rechnern) ist ein interessanter Punkt.

Für Machine Learning scheint aber eher [Apache Spark](https://spark.apache.org/) relevant zu sein, das zwar auf Hadoop aufbaut, aber ohne MapReduce auskommt.


