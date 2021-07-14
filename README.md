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
```javascript
{
	"param1": "テスト"
}
```
http://localhost/app/form-action-json.php?param1=%E3%83%86%E3%82%B9%E3%83%88&_=1626243689251

というフォーマットにjQueryに加工されてサーバのPHPが呼び出されます
## PHPでデータを受け取る
QuerString と呼ばれる ? 以降の文字列が$_GET にセットされてPHPに入る
```
param1=%E3%83%86%E3%82%B9%E3%83%88&_=1626243689251
```
<b>$_GET["param1"]</b> に"テスト"がセットされてスーパーグローバル変数として利用可能となる。
## PHP で json 文字列を返す為に, stdClass という簡易オブジェクトを作成して利用する
```php
$json = new stdClass;
$json-> = $_GET;
```
## $.ajaxに返す為の json フォーマットの文字列を　json_encode 関数で作成する
```php
print json_encode( $json, JSON_UNESCAPED_UNICODE | JSON_PRETTY_PRINT );
```
## PHP より返却された json を .done で data として受け取る
```ajax
{
	"get": {
		"param1": "テスト",
		"_": "1626244995036"
	},
	"post": [],
	"session": []
}
```

