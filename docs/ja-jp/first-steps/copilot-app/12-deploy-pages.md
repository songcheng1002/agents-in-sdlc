---
title: "レッスン 12 - GitHub Pages でサイトをデプロイする"
description: "GitHub Copilot app を使って Pages ワークフローを構成し、その pull request をレビューして、公開された Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Space Quiz を GitHub Pages にデプロイして、誰でもアクセスできるようにします。Copilot はワークフローの準備とデプロイの案内を行えますが、変更をレビューし、サイトが公開されたことを確認するのはユーザーの責任です。

このレッスンでは、次の操作を行います。

- Copilot に GitHub Pages のデプロイ構成を依頼します。
- マージする前にワークフローと pull request をレビューします。
- デプロイを進め、公開されたサイトを確認します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、まだ簡単に試す方法がありません。単一ファイルのサイトを GitHub Pages で公開すると、サーバーやランタイム依存関係を追加せずに、公開 URL からアクセスできるようになります。

## Copilot にデプロイの準備を依頼する

> [!WARNING]
> pull request を作成すると、コードがコミットおよびプッシュされることがあります。このプロンプトを送る前に、承認設定と送信先リポジトリを確認してください。**Approve all** が選択されている場合、別途確認を求められるとは限りません。

`space-quiz` の Copilot app セッションで、次のプロンプトを送信します。

```plaintext
このリポジトリの GitHub Pages デプロイを準備してください。変更が既定のブランチに反映された後、必要に応じて Web サイトをビルドし、GitHub Pages にデプロイする GitHub Actions ワークフローを作成してください。README がまだない場合は、アプリの説明とローカルでの実行方法を記載した README を追加してください。これらの変更で pull request を作成し、そのリンクと必要な Pages の設定または権限を報告してください。マージ、自動マージの有効化、Pages 設定の変更、デプロイは行わないでください。停止して、レビューを待ってください。
```

## ワークフローと pull request をレビューする

1. README がまだない場合に限り、追加されていることを確認します。
2. ワークフローのビルドおよびデプロイ手順、トリガー、権限を含めて、pull request の変更をレビューします。
3. ワークフローが、未マージの pull request ではなく既定のブランチからデプロイすることを確認します。
4. 必要な修正を依頼して、更新された diff をレビューします。マージを許可する前に、必須の pull request チェックが成功するまで待ちます。

## マージとデプロイを許可する

> [!WARNING]
> 次のプロンプトは、レビュー済みの pull request のマージ、リポジトリの Pages 設定の変更、サイトの公開をエージェントに許可します。レビューを終え、リポジトリと pull request を確認した後にのみ送信してください。承認設定によっては、別途確認されずにこれらの操作が実行されることがあります。

`<PR_NUMBER>` をレビューした pull request の番号に置き換えて、このプロンプトを別途送信します。

```plaintext
このリポジトリの pull request <PR_NUMBER> をレビューし、マージとデプロイを許可します。GitHub Actions を使って GitHub Pages を有効にし、必須チェックの成功後に限りその pull request をマージして、デプロイが成功するまで監視してください。公開された Web サイトの最終 URL を報告してください。Pages の有効化やマージに必要な権限がない場合は、何を承認または実行する必要があるかを正確に説明してください。サイトが公開されるまで、成功したと報告しないでください。
```

![3 段階の図: マージ済みの space-quiz pull request、Build website・Upload artifact・Deploy to Pages の各ステップが成功した GitHub Actions Deploy website 実行、yourname.github.io/space-quiz/ で公開された Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## デプロイを確認する

1. GitHub Actions のデプロイ実行が成功するまで確認します。
2. 報告された URL を開き、Space Quiz が読み込まれることを確認します。

エージェントが Pages の有効化や pull request のマージを実行できない場合は、提示された具体的な手順に従います。デプロイが成功し、公開サイトが読み込まれるまで、タスクを完了したと見なさないでください。

## まとめと次のステップ

Space Quiz が公開サイトとして利用可能になり、エージェントの報告に頼らずデプロイを確認できました。続けて[レッスン 13: レビューと次のステップ][next-lesson]に進みます。

[next-lesson]: ../13-review/
