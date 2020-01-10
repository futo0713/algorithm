# requestの使い方

### ざっくりした使い方

    requests.get()
    
Webサイトに行く、みたいな
    
    import requests

    url = 'https://example.com/'

    response = requests.get(url)
    
こんな使い方、responseは「Responseオブジェクト」と言うらしい

### Responseオブジェクトに入っているもの

    url: url属性

    ステータスコード: status_code属性

    レスポンスヘッダ: headers属性

    エンコーディング: encoding属性

    テキスト: text属性

    バイナリデータ: content属性







