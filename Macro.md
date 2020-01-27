# MacroのTips
一回書いた記述は忘れたくないでござる


### 表の最終行を取得

    MaxRow = Worksheets("ParamSheet").Range("A2").End(xlDown).Row
    
### RangeとCells
決め打ちのときRange / 座標っぽい感じにするときにCells / 変数を使うときはCells

    Cells(MaxRow, 2)
    Range("B4")

### 値を取得

    .Value

### 今日という日は一度きり

    Year(Date)
    Month(Date)
    Day(Date)













