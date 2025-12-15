# 言語設定・コミュニケーション規則

## 基本言語設定

**すべてのコミュニケーションは日本語で行う**

- チャット・会話：日本語
- コード内コメント：日本語
- 変数名・関数名：英語（技術的慣例に従う）
- ドキュメント・仕様書：日本語
- エラーメッセージ：日本語
- ログ出力：日本語

## コーディング規則

### コメント・ドキュメント
```python
# 日本語でコメントを記述
def generate_specification(requirements: str) -> dict:
    """
    業務要件から仕様書を自動生成する
    
    Args:
        requirements: 日本語で記述された業務要件
        
    Returns:
        生成された仕様書データ
    """
    pass
```

### エラーハンドリング
```python
try:
    result = process_requirements(requirements)
except ValidationError as e:
    logger.error(f"要件の検証に失敗しました: {e}")
    raise BusinessException("業務要件の形式が正しくありません")
```

### API レスポンス
```json
{
    "status": "success",
    "message": "仕様書の生成が完了しました",
    "data": {
        "specification_id": "spec_001",
        "title": "受注管理システム仕様書"
    }
}
```

## ユーザーインターフェース

### Vue.js コンポーネント
- ラベル・ボタンテキスト：日本語
- バリデーションメッセージ：日本語
- 進捗表示・ステータス：日本語

### 例：
```vue
<template>
  <div>
    <h1>業務要件入力</h1>
    <textarea 
      v-model="requirements" 
      placeholder="受注から請求までの業務フローを日本語で記述してください"
    />
    <button @click="submitRequirements">仕様書生成開始</button>
  </div>
</template>
```

## AI プロンプト・応答

- AIへの指示：日本語
- AI応答の期待言語：日本語
- 生成される成果物：日本語（コード除く）

## 技術用語の扱い

### 日本語化する用語
- Requirements → 要件
- Specification → 仕様書
- Design → 設計書
- Implementation → 実装
- Testing → テスト
- Deployment → デプロイ・配置
- Monitoring → 監視

### 英語のまま使用する用語
- API, REST, JSON
- Vue.js, FastAPI, PostgreSQL
- AWS, Lambda, S3
- Git, GitHub, CI/CD

## 文書作成規則

- 見出し：日本語
- 本文：日本語（技術仕様は英語併記可）
- 図表キャプション：日本語
- ファイル名：英語（システム互換性のため）