# Swift Entwicklung – Ausgabeformat – Zahlenformatierung

_Captured: 2015-06-16 at 22:54 from [apfelcheck.de](http://apfelcheck.de/tutorials/swift-entwicklung-ausgabeformat-zahlenformatierung/)_

![](http://apfelcheck.de/wp-content/uploads/2015/02/caseual_leatherwallet_iphone6_case_leder_titel.png)

> _Review - Caseual Leather Wallet - iPhone 6 & 6 Plus Case aus Leder mit dezentem Design und integrierten Kartenfachern sowie Stand-Funktion_

![](http://apfelcheck.de/wp-content/uploads/2015/02/tizi_schlingel_lightning_kabel_titel.png)

> _Vorstellung - Tizi Schlingel - Lightning-Kabel fur unterwegs mit Flip-Technologie und weitere Alternativen_

![](http://apfelcheck.de/wp-content/uploads/2014/11/save.tv_online_recoder_titel.jpg)

> _Review - Online Videorecorder Save.TV mit iOS App und Download-Manager fur den Mac_

![](http://apfelcheck.de/wp-content/uploads/2014/11/twelvesouth_hirisedeluxe_titel.jpg)

> _Twelve South - Das neue Dock HiRise Deluxe fur iPad und iPhone bereits in Deutschland verfugbar_

![](http://apfelcheck.de/wp-content/uploads/2014/11/1_g4-sleeve-stone.png)

> _Review - WoodUp Airwolf - Massiver iPad Air Stander aus Walnussholz_

![](http://apfelcheck.de/wp-content/uploads/2014/10/woodup_airwolf_ipadair_ständer_holz_titel.png)

> _Review - WoodUp Airwolf - Massiver iPad Air Stander aus Walnussholz_

Umfangreichere Taschenrechner, zum Beispiel von HP, verfugen uber die Moglichkeit Zahlen auf verschiedene Art zu formatieren. Neben der Moglichkeit Zahlen auf eine bestimmte Anzahl von Stellen gerundet anzeigen zu konnen, kann man auch die technische und mathematische Darstellung mit einer Zehnerpotenz-Mantisse auswahlen. Weiter mochten wir heute das allgemeine Layout der App verbessern und es fur verschiedene Displayformate anpassen.

Wie bereits oben erwahnt, werden wir in der Anzeige drei verschiedene Anzeige-Modi implementieren. Einerseits eine Festkomma-Variante, bei der immer nur eine bestimmte Anzahl von Nachkommastellen angezeigt wird und ansonsten nach jeder Rechenoperation auch gerundet wird. Anschließend eine technische/naturwissenschaftliche Variante, die uber eine Zehnerpotenzdarstellung verfugt. Diese wird in Dreierschritten hoch-/runtergezahlt. Damit kann man dann mit den ublichen Maßeinheit-Prafixen rechnen, wie Kilo, Mega, Giga, Terra oder halt in die andere Richtung: Mili, Mikro, Nano, Pico usw. Zu guter Letzt noch die "normale" Darstellungsweise, bei der erst nach Über-/Unterschreitung eines vorgegegebenen Wertebereichs eine Zehnerpotenzdarstellung benotigt wird.

Dieses Verhalten wollen wir durch eine entsprechende implementierte Closures anstelle einer Klassenhierarchie erreichen. Es gabe naturlich auch noch viele andere Moglichkeiten das Verhalten so hinzubekommen, aber das Problem hat man nun bei der Programmierung immer wieder - nur selten gibt es ausschließlich einen Weg zum Ziel sprich der Implementierung eines Problembereiches. Man sollte sich halt die verschiedenen Moglichkeiten vor Augen fuhren und es nach mehreren Kriterien beurteilen. Diese sind: die Schlichtheit und Pragnanz der Implementierung, die Erweiterbarkeit und die Wartbarkeit des Codes.

## Was sind denn eigentlich Closures und wie implementiert man sie in Swift?

Closures sind namenlose Funktionen, die jedoch in einem Kontext z.B. einer anderen Funktion platziert sind. Man kann sie ein wenig mit anonymen Klassen von Java vergleichen, jedoch haben wir hier nur eine Methode und diese ist noch zusatzlich namenlos. Dafur kann man eine solche Funktion nicht nur einfach verwenden, sondern auch einer Variable zuordnen und uber diese Variable dann aufrufen. Somit kann man sagen, man ruft die Funktion uber deren Referenz auf. Der Einsatz solcher Closures ist vielfaltig. Von einer schnellen Implementierung eines Event-Handlers bis hin zum kontextabhangigen Aufruf ist vieles moglich. Wir werden die zweite Moglichkeit benutzen und eine von drei moglichen Methoden je nach Schalterstellung nutzen.

Zuerst platzieren wir einen weiteren Dreier-Schalter fur die verschiedenen Modi. Dahinter dann eine Box fur Anzahl der Stellen. Diese werden an der Mitte ausgerichtet. Nicht vergessen den Seitenverhaltnismodus wieder auf Any/Any zuruckzuschalten, da sonst die eingefugten Bedienelemente nur im gewahlten Modus erscheinen.

![Swift 9.1](http://apfelcheck.de/wp-content/uploads/2015/06/Swift-9.1.png)

> _[Swift 9.1](http://apfelcheck.de/wp-content/uploads/2015/06/Swift-9.1.png)_

Im Anschluss daran mussen wir unsere Methoden, die wir den Bedienelement-Events zuordnen, implementieren. Diese werden wie folgt kodiert:

@IBAction funcfloatFormatValueChanged(sender:UISegmentedControl){displayController!.floatFormatValue=Int8(sender.selectedSegmentIndex);}@IBAction functrailingPlacesCountChanged(sender:UITextField){if(sender.text.isEmpty){}vartext=sender.text!vartrailingPlaces=text.toInt()if(trailingPlaces>=0&&trailingPlaces<=9){displayController!.decimalPlaces=Int8(sender.text!.toInt()!);}else{sender.text=String(displayController!.decimalPlaces)}}

und werden den passenden Ereignissen zugeordnet.

![Swift 9.2](http://apfelcheck.de/wp-content/uploads/2015/06/Swift-9.2.png)

> _[Swift 9.2](http://apfelcheck.de/wp-content/uploads/2015/06/Swift-9.2.png)_

Analog passiert dies fur die Anzahl der jeweiligen Stellen. Hier haben wir mehrere Moglichkeiten. Wir entscheiden uns fur "Editing changed". An sich konnte man hier vielleicht besser ein +/- Element oder eine Combo-Box einbauen. Fur den Anfang wollen wir aber erst einmal eine normale Textbox verwenden. Auch hier konnte man wiederum mit einer abgeleiteten Textbox arbeiten, die ausschließlich Zahlen und dann nur eine davon akzeptiert. Fur den Anfang wollen wir jedoch den Aufwand moglichst klein halten und uns dem Thema "Closures" widmen.

![Swift 9.3](http://apfelcheck.de/wp-content/uploads/2015/06/Swift-9.3.png)

> _[Swift 9.3](http://apfelcheck.de/wp-content/uploads/2015/06/Swift-9.3.png)_

Die eigentliche Implementierung geschieht dann im Display Controller. Dort implementieren wir drei Formatter, die die gleichen Parameter und den gleichen Ruckgabewert aufweisen. Vorab werden fur zwei davon nur Variablen reserviert. Der Standardcontroller kann direkt an eine Konstante zugewiesen werden, da er auf keine Werte der aktuellen Instanz des Display-Controllers zugreifen muss und somit außerhalb des Kontexts der Instanz laufen kann.

letstandardFormatter={(value:Double,decimalPlaces:Int8)->Stringinifvalue==Double.infinity{}elseifvalue==Double.NaN{}returnNSString(format:"%f",value)asString}varfixedFormatter:(value:Double,decimalPlaces:Int8)->StringvarengineerFormatter:(value:Double,decimalPlaces:Int8)->String

Auch die Variable, die Closures des gerade aktiven Formatters beinhaltet, wird genauso definiert

Im Konstruktor, also der init-Methode werden die beiden anderen Formatter-Closures definiert. Kurioserweise beklagt sich der Compiler, wenn man direkt die Implementierung an eine leere Variable zuordnen will. Diese muss vorweg durch den konstanten Standard-Formatter vorbelegt werden, dann klappt es. Es ist definitiv ein Compiler-Fehler und meine Vorgehensweise nur ein Workaround und womoglich ist es auch bereits in einer der nachfolgenden Xcode-Versionen bereits behoben. Wir haben es bereits als Bug gemeldet und sind gespannt, was die Developer von Apple zu dem Thema schreiben.

init(_displayTextField:UITextField){currentFormatter=standardFormatterfixedFormatter=standardFormatterengineerFormatter=standardFormattercurrentValue=0decimalPlaces=9floatFormatValue=0fixedFormatter={(value:Double,decimalPlaces:Int8)->Stringinifvalue==Double.infinity{}elseifvalue==Double.NaN{}returnself.formatFixed(value,decimalPlaces:decimalPlaces)asString}engineerFormatter={(value:Double,decimalPlaces:Int8)->Stringinifvalue==Double.infinity{}elseifvalue==Double.NaN{}returnself.formatEngineer(value,decimalPlaces:decimalPlaces)}}

Die Umschaltung der Genauigkeit und des Formatters erfolgt uber didSet-Observer in den jeweiligen Property-Implementationen.

Der Aufruf des jeweiligen Formatters geschieht in der refreshDisplay() - Methode

Die Funktionalitat der Value-Property musste auch angepasst werden, da es jetzt keine einfache Methode mehr gibt, den Wert aus den angezeigten Ziffern zu konvertieren.

Somit musste auch der aktuelle Wert jeweils bei jedem Tastendruck neu berechnet und gegebenenfalls auch beim Negieren geandert werden.

Es ist noch einiges am neuen Code in den DisplayController eingeflossen. Da es weitestgehend Standard-Swift ist, wollen wir hier jetzt nicht naher darauf eingehen - man kann sich den Code ja genauer anschauen und die Neuerungen analysieren. In der nachsten Folge machen wir einen kurzen Exkurs in die Neuerungen von Swift 2 (sowie dem dazu passendem Xcode 7), welche wir aufgrund dessen, dass Swift 2 erst ab iOS 9 unterstutzt wird, noch nicht im Projekt verwenden konnen. Allerdings konnen wir uns damit problemlos im Playground beschaftigen, hierfur sollte Xcode 7 auf dem System installiert sein.

Verpasse keine Artikel mehr, hier sind unsere sozialen Profile. Danke fuers Folgen! [Twitter](https://twitter.com/apfelcheck_de) \- [ App.net](https://alpha.app.net/appleuser_de) \- [ Facebook](https://www.facebook.com/AppleUserDeutschland) \- [Google+](https://plus.google.com/b/104582887386945125404/104582887386945125404/posts) \- [Community](https://plus.google.com/u/0/communities/107972702385498602333) \- [RSS Feed](http://feeds.feedburner.com/Apfelcheck)
