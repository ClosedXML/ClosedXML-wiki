Open XML offers predefined formats for dates and numbers. The applied format will change according to the culture of the machine. For example NumberFormatId 2 for US will separate the decimal places with a dot yet the same file opened with a DE locale will display a comma.

You can use these codes in the following way:

```c#
range.Style.NumberFormat.NumberFormatId = #;
```
<table cellspacing="0" cellpadding="2" style="width:300px">

<thead>

<tr style="background-color:#000000; color:#ffffff">

<th>**ID**</th>

<th>**Format Code**</th>

</tr>

</thead>

<tbody>

<tr>

<td>0</td>

<td>General</td>

</tr>

<tr>

<td>1</td>

<td>0</td>

</tr>

<tr>

<td>2</td>

<td>0.00</td>

</tr>

<tr>

<td>3</td>

<td>#,##0</td>

</tr>

<tr>

<td>4</td>

<td>#,##0.00</td>

</tr>

<tr>

<td>9</td>

<td>0%</td>

</tr>

<tr>

<td>10</td>

<td>0.00%</td>

</tr>

<tr>

<td>11</td>

<td>0.00E+00</td>

</tr>

<tr>

<td>12</td>

<td># ?/?</td>

</tr>

<tr>

<td>13</td>

<td># ??/??</td>

</tr>

<tr>

<td>14</td>

<td>d/m/yyyy</td>

</tr>

<tr>

<td>15</td>

<td>d-mmm-yy</td>

</tr>

<tr>

<td>16</td>

<td>d-mmm</td>

</tr>

<tr>

<td>17</td>

<td>mmm-yy</td>

</tr>

<tr>

<td>18</td>

<td>h:mm tt  
</td>

</tr>

<tr>

<td>19</td>

<td>h:mm:ss tt  
</td>

</tr>

<tr>

<td>20</td>

<td>H:mm</td>

</tr>

<tr>

<td>21</td>

<td>H:mm:ss</td>

</tr>

<tr>

<td>22</td>

<td>m/d/yyyy H:mm</td>

</tr>

<tr>

<td>37</td>

<td>#,##0 ;(#,##0)</td>

</tr>

<tr>

<td>38</td>

<td>#,##0 ;[Red](#,##0)</td>

</tr>

<tr>

<td>39</td>

<td>#,##0.00;(#,##0.00)</td>

</tr>

<tr>

<td>40</td>

<td>#,##0.00;[Red](#,##0.00)</td>

</tr>

<tr>

<td>45</td>

<td>mm:ss</td>

</tr>

<tr>

<td>46</td>

<td>[h]:mm:ss</td>

</tr>

<tr>

<td>47</td>

<td>mmss.0</td>

</tr>

<tr>

<td>48</td>

<td>##0.0E+0</td>

</tr>

<tr>

<td>49</td>

<td>@</td>

</tr>

</tbody>

</table>