# 第6回 解答

## 演習

- STEP 1 のツールの名前：
 [glossary_search_glossary]

- STEP 2 の [tool call]：
 [tool call]   glossary_search_glossary({'query': '3レベル'})

- STEP 3 の [tool call]：
 [tool call]   fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
 [tool call]   glossary_search_glossary({'query': 'MCP'})

- STEP 4 の [tool call]：
 [tool call]   aws_aws___search_documentation({'search_phrase': 'Amazon S3 バージョニング 概要', 'topics': ['general']})
 [tool call]   aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Using versioning Amazon S3 overview'})

- 気づき・疑問：
 app.mcp_agentで必要なものだけをサーバー起動する作りにはなっていないと感じた。

## 宿題

- 取り組んだレベル：
 基礎 

- やったこと：
 「get_lecture_summary」というtoolを自前MCPサーバーに追加

- 結果：
 「第二回は何を学びますか？」という質問を「uv run python -m app.mcp_agent」で実行。
 結果、正常にtoolが呼ばれて回答生成された。
 
 生成された回答

 ---
 第2回では、**「ファインチューニングとLoRA」**について学びます。
 ### 主な内容
 - **事前学習とファインチューニングの違い**: ファインチューニングが向く場面・向かない場面を理解します。
 - **SFT（教師あり微調整）**: 入力と望ましい出力のペアでモデルを追加学習させる手法を学びます。
 - **PEFTとLoRA**: 全パラメータを更新せず、小さな低ランク行列だけを効率的に学習させる仕組み（LoRA） の考え方を理解します。
 - **演習**: Google Colab上で小さなモデル（Qwen2.5-0.5Bなど）を架空のFAQデータでLoRA学習させ、学習前後での出力の変化を体験します。
 ---
 関連する回：第2回
 --- trace ---
 [tool call]   glossary_get_lecture_summary({'lecture': 2})
 [tool return] glossary_get_lecture_summary -> # 第2回 ファインチューニングとLoRA

- 気づき・疑問：
 エージェントの内容を大きく変えずにtool登録するだけでエージェントのできることが広がることがわかった。
 エージェントに余計な思考をさせずに的確な回答ができるのは有用だと感じた。