## Lernziele
- [ ] [Sie kennen den Begriff der Codierung.](#Codierung)
- [ ] [Sie können Bit und Byte unterscheiden.](#Bit*vs.*Byte)
- [ ] [Sie können folgende Begriffe erklären:](#Codierung*Begriffe)
	- [ ] [Fano](#Fano-Bedingung)
	- [ ] [Binärcode](#Binärcode)
	- [ ] [Zeichenvorrat](#Zeichenvorrat)
	- [ ] [Redundanz](#Redundanz)
	- [ ] [Hammingdistanz](#Hammingdistanz) 
- [ ] [Sie erkennen, dass eine höhere Redundanz und eine grössere Hammingdistanz helfen, Übertragungsfehler zu erkennen.](#Höhere*Redundanz*und*grössere*Hammingdistanz)
- [ ] [Sie können Übertragungsfehler erkennen und eliminieren (mittels Hamming-ECC-Verfahren).](#Übertragungsfehler*erkennen*(Hamming-ECC-Verfahren))
- [ ] Sie verstehen die verschiedenen Arten von Binärcodes (ASCII, Unicode, BCD-Code, EAN-Code, 1 aus n-Code, UTF-8).     
- [ ] Sie kennen binäre, oktale und hexadezimale Zahlensysteme und können diese jeweils umrechnen.     
- [ ] Sie kennen Verfahren zur binären Codierung von Zahlen.
- [ ] Sie kennen Einsatzgebiete der unterschiedlichen Zahlensysteme in der Informatik.
- [ ] Sie kennen die logischen Operatoren OR, AND und NOT    
- [ ] Sie können mit Dualzahlen rechnen (Addition, Subtraktion, Multiplikation und Division)
## Codierung

Ein Computer kann **nur zwischen 0 und 1 unterscheiden**. Damit ein Computer Texte, Bilder, Musik oder Filme lesen und verarbeiten kann, müssen diese in ein `digitales Datenformat` umgewandelt werden.

![[./Resources/Pasted image 20240908144915.png]]

## Bit vs. Byte

- **Bit:** Ein Bit ist die kleinste Einheit digitaler Information und kann entweder den Wert 0 (falsch) oder 1 (wahr) haben.
- **Byte:** Eine Gruppe von 8 Bit ist ein Byte. Mit den 8 Zuständen eines Bytes lassen sich 256 (28) unterschiedliche Zustände abbilden.

![[./Resources/Pasted image 20240908150046.png]]
## Codierung Begriffe

### Fano-Bedingung

Die `Fano-Bedingung` bedeutet, dass **kein Codewort der Anfang eines anderen Codeworts sein darf.**

**Beispiel**
Der Code {0, 10, 110, 1110, 11110} erfüllt die Fano-Bedingung.
- "1110100" kann nur als "1110 10 0" gelesen werden.

Der **Morse-Code** erfüllt die Fano-Bedingung nicht, da unklar ist, wie **die Zeichen ohne Pausen** getrennt werden.

### Binärcode

Für die **Übersetzung von Informationen in digitale Daten** werden `Binärcodes` benötigt.

Binärcodes zeichnen sich durch folgende Eigenschaften aus:
-  Ein Binärcode verwendet den Ziel-Zeichenvorrat {0, 1}.
-  Alle Codewörter eines Binärcodes habe die gleiche Länge

### Zeichenvorrat

Der Zeichenvorrat enthält alle Codewörter eines Codes. Jedes Codewort besteht aus Zeichen des Ziel-Zeichenvorrats.

Um die maximale Anzahl der Zeichen im Zeichenvorrat zu berechnen, braucht man:
- Ziel-Zeichenvorrat
- Maximale Länge eines Codeworts

**Beispiel**
Bei Binärcodes gibt es zwei Zeichen im Ziel-Zeichenvorrat, und alle Codewörter haben die gleiche Länge. Deshalb wird nur die Länge eines Codeworts für die Berechnung benötigt.

Folgende Grafik zeigt den möglichen Zeichenvorrat für Binärcodes mit den Längen 1 Bit, 2 Bit und 3 Bit:
![[./Resources/Pasted image 20240908151602.png]]

### Redundanz

Daten sind dann redunant, wenn sie **ohne Informationsverlust** weggelassen werden können.

Redundanz ist gewollt, um Fehlererkennung und Fehlerkorrektur zu ermöglichen und dadurch die **Übertragungssicherheit** zu erhöhen.

>Redundanz bedeutet, dass man zusätzliche Informationen hat, die man eigentlich nicht braucht, um etwas zu verstehen. Es ist so, als ob man einen Satz mit mehr Wörtern schreibt, als nötig, aber den Satz trotzdem versteht, wenn man einige Wörter weglässt.

Bei einem Code beschreibt die Redundanz den Unterschied zwischen der maximal möglichen Anzahl von Codes und der tatsächlich verwendeten Anzahl.

**Zum Beispiel**
- Wenn ein Code **3 Bits hat**, aber **nur 2 Codewörter benutzt** werden, ist die Redundanz 2 Bits. Das bedeutet, dass **2 Bits weggelassen werden könnten**, ohne dass Informationen verloren gehen.
- Wenn **6 Codewörter benutzt werden**, braucht man fast **alle 3 Bits**, also ist die Redundanz kleiner, **weniger als 1 Bit.**

### Hammingdistanz

Die Hammingdistanz ist ein Mass für die **Unterschiedlichkeit** zweier Zeichenketten.

Genauer gesagt gibt sie an, wie viele Stellen (Bits oder Zeichen) sich zwischen zwei gleich langen Codewörtern unterscheiden.

Die Hamming-Distanz (auch Hamming-Abstand genannt) ist ein Maß dafür, wie unterschiedlich zwei Codewörter sind. Genauer gesagt gibt sie an, wie viele Stellen (Bits oder Zeichen) sich zwischen zwei gleich langen Codewörtern unterscheiden.

**Zum Beispiel**
- Codewort 1: `101010`
- Codewort 2: `100110`
Hier unterscheiden sich die beiden Codewörter an der **dritten** und **vierten** Stelle, also beträgt die **Hamming-Distanz 2**.

## Höhere Redundanz und grössere Hammingdistanz

Je höher die Hamming-Distanz des Codes ist, desto eher können Übertragungsfehler erkannt und teils sogar korrigiert werden.

#### Beispiel 1: Hamming-Distanz 1

Stell dir vor, wir haben zwei Codewörter mit einer Hamming-Distanz von **1**:

**Codewort A:** `1010`
**Codewort B:** `1011`

- Diese Codewörter unterscheiden sich nur an einer Stelle (der letzten).

- Wenn bei der Übertragung von **Codewort A** ein Bit fehlerhaft ist (z.B. das letzte Bit ändert sich von 0 zu 1), wird das empfangene Codewort zu **1011**, was dann nicht mehr von **Codewort B** unterscheidbar ist.

- Das bedeutet, der Fehler kann nicht erkannt oder korrigiert werden, weil die Hamming-Distanz nur 1 beträgt.

#### Beispiel 2: Hamming-Distanz 3

Jetzt haben wir zwei Codewörter mit einer Hamming-Distanz von **3**:

**Codewort A**: `101000`
**Codewort B**: `010111`

- Die Codewörter unterscheiden sich an drei Stellen.
- Wenn bei der Übertragung von **Codewort A** ein Bit fehlerhaft ist (z.B. das zweite Bit ändert sich von 0 zu 1), wird das empfangene Codewort zu **111000**. 
- Dieses neue Codewort ist immer noch klar von **Codewort B** unterscheidbar, weil sich **Codewort B** an weiteren Stellen unterscheidet.

Wenn nur ein oder zwei Fehler auftreten, kann der Empfänger also leicht erkennen, dass das empfangene Codewort nicht das richtige ist, und in vielen Fällen das ursprüngliche Codewort sogar korrigieren.


## Übertragungsfehler erkennen (Hamming-ECC-Verfahren)

**Hamming-ECC-Verfahren (Error Correction Code)** ist ein Fehlerkorrekturverfahren, um Übertragungsfehler in Daten zu erkennen und zu korrigieren.

#### Fehlererkennung ohne Korrektur

Die einfachste Methode für eine Fehlererkennung ist die **Paritätsprüfung**.
Dazu wird das Informationswort mit einem zusätzlichen Bit so erweitert, dass die Anzahl der mit 1 belegten Bits gerade (gerade Pariät) oder ungerade (ungerade Parität) ist.

Mit einem Paritätsbit lässt sich eine ungerade Anzahl von Bitfehlern erkennen. Eine Korrektur des Codeworts ist jedoch nicht möglich, da die Fehlerpositionen nicht identifziert werden können.

**Beispiel** (gerade Parität)
Erweitern Sie den Binärcode `1001001` um ein Paritätsbit, um eine **gerade Parität** zu erhalten:
$$
1 \oplus 0 \oplus 0 \oplus 1 \oplus 0 \oplus 0 \oplus 1 = 1
$$
Codewort mit Paritätsbit: 1001001**1**

**Beispiel** (ungerade Parität)
Erweitern Sie den Binärcode 1001001 um ein Paritätsbit, um eine **ungerade Parität** zu erhalten:

$$
\lnot ( 1 \oplus 0 \oplus 0 \oplus 1 \oplus 0 \oplus 0 \oplus 1 ) = 0
$$
Codewort mit Paritätsbit: 1001001**0**

### Fehlererkennung mit Korrektur
Wenn das fehlerhafte Bit identifiziert werden soll, benötigt man mehrere Paritätsbits.

**Hamming-Code**
Mit dem Hamming-Code werden Übertragungsfehler von 1 Bit erkannt und korrigiert.
Ein Hamming Codewort wird erzeugt, indem mehrere Paritätsbits geschickt in das Informationswort eingefügt werden.

1. Wir sollten die Positionen (2^0, 2^1, 2^2, 2^3 usw.) reservieren.
2. Wir schreiben unseren Binärcode wie gewohnt auf, lassen jedoch die oben genannten Positionen leer.![[./Resources/Pasted image 20240908161142.png]]
3. Dann notieren wir die Positionen, an denen eine 1 steht. (11, 6 und 3)
4. Wir berechnen die Binärdarstellung dieser Positionen (zum Beispiel hat die Position 3 eine 1, 3 in Binärform ist 0011).
5. Anschliessend führen wir für jede Positionsnummer in Binärform eine XOR-Operation durch.![[./Resources/Pasted image 20240908161403.png]]
6. Wir schreiben die XOR-Ergebnisse Bit für Bit von links nach rechts in unsere reservierten Paritätsbits. ![[./Resources/Pasted image 20240908161528.png]]
#### Fehlererkennung
Als Beispiel gibt es ein Problem bei der Position 3.
![[./Resources/Pasted image 20240908161730.png]]

1. Der Empfänger notiert sich die Positionen, an denen eine 1 steht.
2. Anschliessend führt er XOR-Operationen durch, genauso wie wir es zuvor gemacht haben.
3. Das Ergebnis der XOR-Operation zeigt, an welcher Position der Fehler aufgetreten ist.![[./Resources/Pasted image 20240908161933.png]]
4. Falls kein Problem aufgetreten wäre, müsste das Ergebnis **nur aus Nullen bestehen**.

