(c) 2001, 2002, 2003, 2004 Helmut Bayerlein.<br><br><br>

<strong>Protokollversion V1.1<br></strong>
Codierung eines Bits: <ul>
	<li>die Länge eines Bits beträgt 1831.05µs, entsprechend 546.13 Hz
	<li>sie wird abgeleitet von 32768 Hz : 20 * 3
	<li>das Puls-Pausenverhältnis beträgt 1:2 bzw. 2:1
	<li>eine logische 0 wird durch einen HF-Träger von 1220.7µs und 610.4µs Pause dargestellt
	<li>eine logische 1 wird durch einen HF-Träger von 610.4µs und 1220.7µs Pause dargestellt
</ul>
Die Präambel besteht aus 16 * 0 und 1 * 1.<br>
Die Daten werden immer als 4bit-Nibble übertragen. Danach folgt eine 1.<br>
Das LSBit wird zuerst übertragen.<br><br>
Für die Quersumme am Schluss werden alle Nibbles beginnend mit dem Typ XOR-verknüpft<br><br>
Der Typ besteht aus 3 Bit, die wie folgt codiert sind. Die Links zeigen die einzelnen Protokolle:
<ol start="0">
	<li><a href="thermo_alt.htm">Thermo</a>
	<li><a href="thermohygro_alt.htm">Thermo/Hygro</a>
	<li><a href="regen_alt.htm">Regen</a>
	<li><a href="wind_alt.htm">Wind</a>
	<li><a href="thermohygrobaro_alt.htm">Thermo/Hygro/Baro</a>
</ol>
Von dieser Protokollversion habe ich noch keine Helligkeitssensoren oder Pyranometer gemessen, sodass ich deren
Aufbau nicht beschreiben kann.<br><br>
Die Adresse geht von 0 bis 7, sodass nur 3 Bit benötigt werden. Das restliche Bit wird für Temperaturvorzeichen 
oder als Hunderter der Windgeschwindigkeit verwendet.<br>
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
</table>
</p>
Die Aussendung der Telegramme erfolgt dreimal hintereinander im Abstand von 100ms.<br>
