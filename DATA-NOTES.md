# データの意味・出典・加工

公開見本：v0.1。5文書・5案件。取得時点はJSON各行の `observed_at`。
原資料の更新日時ではありません。現在の募集状況は未確認です。

## 出典

出典：環境省ホームページの次の公開資料。Wrennly / Evidence Data APIが抽出・加工して作成。
環境省が作成した未加工データではありません。

- https://www.env.go.jp/kanbo/chotatsu/chotatsu_03842.html
- https://www.env.go.jp/kanbo/chotatsu/chotatsu_04376.html
- https://www.env.go.jp/kanbo/chotatsu/chotatsu_04392.html
- https://www.env.go.jp/kanbo/chotatsu/chotatsu_04399.html
- https://www.env.go.jp/content/000317013.pdf

[環境省のコンテンツ利用方針](https://www.env.go.jp/mail.html)は、別の権利表記がない
コンテンツに[公共データ利用規約PDL1.0](https://www.digital.go.jp/resources/open_data/public_data_license_v1.0)
が適用されるとしています。利用する原資料と規約も確認してください。
原資料の権利を当プロジェクト独自のものとして表示したり、政府の推奨を示すものではありません。
この見本に政府ロゴ、地図、第三者画像、官公庁の担当者氏名・連絡先や原資料の全文は含めていません。

## 項目と空欄

- `title`：資料内の件名。落札方式の印字があれば残す。
- `budget`：明記された予算上限。税の計算式や単価を総予算と混同しない。
- `proposal_deadline`：技術提案・企画書の提出期限。質問受付期限や開札日時とは別。
- `bid_submission_deadline`：価格入札書の受付期限が明記された場合だけ収録。
  **今回の5文書では全て空欄で、陽性例の抽出能力は未検証です。**
- `delivery_deadline`：最終の納入・履行期限。
- `qualification_grades`：明記された等級の列挙。特にGX案件には別等級の条件付き例外がある。
  引用に例外文脈も残している。実際の参加可否の判定には使わない。

`not_stated_in_examined_document` は独立確認した対象文書内に記載がなかった意味です。
当該案件の全添付資料を確認した意味ではなく、予算0円・期限なし・参加不要を表しません。
`reviewed_sample` は固定見本の文脈を別のAIレビューで確認した印で、将来の自動品質保証ではありません。

## 引用と座標

`value_raw` は原文文字列です。日付や金額への変換はしていません。
根拠 `quote` は見出し等の意味文脈を含む原文です。
`start` / `end` は保存した正規化テキスト内のUnicodeコードポイント位置。
HTMLのbyte位置・ブラウザー表示位置・PDFページ座標ではありません。
原本を照合するためのraw hashと正規化テキストhashを行ごとに保持しています。
このリポジトリには原本全文やPDFを再配布していないため、hash・offset単独での完全再現はできません。
根拠の表示確認は原資料リンクと引用で行ってください。

## 訂正

Issuesに行ID、項目名、原資料URL、相違の内容を記載してください。
機密情報や応募者の個人情報は投稿しないでください。内容を確認して訂正版を公開します。
常時監視・一定時間内の訂正や更新を契約したサービスではありません。
