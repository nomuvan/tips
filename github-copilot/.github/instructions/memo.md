
* 参考
    * https://qiita.com/masakinihirota/items/247bee4bd66ace86e1da

```
.github/
├── copilot-instructions.md (全体の指示書)
├── memory.md (メモリーファイル)
├── .copilot-commit-message-instructions.md (以下、個別の指示書)
├── .copilot-review-instructions.md
├── .copilot-test-instructions.md
├── .copilot-codeGeneration-instructions.md
└── prompts/ (プロンプトファイル用のフォルダ)
├── task-list.prompt.md (タスクリストファイル)
├── completes/ (実装が終わったプロンプトファイルを入れるフォルダ)
├── 20250401-001-code-style-doc.prompt.md (以下、プロンプトファイル)
├── 20250401-003-comment-rule-doc.prompt.md
├── 20250401-004-component-style-doc.prompt.md
├── 20250401-005-sample-doc.prompt.md
├── 20250401-002-test-rule-doc.prompt.md
└── 20250401-006-user-authentication-feat.prompt.md

```

* Github CopilotでのMemory-Bankの実装
  * https://zenn.dev/bluetang/articles/memorybank_in_gh_copilot

* GitHub Copilot の指示書が複数ファイル対応に！ルールを用途別に整理できる新機能
  * https://zenn.dev/m10maeda/articles/copilot-multi-instruction-files