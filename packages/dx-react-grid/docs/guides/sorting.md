# React Grid - Sorting

The Grid component supports sorting data by one or several column values. Use the corresponding plugins to manage the sorting state and sort data programmatically or via the UI (column headers and Group Panel).

Click several columns while holding `Shift` to sort data by these columns. Clicking a column while holding `Ctrl` (`Cmd` for MacOS) cancels sorting by this column.

## Related Plugins

The following plugins implement sorting features:

- [SortingState](../reference/sorting-state.md) - controls the sorting state
- [IntegratedSorting](../reference/integrated-sorting.md) - performs built-in data sorting
- [TableHeaderRow](../reference/table-header-row.md) - renders the header row with sorting indicators
- [GroupingPanel](../reference/grouping-panel.md) - renders the Group Panel with sorting indicators

Note that the [plugin order](./plugin-overview.md#plugin-order) is important.

## Basic Setup

Use the `SortingState`, `IntegratedSorting` and `TableHeaderRow` plugins to set up a Grid with simple static sorting.

Set the `TableHeaderRow` plugin's `showSortingControls` property to true to enable changing the sorting criteria in the header row.

## Uncontrolled Mode

In the [uncontrolled mode](controlled-and-uncontrolled-modes.md), specify the initial sorting conditions in the `SortingState` plugin's `defaultSorting` property.

.embedded-demo(grid-sorting/header-sorting)

## Controlled Mode

In the [controlled mode](controlled-and-uncontrolled-modes.md), pass the sorting options to the `SortingState` plugin's `sorting` property and handle the `onSortingChange` event to control the sorting state externally.

.embedded-demo(grid-sorting/controlled-mode)

## Using Sorting with Grouping

If you use grouping features, the Grid allows you to sort groups as well as data rows. For this, set the `GroupingPanel` plugin's `showSortingControls` property to true, which enables the sorting UI for the Group Panel's column headers.

Note that the `IntegratedGrouping` plugin should follow `IntegratedSorting` to provide correct group row sorting.

.embedded-demo(grid-sorting/group-sorting)

## Custom Sorting Algorithm

The [IntegratedSorting](../reference/integrated-sorting.md) plugin's `columnExtensions` property allows you to implement a custom sorting algorithm for a specific column.

.embedded-demo(grid-sorting/custom-sorting)

## Remote Sorting

It is possible to perform sorting remotely by handling sorting state changes, generating a request, and sending it to the server.

Sorting options are updated once an end-user interacts with a column header in the header row or Group Panel. Handle sorting option changes using the `SortingState` plugin's `onSortingChange` event and request data from the server using the applied sorting options. Once the sorted data is received from the server, pass it to the `Grid` component's `rows` property.

Note that in the case of remote sorting, you do not need to use the `IntegratedSorting` plugin.

.embedded-demo(grid-sorting/remote-sorting)
