# GPU Unite 2025 参加所感

## 聴講メモ抜粋　（AI エージェント社会実装への挑戦）

- 講演者:
  Sakana AI 株式会社 Applied Research Engineer 太田 さん
- 概要
  AI エージェントの社会実装に向けた取り組みについて[AI Scientist](https://sakana.ai/ai-scientist-jp/)を題材に解説
  - Sakana AI の R&D 説明
    - Small Model
      TAID(Temporally Adaptive Interpolated Distillation)
    - Efficient Model
      - EMM(Evolutionary Model Merge)/CycleQD
      - Transformer^2
    - Reasoning Model
      - LLM-MCTS(Monte Carlo Tree Search)
    - Agentic Capabilities
      - ADAS\*1(Automated Design of Agentic Systems)
      - LLM^2(DiscoPop)(Discovered Preference Optimization)
  - Agent Used as Application
    - WORKFLOW AUTOMATION
      AI Scientist
  - SIMULATION
    Agent Based Modeling
  - VERTICALS
    AI CUDA Engineer
  - Sakana AI が掲げる AI エージェントの定義
    AI エージェントは、意思決定を繰り返して目標を達成する。（Thought × Action ⇔ Environment）
    - 具体例：deep research, computer use, coding agent 等
  - ① 業務のエンドツーエンドの自動化
    情報収集～抽出～分析～報告
  - ② 要素技術の応用（アイデア生成、実行、レポート生成）
    - 例：論文調査、要約、レポート作成
- 実装の課題
  Search⇒Ideation⇒Execution⇒Report⇒Review の内、Ideation のフェーズが最も実装するのが難しい。

- キーワード

# beyond Transformer # 進化計算 # MCTS # RL # プロンプトエンジニアリング # コンテキストエンジニアリング

# Auto-Eval # 自己進化 # Function Calling # LangChain # MCP Server

---

### 説明可能な SLM（eXplainableSLM：XSLM）の可能性と未来の展望

#### 予測モデルの種類

- ルールベース
  - 学習データ ⇒ ルール構築 ⇒ ルール ⇒ ルール適用 ⇒ 予測結果
- データ駆動型予測モデル
  - 学習データ ⇒ 特徴量エンジニアリング ⇒ 特徴量 ⇒ML 学習モデルの構築 ⇒ 予測結果
- プロンプトベース予測モデル
  - 学習データ ⇒ プロンプトエンジニアリング（LLM）⇒ 予測結果

#### プロンプトのフレームワーク

- 役割
- タスク指示
- データテーブル
- データ定義
- コンテキスト
- 指示
  ⇒ これらすべての要素を入れればよいというわけではない

- 論文
  [From classification to clinical insights: Towards analyzing and reasoning about mobile and behavioral healthdatawith large language models.](https://arxiv.org/pdf/2311.13063)

- モデル規模と計算に必要な計算資源
  |モデルタイプ|パラメータ数|例|必要な GPU メモリ量 | 推奨 GPU 型番(Nvidia) |
  |-----------|-----------|--|-----------------|------------|
  |SLM|100M~1B|Gemma-2B,Phi-2|6~16GB/学習時：24GB|RTX 3060(12GB),RTX4070(12GB),RTX PRO 4000(24GB)|
  |Middle LM|1B~20B|Mistral-7B,LLaMA-13B,gpt-oss-20b||24~48GB/学習時：80GB 以上|RTX 3090(24GB),RTX4090(24GB),RTX PRO 5000(48GB),H100(80GB),RTX PRO 6000(96GB)|
  |LLM|65B~数百 B~1T 超|GPT-4,Claude Opus, Gemini, 1.5Pro, gpt-oss-120b|80GB 以上（分散必須）/学習不可（単体 GPU)|A100, H100(80GB),RTX PRO 6000(96GB)(複数台前提)|

- SLM 開発元の特徴
  |モデル群|スケーリング|特徴 |
  |-----------|-----------|--|-----------------|
  |Gemma(Google)|1B~27B|小規模～中規模モデルで、省リソースでも高性能を狙う|
  |Phi(MS)|3.8B~42B|小規模～中規模モデルで、省リソースでも高性能を狙う|
  |Mistral|7B~50B|MoE(Mixture of Experts)などを活用し、パラメータの有効活用と推論効率に特化|
  |Qwen(Alibaba)|0.6B~235B|MoE(Mixture of Experts)などを活用し、パラメータの有効活用と推論効率に特化|
  |LLaMA(Meta)|7B~2000B|数百 B~2T パラメータ級のスケーリングで、SOTA を目指すスペック指向|
  |DeepSeek|7B~685B 以上|数百 B~2T パラメータ級のスケーリングで、SOTA を目指すスペック指向|
