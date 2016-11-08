# サブレポート構成

## ファイル名
tag_list.jrxml

## 環境情報
- LaKeelBI studio 6.2.0
- LaKeelBI server 6.2.0
- その他詳細は244サーバー環境情報参照

## DB
Blueberry_DB設計書ver0.md参照

## パス
### レポート
/QA/Report/QA_01
### データソース
/QA/DataSource/check_ds

## レイアウト
![サブレポート.png](https://qiita-image-store.s3.amazonaws.com/0/124751/8a83dc6e-3ec9-30a4-2fbe-5fb70ddb1e56.png)

## コンポーネント
|No|項目名称|表示場所|タイプ|ファイル名|ソート順|表示形式|フォント|データ取得元|その他|
|:---:|---|---|:---:|---|:---:|:---:|---|---|---|
|1|タグ|レポート_詳細|文字列|-|-||MSｺﾞｼｯｸ|tag.t_name|タグ名称を表示|

## クエリ
```sql
SELECT
    t.name, t.no
FROM
    question q
        LEFT JOIN
    relay r ON q.no = r.no
        LEFT JOIN
    tag t ON t.no = r.tag_no
WHERE
    q.no= $P{P_RELAY_NO}
GROUP BY t.no
LIMIT 12
```
## 結合条件
- tag.no=relay.tag_no

## インプットコントローラー
なし
