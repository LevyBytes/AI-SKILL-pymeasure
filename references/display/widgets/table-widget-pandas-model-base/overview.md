# pymeasure.display.widgets.table_widget.PandasModelBase

*class *pymeasure.display.widgets.table_widget.PandasModelBase(*column_index=None*, *results_list=[]*, *parent=None*)

Bases: `QAbstractTableModel`

This class supplies a model for managing multiple panda dataframes and presenting them as one table.

The multiple pandas dataframes are passed in as ResultTable class instances, and each one must have the same column count.

Assumptions: - Series in the dataframe are identical; this count is called k - Series length may vary; this count is called l(x), where x=1..n

The data may be arranged as follows: - By column: each series uses its own column, giving table shape: (k*n) x (max(l(x) x=1..n) - By row: columns stay fixed to the series count, giving table shape: k x (sum of l(x) x=1..n)
