# FastAPI Hello World for Cloud Run

`/` では API ドキュメント (`/docs`) を開くよう案内し、`/hello_world` で `{"message": "hello world"}` を返す FastAPI アプリです。ローカル実行と Docker 実行の 2 パターンを日本語でまとめています。

## 1. 仮想環境を使ってローカルで実行する
1. プロジェクトへ移動  
   ```bash
   cd "api_hello_world"
   ```
2. 仮想環境を作成してアクティベート  
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate        # Windows: .venv\Scripts\activate
   ```
3. 依存パッケージをインストール  
   ```bash
   pip install -r requirements.txt
   ```
4. 開発サーバーを起動  
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8080   # 自動再起動したい場合は --reload を追加
   ```
5. ブラウザで `http://127.0.0.1:8080/` を開き、`http://0.0.0.0:8080/docs` への案内が出ることを確認。`http://127.0.0.1:8080/hello_world` で `{"message":"hello world"}` を確認。

## 2. Docker を使って実行する
1. プロジェクトへ移動  
   ```bash
   cd "api_hello_world"
   ```
2. コンテナイメージをビルド  
   ```bash
   docker build -t fastapi-hello .
   ```
3. コンテナを起動（ホストの 8080 に公開）  
   ```bash
   docker run -p 8080:8080 fastapi-hello
   ```
4. ブラウザで `http://127.0.0.1:8080/` を開き、`http://0.0.0.0:8080/docs` への案内が出ることを確認。`http://127.0.0.1:8080/hello_world` で `{"message":"hello world"}` を確認。
