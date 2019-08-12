# Raspberry Pi 3 Model B+ Temperatur/Watt Benchmark

_Captured: 2019-04-20 at 22:34 from [buyzero.de](https://buyzero.de/blogs/news/raspberry-pi-3-model-b-temperatur-watt-benchmark)_

![Raspberry Pi 3 Model B+ Temperatur/Watt Benchmark](https://cdn.shopify.com/s/files/1/1560/1473/articles/raspberry_pi3b__with_heatsinks_e3aae54b-b066-446d-be74-39a647ad1628_2048x.jpg?v=1529948205)

> _English version below_

_**Raspberry Pi 3 Model B+ Temperatur/Watt Benchmark**_

Dieser Benchmark dient dazu um zu zeigen ob irgend eine Kuhlvorrichtung fur den Pi benotigt wird.

Allerdings, nachdem es eine shier endlose Anzahl an Applikationen fur den Mikrocomputer gibt ist es sehr schwierig eine Liste fur alle verschiedenen Anwendungsgebiete zusammen zu stellen.

Daher zeigen wir die Werte fur die Auslastung von 4, 3 und 2 Kernen welches einer Auslastung von 100, 75 and 50% entspricht.

Indem man die Werte betrachtet und mit seiner eigenen Auslastung vergleicht, kann man entscheiden ob der Pi eine Kuhlung benotigt. In manchen Fallen, bei dem die CPU Auslastung unklar, schwankend oder gar lanzeitig ist, macht es Sinn auf der sicheren Seite zu sein.

Kriterien:

\- Die Raumtemperatur schwankte da das Fenster zum Benchmark Zimmer offen war (Sonnenschein / Gewitter = Temperatur Schwankungen). Daher sind die Angaben ohne Gewahr.

\- Demzufolge ist dieser Benchmark dazu gedacht dem End User bzw. normalen "hacker" eine Idee zu verschaffen wie effektiv die verschiedenen Optionen der Kuhlung sind.

\- Diese Werte sind nicht fur die Industrie bestimmt da die Messwerte nicht in einer industriellen Umgebung gemessen worden sind.

\- Die einzige Komponente die sich warend der Messungen verandert hat war der Pi selbst.

\- Die Temperaturangaben wurden der Pi internen Kommandozeilen Funktion entnommen.

(vcgencmd measure_temp)

\- Fur den Benchmark wurde das Tool ,,Sysbench" verwendet.

(sysbench -test=cpu -num-threads=n -cpu-max-prime 20000)

\- Die Watt Messungen wurden mit dem Gerat Intertek EM321-A vorgenommen.

\- Die angehangte Peripherie bestanden aus einer Gaming Tastatur und Maus, welche vermutlich die Watt Messungen, auf Grund der LEDs, angeboben haben.

\- Andere Komponenten bestanden aus einem 2A Netzteil, einem Philips 22" 36 Watt Monitor und einer 16 GB SanDisk microSD Klasse 10 karte.

\- Alle Messungen wurden innerhalb von 1,5 Minuten getatigt.

\- Nach einem Benchmark wurde eine Kuhlphase von 10-15 Minuten eingehalten.

\- 3 Messungen wurden pro Konfiguration notiert.

\- Der Durschnitt dieser Messungen wird dargestellt.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/fig1_large.JPG?v=1529947919)

> _Fig 1. Zeigt die Watt aufname und die Hitzegenerierung in C° eines Raspberry Pi 3 Model B+; 4 Kerne bei 100% Auslastung._

wo= ohne Kuhlkorper (standard Ausgabe). w= mit Kuhlkorper wie von pi3g hergestellt. active= Aktive Kuhlung wie von pi3g zusammengestellt (Mitgelieferte Warmeleitende Klebefolie).

![](https://cdn.shopify.com/s/files/1/1560/1473/files/fig2_large.JPG?v=1529947935)

> _Fig 2. Zeigt die Watt aufname und die Hitze Generierung in C° eines Raspberry Pi 3 Model B+; 3 Kerne bei 75% Auslastung._

wo= ohne Kuhlkorper (standard Ausgabe). w= mit Kuhlkorper wie von pi3g hergestellt. active= Aktive Kuhlung wie von pi3g zusammengestellt (Mitgelieferte Warmeleitende Klebefolie).

![](https://cdn.shopify.com/s/files/1/1560/1473/files/fig3_large.JPG?v=1529947949)

> _Fig 3. Zeigt die Watt aufname und die Hitze Generierung in C° eines Raspberry Pi 3 Model B+; 2 Kerne bei 50% Auslastung._

wo= ohne Kuhlkorper (standard Ausgabe). w= mit Kuhlkorper wie von pi3g hergestellt. active= Aktive Kuhlung wie von pi3g zusammengestellt (Mitgelieferte Warmeleitende Klebefolie).

Desweiteren hat mich interessiert, inwiefern sich der mitgelieferten, warmeleitenden Klebestreifen

sich mit unserem 2 Komponenten warmeleitenden Kleber vergleicht. Angenommen wurde eigentlich, dass diese mehr oder minder den gleichen warmeleitenden Effekt haben sollten.

Das Ergebnis war dann doch sehr verbluffend.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/fig4small_large.JPG?v=1529948494)

> _Fig 4. Zeigt den Temperaturanstieg in C° mit einem aktiven Kuhler auf dem Raspberry Pi 3 Model B+._

Es werden alle 4 Kerne verwendet. Foil= Warmeleitende Folie. 2 ccp= 2 Komponenten warme leitender Kleber.

\-------------------------------------------------------------------------------------------------------------------

_**Raspberry Pi 3 Model B+ Temperature/Wattage Benchmark**_

This Benchmark is intended to show you whether you need some form of cooling device for

your Pi. As there are a shear endless amounts of applications for a microcomputer, it is pretty

difficult to establish a list for all of its applications. Therefore, we created a list of values showing

the usage of 4, 3 and 2 cores which illustrates the total CPU usage of 100, 75 and 50%, respectively.

Using these values you can observe the CPU usage on your Pi and decide whether you need any type of cooling. In some cases, where the CPU usage is unclear, erratic or prolonged it might make sense to better be safe than sorry.

Criteria:

\- The room temperature varied as the window of the benchmark room was open and the weather changed (Sunny / Thunderstorm = Temperature fluctuation). Therefore, we cannot guarantee that these measurements can be replicated.

\- Therefore, this benchmark is supposed to give the end user / ordinary "hacker" an idea of the effectiveness of various cooling devices.

\- These readings were not intended for industrial purposes because they were not conducted in an industrial environment.

\- The only component that changed was the Raspberry Pi 3 Model B+ itself.

\- Measurements were taken by the Raspberry Pi´s temperature displaying command line itself (vcgencmd measure_temp)

\- For the Benchmark the tool ,,Sysbench" was used.

(sysbench -test=cpu -num-threads=n -cpu-max-prime 20000)

-Wattage was measured using the meter Intertek EM321-A

\- Attached peripheries were a gaming mouse and gaming keyboard, probably increasing the wattage measurement, due to the attached LEDs.

\- Other components consisted out of a 2A power supply, a Phillips 22" 36W monitor and a 16GB SanDisk microSD card class 10.

\- A measurement was taken all 1.5 minutes.

\- After a benchmark, a cool down time of 10-15 minutes was implemented.

\- 3 measurements were taken in total per configuration.

\- The averages of these 3 measurements are being displayed.

Fig 1. Showing the watt consumption and heat generation in C° of a Raspberry Pi 3 Model B+; 4 cores at 100% usage.

wo= without heatsink (standard issue). w= with heatsink as manufactured by pi3g. active= active cooling as assembled by pi3g (Attached cooling foil).

Fig 2. Showing the watt consumption and heat generation in C° of a Raspberry Pi 3 Model B+; 3 cores at 75% usage.

wo= without heatsink (standard issue). w= with heatsink as manufactured by pi3g. active= active cooling as assembled by pi3g (Attached cooling foil).

Fig 3. Showing the watt consumption and heat generation in C° of a Raspberry Pi 3 Model B+; 2 cores at 50% usage.

wo= without heatsink (standard issue). w= with heatsink as manufactured by pi3g. active= active cooling as assembled by pi3g (Attached cooling foil).

Furthermore, I was interested in how the included and attached cooling foil would compare to the 2 component cooling glue, which we use, would compare with each other. It was assumed that both of them should have more or less the same effect. But the result was quite astonishing.

Fig 4. Illustrated the increase in temperature in C° with an active cooling device mounted on the Raspberry Pi 3B+. All 4 cores were used. Foil= cooling foil. 2 ccp = 2 component cooling paste.

## Hinterlassen Sie einen Kommentar

Bitte beachten Sie, dass Kommentare vor der Veroffentlichung freigegeben werden mussen
