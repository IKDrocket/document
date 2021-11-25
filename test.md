## pytest

```shell

# カレントディレクトリ内のテストファイル全て

$ pytest

# HTML 形式でカバレッジを表示、出力

pytest --cov=. --cov-report=html

# テストケースごとに表示

$ pytest -v

# ファイルを指定してテスト

$ pytest -v test_get_core_user_admin.py

# テストケースごとに詳細

pytest -vs test_get_core_user_admin.py

```
