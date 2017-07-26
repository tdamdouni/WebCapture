# Bluetooth-Konfiguration mit bluetoothctl

_Captured: 2017-05-06 at 10:15 from [pi-buch.info](https://pi-buch.info/bluetooth-konfiguration-mit-bluetoothctl/)_

Soeben habe ich versucht, diverse Bluetooth-Gerate mit dem Bluetooth-Konfigurationswerkzeugen von Raspbian Jessie zu konfigurieren. Also Installation der Werkzeuge mit `apt-get install bluetooth blueman` und sicherheitshalber ein Neustart. Danach erscheint im Panel des Raspbian-Desktops das Bluetooth-Icon, dessen Menueintrage in den aus fruheren Raspbian-Versionen bekannten Bluetooth-Manager fuhren.

Nicht geandert hat sich leider die miserable Qualitat dieses Tools: Von meinen Testkandidaten (eine Maus, zwei Tastaturen, eine Lautsprecherbox) gelang nur bei der Maus und bei der Lautsprecherbox das Pairing. In allen anderen Fallen war es nicht moglich, die Gerate mit dem Raspberry Pi zu verbinden. Trostlos!

Wohl oder ubel habe ich nun versucht, die Konfiguration auf Kommandoebene durchzufuhren. Das von Raspbian Wheezy bekannte Werkzeug `bluez-simple-agent` steht unter Jessie nicht mehr zur Verfugung. Eine gute Alternative ist das Kommando `bluetoothctl`.

### bluetoothctl-Kommando

Nach dem Start von `bluetoothctl` gelangen Sie in einen Kommandomodus. Die weitere Vorgehensweise zur Verbindung eines Bluetooth-Gerats sieht so aus:

  * Sie aktivieren mit `pairable on` den Kuppelungsmodus.
  * Sie aktivieren mit `scan on` den Scan-Modus. Das Programm listet nun alle erkannten Gerate in Funkreichweite auf. Dieser Vorgang kann geraume Zeit dauern, einzelne Gerate werden dabei immer wieder aufgelistet. Wenn Sie das gewunschte Gerat gefunden haben, schalten Sie den Modus mit `scan off` einfach wieder aus. 
  * Sie aktivieren mit `agent on` einen sogenannten Bluetooth-Agenten. Er kummert sich um die Autorisierung neuer Gerate (bei Tastaturen: Passworteingabe).
  * Mit `pair xx:xx:xx` initiieren Sie den Verbindungsaufbau zu einem Gerat. Bei einer Tastatur werden Sie nun dazu aufgefordert, einen sechstelligen Code einzutippen. Vergessen Sie nicht, die Eingabe mit _Return_ abzuschließen! Die erfolgreiche Kuppelung erkennen Sie an der Meldung _pairing successful_.
  * Und mit `trust xx:xx:xx` machen Sie dem Bluetooth-System klar, dass Sie dem Gerat wirklich vertrauen.
  * Mit `connect xx:xx:xx` geben Sie an, dass Sie das Gerat tatsachlich nutzen mochten. (Das hatte sich `bluetoothctl` mittlerweile eigentlich denken konnen …) Wenn alles klappt, lautet die Reaktion _connection successful_. Das Gerat kann jetzt verwendet werden! 
  * `info xx:xx:xx` zeigt den Verbindungsstatus und diverse weitere Informationen zum Gerat an.
  * Mit `exit` beenden Sie das `bluetoothctl`-Kommando.

Wichtig ist, dass Sie bei neu zu konfigurierenden Bluetooth-Geraten immer wieder auf den Bluetooth-Knopf (Pairing-Knopf) drucken, damit das Gerat so der Umwelt signalisiert, dass es bereits zum Verbindungsaufbau ist. Die meisten Gerate signalisieren diesen Zustand auch durch eine blinkende Leuchtdiode.

### bluetoothctl-Beispiel

Die folgenden Zeilen zeigen (leicht gekurzt) die Ein- und Ausgaben, die in einem Terminal-Fenster erfolgen.
    
    
    pi@pi2$ bluetoothctl 
    [NEW] Controller 00:1A:7D:DA:71:13 pi2 [default]
    [NEW] Device 88:E7:A6:04:9E:A7 Bluetooth Laser Mouse
    [NEW] Device 00:25:BC:FB:C1:E5 Michael Koflers Tastatur
    
    [bluetooth]# agent on
    Agent registered
    
    [bluetooth]# pairable on
    Changing pairable on succeeded
    
    [bluetooth]# scan on
    Discovery started
    [CHG] Controller 00:1A:7D:DA:71:13 Discovering: yes
    [NEW] Device 70:10:00:1A:92:20 70-10-00-1A-92-20
    [NEW] Device 73:0C:0F:CF:F3:BE 73-0C-0F-CF-F3-BE
    [CHG] Device 70:10:00:1A:92:20 LegacyPairing: no
    [CHG] Device 70:10:00:1A:92:20 Name: Bluetooth 3.0 Keyboard
    [CHG] Device 70:10:00:1A:92:20 Alias: Bluetooth 3.0 Keyboard
    [CHG] Device 70:10:00:1A:92:20 LegacyPairing: yes
    ...
    
    bluetooth]# scan off
    Discovery stopped
    
    [bluetooth]# pair 70:10:00:1A:92:20
    Attempting to pair with 70:10:00:1A:92:20
    [CHG] Device 70:10:00:1A:92:20 Connected: yes
    [agent] PIN code: 963064
    
      --> Pin-Eingabe + Return auf der Tastatur <--
    
    [CHG] Device 70:10:00:1A:92:20 Paired: yes
    Pairing successful
    
    [bluetooth]# trust 70:10:00:1A:92:20
    Changing 70:10:00:1A:92:20 trust succeeded
    [CHG] Device 88:E7:A6:04:9E:A7 Connected: yes
    
    [bluetooth]# connect 70:10:00:1A:92:20
    Attempting to connect to 70:10:00:1A:92:20
    Connection successful
    
    [bluetooth]# info 70:10:00:1A:92:20
    Device 70:10:00:1A:92:20
        Name: Bluetooth 3.0 Keyboard
        Alias: Bluetooth 3.0 Keyboard
        Class: 0x000540
        Icon: input-keyboard
        Paired: yes
        Trusted: yes
        Blocked: no
        Connected: yes
        LegacyPairing: no
        UUID: Service Discovery Serve.. (00001000-...)
        UUID: Human Interface Device... (00001124-...)
        UUID: PnP Information           (00001200-...)
        Modalias: usb:v04E8p7021d0001
    
    [bluetooth]# exit
    

### Test, Interna

Wenn soweit alles klappt, sollten Sie nun einen Neustart durchfuhren. Auf diese Weise stellen Sie sicher, dass die Konfiguration tatsachlich gespeichert wurde und nachhaltig funktioniert.

Die Bluetooth-Konfiguration fur ein bestimmtes Gerat wird in `/var/lib/bluetooth/id1/id2/info` gespeichert. Dabei ist `id1` der ID-Code des Bluetooth-Controllers (beim Raspberry Pi also eines USB-Bluetooth-Steckers) und `id2` der ID-Code des Bluetooth-Gerats.
    
    
    sudo less /var/lib/bluetooth/controller-id/device-id/info
    [LinkKey]
    Key=44763CF7C981D575C28BC05C90184F00
    Type=0
    PINLength=0
    
    [General]
    Name=Bluetooth 3.0 Keyboard
    Class=0x000540
    SupportedTechnologies=BR/EDR;
    Trusted=true
    Blocked=false
    Services=00001000-0000-1000-8000-00805f9b34fb;00001124-0000-1000-8000-00805f9b34fb;00001200-0000-1000-8000-00805f9b34fb;
    
    [DeviceID]
    Source=2
    Vendor=1256
    Product=28705
    Version=1
    

### Quellen
