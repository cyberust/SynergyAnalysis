# VC Team Synergy Analysis Toolkit

## 概要 (Overview)

このリポジトリは、VC（ベンチャーキャピタル）の創業者チームと新規採用候補者間の潜在的な共創シナジーを分析・評価するためのPythonベースのツールキットです。Google Colaboratory (Colab) 上で動作し、提供されたCV（履歴書）やプロフィールテキストから、自然言語処理 (NLP) 技術を用いて以下の分析を行います。

*   **スキル抽出:** 各個人のスキルセットを特定し比較します。
*   **トピックモデリング:** 各個人の主要な専門分野や関心領域を抽出します。
*   **共起関係分析:** テキスト中の単語の共起関係をネットワークとして可視化し、関連性の強いキーワード群を把握します。

これらの分析を通じて、候補者の参画がチームの能力補完、事業戦略の加速化、成長機会の拡大にどのように貢献しうるかについての洞察を得ることを目的としています。

## ✨ Open in Colab ✨

以下のバッジをクリックすると、Google Colab でノートブックを開き、直接コードを実行できます。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/YOUR_REPOSITORY_NAME/blob/main/Synergy_Analysis_VC_Hiring.ipynb)

**重要:** 上記バッジのリンクURLに含まれる `YOUR_GITHUB_USERNAME`、`YOUR_REPOSITORY_NAME`、およびノートブックファイル名 (`Synergy_Analysis_VC_Hiring.ipynb`) は、ご自身のものに正しく置き換えてください。ブランチ名も `main` 以外の場合は適宜修正してください。

## 🚀 実行手順 (How to Run)

1.  **データの準備:**
    *   分析対象者（例: Arale Cohen氏, Yanay Geva氏, Yasuyuki Sakane氏）のCVまたはプロフィール情報をテキストファイル (`.txt`) で準備します。
    *   ご自身のGoogle Driveの「マイドライブ」直下に `VC_Analysis_Data` という名前のフォルダを作成します。
    *   作成したフォルダ内に、準備したテキストファイルをアップロードします。
        *   例: `My Drive/VC_Analysis_Data/arale_cohen_profile.txt`
2.  **Colabノートブックを開く:**
    *   上記の「Open in Colab」バッジをクリックするか、直接 [Synergy\_Analysis\_VC\_Hiring.ipynb](Synergy_Analysis_VC_Hiring.ipynb) （ノートブックファイルへのリンク）を開きます。
3.  **Google Driveのマウント:**
    *   ノートブックの最初のコードセル（ステップ1）を実行し、Google Driveへのアクセスを許可します。
4.  **ファイルパスとファイル名の設定:**
    *   ノートブックのステップ2にある `BASE_PATH` と `persons_files` の変数を、ご自身のGoogle Driveのフォルダパスとファイル名に合わせて正しく設定してください。
    ```python
    # ステップ2の該当箇所を修正
    BASE_PATH = '/content/drive/MyDrive/VC_Analysis_Data/' # ご自身のパスを確認
    persons_files = {
        'Arale Cohen': 'arale_cohen_profile.txt',    # ご自身のファイル名に修正
        'Yanay Geva': 'yanay_geva_profile.txt',      # ご自身のファイル名に修正
        'Yasuyuki Sakane': 'yasuyuki_sakane_profile.txt' # ご自身のファイル名に修正
    }
    ```
5.  **全てのセルを実行:**
    *   Colabのメニューから「ランタイム」を選択し、「すべてのセルを実行」をクリックします。
    *   各ステップの出力（テキスト抽出、スキル分析、トピックモデリング、共起関係分析の結果など）が順次表示されます。

## 📊 分析内容 (Analysis Performed)

*   **ステップ1-2:** 環境設定、ライブラリのインポート、基本設定。
*   **ステップ3:** Google Driveからテキストファイルを読み込み、テキストデータを抽出。
*   **ステップ4:** テキストデータの前処理（小文字化、不要文字除去、レンマ化、ストップワード除去など）。
*   **ステップ5:** 定義済みスキルキーワードリストに基づき、各個人のスキルを抽出・比較し、可視化。
*   **ステップ6:** LDA (Latent Dirichlet Allocation) を用いたトピックモデリングにより、各個人の主要なトピックを抽出し、ワードクラウドで可視化。
*   **ステップ7:** 単語の共起関係ネットワークを構築・可視化し、関連性の強い単語群を分析。
*   **ステップ8 (オプション):** 分析結果の統合レポート（テキストベース）。

## 🛠️ 使用技術 (Technology Stack)

*   Python 3
*   Google Colaboratory
*   主要ライブラリ:
    *   `spaCy`: テキスト前処理 (レンマ化、ストップワード除去など)
    *   `scikit-learn`: `CountVectorizer`, `LatentDirichletAllocation` (トピックモデリング)
    *   `nltk`: ストップワード処理
    *   `pandas`: データ整形 (スキル分析など)
    *   `matplotlib`, `seaborn`: グラフ描画
    *   `wordcloud`: ワードクラウド生成
    *   `networkx`: 共起関係ネットワーク分析・描画

## 📝 注意事項 (Important Notes)

*   **個人情報:** 分析対象のCVデータには個人情報が含まれる可能性があります。データの取り扱いには十分注意し、プライバシー保護の観点からGoogle Driveの共有設定やアクセス権限を適切に管理してください。
*   **分析精度:** NLPによる分析結果（スキル、トピック、共起関係など）は、入力テキストの質、前処理の方法、パラメータ設定によって変動します。あくまで分析の一助として活用し、最終的な判断は人間の洞察に基づいて行ってください。
*   **パラメータ調整:** ノートブック内の各種パラメータ（`SKILL_KEYWORDS`, `NUM_TOPICS`, `CountVectorizer`のパラメータ, `min_cooccurrence`など）は、分析対象のデータや目的に応じて適宜調整することで、より有益な結果が得られる可能性があります。

## 📄 ライセンス (License)

このプロジェクトは [MITライセンス](LICENSE) の下で公開されています。
