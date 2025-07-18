# Rustの特徴と技術的負債・変更容易性に基づくPythonコード評価プロンプト

以下のRustの特徴を基準に、指定されたPythonファイルのコードを

- 5段階評価（1:皆無〜5:完璧）  
- 不足や改善点の指摘（該当行数や改善案を含む）

で評価してください。

---

## 評価基準

1. **メモリ安全性とコンパイル時チェックの観点**  
   - Pythonでメモリ安全性に類似した対策が取れているか（例: リソース管理、ガベージコレクションの適切利用、競合状態の回避など）  
   - 実行時エラーや例外処理の網羅性

2. **型システムの強さ（静的型付けの代替）**  
   - Pythonで型ヒント（Type Hints）や型チェックツール（mypy等）の利用状況  
   - インターフェースの明確さ、関数の引数や戻り値の型が適切に定義・使用されているか

3. **明示的なエラーハンドリング**  
   - 例外処理の実装状況（try-exceptの適切な使用）  
   - エラー検出や処理の抜け漏れがないか

4. **変更容易性（保守性・リファクタリングしやすさ）**  
   - コードの可読性や構造の整然さ  
   - 冗長さや重複の有無、モジュール分割の適切さ  
   - コメントやドキュメンテーションの充実度

5. **技術的負債の蓄積度合い**  
   - レガシーコードや古い設計に依存していないか  
   - 急ごしらえや暫定実装、ハック的コードの有無  
   - 保守や拡張を困難にしている設計上の問題点の存在

---

## 指摘フォーマット

- <項目名>：<指摘内容>  
- 該当行数：<該当箇所の行数～行数>  
- <改善案>

---

## 出力例

### 総合評価: 3 / 5

- メモリ安全性とコンパイル時チェック：3  
- 型システムの強さ：2  
- 明示的なエラーハンドリング：4  
- 変更容易性：3  
- 技術的負債：2

### 指摘事項

- 型システムの強さ：型ヒントがほとんど使われておらず、関数の引数や戻り値の型が不明瞭。  
- 該当行数：15～45  
- 改善案]PEP484準拠の型ヒントを導入し、mypyなどで静的型チェックを導入してください。

- 技術的負債：複数箇所で暫定的なハックコードが見られ、保守時に問題を生みそう。  
- 該当行数：80～100  
- 改善案：コードの意図を整理し、リファクタリングして暫定処理を除去してください。

---

## 指示

1. 指定されたPythonコード全体を読み込み、上記基準で評価してください。  
2. 評価スコアと共に、明確な指摘をフォーマットに沿って出力してください。  
3. 指摘は具体的に「何ができていないか」「どの部分か」「どう改善すれば良いか」を示してください。  
4. 出力はMarkdown形式で整形してください。

---

以上の指示に従って評価をお願いします。
