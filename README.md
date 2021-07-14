# sample-ajax
授業中のリソース置き場所

ajaxのgetを行う為のテンプレート
## jQuery 側の json オブジェクトの準備
```javascript
formData = {};
```
{}は 空の json オブジェクト
```javascript
formData["param1"] = "テスト";
```
formData のプロパティは formData に["プロパティ文字列"] に値をセットして作成される

formData のプロパティは formData.プロパティ文字列と書くこともできます
```javascript
formData.param1 = "テスト";
```
## jQuery 側からサーバへデータを送る
```javascript
data: formData
```
