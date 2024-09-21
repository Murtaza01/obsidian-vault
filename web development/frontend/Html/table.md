# table

table is used for semantic purposes, but they also makes things easier to handle, to use tables we need the following html elements:

```html
<table>
	<caption>Name of the table</caption>
	<colgroup>
		<col>
	</colgroup>
	<thead>
	<tr>
		<th colspan="2">table head</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>table data</td>
	</tr>
	</tbody>
</table>
```

here is some information:
```html
<colgroup> <!-- to style groups -->
<col> <!-- we can add border and style different col based on how much cols we have, if we put one, it will style all of them -->
<tbody> <!-- for sematinc purposes -->
<thead> <!-- for sematinc purposes -->
<tr> <!-- needed to form a row -->
<td> <!-- table data, is a cell -->
<th> <!-- also a cell but its bold -->
<th colspan="2"> <!-- how much the cell takes space, two cells in this case -->
```

> styling tables

we need to put those styles to change the default behavior of tables:

```css
table{
	table-layout: fixed;
	border-collapse: collapse;
}
```

