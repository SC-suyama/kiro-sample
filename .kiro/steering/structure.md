# プロジェクト構造・組織

## リポジトリレイアウト

```
business-spec-generator/
├── .kiro/                          # Kiro設定・仕様
│   ├── specs/                      # プロジェクト仕様書
│   └── steering/                   # AIアシスタント指導ルール
├── frontend/                       # Vue.js 3 アプリケーション
│   ├── src/
│   │   ├── components/            # Vueコンポーネント
│   │   ├── views/                 # ページビュー
│   │   ├── composables/           # Composition APIロジック
│   │   └── services/              # APIクライアントサービス
│   ├── tests/                     # フロントエンドテスト
│   └── package.json
├── backend/                        # FastAPI アプリケーション
│   ├── app/
│   │   ├── api/                   # APIルートハンドラー
│   │   ├── core/                  # 核となる業務ロジック
│   │   ├── ai_engines/            # AI生成エンジン
│   │   ├── models/                # データベースモデル
│   │   └── services/              # 業務サービス
│   ├── tests/                     # バックエンドテスト
│   ├── alembic/                   # データベースマイグレーション
│   └── requirements.txt
├── infrastructure/                 # AWS CloudFormation テンプレート
│   ├── templates/                 # Infrastructure as Code
│   ├── scripts/                   # デプロイスクリプト
│   └── monitoring/                # CloudWatch/DataDog設定
├── ai_prompts/                    # AIプロンプトテンプレート
│   ├── requirements_analysis/     # 自然言語処理
│   ├── specification_generation/  # 仕様書生成プロンプト
│   ├── design_generation/         # 設計書生成プロンプト
│   ├── code_generation/           # コード生成プロンプト
│   └── test_generation/           # テスト生成プロンプト
└── docs/                          # ドキュメント
    ├── api/                       # API ドキュメント
    ├── architecture/              # システムアーキテクチャ文書
    └── user_guides/               # ユーザーガイド
```

## 主要アーキテクチャコンポーネント

### AI生成エンジン（`backend/app/ai_engines/`）
- `natural_language_parser.py` - 日本語要件分析
- `specification_generator.py` - 業務仕様書生成
- `design_generator.py` - システム設計書生成
- `code_generator.py` - フルスタックコード生成
- `test_generator.py` - 包括的テストスイート生成
- `operations_generator.py` - CI/CD・監視生成

### 核となるサービス（`backend/app/services/`）
- `project_service.py` - プロジェクトライフサイクル管理
- `workflow_service.py` - AIワークフローオーケストレーション
- `deployment_service.py` - AWS デプロイ自動化
- `monitoring_service.py` - システム監視・アラート
- `improvement_service.py` - 請求最適化エンジン

### データモデル（`backend/app/models/`）
- `project.py` - プロジェクト・要件モデル
- `artifact.py` - 生成成果物モデル
- `deployment.py` - デプロイ・監視モデル
- `improvement.py` - 請求改善追跡

## 開発ワークフロー

### 機能開発
1. 複雑な機能は`.kiro/specs/`に仕様を作成
2. AIエンジンを最初に実装（核となる業務ロジック）
3. `backend/app/api/`にAPIエンドポイントを追加
4. `frontend/src/`にVue.jsコンポーネントを構築
5. Hypothesisを使用してプロパティベーステストを記述
6. 必要に応じてインフラテンプレートを更新

### AIプロンプト管理
- `ai_prompts/`に全プロンプトをバージョン管理で保存
- 明確な入出力スキーマを持つ構造化プロンプトテンプレートを使用
- 多様な日本語業務シナリオでプロンプトをテスト
- プロンプトパフォーマンス指標と最適化履歴を維持

### テスト戦略
- **プロパティベーステスト** AI生成の正確性検証
- **単体テスト** 個別コンポーネント
- **統合テスト** APIエンドポイント
- **E2Eテスト** 完全ワークフロー検証
- **パフォーマンステスト** AWSデプロイスケーラビリティ

## コード組織原則

- **ドメイン駆動設計**: 技術レイヤーではなく業務能力で組織化
- **AIファーストアーキテクチャ**: 全主要コンポーネントにAIエンジン対応
- **サーバーレスパターン**: 全コードをAWS Lambdaデプロイ用に設計
- **日本語サポート**: 全体でUTF-8、日本語最適化バリデーション
- **プロパティ検証**: 重要な業務ロジックを形式的プロパティで支援