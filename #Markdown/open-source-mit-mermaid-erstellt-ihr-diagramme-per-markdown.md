# Open Source: Mit Mermaid erstellt ihr Diagramme per Markdown

_Captured: 2017-01-15 at 04:42 from [t3n.de](http://t3n.de/news/open-source-mermaid-diagramme-markdown-782717/?utm_source=t3n-Newsletter&utm_medium=E-Mail&utm_campaign=t3n%20Newsletter%20Nr.%20714%20-%20digital%20pioneers)_

![    Open Source: Mit Mermaid erstellt ihr Diagramme per Markdown
](http://img.t3n.sc/news/wp-content/uploads/2017/01/diagramme-per-markdown-mermaid.jpg?auto=compress%2Cformat&fit=crop&fm=jpg&h=347&ixlib=php-1.1.0&q=65&w=620&s=571b8e203ae7882393b670de2b6bd5c0)

> _(Grafik: Knut Sveidqvist)_

## Mermaid: Diagramme einfach beschreiben

[Markdown](http://t3n.de/news/eigentlich-markdown-478610/) hat sich in vielen Texteditoren durchgesetzt. Der Vorteil der Auszeichnungssprache liegt darin, dass damit formatierte Texte auch ohne Umwandlung leicht lesbar sind. Mermaid will dieses Konzept auf Diagramme ubertragen. Dazu wurde eine an [Markdown](http://t3n.de/tag/markdown) orientierte Syntax geschaffen.

Selbst einigermaßen komplexe Flussdiagramme, die mit Mermaid erstellt wurden, lassen sich auch in Textform noch recht gut verstehen. Dazu hier ein Beispiel aus der [offiziellen Dokumentation](https://knsv.github.io/mermaid/#usage):
    
    
    %% Sequence diagram code
    sequenceDiagram
        Alice ->> Bob: Hello Bob, how are you?
        Bob-->>John: How about you John?
        Bob--x Alice: I am good thanks!
        Bob-x John: I am good thanks!
        Note right of John: Bob thinks a long<br/>long time, so long<br/>that the text does<br/>not fit on a row.
    
        Bob-->Alice: Checking with John...
        Alice->John: Yes... John, how are you?
    

Von Mermaid gerendert wird aus dem Text das folgende Diagramm:

![Mermaid: Dieses Diagramm entsteht aus dem obigen Textbeispiel. \(Screenshot: knsv.github.io/mermaid/\)](http://t3n.de/news/wp-content/uploads/2017/01/diagramme-per-markdown-mermaid-1-620x433.jpg)

> _Mermaid: Dieses Diagramm entsteht aus dem obigen Markdown-Beispiel. (Screenshot: knsv.github.io/mermaid/)_

## Mermaid: Open-Source-Projekt bietet auch einen Online-Editor

Mermaid wurde ursprunglich von Knut Sveidqvist entwickelt und steht unter der MIT-Lizenz. Den Quellcode der Open-Source-Software findet ihr auf [Github](https://github.com/knsv/mermaid). Außerdem gibt es auch einen [Live-Editor](https://knsv.github.io/mermaid/live_editor/) im Web. Über den konnt ihr euch mit der Mermaid-Syntax vertraut machen und eigene Diagramme erstellen. Die konnt ihr dann als SVG-Datei herunterladen oder euren Diagramm-Entwurf per Link mit einem Kollegen teilen. Der kann dann auch selbst Hand anlegen und gegebenenfalls Verbesserungen vornehmen.

**Ebenfalls interessant:**
