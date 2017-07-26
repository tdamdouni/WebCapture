# ScrollMagic: Ein Animationsframework, das hält was der Name verspricht

_Captured: 2015-12-13 at 17:57 from [t3n.de](http://t3n.de/news/scrollmagic-animationsframework-534920/)_

Jan Paepke hat den Urvater der Scroll- und Animation-Frameworks, namlich Superscrollorama, von Grund auf neu entwickelt und geschrieben.

Am besten konnt ihr euch ScrollMagic als ein Skript vorstellen, das den Scrollbalken als eine Art „Fortschrittsbalken" sieht. Wird ein gewisser Punkt erreicht: Zack - und es wird eine Funktion gezundet. Das hort sich jetzt noch alles sehr abstrakt und wenig spektakular an: wartet aber bis ihr die Demos gesehen habt.

Wie auch Superscrollorama basiert ScrollMagic auf der „Greensock Animation Plattform" (GSAP), wurde aber um folgende Funktionen erweitert:

  * Erhohte Performance
  * Unterstutzung mobiler Gerate
  * Full-responsive-Unterstutzung
  * Objektorientierte Programmierung
  * Unterstutzung von horizontalem und vertikalem scrollen
  * Scroll-Moglichkeit innerhalb von (multiplen) Divisions
  * Debugging-Extension

Mit ScrollMagic konnt ihr ganz einfach Parallax-Effekte erzeugen, Scrollbar-abhangige Events abfeuern, „Infinite-Scrolling" mit Ajax-Anfragen umsetzen und Animationen mit der Scrollgeschwindigkeit synchronisieren, kurzum: ScrollMagic halt was der Name verspricht.

## ScrollMagic: So konnt ihr es nutzen

Bevor ihr ScrollMagic nutzen konnt, musst ihr vorher die Abhangikeiten beachten. Das jQuery-Plugin benotigt jQuery sowie GSAP. [Tutorials zur Installation und Demos zu GSAP konnt ihr auf der offiziellen Seite finden ](http://www.greensock.com/gsap-js/). Wie bereits angesprochen verfugt ScrollMagic uber eigene Debugging-Tools die ihr wie folgt einbinden konnt.
    
    
    <script type="text/javascript" src="js/jquery.scrollmagic.debug.js"></script>

Der folgende Code zeigt euch, wie ihr das Skript initialisieren konnt und wie ihr mit mehreren Szenen umgeht:
    
          1. // init controller
      2. var controller =newScrollMagic();
      3. // assign handler "scene" and add it to Controller
      4. var scene =newScrollScene({duration:100})
      5. .addTo(controller);
      6. // add multiple scenes at once
      7. controller.addScene([
      8.     scene,// add above defined scene
      9.     scene2 =newScrollScene({duration:200}),// add scene and assign handler "scene2"
      10. newScrollScene({offset:20})// add anonymous scene
    
          1. var controller;
      2.     $(document).ready(function($){
      3. // init controller
      4.         controller =newScrollMagic();
      5. <div class="spacer s2"></div>
      6. <div id="trigger1"class="spacer s0"></div>
      7. <div id="animate1"class="box2 skin">
      8. <p>You wouldn't like me, when I'm angry!</p>
      9. <a href="#"class="viewsource">view source</a>
      10. </div>
      11. <div class="spacer s2"></div>
      12.     $(document).ready(function($){
      13. // build tween
      14. var tween =TweenMax.to("#animate1",0.5,{backgroundColor:"green", scale:2.5});
      15. // build scene
      16. var scene =newScrollScene({triggerElement:"#trigger1"})
      17. .setTween(tween)
      18. .addTo(controller);
      19. // show indicators (requires debug extension)
      20.         scene.addIndicators();
      21. </script>

ScrollMagic verfugt uber eine [umfassende Demo-Sammlung ](http://janpaepke.github.io/ScrollMagic/examples/index.html), in der auf beinahe jedes Szenario eingegangen wird. In der ausgezeichneten Dokumentation konnt ihr euch einen guten Überblick uber alle Methoden und Klassen machen - auf jedenfall einen Blick wert.

## Fazit: Gefallt mir!

ScrollMagic ist wirklich gut, ganz besonders gefallt mir aber wie ausfuhrlich und ubersichtlich das jQuery-Plugin dokumentiert ist. Ihr findet [das Plugin auf GitHub ](https://github.com/janpaepke/ScrollMagic). Und wer einfach nur einmal sehen mochte, was mit ScrollMagic alles moglich ist, dem kann ich die [Website selbst empfehlen ](http://janpaepke.github.io/ScrollMagic/).

Mit dem DEVELOPER Tarif vom TYPO3 Spezialisten jweiland.net kannst du Web-Projekte 3 Monate in einer realen Hosting Umgebung entwickeln und testen - ohne jede Verpflichtung. Auf Wunsch kann der Tarif anschließend in ein regulares Hosting Paket umgewandelt werden.

[Fordere jetzt dein kostenloses Entwickler-Hosting an!](http://guruads.de/api/click/56542c13497959332200003f)
