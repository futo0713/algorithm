Pandasの使い方とかイロイロ
=============

pandasで列名を「ヘッダー（header）」、行名を「インデックス（index）」という

● csvファイルを読み込んでデータフレームを作成
-------------

  pd.read_csv()
  
  デフォルトの区切りがカンマ「,」

  csv_data  = pd.read_csv('./path/to/hoge.csv')
  
  こんな感じ

● csvファイルを読み込んでデータフレームを作成
-------------

  pd.read_table()
  
  デフォルトの区切りがタブ「\t」
  
  tsv_data  = pd.read_csv('./path/to/hoge.csv', delimiter='\t')
  
  これでも可、delimiterで区切り文字を指定
  
  sep='\t'でも区切り可能

--------------------------------------------------------------------------------------------
● headerがない時
-------------

  df_none = pd.read_csv('data/src/sample.csv', header=None)

  df_names = pd.read_csv('data/src/sample.csv', names=('A', 'B', 'C', 'D'))
  
  namesでヘッダーを設定することもできる

● headerの位置を指定したいとき
-------------

  df_header_2 = pd.read_csv('data/src/sample_header.csv', header=2)
  
  （0始まりで）1行目がヘッダーになり、2行目から始まる

● indexがあるとき
-------------

  df_header_index_col = pd.read_csv('data/src/sample_header_index.csv', index_col=0)
  
  0列目がindexとして認識される
  
--------------------------------------------------------------------------------------------
● 特定の「列」だけを読み込む場合
-------------

  df_none_usecols = pd.read_csv('data/src/sample.csv', header=None, usecols=[1, 3])
  
  usecolsで1、3「列」目だけが読み込まれる、これはヘッダーの名前でも可
  
  特定の列を除外して読み込む場合、無名関数（ラムダ式）を使うと便利。
  
  特に列数が多いファイルから少数の列を除外して読み込みたいたいときは読み込む列番号を大量に指定するより楽。
  
● ファイルの先頭「行」を除外して読み込む場合
-------------

  df_none = pd.read_csv('data/src/sample.csv', header=None, skiprows=2)
  
  skiprowsで先頭から1「行」目まで除外され、2「行」目から始まる
  
  df_none_skiprows = pd.read_csv('data/src/sample.csv', header=None, skiprows=[0, 2])
  
  この場合、0「行」目と2「行」目が除外される
  
  headerの行も考慮する必要があるので注意。
  
  特定の行だけを読み込む場合は、無名関数（ラムダ式）を使うと便利。
  
  特に行数が多いファイルから特定の行だけを読み込みたいたいときはスキップする行番号を指定するより楽。
  
● ファイルの末「行」を除外して読み込む場合
-------------
  df_none_skipfooter = pd.read_csv('data/src/sample.csv', header=None, skipfooter=1, engine='python')
  
  skipfooterで最後の1「行」を除外（末尾を数えるときは0を含まない）
  
  engine='python'は警告防止
  
● 最初の数行だけを読み込む場合
-------------

  df_none_nrows = pd.read_csv('data/src/sample.csv', header=None, nrows=2)
  
  nrowsで最初の2行（0行目と1行目）を読み込み
  
--------------------------------------------------------------------------------------------
● 型を指定して読み込む場合
-------------
  df_str = pd.read_csv('data/src/sample_header_index_dtype.csv', index_col=0, dtype=str)
  
  この場合すべての値がstrになる
  
  欠損値は常にfloat
  
  指定がなければ
  
● 列の型を指定したいとき
-------------

  df_str_col = pd.read_csv('data/src/sample_header_index_dtype.csv', index_col=0, dtype={'b': str, 'c': str})
  
  dtypeを辞書型で指定、列の指定はインデックスナンバーでもOK
  
 --------------------------------------------------------------------------------------------
● NaNとして認識される文字列
-------------
  ‘ ’（空欄）
  #N/A
  #N/A N/A
  #NA 
  -1.#IND
  -1.#QNAN
  -NaN 
  -nan
  1.#IND
  1.#QNAN
  N/A
  NA 
  NULL
  NaN
  n/a
  nan
  null

  NaNかどうかを判定するには「.isnull()」、TrueかFalse
  
● 指定の文字列をNaNとして認識させる場合
-------------

  df_nan_set_na = pd.read_csv('data/src/sample_header_index_nan.csv', index_col=0, na_values='-')
  
  na_valuesによって-がNaNとして認識させる

● NaNとして認識させない
-------------

  df_nan_no_filter = pd.read_csv('data/src/sample_header_index_nan.csv', index_col=0, na_filter=False)
  
  na_filter=Falseですべての値がNaNとは認識されない
  
  
  
  
