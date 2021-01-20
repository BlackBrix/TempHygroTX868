Das folgende Datenübertragungsformat habe ich bei meinen Versuchen herausgefunden. 
Es gibt ein älteres, das <a href="https://github.com/BlackBrix/TempHygroTX868/tree/master/Protokoll_V1_1">hier</a> beschrieben ist. Bei diesem werden die Telegramme dreimal
hintereinander im Abstand von 0.1s ausgesendet.
Die Beschreibung des neueren Protokolls folgt im Anschluss.<br><br>
Ich konnte keine Probleme mit den Displays erkennen, wenn es genau eingehalten wird.<br><br>

(c) 2002, 2003, 2004, 2006 Helmut Bayerlein.<br><br><br>

<strong>Protokollversion V1.2<br></strong>
Codierung eines Bits: <ul>
	<li>die Länge eines Bits beträgt 1220.7µs, entsprechend 819.2 Hz
	<li>sie wird abgeleitet von 32768 Hz : 40
	<li>das Puls-Pausenverhältnis beträgt 7:3 bzw. 3:7
	<li>eine logische 0 wird durch einen HF-Träger von 854.5µs und 366.2µs Pause dargestellt
	<li>eine logische 1 wird durch einen HF-Träger von 366.2µs und 854.5µs Pause dargestellt
</ul>
Die Präambel besteht aus 7 bis 10 * 0 und 1 * 1.<br>
Die Daten werden immer als 4bit-Nibble übertragen. Danach folgt eine 1.<br>
Das LSBit wird zuerst übertragen.<br><br>
Die Quersummen am Schluss berechnen sich folgendermaßen:<ol>
	<li>Check:	alle Nibbles beginnend mit dem Typ bis Check werden XOR-verknüpft, 
    Ergebnis ist 0<li>Summe:	alle Nibbles beginnend mit dem Typ bis Check 
    werden aufsummiert, dazu 5 addiert und die oberen 4 Bit verworfen	
</ol>
Der Typ besteht aus 3 Bit, die wie folgt codiert sind. Die Links zeigen die einzelnen Protokolle:
<br>
&nbsp;<table border="0" cellpadding="0" cellspacing="0" style="border-collapse: collapse" bordercolor="#111111" width="78%">
  <tr>
    <td width="8%" align="center">0</td>
    <td width="92%"><a href="thermo.md">Thermo</a> (AS3)</td>
  </tr>
  <tr>
    <td width="8%" align="center">1</td>
    <td width="92%"><a href="thermohygro.md">Thermo/Hygro</a> (AS2000, ASH2000, 
    S2000, S2001A, S2001IA, ASH2200, S300IA)</td>
  </tr>
  <tr>
    <td width="8%" align="center">2</td>
    <td width="92%"><a href="regen.md">Regen</a> (S2000R)</td>
  </tr>
  <tr>
    <td width="8%" align="center">3</td>
    <td width="92%"><a href="wind.md">Wind</a> (S2000W)</td>
  </tr>
  <tr>
    <td width="8%" align="center">4</td>
    <td width="92%"><a href="thermohygrobaro.md">Thermo/Hygro/Baro</a> (S2001I, 
    S2001ID)</td>
  </tr>
  <tr>
    <td width="8%" align="center">5</td>
    <td width="92%"><a href="licht.md">Helligkeit</a> (S2500H)</td>
  </tr>
  <tr>
    <td width="8%" align="center">6</td>
    <td width="92%"><a href="pyrano.md">Pyrano (Strahlungsleistung)</a></td>
  </tr>
  <tr>
    <td width="8%" align="center">7</td>
    <td width="92%"><a href="kombi.md">Kombi</a> (KS200, KS300)</td>
  </tr>
</table>
&nbsp;<p>Die Adresse geht von 0 bis 7, sodass nur 3 Bit benötigt werden. Das restliche Bit wird für Temperaturvorzeichen 
oder als Hunderter der Windgeschwindigkeit verwendet.<br>
</p>
<p>
Besonders wichtig ist die Wiederholzeit der Telegramme, denn der Empfänger ist nur während einer kurzen Zeit aktiv. 
Zwei bis dreimal am Tag ist dieser Empfänger allerdings für längere Zeit eingeschaltet und lernt, welche Sensoren vorhanden sind. 
Nur zu diesen Zeiten werden dann später auch Telegramme empfangen. Die Wiederholraten sind abhängig vom Sensortyp und der eingestellten 
Adresse.<br>
Folgende Zusammenhänge bestehen:<br><br>
<table cellspacing="2" cellpadding="2" border="0">
<tr>
	<th>Typ</th>
	<th>Wiederholzeit</th>
</tr>
<tr>
	<td>Thermo</td>
	<td>177s - Adr * 0.5s</td>
</tr>
<tr>
	<td>ThermoHygro</td>
	<td>177s - Adr * 0.5s</td>
</tr>
<tr>
	<td>ThermoHygroBaro</td>
	<td>165s - Adr * 0.5s</td>
</tr>
<tr>
	<td>Regen</td>
	<td>173s - Adr * 0.5s</td>
</tr>
<tr>
	<td>Wind</td>
	<td>169s - Adr * 0.5s</td>
</tr>
<tr>
	<td>Helligkeit</td>
	<td>161s - Adr * 0.5s</td>
</tr>
<tr>
	<td>Strahlungsleistung</td>
	<td>157s - Adr * 0.5s</td>
</tr>
<tr>
	<td>Kombi</td>
	<td>153s - Adr * 0.5s</td>
</tr>
</table>
</p><br><br>
Bei der Erstellung dieser Beschreibung hat mir folgender Artikel sehr geholfen: <a href="http://www.elv.de">ELVJournal</a> 6/2000, PC-Wettersensor-Empfänger 
(ELV-Best. Nr. 68-390-61) .
Der dort beschriebene Empfänger ist für solche Forschungen auch gut geeignet, da er immer aktiv ist und die Telegramme gleich decodiert. 
Allerdings gilt das nicht für das Kombiprotokoll. Das Protokoll zwischen 
Empfänger und PC sowie eine Modifikation zum Empfang von 868MHz-Sensoren ist
<a href="pc_wx_rx.htm">hier</a> beschrieben.<br>

