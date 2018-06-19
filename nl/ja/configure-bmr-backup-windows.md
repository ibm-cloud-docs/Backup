---

copyright:
  years: 1994, 2018
lastupdated: "2018-05-31"

---
{:new_window: target="_blank"}

# Windows での BMR バックアップ・ジョブの構成

## 前提条件

BMR バックアップを実行するには、BMR プラグインを購入する必要があります。BMR は Windows ベアメタル・サーバー用のみがあります。VSI には BMR オプションはありません。

## WebCC の起動
**注**: WebCC を開始するには、{{site.data.keyword.BluSoftlayer_full}} プライベート・ネットワークに接続している必要があります。
1. [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}にログインし、メインメニューから**「ストレージ」** > **「バックアップ」**をクリックして EVault バックアップ・サービスのサーバーを表示します。 
2. バックアップ対象のファイルがあるサーバーを選択します。右向きの展開矢印をクリックし、WebCC リンクを表示します。
4. **「WebCC ログイン」**をクリックし、ブラウザーで WebCC クライアントを開始します。
  **注**: WebCC が開始されない場合は、VPN 接続に問題がある可能性があります。また、送信しようとしているフォームがセキュアではないというメッセージが表示されることもあります。このことは予期されることであるため、フォームを送信して続行します。
  
## BMR バックアップ・ジョブの構成

1. 左のナビゲーション・ペインで、**「すべてのエージェント」**をクリックして、現在の EVault エージェントを表示します。
2. **「これは構成対象の新しいエージェントです (This is a new Agent I would like to configure)」**をクリックします。
3. 構成または作成するジョブのジョブ名とジョブ記述を入力します。
4. **「バックアップ・ソース・タイプ (Backup Source Type)」**で、バックアップ対象とするファイル・システム・タイプをプルダウン・メニューから選択し、次に、**「次へ」**をクリックします。
5. **「ジョブ・タイプの選択 (Job Type Selection)」**メニューが表示されます。**「ベアメタルのリストア (Bare Metal Restore)」**の隣のボックスをチェックし、**「次へ」**をクリックして続行します。
6. 確認ウィンドウでは**「はい」**をクリックします。
7. 画面のバックアップ・セットに、新しいジョブが表示されるようになります。**「次へ」**をクリックします。
8. 画面に、暗号化オプションとバックアップの拡張オプションが表示されます。通常、これらは必要ありません。**「次へ」**をクリックして、**「スケジュールの作成 (Create a schedule)」**画面に進みます。   
9. **「スケジュールの作成 (Create a schedule)」**ページで、**「追加」**をクリックして時刻ベースのバックアップ・ジョブをスケジュールに入れるか、**「次へ」**をクリックして手動ジョブを作成します。
  - 手動ジョブを作成する場合は、新しいジョブの実行に進みます。
  - 時刻ベースのジョブをスケジュールに入れる場合は、バックアップを実行する曜日と時刻を選択します。
  - 保存スキームを選択します。保存スキームについて詳しくは、[ここ](evault-backup-faq.html#how-do-the-retention-schemes-work-)を参照してください。
  - バックアップ・スケジュールを構成した後、**「OK」**をクリックして保存します。スケジュールに入れたジョブが、スケジュール済みのジョブのリストに追加されます。 
10. バックアップ・ジョブのボールトを選択し、**「変更の保存」**をクリックします。


## BMR バックアップ・ジョブの実行
  - 時刻ベースのバックアップ・ジョブをスケジュールした場合は、この先の手順はありません。ジョブはスケジュールに従って自動的に実行されます。
  - 手動ジョブを (時刻ベースのスケジュールなしで) セットアップした場合は、ジョブ・リストでその行を選択し、**「バックアップの実行 (Run Backup)」**をクリックすることによって実行できます。<br/> 時刻ベースのジョブについては、**保存スキーム**と**バックアップの拡張オプション**を選択できます。構成の選択を完了した後、**「バックアップの開始 (Start Backup)」**をクリックして、ジョブを開始します。