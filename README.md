# How to customize caption row height in Flutter DataTable (SfDataGrid)?

In this article, we will show how to customize caption row height in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the SfDataGrid widget with the required properties. To customize the height of the [CaptionSummaryRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowType.html#captionSummaryCoveredRow) when grouping, handle the [onQueryRowHeight](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onQueryRowHeight.html) callback. By default, the CaptionSummaryRow uses the height specified in the SfDataGrid.rowHeight property. To override this, check if the current row is a caption summary row using the [getRowDetails](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/getRowDetails.html) method from the controller within the onQueryRowHeight callback, and assign the appropriate height accordingly.

```dart
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: SfDataGrid(
        source: employeeDataSource,
        controller: _dataGridController,
        allowExpandCollapseGroup: true,
        columnWidthMode: ColumnWidthMode.fill,
        gridLinesVisibility: GridLinesVisibility.both,
        headerGridLinesVisibility: GridLinesVisibility.both,
        onQueryRowHeight: (details) {
          DataGridRowDetails? rowDetails =
                    _dataGridController.getRowDetails(details.rowIndex);
          if (rowDetails != null && rowDetails.rowType == RowType.captionSummaryCoveredRow) {
                return 90.0;
          }
          return details.rowHeight;
        },
        columns: <GridColumn>[
          GridColumn(
            columnName: 'id',
            label: Container(
              padding: EdgeInsets.all(16.0),
              alignment: Alignment.center,
              child: Text('ID'),
            ),
          ),
          GridColumn(
            columnName: 'name',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Name'),
            ),
          ),
          GridColumn(
            columnName: 'designation',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Designation', overflow: TextOverflow.ellipsis),
            ),
          ),
          GridColumn(
            columnName: 'salary',
            label: Container(
              padding: EdgeInsets.all(8.0),
              alignment: Alignment.center,
              child: Text('Salary'),
            ),
          ),
        ],
      ),
    );
  }
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-customize-caption-row-height-in-Flutter-DataTable-SfDataGrid).