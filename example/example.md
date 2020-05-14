---
# Das ist der YAML-Header. Hiermit wird das Dokument konfiguriert

# Meta-Daten zum Dokument
title: Das beste Paper der Welt
author: Hannes Dröse
date: 14.05.2020
abstract: |
    Ein Abstract ist eine ganz kurze Zusammenfassung der wesentlichen Inhalte des Papers. Es ist i.d.R. ein einziger Absatz ohne irgendwelche Formatierungen.

# Quellen im BibTex-Format
bibliography: example.bib # Leider funktioniert das hier nicht, ich weiß aber noch nicht warum
nocite: | # Diesen Eintrag entfernen, wenn nur die Quellen im Quellenverzeichnis gelistet werden sollen, die tatsächlich im Dokument verwendet worden sind
    @*

# Formatierung des Dokuments
lang: de # Sprache
documentclass: report # Hier die Dokumentenklasse eintragen. Die wird häufig vorgegeben.

# Hier können nun weitere Aspekte konfiguriert werden. Meist ist das nicht nötig, weil die Dokumentenklasse das macht.
papersize: a4
geometry: # Ränder
    - top=3cm
    - bottom=3cm
    - left=3cm
    - right=3cm
toc: true # Table of contents an- oder ausschalten
lof: true # List of Figures, also Abbildungen
lot: true # List of Tables
links-as-notes: true # Dadurch werden Links nochmal als Fußnote dargestellt

# hier zusätzliche Abhängigkeiten z.B. für LaTeX Packages definiert werden
header-includes: |
    \pagenumbering{Roman}

    \usepackage{tikz}
    \usetikzlibrary{trees}

# Ende des YAML-Headers
---

# Einleitung

<!-- Sorgt dafür, dass die Nummerierung hier wieder neu startet -->
\pagenumbering{arabic}
\setcounter{page}{1}
<!-- Sorgt dafür, dass die Nummerierung hier wieder neu startet -->

So einfach ist das Schreiben in Markdown.

Das ist der der zweite Absatz. Man muss nur in Markdown eine Zeile frei lassen, um Absätze von einander zu trennen.

# Überschriften

## Unterüberschrift

Für Überschriften einach ein # am Anfang der Zeile einfügen. Für verschiedene Hierarchien in den Überschriften einfach mehrere # verwenden.

## Unterüberschrift 2

### Unter-Unterüberschrift 1

Markdown erlaubt eine Staffelung in bis zu 6 Ebenen (also 6 mal #)

### Unter-Unterüberschrift 2

Überschriften müssen nicht manuell nummeriert werden. Die Nummerierung kann zentral an und ausgeschaltet werden.

# Innertextliche Formatierung

Markdown erlaubt verschiedene Formatierungsarten innerhalb eines Absatzes. So kann man z.B. Wörter **fett markieren.** Ebenso ist _kursiv möglich._ Oder auch ***beides gleichzeitig***

Wörter können auch durchgestrichen werden ~~auch wenn man das nicht so gut lesen kann~~

Außerdem ist ^hochstellen^ und ~tiefstellen~ möglich.

# Trennlinien

Sind sehr einfach einzufügen:

---

Fertig.

# Verlinkungen und Fußnoten


Links funktionieren sehr einfach, nämlich so: [angezeigter Text](https://pandoc.org/MANUAL.html)

## Verlinkungen vom Überschriften {#tag}

Eine Überschrift kann einfach mit einem Link referenziert werden. [Zur Einleitung](#einleitung).

Damit man sich da nicht einen Wolf schreibt, kann man Überschriften auch einen Tag geben. Dazu einfach hinter die Überschrift `{#tag}` anfügen. Nun reicht es im Link den Tag anzugeben: [zur Überschrfit](#tag)

## Fußnoten

Man kann auch Fußnoten erstellen mittels Zahlen [^1] oder auch mit Wörtern.[^longnote]

[^1]: Die Fußnote muss nun irgendwo im Dokument definiert werden.
[^longnote]: Es ist ziemlich egal wo. Ganz am Ende oder doch direkt darunter. Wie es bliebt.

# Code

Code kann entweder `print('innerhalb eines Absatzes')` verwendet werden. Oder es kann ein ganzer Code-Block eingefügt werden.

```sh
echo "Hello World"
```

Um Markdown mitzuteilen, um welche Programmiersprache es sich handelt, einfach die Dateiendung in der ersten Zeile des Code-Blocks nach den 3 `-Zeichen einfügen. Dadurch wird auch im PDF die Syntax farbig markiert.

Ein paar Beispiele in verschiedene Programmiersprachen:

## C++

```cpp
#include <iostream>

int main(int argc, char* argv[]) {
    std::cout << "Wie wäre es mit C++?" << std::endl;

    return 0;
}
```

## Java

```java
public class Main 
{
       public static void main (String[] args)
       {
             System.out.println("Java ist nicht nur eine Insel");
       }
}
```

## GoLang

```go
package main

import "fmt"

func main() {
    fmt.Println("So sieht zum Beispiel Code in GoLang aus.")
}
```

## HTML

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML-Code</title>
</head>
<body>
    <p>Das ist ja genial!</p>
</body>
</html>
```

# Mathmatische Formeln

Es gibt die Möglichkeit in Markdown mathematische Formeln aus zu drücken. Ähnlich wie beim Code geht das sowohl innerhalb des Fließtextes $\Sigma i = \frac{n(n+1)}{2}$. Oder als eigener Formell-Block:

$$
a(m,n) =
\begin{cases}
    n + 1                &, m = 0 \\
    a(m - 1, 1)          &, m > 0, n = 0 \\
    a(m - 1, a(m, n - 1) &, m > 0, n > 0
\end{cases}
$$

Für die Formeln wird die **LaTeX Math Syntax** verwendet.

# Listen

Es git die Möglichkeit von Stichpunktlisten:

- ein Punkt
- ein weitere Punkt
  - ein Unterpunkt
  - ist ebenfalls möglich
- ganz simpel

Oder nummerierte Listen:

1. erster Punkt
2. zweiter Punkt
   1. auch hier kann
   2. verschachtelt werden
3. Einfach genial!

So funktioniert es ebenfalls:

#. erster Punkt
#. zweiter Punkt
   #. auch hier kann
   #. verschachtelt werden
#. Einfach genial!

Mehr dazu unter: [hier](https://pandoc.org/MANUAL.html#lists)

# Bilder und Grafiken

Bilder werden sehr ähnlich wie Links eingefügt:

![Das Logo von Markdown](markdown_logo.jpg)

Es gibt außerdem die Möglichkeit zum Beispiel die Größe einer Abbildung zu beeinflussen:

![Das Logo von Markdown etwas kleiner](markdown_logo.jpg){ width=30% }

Es gibt auch die Möglichkeit Grafiken mit LaTeX zu erstellen. Zum Beipiel mit dem Package "tikz". Damit kann man zum Beispiel mittels Code Grafiken erzeugen.

Man kann einfach den LaTeX-Code direkt hier ins Markdown einfügen und das wird entsprechend gerendert. Dazu muss natürlich das LaTeX-Package inkludiert sein (siehe YAML-Header am Anfang des Dokuments)

\begin{figure}
\centering
\begin{tikzpicture}
  \node {max}
    child {node {$+3$}}
    child {node {min}
    child {node {$-2$}}
      child {node {$\vdots$}}
    };
\end{tikzpicture}
\caption{Alpha-Beta Pruning. Bereits wenn Min die -2 entdeckt, ist klar, dass Max sich niemals für den rechten Zweig entscheiden wird.}
\label{fig:ab-pruning}
\end{figure}

Nicht wundern, wenn die Bilder und Grafiken nicht genau an der gleichen Stelle dargestellt werden wie im Markdown deklariert. LaTeX versucht Grafiken möglichst geschickt zu platzieren.

# Tabellen

Es gibt viele verschiedene Arten, Tabellen zu erzeugen.

## Simple mit Header

  Right     Left     Center     Default
-------     ------ ----------   -------
     12     12        12            12
    123     123       123          123
      1     1          1             1

: Eine einfache Tabelle mit Header

## Simple ohne mit Header

-------     ------ ----------   -------
     12     12        12             12
    123     123       123           123
      1     1          1              1
-------     ------ ----------   -------

: Eine einfache Tabelle ohne Header

## Tabellen mit mehrzeiligen Einträgen und ohne Beschreibung

-------------------------------------------------------------
 Centered   Default           Right Left
  Header    Aligned         Aligned Aligned
----------- ------- --------------- -------------------------
   First    row                12.0 Example of a row that
                                    spans multiple lines.

  Second    row                 5.0 Here's another one. Note
                                    the blank line between
                                    rows.
-------------------------------------------------------------

## Pipe-Tables

PipeTables sind eine sehr kondensierte Form der Tabellen

| Right | Left | Default | Center |
|------:|:-----|---------|:------:|
|   12  |  12  |    12   |    12  |
|  123  |  123 |   123   |   123  |
|    1  |    1 |     1   |     1  |

: Demonstration der Pipe-Table Syntax.

Pipe-Table können sehr stark abgekürzt werden. Sieht war nicht mehr so schön aus in Markdown, im PDF dann aber schon.

fruit| price
-----|-----:
apple|2.05
pear|1.37
orange|3.09

# Zitate

Wörtliche Zitate können in einem sog. Blockquote geschrieben werden.

> Vom Eise befreit sind Strom und Bäche \
> Durch des Frühlings holden, belebenden Blick; \
> Im Tale grünet Hoffnungsglück; \
> Der alte Winter, in seiner Schwäche, \
> Zog sich in rauhe Berge zurück.
> 
> *Osterspaziergang – Johann Wolfgang von Goethe*

Darüber hinaus können Quellen in einer sog. BibTex-Datei gespeichert werden. Siehe dazu die Datei `example.bib`. Das BibTex Format zu einem Buch kann zum Beispiel über [Google Scholar](https://scholar.google.com) gesucht werden.

BibTex-Einträge haben alle einen eigenen Tag und dieser kann hier eingefügt werden. [@drose2020]

Dabei ist es üblich, wenn man nicht wortwörtlich zitiert hat "vgl." zu schreiben. [vgl. @drose2020]

Da gibt es noch einige Optionen dazu: [siehe hier](https://pandoc.org/MANUAL.html#citations)

# Quellen {-}

\pagenumbering{Roman}
\setcounter{page}{1}

<!-- Quellen werden hier automatisch angefügt -->