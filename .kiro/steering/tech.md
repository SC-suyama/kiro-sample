# 技術スタック・ビルドシステム

## 核となる技術スタック

### フロントエンド
- **Vue.js 3** with Composition API
- 業務要件入力のためのシンプルで清潔なWebインターフェース
- リアルタイム進捗ダッシュボード・監視画面

### バックエンド
- **Python** with **FastAPI**（サーバーレス対応）
- 要件処理・システム生成のためのRESTful API
- AIワークフローの非同期処理

### データベース
- **PostgreSQL**（Amazon RDS）
- 要件・生成成果物・プロジェクトメタデータの構造化ストレージ
- RAGシステム用ベクトルストレージ統合

### AI/ML コンポーネント
- **OpenAI GPT-4** 日本語処理用カスタムプロンプト
- **Pinecone** + OpenAI Embeddings RAGシステム
- 仕様書・設計書・コード・テスト生成用カスタムAIエンジン

### インフラストラクチャ
- **AWS** サーバーレスアーキテクチャ（Lambda、ECS Fargate、S3、CloudFormation）
- **AWS Step Functions** ワークフロー オーケストレーション
- **CloudWatch** + **DataDog** 監視・アラート

### 開発・デプロイ
- **GitHub Actions** + **AWS CodePipeline** CI/CD
- **AWS CloudFormation** Infrastructure as Code
- **Hypothesis** プロパティベーステスト自動化

## 共通コマンド

### 開発環境セットアップ
```bash
# フロントエンド開発
npm install
npm run dev

# バックエンド開発
pip install -r requirements.txt
uvicorn main:app --reload

# データベースマイグレーション
alembic upgrade head

# テスト実行
pytest
npm run test
```

### デプロイ
```bash
# AWSへのデプロイ
aws cloudformation deploy --template-file infrastructure.yaml --stack-name business-spec-generator

# アプリケーションデプロイ
sam deploy --guided
```

### AIモデル管理
```bash
# AIプロンプト更新
python scripts/update_prompts.py

# モデル再訓練
python scripts/retrain_models.py
```

## アーキテクチャ原則

- **サーバーレスファースト**: 全コンポーネントをAWS Lambda/Fargate用に設計
- **AI駆動**: 全生成ステップを専用AIエンジンで実行
- **プロパティベーステスト**: 重要な業務ロジックを形式的プロパティで検証
- **日本語最適化**: 全NLPコンポーネントを日本語業務用語に調整