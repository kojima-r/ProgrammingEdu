# 🖥 Macでの開発環境構築ガイド

このドキュメントでは、Mac上でPython開発を行うための基本的な環境構築手順を説明します。

---

# 📌 全体の流れ

1. ターミナルを開く
2. Homebrewの確認
3. Gitの確認
4. GitHub（SSH）設定
5. **自分がフォークしたリポジトリをクローン**
6. Miniforge（conda）導入
7. 仮想環境の構築
8. Hello Worldで動作確認
9. VS Codeの設定

---

# ① 🧭 ターミナルを開く

### 方法1

Finder → 「移動」→「ユーティリティ」→「ターミナル」

### 方法2（おすすめ）

`command + space` → 「Terminal」と入力

---

# ② 🍺 Homebrew の確認

```bash
brew --version
```

バージョンが表示されればOK。

表示されない場合はインストール：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

# ③ 🧩 Git の確認

```bash
git --version
```

表示されなければ：

```bash
brew install git
```

---

# ④ 🔐 GitHub の SSH セットアップ

## 4-1. SSH鍵の作成（推奨方式）

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

* 保存先はそのままEnterでOK
* パスフレーズは任意

---

## 4-2. 公開鍵の確認

```bash
cat ~/.ssh/id_ed25519.pub
```

表示された文字列をコピー。

---

## 4-3. GitHubへ登録

1. [https://github.com/settings/ssh/new](https://github.com/settings/ssh/new) を開く
2. 以下を入力

   * **Title**：任意
   * **Key type**：Authentication Key
   * **Key**：コピーした公開鍵
3. 「Add SSH key」をクリック

---

## 4-4. 接続確認

```bash
ssh -T git@github.com
```

以下のように表示されれば成功：

```
Hi username! You've successfully authenticated...
```

---

# ⑤ 📂 リポジトリをクローン

⚠ **重要**

クローンするのは **自分がフォークしたリポジトリ** です。
このリポジトリを自分のアカウントでフォークしたものを想定しています．
フォークはgithubのこのリポジトリのページから右上の「Fork」ボタンで行うことができます

例：

```bash
cd ~
git clone git@github.com:あなたのGitHubユーザー名/フォークしたリポジトリ名.git
```

### 例

もしフォークしたリポジトリ名が `ProgrammingEdu` なら：

```bash
git clone git@github.com:yourname/ProgrammingEdu.git
```

---

# ⑥ 🐍 Miniforge（conda）のインストール

```bash
brew install --cask miniforge
```

---

# ⑦ ⚙ conda の初期設定

```bash
conda init zsh
source ~/.zshrc
```

---

# ⑧ 🧪 仮想環境の構築

```bash
cd ~/フォークしたリポジトリ名
conda env create -f environment.yml
conda activate clinfo
```

---

# ⑨ 👋 Hello World（動作確認）

```bash
python
```

```python
print("Hello World")
```

`Hello World` と表示されれば成功。

---

# ⑩ 🧑‍💻 Visual Studio Code のインストール

1. [https://code.visualstudio.com/](https://code.visualstudio.com/) からダウンロード
2. 起動
3. Extensionsで「Python（Microsoft）」をインストール

---

## 🔧 Pythonインタプリタの設定

1. `Command + Shift + P`
2. `Python: Select Interpreter`
3. `clinfo` 環境を選択

---

## 🧪 VS Code上で再確認

```
Terminal → New Terminal
```

```bash
conda activate clinfo
python
```

```python
print("Hello World")
```

表示されれば環境構築完了です。

---

# ✅ 完了

これでMacでのPython開発環境構築は完了です。

