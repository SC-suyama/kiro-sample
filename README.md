# Business Spec Generator

## 概要

Business Spec Generatorは、日本語で記述された「受注〜請求〜入金確認」業務要件を完全に動作するシステムに変換するAI駆動システムです。

## 主要機能

- **自然言語要件分析**: 日本語業務要件の自動構造化
- **AI仕様書生成**: 機能要件・非機能要件の自動生成
- **AI設計書生成**: システムアーキテクチャ・データベース設計の自動生成
- **AIコード生成**: Vue.js 3 + FastAPI + PostgreSQLの完全なソースコード自動生成
- **AIテスト生成**: 包括的テストスイートの自動生成
- **AWS自動デプロイ**: 本番環境への完全自動デプロイ・運用

## 技術スタック

- **フロントエンド**: Vue.js 3 + Composition API
- **バックエンド**: Python + FastAPI
- **データベース**: PostgreSQL (Amazon RDS)
- **AI/ML**: OpenAI GPT-4 + Pinecone RAG
- **インフラ**: AWS (Lambda, ECS Fargate, S3, CloudFormation)
- **CI/CD**: GitHub Actions + AWS CodePipeline

## プロジェクト構造

```
.kiro/
├── specs/business-spec-generator/    # プロジェクト仕様書
│   ├── requirements.md               # 要件定義書
│   ├── design.md                    # 設計書
│   └── tasks.md                     # 実装計画
├── steering/                        # AIアシスタント指導ルール
│   ├── language.md                  # 言語設定・コミュニケーション規則
│   ├── product.md                   # プロダクト概要
│   ├── structure.md                 # プロジェクト構造・組織
│   └── tech.md                      # 技術スタック・ビルドシステム
└── hooks/                           # Kiroフック設定
    └── sync-spec-files.kiro.hook    # 仕様書ファイル同期フック
```

## Kiroフック機能

このプロジェクトには、`requirements.md`、`design.md`、`tasks.md`が編集された際に関連ファイルを自動同期するKiroフックが設定されています。

## 開発開始

1. 要件定義: `.kiro/specs/business-spec-generator/requirements.md`を確認
2. 設計確認: `.kiro/specs/business-spec-generator/design.md`を確認  
3. 実装計画: `.kiro/specs/business-spec-generator/tasks.md`を確認
4. 開発ガイドライン: `.kiro/steering/`配下のファイルを確認

## ライセンス

MIT License