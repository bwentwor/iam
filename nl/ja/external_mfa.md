---

copyright:

  years: 2018, 2019

lastupdated: "2019-01-30"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# ユーザー用の外部認証 MFA の注文
{: #external}

適切なアクセス権限を持つ管理者は、外部認証を注文し、ユーザーのログインに対して多要素認証 (MFA) オプションを有効にすることができます。 外部認証オプションの料金は月次で課金されます。 ID ベースの MFA とは違って、このタイプの多要素認証 (MFA) は設定が有効にされているアカウントでのみ必要になります。 詳しくは、『[多要素認証のタイプ](/docs/iam?topic=iam-types#types)』を参照してください。
{:shortdesc}

## 外部認証の注文
{: #ordering}

以下のアクセス権限を持っている場合、ユーザー用に外部認証を注文できます。

* ユーザー管理サービスに対するエディター以上の役割
* 当該ユーザーのクラシック・インフラストラクチャー階層内で上位にいて、かつ、「ユーザーの管理」クラシック・インフラストラクチャー許可を割り当てられている

外部認証を注文するには、以下の手順を実行します。

1. メニュー・バーから、**「管理」** &gt; **「アクセス (IAM)」**をクリックして、**「ユーザー」**を選択します。
2. リストからユーザーを選択します。
3. **「ユーザーの詳細」**ページの「ユーザー・ログインの管理」セクションで、**「外部認証の注文」**を選択します。
4. **「Symantec ID 保護」**または**「電話ベースの ID 保護」**を選択します。
    * Symantec 認証の場合、注文プロセスを続行するためには、ユーザーが [Symantec VIP](https://vip.symantec.com/){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg) アプリをダウンロードし、資格情報 ID を取得する必要があります。
    * 電話ベースの認証の場合、注文を続行できますが、ユーザーがユーザー自身の[構成のセットアップ](/docs/account?topic=account-third-party-MFA#third-party-MFA)を行った後でないと、このオプションを有効にすることはできません。
5. 注文する前に、選択に基づいて、プロンプトに従って価格と使用条件を検討します。
6. **「注文」**をクリックして選択を確定します。

Symantec 認証の場合、注文後に「ユーザーの詳細」ページからユーザーに対してこのオプションをオンにすることができます。 電話ベースの認証の場合、注文が終わって、ユーザーによって構成された後に、「ユーザーの詳細」ページからユーザーに対してこのオプションをオンにすることができます。

## 外部認証オプションの無効化
{: #disable}

ユーザーに対する Symantec または電話ベースの MFA をいつでも無効化できます。

1. メニュー・バーから、**「管理」** &gt; **「アクセス (IAM)」**をクリックして、**「ユーザー」**を選択します。
2. リストからユーザーを選択します。
3. **「ユーザーの詳細」**ページで、**「Symantec 認証」**オプションまたは**「電話ベースの認証」**オプションをオフに設定します。

## 外部認証オプションの取り消し
{: #cancel}

適切なアクセス権限を持っている場合、いつでも外部認証の注文を取り消すことができます。 返金なしで即時に取り消すことも、注文してから 1 年の時点で取り消すこともできます。

外部認証の注文を取り消すには、アカウント所有者であるか、以下のすべてのアクセス権限を持っている必要があります。

* 「ユーザーの管理」クラシック・インフラストラクチャー許可
* 「サービスの取り消し」クラシック・インフラストラクチャー許可
* サポート・センターのアカウント管理サービスの管理者、または、[マイグレーションされた許可アクセス・グループ](/docs/iam?topic=iam-predefined#predefined)内では使用可能ではない、マイグレーションされた、チケットの表示、編集、および追加の各クラシック・インフラストラクチャー許可。

外部認証の注文を取り消すには、以下の手順を実行します。

1. メニュー・バーから、**「管理」** &gt; **「アクセス (IAM)」**をクリックして、「ユーザー」を選択します。
2. リストからユーザーを選択します。
3. **「ユーザーの詳細」**ページで、どちらを注文したのかに応じて**「Symantec 認証」**行または**「電話ベースの認証」**行で**「削除」** ![削除アイコン](../icons/icon_trash.svg) をクリックします。
4. 削除するタイミングを選択します。
5. **「削除」**をクリックします。