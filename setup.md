# macbook air(M1 2020)セットアップ手順

## アプリケーションのインストール

### Google Chrome

- https://www.google.com/intl/ja/chrome/

### Gogle Drive

- https://www.google.com/intl/ja_jp/drive/download/

### Slack

- https://apps.apple.com/jp/app/slack/id803453959?ls=1&mt=12

### AppCleaner

- https://freemacsoft.net/appcleaner/

### キーボード入力

- https://blog.y-yuki.net/entry/2020/04/15/000000

#### 標準キーボード

- caps lock → command
- 入力切り替え 「command + space」に変更

#### HHKB キーボード

- control ↔︎ command

### VScode

- https://code.visualstudio.com/download

#### code コマンドを使う

- https://code.visualstudio.com/docs/setup/mac
  - VSCode でコマンドパレットを開く（⇧⌘P）
  - 表示されたコマンドパレットに`> shell command`と入力。
  - `シェルコマンド : PATH内にcode-insidersコマンドをインストールします`を選択
  - `code .`

### Iterm2

- https://iterm2.com/downloads.html
- https://bottoms-programming.com/archives/mac-terminal-to-iterm2.html#toc4

#### Thema

- https://github.com/mbadolato/iTerm2-Color-Schemes
  - kolorit

#### Font

- https://github.com/powerline/fonts
  - Source Code Pro for Powerline Regular
  - 18pt

### Docker Desktop

###

- https://hub.docker.com/editions/community/docker-ce-desktop-mac/?tab=description

## ツールのインストール

### init

- `~/.zshrc`に以下を追加

```
typeset -U path PATH
path=(
  /opt/homebrew/bin(N-/)
  /opt/homebrew/sbin(N-/)
  /usr/bin
  /usr/sbin
  /bin
  /sbin
  /usr/local/bin(N-/)
  /usr/local/sbin(N-/)
  /Library/Apple/usr/bin
)
```

#### Git と GitHub を SSH で接続する

```shell
$ git config --global user.name IKDrocket
$ git config --global user.email yusuke1128rocket@gmail.com
$ git config --list

$ mkdir ~/.ssh
$ ssh-keygen -t rsa -b 4096 -C "yusuke1128rocket@gmail.com"
$ pbcopy < id_rsa.pub
```

- ~/.ssh/config

```config
Host github
HostName github.com
IdentityFile ~/.ssh/id_rsa
User git
```

- Github にて公開鍵を登録する

  - https://github.com/settings/keys

- GitHub への接続を確認

```shell
$ ssh -T git@github.com
```

### brew

- https://brew.sh/

```shell
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

$ echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/ユーザ名/.zprofile

$ brew -v
Homebrew 3.3.3
Homebrew/homebrew-core (git revision 7949d844e94; last commit 2021-11-09)
```

### Git

```shell
$ brew install git

$ export PATH=/usr/local/bin/git:$PATH >> ~/.zshrc

$ source ~/.zshrc

$ git --version
git version 2.33.1
```

### shell プロンプトの改造

`.zshrc`に以下を追加する。

```~/.zshrc
function parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}

COLOR_DEF=$'\e[0m'
COLOR_USR=$'\e[38;5;243m'
COLOR_DIR=$'\e[38;5;197m'
COLOR_GIT=$'\e[38;5;39m'
setopt PROMPT_SUBST
export PROMPT='${COLOR_USR}%n: ${COLOR_DIR}%~ ${COLOR_GIT}$(parse_git_branch)${COLOR_DEF}
# '
```

### asdf

- https://github.com/asdf-vm/asdf

```shell
$ brew install asdf

$ echo -e "\n. $(brew --prefix asdf)/asdf.sh" >> >> ~/.zshrc
```

#### python(asdf)

- https://github.com/danhper/asdf-python

```shell
$ asdf plugin-add python
$ asdf list-all python
$ asdf install python 3.9.8
$ asdf global python 3.9.8

$ python -V
Python 3.9.8
```

#### nodejs(asdf)

- https://github.com/asdf-vm/asdf-nodejs

```shell
$ brew install gpg gawk
$ asdf plugin-add nodejs
$ asdf list-all nodejs
$ asdf install nodejs 14.17.2
$ asdf global nodejs 14.17.2

$ node -v
v14.17.2
```

#### terraform

```
$ asdf plugin add terraform
$ asdf list all terraform
$ asdf install terraform 1.0.10
$ asdf global terraform 1.0.10

$ terraform -v
Terraform v1.0.10
on darwin_arm64
```

### aws cli

```shell
$ curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
$ sudo installer -pkg AWSCLIV2.pkg -target /
$ rm AWSCLIV2.pkg
$ aws --version
aws-cli/2.3.6 Python/3.8.8 Darwin/20.6.0 exe/x86_64 prompt/off
```

- `.aws`を Google ドライブより` ~/.aws`、aws 関連の公開鍵を Google ドライブより` ~/.ssh`に配置する

### PlantUML

1. Java のインストール

- https://www.azul.com/downloads/?version=java-17-lts&os=macos&architecture=arm-64-bit&package=jdk からインストール(asdf で m1 で動くやつがなかった)
- 下記コマンドで確認

```shell
$ ls /Library/Java/JavaVirtualMachines
$ java --version
```

2. Graphviz のインストール

- 以下のコマンドを実行

```shell
$ brew install graphviz
```

3. VScode の拡張機能にて PlantUML をインストール

### Postman

- https://qiita.com/zaburo/items/16ac4189d0d1c35e26d1
