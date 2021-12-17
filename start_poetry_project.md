## インストール
```
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
```

## 新規に立ち上げる場合

```shell
poetry new <project-name>
```

```
project-name
├── README.rst
├── project-name
│   └── __init__.py
├── pyproject.toml
└── tests
    ├── __init__.py
    └── test_project-name.py
```

## 既にあるプロジェクトを poetry 管理下に置く場合

```shell
cd project_xyz
poetry init
```

## 仮想環境のセットアップ

```
poetry install --no-interaction
```

## 依存パッケージの追加

```
poetry add <package-name>
```

## 仮想環境に入る
```
poetry shell
```

## 仮想環境外でコマンドを実行する
```
poetry run <command>
```
