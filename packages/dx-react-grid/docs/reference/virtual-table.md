# VirtualTable Plugin Reference

A plugin that renders a scrollable table instead of a static one. It contains the [VirtualTable.Row](#plugin-components) and [VirtualTable.Cell](#plugin-components) components that provide ways to customize virtual table rows and columns and can be extended by other plugins.

## User Reference

### Dependencies

- [DragDropProvider](drag-drop-provider.md) [Optional]
- [DataTypeProvider](data-type-provider.md) [Optional]

### Properties

Name | Type | Default | Description
-----|------|---------|------------
height | number | 530 | The virtual table's height.
estimatedRowHeight | number | `37` for [Bootstrap3](https://www.npmjs.com/package/@devexpress/dx-react-grid-bootstrap3); `48` for [Material UI](https://www.npmjs.com/package/@devexpress/dx-react-grid-material-ui) | Estimated row height. Specify the average value for a table whose rows have different heights.
columnExtensions? | Array&lt;[Table.ColumnExtension](table.md#tablecolumnextension)&gt; | Additional column properties that the plugin can handle.
cellComponent | ComponentType&lt;[Table.DataCellProps](table.md#tabledatacellprops)&gt; | | A component that renders a table cell.
rowComponent | ComponentType&lt;[Table.DataRowProps](table.md#tabledatarowprops)&gt; | | A component that renders a table row.
noDataCellComponent | ComponentType&lt;[Table.NoDataCellProps](table.md#tablenodatacellprops)&gt; | | A component that renders a table cell when the table is empty.
noDataRowComponent | ComponentType&lt;[Table.RowProps](table.md#tablerowprops)&gt; | | A component that renders a table row when the table is empty.
stubCellComponent | ComponentType&lt;[Table.CellProps](table.md#tablecellprops)&gt; | | A component that renders a stub table cell if the cell value is not provided.
stubHeaderCellComponent | ComponentType&lt;[Table.CellProps](table.md#tablecellprops)&gt; | | A component that renders a stub header cell if the cell value is not provided.
messages? | [Table.LocalizationMessages](table.md#localization-messages) | | An object that specifies the localization messages.

## Plugin Components

Name | Properties | Description
-----|------------|------------
VirtualTable.Cell | [Table.DataCellProps](table.md#tabledatacellprops) | Renders a table data cell.
VirtualTable.Row | [Table.DataRowProps](table.md#tabledatarowprops) | Renders a table data row.
VirtualTable.NoDataCell | [Table.CellProps](table.md#tablecellprops) | Renders a table cell when the table is empty.
VirtualTable.NoDataRow | [Table.RowProps](table.md#tablerowprops) | Renders a table row when the table is empty.
VirtualTable.StubCell | [Table.CellProps](table.md#tablecellprops) | Renders a stub table cell.
VirtualTable.StubHeaderCell | [Table.CellProps](table.md#tablecellprops) | Renders a stub table header cell.

If you specify additional properties, they are added to the component's root element.

## Plugin Developer Reference

### Imports

Name | Plugin | Type | Description
-----|--------|------|------------
rows | Getter | Array&lt;any&gt; | Rows to be rendered by the virtual table view.
columns | Getter | Array&lt;[Column](grid.md#column)&gt; | Columns the virtual table view should render.
getRowId | Getter | (row: any) => number &#124; string | A function used to get a unique row identifier.
getCellValue | Getter | (row: any, columnName: string) => any | A function used to get a cell’s value.

### Exports

Name | Plugin | Type | Description
-----|--------|------|------------
tableHeaderRows | Getter | Array&lt;[TableRow](table.md#tablerow)&gt; | Header rows to be rendered.
tableBodyRows | Getter | Array&lt;[TableRow](table.md#tablerow)&gt; | Body rows to be rendered.
tableColumns | Getter | Array&lt;[TableColumn](table.md#tablecolumn)&gt; | Columns to be rendered.
table | Template | Object? | A template that renders the virtual table.
tableCell | Template | [Table.CellProps](table.md#tablecellprops) | A template that renders a virtual table cell.
tableRow | Template | [Table.RowProps](table.md#tablerowprops) | A template that renders a virtual table row.
