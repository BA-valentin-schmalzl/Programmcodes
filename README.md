# Einsatzmöglichkeiten von künstlicher Intelligenz in der Bauschadensanierung
Die Dateien sind im Rahmen der Bachelorarbeit "Einsatzmöglichkeiten von künstlicher Intelligenz in der Bauschadensanierung" an der Hochschule Weihenstephan-Triesdorf entstanden. Betreuer der Arbeit ist Prof. Dr-Ing. Oliver Christ. Verfasser der Arbeit ist Valentin Schmalzl.

> ## Kurzfassung 
> Die Beurteilung von Schäden in Bauwerken der Abwassertechnik stellt einen hohen Arbeitsaufwand dar und erfordert qualifiziertes Personal. Die Entwicklung, die ein Teilbereich der künstlichen Intelligenz in den letzten Jahren durchlaufen hat, hat das Potential diese Schadensbeurteilung zu automatisieren. Dieser Teilbereich sind künstliche neuronale Netze.<br/><br/>
In der Arbeit wird die Theorie zu künstlichen neuronalen Netzen erläutert und auf die aktuelle Vorgehensweise bei der Schadensbeurteilung in Kanälen und Pumpwerken eingegangen. Es wird ein künstliches neuronales Netz entworfen, mit dem Ziel die Möglichkeiten und Probleme einer automatisierten Schadensbeurteilung in Pumpwerken, an einem praktischen Beispiel darzulegen. Anhand dessen wird eine Möglichkeit vorgestellt, wie eine automatisierte Schadensbeurteilung in Zukunft erfolgen kann und was noch zu erforschen ist, um dies umzusetzen.<br/><br/>
Die letztlich vorgestellte Möglichkeit zur automatischen Schadensbeurteilung basiert auf der Instance-Segmentation, mittels eines künstlichen neuronalen Netzes. Dabei werden Schäden auf Bildern automatisch pixelweise erfasst. Um die Möglichkeiten der Instance-Segmentation darzulegen wird diese ebenfalls praktisch, anhand von Schäden in Pumpwerken, umgesetzt.

## Anmerkungen
Im folgenden sind einige Anmerkungen zu verschiedenen Dateien zu finden.
### 2.1.3.3 Grundlage der Abbildung 6 & 2.1.3.3 Grundlage der Abbildung 7
Im Verlauf der Bachelorarbeit sind einige Convolutional neuronal Networks (CNN) entstanden. Die meisten um verschiedene Netzarchitekturen zu testen und zur Übung.
Zwei davon wurden schließlich verwendet um die Daten für die beiden Abbildungen 6 und 7 in der Bachelorarbeit zu erzeugen. Die Abbildungen wurden in Excel erstellt.

* Abbildung 6 zeigt wie die Überanpassung in CNNs zu erkennen ist. Das CNN ist daher so ausgelegt, dass eine Überanpassung gut erkennbar auftritt. Es wird kein Dropout und keine Regularisierung verwendet bei einem kleinen Netz mit wenig Daten. 
Die SeparableConv2 Schichten führen eine Faltung mit verschiedenen Fenstergrößen und Schrittweiten aus und führen das Ergebnis dieser Faltungen wieder zusammen ([eine genauere Erläuterung ist hier zu finden](https://arxiv.org/pdf/1610.02357.pdf)).

* Abbildung 7 zeigt die Verteilungsdichte der Werte der Gewichtungen, um das Ergebnis der Regularisierungsmethoden zu zeigen. In der aktuellen Datei ist dies, die l1 Regularisierung. Die Gewichtungen der untersuchten Schicht werden ab Zeile 120 ausgelesen und in einer csv-Datei hinterlegt. Die [Batch Normalization](https://arxiv.org/pdf/1502.03167.pdf) in Zeile 85 hat einen änhlichen Effekt wie die l2 Kernel Regularisierung. Somit sind die Verteilungsdichtekurven ähnlich skaliert und die Darstellung der Kurven in der Abbildung ist verbessert.  

### 4.1 Train and Evaluate_VGG16 & 4.3 Train and Evaluate_Xception
Beiden Dateien liegt der selbe Code zugrunde. Es wird lediglich das vortrainierte Model ausgetauscht und die Schicht ab der das Modell neu trainiert werden soll verändert. Ein großer Teil des Codes dient dabei der Datenauswertung und der Kreuzvalidierung. Es werden Daten zu der TOP 1 und TOP 2 Vorhersage und zu der vom Modell berechneten Wahrscheinlichkeit je Vorhersage, gesammelt. Die Daten werden für jedes der 5 trainierten CNNs (Kreuzvalidierung) in einer csv-Datei gespeichert. Es lassen sich anhand der Daten zum Beispiel die Korrektklassifizierungsraten je Kategorie und je Klasse berechnen. Zudem sind einige weiterführenden Auswertungen der Daten möglich. Diese Auswertung fand letztlich keinen Eingang in die Bachelorarbeit da die Datenmenge, aufgeteilt nach Klasse oder Kategorie, zu gering ist für eine relevante Schlussfolgerung.  

### 5.1 Trainieren_Mask R-CNN & 9.2 Masken erstellen mittels Mask R-CNN
Beide Dateien basieren weitgehend unverändert auf der Programmbibliothek, zur Verwendung von Mask R-CNN mit Python und Keras von Matterport Inc., geschrieben von Waleed Abdulla (siehe: https://github.com/matterport/Mask_RCNN) 
