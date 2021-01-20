https://www.kompf.de/tech/rftemp.html  
https://github.com/BlackBrix/TempHygroTX868  
(Original: https://github.com/skaringa/TempHygroTX868 )  
  
Sender ist: "HF-Sendemodul TX868-75, 868 MHz"  
https://de.elv.com/hf-sendemodul-tx868-75-868-mhz-062011  
  
## geplante Verbesserungen (in diesem Fork): 
----
### genauerer oder sparsamerer Sensor:  
sparsamer(?): ------------------------------------  
Sensirion SHT40  
https://www.soselectronic.de/articles/sensirion/feuchtigkeits-und-temperatursensor-sht40-2527?utm_source=sosnews2017&utm_medium=email&utm_term=webtr&utm_content=SC&utm_campaign=Sensirion_SHT40&btn=more  
https://www.sensirion.com/de/umweltsensoren/feuchtesensoren/humidity-sensor-sht4x/  
genauer: ------------------------------------  
Sensirion SHT35-DIS (-B oder -F)  
https://www.sensirion.com/de/umweltsensoren/feuchtesensoren/digitale-feuchtesensoren-fuer-diverse-anwendungen/  
https://www.tindie.com/products/closedcube/sht35-d-digital-humidity-temperature-sensor/  
library: https://github.com/closedcube/ClosedCube_SHT31D_Arduino  
oder SHT85 ?  
https://www.sensirion.com/de/umweltsensoren/feuchtesensoren/sht85-steckbarer-feuchtesensor-fuer-einfachen-austausch/  
  
  
### kein Schaltregler step-up oder LDO   
(bringt immer große Verluste, gerade bei kleinen Strömen verschlechtert sich der Wirkungsgrad enorm beim Shaltregler)  
statt dessen Atmega328 mit 4MHz oder 1MHz betreiben und dann mit 3,0V..1,8V direkt aus 2x AA Lithium betreiben (ohne Bootloader , sondern ISP-Programmierung)  
vergl.: http://www.gammon.com.au/power  
  
### ggf. Sender und Sensor beim MCU-Schlaf mit abschalten (über Ausgänge der MCU),  
wenn sich das lohnt -> Sender und Sensor haben schon recht kleine (Ruhe-) Stromaufnahme  
Sensor: 0,2 - 0,4µA  
Sender: Zitat aus Datenblatt: "Standby Stromaufnahme <10nA"  
 
----
## original readme.md :
----
   
# TempHygroTX868

Arduino library to control the ELV TX868 rf transmitter module to send temperature and humidity values over the air at 868.35 MHz.

The communication protocol is compatible to ELV sensors like the S 300 and ASH 2200, therefore the data may be received by weather stations like USB-WDE 1, WS 200/300, and IPWE 1 manufactured by [ELV](http://www.elv.de).

## Usage

    #include <TempHygroTX868.h>

    TempHygroTX868 tx;

    void setup()
    {
      tx.setup(5); // TX868 is at data pin 5
    }

    void loop()
    {
      byte address = 3;
      float humidity = 50;
      float temperature = 21.4;

      tx.setAddress(address);
      tx.send(temperature, humidity);

      delay((unsigned long)tx.getPause() * 1000UL);
    }

For all options, see [TempHygroTX868.h][header]. The [examples][example] directory contains several examples including full production code to build a weather sensor/transmitter similar to the S300:

![Wireless temperature and humidity sensor](https://www.kompf.de/tech/images/rftemp_comp_annot.png)

## Extension for old sensor protocol

The library has been extended to implement the old ELV sensor transmission protocol V1.1 as well. This should support Thermo/Hygro sensors like the AS2000 and ASH2000 which are using the 433 MHz transmitter HFS-300.

To enable the old protocol, pass the protocol version to the setup() method:

    void setup()
    {
      // TX868 is at data pin 5
      // Use the old protocol V1.1
      tx.setup(5, TempHygroTX868::PROT_V11);
    }

## Installation

* Download TempHygroTX868.zip from [releases page][release].
* Follow the steps described at [Installing Additional Arduino Libraries](https://www.arduino.cc/en/guide/libraries).

## References

* [Protokollversion V1.2][prot_12]
* [Protokollversion V1.1][prot_11]

## License

Copyright 2015, 2020 Martin Kompf

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
 
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

[header]: https://github.com/skaringa/TempHygroTX868/blob/master/TempHygroTX868.h "Header file"
[example]: https://github.com/skaringa/TempHygroTX868/blob/master/examples "Examples"
[release]: https://github.com/skaringa/TempHygroTX868/releases/latest
[prot_11]: http://www.dc3yc.homepage.t-online.de/protocol_alt.htm
[prot_12]: http://www.dc3yc.homepage.t-online.de/protocol.htm

