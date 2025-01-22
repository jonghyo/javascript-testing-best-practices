<img src="/assets/jtbp-header-blue.png" width="1920px"/>

<br/>

# 👇 このガイドを読むとテストスキルが向上する理由

<br/>

## 📗 非常にわかりやすく、網羅的な46以上のベストプラクティス

これは JavaScript & Node.js の信頼性のためのA-Zなガイドです。  
本ガイドは、沢山の素晴らしいブログ記事、書籍などの世にある様々なツールから内容をキュレーションし、要約して作られています。

## 🚢 基礎なんて10000マイル以上置いてきぼりにするアドバンスドな内容

基礎はもちろんのこと、多くのアドバンスドなトピック（本番環境でのテスト・ミューテーションテスト・property-basedテスト・戦略的でプロフェッショナルなツールについてなど）まで学べる旅に出ましょう！
このガイドを隅々まで読みこめば、あなたのテストスキルは並のレベルを大きく凌駕することでしょう。

## 🌐 フロントエンド、バックエンド、CI、その他なんでもフルスタックに

まずは、どんなアプリケーションにとっても根幹となる普遍的なテストの習慣を理解するところから始めましょう。  
そして、フロントエンド/UI、バックエンド、CI、あるいはなんならその全てでも、自分の興味のある分野を探求していきましょう。

<br/>

### 著者: Yoni Goldberg について

- JavaScript & Node.js のコンサルタントです
- 📗 [Testing Node.js & JavaScript From A To Z](https://www.testjavascript.com) - [10時間以上の動画](https://www.testjavascript.com)、14種類のテスト、40以上のベストプラクティスを取り扱った、分かりやすいオンラインコースです
- [Twitterはこちら](https://twitter.com/goldbergyoni/)

<br/>

### 翻訳 - 自分の言語で読んでください

- 🇨🇳[中国語](readme-zh-CN.md) - [Yves yao](https://github.com/yvesyao)さんの貢献
- 🇰🇷[韓国語](readme.kr.md) - [Rain Byun](https://github.com/ragubyun)さんの貢献
- 🇵🇱[ポーランド語](readme-pl.md) - [Michal Biesiada](https://github.com/mbiesiad)さんの貢献
- 🇪🇸[スペイン語](readme-es.md) - [Miguel G. Sanguino](https://github.com/sanguino)さんの貢献
- 🇧🇷[ポルトガル語](readme-pt-br.md) - [Iago Angelim Costa Cavalcante](https://github.com/iagocavalcante)さん、[Douglas Mariano Valero](https://github.com/DouglasMV)さん、[koooge](https://github.com/koooge)さんの貢献

- 自分の言語に翻訳したいですか? issueをぜひ立ててください 💜

<br/><br/>

## `目次`

#### [`Section 0: 黄金律`](#section-0️⃣-the-golden-rule)

他をインスパイアするたったひとつのアドバイス（1発の特別な弾丸）

#### [`Section 1: テスト解剖図`](#section-1-the-test-anatomy-1)

綺麗なテストを構築するための土台 (12発の弾丸)

#### [`Section 2: バックエンド`](#section-2️⃣-backend-testing)

バックエンドおよびマイクロサービスのテストを効果的に書く（8発の弾丸）

#### [`Section 3: フロントエンド`](#section-3️⃣-frontend-testing)

コンポーネントテストやE2Eテストなどを含むWeb UIのテストを書く（11発の弾丸）

#### [`Section 4: テストの有効性を計測する`](#section-4️⃣-measuring-test-effectiveness)

監視員を監視する - テスト品質を測る (4発の弾丸)

#### [`Section 5: 継続的インテグレーション`](#section-5️⃣-ci-and-other-quality-measures)

JSの世界におけるCIのガイドライン (9発の弾丸)

<br/><br/>

# Section 0️⃣: 黄金律

<br/>

## ⚪️ 0 黄金律: リーンなテストのためのデザイン

:white_check_mark: **Do:**
テストコードは本番コードとは違います - 非常にシンプルで、短く、抽象さを排除し、フラットで、リーンで、書きたくなるようなものにしましょう。誰でも一目見て意図がすぐに伝わるようなテストを心がけましょう。  

私たちの頭はいつもメインの本番コードのことでいっぱいなので、余計にややこしいものを追加するような「脳内のスペース」なんてありません。もしも追加で難しいコードを我々のちっぽけな脳に押し込もうなんてしようものなら、チームを遅滞させますし、それはそもそもテストを書きたかった理由と逆行していて本末転倒です。実際のところ、これが多くのチームがテストを諦めてしまう理由です。

テストとは、ある別のことのための機会だと捉えましょう。それは、一緒に協業して楽しいような、友好的で笑顔に満ち溢れたアシスタントであり、小さな投資で大きなリターンをもたらすものなのです。  
科学的に人間には2つの脳のシステムがあります: システム1は、たとえばガラガラの道路を車を運転するような努力のいらない活動のために使われ、システム2は、たとえば数式を解くような複雑で意識的な操作のために使われます。  
システム1で処理できるようなテストをデザインしましょう。テストコードと向き合う時には、まるでHTML文書を編集するかのような気楽さを感じられるべきであって、2X(17 × 24)という数式を解く時のようであってはいけません。

その達成のためには、テクニック、ツール、費用対効果が高いテスト対象を選択的に取捨選択するとよいでしょう。必要なものだけをテストし、敏捷性を保つことを心がけましょう。時には、信頼性を敏捷性と簡潔さと天秤にかけ、いくつかのテストを捨てることも有効です。

![alt text](/assets/headspace.png "We have no head room for additional complexity")

ここから先のアドバイスのほとんどは、この原則から派生したものです。

### 準備はいいですか?

<br/><br/>

# Section 1: テスト解剖図

<br/>

## ⚪ ️ 1.1 テスト名には3つの要点を含める

:white_check_mark: **こうしましょう:** テストレポートとは、現在のアプリケーションの変更が要件を満たせているかどうかを伝えるものでなければなりません。その要件とはコードベースに詳しいとは限らない人たちにとってのものであり、それは、テスターやデプロイをするDevOpsエンジニアや2年後のあなたです。
そのためには、テスト自体が要件レベルで話し、3つの要点を含んでいるとよいでしょう。

(1) 何がテストされているのか？ たとえば、ProductsService.addNewProduct というメソッド

(2) どのような状況とシナリオを想定しているか？　たとえば、 priceがメソッドに渡されなかった時

(3) どんなテスト結果を予期しているか？ たとえば、 新しいproductが承認されないこと

<br/>

❌ **さもなくば:** デプロイが失敗し、"Add product"という名前のテストが落ちています。これで何が不具合を起こしているか正確に分かると言えますか？ 

<br/>

**👇 Note:** それぞれの弾丸にはコード例がついていて、時にはイラストもあります。クリックして広げてください。
<br/>

<details><summary>✏ <b>コード例</b></summary>
  
<br/>
  
### :clap: 正しい例: 3つの要点を満たしたテスト名

![](https://img.shields.io/badge/🔨%20Example%20using%20Mocha-blue.svg "Using Mocha to illustrate the idea")

```javascript
//1. テスト対象のユニット
describe('Products Service', function() {
  describe('productを追加する', function() {
    //2. シナリオ and 3. 期待する結果
    it('priceが指定されていない時、 productのステータスが承認待ちであること', ()=> {
      const newProduct = new ProductService().add(...);
      expect(newProduct.status).to.equal('pendingApproval');
    });
  });
});

```

<br/>

### :clap: 正しい例: 3つの要点を満たしたテスト名

![alt text](/assets/bp-1-3-parts.jpeg "A test name that constitutes 3 parts")

</details>

<br/>
<details><summary>© <b>クレジット & もっと読む</b></summary>
  1. <a href='https://osherove.com/blog/2005/4/3/naming-standards-for-unit-tests.html'>Roy Osherove - Naming standards for unit tests</a>
</details>

<br/><br/>

## ⚪ ️ 1.2 AAAパターンでテストを構成する

:white_check_mark: **こうしましょう:** Arrange(準備する), Act(動かす), Assert(確認する)という3つの工程でテストを構成しましょう。こうすることで、コードを読む人がテストの方針を理解するために脳内CPUを費やさずに済みます。

1つ目のA - Arrange(準備する): テストがシミュレートしたい状況をセットアップするためのコードです。これには、テストしたい対象をインスタンス化する、DBレコードを追加する、特定のオブジェクトをモック/スタブすることなどが含まれます。  

2つ目のA - Act(動かす): テスト対象を動かします。 大抵は1行で済みます。  

3つ目のA - Assert(確認する): 返り値が期待している結果となっているかどうかを確認します。大抵は1行で済みます。  

<br/>

❌ **さもなくば:** メインのコードを理解するのに何時間もかかってしまうばかりか、1日のタスクの中で本来は最も簡単であるはずのテストを書くという行為で脳がくたくたになってしまいます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: AAAパターンで構成されたテスト

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest") ![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Examples with Mocha")

```javascript
describe("Customer classifier", () => {
  test("カスタマーが500$費やした時, プレミアムとして識別されること", () => {
    //Arrange(準備する)
    const customerToClassify = { spent: 505, joined: new Date(), id: 1 };
    const DBStub = sinon.stub(dataAccess, "getCustomer").reply({ id: 1, classification: "regular" });

    //Act(動かす)
    const receivedClassification = customerClassifier.classifyCustomer(customerToClassify);

    //Assert(確認する)
    expect(receivedClassification).toMatch("premium");
  });
});
```

<br/>

### :thumbsdown: アンチパターン例: 区切りがなく、ひとかたまりで、分かりにくい

```javascript
test("プレミアムとして識別されること", () => {
  const customerToClassify = { spent: 505, joined: new Date(), id: 1 };
  const DBStub = sinon.stub(dataAccess, "getCustomer").reply({ id: 1, classification: "regular" });
  const receivedClassification = customerClassifier.classifyCustomer(customerToClassify);
  expect(receivedClassification).toMatch("premium");
});
```

</details>

<br/><br/>

## ⚪ ️1.3 プロダクト由来の言葉で期待する振る舞いを記述する: BDDスタイルのアサーションを使う

:white_check_mark: **こうしましょう:** 宣言的なスタイルでテストを書くことは、読者に少しも脳内CPUを使わせずに概観を掴ませる助けとなります。沢山の条件ロジックを含むような命令的なコードを書くと、読者は脳内CPUを沢山使うことを強制されてしまいます。  
なので、宣言的なBDDスタイルで、 `expect` や `should` などを用い、お手製を避けつつ、人間的な言葉で期待する結果を書きましょう。  
もしも、ChaiやJestが欲しいアサーションメソッドをもっておらず、そしてその欲しいアサーションメソッドが何度も使いうるものであれば、[Jestのマッチャーを拡張すること](https://jestjs.io/docs/en/expect#expectextendmatchers)や[カスタムChaiプラグイン](https://www.chaijs.com/guide/plugins/)を書くことを検討してみてください。
<br/>

❌ **さもなくば:** チームがテストを書かなくなり、面倒なテストを.skip()で飛ばすようになります。

<br/>

<details><summary>✏ <b>コード例</b></summary><br/>

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Examples with Mocha & Chai") ![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest")

### :thumbsdown: アンチパターン例: 読者がテストの方針を知るために、命令的なコードをそれなりの量確認しなければならない

```javascript
test("アドミンを取得する時、 アドミンのみが取得結果に含まれること", () => {
  //"admin1"、 "admin2" というアドミンと、"user1"というユーザーを追加してあると仮定する
  const allAdmins = getUsers({ adminOnly: true });

  let admin1Found,
    adming2Found = false;

  allAdmins.forEach(aSingleUser => {
    if (aSingleUser === "user1") {
      assert.notEqual(aSingleUser, "user1", "A user was found and not admin");
    }
    if (aSingleUser === "admin1") {
      admin1Found = true;
    }
    if (aSingleUser === "admin2") {
      admin2Found = true;
    }
  });

  if (!admin1Found || !admin2Found) {
    throw new Error("Not all admins were returned");
  }
});
```

<br/>

### :clap: 正しい例: 宣言的なテストを俯瞰するのは容易いことです

```javascript
it("アドミンを取得する時、 アドミンのみが取得結果に含まれること", () => { 
  // 2人アドミンを追加してあると仮定する
  const allAdmins = getUsers({ adminOnly: true });

  expect(allAdmins)
    .to.include.ordered.members(["admin1", "admin2"])
    .but.not.include.ordered.members(["user1"]);
});
```

</details>

<br/><br/>

## ⚪ ️ 1.4 ブラックボックステストを守る: パブリックメソッドのみをテストする

:white_check_mark: **こうしましょう:** 内部実装をテストしても大きなオーバーヘッドの割に、何も得られません。もしコードやAPIが正しい結果を返しているのなら、3時間もかけて"どのように"それが達成されたかをテストし、更にそのような壊れやすいテストをメンテしていく必要がありますか？   
公開されている振る舞いがテストされている時は、常に内部実装も暗黙的にテストされていて、そのテストが壊れる時というのは何か特定の問題があった時だけです（たとえば、出力が間違っているなど）。
このようなアプローチは`behavioral testing`と呼ばれます。
逆に、内部実装をテストする場合（ホワイトボックス的アプローチ) - フォーカスがコンポーネントの出力から核心的な詳細に移ります。小さなリファクタリングによって、たとえ出力結果が問題なかったとしても、テストが壊れるかもしれません。- これはメンテナンスコストを著しく向上させてしまいます。

<br/>

❌ **さもなくば:** テストが[オオカミ少年](https://ja.wikipedia.org/wiki/%E5%98%98%E3%82%92%E3%81%A4%E3%81%8F%E5%AD%90%E4%BE%9B)になります: （例えば、プライベート変数の名前が変わったことでテストが壊れたなどの理由で）嘘の叫びをあげます。開発者たちがCIの通知を無視し続けてある日本当のバグが無視されてしまうようになるのも、全く驚くことではありません。

<br/>
<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: 特に理由もなく内部実装をテストしている

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Examples with Mocha & Chai")

```javascript
class ProductService {
  // このメソッドは内部でしか使われていない
  // このメソッド名を変更するとテストが壊れる
  calculateVATAdd(priceWithoutVAT) {
    return { finalPrice: priceWithoutVAT * 1.2 };
    // 上記の返り値の形やキー名を変えるとテストが壊れる
  }
  //public method
  getPrice(productId) {
    const desiredProduct = DB.getProduct(productId);
    finalPrice = this.calculateVATAdd(desiredProduct.price).finalPrice;
    return finalPrice;
  }
}

it("ホワイトボックステスト: 内部メソッドが0 vatを受け取る時, 0を返す", async () => {
  // ユーザーがVATを計算できるようにしなければいけない要件はなく、最終金額が示せれば良い。それにも関わらず、クラス内部をテストすることに固執してしまっている。
  expect(new ProductService().calculateVATAdd(0).finalPrice).to.equal(0);
});
```

</details>

<br/><br/>

## ⚪ ️ ️1.5 正しいテストダブルを選択する: スタブやスパイの代わりにモックを使わない

:white_check_mark: **こうしましょう:** テストダブルはアプリケーションの内部に結合しているため必要悪ですが、時には大きな価値をもたらします。 (<a href="https://martinfowler.com/articles/mocksArentStubs.html" data-href="https://martinfowler.com/articles/mocksArentStubs.html" class="markup--anchor markup--p-anchor" rel="noopener nofollow" target="_blank">[テストダブルって何のことか忘れてしまった人はこちらを読みましょう: モック vs スタブ vs スパイ](https://martinfowler.com/articles/mocksArentStubs.html)</a>).

テストダブルを使う前に簡単な自問をしましょう： 私がテストしようとしている機能は仕様書に書いてある、あるいは今後書かれうることか？もし違うなら、それはホワイトボックステストになってしまっている可能性があります。

たとえば、もし決済サービスが落ちた時にどんな風にアプリケーションが振る舞うのかテストしたい時、決済サービスをスタブして'No Response'を返却させることでテスト対象が正しい値を返しているか確認することでしょう。これは特定のシナリオ下におけるアプリケーションの振る舞い、応答、結果をチェックします。あるいは、決済サービスが落ちている時にメールが送信されることをスパイを使って確認することでしょう。 - これも仕様書におそらく書かれていることの振る舞い確認です。（"決済に失敗したらメールを送信する"）  
一方で、決済サービスをモックしてそれが正しいJavaScriptの型で呼び出されていることを確認する場合 - アプリケーションの機能とは関係のない内部のことにテストがフォーカスしてしまい、頻繁に更新しなければならないでしょう。

<br/>  

❌ **さもなくば:** どんなリファクタリングをするにも、コード上で使われている全てのモックを探して更新することが必要になってしまいます。すると、テストは頼りがいのある親友ではなく、重荷になってしまいます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: モックの関心が内部実装にある

![](https://img.shields.io/badge/🔧%20Example%20using%20Sinon-blue.svg "Examples with Sinon")

```javascript
it("有効なプロダクトが削除される時, データアクセス用のDALが正しいプロダクトと正しいコンフィグで1度だけ呼ばれること", async () => {
  //既にプロダクトを追加してあるとする
  const dataAccessMock = sinon.mock(DAL); 
  //う〜ん、よくないですね: 内部実装をテストすることがゴールになってしまっていて、ただの副作用ではなくなってしまっています。
  dataAccessMock
    .expects("deleteProduct")
    .once()
    .withArgs(DBConfig, theProductWeJustAdded, true, false);
  new ProductService().deletePrice(theProductWeJustAdded);
  dataAccessMock.verify();
});
```

<br/>

### :clap:正しいコード例: スパイの関心が要件をテストすることにあり、副作用は結果として内部実装に触れている

```javascript
it("有効なプロダクトが削除される時, メールが送信されること", async () => {
  //既にプロダクトを追加してあるとする
  const spy = sinon.spy(Emailer.prototype, "sendEmail");
  new ProductService().deletePrice(theProductWeJustAdded);
  //う〜ん、OK: これも内部実装じゃないのかって? そうですね、でもメールを送信するという要件をテストする上での副作用としてです
  expect(spy.calledOnce).to.be.true;
});
```

</details>

<br/><br/>

## 📗 これらのプラクティスを動画で学びたいですか?

### 私のオンラインコースをチェックしてみてください [Testing Node.js & JavaScript From A To Z](https://www.testjavascript.com)

<br/><br/>

## ⚪ ️1.6 "foo"ではなく、リアルな入力データを使う

:white_check_mark: **こうしましょう:** 時にプロダクションのバグは予期せぬ非常に限定的な入力値によってもたらされます - テストの入力値がリアルであるほど、バグを早期に発見できる可能性が高まります。[Faker](https://www.npmjs.com/package/faker)のような専用のライブラリを使うことで、擬似的にリアルで、プロダクションの様々な状態に似せたデータを生成しましょう。たとえば、そういうライブラリを使うとリアルっぽい電話番号、ユーザー名、クレジットカード情報、会社名、あるいは'lorem ipsum'テキストまで生成できます。fakerのデータをランダムにしてテスト対象ユニットを拡張するようなテストを作ることもできますし（通常のテストに加えてです、代わりにではなく）、あるいは実際のプロダクション環境からデータをインポートすることもできます。もっと高いレベルをみたいですか？次の弾丸をみてください（property-basedテスト）

<br/>

❌ **さもなくば:** 
"Foo"のような人工的な入力値を使っていると、開発時のテストでは誤ってグリーンになってしまうかもしれませんが、本番環境でハッカーが“@3e2ddsf . ##’ 1 fdsfds . fds432 AAAA”のような薄汚い文字列を渡してきたら、レッドになってしまうかもしれません。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: 人工的なデータのせいでテストスイートが通ってしまう

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest")

```javascript
const addProduct = (name, price) => {
  const productNameRegexNoSpace = /^\S*$/; //空白文字列を許容しない

  if (!productNameRegexNoSpace.test(name)) return false; //入力値が簡易的なせいで、このパスには到達しない

  //なにかここにロジックがあるとする
  return true;
};

test("ダメな例: 有効なプロパティでproductを追加する時、確認に成功する", async () => {
  //"Foo"という文字列が全てのテストで使われ、永遠にfalseな結果を引き起こさない
  const addProductResult = addProduct("Foo", 5);
  expect(addProductResult).toBe(true);
  //誤った成功: 空白の入った長い文字列で試さなかったので成功してしまった
});
```

<br/>

### :clap: 正しい例: ランダムにリアルな入力値を使う

```javascript
it("良い例: 有効なproductを追加する時、確認に成功する", async () => {
  const addProductResult = addProduct(faker.commerce.productName(), faker.random.number());
  //生成されたランダムな入力値: {'Sleek Cotton Computer',  85481}
  expect(addProductResult).to.be.true;
  //ランダムな入力値のおかげで、予期していなかったコードパスに到達してテストが失敗した。
  //バグを早期発見できた！
});
```

</details>

<br/><br/>

## ⚪ ️ 1.7 Property-basedテストで多様な入力値の組み合わせをテストする

:white_check_mark: **こうしましょう:** 開発者は往々にしてわずかな入力値のパターンでテストをしてしまいがちです。入力値のフォーマットが現実のデータに近い時ですら（[’fooを使うな’](https://github.com/goldbergyoni/javascript-testing-best-practices#-%EF%B8%8F16-dont-foo-use-realistic-input-data)の項を読んでください）、開発者は method(‘’, true, 1), method(“string” , false , 0) のような限られた入力値の組合せしかカバーしません。 
 
 しかし本番環境では、5個のパラメーターを持つAPIは何千もの組合せで呼び出されますし、その中の1つがプロセスを落としてしまうかもしれません。（[Fuzz Testingを読んでください](https://en.wikipedia.org/wiki/Fuzzing)）。
 もし、1個のテストで1000種もの入力値を自動で試し、どの入力値が正しいレスポンスを返せなかったかを把握できる、と言ったらどうですか？  
 Property-basedテストという技術はまさにそれをやってくれます: ありえる全ての入力値のパターンをテスト対象に流し込むことで、バグを発見する機運を高めてくれるのです。
たとえば、addNewProduct(id, name, isDiscount) というメソッドがあるとしましょう。このメソッドを使うライブラリは、(1, “iPhone”, false), (2, “Galaxy”, true) のような、(number, string, boolean)のあらゆる組合せで呼び出します。
[js-verify](https://github.com/jsverify/jsverify) や [testcheck](https://github.com/leebyron/testcheck-js) (こちらの方がドキュメントが断然良いです)のようなライブラリを使うと、MochaやJestなどお好みのテストランナーライブラリでproperty-basedテストを実行することができます。
Update: Nicolas Dubienさんが下記のコメントで[fast-checkを見てみてください](https://github.com/dubzzz/fast-check#readme)と提案してくれましたが、こちらのライブラリはさらにフィーチャーを提供していて、アクティブにメンテナンスされているようです。
<br/>

❌ **さもなくば:** ちゃんと動くコードパスしか網羅しないテスト入力値を無意識で選択してしまいます。残念ながらこれでは、バグを表出させるための相棒であるテストの効率を下げてしまいます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: "fast-check"を使って多様な入力値の組み合わせをテスト

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest")

```javascript
import fc from "fast-check";

describe("Product service", () => {
  describe("Adding new", () => {
    //これはランダムなプロパティで100回走る
    it("有効な範囲内でランダムなプロパティでproductを追加する時、常に成功すること", () =>
      fc.assert(
        fc.property(fc.integer(), fc.string(), (id, name) => {
          expect(addNewProduct(id, name).status).toEqual("approved");
        })
      ));
  });
});
```

</details>

<br/><br/>

## ⚪ ️ 1.8 必要に応じて、短くインラインのスナップショットを使用

:white_check_mark: **こうしましょう:** [スナップショットテスト](https://jestjs.io/docs/en/snapshot-testing)が必要な場合、短く集中したスナップショット（3〜7行程度）を使用し、テストの一部としてインラインで含めること（[Inline Snapshot](https://jestjs.io/docs/en/snapshot-testing#inline-snapshots)）が推奨されます。外部ファイルに保存しないことで、テストは自己説明的で壊れにくくなります。

一方で、「クラシックスナップショット」のチュートリアルやツールは、大きなファイル（例：コンポーネントのレンダリングマークアップやAPIのJSON結果）を外部に保存し、テスト実行時に受け取った結果と保存されたバージョンを比較することを推奨しています。しかし、これにより、テストが1000行や3000個のデータ値に暗黙的に結び付けられ、テスト作成者がそれを読んで理解することができなくなります。なぜこれが問題なのでしょうか？ その理由は多岐にわたり、スナップショットが無効になるのに1行の変更で十分で、これは頻繁に発生します。具体的には、スペース、コメント、CSS/HTMLの小さな変更ごとに起こり得ます。このような場合、テスト名からエラーの手がかりを得ることは難しく、単に1000行が変更されなかったかをチェックするだけになります。また、テスト作成者が確認も検証もできない長文ドキュメントを望ましい真実として受け入れるように促します。これらはすべて、焦点が定まらず、過剰な目標を達成しようとする不透明で過度なテストの症状です。

なお、スキーマを確認し、データを確認しない場合（フィールドに焦点を当て、値を抽出する）や、受け取るドキュメントがほとんど変更されない場合など、長い外部スナップショットが受け入れられるケースも少しだけあります。
<br/>

❌ **さもなくば:** UIテストが失敗します。コードは正しいように見え、画面は完璧にレンダリングされているのに、何が起こったのでしょうか？ スナップショットテストは、元のドキュメントと現在受け取ったものとの差異を発見しました—マークダウンにスペースが1つ追加されていただけでした...

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: 目に見えない2000行のコードにテストを結び付ける

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest")

```javascript
it("TestJavaScript.com is renderd correctly", () => {
  //Arrange(準備する)

  //Act(動かす)
  const receivedPage = renderer
    .create(<DisplayPage page="http://www.testjavascript.com"> Test JavaScript </DisplayPage>)
    .toJSON();

  //Assert(確認する)
  expect(receivedPage).toMatchSnapshot();
  //これで私たちは暗黙的に2000行のドキュメントを維持することになります
  //追加の改行やコメントごとに、このテストは壊れます
});
```

<br/>

### :clap: 正しい例: 期待値が明確で集中している

```javascript
it("When visiting TestJavaScript.com home page, a menu is displayed", () => {
  //Arrange(準備する)

  //Act(動かす)
  const receivedPage = renderer
    .create(<DisplayPage page="http://www.testjavascript.com"> Test JavaScript </DisplayPage>)
    .toJSON();

  //Assert(確認する)

  const menu = receivedPage.content.menu;
  expect(menu).toMatchInlineSnapshot(`
<ul>
<li>Home</li>
<li> About </li>
<li> Contact </li>
</ul>
`);
});
```

</details>

<br/><br/>

## ⚪ ️ 1.9 必要なコードのみをコピーする

:white_check_mark: **こうしましょう:** テスト結果に影響を与える必要な詳細はすべて含めますが、それ以上は含めません。例えば、100行の入力JSONを処理するテストを考えてみましょう。これを毎回テストに貼り付けるのは手間です。これを外部に抽出して `transferFactory.getJSON()` とすると、テストが曖昧になってしまいます — データがなければ、テスト結果とその原因を関連付けるのが難しくなります（「なぜ400ステータスを返すべきなのか？」）。古典的な書籍「x-unitパターン」では、このパターンを「謎のゲスト」と呼んでいます — 何か見えないものがテスト結果に影響を与えていますが、正確には何が影響を与えたのか分かりません。繰り返し使われる長い部分を外部に抽出し、テストに重要な具体的な詳細を明示的に示すことで、改善できます。上記の例を使うと、テストは重要な部分を強調するパラメーターを渡すことができます：`transferFactory.getJSON({sender: undefined})`。この例では、読者はすぐに「senderフィールドが空であることが、テストがバリデーションエラーやその他の適切な結果を期待する理由である」と推測すべきです。
<br/>

❌ **さもなくば:** 500行のJSONをコピーすることは、テストを維持不可能で読みにくくします。すべてを外部に移動すると、理解しにくい曖昧なテストが生まれます

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>


### :thumbsdown: アンチパターン例: テストの失敗が不明確で、原因が外部にあり、大きなJSON内に隠れている

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Examples with Mocha")

```javascript
test("クレジットがない場合、転送は拒否される", async() => {
      //Arrange(準備する)
      const transferRequest = testHelpers.factorMoneyTransfer() //200行のJSONが返ってくる;
      const transferServiceUnderTest = new TransferService();

      //Act(動かす)
      const transferResponse = await transferServiceUnderTest.transfer(transferRequest);

      //Assert(確認する)
      expect(transferResponse.status).toBe(409);// でもなぜ失敗を期待するのか: テスト内ではすべてが完璧に有効に見える 🤔
    });
```

<br/>

### :clap: 正しい例: テスト結果の原因を強調する

```javascript
test("クレジットがない場合、転送は拒否される", async() => {
      //Arrange(準備する)
      const transferRequest = testHelpers.factorMoneyTransfer({userCredit:100, transferAmount:200}) // 明らかにクレジットが不足している
      const transferServiceUnderTest = new TransferService({disallowOvercharge:true});

      //Act(動かす)
      const transferResponse = await transferServiceUnderTest.transfer(transferRequest);

      //Assert(確認する)
      expect(transferResponse.status).toBe(409); // ユーザーにクレジットがない場合、明らかに失敗するべき
    });
```

</details>

<br/><br/>

## ⚪ ️ 1.10 エラーをキャッチせず、エラーを期待する

:white_check_mark: **こうしましょう:** ある入力がエラーを引き起こすことをアサートしようとするとき、try-catch-finallyを使用してcatch句が実行されたことを確認するのは正しいように見えるかもしれません。しかし、その結果はシンプルなテストの意図や結果の期待を隠してしまう、冗長で不格好なテストケースになります（以下の例参照）。

よりエレガントな代替手段は、専用のChaiアサーションを1行で使用することです：expect(method).to.throw（またはJestではexpect(method).toThrow()）。また、例外がエラータイプを示すプロパティを含むことを確認することが絶対に必要です。さもないと、単なる一般的なエラーを渡すだけでは、アプリケーションはユーザーに失望させるメッセージを表示する以外に多くのことができません。

<br/>

❌ **さもなくば:** テストレポート（例: CIレポート）から何が問題だったのかを推測するのが難しくなります。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: try-catchでエラーの存在をアサートしようとする冗長なテストケース

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Examples with Mocha")

```javascript
it("商品名がない場合、エラー400をスローする", async () => {
  let errorWeExceptFor = null;
  try {
    const result = await addNewProduct({});
  } catch (error) {
    expect(error.code).to.equal("InvalidInput");
    errorWeExceptFor = error;
  }
  expect(errorWeExceptFor).not.to.be.null;
  // このアサーションが失敗した場合、テスト結果/レポートには
  // 値がnullであることしか表示されず、例外が見つからないことについては言及されません
});
```

<br/>

### :clap: 正しい例: QAや技術的なPMでも簡単に理解できる人間が読めるexpect

```javascript
it("商品名がない場合、エラー400をスローする", async () => {
  await expect(addNewProduct({}))
    .to.eventually.throw(AppError)
    .with.property("code", "InvalidInput");
});
```

</details>

<br/><br/>

## ⚪ ️ 1.11 テストにタグを付ける

:white_check_mark: **こうしましょう:** 異なるテストは異なるシナリオで実行する必要があります。例えば、クイックなスモークテストやI/Oレスなテストは、開発者がファイルを保存またはコミットしたときに実行し、フルなエンドツーエンドテストは通常、プルリクエストが提出されたときに実行されます。これを実現するためには、#cold #api #sanity などのキーワードでテストにタグを付け、テストハーネスでgrepを使って必要なサブセットを呼び出すことができます。例えば、Mochaでsanityテストグループのみを呼び出す方法は以下の通りです：mocha — grep ‘sanity’

<br/>

❌ **さもなくば:** 開発者が小さな変更を加えるたびに、データベースクエリを数十回実行するテストも含めてすべてのテストを実行するのは非常に遅くなり、開発者がテストを実行するのを避ける原因となります。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: ‘#cold-test’としてテストにタグを付けることで、テストランナーは高速なテストのみを実行できるようになります（Cold === I/Oを行わない迅速なテストで、開発者が入力している間でも頻繁に実行できます）

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest")

```javascript
//このテストは高速で（DBを使用しない）、それに応じてタグ付けしています
//これでユーザーやCIは頻繁に実行できます
describe("Order service", function() {
  describe("新しい注文の追加 #cold-test #sanity", function() {
    test("シナリオ - 通貨が指定されていない。期待 - デフォルト通貨を使用 #sanity", function() {
      //コードロジックここに
    });
  });
});
```

</details>

<br/><br/>

## ⚪ ️ 1.12 テストを少なくとも2つのレベルで分類する

:white_check_mark: **こうしましょう:** テストスイートにある程度の構造を適用し、偶然訪れる人がテストの要件（テストは最高のドキュメント）やテストされているさまざまなシナリオを簡単に理解できるようにします。この方法の一般的なものは、テストの前に少なくとも2つの'describe'ブロックを配置することです。1つ目はテスト対象のユニットの名前、2つ目はシナリオやカスタムカテゴリーなどの追加の分類レベルです（以下のコード例とスクリーンショットを参照）。これにより、テストレポートが大幅に改善されます：読者はテストのカテゴリーを簡単に推測し、希望するセクションに深入りして失敗したテストと相関させることができます。さらに、多くのテストを含むスイートのコードを開発者がナビゲートするのがずっと簡単になります。テストスイートの構造に関して、[given-when-then](https://github.com/searls/jasmine-given) や [RITE](https://github.com/ericelliott/riteway) などの複数の代替構造を検討することができます。

<br/>

❌ **さもなくば:** フラットで長いテストのリストを見たとき、長いテキストをざっと読んで主要なシナリオを結論し、失敗したテストの共通点を相関させる必要があります。例えば、100のテストのうち7つが失敗した場合、フラットなリストでは失敗したテストのテキストを読み、どのように関連しているかを確認しなければなりません。しかし、階層的なレポートでは、すべてが同じフローやカテゴリの下にあり、原因をすばやく推測できます。少なくともどこが根本的な失敗の原因かを推測することができます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: テスト対象ユニットとシナリオでスイートを構造化すると、以下のような便利なレポートが得られます

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest")

```javascript
// テスト対象ユニット
describe("Transfer service", () => {
  // シナリオ
  describe("When no credit", () => {
    // 期待値
    test("Then the response status should decline", () => {});

    // 期待値
    test("Then it should send email to admin", () => {});
  });
});
```

![alt text](assets/hierarchical-report.png)

<br/>

### :thumbsdown: アンチパターン例: テストのフラットなリストは、読者がユーザーストーリーを特定し、失敗したテストを関連付けるのを難しくする

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Mocha")

```javascript
test("レスポンスステータスが拒否されるべき", () => {});

test("それが管理者にメールを送信するべき", () => {});

test("新しい転送レコードが作成されないべき", () => {});
```

![alt text](assets/flat-report.png)

<br/>

</details>

<br/><br/>

## ⚪ ️1.13 その他の一般的な良いテスト習慣

:white_check_mark: **こうしましょう:** この投稿は、Node JSに関連した、または少なくともNode JSを例に挙げて説明できるテストに関するアドバイスに焦点を当てています。ただし、この項目では、Nodeに関連しないいくつかのよく知られたアドバイスをまとめています。

[TDDの原則](https://www.sm-cloud.com/book-review-test-driven-development-by-example-a-tldr/)を学び、実践する — これは多くの人にとって非常に価値がありますが、自分のスタイルに合わない場合でも気にしないでください、あなたが唯一の人ではありません。コードの前にテストを書くことを検討し、[レッド・グリーン・リファクタリングスタイル](https://blog.cleancoder.com/uncle-bob/2014/12/17/TheCyclesOfTDD.html)を採用し、各テストが正確に1つのことをチェックするようにしましょう。バグを見つけた場合は、それを修正する前にそのバグを将来検出できるテストを書き、少なくとも1回はテストを失敗させた後に成功するようにしましょう。モジュールを始めるときは、最初にテストを満たすための簡単でシンプルなコードを書き、その後、徐々にリファクタリングして本番用の品質に仕上げていきます。環境（パス、OSなど）への依存は避けましょう。
<br/>

❌ **さもなくば:** 数十年にわたって集められた知恵の宝石を見逃すことになります

<br/><br/>

# Section 2️⃣: バックエンドテスティング

## ⚪️ 2.1 あなたのテストポートフォリオを豊かにする：Unit testsとピラミッドを超えて

:white_check_mark: **こうしましょう：** [testing pyramid](https://martinfowler.com/bliki/TestPyramid.html)は10年以上前のものですが、3つのテストタイプを提案し、多くの開発者のテスト戦略に影響を与える素晴らしく関連性の高いモデルです。同時に、testing pyramidの影に隠れた輝かしい新しいテスト手法がいくつも登場しました。過去10年に見られた（Microservices、cloud、serverless）といった劇的な変化を考えると、一つの古いモデルが*全て*のアプリケーションタイプに適合することが可能なのでしょうか？テストの世界は新しいテスト手法を歓迎すべきではないでしょうか？

誤解しないでください。2019年においても、testing pyramid、TDD、unit testsは依然として強力な手法であり、多くのアプリケーションにとって最適な選択でしょう。しかし、他のどんなモデルと同様に、その有用性にもかかわらず、[時には間違っているに違いありません](https://en.wikipedia.org/wiki/All_models_are_wrong)。例えば、Kafka/RabbitMQのようなメッセージバスに多くのイベントを取り込むIoTアプリケーションを考えてみましょう。これらはデータウェアハウスに流れ込み、最終的には分析用UIでクエリされます。ほとんどロジックがなく、統合が中心のアプリケーションに対して、テスト予算の50%をUnit testsの作成に費やすべきでしょうか？アプリケーションタイプの多様性が増すにつれて（bots、crypto、Alexa-skills）、testing pyramidが最適な適合ではないシナリオが見つかる可能性が高くなります。

あなたのテストポートフォリオを豊かにし、より多くのテストタイプに精通する時です（次の箇条書きでいくつかのアイデアを提案します）。testing pyramidのようなマインドモデルを持ちながらも、直面している現実の問題にテストタイプを合わせましょう（「おい、APIが壊れている。consumer-driven contract testingを書こう！」）。リスク分析に基づいてポートフォリオを構築する投資家のようにテストを多様化しましょう—問題が発生し得る箇所を評価し、それらの潜在的なリスクを軽減するための予防策を適用します。

注意点：ソフトウェアの世界におけるTDDに関する議論は典型的な偽の二分法を呈しています。あらゆる場所で使うべきだと説く人もいれば、悪魔だと考える人もいます。絶対的な言い方をする人は皆、間違っています :]

<br/>

❌ **さもなくば：** 驚くほどROIの高いツールを見逃すことになります。Fuzz、lint、mutationのようなものは10分で価値を提供できます

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: Cindy Sridharan は彼女の素晴らしい投稿『Testing Microservices — the same way』で豊富なテストポートフォリオを提案しています

![alt text](assets/bp-12-rich-testing.jpeg "Cindy Sridharan は彼女の素晴らしい投稿『Testing Microservices — the sane way』で豊富なテストポートフォリオを提案しています")

<strong class="markup--strong markup--p-strong">☺️例: </strong><a href="https://www.youtube.com/watch?v=-2zP494wdUY&amp;feature=youtube" data-href="https://www.youtube.com/watch?v=-2zP494wdUY&amp;feature=youtu.be" class="markup--anchor markup--p-anchor" rel="nofollow noopener" target="_blank">[YouTube: “Beyond Unit Tests: 5 Shiny Node.JS Test Types (2018)” (Yoni Goldberg)](https://www.youtube.com/watch?v=-2zP494wdUY&feature=youtu.be)</a>

<br/>

![alt text](assets/bp-12-Yoni-Goldberg-Testing.jpeg "A test name that constitutes 3 parts")

</details>

<br/><br/>

## ⚪ ️2.2 コンポーネントテストはあなたのベストな選択かもしれません

:white_check_mark: **こうしましょう:** 各ユニットテストはアプリケーションのごく一部をカバーしており、全体をカバーするには高コストです。一方、エンドツーエンドテストは多くを簡単にカバーできますが、信頼性が低く、遅いです。なぜ、バランスの取れたアプローチを適用し、ユニットテストより大きく、エンドツーエンドテストより小さいテストを書くことを考えないのでしょうか？コンポーネントテストはテストの世界の隠れた名曲です — 彼らは両者の良いところを提供します。妥当なパフォーマンスとTDDパターンの適用可能性、そして現実的で素晴らしいカバレッジを提供します。

コンポーネントテストはマイクロサービスの「単位」に焦点を当てており、APIに対して動作し、マイクロサービス自体に属するもの（例えば、実際のDB、もしくは少なくともそのDBのインメモリ版）をモックせず、他のマイクロサービスへの呼び出しなどの外部のものはスタブします。この方法により、デプロイするものをテストし、アプリを外部から内部へとアプローチし、合理的な時間で大きな自信を得ることができます。
<br/>

❌ **さもなくば:** ユニットテストを書くことに長い日々を費やし、システムのたった20％しかカバーできていないことが分かるかもしれません。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: SupertestはExpress APIへのインプロセスアプローチを可能にします（高速で多くの層をカバー）

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Examples with Mocha")

![alt text](assets/bp-13-component-test-yoni-goldberg.png " [Supertest](https://www.npmjs.com/package/supertest) allows approaching Express API in-process (fast and cover many layers)")

</details>

<br/><br/>

## ⚪ ️2.3 コントラクトテストを使用して新リリースがAPIを壊さないことを保証する

:white_check_mark: **こうしましょう:** あなたのマイクロサービスには複数のクライアントがあり、互換性の理由で複数のバージョンのサービスを実行しています（すべての人を満足させるため）。そこで、何かフィールドを変更しようとしたら「ドカン！」と、そのフィールドに依存している重要なクライアントが怒ってしまいました。これは統合の世界のジレンマです：サーバー側が複数のクライアントの期待をすべて考慮するのは非常に挑戦的であり、一方でクライアントはサーバーがリリース日を制御するため、テストを実行できません。[Consumer-driven contracts とフレームワークPACT](https://docs.pact.io/)は、非常に革新的なアプローチでこのプロセスを形式化するために生まれました。サーバーは自分自身のテスト計画を定義するのではなく、クライアントがサーバーのテストを定義します！PACTはクライアントの期待を記録し、共有場所「ブローカー」に配置することで、サーバーがPACTライブラリを使用して各ビルドで期待を引き出し、破れた契約 — 満たされないクライアントの期待 — を検出することができます。この方法により、すべてのサーバークライアントAPIの不一致がビルド/CIの早期に発見され、大きなフラストレーションを避けることができるかもしれません。
<br/>

❌ **さもなくば:** 他の選択肢は疲れる手動テストやデプロイの恐怖です。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例:

![](https://img.shields.io/badge/🔧%20Example%20using%20PACT-blue.svg "Examples with PACT")

![alt text](assets/bp-14-testing-best-practices-contract-flow.png)

</details>

<br/><br/>

## ⚪ ️2.4 ミドルウェアを単体でテストする

:white_check_mark: **こうしましょう:** ミドルウェアテストを避ける人は多いですが、それはシステムの小さな部分であり、ライブのExpressサーバーを必要とするからです。これらの理由はどちらも間違っています —  ミドルウェアは小さいですが、すべてまたはほとんどのリクエストに影響を与え、{req,res} JSオブジェクトを受け取る純関数として簡単にテストできます。ミドルウェア関数をテストするには、それを呼び出し、{req,res}オブジェクトとのやりとりをスパイ（例えば[Sinonを使用して](https://www.npmjs.com/package/sinon)）して、関数が正しいアクションを実行したことを確認するだけでいいのです。[node-mock-http](https://www.npmjs.com/package/node-mocks-http)ライブラリは、{req,res}オブジェクトを因数分解し、それらの振る舞いをスパイすることさらに進みます。例えば、resオブジェクトに設定されたHTTPステータスが期待に合っているかをアサートできます（以下の例を参照）。
<br/>

❌ **さもなくば:** Expressミドルウェアのバグ === すべてまたはほとんどのリクエストのバグ

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: ネットワーク呼び出しを発行せず、Express全体を起動させずにミドルウェアを単体でテスト

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Examples with Jest")

```javascript
// テストしたいミドルウェア
const unitUnderTest = require("./middleware");
const httpMocks = require("node-mocks-http");
// Jestの文法、Mochaのdescribe() & it()と同等
test("認証ヘッダーなしのリクエストは、httpステータス403を返すべき", () => {
  const request = httpMocks.createRequest({
    method: "GET",
    url: "/user/42",
    headers: {
      authentication: ""
    }
  });
  const response = httpMocks.createResponse();
  unitUnderTest(request, response);
  expect(response.statusCode).toBe(403);
});
```

</details>

<br/><br/>

## ⚪ ️2.5 静的解析ツールを使用して測定しリファクタリング

:white_check_mark: **こうしましょう:** 静的解析ツールを使用することで、コードの品質を向上させ、コードを保守可能に保つための客観的な方法が提供されます。静的解析ツールをCIビルドに追加して、コードの悪臭を発見したときにビルドを中止することができます。通常のリンティングに対する主な売りのポイントは、複数のファイルの文脈で品質を検査する能力（例: 重複の検出）、高度な解析の実施（例: コードの複雑さ）そしてコードの問題の履歴と進捗の追跡です。使用できるツールの例として、[SonarQube](https://www.sonarqube.org/)（4,900以上の[stars](https://github.com/SonarSource/sonarqube)）と[Code Climate](https://codeclimate.com/)（2,000以上の[stars](https://github.com/codeclimate/codeclimate)）があります。

クレジット: <a href="https://github.com/TheHollidayInn" data-href="https://github.com/TheHollidayInn" class="markup--anchor markup--p-anchor" rel="noopener nofollow" target="_blank">[Keith Holliday](https://github.com/TheHollidayInn)</a>

<br/>

❌ **さもなくば:** 低品質のコードでは、バグとパフォーマンスが常に問題となり、どんな新しいライブラリや最先端の機能でも解決できません。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: 複雑なメソッドを識別できる商用ツールCodeClimate:

![](https://img.shields.io/badge/🔧%20Example%20using%20Code%20Climate-blue.svg "Examples with CodeClimate")

![alt text](assets/bp-16-yoni-goldberg-quality.png "CodeClimate, a commercial tool that can identify complex methods:")

</details>

<br/><br/>

## ⚪ ️2.6 Node関連のカオスへの準備を確認する

:white_check_mark: **こうしましょう:** 奇妙なことに、ほとんどのソフトウェアテストはロジックとデータのみですが、最悪の出来事（そして本当に緩和が難しいもの）はインフラストラクチャの問題です。例えば、プロセスメモリが過負荷になったり、サーバー/プロセスがクラッシュしたり、APIの処理が50％遅くなったときに監視システムが認識するかどうかをテストしたことがありますか？これらの悪影響をテストして緩和するために — [カオスエンジニアリング](https://principlesofchaos.org/)はNetflixによって生み出されました。これは、混乱した問題に対するアプリの回復力をテストするための認識、フレームワーク、ツールを提供することを目的としています。例えば、その有名なツールの一つ、[カオスモンキー](https://github.com/Netflix/chaosmonkey)はサーバーをランダムに停止させることで、サービスがユーザーにサービスを提供し続け、単一のサーバーに依存しないことを確認します（また、Kubernetes版としてポッドを停止する[kube-monkey](https://github.com/asobti/kube-monkey)もあります）。これらのツールはすべてホスティング/プラットフォームレベルで機能しますが、純粋なNodeカオスをテストおよび生成したい場合はどうでしょうか。たとえば、Nodeプロセスが未処理のエラー、未処理のpromise拒否、1.7GBの最大許可メモリでのv8メモリ過負荷にどのように対処するか、またはイベントループが頻繁にブロックされるときにUXが満足な状態であるかどうかを確認する場合などを考慮するために、私は[node-chaos](https://github.com/i0natan/node-chaos-monkey)（アルファ版）を作成しました、これはNode関連のカオス的な行為をすべて提供します。
<br/>

❌ **さもなくば:** ここには逃げ場はありません、マーフィーの法則があなたのプロダクションを容赦なく襲撃します

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: Node-chaosはあらゆる種類のNode.jsのいたずらを生成し、アプリのカオスへの耐性をテストできます

![alt text](assets/bp-17-yoni-goldberg-chaos-monkey-nodejs.png "Node-chaos can generate all sort of Node.js pranks so you can test how resilience is your app to chaos")

</details>

<br/>

## ⚪ ️2.7 グローバルなテストフィクスチャとシードを避け、テストごとにデータを追加する

:white_check_mark: **こうしましょう:** ゴールデンルール（箇条書き0）に従うと、各テストは独自のDB行セットを追加し、それに基づいて動作し、結合を防ぎ、テストフローについて簡単に理由づけできるようにすべきです。現実には、パフォーマンス向上のためにテスト前にDBにデータをシード（いわゆる「テストフィクスチャ」）を行うテスターにより、このルールはしばしば違反されます。確かにパフォーマンスは正当な懸念ですが（「コンポーネントテスト」の箇条書きを参照）、テストの複雑さは他の考慮事項を支配すべき辛い問題です。実践的には、各テストケースが必要なDBレコードを明示的に追加し、それらのレコードのみに基づいて動作します。もしパフォーマンスが重要な懸念となった場合は、データを変化させない一部のテストスイート（例: クエリ）のみをシードするという形でバランスの取れた妥協があるかもしれません。
<br/>

❌ **さもなくば:** いくつかのテストが失敗し、デプロイが中止され、私たちのチームは貴重な時間を費やすことになり、「バグがありますか？」と調査することになり、とても大変です。そして、「あぁ、2つのテストが同じシードデータを変化させていました」と気づくのです。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: テストが独立しておらず、グローバルなフックに依存してグローバルなDBデータを供給

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Examples with Mocha")

```javascript
before(async () => {
  // サイトと管理者データをDBに追加します。データはどこですか？外部です。いくつかの外部jsonまたは移行フレームワーク
  await DB.AddSeedDataFromJson('seed.json');
});
it("サイト名を更新すると、成功の確認を得る", async () => {
  // サイト名 "portal" が存在することを知っている - シードファイルでそれを見た
  const siteToUpdate = await SiteService.getSiteByName("Portal");
  const updateNameResult = await SiteService.changeName(siteToUpdate, "newName");
  expect(updateNameResult).to.be(true);
});
it("サイト名でクエリすると、正しいサイトを取得する", async () => {
  // サイト名 "portal" が存在することを知っている - シードファイルでそれを見た
  const siteToCheck = await SiteService.getSiteByName("Portal");
  expect(siteToCheck.name).to.be.equal("Portal"); // 失敗！前のテストで名前が変更された :[
});

```

<br/>

### :clap: 正しい例: テスト内で実施し続けられ、各テストは独自のデータセットで動作

```javascript
it("サイト名を更新すると、成功の確認を得る", async () => {
  // テストは新しいレコードを追加し、レコードに対してのみ動作する
  const siteUnderTest = await SiteService.addSite({
    name: "siteForUpdateTest"
  });
  const updateNameResult = await SiteService.changeName(siteUnderTest, "newName");
  expect(updateNameResult).to.be(true);
});
```

</details>

<br/><br/>

# Section 3️⃣: フロントエンドテスティング

## ⚪ ️3.1 UIと機能を分離する

:white_check_mark: **こうしましょう:** コンポーネントロジックのテストに集中するときは、UIの詳細がノイズになり得るため取り除くべきです。これにより、テストが純粋なデータに焦点を当てられます。実際には、マークアップからグラフィックの実装にあまり結びつかない抽象的な方法で必要なデータを抽出し、純粋なデータ（HTML/CSSのグラフィック詳細ではなく）のみをアサートし、遅延を引き起こすアニメーションを無効にします。UIの裏側（例: サービス、アクション、ストア）のみをテストしてレンダリングを避けたくなるかもしれませんが、これは現実と似ていない架空のテストとなり、正しいデータがUIに届いていないケースを明らかにしません。

<br/>

❌ **さもなくば:** テストの純粋な計算データは10msで準備ができるかもしれませんが、関係のないアニメーションによって全体のテストが500ms（100のテスト = 1分）になるかもしれません。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: UIの詳細を分離

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Examples with React") ![](https://img.shields.io/badge/🔧%20Example%20using%20React%20Testing%20Library-blue.svg "Examples with react-testing-library")

```javascript
test("users-listにVIPのみを表示するフラグが設定されている場合、VIPメンバーのみを表示する", () => {
  // Arrange
  const allUsers = [{ id: 1, name: "Yoni Goldberg", vip: false }, { id: 2, name: "John Doe", vip: true }];

  // Act
  const { getAllByTestId } = render(<UsersList users={allUsers} showOnlyVIP={true} />);

  // Assert - まずUIからデータを抽出する
  const allRenderedUsers = getAllByTestId("user").map(uiElement => uiElement.textContent);
  const allRealVIPUsers = allUsers.filter(user => user.vip).map(user => user.name);
  expect(allRenderedUsers).toEqual(allRealVIPUsers); // データとデータを比較、UIはここにはない
});
```

<br/>

### :thumbsdown: アンチパターン例: アサーションがUIの詳細とデータを混合

```javascript
test("users-listにVIPのみを表示するフラグが設定されている場合、VIPメンバーのみを表示する", () => {
  // Arrange
  const allUsers = [{ id: 1, name: "Yoni Goldberg", vip: false }, { id: 2, name: "John Doe", vip: true }];

  // Act
  const { getAllByTestId } = render(<UsersList users={allUsers} showOnlyVIP={true} />);

  // Assert - アサーションにUIとデータを混在させる
  expect(getAllByTestId("user")).toEqual('[<li data-test-id="user">John Doe</li>]');
});
```

</details>

<br/><br/>

## ⚪ ️3.2 変更する可能性が低い属性に基づいてHTML要素をクエリする

:white_check_mark: **こうしましょう:** CSSセレクターやフォームラベルのようにグラフィックの変更にも耐える可能性がある属性に基づいてHTML要素をクエリします。指定された要素にそのような属性がない場合、 'test-id-submit-button' のような専用のテスト属性を作成します。この方法だと、機能/ロジックテストは外観の変更によって壊れることがなくなるだけでなく、この要素と属性がテストで使用され、そのため削除されるべきではないことがチーム全体に明確になります。

<br/>

❌ **さもなくば:** 多くのコンポーネント、ロジック、サービスにわたるログイン機能をテストしたいとき、準備は完璧 — スタブ、スパイ、Ajaxコールが孤立しています。すべては完璧に見えます。しかしデザイナーがdivのCSSクラスを 'thick-border' から 'thin-border' に変更したためにテストが失敗します。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しいやり方の例: テスト用に専用の属性を使用して要素をクエリ

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Examples with React")

```html
// マークアップコード（Reactコンポーネントの一部）
<h3>
  <Badge pill className="fixed_badge" variant="dark">
    <span data-test-id="errorsLabel">{value}</span>
    <!-- 属性 data-test-id に注目 -->
  </Badge>
</h3>
```

```javascript
// この例はreact-testing-libraryを使用しています
test("Whenever no data is passed to metric, show 0 as default", () => {
  // Arrange
  const metricValue = undefined;

  // Act
  const { getByTestId } = render(<dashboardMetric value={undefined} />);

  expect(getByTestId("errorsLabel").text()).toBe("0");
});
```

<br/>

## :thumbsdown: アンチパターン例: CSS属性に依存する

```html
<!-- マークアップコード（Reactコンポーネントの一部） -->
<span id="metric" className="d-flex-column">{value}</span>
<!-- デザイナーがクラスを変更したらどうしますか？ -->
```

```javascript
// この例はenzymeを使用しています
test("Whenever no data is passed, error metric shows zero", () => {
  // ...

  expect(wrapper.find("[className='d-flex-column']").text()).toBe("0");
});
```

</details>

<br/>

## ⚪ ️3.3 可能な限り、リアルで完全にレンダリングされたコンポーネントでテストする

:white_check_mark: **こうしましょう:** サイズが適切である限り、ユーザーが行うようにコンポーネントを外からテストし、UIを完全にレンダリングし、それに対して操作を行い、レンダリングされたUIが期待通りに動作することをアサートします。すべての種類のモック、部分的および浅いレンダリングを避けます — このアプローチは、詳細の欠如によるバグの見落としや、テストが内部に干渉するためメンテナンスを難しくする可能性があります（「ブラックボックステストを好む」を参照）。もし子コンポーネントの一つが著しく動作を遅くしたり（例: アニメーション）、セットアップを複雑にしたりする場合は、明示的に偽のものに置き換えることを検討してください。

それに加えて、注意を要する言葉の一つがあります：この技術は、適切なサイズの子コンポーネントをパックしている小規模/中規模のコンポーネントに対して機能します。あまりに多くの子を持つコンポーネントを完全にレンダリングすることは、テストの失敗（根本原因の分析）についての説明を困難にしすぎることがあり、あまりにも遅くなる可能性があります。そのような場合、その大きな親コンポーネントに対してはいくつかのテストを行い、その子に対しては多くのテストを行います。

<br/>

❌ **さもなくば:** コンポーネントのプライベートメソッドを呼び出し、その内部状態をチェックすることによって、コンポーネントの内部をつつくとき、コンポーネントの実装をリファクタリングするときにすべてのテストをリファクタリングする必要があります。このレベルのメンテナンスを行う能力がありますか？

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: 完全にレンダリングされたコンポーネントをリアルに扱う

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Examples with React") ![](https://img.shields.io/badge/🔧%20Example%20using%20Enzyme-blue.svg "Examples with Enzyme")

```javascript
class Calendar extends React.Component {
  static defaultProps = { showFilters: false };

  render() {
    return (
      <div>
        A filters panel with a button to hide/show filters
        <FiltersPanel showFilter={showFilters} title="Choose Filters" />
      </div>
    );
  }
}

// 例はReact & Enzymeを使用
test("リアルなアプローチ: フィルターを表示するためにクリックすると、フィルターが表示される", () => {
  // Arrange
  const wrapper = mount(<Calendar showFilters={false} />);

  // Act
  wrapper.find("button").simulate("click");

  // Assert
  expect(wrapper.text().includes("Choose Filter"));
  // ユーザーはこの要素に次のようにアプローチする: by text
});
```

### :thumbsdown: アンチパターン例: 浅いレンダリングでモックする

```javascript
test("浅い/モックされたアプローチ: フィルターを表示するためにクリックすると、フィルターが表示される", () => {
  // Arrange
  const wrapper = shallow(<Calendar showFilters={false} title="Choose Filter" />);

  // Act
  wrapper
    .find("filtersPanel")
    .instance()
    .showFilters();
  // 内部に直接アクセスし、UIをスキップし、メソッドを呼び出します。ホワイトボックスアプローチ

  // Assert
  expect(wrapper.find("Filter").props()).toEqual({ title: "Choose Filter" });
  // もしプロップ名を変更したり、関連するものを何も渡さなかったらどうなりますか？
});
```

</details>

<br/>

## ⚪ ️3.4 スリープせず、フレームワークの組み込みサポートを使って非同期イベントを処理し、可能な限り高速化する

:white_check_mark: **こうしましょう:** テスト対象のユニットの完了時間が不明である場合が多くあります（例: アニメーションが要素の出現を遅延させる）。その場合、スリープ（例: setTimeOut）を避け、ほとんどのプラットフォームが提供するより決定論的なメソッドを利用します。一部のライブラリでは操作を待つことが許可されています（例: [Cypress cy.request('url')](https://docs.cypress.io/guides/references/best-practices.html#Unnecessary-Waiting)）。他は[@testing-library/dom メソッド wait(expect(element))](https://testing-library.com/docs/guide-disappearance)のように待機用のAPIを提供しています。よりエレガントな方法としては、APIのような遅いリソースをスタブ化し、レスポンスのタイミングが決定論的になったときにコンポーネントを明示的に再レンダリングすることもあります。外部コンポーネントがスリープする場合、[時計を急がせる](https://jestjs.io/docs/en/timer-mocks)ことが有用な場合もあります。スリープはテストを遅くしたり（短い時間を待つときの場合）危険にしたりするため避けるべきパターンです。スリープやポーリングが避けられず、テストフレームワークのサポートがない場合は、[wait-for-expect](https://www.npmjs.com/package/wait-for-expect)のようなnpmライブラリが半決定論的な解決策を提供するのに役立つことがあります。
<br/>

❌ **さもなくば:** 長時間スリープする場合、テストは桁違いに遅くなります。小さな数でスリープしようとすると、テスト対象のユニットがタイムリーに反応しなかった場合にテストが失敗します。つまり、フレーク性と悪いパフォーマンス間のトレードオフに帰結します。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: 非同期操作が完了するときにのみ解決するE2E API (Cypress)

![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Using Cypress to illustrate the idea")
![](https://img.shields.io/badge/🔧%20Example%20using%20React%20Testing%20Library-blue.svg "Examples with react-testing-library")

```javascript
// Cypressを使用
cy.get("#show-products").click(); // ナビゲート
cy.wait("@products"); // ルートが表示されるのを待つ
// この行はルートが準備完了のときにのみ実行されます
```

### :clap: 正しい例: DOM要素を待機するテストライブラリ

```javascript
// @testing-library/dom
test("映画タイトルが表示される", async () => {
  // 要素は初期状態では存在しない...

  // 表示を待つ
  await wait(() => {
    expect(getByText("the lion king")).toBeInTheDocument();
  });

  //表示を待って要素を返す
  const movie = await waitForElement(() => getByText("the lion king"));
});
```

### :thumbsdown: アンチパターン例: 独自のスリープコード

```javascript
test("映画タイトルが表示される", async () => {
  // 要素は初期状態では存在しない...

  // 独自の待機ロジック（注意: 単純すぎ、タイムアウトなし）
  const interval = setInterval(() => {
    const found = getByText("the lion king");
    if (found) {
      clearInterval(interval);
      expect(getByText("the lion king")).toBeInTheDocument();
    }
  }, 100);

  // 出現を待って要素を返す
  const movie = await waitForElement(() => getByText("the lion king"));
});
```

</details>

<br/>

## ⚪ ️3.5 コンテンツがネットワークを介してどのように配信されるかを観察する

![](https://img.shields.io/badge/🔧%20Example%20using%20Google%20LightHouse-blue.svg "Examples with Lighthouse")

✅ **こうしましょう:** 実際のネットワーク下でのページロードが最適化されていることを保証するアクティブモニターを適用します。これには、ページロードが遅かったりミニファイされていないバンドルなど、UXに関する懸念が含まれます。インスペクションツールの市場は豊富で、[pingdom](https://www.pingdom.com/)やAWS CloudWatch、[gcp StackDriver](https://cloud.google.com/monitoring/uptime-checks/)などの基本的なツールは、サーバーが存続し、合理的なSLAの下で応答するかどうかを監視するために簡単に設定できます。これだけでは間違いが発生する可能性がある多くの状況を網羅できないため、フロントエンドに特化し、よりリッチな分析を行うツールを選ぶことが望ましいです（例: [lighthouse](https://developers.google.com/web/tools/lighthouse/)、[pagespeed](https://developers.google.com/speed/pagespeed/insights/)）。焦点はUXに直接影響を与える症状や指標、例えばページロード時間、[意味のあるペイント](https://scotch.io/courses/10-web-performance-audit-tips-for-your-next-billion-users-in-2018/fmp-first-meaningful-paint)、[ページの対話可能になるまでの時間(TTI)](https://calibreapp.com/blog/time-to-interactive/)などに置くべきです。加えて、コンテンツが圧縮されているか、最初のバイトまでの時間、画像の最適化、合理的なDOMサイズの確保、SSLなどの技術的な原因を監視することも重要です。これらのリッチなモニターを開発中、CIの一部として、そして最も重要なのは、プロダクションのサーバー/CDNを24時間365日監視することが推奨されます。

<br/>

❌ **さもなくば:** UIの制作に多大な注意を払い、100%の機能テストが合格し、洗練されたバンドルを行ったにもかかわらず、CDNの誤設定によりUXがひどく遅いと気付くのは失望です。

<br/>

<details><summary>✏ <b>コード例</b></summary>

### :clap: 正しい例: Lighthouseページロード検査レポート

![](/assets/lighthouse2.png "Lighthouse page load inspection report")

</details>

<br/>

## ⚪ ️3.6 バックエンドAPIのような不安定で遅いリソースをスタブ化する

:white_check_mark: **こうしましょう:** メインストリームのテスト（E2Eテストではない）をコーディングする際には、バックエンドAPIのように責任と制御を超えたリソースを関与させるのは避け、代わりにスタブ（つまりテストダブル）を使用します。実際には、APIへの実際のネットワーク呼び出しの代わりに、[Sinon](https://sinonjs.org/)や[Test doubles](https://www.npmjs.com/package/testdouble)のようなテストダブルライブラリを使ってAPIのレスポンスをスタブ化します。主な利点はフレーク性を防ぐことです。テストやステージングAPIは高い安定性がないため、時々、コンポーネントがしっかり動作しているにもかかわらず、テストが失敗することがあります（プロダクション環境はテスト目的で設計されておらず、通常リクエストを制限しています）。これを行うことで、データが見つからなかった場合やAPIがエラーを投げた場合のような、コンポーネントの動作を駆動するべき様々なAPIの動作をシミュレートできます。加えて、ネットワーク呼び出しはテストを大幅に遅くします。

<br/>

❌ **さもなくば:** 平均的なテストは数ミリ秒以内に終了しますが、典型的なAPI呼び出しは100ms以上です。これにより、各テストは約20倍遅くなります。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: API呼び出しのスタブまたはインターセプト

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Examples with React") ![](https://img.shields.io/badge/🔧%20Example%20using%20React%20Testing%20Library-blue.svg "Examples with react-testing-library")

```javascript
// テスト対象のユニット
export default function ProductsList() {
  const [products, setProducts] = useState(false);

  const fetchProducts = async () => {
    const products = await axios.get("api/products");
    setProducts(products);
  };

  useEffect(() => {
    fetchProducts();
  }, []);

  return products ? <div>{products}</div> : <div data-test-id="no-products-message">No products</div>;
}

// テスト
test("商品が存在しない場合、適切なメッセージを表示する", () => {
  // Arrange
  nock("api")
    .get(`/products`)
    .reply(404);

  // Act
  const { getByTestId } = render(<ProductsList />);

  // Assert
  expect(getByTestId("no-products-message")).toBeTruthy();
});
```

</details>

<br/>

## ⚪ ️3.7 システム全体に及ぶエンドツーエンドテストはごく少数にする

:white_check_mark: **こうしましょう:** エンドツーエンド（E2E）は通常、実際のブラウザを使ったUIのみのテストを意味しますが（3.6を参照）、他の人々にとっては実際のバックエンドを含むシステム全体に及ぶテストを意味します。後者のタイプのテストは非常に価値があり、フロントエンドとバックエンドの統合バグをカバーしているため、データスキーマの誤解によって起こる可能性のある問題を防ぎます。また、バックエンド間の統合問題を発見する効率的な方法であり（例: マイクロサービスAがマイクロサービスBに誤ったメッセージを送信する）、デプロイメントの失敗を検出するためにも利用できます。UIフレームワークの[Cypress](https://www.cypress.io/)や[Puppeteer](https://github.com/GoogleChrome/puppeteer)のように、バックエンドのE2Eテストのための親しみやすく成熟したフレームワークは存在しません。このようなテストの欠点は、多くのコンポーネントを持つ環境の構成に高コストがかかること、そして多くの場合その脆さです。50のマイクロサービスのうち1つでも失敗すれば、E2E全体が失敗してしまいます。そのため、この手法は控えめに使用し、1〜10種類程度に留めるべきです。それでも、少数のE2Eテストであっても、デプロイメントと統合の不具合を検出する能力は高いです。プロダクションに近いステージング環境でこれらを実行することが推奨されます。

<br/>

❌ **さもなくば:** UIが自機能のテストに多大な投資をしても、バックエンドが返したペイロード（UIが扱うべきデータスキーマ）が期待とは大きく異なることに気付くのが非常に遅れるかもしれません。

<br/>

## ⚪ ️3.8 ログイン認証情報を再利用してE2Eテストを高速化する

:white_check_mark: **こうしましょう:** 実際のバックエンドを含むE2Eテストで、API呼び出しに有効なユーザートークンが必要な場合、毎回ユーザーを作成してログインさせるようなレベルまでテストを分離するのは得策ではありません。代わりに、テスト実行開始前に一度だけログインし（before-allフックで）、トークンをローカルストレージに保存し、リクエスト間で再利用します。これはテストの基本原則の1つ、リソースの結合なしにテストを自律的に保つというものを違反しているように見えますが、E2Eテストでは性能が重要であり、個々のテストを開始する前に1〜3のAPIリクエストを生成することは、実行時間に大きな悪影響を与えるかもしれません。資格情報を再利用することは、テストが同じユーザーレコードで動作することを意味しません。ユーザーレコードに依存する（例: ユーザーの支払い履歴をテスト）場合は、それらのレコードをテストの一部として生成し、他のテストと共有しないようにしてください。また、バックエンドが偽装できることを忘れないでください。テストがフロントエンドに集中している場合は、それを分離してバックエンドAPIのスタブ化を検討する方が良い場合もあります（[3.6節](https://github.com/goldbergyoni/javascript-testing-best-practices#-%EF%B8%8F-36-stub-flaky-and-slow-resources-like-backend-apis)を参照）。

<br/>

❌ **さもなくば:** 200のテストケースがあり、ログインに100msかかると仮定すると、ログインを繰り返すだけで合計20秒かかります。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: before-allでログインし、before-eachではしない

![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Cypressを使ってアイデアを説明")

```javascript
let authenticationToken;

// すべてのテストが実行される前に行われる
before(() => {
  cy.request('POST', 'http://localhost:3000/login', {
    username: Cypress.env('username'),
    password: Cypress.env('password'),
  })
  .its('body')
  .then((responseFromLogin) => {
    authenticationToken = responseFromLogin.token;
  })
})

// 各テストが実行される前に行われる
beforeEach(setUser => () {
  cy.visit('/home', {
    onBeforeLoad (win) {
      win.localStorage.setItem('token', JSON.stringify(authenticationToken))
    },
  })
})

```

</details>

<br/>

## ⚪ ️3.9 サイトマップを巡回するだけのE2Eスモークテストを一つ持つ

:white_check_mark: **こうしましょう:** 本番モニタリングや開発時の正常性チェックのために、すべてのページ、または大部分のサイトページを訪れ、何も壊れていないことを確認する単一のE2Eテストを実行します。このタイプのテストは、執筆と保守が非常に簡単でありながら、機能的、ネットワーク的、およびデプロイメントの問題を含むあらゆる種類の障害を検出できるため、非常に高い投資対効果をもたらします。他のスモークおよび正常性チェックのスタイルは信頼性や網羅性が劣ります。オペレーションチームの一部はホームページだけをpingする（本番環境）、または多くの統合テストを実行する開発者は、パッケージングやブラウザの問題を発見しないことがあります。もちろん、スモークテストは機能テストの代替ではなく、単に素早い問題検出を目指すものです。

<br/>

❌ **さもなくば:** すべてが完璧に見えるかもしれません、すべてのテストが通過し、本番のヘルスチェックも良好ですが、Paymentコンポーネントにはパッケージングの問題があり、/Paymentルートだけがレンダリングされない状況があります。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: すべてのページを巡るスモークテスト

![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Cypressを使ってアイデアを説明")

```javascript
it("全ページでスモークテストを行うとき、すべて正常にロードされるべきである", () => {
  // Cypressを使って示していますが、任意のE2Eスイートで簡単に実装できます
  cy.visit("https://mysite.com/home");
  cy.contains("Home");
  cy.contains("https://mysite.com/Login");
  cy.contains("Login");
  cy.contains("https://mysite.com/About");
  cy.contains("About");
});
```

</details>

<br/>

## ⚪ ️3.10 テストをライブ共同作業ドキュメントとして公開する

:white_check_mark: **こうしましょう:** アプリの信頼性を向上させるだけでなく、テストはもう1つの魅力的な機会を提供します。それは、ライブのアプリドキュメントとして機能することです。テストは本質的に、技術的でなく製品/UXの言語で表現されるため、適切なツールを使用することで、開発者と顧客すべての仲間を大きく一致させるコミュニケーションアーティファクトとして役立つことができます。例えば、いくつかのフレームワークでは、人間が読みやすい言語を使ってフローと期待値（つまりテスト計画）を表現でき、製品管理者を含むあらゆるステークホルダーがテストを読み、承認し、協力できるので、テストはライブの要件ドキュメントになります。この手法は「受入テスト」とも呼ばれ、顧客が平易な言葉で受け入れ基準を定義できるようにします。これは[BDD（振る舞い駆動開発）](https://en.wikipedia.org/wiki/Behavior-driven_development)の最も純粋な形です。これを可能にする人気のフレームワークの1つが[Cucumber（JavaScript用のバージョンあり）](https://github.com/cucumber/cucumber-js)です。以下の例をご覧ください。もう1つの関連した機会として、[StoryBook](https://storybook.js.org/)は、UIコンポーネントをグラフィックカタログとして公開し、それぞれのコンポーネントの様々な状態をたどりながら、その見た目やその状態をトリガーする方法を提示することができます。これにより、製品の担当者にもアピールすることができ、主にそのコンポーネントを消費する開発者のためのライブドキュメントとして役立ちます。

❌ **さもなくば:** テストにトップリソースを投資した後、この投資を活用して大きな価値を得られないのは、ただの悲劇です。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: cucumber-jsを用いて人間の言葉でテストを記述する

![](https://img.shields.io/badge/🔨%20Example%20using%20Cucumber-blue.svg "Examples using Cucumber")

```javascript
// collaborateを使ったテストは、このように説明することができる。

Feature: Twitter new tweet

  I want to tweet something in Twitter

  @focus
  Scenario: Tweeting from the home page
    Given I open Twitter home
    Given I click on "New tweet" button
    Given I type "Hello followers!" in the textbox
    Given I click on "Submit" button
    Then I see message "Tweet saved"

```

### :clap: 正しい例: Storybookを使用してコンポーネント、その様々な状態と入力を視覚化する

![](https://img.shields.io/badge/🔨%20Example%20using%20StoryBook-blue.svg "Using StoryBook")

![alt text](assets/story-book.jpg "Storybook")

</details>

<br/><br/>

## ⚪ ️3.11 自動化ツールで視覚的な問題を検出する

:white_check_mark: **こうしましょう:** 変更がある場合にUIのスクリーンショットをキャプチャし、コンテンツの重なりや崩れといった視覚的な問題を検出するための自動化ツールをセットアップしましょう。これにより、正しいデータが用意されるだけでなく、ユーザーがそれを便利に見ることができるようになります。この手法は広く採用されているわけではありませんが、私たちのテストの思考法は機能テストに傾いているのに対し、視覚的な要素がユーザー体験であり、様々なデバイスタイプの存在によりいくつかの厄介なUIバグを見過ごすのは非常に簡単です。無料のツールでも基本を提供できます。つまり、人間の目による検査のためにスクリーンショットを生成・保存するということです。このアプローチは小規模なアプリには十分かもしれませんが、人間の労力を要求するあらゆる手動テストと同様に欠点があります。一方で、UIの問題を自動的に検出するのは非常に難しいため、この分野では'Visual Regression'が登場します。これは、古いUIと最新の変更を比較して違いを検出することでこのパズルを解決します。いくつかのOSS/無料ツールが基本的な機能を提供することができます（例: [wraith](https://github.com/BBC-News/wraith), [PhantomCSS](https://github.com/HuddleEng/PhantomCSS)）が、セットアップにかなりの時間がかかるかもしれません。商用のツール（例: [Applitools](https://applitools.com/), [Percy.io](https://percy.io/)）はさらに一歩進んで、インストールをスムーズにし、管理UI、アラート、'視覚的ノイズ'（例: 広告、アニメーション）を排除するスマートキャプチャー、問題を引き起こしたDOM/CSSの変更の根本原因分析といった高度な機能を搭載しています。

<br/>

❌ **さもなくば:** 素晴らしいコンテンツを表示し（100%のテストが合格）、瞬時にロードされるが、コンテンツエリアの半分が隠れているコンテンツページはどれほど良いでしょうか？

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: 提供され方が悪い典型的な視覚的回帰

![alt text](assets/amazon-visual-regression.jpeg "Amazonページの崩れ")

<br/>

### :clap: 正しい例: wraithを設定してUIスナップショットをキャプチャし比較する

![](https://img.shields.io/badge/🔨%20Example%20using%20Wraith-blue.svg "Using Wraith")

```
​# 必要なだけドメインを追加します。キーがラベルとして機能します​

domains:
  english: "http://www.mysite.com"​

​# 以下にスクリーンの幅を入力します。いくつかの例を示します​

screen_widths:
  - 600​
  - 768​
  - 1024​
  - 1280​

​# 以下にページのURLパスを入力します。いくつかの例を示します​
paths:
  about:
    path: /about
    selector: '.about'​
  subscribe:
    path: /subscribe
    selector: '.subscribe'​
```

### :clap: 正しい例: Applitoolsを使用してスナップショットの比較やその他の高度な機能を利用する

![](https://img.shields.io/badge/🔨%20Example%20using%20AppliTools-blue.svg "Applitoolsを使用した例") ![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Cypressを使用してアイデアを示す")

```javascript
import * as todoPage from "../page-objects/todo-page";

describe("visual validation", () => {
  before(() => todoPage.navigate());
  beforeEach(() => cy.eyesOpen({ appName: "TAU TodoMVC" }));
  afterEach(() => cy.eyesClose());

  it("should look good", () => {
    cy.eyesCheckWindow("empty todo list"); // 空のToDoリストを確認
    todoPage.addTodo("Clean room");
    todoPage.addTodo("Learn javascript");
    cy.eyesCheckWindow("two todos"); // 2つのToDoを確認
    todoPage.toggleTodo(0);
    cy.eyesCheckWindow("mark as completed"); // 完了としてマークをチェック
  });
});
```

</details>

<br/><br/>

# Section 4️⃣: Measuring Test Effectiveness

<br/><br/>

## ⚪ ️ 4.1 Get enough coverage for being confident, ~80% seems to be the lucky number

:white_check_mark: **Do:** The purpose of testing is to get enough confidence for moving fast, obviously the more code is tested the more confident the team can be. Coverage is a measure of how many code lines (and branches, statements, etc) are being reached by the tests. So how much is enough? 10–30% is obviously too low to get any sense about the build correctness, on the other side 100% is very expensive and might shift your focus from the critical paths to the exotic corners of the code. The long answer is that it depends on many factors like the type of application — if you’re building the next generation of Airbus A380 than 100% is a must, for a cartoon pictures website 50% might be too much. Although most of the testing enthusiasts claim that the right coverage threshold is contextual, most of them also mention the number 80% as a thumb of a rule ([Fowler: “in the upper 80s or 90s”](https://martinfowler.com/bliki/TestCoverage.html)) that presumably should satisfy most of the applications.

Implementation tips: You may want to configure your continuous integration (CI) to have a coverage threshold ([Jest link](https://jestjs.io/docs/en/configuration.html#collectcoverage-boolean)) and stop a build that doesn’t stand to this standard (it’s also possible to configure threshold per component, see code example below). On top of this, consider detecting build coverage decrease (when a newly committed code has less coverage) — this will push developers raising or at least preserving the amount of tested code. All that said, coverage is only one measure, a quantitative based one, that is not enough to tell the robustness of your testing. And it can also be fooled as illustrated in the next bullets

<br/>

❌ **Otherwise:** Confidence and numbers go hand in hand, without really knowing that you tested most of the system — there will also be some fear and fear will slow you down

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Example: A typical coverage report

![alt text](assets/bp-18-yoni-goldberg-code-coverage.png "A typical coverage report")

<br/>

### :clap: Doing It Right Example: Setting up coverage per component (using Jest)

![](https://img.shields.io/badge/🔨%20Example%20using%20Jest-blue.svg "Using Jest")

![alt text](assets/bp-18-code-coverage2.jpeg "Setting up coverage per component (using Jest)")

</details>

<br/><br/>

## ⚪ ️ 4.2 Inspect coverage reports to detect untested areas and other oddities

:white_check_mark: **Do:** Some issues sneak just under the radar and are really hard to find using traditional tools. These are not really bugs but more of surprising application behavior that might have a severe impact. For example, often some code areas are never or rarely being invoked — you thought that the ‘PricingCalculator’ class is always setting the product price but it turns out it is actually never invoked although we have 10000 products in DB and many sales… Code coverage reports help you realize whether the application behaves the way you believe it does. Other than that, it can also highlight which types of code is not tested — being informed that 80% of the code is tested doesn’t tell whether the critical parts are covered. Generating reports is easy — just run your app in production or during testing with coverage tracking and then see colorful reports that highlight how frequent each code area is invoked. If you take your time to glimpse into this data — you might find some gotchas
<br/>

❌ **Otherwise:** If you don’t know which parts of your code are left un-tested, you don’t know where the issues might come from

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :thumbsdown: Anti-Pattern Example: What’s wrong with this coverage report?

Based on a real-world scenario where we tracked our application usage in QA and find out interesting login patterns (Hint: the amount of login failures is non-proportional, something is clearly wrong. Finally it turned out that some frontend bug keeps hitting the backend login API)

![alt text](assets/bp-19-coverage-yoni-goldberg-nodejs-consultant.png "What’s wrong with this coverage report?")

</details>

<br/><br/>

## ⚪ ️ 4.3 Measure logical coverage using mutation testing

:white_check_mark: **Do:** The Traditional Coverage metric often lies: It may show you 100% code coverage, but none of your functions, even not one, return the right response. How come? it simply measures over which lines of code the test visited, but it doesn’t check if the tests actually tested anything — asserted for the right response. Like someone who’s traveling for business and showing his passport stamps — this doesn’t prove any work done, only that he visited few airports and hotels.

Mutation-based testing is here to help by measuring the amount of code that was actually TESTED not just VISITED. [Stryker](https://stryker-mutator.io/) is a JavaScript library for mutation testing and the implementation is really neat:

(1) it intentionally changes the code and “plants bugs”. For example the code newOrder.price===0 becomes newOrder.price!=0. This “bugs” are called mutations

(2) it runs the tests, if all succeed then we have a problem — the tests didn’t serve their purpose of discovering bugs, the mutations are so-called survived. If the tests failed, then great, the mutations were killed.

Knowing that all or most of the mutations were killed gives much higher confidence than traditional coverage and the setup time is similar
<br/>

❌ **Otherwise:** You’ll be fooled to believe that 85% coverage means your test will detect bugs in 85% of your code

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :thumbsdown: Anti-Pattern Example: 100% coverage, 0% testing

![](https://img.shields.io/badge/🔨%20Example%20using%20Stryker-blue.svg "Using Stryker")

```javascript
function addNewOrder(newOrder) {
  logger.log(`Adding new order ${newOrder}`);
  DB.save(newOrder);
  Mailer.sendMail(newOrder.assignee, `A new order was places ${newOrder}`);

  return { approved: true };
}

it("Test addNewOrder, don't use such test names", () => {
  addNewOrder({ assignee: "John@mailer.com", price: 120 });
}); //Triggers 100% code coverage, but it doesn't check anything
```

<br/>

### :clap: Doing It Right Example: Stryker reports, a tool for mutation testing, detects and counts the amount of code that is not tested (Mutations)

![alt text](assets/bp-20-yoni-goldberg-mutation-testing.jpeg "Stryker reports, a tool for mutation testing, detects and counts the amount of code that is not tested (Mutations)")

</details>

<br/><br/>

## ⚪ ️4.4 Preventing test code issues with Test linters

:white_check_mark: **Do:** A set of ESLint plugins were built specifically for inspecting the tests code patterns and discover issues. For example, [eslint-plugin-mocha](https://www.npmjs.com/package/eslint-plugin-mocha) will warn when a test is written at the global level (not a son of a describe() statement) or when tests are [skipped](https://mochajs.org/#inclusive-tests) which might lead to a false belief that all tests are passing. Similarly, [eslint-plugin-jest](https://github.com/jest-community/eslint-plugin-jest) can, for example, warn when a test has no assertions at all (not checking anything)

<br/>

❌ **Otherwise:** Seeing 90% code coverage and 100% green tests will make your face wear a big smile only until you realize that many tests aren’t asserting for anything and many test suites were just skipped. Hopefully, you didn’t deploy anything based on this false observation

<br/>
<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :thumbsdown: Anti-Pattern Example: A test case full of errors, luckily all are caught by Linters

```javascript
describe("Too short description", () => {
  const userToken = userService.getDefaultToken() // *error:no-setup-in-describe, use hooks (sparingly) instead
  it("Some description", () => {});//* error: valid-test-description. Must include the word "Should" + at least 5 words
});

it.skip("Test name", () => {// *error:no-skipped-tests, error:error:no-global-tests. Put tests only under describe or suite
  expect("somevalue"); // error:no-assert
});

it("Test name", () => {*//error:no-identical-title. Assign unique titles to tests
});
```

</details>

<br/><br/>

# Section 5️⃣: CI 及びその他の品質基準

<br/><br/>

## ⚪ ️ 5.1 リンターを充実させ、リントに問題がある時はビルドを止める

:white_check_mark: **こうしましょう:** リンターはフリーランチです。5分のセットアップで、コードを守る自動操縦装置を無料で手に入れることができ、重要な問題をキャッチすることができます。 リンティングが装飾のためのものだった時代はもう終わりました。現在ではリンターは、正しくスローされないことによって情報が失われてしまうエラーのような深刻な問題を検知することができます。 [ESLint standard](https://www.npmjs.com/package/eslint-plugin-standard) や [Airbnb style](https://www.npmjs.com/package/eslint-config-airbnb) のような基本的なルールセットに加え、[eslint-plugin-chai-expect](https://www.npmjs.com/package/eslint-plugin-chai-expect) はアサーションのないテストを、[eslint-plugin-promise](https://www.npmjs.com/package/eslint-plugin-promise?activeTab=readme) は resolve しない promise を、[eslint-plugin-security](https://www.npmjs.com/package/eslint-plugin-security?activeTab=readme) は DOS 攻撃に使われる可能性のある正規表現を、[eslint-plugin-you-dont-need-lodash-underscore](https://www.npmjs.com/package/eslint-plugin-you-dont-need-lodash-underscore) は Lodash の`_.map(…)`ような V8 コアメソッドの一部であるユーティリティーライブラリメソッドをコードが使用している場合に警告することができます。
<br/>

❌ **さもなくば:** 雨の日に、本番環境がクラッシュし続けているのに、ログにはエラーのスタックトレースが表示されていない場合を考えてみましょう。何が起こったのでしょうか？あなたのコードが誤ってエラーではないオブジェクトを投げてしまい、スタックトレースが失われたのです。そんなことが起こった日には、壁に頭を打ち付けたくなりますよね。5分間のリンターのセットアップでこのタイポを検出し、あなたの一日を救うことができます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :thumbsdown: アンチパターン例: 間違ったエラーオブジェクトが誤ってスローされ、このエラーのスタックトレースは表示されません。幸運なことに、ESLint は次の本番環境でのバグをキャッチします。

![alt text](assets/bp-21-yoni-goldberg-eslint.jpeg "間違ったエラーオブジェクトが誤ってスローされ、このエラーのスタックトレースは表示されません。幸運なことに、ESLint は次の本番環境でのバグをキャッチします")

</details>

<br/><br/>

## ⚪ ️ 5.2 ローカルでの開発者とCIのフィードバックループを短くする

:white_check_mark: **こうしましょう:** テスト、リンティング、脆弱性チェックなどの品質検査がピカイチのCIを使っていますか？ 開発者がパイプラインをローカルで実行し即座にフィードバックを得られるようにして、[フィードバックループ](https://www.gocd.org/2016/03/15/are-you-ready-for-continuous-delivery-part-2-feedback-loops/) を短くしましょう。なぜか？ 効率的なテストプロセスは、多くの反復的なループを構成しているからです。(1)トライアウト -> (2)フィードバック -> (3)リファクタリング。フィードバックが早ければ早いほど、開発者はモジュールごとに改善の反復回数が増え、結果を完璧にすることができます。逆に、フィードバックが遅くなると、1日にできる改善の反復回数が少なくなり、チームはすでに別のトピック/タスク/モジュールに進んでしまい、そのモジュールを改善する気にならないかもしれません。

実際に、いくつかのCIベンダー（例：[CircleCI local CLI](https://circleci.com/docs/2.0/local-cli/)) は、パイプラインをローカルで実行することができます。[wallaby](https://wallabyjs.com/) のようないくつかの商用ツールは、開発者のプロトタイプとして非常に価値のあるテスト用のインサイトを提供しています。または、すべての品質チェックのコマンド（例：テスト、リント、脆弱性チェック）を実行するnpmスクリプトをpackage.jsonに追加するだけでも構いません。並列化のために [concurrently](https://www.npmjs.com/package/concurrently) のようなツールを使用し、ツールの1つが失敗した場合でも0以外の終了コードを返すようにしましょう。開発者は「npm run quality」などのコマンドを実行するだけで、即座にフィードバックを得ることができます。githookを使って品質チェックに失敗したときにコミットを中止することも検討してみましょう([husky](https://github.com/typicode/husky) が使えます）。
<br/>

❌ **さもなくば:** 品質チェックの結果がコードの翌日に出るようでは、テストは開発の一部ではなく、後付の形式的な成果物になってしまいます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: コード品質のチェックを行うnpmスクリプトは、手動または開発者が新しいコードをプッシュしようとしているときに自動ですべて並行して実行されます。

```javascript
"scripts": {
    "inspect:sanity-testing": "mocha **/**--test.js --grep \"sanity\"",
    "inspect:lint": "eslint .",
    "inspect:vulnerabilities": "npm audit",
    "inspect:license": "license-checker --failOn GPLv2",
    "inspect:complexity": "plato .",

    "inspect:all": "concurrently -c \"bgBlue.bold,bgMagenta.bold,yellow\" \"npm:inspect:quick-testing\" \"npm:inspect:lint\" \"npm:inspect:vulnerabilities\" \"npm:inspect:license\""
  },
  "husky": {
    "hooks": {
      "precommit": "npm run inspect:all",
      "prepush": "npm run inspect:all"
    }
}

```

</details>

<br/><br/>

## ⚪ ️5.3 本番環境のミラーでのe2eテストの実施

:white_check_mark: **こうしましょう:** エンドツーエンド (e2e) テスティングは、すべてのCIパイプラインの主な課題です - 本番環境と同一の一時的な環境を、関連するすべてのクラウド・サービスと一緒にその場で作成するのは面倒でコストがかかります。最適な妥協案を見つけるのがあなたの仕事です: [Docker-compose](https://serverless.com/) は、1つのプレーンなテキストファイルを使用して、同一のコンテナで隔離されたdocker環境を作ることができますが、裏側の技術（例: ネットワークやデプロイメントモデル）は、実際の本番環境とは異なります。[`AWS Local`](https://github.com/localstack/localstack) と組み合わせることで、実際のAWSサービスのスタブを利用することができます。サーバーレスにした場合は、[serverless](https://serverless.com/) や [AWS SAM](https://docs.aws.amazon.com/lambda/latest/dg/serverless_app.html) などの複数のフレームワークにより、FaaSコードのローカル起動が可能になります。

巨大なKubernetesのエコシステムでは、多くの新しいツールが頻繁に発表されていますが、ローカルおよびCI-ミラーリングのための標準的で便利なツールはまだ公式化されていません。1つのアプローチとして [Minikube](https://kubernetes.io/docs/setup/minikube/) や [MicroK8s](https://microk8s.io/) などのツールを使って`最小化されたKubernetes`を実行する方法があります。これらのツールは本物に似ていますが、オーバーヘッドが少ないのが特徴です。 他のアプローチとしては、リモートの`実際のKubernetes`上でテストする方法があります。いくつかのCIプロバイダー(例：[Codefresh](https://codefresh.io/)) はKubernetes環境とネイティブに統合されており、実際のKubernetes上でCIパイプラインを簡単に実行できます。他のプロバイダーはリモートのKubernetesに対してカスタムスクリプトを実行できます。
<br/>

❌ **さもなくば:** 本番環境とテスト環境で異なるテクノロジーを使用すると、2つのデプロイメントモデルを維持する必要があり、開発者と運用チームが分離されてしまいます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 例: CIパイプライン上でその場でKubernetesクラスタを生成する <a href="https://container-solutions.com/dynamic-environments-kubernetes/" data-href="https://container-solutions.com/dynamic-environments-kubernetes/" class="markup--anchor markup--p-anchor" rel="noopener nofollow" target="_blank">([出典: Dynamic-environments Kubernetes](https://container-solutions.com/dynamic-environments-kubernetes/))</a>

<pre name="38d9" id="38d9" class="graf graf--pre graf-after--p">deploy:<br>stage: deploy<br>image: registry.gitlab.com/gitlab-examples/kubernetes-deploy<br>script:<br>- ./configureCluster.sh $KUBE_CA_PEM_FILE $KUBE_URL $KUBE_TOKEN<br>- kubectl create ns $NAMESPACE<br>- kubectl create secret -n $NAMESPACE docker-registry gitlab-registry --docker-server="$CI_REGISTRY" --docker-username="$CI_REGISTRY_USER" --docker-password="$CI_REGISTRY_PASSWORD" --docker-email="$GITLAB_USER_EMAIL"<br>- mkdir .generated<br>- echo "$CI_BUILD_REF_NAME-$CI_BUILD_REF"<br>- sed -e "s/TAG/$CI_BUILD_REF_NAME-$CI_BUILD_REF/g" templates/deals.yaml | tee ".generated/deals.yaml"<br>- kubectl apply --namespace $NAMESPACE -f .generated/deals.yaml<br>- kubectl apply --namespace $NAMESPACE -f templates/my-sock-shop.yaml<br>environment:<br>name: test-for-ci</pre>

</details>

<br/><br/>

## ⚪ ️5.4 テスト実行を並列化する

:white_check_mark: **こうしましょう:** 正しい方法で行えば、テストは24時間365日ほぼ即座にフィードバックを提供してくれる友人です。 しかし、実践的には、1つのスレッドで500のCPUバウンドのユニットテストを実行するには時間がかかりすぎます。 幸いなことに、最新のテストランナーやCIプラットフォーム（[Jest](https://github.com/facebook/jest) や [AVA](https://github.com/avajs/ava) 、[Mocha extensions](https://github.com/yandex/mocha-parallel-tests) のような）では、テストを複数のプロセスに並列化し、フィードバックまでの時間を大幅に改善することができます。CIベンダーの中には、テストをコンテナ間（！）で並列化するものもあり、これによりフィードバックループがさらに短縮されます。ローカルで複数のプロセスを使用しても、クラウドのCLIで複数のマシンを使用しても、それぞれが異なるプロセスで実行される可能性があるため、並列化によってテストを自律的に維持する必要があります。

❌ **さもなくば:** 新しいコードをプッシュしてから1時間後にテストの結果が出るのでは、その頃には既に次の機能のコーディングをしているでしょうから、テストの効果を半減させてしまいます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例: テストの並列化により、Mocha parallelとJestは従来のMochaを簡単に凌駕しました ([出典: JavaScript Test-Runners Benchmark](https://medium.com/dailyjs/javascript-test-runners-benchmark-3a78d4117b4))

![alt text](assets/bp-24-yonigoldberg-jest-parallel.png "テストの並列化により、Mocha parallelとJestは従来のMochaを簡単に凌駕しました (出典: JavaScript Test-Runners Benchmark)")

</details>

<br/><br/>

## ⚪ ️5.5 ライセンスチェックと盗用チェックで法的問題を回避しよう

:white_check_mark: **こうしましょう:** ライセンスや盗用の問題は、おそらく今は主な関心事ではないでしょうが、10分でこの項目を満たせるとしたらどうでしょう？ [license check](https://www.npmjs.com/package/license-checker) や [plagiarism check](https://www.npmjs.com/package/plagiarism-checker) （商用利用可能な無料プラン）などのnpmパッケージは、CIパイプラインに簡単に組み込むことができ、制限付きライセンスの依存関係や、Stack Overflowからコピーペーストされたコードなど、明らかに著作権に違反しているコードを検査することができます。

❌ **さもなくば:** 意図せずに不適切なライセンスのパッケージを使用したり、商用コードをコピーペーストしたりして、法的な問題が発生する可能性があります。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 正しい例:

```javascript
// license-checker をローカル又はCI環境にインストールしてください
npm install -g license-checker

// すべてのライセンスをスキャンし、未承認のライセンスを見つけた場合は0以外の終了コードで失敗するようにします。CI環境では、この失敗をキャッチして、ビルドを停止する必要があります。
license-checker --summary --failOn BSD

```

<br/>

![alt text](assets/bp-25-nodejs-licsense.png)

</details>

<br/><br/>

## ⚪ ️5.6 脆弱性のある依存関係を常に検査する

:white_check_mark: **こうしましょう:** Expressなどの最も信頼できる依存関係であっても、既知の脆弱性があります。これは、[npm audit](https://docs.npmjs.com/getting-started/running-a-security-audit) のようなコミュニティツールや、[snyk](https://snyk.io/) （無料のコミュニティバージョンもあります）のような商用ツールを使えば、簡単に解決できます。これらのツールは、ビルドのたびにCIから起動することができます。

❌ **さもなくば:** 専用のツールを使わずにコードを脆弱性から守るには、新たな脅威に関するオンラインの情報を常にチェックする必要があります。非常に面倒です。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 例: NPM Audit の結果

![alt text](assets/bp-26-npm-audit-snyk.png "NPM Audit result")

</details>

<br/><br/>

## ⚪ ️5.7 依存関係のアップデートを自動化する

:white_check_mark: **こうしましょう:** Yarnとnpmのpackage-lock.jsonの導入は、深刻な課題をもたらしました（地獄への道は善意で敷かれています） - 標準では、パッケージはもはや更新されません。‘npm install’ と ‘npm update’ で何度もデプロイを繰り返すチームでも、新しいアップデートは得られません。その結果、依存パッケージのバージョンは良くても標準以下になり、最悪の場合は脆弱なコードになります。現在、チームは手動でpackage.jsonを更新するために開発者の善意と記憶力に頼っていたり、[ncu]((https://www.npmjs.com/package/npm-check-updates)) のようなツールを手動で使用しています。 より確実な方法は、最も信頼性の高い依存関係のバージョンを取得するプロセスを自動化することですが、まだ銀の弾丸のような解決策はありません。ただ、可能性のある自動化の道は2つあります:

(1) CIで、[‘npm outdated’](https://docs.npmjs.com/cli/outdated) や‘npm-check-updates (ncu)’などのツールを使って、古い依存関係を持つビルドを失敗させます。これにより、開発者に依存関係の更新を強制することができます。

(2) コードをスキャンして、依存関係を更新したプルリクエストを自動的に作成する商用ツールを使用します。残る一つの興味深い問題は、依存関係の更新ポリシーをどうするかということです。- パッチごとに更新するとオーバーヘッドが大きくなりすぎますし、メジャーリリース直後に更新すると不安定なバージョンになってしまう可能性もあるでしょう（多くのパッケージがリリース後数日で脆弱性が発見されています。[eslint-scopeのインシデント](https://nodesource.com/blog/a-high-level-post-mortem-of-the-eslint-scope-security-incident/) をみてください）。

効率的なアップデートポリシーでは、いくつかの「権利確定期間」を設けることができます - ローカルが古くなったと判断する前に、コードを@latestよりもしばらく遅れたバージョンになるようにします（例：ローカルバージョンは1.3.1、リポジトリバージョンは1.3.8）。
<br/>

❌ **さもなくば:** 作成者によってリスクがあると明示的にタグ付けされたパッケージがプロダクションで実行されます。

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 例: [ncu](https://www.npmjs.com/package/npm-check-updates) は手動またはCIパイプライン上で、コードがどの程度最新バージョンから遅れているかを検出するために使用できます。

![alt text](assets/bp-27-yoni-goldberg-npm.png "ncu は手動またはCIパイプライン上で、コードがどの程度最新バージョンから遅れているかを検出するために使用できます")

</details>

<br/><br/>

## ⚪ ️ 5.8 その他、Nodeに関連のないCIのTips

:white_check_mark: **こうしましょう:** この記事は、Node JSに関連するか、少なくともNode JSで例示できるテストのアドバイスに焦点を当てています。ですがこの項目では、Nodeに関連しないけれどよく知られているCIのTipsをいくつかまとめて紹介します。

 <ol class="postList"><li name="e3e4" id="e3e4" class="graf graf--li graf-after--p">宣言型の構文を使用する。ほとんどのベンダーではこれが唯一の選択肢ですが、Jenkinsの古いバージョンでは、コードやUIを使用することができます。</li><li name="1fdc" id="1fdc" class="graf graf--li graf-after--li">Dockerにネイティブで対応しているベンダーを選ぶ。</li><li name="edcd" id="edcd" class="graf graf--li graf-after--li">早期に失敗し、最速のテストを最初に実行する。複数の高速な検査（例：リンティング、ユニットテスト）をまとめた「スモークテスト」のステップ/マイルストーンを作成し、コードコミッターに迅速なフィードバックを提供しましょう。</li><li name="0375" id="0375" class="graf graf--li graf-after--li">テストレポート、カバレッジレポート、ミューテーションレポート、ログなど、すべてのビルド成果物に簡単に目を通すことができる。</li><li name="df82" id="df82" class="graf graf--li graf-after--li">イベントごとに複数のパイプライン/ジョブを作成し、それらの間でステップを再利用する。例えば、フィーチャーブランチのコミット用のジョブと、マスターブランチのPR用のジョブには別のジョブを設定します。それぞれが共有ステップを使ってロジックを再利用できるようにします（ほとんどのベンダーがコード再利用のための何らかのメカニズムを提供しています）。</li><li name="19b0" id="19b0" class="graf graf--li graf-after--li">ジョブ宣言に機密情報を埋め込まない。特定の保存場所やジョブの設定から機密情報を取得するようにしてください。</li><li name="b70d" id="b70d" class="graf graf--li graf-after--li">リリースビルドで明示的にバージョンを上げるか、少なくとも開発者が行ったことを保証する。</li><li name="957c" id="957c" class="graf graf--li graf-after--li">一度だけビルドし、単一のビルド成果物（例：Docker Image）に対してすべての検査を実行する</li><li name="339b" id="339b" class="graf graf--li graf-after--li">ビルド間で状態が移動しない短命な環境でテストを行う。node_modulesのキャッシュは唯一の例外かもしれません。</li></ol>
<br/>

❌ **さもなくば:** 長年の知恵を失うことになるでしょう

<br/><br/>

## ⚪ ️ 5.9 ビルドマトリックス: 複数のNodeバージョンで同じCIステップを実行する

:white_check_mark: **こうしましょう:** 品質チェックは偶然の発見であり、カバーする範囲が広ければ広いほど、問題を早期に発見することができます。再利用可能なパッケージを開発したり、様々な構成やNodeのバージョンを持つ複数の顧客の製品を開発する場合、CIはすべての構成の組み合わせに対してテストのパイプラインを実行する必要があります。 例えば、ある顧客にはMySQLを使用し、他の顧客にはPostgresを使用する場合、いくつかのCIベンダーは「マトリックス」と呼ばれる機能をサポートしており、MySQL、Postgres、そしてNodeバージョン8、9、10のような複数のすべての組み合わせに対してテストスイートを実行することができます。これは設定のみで行われ、追加の手間はかかりません（テストまたはその他の品質チェックが既にあることを前提としています）。マトリックスをサポートしていない他のCIでは、拡張機能や調整機能で対応しているかもしれません。
<br/>

❌ **さもなくば:** テストを書くという大変な作業をすべて終えた後に、設定の問題だけでバグが紛れ込むのを許すのでしょうか？

<br/>

<details><summary>✏ <b>コード例</b></summary>

<br/>

### :clap: 例: Travis（CIベンダー）のビルド定義を使って、同じテストを複数のNodeバージョンで実行する

<pre name="f909" id="f909" class="graf graf--pre graf-after--p">language: node_js<br>node_js:<br>  - "7"<br>  - "6"<br>  - "5"<br>  - "4"<br>install:<br>  - npm install<br>script:<br>  - npm run test</pre>
</details>

<br/><br/>

# Team

## Yoni Goldberg

<br/>
<img width="480px" src="assets/yoni-goldberg.jpg"/>
<br/>

**Role:** Writer

**About:** I'm an independent consultant who works with Fortune 500 companies and garage startups on polishing their JS & Node.js applications. More than any other topic I'm fascinated by and aims to master the art of testing. I'm also the author of [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)

**📗 Online Course:** Liked this guide and wish to take your testing skills to the extreme? Consider visiting my comprehensive course [Testing Node.js & JavaScript From A To Z](https://www.testjavascript.com)

<br/>

**Follow:**

- [🐦 Twitter](https://twitter.com/goldbergyoni/)
- [📞 Contact](https://testjavascript.com/contact-2/)
- [✉️ Newsletter](https://testjavascript.com/newsletter//)

<br/>
<hr/>
<br/>

## [Bruno Scheufler](https://github.com/BrunoScheufler)

**Role:** Tech reviewer and advisor

Took care to revise, improve, lint and polish all the texts

**About:** full-stack web engineer, Node.js & GraphQL enthusiast

<hr/>
<br/>

## [Ido Richter](https://github.com/idori)

**Role:** Concept, design and great advice

**About:** A savvy frontend developer, CSS expert and emojis freak

## [Kyle Martin](https://github.com/js-kyle)

**Role:** Helps keep this project running, and reviews security related practices

**About:** Loves working on Node.js projects and web application security.

## Contributors ✨

Thanks goes to these wonderful people who have contributed to this repository!

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="http://geospatialscott.blogspot.com/"><img src="https://avatars3.githubusercontent.com/u/1326248?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Scott Davis</b></sub></a><br /><a href="#content-stdavis" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/AdrienRedon"><img src="https://avatars2.githubusercontent.com/u/5978436?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Adrien REDON</b></sub></a><br /><a href="#content-AdrienRedon" title="Content">🖋</a></td>
    <td align="center"><a href="https://twitter.com/NoriSte"><img src="https://avatars0.githubusercontent.com/u/173663?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Stefano Magni</b></sub></a><br /><a href="#content-NoriSte" title="Content">🖋</a></td>
    <td align="center"><a href="https://www.joer.im"><img src="https://avatars2.githubusercontent.com/u/47742486?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Yeoh Joer</b></sub></a><br /><a href="#content-yjoer" title="Content">🖋</a></td>
    <td align="center"><a href="http://jhonnymoreira.dev"><img src="https://avatars0.githubusercontent.com/u/2177742?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Jhonny Moreira</b></sub></a><br /><a href="#content-jhonnymoreira" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/Germanika"><img src="https://avatars2.githubusercontent.com/u/8846678?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Ian Germann</b></sub></a><br /><a href="#content-Germanika" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/AbdelrahmanHafez"><img src="https://avatars3.githubusercontent.com/u/19984935?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Hafez</b></sub></a><br /><a href="#content-AbdelrahmanHafez" title="Content">🖋</a></td>
  </tr>
  <tr>
    <td align="center"><a href="http://www.ruxandrafediuc.com"><img src="https://avatars1.githubusercontent.com/u/11021586?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Ruxandra Fediuc</b></sub></a><br /><a href="#content-ruxandrafed" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/jacklee814"><img src="https://avatars0.githubusercontent.com/u/9951291?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Jack</b></sub></a><br /><a href="#content-jacklee814" title="Content">🖋</a></td>
    <td align="center"><a href="https://www.petercarrero.com"><img src="https://avatars0.githubusercontent.com/u/231727?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Peter Carrero</b></sub></a><br /><a href="#content-aloyr" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/huhgawz"><img src="https://avatars3.githubusercontent.com/u/369338?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Huhgawz</b></sub></a><br /><a href="#content-huhgawz" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/haakonmb"><img src="https://avatars1.githubusercontent.com/u/7099302?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Haakon Borch</b></sub></a><br /><a href="#content-haakonmb" title="Content">🖋</a></td>
    <td align="center"><a href="https://jaimemendoza.com/"><img src="https://avatars3.githubusercontent.com/u/5395811?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Jaime Mendoza</b></sub></a><br /><a href="#content-jaimemendozadev" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/camerondunford"><img src="https://avatars0.githubusercontent.com/u/840612?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Cameron Dunford</b></sub></a><br /><a href="#content-camerondunford" title="Content">🖋</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/shadowspawn"><img src="https://avatars1.githubusercontent.com/u/15719847?v=4?s=100" width="100px;" alt=""/><br /><sub><b>John Gee</b></sub></a><br /><a href="#content-shadowspawn" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/aurelijusrozenas"><img src="https://avatars0.githubusercontent.com/u/3273544?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Aurelijus Rožėnas</b></sub></a><br /><a href="#content-aurelijusrozenas" title="Content">🖋</a></td>
    <td align="center"><a href="http://aaronshivers.com"><img src="https://avatars2.githubusercontent.com/u/42848750?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Aaron</b></sub></a><br /><a href="#content-aaronshivers" title="Content">🖋</a></td>
    <td align="center"><a href="https://tomdoes.tech/"><img src="https://avatars1.githubusercontent.com/u/8683577?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Tom Nagle</b></sub></a><br /><a href="#content-tomanagle" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/yvesyao"><img src="https://avatars0.githubusercontent.com/u/7723729?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Yves yao</b></sub></a><br /><a href="#content-yvesyao" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/Userbit"><img src="https://avatars1.githubusercontent.com/u/34487074?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Userbit</b></sub></a><br /><a href="#content-Userbit" title="Content">🖋</a></td>
    <td align="center"><a href="https://glaucialemos.netlify.com/"><img src="https://avatars0.githubusercontent.com/u/1631477?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Glaucia Lemos</b></sub></a><br /><a href="#maintenance-glaucia86" title="Maintenance">🚧</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://twitter.com/koooge"><img src="https://avatars2.githubusercontent.com/u/7419215?v=4?s=100" width="100px;" alt=""/><br /><sub><b>koooge</b></sub></a><br /><a href="#content-koooge" title="Content">🖋</a></td>
    <td align="center"><a href="https://twitter.com/michalbiesiada"><img src="https://avatars0.githubusercontent.com/u/18367606?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Michal</b></sub></a><br /><a href="#content-mbiesiad" title="Content">🖋</a></td>
    <td align="center"><a href="http://roywalker.me"><img src="https://avatars0.githubusercontent.com/u/611846?v=4?s=100" width="100px;" alt=""/><br /><sub><b>roywalker</b></sub></a><br /><a href="#content-roywalker" title="Content">🖋</a></td>
    <td align="center"><a href="https://dangen-effy.github.io/"><img src="https://avatars3.githubusercontent.com/u/23185799?v=4?s=100" width="100px;" alt=""/><br /><sub><b>dangen</b></sub></a><br /><a href="#content-dangen-effy" title="Content">🖋</a></td>
    <td align="center"><a href="https://dev.to/mbiesiad"><img src="https://avatars1.githubusercontent.com/u/60202305?v=4?s=100" width="100px;" alt=""/><br /><sub><b>biesiadamich</b></sub></a><br /><a href="#content-biesiadamich" title="Content">🖋</a></td>
    <td align="center"><a href="https://tarojsx.github.io"><img src="https://avatars3.githubusercontent.com/u/127009?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Yanlin Jiang</b></sub></a><br /><a href="#content-cncolder" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/sanguino"><img src="https://avatars2.githubusercontent.com/u/2077168?v=4?s=100" width="100px;" alt=""/><br /><sub><b>sanguino</b></sub></a><br /><a href="#content-sanguino" title="Content">🖋</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/MorganGeek"><img src="https://avatars0.githubusercontent.com/u/3721240?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Morgan</b></sub></a><br /><a href="#content-MorganGeek" title="Content">🖋</a></td>
    <td align="center"><a href="https://luk4s.dev"><img src="https://avatars0.githubusercontent.com/u/8350985?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Lukas Bischof</b></sub></a><br /><a href="https://github.com/goldbergyoni/javascript-testing-best-practices/commits?author=lukasbischof" title="Tests">⚠️</a> <a href="#content-lukasbischof" title="Content">🖋</a></td>
    <td align="center"><a href="https://juanmaruiz.surge.sh"><img src="https://avatars2.githubusercontent.com/u/1837650?v=4?s=100" width="100px;" alt=""/><br /><sub><b>JuanMa Ruiz</b></sub></a><br /><a href="#content-JuanMaRuiz" title="Content">🖋</a></td>
    <td align="center"><a href="https://luisangelorjr.com.br"><img src="https://avatars3.githubusercontent.com/u/22268900?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Luís Ângelo Rodrigues Jr.</b></sub></a><br /><a href="#content-luisangelorjr" title="Content">🖋</a></td>
    <td align="center"><a href="https://jfernandezpe.wordpress.com/"><img src="https://avatars0.githubusercontent.com/u/12046620?v=4?s=100" width="100px;" alt=""/><br /><sub><b>José Fernández</b></sub></a><br /><a href="#content-jfernandezpe" title="Content">🖋</a></td>
    <td align="center"><a href="http://www.linkedin.com/in/AlejandroGutierrezB"><img src="https://avatars3.githubusercontent.com/u/56408597?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Alejandro Gutierrez Barcenilla</b></sub></a><br /><a href="#content-AlejandroGutierrezB" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/jasonandmonte"><img src="https://avatars1.githubusercontent.com/u/30088000?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Jason</b></sub></a><br /><a href="#content-jasonandmonte" title="Content">🖋</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/otavionetoca"><img src="https://avatars.githubusercontent.com/u/11263232?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Otavio Araujo</b></sub></a><br /><a href="https://github.com/goldbergyoni/javascript-testing-best-practices/commits?author=otavionetoca" title="Tests">⚠️</a> <a href="#content-otavionetoca" title="Content">🖋</a></td>
    <td align="center"><a href="https://contributor.pw"><img src="https://avatars.githubusercontent.com/u/5027939?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Alex Ivanov</b></sub></a><br /><a href="#content-contributorpw" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/YeeJone"><img src="https://avatars.githubusercontent.com/u/20400822?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Yiqiao Xu</b></sub></a><br /><a href="#content-YeeJone" title="Content">🖋</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->
