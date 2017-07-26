# Alexa, schalte ZDF ein

_Captured: 2017-05-10 at 21:57 from [blogs.itemis.com](https://blogs.itemis.com/de/alexa-schalte-zdf-ein?utm_source=hs_email&utm_medium=email&utm_content=51748968&_hsenc=p2ANqtz--vDsPLpeRLlzmVXbsw3qMybTBwpFcVkgs6Lp5WeCevOVq4B3pDkCs2jftPK7NpwFuRxeGJnrSdfepNVprG24VlA2f7OA&_hsmi=51749262)_

Wer von euch kennt das nicht? Ihr seht gerade fern und wollt umschalten, allerdings liegt die Fernbedienung mehrere Meter weit weg oder irgendwo unter Kissen begraben. Was ist also naheliegender als Alexa darum zu bitten, auch den Fernseher zu steuern? Vorausgesetzt, der Fernseher oder Receiver ist smart und uber's Netzwerk steuerbar.

![alexa-schalte-zdf-ein.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Embedded/alexa-schalte-zdf-ein.jpg?t=1494425153587&width=362&height=172&name=alexa-schalte-zdf-ein.jpg)

Die erste Anlaufstelle ist der [Skill Store](https://www.amazon.de/b?ie=UTF8&node=10068460031), doch dort gibt es nur Skills, um das Fernsehprogramm zu erfragen. Die zweite Anlaufstelle ist Google, und da ergeben sich mehrere Moglichkeiten - via Skills die (noch) nicht auf Deutsch erhaltlich sind und zusatzliche Hardware benotigen, z.B. ein [Harmony Hub](https://www.cnet.com/how-to/how-to-logitech-harmony-amazon-alexa-echo/) oder [AnyMote](https://www.anymote.io/tutorials/tutorial-how-to-control-your-tv-with-amazon-echo). Allerdings muss bei AnyMote stets der Name des Skills mit genannt werden:

  * Alexa, tell AnyMote to Volume UP 5 times on my TV
  * Alexa, tell AnyMote to CHANNEL ONE HUNDRED AND TWENTY TWO

Der Harmony Hub Skill scheint etwas cleverer zu sein, er erlaubt zumindest folgende Phrasen:

  * Alexa, turn on Netflix/Hulu/HBO
  * Alexa, turn off the TV

Befehle zur Lautstarkeregelung versteht Alexa allerdings fur das eigene Gerat (Echo/Dot), daher ist dafur die Nennung des Skills unumganglich:

  * Alexa, tell Harmony to (raise/increase/lower/decrease) the volume
  * Alexa, tell Harmony to mute/unmute

Um diese Skills nutzen zu konnen, mussten wir unseren Amazon-Account auf Englisch umstellen - was wir naturlich nicht wollen. Falls ihr ein Harmony Hub besitzt, konnt ihr auch [dieser Anleitung](https://www.amzecho.de/wiki/anleitungen:smart_home:harmony_yonomi_senderwahl) folgen. Ansonsten bleibt uns aktuell nichts anderes ubrig als zu warten, bis diese Skills auch auf Deutsch verfugbar sind - oder wir programmieren uns unseren eigenen Skill.

## Smart und Custom als sinnvolle Skill-Kombi

Hierzu ist zunachst ein kleiner Exkurs notwendig, um zu verstehen, wie Alexa erweitert werden kann. Es gibt vier Kategorien, in die sich Alexas Fahigkeiten einteilen lassen:

  1. Built-in Fahigkeiten (keine expliziten Skills), die von Amazon kontrolliert und direkt implementiert werden. Zum Beispiel [Wetterabfragen](https://www.amazon.de/gp/help/customer/display.html?nodeId=201549880), [Wissensfragen](https://www.amazon.de/gp/help/customer/display.html?nodeId=201549800), [Kalender](https://www.amazon.de/gp/help/customer/display.html?nodeId=201810470)\- und [ToDo-Listen](https://www.amazon.de/gp/help/customer/display.html?nodeId=201549900)-Zugriff, [Easter Eggs](http://www.go-gadget.de/gadgets/amazon-echo-coole-hacks-tipps-easter-eggs/), etc.
  2. Installierbare [Nachrichten-Skills](https://www.amazon.de/s/ref=nb_sb_noss?url=node%3D10536651031) fur die [tagliche Zusammenfassung](https://www.amazon.de/gp/help/customer/display.html?nodeId=201601880).
  3. Installierbare [Smarthome-Skills](https://www.amazon.de/s/ref=nb_sb_noss?url=node%3D10536655031) um [IoT-Gerate direkt zu steuern](https://www.amazon.de/alexasmarthome).
  4. Installierbare [Custom-Skills](https://www.amazon.de/skills) um komplexere Dialoge, Abfragen oder Steuerungen durchzufuhren.

Die Built-in-Fahigkeiten (1) sind vordefinierte Fragen und Phrasen, an denen wir nicht rutteln konnen. Nachrichten-Skills (2) bieten lediglich Inhalte an, die in der taglichen Zusammenfassung mit ausgegeben werden, bieten aber keinerlei Interaktion.

Smarthome-Skills (3) mussen sich an bestimmte [Konventionen](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/overviews/understanding-the-smart-home-skill-api) halten und erlauben es, Dinge ein oder aus zu schalten und Temperaturen zu regeln (in Zukunft werden sicherlich noch [weitere Funktionen](https://developer.amazon.com/blogs/post/2cb7be43-749f-497d-aa8c-0607a25938f7/announcing-lock-control-and-query-for-smart-home-skills) auf Deutsch hinzukommen). Custom-Skills (4) erlauben es mittels eines Keywords in ein sprachliches Submenu einzutauchen, in dem man vollstandige Kontrolle uber die gesprochenen Phrasen hat.

Letzteres hat einige Vor- aber auch Nachteile:

**Vorteile**

**Nachteile**

Beliebige Phrasen sind moglich.

Der Nutzer muss sich das Keyword merken, um den Custom-Skill zu verwenden.

Reservierte Phrasen sind moglich, wie z.B. _Lauter_, _Ton aus_, _Was gibt's Neues?_

Innerhalb des Skills konnen (bis auf einige Ausnahmen) keine anderen Fahigkeiten verwendet werden.

Komplexe Dialoge inkl. Ruckfragen sind moglich.

Die Phrasen inkl. Keyword konnen sehr lang werden; Beispiel:  
_"Alexa, sage Magenta Smarthome, die Rollladen im Wohnzimmer auf funfzig Prozent zu stellen"._

Ein Custom-Skill ist zustandsbasiert, d.h. er kann sich Dinge "merken".

Um beliebige Phrasen korrekt zu erkennen, ist eine umfangreiche Spezifikation der Interaktion mit dem Custom Skills erforderlich (betrifft die Skill-Entwickler).

Die Phrasen fur unsere Fernsehersteuerung sollen so einfach und intuitiv wie moglich sein. Unser Ziel ist es, Kanale zu wechseln und die Lautstarke zu regulieren. Jetzt konnen wir naturlich alle Funktionen als Custom-Skill implementieren (was immer das Skill-Keyword erfordert). Setzen wir das Keyword auf _Fernseher_, sollte folgendes moglich sein:

  * Alexa, sage Fernseher lautlos/Ton aus/mute
  * Alexa, sage Fernseher Lautstarke 10
  * Alexa, sage Fernseher Kanal rauf/hoch/runter

Zusatzlich konnen wir aber auch die Smarthome-Phrasen missbrauchen, um Kanale in Form von virtuellen Geraten zu schalten:

  * Alexa, schalte ARD/ZDF/... ein
  * Alexa, schalte Fernseher aus

## Ab in die Cloud!

Die o.g. Skills fur Harmony Hub oder AnyMote sind Out-of-the-Box-Losungen, erfordern besagte Gerate - und sind noch nicht auf Deutsch erhaltlich. Fur eine eigene Losung wird, wie fur jeden Skill ubrigens, auch fur die beiden gerade genannten, ein Server in der Cloud benotigt.

Wir fuhren das Ganze fur [openHAB](http://www.openhab.org/) mittels des Cloud-Service [myopenhab](https://myopenhab.org/) durch, das sollte jedoch auch auf andere Dienste adaptiert werden konnen. Voraussetzung ist, dass der zu steuernde Fernseher (oder Receiver) in openHAB uber [Items](http://docs.openhab.org/configuration/items.html) zur Kanalwahl und Lautstarkeregelung konfiguriert ist (z.B. via Bindings [LG Netcast](http://docs.openhab.org/addons/bindings/lgtv1/readme.html), [LG WebOs](https://github.com/sprehn/openhab2-addons/releases/), [Panasonic](http://docs.openhab.org/addons/bindings/panasonictv1/readme.html), [Philips](http://docs.openhab.org/addons/bindings/jointspace1/readme.html), oder [Samsung](http://docs.openhab.org/addons/bindings/samsungtv/readme.html)).

Falls es fur euren Fernseher oder Receiver kein solches Binding gibt, die Steuerung ubers Netzwerk aber z.B. durch einen Konsolenbefehl oder Script moglich ist, konnt ihr immer noch das [exec-Binding](http://docs.openhab.org/addons/bindings/exec/readme.html) zur Steuerung verwenden.

Ein Teil unseres Vorhabens kann nun bereits automatisiert durchgefuhrt werden, denn es gibt glucklicherweise schon einen [Smarthome-Skill fur openhab](https://www.amazon.de/openHAB-Foundation/dp/B01MTY7Z5L). Die Sourcen sind in diesem [git-Repository](https://github.com/openhab/openhab-alexa) verfugbar, wo auch erklart wird, [wie Gerate in openHAB konfiguriert werden mussen](https://github.com/openhab/openhab-alexa#item-configuration), damit sie von Alexa gefunden werden.

In unseren Fall benotigen wir drei Items fur Lautstarke und Senderwahl, und einige virtuelle Items (die nicht direkt ein Gerat reprasentieren) fur den Smarthome-Skill:
    
    
    Switch TV_Power "Fernseher" ["Lighting"] { channel="..." } // used to switch TV on and offString TV_Channel { channel="..." } // used to switch TV channelsNumber TV_Volume { channel="..." } // used to set TV volumeSwitch TV_Mute { channel="..." } // used to (un)mute TVSwitch TV_Channel_ARD "ARD" ["Lighting"] // virtual item to allow Alexa to directly switch to a channelSwitch TV_Channel_ZDF "ZDF" ["Lighting"] // virtual item to allow Alexa to directly switch to a channelSwitch TV_Channel_WDR "WDR" ["Lighting"] // virtual item to allow Alexa to directly switch to a channel...

Fangen wir mit dem Smarthome-Skill an:  
Mittels _Tags_ (in eckigen Klammern) wird ein Switch-Item als schaltbares Gerat gekennzeichnet ("Lighting", angelehnt an die [Homekit-Notation](http://docs.openhab.org/addons/io/homekit/readme.html): 'A lightbulb, _switchable_, dimmable, or rgb') und kann deshalb von Alexa erkannt werden.

Ein Satz von Regeln reagiert darauf, sobald ein virtuelles Item von Alexa geschaltet wird und fuhrt dann die eigentliche Senderwahl durch (der tatsachliche Command hangt vom verwendeten Binding ab):
    
    
    rule "tv ard" when Item ARD received command then TV_Channel.sendCommand("1") end
    rule "tv zdf" when Item ZDF received command then TV_Channel.sendCommand("2") end
    rule "tv wdr" when Item WDR received command then TV_Channel.sendCommand("15") end...

Lasst man nun Alexa seine [smarten Gerate erkennen](https://www.amazon.de/gp/help/customer/display.html?nodeId=201749240), sollten alle definierten Sender gefunden und in der App als Gerate gelistet werden:

  * Alexa, erkenne Gerate.
  * Suche abgeschlossen. Ich habe 8 Smarthome Gerate gefunden..
  * Alexa, schalte ARD ein.
  * OK.
  * Alexa, schalte ZDF ein.
  * OK.
![alexa-smart-home-meine-geräte.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Embedded/alexa-smart-home-meine-gera%CC%88te.png?t=1494425153587&width=246&name=alexa-smart-home-meine-gera%CC%88te.png)

Sehr schon, die Senderwahl ist mittels uberaus einfacher Phrasen realisiert.

## Wir bauen uns einen Custom-Skill

Etwas umfangreicher ist die Definition des Custom-Skills zur Lautstarkeregelung, denn dafur gibt es noch keinen vordefinierten Skill. Daher nutzen wir das [Alexa Skill Kit](https://developer.amazon.com/alexa-skills-kit) (ASK) und eine eigene Lambda-Funktion in den [Amazon Web Services](https://aws.amazon.com/de/lambda/) (AWS), um unser Vorhaben zu realisieren.

Als erstes erstellen wir die Funktion zum Setzen der openHAB-Items via myopenhab (falls euch die Schritte zu knapp ausfallen, [hier](http://robinhenniges.com/de/tutorial-alexa-skills-kit-deutsch) oder [hier](https://www.youtube.com/watch?v=AxYSqu8CXCI) sind sie in ahnlicher Weise etwas detaillierter beschrieben):

  1. Bei [aws.amazon.com](https://aws.amazon.com) (kostenlos) anmelden.
  2. In der [AWS Management Console](https://console.aws.amazon.com/) rechts oben die Region auf 'EU (Ireland)' umschalten.
  3. Links oben unter '_Services_' - '_Lambda_' - '_Functions_' - '_Create a Lambda Function_' - '_Blank Function_' - als Trigger: '_Alexa Skills Kit_'.
  4. Name: '_Fernseher_', Runtime: '_Node.js 4.3_', Role: '_Create new role from template(s)_' ('_lambda_basic_execution_').
  5. Copy & replace JavaScript Code von hier in den Editor im Browser und setze USER und PASSWORD (keine Bange, der Code ist ausschließlich in eurem privaten Amazon Account gespeichert und [kann von niemand anderem eingesehen werden](https://blogs.itemis.com/de/alexa-wer-ist-der-boss)):  
  

    
        /*
    * The purpose of this code is merely to demonstrate how to control your TV
    * volume via https://myopenhab.org with an Alexa custom skill. Adjust the
    * constants at the top to your setup. Please note that the code is a prototype
    * and is neither thoroughly tested, nor does it do proper error handling.
    * The code is based on the ‘alexa-skills-kit-color-expert’ template.
    */'use strict';  
    const USER = "max@mustermann.de"; // email address for myopenhab.orgconst PASSWORD = "mustermann123"; // password for myopenhab.orgconst ITEM_POWER = "TV_Power"; // openhab item for TV powerconst ITEM_VOLUME = "TV_Volume"; // openhab item for TV volumeconst ITEM_MUTE = "TV_Mute"; // openhab item for muting TVvar https = require('https');// --------------- Helpers that build all of the responses -----------------------function buildSpeechletResponse(spokenText, shouldEndSession) {
       return { // no image and no card, just voice
           outputSpeech: {
               type: 'PlainText',
               text: spokenText
           },
           shouldEndSession
       };}function buildResponse(sessionAttributes, speechletResponse) {
       return {
           version: '1.0',
           sessionAttributes,
           response: speechletResponse
       };}// --------------- Functions that control the skill's behavior -----------------------function setTVCommand(callback, item, value) {
       const options = {
           hostname: "myopenhab.org",
           port: 443,
           path: "/rest/items/" + item + "/state",
           method: "PUT",
           auth: USER + ":" + PASSWORD,
           headers: {}
       };
       options.headers['Content-Type'] = 'text/plain';
       options.headers['Content-Length'] = value.length;
       // console.log("request options: " + JSON.stringify(options));
       var req = https.request(options, function (response) {
           var body = '';
           if (response.statusCode === 200 || response.statusCode === 201 || response.statusCode === 202) {
               callback({}, buildSpeechletResponse('OK', true));
           } else {
               console.log("Fehler in https request (" + response.statusCode + "): ", response);
               callback({}, buildSpeechletResponse('Unerwarteter Return Code: ' + response.statusCode, true));
           }
           response.on("error", function (e) {
               console.log("request error: " + JSON.stringify(e));
               callback({}, buildSpeechletResponse('Unerwarteter Fehler: ' + e.message, true));
           });
       });
       req.write(value);
       req.end();}// --------------- Events -----------------------/**
    * Called when the session starts.
    */function onSessionStarted(sessionStartedRequest, session) {
       console.log(`onSessionStarted requestId=${sessionStartedRequest.requestId}, sessionId=${session.sessionId}`);}/**
    * Called when the user launches the skill without specifying what they want.
    */function onLaunch(launchRequest, session, callback) {
       console.log(`onLaunch requestId=${launchRequest.requestId}, sessionId=${session.sessionId}`);
       getWelcomeResponse(callback);}/**
    * Called when the user ends the session.
    * Is not called when the skill returns shouldEndSession=true.
    */function onSessionEnded(sessionEndedRequest, session) {
       console.log(`onSessionEnded requestId=${sessionEndedRequest.requestId}, sessionId=${session.sessionId}`);}function getWelcomeResponse(callback) {
       // If we wanted to initialize the session to have some attributes we could add those here.
       const sessionAttributes = {};
       const msg = 'Du kannst die Fernseher Lautstärke verändern.';
       callback(sessionAttributes, buildSpeechletResponse(msg, false));}function handleSessionEndRequest(callback) {
       callback({}, buildSpeechletResponse('Fernseher Steuerung beendet.', true));}/**
    * Called when the user specifies an intent for this skill.
    */function onIntent(intentRequest, session, callback) {
       console.log(`onIntent requestId=${intentRequest.requestId}, sessionId=${session.sessionId}`);
       const intent = intentRequest.intent;
       const intentName = intentRequest.intent.name;
       // Dispatch to your skill's intent handlers
       if (intentName === 'Mute') {
           setTVCommand(callback, ITEM_MUTE, 'ON');
       } else if (intentName === 'Ton') {
           setTVCommand(callback, ITEM_MUTE, 'OFF');
       } else if (intentName === 'Aus') {
           setTVCommand(callback, ITEM_POWER, 'OFF');
       } else if (intentName === 'An') {
           setTVCommand(callback, ITEM_POWER, 'ON');
       } else if (intentName === 'Volume') {
           const VolumeSlot = intent.slots.value;
           if (VolumeSlot && VolumeSlot.value === parseInt(VolumeSlot.value, 10).toString()) {
               setTVCommand(callback, ITEM_VOLUME, VolumeSlot.value.toString());
           } else {
               var msg = "Ich konnte die Lautstärke '" + VolumeSlot.value + "' nicht verarbeiten.";
               callback({}, buildSpeechletResponse(msg, true));
           }
       } else if (intentName === 'AMAZON.HelpIntent') {
           getWelcomeResponse(callback);
       } else if (intentName === 'AMAZON.StopIntent' || intentName === 'AMAZON.CancelIntent') {
           handleSessionEndRequest(callback);
       } else {
           throw new Error('Invalid intent');
       }}// --------------- Main handler -----------------------// Route the incoming request based on type (LaunchRequest, IntentRequest,// etc.) The JSON body of the request is provided in the event parameter.
    exports.handler = (event, context, callback) => {
       try {
           console.log(`event.session.application.applicationId=${event.session.application.applicationId}`);
           /**
            * Uncomment this if statement and populate with your skill's application ID to
            * prevent someone else from configuring a skill that sends requests to this function.
            */
           // if (event.session.application.applicationId !== 'amzn1.ask.skill.816d3b56-abcd-1234-98b2-1e544500a25a') {
           //    callback('Invalid Application ID');
           // }
           if (event.session.new) {
               onSessionStarted({ requestId: event.request.requestId }, event.session);
           }
           if (event.request.type === 'LaunchRequest') {
               onLaunch(event.request,
                   event.session,
                   (sessionAttributes, speechletResponse) => {
                       callback(null, buildResponse(sessionAttributes, speechletResponse));
                   });
           } else if (event.request.type === 'IntentRequest') {
               onIntent(event.request,
                   event.session,
                   (sessionAttributes, speechletResponse) => {
                       callback(null, buildResponse(sessionAttributes, speechletResponse));
                   });
           } else if (event.request.type === 'SessionEndedRequest') {
               onSessionEnded(event.request, event.session);
               callback();
           }
       } catch (err) {
           callback(err);
       }};

  6. Actions - Configure test event - fuge dieses Snippet ein - Save and Test - unten eine Datenstruktur mit _"text": "OK"_ angezeigt werden: 
    
        {
     "session": {
       "sessionId": "SessionId.a7c6ea36-5d4d-40c7-936c-dba524758bbd",
       "application": {
         "applicationId": "amzn1.ask.skill.3ddb9fb0-eeee-4986-ffff-03dd0093edfb"
       },
       "attributes": {},
       "user": {
         "userId": "amzn1.ask.account.ABCXYZ"
       },
       "new": true
     },
     "request": {
       "type": "IntentRequest",
       "requestId": "EdwRequestId.b9e1ad2a-aaaa-49f3-cccc-0cbf58c7684a",
       "locale": "de-DE",
       "timestamp": "2017-03-22T11:46:51Z",
       "intent": {
         "name": "Volume",
         "slots": {
           "value": {
             "name": "value",
             "value": "20"
           }
         }
       }
     },
     "version": "1.0"}

Der openHAB-spezifische Code ist in der Funktion _setTVCommand_ enthalten und besteht aus einem https-Request auf der REST-API von myopenhab.org, um die Zustande einiger Items in openHAB zu setzen. Fur eine Fernsehsteuerung uber einen anderen Dienst muss dieser Code naturlich abgeandert werden. Damit haben wir unseren Glue-Code zwischen einem Alexa-Custom-Skill und myopenhab fertig.

Als nachstes definieren wir den eigentlichen Custom-Skill:

  1. Bei [developer.amazon.com](https://developer.amazon.com) (kostenlos) anmelden (mit dem gleichen Amazon Account wie Alexa!).
  2. Gehe zu '_Alexa_' \- '_Alexa Skills Kit_' \- '_Get Started >_' \- '_Add a New Skill_'.
  3. Setze Skill Typ '_Custom Interaction Model_', Sprache '_German_', Name & Invocation Name '_Fernseher_'.
  4. Fuge dieses Intent Schema ein: 
    
        {
     "intents": [
       { "intent": "Mute", "slots": [] },
       { "intent": "Ton", "slots": [] },
       { "intent": "An", "slots": [] },
       { "intent": "Aus", "slots": [] },
       { "intent": "Lauter", "slots": [] },
       { "intent": "Leiser", "slots": [] },
       { "intent": "Pause", "slots": [] },
       { "intent": "Play", "slots": [] },
       { "intent": "Volume", "slots": [ { "name": "value", "type": "AMAZON.NUMBER" } ] }
     ]}

  5. Und fuge diese Sample Utterances ein: 
    
        Mute lautlos
    Mute still
    Mute Ton aus
    Mute Ton aus schalten
    Mute Ton aus stellen
    Ton Ton an
    Ton Ton an schalten
    Ton Ton an stellen
    Ton Ton einschalten
    Ton Ton einstellen
    An an
    An an schalten
    An an stellen
    An einschalten
    An einstellen
    Aus aus
    Aus aus schalten
    Aus aus stellen
    Volume Lautstärke {value}

  6. Als Endpoint '_AWS Lambda_' und '_Europe_' auswahlen, und die bei der oben erstellten Lambda Function rechts oben angezeigte ID eintragen (beginnt mit '_arn:aws:lambda:eu-west-1:_').
  7. Dann im Tab '_Test_' im Service Simulator als '_Utterance_' probehalber eingeben: '_Ton aus_' \- dann sollte unten eine Datenstruktur mit _"text": "OK"_ angezeigt werden.

In der Alexa-App sollte automatisch unser neuer _Fernseher_-Skill gelistet sein (da wir außer dem Namen noch keine weiteren Informationen zum Skill angegeben haben, fehlen Icon und Beschreibung; _'devDE'_ bedeutet, dass der Skill nicht offentlich ist):

![alexa-smart-home-skills.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Embedded/alexa-smart-home-skills.png?t=1494425153587&width=182&height=210&name=alexa-smart-home-skills.png)

Nach diesen Muhen konnen wir nun endlich faul auf der Couch liegen:

  * Alexa, schalte ZDF an.

## Ganz schon umstandlich?

Ja und nein. Durch Alexas Einschrankungen bei Smarthome-Skills und durch die vorgegebene Grammatik fur Custom-Skills ist es schwierig, einen Mix aus vernunftigen Phrasen fur einen Anwendungsfall zu finden. Da wurde ich mir ab und zu mehr Freiheiten wunschen, z.B. eine freiere Definition von Phrasen ohne Skill Keyword - was aktuell nur bei Built-in-Funktionen und Smarthome-Skills moglich ist.

Dadurch ergeben sich fur Custom-Skills (das sind ja die meisten aus dem [Skill-Store](https://www.amazon.de/b?ie=UTF8&node=10068460031)) unnotig kompliziert erscheinende, technisch aber nachvollziehbare Phrasen.  
Diese Phrasen-Komplexitat zusammen mit der noch [jungen ungeubten deutschen Spracherkennung](https://blogs.itemis.com/de/alexa-wer-ist-der-boss) ergibt ein aktuell ernuchterndes Erlebnis, sofern man nur durch die vorhandenen Skills stobert.

Sobald man sich aber die Muhe macht, fur sich selbst sinnvolle und angepasste Funktionen zu erganzen, gewinnt Alexa stark an Komfort :-) Bisher gab es keine wirklichen Alternativen zu Alexa, wenn es darum geht eigene Gerate mit der Sprache zu steuern. Apples Siri kann um [einige spezielle Features](https://developer.apple.com/library/content/documentation/Intents/Conceptual/SiriIntegrationGuide/index.html) erweitert werden, aber Gerate lassen sich damit nicht schalten.

Samsungs neues [Bixby](http://www.samsung.com/global/galaxy/apps/bixby/) scheint vorerst ein geschlossenes System zu werden. Lediglich der vor kurzem erschienene [Google Assistant](https://assistant.google.com/) via [Google Home](https://madeby.google.com/home/) scheint mittels [Actions](https://developers.google.com/actions/) ebenfalls frei erweiterbar zu werden - zumindest sieht dessen [Entwickler-Doku](https://developers.google.com/actions/develop/conversation) sehr vielversprechend aus.

Nun gilt es noch herauszufinden, ob und wie eigene Anwendungsfalle wie das Steuern des eigenen Fernsehers damit realisiert werden konnen.

## Fazit

Hat man die Funktionsweise von Alexa erst einmal verstanden, dann lassen sich damit schon ganz beachtliche Dinge realisieren - und das bequeme Steuern des TVs kann sogar den [WAF](https://de.wikipedia.org/wiki/Woman_acceptance_factor) von Alexa erhohen ;-) Die Kombination aus Smarthome- und Custom-Skill erfordert zwar die Installation (bzw. ggf. auch die Implementierung) zweier Skills fur eine Funktionalitat, aber dafur bekommt man komfortabel kurze Phrasen, soweit es technisch moglich ist. Und wenn man das einmal geschafft hat, ist die Lernkurve beschritten und man bekommt schnell eine Vorstellung davon und auch Ideen daruber, was noch alles moglich ist.

Dieser Blog-Beitrag ist nach den [ersten Erfahrungen mit Alexa](https://blogs.itemis.com/de/alexa-wer-ist-der-boss) der zweite einer Serie, die von unseren Experimenten mit Alexa berichtet. Weitere, auch (software-)technische Beitrage werden folgen - zum Beispiel das Experiment, bestimmte Personen in einem Gebaude zu lokalisieren.
