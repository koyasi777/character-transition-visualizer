# Character Transition Visualizer

---

## 🇯🇵 日本語 (Japanese)

### 概要
Character Transition Visualizer は、テキスト中の文字どうしの連接をネットワークとして可視化する、単一 HTML ファイルのブラウザアプリケーションです。入力テキストを解析し、文字をノード、隣接する文字のつながりをリンクとしてグラフ化します。

#### 3つの解析モード
- **自動判定**: 日本語を含む入力は「文字単位」で解析し、日本語を含まない入力はローマ字からひらがなへ変換して解析します。
- **ローマ字→ひらがな**: ローマ字入力をひらがなへ変換して解析します。
- **文字単位**: 文字をそのまま 1 文字ずつ解析します。

### 主な機能
* **文字連接ネットワークの可視化**
  * 文字をノードとして表示し、隣接する文字のつながりをリンクとして集計します。
  * 同じ連接が繰り返されるほどリンクの重みが増えます。
* **高精度なローマ字変換**
  * m 同化や tch による促音に対応。
  * マクロンや一部の表記ゆれを吸収。
  * 小書き仮名や拡張外来音を含む多くのパターンを網羅。
* **柔軟な表示制御**
  * 最小リンク重みでの絞り込み、上位割合での重要リンク強調・単独表示。
  * ラベル表示の ON/OFF 切り替え。
* **レイアウトと 3D 表示**
  * 任意のタイミングでの再レイアウト。
  * 3D 表示やオートローテーション（自動回転）の切り替え。
* **多様な入出力**
  * テキストの直接貼り付け、ローカルファイルの読み込み。
  * 現在のグラフの SVG 書き出し。
* **充実した統計表示**
  * 対象文字数、ノード数、表示/強調リンク数、変換率、プレビュー、上位リンク一覧などを確認可能。

### 動作環境・対応ファイル
* **動作環境**: モダンブラウザ（ビルドや外部フレームワーク不要、単一 HTML ファイルで動作）
* **対応ファイル**: `.txt`, `.csv`, `.tsv`, `.md`, `.log`, `.json`

### 使い方
1. HTML ファイルをブラウザで開きます。
2. テキストを貼り付けるか、ローカルファイルを読み込みます。
3. 解析モードを選びます。
4. 「解析して描画」を実行します。
5. 必要に応じて各種設定（最小リンク重み、ノード反発の強さ、3D 表示など）を調整します。
6. 必要に応じて再レイアウトや SVG 書き出しを行います。

### 操作方法
* **ノードをドラッグ**: ノードを移動して固定
* **固定済みノードをダブルクリック**: 固定解除
* **背景をドラッグ**: 表示位置を移動（パン）
* **Shift + 背景ドラッグ**: 3D 回転
* **マウスホイール**: 拡大縮小

### 仕組み・注意事項
このツールは、処理後の文字列から隣接する文字の組を集計してグラフを作ります。句読点や空白では連接が切られます。
* **例 (かなかな)**: 「か→な」「な→か」「か→な」として集計されます。
* **注意**: 対象文字が 2 文字未満の場合、リンクは構築されません。文字単位モードでは、非空白かつ非句読点の文字が対象となります。

---

## 🇬🇧 English

### Overview
Character Transition Visualizer is a browser-based single-file HTML application that visualizes character-to-character transitions in text as a network graph. It analyzes input text, turns characters into nodes, and converts adjacency between characters into weighted links.

#### Three Analysis Modes
- **Auto**: Chooses the analysis method based on the input. Text containing Japanese characters is analyzed in Raw mode; otherwise, it is converted from Romaji to Hiragana.
- **Romaji -> Hiragana**: Converts Romaji input to Hiragana before analysis.
- **Raw**: Analyzes the input one character at a time without conversion.

### Key Features
* **Network Visualization**
  * Characters are displayed as nodes, and adjacent relationships are aggregated as links.
  * Repeated transitions increase link weight.
* **Romaji Conversion Support**
  * Handles m-assimilation and sokuon patterns (e.g., tch).
  * Normalizes macrons and spelling variants.
  * Supports combinations including small kana and extended foreign-sound patterns.
* **Display Controls**
  * Filter links by minimum weight, highlight top links by ratio, or show *only* important links.
  * Toggle labels on and off.
* **Layout and 3D View**
  * Re-run layout at any time.
  * Toggle 3D view and auto-rotation.
* **Input and Output**
  * Paste text directly or load local text-based files.
  * Export the current graph as SVG.
* **Statistics and Inspection**
  * View token/node/edge counts, mode indicator, conversion coverage, preview output, and top edges table.

### Requirements & Supported Files
* **Requirements**: Modern web browser (No build step or external framework required; runs as a single HTML file).
* **Supported files**: `.txt`, `.csv`, `.tsv`, `.md`, `.log`, `.json`

### Usage
1. Open the HTML file in a web browser.
2. Paste text into the input area or load a local file.
3. Select an analysis mode.
4. Run "Analyze and Render".
5. Adjust settings as needed (minimum link weight, node repulsion strength, 3D depth, etc.).
6. Re-layout the graph or export it as SVG when needed.

### Controls
* **Drag a node**: Move and pin the node.
* **Double-click a pinned node**: Unpin the node.
* **Drag the background**: Pan the view.
* **Shift + drag the background**: Rotate in 3D.
* **Mouse wheel**: Zoom.

### How it Works & Notes
The tool builds a graph from adjacent character pairs in the processed sequence. Punctuation and whitespace break the sequence.
* **Example (k a n a k a n a)**: Converted to "かなかな", the graph includes transitions like "か -> な", "な -> か", and "か -> な".
* **Notes**: If fewer than two target characters are available, no links are produced. In Raw mode, non-whitespace and non-punctuation characters are analyzed directly.
