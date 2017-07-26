# Einführung in JSON

_Captured: 2015-10-14 at 01:21 from [json.org](http://json.org/json-de.html)_

**JSON** (JavaScript Object Notation) ist ein schlankes Datenaustauschformat, das fur Menschen einfach zu lesen und zu schreiben und fur Maschinen einfach zu parsen (Analysieren von Datenstrukturen) und zu generieren ist. Es basierd auf einer Untermenge der [JavaScript Programmiersprache](http://javascript.crockford.com/), [Standard ECMA-262 dritte Edition - Dezember 1999](http://www.ecma-international.org/publications/files/ecma-st/ECMA-262.pdf).

Bei JSON handelt es sich um ein Textformat, das komplett unabhangig von Programmiersprachen ist, aber vielen Konventionen folgt, die Programmieren aus der Familie der C-basierten Sprachen (inklusive C, C++, C#, Java, JavaScript, Perl, Python und vielen anderen) bekannt sind. Diese Eigenschaften machen JSON zum idealen Format fur Datenaustausch.

JSON baut auf zwei Strukturen auf:

  * **Name/Wert Paare**. In verschiedenen Sprachen wird dies realisiert als ein Objekt (object), Satz (record), Struktur (struct), Worterbuch bzw. Verzeichnis (dictionary), Hash-Tabelle (hash table), Schlussel-Liste (keyed list) oder als ein assoziatives Array (associative array). 
  * **Eine geordnete Liste von Werten.** In den meisten Sprachen wird das als Array (array), Vektor (vector), Liste (list) oder Sequenz (sequence) realisiert. 

Hierbei handelt es sich um universelle Datenstrukturen, die von so gut wie allen modernen Programmiersprachen in der einen oder anderen Form unterstutzt werden. Es macht also Sinn, dass ein zwischen Programmiersprachen austauschbares Datenformat auch auf diesen Strukturen aufbaut.

In JSON gibt es:

**Ojekte**: Ein Objekt ist eine ungeordnete Menge von Name/Wert Paaren. Ein Objekt beginnt mit `{` (geschwungene Klammer auf) und endet mit `}` (geschwungene Klammer zu). Jedem Namen folgt ein `:` (Doppelpunkt) gefolgt vom Wert und die einzelnen Name/Wert Paare werden durch `,` (Komma) voneinander getrennt.

Ein **Array** ist eine geordnete Liste von Werten. Arrays beginnen mit `[` (eckige Klammer auf) und enden mit `]` (eckige Klammer zu). Werte werden durch `,` (Komma) voneinander getrennt.

Ein **Wert** kann ein Objekt, ein Array, eine Zeichenkette (string), eine Zahl oder einer der Ausdrucke `true`, `false` oder `null` sein. Diese Strukturen konnen ineinander verschachtelt sein.

![](http://json.org/value.gif)

Eine **Zeichenkette** besteht aus keinem (leere Zeichenkette) oder mehr Unicode Zeichen und wird von doppelten Anfuhrungszeichen umschlossen. Eine Zeichenkette kann Escape-Sequenzen mit einer besonderen Bedeutung enthalten. Ein einzelnes Zeichen wird durch eine Zeichenkette bestehend aus nur einem einzigen Zeichen dargestellt. Eine Zeichenkette (string) in JSON ist einer Zeichenkette in C oder Java sehr ahnlich.

![](http://json.org/string.gif)

Eine Zahl in JSON ist einer Zahl in C oder Java sehr ahnlich mit der Ausnahme, dass oktale und hexadezimale Zahlen nicht verwendet werden.

![](http://json.org/number.gif)

> _Leerzeichen konnen zwischen JSON-Elementen beliebig eingefugt werden._

It der Ausnahme einiger Details zur Enkodierung beschreibt das die gesamte Sprache.

```
object
{}
{ members }
members
pair
pair , members
pair
string : value
array
[]
[ elements ]
elements
value 
value , elements
value
string
number
object
array
true
false
null
string
""
" chars "
chars
char
char chars
char
any-Unicode-character-
    except-"-or-\-or-
    control-character
\"
\\
\/
\b
\f
\n
\r
\t
\u four-hex-digits
number
int
int frac
int exp
int frac exp
int
digit
digit1-9 digits 
- digit
- digit1-9 digits
frac
. digits
exp
e digits
digits
digit
digit digits
e
e
e+
e-
E
E+
E-
```
