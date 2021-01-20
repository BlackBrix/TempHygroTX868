Wind-Sensor (V1.2):  
  
  

<table cellspacing="2" cellpadding="2" border="0">
<tr>
	<td align="center" valign="top">00000001</td>
	<td>T<SUB>1</SUB>T<SUB>2</SUB>T<SUB>3</SUB>T<SUB>4</SUB>1</td>
	<td>A<SUB>1</SUB>A<SUB>2</SUB>A<SUB>3</SUB>V1</td>
	<td>W<SUB>11</SUB>W<SUB>12</SUB>W<SUB>13</SUB>W<SUB>14</SUB>1</td>
	<td>W<SUB>21</SUB>W<SUB>22</SUB>W<SUB>23</SUB>W<SUB>24</SUB>1</td>
	<td>W<SUB>31</SUB>W<SUB>32</SUB>W<SUB>33</SUB>W<SUB>34</SUB>1</td>
	<td>R<SUB>11</SUB>R<SUB>12</SUB>R<SUB>13</SUB>R<SUB>14</SUB>1</td>
	<td>R<SUB>21</SUB>R<SUB>22</SUB>R<SUB>23</SUB>R<SUB>24</SUB>1</td>
	<td>R<SUB>31</SUB>R<SUB>32</SUB>B<SUB>1</SUB>B<SUB>2</SUB>1</td>
	<td>Q<SUB>1</SUB>Q<SUB>2</SUB>Q<SUB>3</SUB>Q<SUB>4</SUB>1</td>
	<td>S<SUB>1</SUB>S<SUB>2</SUB>S<SUB>3</SUB>S<SUB>4</SUB>1</td>
</tr>
<tr>
	<td>Präambel</td>
	<td>___3___</td>
	<td>_0..7_V</td>
	<td>_0.1 km/h__</td>
	<td>___1 km/h__</td>
	<td>__10 km/h__</td>
	<td>____1°_____</td>
	<td>____10°____</td>
	<td>_100°__B_</td>
	<td>_Check_</td>
	<td>_Summe_</td>
</tr>
</table>
</P>

<P><br>V: 100 km/h Windgeschwindigkeit<br>
W<SUB>1</SUB>..W<SUB>3</SUB>: 3 * 4Bit Windgeschwindigkeit (BCD)<br>
R<SUB>1</SUB>..R<SUB>3</SUB>: 2&frac12; * 4Bit Windrichtung (BCD)<br>
B: Schwankungsbreite (0 = &plusmn;0°, 1 = &plusmn;22.5°, 2 = &plusmn;45°, 3 = &plusmn;67.5°)</P></tt>
