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

### ユーザーフォームのオープン / クローズ
    
    UserForm1.Show
    Unload UserForm1

### ユーザーフォームのTextBox / 初期値入力

    UserForm1.TextBox1.Text = "aaa"

「UserForm1.Show」の前に挿入する

### ユーザーフォームのLabel / フォントとか
プロパティの「Font」でボタンを押すと、ボックスが出てきていろいろ編集できる



    MaxRow = Worksheets("ParamSheet").Range("A2").End(xlDown).Row

    'sample number
    'PramInForm.Label3.Caption = Worksheets("ParamSheet").Cells(MaxRow, 1)
    
    'test date
    'Dim Y As String
    'Dim m As String
    'Dim d As String
    
    'Y = Worksheets("ParamSheet").Cells(MaxRow, 2)
    'm = Worksheets("ParamSheet").Cells(MaxRow, 3)
    'd = Worksheets("ParamSheet").Cells(MaxRow, 4)
    
    'PramInForm.Label5.Caption = Y + "/" + m + "/" + d
    
    'Laser source
    'PramInForm.TextBox1.Text = Worksheets("ParamSheet").Cells(MaxRow, 5)
    'PramInForm.TextBox2.Text = Worksheets("ParamSheet").Cells(MaxRow, 6)
    'PramInForm.TextBox3.Text = Worksheets("ParamSheet").Cells(MaxRow, 7)
    
    'PramInForm.Show


