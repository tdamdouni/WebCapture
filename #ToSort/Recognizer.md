# Recognizer

_Captured: 2015-06-09 at 21:45 from [de.m.wikipedia.org](http://de.m.wikipedia.org/wiki/Recognizer)_

Ein **Recognizer** ([engl.](http://de.m.wikipedia.org/wiki/Englische_Sprache) _to recognize_: „erkennen"), auch **Erkenner**, ist in der [Informatik](http://de.m.wikipedia.org/wiki/Informatik) ein bestimmtes abstraktes Maschinenmodell, ein sogenannter [Automat](http://de.m.wikipedia.org/wiki/Automat_\(Informatik\)). Dieser Automat stellt auf Grundlage einer [formalen Grammatik](http://de.m.wikipedia.org/wiki/Formale_Grammatik) fest, ob ein konkretes [Wort](http://de.m.wikipedia.org/wiki/Wort_\(Theoretische_Informatik\)) Element einer [formalen Sprache](http://de.m.wikipedia.org/wiki/Formale_Sprache) ist oder nicht. Die Sprache wird dabei durch die zugrundegelegte formale Grammatik definiert bzw. erzeugt. Der _Recognizer_ entscheidet nur, ob ein Eingabetext hinsichtlich der Vorgaben „richtig" oder „falsch" ist; das unterscheidet ihn von einem [Parser](http://de.m.wikipedia.org/wiki/Parser), der zusatzlich die analysierte grammatikalische Struktur beschreiben und ausgeben kann. Ein typisches Beispiel fur einen _Recognizer_ in der [Automatentheorie](http://de.m.wikipedia.org/wiki/Automatentheorie) ist der [Kellerautomat](http://de.m.wikipedia.org/wiki/Kellerautomat).

In der Programmiersprache [Prolog](http://de.m.wikipedia.org/wiki/Prolog_\(Programmiersprache\)) konnen sogenannte _Definite Clause Grammars_ (DCG) dazu verwendet werden, um manche [kontextfreien Grammatiken](http://de.m.wikipedia.org/wiki/Kontextfreie_Grammatik) zu erstellen und zu verarbeiten. Angewandt auf die [maschinelle Sprachverarbeitung](http://de.m.wikipedia.org/wiki/Computerlinguistik) zeigt das folgende Beispiel einer DCG eine sehr einfache Grammatik, mit der eine kleine Menge deutscher Satze analysiert werden kann. Die Grammatikregeln legen fest, dass sich ein Satz aus einer [Nominal](http://de.m.wikipedia.org/wiki/Nominalphrase)\- (NP) und einer [Verbalphrase](http://de.m.wikipedia.org/wiki/Verbalphrase) zusammensetzt, die NP wiederum besteht aus einem [Artikel](http://de.m.wikipedia.org/wiki/Artikel_\(Wortart\)) und einem [Nomen](http://de.m.wikipedia.org/wiki/Nomen), wobei beide in [Numerus](http://de.m.wikipedia.org/wiki/Numerus) und [Genus](http://de.m.wikipedia.org/wiki/Genus) ubereinstimmen mussen. Im Lexikon werden die lexikalischen Einheiten als [Terminalsymbole](http://de.m.wikipedia.org/wiki/Terminalsymbol) definiert. Die Prolog-Abfrage _recognize('Liste von Wortern')_ setzt den _Recognizer_ in Gang, der entscheidet, ob eine Folge von Wortern auf Grundlage der modellierten DCG grammatisch ist oder nicht.
    
    
     % Grammatikregeln:
     satz          --> nominalphrase, verbalphrase.
     nominalphrase --> artikel(Numerus, Genus), nomen(Numerus, Genus). 
     verbalphrase  --> finites_verb. 
     
     % Lexikon:
     artikel(singular, maskulin) --> [der].
     artikel(singular, feminin)  --> [die].
     nomen(singular, maskulin)   --> [hund].
     nomen(singular, feminin)    --> [katze]. 
     finites_verb                --> [bellt].
     
     recognize(Satz) :- satz(Satz, []).
    

Die Anfrage an den _Recognizer_ ist erfolgreich (der Beispielsatz ist grammatisch):
    
    
     ?- recognize([der, hund, bellt]). 
     Yes
    

Die Anfrage an den _Recognizer_ ist nicht erfolgreich (der Beispielsatz ist ungrammatisch):
    
    
     ?- recognize([der, katze, bellt]). 
     No
    
