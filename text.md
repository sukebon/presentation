# 大丸白衣のアプリケーションはどのように作られている？

## 今までに作成したアプリ一覧
- マイユニポータル
- 社内ポータルサイト
- メーカー在庫
- 生地アプリ
- 加工指示書管理アプリ
- 学販アプリ
- TSUCHUYA アプリ
etc.

## アプリを作るための基本的な言語
1. HTML
2. CSS
3. javascript

## HTMLとは
HTML（HyperText Markup Language）とは、Webページを作成するための基本的な言語です。

  複雑な計算といった処理は行わず、ページの見出し、段落、画像などの要素を配置して、Webページの構造　を作るものになるので、プログラミング言語ではなく「マークアップ言語」にあたります。

  ※マークアップ言語とは、文章に構造や表現方法を与えるための言語。文章に「飾り付け」や「指示」をするための「タグ」と呼ばれる記号を使って、文章の意味や見た目をコンピュータに伝えるためのものです。

## HTMLの役割
  ### Webページの構造を定義する
  見出し、文章、画像、動画などのコンテンツの配置して、どの要素がどこにあるのかを指定。例えば、\<h1>タグで見出し、\<p>タグで段落、\<img>タグで画像をそれぞれ表したり、
  \<header>、\<nav>、\<main>、\<footer>などのセクション要素を使って、ページを分かりやすく構造化します。
 
  ### ブラウザへの指示
  構造化したHTMLをグーグルクロームやマイクロソフトのEdgeなどのブラウザに「この部分は見出しです」「この部分は画像です」といった指示を与えることによって、ブラウザで表示することができる。

  この二つがHTMLの大きな役割です。

## HTML 記入例
```
<!DOCTYPE html>
  <html>
    <head>
      <title>社内ポータルサイト</title>
    </head>
    <body>
      <header>
      <nav>
        <ul>
          <li>生地アプリ</li>
          <li>WEB在庫</li>
        </ul>
      </nav>
      </header>
      <main>
        <h1>社内ポータル</h1>
        <p>これは、HTMLで作成された簡単な段落です。</p>
        <img src="image.jpg" alt="画像">
      </main>
    </body>
  </html>
```
このコードでは
  - \<h1>タグで「社内ポータル」という見出しを作成
  - \<p>タグで段落を作成
  - \<img>タグで画像を表示
といった指示が与えられています。

## まとめ
- HTMLはWEB作成の基本的な言語
- 見出しや画像などの構造を定義
- ブラウザに見出しや画像などの指示を与える

　HTMLは、Webページを作成するための基本的な言語で、Webページの構造を作るためには必須になります。
　比較的簡単で覚えやすい言語で、使うだけであれば半日もあれば十分。

## CSSとは
CSS (Cascading Style Sheets) とは、Webページの見た目をデザインするための言語。

  HTML で作成されたページの構造に、CSS を加えることで、文字の色や大きさ、背景、レイアウトなど、様々なデザインを施すことができます。

## CSSの役割
### Webページの見た目をデザインする
  HTML で作成されたページの要素（見出し、段落、画像など）に、CSS でスタイルを適用します。
  - フォント: 文字の種類、サイズ、色などを変更できます。
  - 色: 背景色、文字色、線の色などを設定できます。
  - レイアウト: 要素の配置、サイズ、間隔などを調整できます。
  - 装飾: 影、丸角、グラデーションなどを加えることができます。

### HTMLとデザインを分離する
  HTMLからスタイルを分けてを記述することができるので、コードの整理がしやすくなる。
  またデザイン変更の際、HTMLを修正する必要がなく、CSSファイルのみを編集すれば済む。

### レスポンシブデザイン
  異なるデバイス（パソコン、スマートフォン、タブレットなど）に合わせて、レイアウトを自動的に調整することができます。

## CSS記入例
```
  h1 {
    color: blue;
    font-size: 32px;
  }
```
※このコードは、全ての\<h1>タグの文字色を青色に、フォントサイズを32pxに変更します。

## まとめ
CSSは、HTMLで記述された文書構造にスタイルを付与し、表現豊かなWebページを実現するスタイルシート言語です。 セレクタ、プロパティ、値といった要素を組み合わせることで、高度なデザインやレイアウトを構築できます。


## Javascriptとは
  JavaScript（ジャバスクリプト）は、Webページに動きやインタラクティブな機能を追加するためのプログラミング言語。静的なHTMLだけでは表現できない、動的な要素をウェブサイトに実装することができる。

  ※インタラクティブ
  　「相互に作用し合う」という意味で、ボタンをクリックしたらポップアップを表示したり、
    画像がスライドしたり、検索結果をリアルタイムで表示するなど。

## Javascriptの役割

### 動的なWebページの作成
　　ボタンをクリックしたときの反応、マウスを合わせたときの変化など、ユーザーの操作に対して様々な動き　　例）ドロップダウンメニューやタブ切り替えなど。
 　 入力フォームで内容が正しいか、必要な情報がすべて入力されているかのバリデーションチェック。

### WEBサーバーの構築
　　サーバー側でのアプリケーションのロジックからデータベースとの連携、ファイルの読み書き、外部サービ　　スとの連携など、様々なデータ処理を行うことができます。

```
import { auth } from "@/auth";
import { db } from "@/lib/firebase/server";
import {
  CreateMeasureStudent,
  CreateMeasureStudentSchema,
  validateWithZodSchema,
} from "@/utils/schemas";
import { School } from "@/utils/school.interface";
import { FieldValue } from "firebase-admin/firestore";

export async function createMeasureStudent(
  data: CreateMeasureStudent,
  { schoolId, studentId }: { schoolId: string; studentId: string }
): Promise<{ status: string; message: string }> {
  const session = await auth();

  try {
    const result = validateWithZodSchema(CreateMeasureStudentSchema, data);

    if (!session) {
      throw new Error("認証に失敗しました");
    }

    const snapshot = db
      .collection("schools")
      .doc(schoolId)
      .collection("students")
      .doc(studentId);

    const school = (
      await db.collection("schools").doc(schoolId).get()
    ).data() as School;
    const shippingFee = school.isShipping ? school.shippingFee : 0;

    const totalAmount = result.products.reduce((sum, product) => {
      const productPrice = product.price * product.quantity;
      const inseamPrice = product.inseam.price * product.quantity;
      sum = sum + productPrice + inseamPrice;
      return sum;
    }, 0);

    await snapshot.update({
      products: result.products,
      finishedAt: FieldValue.serverTimestamp(),
      totalAmount: totalAmount + shippingFee,
    });

    return {
      status: "success",
      message: "登録に成功しました",
    };
  } catch (e: unknown) {
    return {
      status: "error",
      message: e instanceof Error ? e.message : "登録に失敗しました",
    };
  }
}
```　　

## JavascriptのWEB以外の活用

  - ゲーム開発
  - 機械学習
  - Iot
  etc.

### まとめ
　　JavaScriptは、Web開発において欠かせない存在であり、その他の分野でも成長していて、その重要性はま　　すます高まっていく。JavaScriptを使うことによって、より動的で魅力的なWebサイトやWebアプリケーシ　　ョンを開発することができる。

## 総括
　　HTML、CSS、Javascriptを学ぶことによって、動的なWEBサイトを構築することが可能ですが、
    正直、この3つを学んだだけではWEBアプリケーションを作ることは難しい。
    その他に覚えることはたくさんあります。

    - データベース　（firestore, MySql, postgreSQL）
    - 他のプログラミング言語 (Typescript)
    - ストレージ　(cloud storage)
    - 認証サービス(firebase auth)
    - WEBフレームワーク　(react, nextjs,)
    - css フレームワーク　(tailwind css, shadcn ui, chakura ui, mantain ui)
    - インフラ , ホスティングサービス(aws, gcp ,vercel )
    - バージョン管理　(git, github)
    - 決済サービス (stripe)
    - コンテナ (Docker)
    - モジュールバンドラー(webpack, vite, Turbopack )
    - その他　複数のライブラリ

    ただし、HTML、CSS、Javascriptの3つを覚えることによって、アプリ開発のスタート地点には立てるので、興味があればぜひ学んでみてください。
　