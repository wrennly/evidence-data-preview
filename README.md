# Evidence Data API — 公開データ見本

**公開資料を、出典・原文引用・観測時点付きのデータへ。**

官公庁の募集資料を読む営業担当者と、資料をソフトウェアに組み込む開発者に向けた
データ商品の試作です。最初の見本として、環境省のHTML/PDFから、件名・予算上限・
提案締切・納期・参加等級をCSV/JSONに整理しました。

**この公開物は5文書・5案件の固定した形式見本です。募集中案件の一覧・日次更新サービスではありません。**
過去の締切を含み、現在の応募可否は確認していません。政府・環境省の公式サービスではありません。

## まず見本を試す

- [JSONを読む](samples/notices.json)：値と、項目の意味が分かる見出し付き引用。
- [CSVをダウンロード](https://raw.githubusercontent.com/wrennly/evidence-data-preview/main/samples/notices.csv)：Excel等で確認する形式。
- [データの意味と出典](DATA-NOTES.md)：空欄、参加等級の例外、加工・利用条件。
- [実装から分かったこと](TECHNICAL-NOTES.md)：引用があっても項目を取り違え得る理由。

Python標準ライブラリだけで、公開見本を読み出せます。

```python
import json
from urllib.request import urlopen

url = "https://raw.githubusercontent.com/wrennly/evidence-data-preview/main/samples/notices.json"
with urlopen(url, timeout=15) as response:
    preview = json.load(response)
for record in preview["records"]:
    print(record["fields"]["title"]["value_raw"])
    print(record["fields"]["proposal_deadline"])
```

この見本の読み出しにAPIキーやメール登録は不要です。
REST API/MCPはローカル試作段階です。本リポジトリにはホスト型APIやインストール可能なMCPサーバーを同梱していません。

## 誰の、どの作業を減らすか

**受注・営業担当者**には、公告や添付資料から必要な条件を拾って比較・共有する作業。
**開発者**には、その情報を自社ツールで使うために形式を揃え、出典と変更を維持する作業。
映像分野に限定せず、今回の見本にはシステム運用・調査業務も含めています。

単なる公告一覧は、公式サイト・既存の入札サービス・顧客自身のAI利用でも得られます。
出典を追える項目、資料内の意味の区別、更新履歴が追加の価値になるかを確かめています。
履歴保存はローカル試作済みですが、この固定見本は改訂の時系列データを含みません。

## 価格の仮説 — 注文受付前

- 初回：範囲を合意した**20文書の一括データ、4,980円／1組織・一回**。
- 継続版の仮説：CSVは**月9,800円**、開発者向けAPI/MCPは**月19,800円**。

いずれも市場確認のための想定価格です。対象機関・更新頻度・利用条件・税を含む最終価格は未確定で、
現時点では購入・予約決済・契約を受け付けていません。20文書は20案件とは限りません。
再販売・顧客向け組込み条件は未設定です。

**この範囲・価格なら検討したい業務があれば、[用途・必要範囲を教えてください](https://github.com/wrennly/evidence-data-preview/issues/new?template=data-request.yml)。**
コメントは公開されます。機密資料・個人情報を記載しないでください。
「どの発注元が必要か」「CSVとAPI/MCPのどれを使うか」「今の方法で十分か」も歓迎します。

## 品質と限界

AIが値を抽出し、別のAIレビューで原資料の文脈を確認した固定見本です。
人間の専門家による監修、応募資格の判定、網羅性、将来文書の精度を保証するものではありません。
全ての値は原文文字列で、日付・金額の型付き検索は未提供です。
空欄は、この文書で記載を確認できない意味で、他の添付資料にも存在しないとは限りません。

## 開発・運営

**Wrennly / Evidence Data API**。AI主導で開発・調査・検証を行うプロジェクトです。
試作結果と制約を公開し、必要なデータ・形式・範囲を利用者の用途から決めていきます。
連絡・訂正依頼はこのリポジトリのIssuesへ。

---

### English summary

A public format preview of evidence-linked Japanese procurement data: five documents / five cases,
with source URLs, observation timestamps, verbatim field values and role-bearing quotes.
This is a fixed historical sample, not a live tender feed. Extraction and a separate semantic review
were AI-assisted; unattended production extraction is not yet validated. Hosted API/MCP access is not available.
Tell us your use case, source coverage, preferred format and whether the proposed prices fit your needs via Issues.
