### Pythonによる因数分解問題生成ツール (Factorization Problem Generator with Python)

[English follows Japanese]

## 概要

これは**Pythonを用いることにより因数分解の問題を簡単に生成**し，さらに**LaTeXコードに変換**するプロジェクトです．

元来因数分解の問題は適当な数を考えそれを展開することにより作成可能ですが，人力で実行するには大変面倒であります．そのため，Pythonを用いることにより，$[-9, 9]$の範囲で整数を2つ生成し，SymPyを用いて展開．その後，自作したLaTeX変換関数を用いファイルへ書き出します．

## 必要環境

- **Python**: 3.12以降，`sympy` がインストールされていること
- **LaTeX**: `lualatex` または `xelatex` が利用できるTeXディストリビューション（`extarticle`，`enumitem`，`fontspec` を使用）

なお，LaTeXについては，大量にファイルをアップロードする運用には向かないため，Overleafは推奨せず，VS Codeなどローカル環境を推奨します．

## 使い方

1. `expr.ipynb` をJupyter Notebook等で実行する．
2. カレントディレクトリに `output1.tex` 〜 `output5.tex` が生成される．
3. プリアンブルと `\input{...}` を含む main.tex を `lualatex` 等でコンパイルする．
4. 5枚分のプリント（各14問，2列レイアウト）を含むPDFが得られる．

掲出したPythonコード内では整数の生成は $[-9, 9]$ の整数の範囲で，ファイルは5個出力されるようになっています．ここは任意に対応しているため，必要に応じて書き換えてください．

## 既知の制限事項

- $(x + 0)(x + 1)$ や $(x + 3)(x + 3)$ など不自然な記法は排除していますが，$(x + 2)(x + 7)$ と $(x + 7)(x + 2)$ が同じファイル内に出てくる可能性を排除していません．
- 完全にランダムに整数を生成しているために，難易度は不規則的であります．
- 乱数シードを固定していないため，再生成時に特定のプリントを再現することができません．

## ライセンス

自由に使用してかまいませんが，それにより及ぼされた責任について，作成者は一切の責任を被らないこととします．

---

## Factorization Problem Generator with Python

### Overview

This project generates **factorization problems automatically using Python** and converts them into **LaTeX code** ready for typesetting.

Factorization problems can be created by expanding products of the form $(x+a)(x+b)$, but doing this by hand for dozens of problems is tedious. This tool uses Python to randomly generate two integers in the range $[-9, 9]$, expands the product symbolically with SymPy, and writes the result to `.tex` files via a custom LaTeX conversion function.

### Requirements

This project requires both Python and LaTeX.

- **Python**: version 3.12 or later, with `sympy` installed
- **LaTeX**: a TeX distribution supporting `lualatex` or `xelatex` (the included setup uses `extarticle`, `enumitem`, and `fontspec`)

Overleaf is not recommended for this project, since uploading many auto-generated files can be inconvenient. A local editor such as VS Code with a LaTeX extension is preferred.

### Usage

1. Run the cells of `expr.ipynb` in Jupyter Notebook (or your preferred environment).
2. Five files `output1.tex` through `output5.tex` will be generated in the working directory.
3. Compile a main `.tex` document that loads these files via `\input{...}` using `lualatex` (or `xelatex`).
4. The resulting PDF contains five worksheets, each with 14 factorization problems arranged in two columns.

Integers are sampled from $[-9, 9]$ and five files are produced by default. Both parameters can be adjusted by editing the corresponding lines in the notebook.

### Known Limitations

- Trivial or degenerate cases such as $(x+0)(x+1)$ or $(x+3)(x+3)$ are excluded, but **duplicate expansions** such as $(x+2)(x+7)$ and $(x+7)(x+2)$ may still appear within the same worksheet.
- Since integers are sampled uniformly at random, **the difficulty of problems is not controlled**, and problem sets may vary considerably in difficulty.
- The random seed is not fixed, so a specific worksheet cannot be reproduced after regeneration.

### License

You are free to use, modify, and redistribute this project. The author assumes no responsibility for any consequences arising from its use.
