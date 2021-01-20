Thermo/Hygro/Baro-Sensor (V1.1):  
  
    
    

<table cellspacing="2" cellpadding="2" border="0">
<tr>
	<td align="center" valign="top">00000000000000001</td>
	<td>T<SUB>1</SUB>T<SUB>2</SUB>T<SUB>3</SUB>T<SUB>4</SUB>1</td>
	<td>A<SUB>1</SUB>A<SUB>2</SUB>A<SUB>3</SUB>V1</td>
	<td>T<SUB>11</SUB>T<SUB>12</SUB>T<SUB>13</SUB>T<SUB>14</SUB>1</td>
	<td>T<SUB>21</SUB>T<SUB>22</SUB>T<SUB>23</SUB>T<SUB>24</SUB>1</td>
	<td>T<SUB>31</SUB>T<SUB>32</SUB>T<SUB>33</SUB>T<SUB>34</SUB>1</td>
	<td>F<SUB>11</SUB>F<SUB>12</SUB>F<SUB>13</SUB>F<SUB>14</SUB>1</td>
	<td>F<SUB>21</SUB>F<SUB>22</SUB>F<SUB>23</SUB>F<SUB>24</SUB>1</td>
	<td>F<SUB>31</SUB>F<SUB>32</SUB>F<SUB>33</SUB>F<SUB>34</SUB>1</td>
	<td>B<SUB>11</SUB>B<SUB>12</SUB>B<SUB>13</SUB>B<SUB>14</SUB>1</td>
	<td>B<SUB>21</SUB>B<SUB>22</SUB>B<SUB>23</SUB>B<SUB>24</SUB>1</td>
	<td>B<SUB>31</SUB>B<SUB>32</SUB>B<SUB>33</SUB>B<SUB>34</SUB>1</td>
	<td>N<SUB>1</SUB>N<SUB>2</SUB>N<SUB>3</SUB>N<SUB>4</SUB>1</td>
	<td>Q<SUB>1</SUB>Q<SUB>2</SUB>Q<SUB>3</SUB>Q<SUB>4</SUB>1</td>
</tr>
<tr>
	<td>Präambel</td>
	<td>___4___</td>
	<td>_0..7_V</td>
	<td>____0.1°___</td>
	<td>____1°_____</td>
	<td>____10°____</td>
	<td>____0.1%___</td>
	<td>____1%_____</td>
	<td>____10%____</td>
	<td>____1 hPa__</td>
	<td>___10 hPa__</td>
	<td>__100 hPa__</td>
	<td>__Null__</td>
	<td>_Check_</td>
</tr>
</table>
</P>

<P><br>V: Vorzeichen Temperatur (1 = negativ)<br>
T<SUB>1</SUB>..T<SUB>3</SUB>: 3 * 4Bit Temperatur (BCD)<br>
F<SUB>1</SUB>..F<SUB>3</SUB>: 3 * 4Bit Feuchte (BCD)<br>
B<SUB>1</SUB>..B<SUB>3</SUB>: 3 * 4Bit Luftdruck (BCD) - 200 hPa. Da mit 3 BCD-Ziffern nur ein Bereich bis 999 hPa möglich ist, werden 200 hPa als Offset abgezogen, sodass ein Messbereich von 200 hPa bis 1199 hPa entsteht.<br>
Warum das letzte Nibble vor den Checksummen NULL sein muss, verstehe ich nicht. Wahrscheinlich war es für die Tausenderstelle des Luftdrucks reserviert.</P></tt>
