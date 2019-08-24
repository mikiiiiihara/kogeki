# 新宿子ども劇場プロジェクトドキュメント

**目次**
- Getting Started
- Form System
- Contents Management System

<br />

## Getting Started

**Git入門ドキュメント**  
https://www.backlog.jp/git-guide/  

**Git CUIをインストール**（必須）  
https://git-scm.com/downloads

**リモートリポジトリが自動的に下記URLにデプロイされる**  
https://shinjuku-kodomo.herokuapp.com/

<br />

### ローカルリポジトリを作成  

1. Terminalを開く。 
2. ローカルリポジトリを設置したいディレクトリへ移動する。（この場合デスクトップ）

  ```
  cd ~/Desktop/
  ```

3. リモートリポジトリからプロジェクトをダウンロードする。  

  ```
  git clone https://github.com/gitoshiaki/shinjuku-kodomo.git
  ```

4. 3で作成されたローカルリポジトリに移動する。今後このディレクトリにいる前提で進める。

  ```
  cd shinjuku-kodomo/
  ```

<br />

### ローカルリポジトリでの更新をリモートに反映させる

1. 更新したファイルをインデックスに登録（この場合、index.htmlとstyle.cssを更新した）

  ```
  git add index.html style.css
  ```
  
2. インデックスに登録されたファイルを新しいバージョンとして記録する

  ```
  git commit -m "index.htmlの一部とstyle.cssの一部を修正"
  ```

3. ローカルリポジトリの記録をリモートリポジトリに反映させる

  ```
  git push origin master
  ```

<br />

## Form System  

**要件**  
- 確認メール自動送信（Google Apps Script のMail APIを使用）
- バリデーション（Javascriptを使用）
- メール内容をAjaxで送信（任意）
- 送信された内容の保存（今回はスプレッドシートへ）

**参考資料**  
- [公式ドキュメント（英語）](https://developers.google.com/apps-script/)
- [初心者向けGAS入門](https://tonari-it.com/google-apps-script-manual/)

<br />

1. Google Appsに[Google Apps Script](https://chrome.google.com/webstore/detail/google-apps-script/eoieeedlomnegifmaghhjnghhmcldobl?hl=ja)を追加
2. Google Driveでプロジェクトフォルダを作成
3. 新規SpreadSheetと新規Google Apps Scriptを作成
4. 各種プログラムを作成（[サンプルコード](https://qiita.com/snowsunny/items/56a85c63598dcfb1b06e#%E3%82%B5%E3%83%B3%E3%83%97%E3%83%AB%E3%82%92%E5%88%A9%E7%94%A8%E3%81%97%E3%81%9F%E4%BD%9C%E3%82%8A%E6%96%B9%E8%AA%AC%E6%98%8E%E3%82%B5%E3%83%B3%E3%83%97%E3%83%AB%E8%A7%A3%E8%AA%AC)）
5. 自動返信メールの内容を作成
6. フォームをHTML/CSSで実装
7. Javascriptでバリデーションを実装
8. 公開、テスト

<br/>

## Contents Management System  

Wordpressを使用するが、カスタマイズする上で、基本的な仕組みなど事前に覚えることも多いため、チュートリアルを通して概観を掴むのが良い。以下のチュートリアルでは最低限テーマを構成するのに必要なファイルのみ用意して、簡単なブログシステムを作成する。

**前提知識**  
- phpの基本構文
- wordpressのテンプレート構造
- wordpressのテンプレートタグ

<br/>

**参考資料**  
- [Progate PHPコース](https://prog-8.com/languages/php)
- [Wordpress Codex (公式ドキュメント)](https://wpdocs.osdn.jp/%E3%83%86%E3%83%BC%E3%83%9E%E3%81%AE%E4%BD%9C%E6%88%90)

<br/>

**チュートリアル**  

1. MAMPをインストールしてWordpressが動作する環境を構築
	1. [公式サイト](https://www.mamp.info/en/)からダウンロードしてインストール
	2. MAMPを起動（MAMP PROではない）
	3. スタートページを開き、phpmyadminのリンクにとぶ
	4. 任意の名前でデータベースを作成する（後に使用するのでメモ）
2. Wordpressをインストール
	1. 公式サイトからzipをダウンロード
	2. Applications/MAMP/htdocs/以下に設置する（必須）
	3. ブラウザから開く（http://localhost/wordpress）
	4. データベースに接続させる設定を行う（先程作成したデータベース名やスタートページに記載されている各種データベース情報を入力する）
3. wp-content/themesディレクトリに自作テーマ用のフォルダを作成（ここではtutorialという名前で作成する）
4. テーマフォルダ内に以下の形式でstyle.cssを作成するとテーマとして認識される  

```css:style.css
/*
Theme Name: tutorial
*/
```

5. index.phpを作成  

```php:index.php
<!DOCTYPE html>
<html lang="ja">
    <head>
        <meta charset="utf-8" />
        <title>チュートリアル</title> <!-- 管理画面から設定するサイトタイトルが表示される -->
        <link rel="stylesheet" href="http://localhost/wp-content/themes/tutorial/style.css" type="text/css" media="screen" /> <!-- 先程作成したスタイルシートをインクルード -->
    </head>
  <body>
    <div class="wrapper">
      <ul class="posts">
        <h2>チュートリアル</h2>
        <li class="post">
          <p class="post_time">2017年1月3日</p>
          <p>WordPress へようこそ。これは三番目の投稿です。</p>
        </li>
        <li class="post">
          <p class="post_time">2017年1月2日</p>
          <p>WordPress へようこそ。これは二番目の投稿です。</p>
        </li>
        <li class="post">
          <p class="post_time">2017年1月1日</p>
          <p>WordPress へようこそ。これは最初の投稿です。</p>
        </li>
      </ul>
    </div>
  </body>
</html>
```

6. index.phpをwordpressのテンプレートタグで作り直す  

```php:index.php

<!DOCTYPE html>
<html <?php language_attributes(); ?>>
    <head>
        <meta charset="<?php bloginfo( 'charset' ); ?>" />
        <title><?php wp_title(); ?></title> <!-- 管理画面から設定するサイトタイトルが表示される -->
        <link rel="stylesheet" href="<?php echo get_stylesheet_uri(); ?>" type="text/css" media="screen" /> <!-- 先程作成したスタイルシートをインクルード -->
        <?php wp_head(); ?> <!-- 各種Wordpressスクリプトをインクルード -->
    </head>
  <body>
    <div class="wrapper">
      <ul class="posts">
        <h2>チュートリアル</h2>
        <?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>
          <li class="post">
            <p class="post_time"><?php the_time('F jS, Y'); ?></p>
            <?php the_content(); ?>
          </li>
        <?php endwhile; else : ?>
          <p><?php _e( '投稿はありません。' ); ?></p>
        <?php endif; ?>
      </ul>
    </div>
    <?php wp_footer(); ?> <!-- 各種Wordpressスクリプトをインクルード -->
  </body>
</html>
```

7. 管理画面から2.3個投稿をしてみる  
8. スタイルをいじって綺麗にしてみる

```css:style.css
/*
Theme Name: tutorial
*/


html, body {
    display: block;
    width: 100%;
    height: 100%;
    background: #d3d3d31f;
    margin: 0;
    padding: 0;
}

.posts {
    width: 500px;
    margin: 0 auto;
    padding-top: 3rem;
}

.post {
    list-style: none;
    box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
    padding: 1rem 2rem .5rem;
    margin-bottom: 1rem;
    background: white;
}

.post_time {
    margin: 0;
    color: darkgrey;
    font-size: 0.6rem;
}

p {
    margin: .5rem 0 1rem;
}
```
**投稿内容の表示**
今のままでは投稿内容は本文、投稿日時のみしか表示されていない。タイトル、タグ、カスタムフィールド（日時、場所などの詳細）なども表示させるにはいくつかのコマンドが必要。
1. カスタムフィールドの表示
```
<?php echo get_post_meta(get_the_ID(),"変数名",true); ?>
```

※get~関数は値の取得のみ行うコマンドゆえ、echoする必要あり。
※"文字列" と 数値　に注意（文字列はダブルクォーテーションで囲む）
2. タグの表示
```
<?php the_tags(); ?>
```

※theで始まる関数には、echoが備わっている場合が多い。
3. タイトルの表示
```
<?php the_title(); ?>
```

