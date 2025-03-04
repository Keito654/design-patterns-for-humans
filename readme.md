<br>
<p align="center">
  <img src="./.github/banner.svg" height="150px" />
</p>

***

<p align="center">
🎉 デザインパターンを超簡単に説明！ 🎉
</p>
<p align="center">
誰もが悩むトピックです。ここでは、可能な限り<i>簡単に</i>説明することで、皆さんの心に（そして私の心にも）残るよう努めます。
</p>

***

<sub>[私の他のプロジェクト](http://roadmap.sh)をチェックして、 [Twitter](https://twitter.com/kamrify)で「こんにちは！」と言ってください。</sub>

<br>

|[生成に関するデザインパターン](#生成に関するデザインパターン)|[構造に関するデザインパターン](#構造に関するデザインパターン)|[振る舞いに関するデザインパターン](#振る舞いに関するデザインパターン)|
|:-|:-|:-|
|[シンプルファクトリー](#-シンプルファクトリー)|[アダプター](#-アダプター)|[責任の連鎖](#-責任の連鎖)|
|[ファクトリーメソッド](#-ファクトリーメソッド)|[ブリッジ](#-ブリッジ)|[コマンド](#-コマンド)|
|[アブストラクトファクトリー](#-アブストラクトファクトリー)|[コンポジット](#-コンポジット)|[イテレーター](#-イテレーター)|
|[ビルダー](#-ビルダー)|[デコレーター](#-デコレーター)|[メディエーター](#-メディエーター)|
|[プロトタイプ](#-プロトタイプ)|[ファサード](#-ファサード)|[メメント](#-メメント)|
|[シングルトン](#-シングルトン)|[フライウェイト](#-フライウェイト)|[オブザーバー](#-オブザーバー)|
||[プロキシ](#-プロキシ)|[ビジター](#-ビジター)|
|||[ストラテジ](#-ストラテジ)|
|||[ステート](#-ステート)|
|||[テンプレートメソッド](#-テンプレートメソッド)|

<br>

はじめに
=================

デザインパターンは、繰り返し発生する問題に対する解決策であり、 **特定の問題に取り組む方法のガイドラインです**。 アプリケーションに接続し、魔法が起こるのを待つクラスやパッケージ、ライブラリではありません。特定の状況で特定の問題に取り組む方法のガイドラインです。

> デザインパターンは、繰り返し発生する問題に対する解決策であり、特定の問題に取り組む方法のガイドラインです。

Wikipediaでは次のように説明されています。

> ソフトウェア開発におけるデザインパターンまたは設計パターン（英: design pattern）とは、過去のソフトウェア設計者が発見し編み出した設計ノウハウを蓄積し、名前をつけ、再利用しやすいように特定の規約に従ってカタログ化したものである。パターン（pattern）とは、型紙（かたがみ）やひな形を意味する。

⚠️ 注意
-----------------
- デザインパターンはすべての問題を解決する銀の弾丸ではありません。
- 無理に適用しようとしないでください。強制的に適用すると、悪い結果を招くことになります。
- デザインパターンは問題**に対する**解決策であり、問題を**見つけるための**方法ではないことに注意してください。そのため、考えすぎないでください。
- 正しい場所で正しく使用すると、それらは救世主となり得ます。間違った場所で不適切に使用するとコードがひどく混乱する可能性があります。

> また、以下のサンプルコードはPHP-7ですが、概念はどの言語でも同じです。理解を妨げることはありません。

デザインパターンの種類
-----------------

* [生成](#生成に関するデザインパターン)
* [構造](#構造に関するデザインパターン)
* [振る舞い](#振る舞いに関するデザインパターン)

生成に関するデザインパターン
==========================

簡単に言えば
> 生成に関するパターンは、オブジェクトまたは関連するオブジェクトのグループをインスタンス化する方法に重点を置いています。

Wikipediaによれば
> ソフトウェア エンジニアリングにおいて、生成に関するデザインパターンは、オブジェクトを作成するメカニズムを扱い、状況に適した方法でオブジェクトを作成しようとするデザインパターンです。オブジェクト生成の基本的な形式は、設計上の問題や設計の複雑さの増加につながる可能性があります。生成に関するデザインパターンは、オブジェクト生成を何らかの方法で制御することでこの問題を解決します。

 * [シンプルファクトリー](#-シンプルファクトリー)
 * [ファクトリーメソッド](#-ファクトリーメソッド)
 * [アブストラクトファクトリー](#-アブストラクトファクトリー)
 * [ビルダー](#-ビルダー)
 * [プロトタイプ](#-プロトタイプ)
 * [シングルトン](#-シングルトン)

🏠 シンプルファクトリー
--------------
現実世界の例
> あなたは家を建てていて、ドアが必要だとします。大工の服を着て、木材、接着剤、釘、必要なすべての道具を持ってきて、家の中で作り始めることもできます。一方、工場に電話し、組み立てられたドアを届けてもらうこともできます。このようにすれば、あなたはドアの作り方を学んだり、ドアを作るときに発生する面倒な作業に対処する必要がなくなります。

簡単に言えば
> シンプルファクトリーは、インスタンス生成のロジックを利用者に公開せず、インスタンスを生成します。

Wikipediaによれば
> オブジェクト指向プログラミング (OOP)では、ファクトリーは他のオブジェクトを生成するためのオブジェクトです。正式には、ファクトリーはメソッドの呼び出しにより変化したプロトタイプ、またはクラスを返すメソッド・関数であり、そのメソッドの呼び出しは"new"であるとみなすことができます。

**プログラム例**

はじめに、ドアのインターフェースとその実装を作ります。
```php
interface Door
{
    public function getWidth(): float;
    public function getHeight(): float;
}

class WoodenDoor implements Door
{
    protected $width;
    protected $height;

    public function __construct(float $width, float $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getWidth(): float
    {
        return $this->width;
    }

    public function getHeight(): float
    {
        return $this->height;
    }
}
```
次に、ドアを生成し返すドアファクトリーを作ります。
```php
class DoorFactory
{
    public static function makeDoor($width, $height): Door
    {
        return new WoodenDoor($width, $height);
    }
}
```
次のように使用します。
```php
// 100x200のドアを作成
$door = DoorFactory::makeDoor(100, 200);

echo 'Width: ' . $door->getWidth();
echo 'Height: ' . $door->getHeight();

// 50x100のドアを作成
$door2 = DoorFactory::makeDoor(50, 100);
```

**いつ使う？**

オブジェクトが単なるいくつかの割り当てではなく、何らかのロジックを必要とする場合、同じコードをあらゆる場所で繰り返すのではなく、専用のファクトリーにするのが理にかなっています。

🏭 ファクトリーメソッド
--------------

現実世界の例
> 採用マネージャーを考えてください。１人の担当者が全ての面接を行うことは不可能です。求人内容に基づき、面接の手順を決め、複数の担当者に委任する必要があります。

簡単に言えば
> インスタンス生成のロジックを子クラスに委任する方法を提供します。

Wikipediaによれば
> Factory Method パターンは、他のクラスのコンストラクタをサブクラスで上書き可能な自分のメソッドに置き換えることで、 アプリケーションに特化したオブジェクトの生成をサブクラスに追い出し、クラスの再利用性を高めることを目的とする。

 **プログラム例**

上記の採用マネージャーの例を見てみましょう。まず、面接官のインターフェースと実装を作ります。

```php
interface Interviewer
{
    public function askQuestions();
}

class Developer implements Interviewer
{
    public function askQuestions()
    {
        echo 'デザインパターンについて質問します。';
    }
}

class CommunityExecutive implements Interviewer
{
    public function askQuestions()
    {
        echo 'コミュニティ構築について質問します。';
    }
}
```

採用マネージャーのクラス`HiringManager`を作成しましょう。

```php
abstract class HiringManager
{

    // ファクトリーメソッド
    abstract protected function makeInterviewer(): Interviewer;

    public function takeInterview()
    {
        $interviewer = $this->makeInterviewer();
        $interviewer->askQuestions();
    }
}

```
子クラスはファクトリーメソッドを継承し、必要な面接官を作成することができます。
```php
class DevelopmentManager extends HiringManager
{
    protected function makeInterviewer(): Interviewer
    {
        return new Developer();
    }
}

class MarketingManager extends HiringManager
{
    protected function makeInterviewer(): Interviewer
    {
        return new CommunityExecutive();
    }
}
```
そして、次のように利用します。

```php
$devManager = new DevelopmentManager();
$devManager->takeInterview(); // 出力: デザインパターンについて質問します。

$marketingManager = new MarketingManager();
$marketingManager->takeInterview(); // 出力: コミュニティ構築について質問します。
```

**いつ使う？**

クラスに汎用的な処理があるが、必要となる子クラスは実行時に動的に決定される場合に役立ちます。別の言葉で表すと、利用側が必要となる子クラスを正確に知らない場合に便利です。

🔨 アブストラクトファクトリー
----------------

現実世界の例
> シンプルファクトリーで例として挙げたドアを拡張します。ニーズに基づき、木製ドアを木製ドアショップから、鉄のドアを鉄を売る店から、プラスチックのドアをプラスチックの店から入手するでしょう。さらに、ドアを取り付けるため、例えば木製ドアには大工、鉄のドアには溶接工など、さまざまな専門技術を持つ人が必要です。このように、木製ドアは大工が必要、鉄のドアには溶接工が必要など、ドアとの間には依存関係が存在します。

簡単に言えば
> ファクトリーのファクトリー。独立してるが関連・依存をもつファクトリーを具体的なクラスを指定せずグループ化するファクトリーです。

Wikipediaによれば
> 関連するインスタンス群を生成するための API を集約することによって、利用側がインスタンス群をまとめて変えられるようにし、さらに組み合わせ方を間違えないようにする。

**プログラム例**

上記のドアの例を書き換えてみましょう。まず、`Door`インターフェースとその実装を作成します。

```php
interface Door
{
    public function getDescription();
}

class WoodenDoor implements Door
{
    public function getDescription()
    {
        echo '私は木のドアです。';
    }
}

class IronDoor implements Door
{
    public function getDescription()
    {
        echo '私は鉄のドアです。';
    }
}
```
次に、各ドアを取り付ける専門家を作ります。

```php
interface DoorFittingExpert
{
    public function getDescription();
}

class Welder implements DoorFittingExpert
{
    public function getDescription()
    {
        echo '私は鉄のドアを取り付けることができます。';
    }
}

class Carpenter implements DoorFittingExpert
{
    public function getDescription()
    {
        echo '私は木のドアを取り付けることができます。';
    }
}
```

では、今から関連するオブジェクトのグループを作成するアブストラクトファクトリーを作ります。例えば、木のドアのファクトリーは木のドアと木のドアを取り付ける専門家を作成します。一方、鉄のドアのファクトリーは鉄ドア、鉄のドアを取り付ける専門家を作成します。
```php
interface DoorFactory
{
    public function makeDoor(): Door;
    public function makeFittingExpert(): DoorFittingExpert;
}

// 大工と木のドアを返す、木のドアのファクトリー
class WoodenDoorFactory implements DoorFactory
{
    public function makeDoor(): Door
    {
        return new WoodenDoor();
    }

    public function makeFittingExpert(): DoorFittingExpert
    {
        return new Carpenter();
    }
}

// 鉄のドアと関連する専門家を返す、鉄のドアのファクトリー
class IronDoorFactory implements DoorFactory
{
    public function makeDoor(): Door
    {
        return new IronDoor();
    }

    public function makeFittingExpert(): DoorFittingExpert
    {
        return new Welder();
    }
}
```
次のように利用します。
```php
$woodenFactory = new WoodenDoorFactory();

$door = $woodenFactory->makeDoor();
$expert = $woodenFactory->makeFittingExpert();

$door->getDescription();  // 出力: 私は木のドアです。
$expert->getDescription(); // 出力: 私は木のドアを取り付けることができます。

// 鉄のドアのファクトリー
$ironFactory = new IronDoorFactory();

$door = $ironFactory->makeDoor();
$expert = $ironFactory->makeFittingExpert();

$door->getDescription();  // 出力: 私は鉄のドアです。
$expert->getDescription(); // 出力: 私は鉄のドアを取り付けることができます。
```

ご覧の通り、木のドアのファクトリーは`carpenter`と`wooden door`をカプセル化しています。また鉄のドアのファクトリーは`iron door`と`welder`をカプセル化しています。これにより、間違った専門家を取得してしまうことがありません。

**いつ使う？**

単純ではない生成ロジックがあり、かつ相互依存関係がある場合

👷 ビルダー
--------------------------------------------
現実世界の例
> マクドナルドで、例えば「ビックバーガー」を注文し、店員が*何も質問せず*商品を手渡すところを想像してください。これはシンプルなファクトリーの例です。ただし生成ロジックに多くの手順が含まれる場合があります。例えば、サブウェイではバーガーの作り方をいくつかのオプションから選ぶことができます。どのパンがいいですか？どの種類のソースがいいですか？どのチーズがいいですか？などです。この場合、ビルダーパターンが役に立ちます。

簡単に言えば
> コンストラクタ汚染を避けながら、異なったフレーバーをオブジェクトに追加できます。１つのオブジェクトにいろいろなフレーバーがある場合や、オブジェクトの生成に多くの手順が含まれる場合に便利です。

Wikipediaによれば
> ビルダーパターンはテレスコープコンストラクタというアンチパターンに対する解決策を見つけることを目的とした、オブジェクト生成に関するソフトウェアデザインパターンです。

ここで、テレスコープコンストラクタのアンチパターンについて少し説明させてください。皆さん一度は以下のようなコンストラクタを見たことがあるでしょう。

```php
public function __construct($size, $cheese = true, $pepperoni = true, $tomato = false, $lettuce = true)
{
}
```

ご覧の通り、コンストラクタの引数の数はすぐに手に負えなくなり、引数の配置を理解することが難しくなるでしょう。さらに、将来的にオプションを追加したくなり、この引数のリストは増え続けるでしょう。これをテレスコープコンストラクタ・アンチパターンと呼びます。

**プログラム例**

まともな代替案として、ビルダーパターンを使うことができます。まず、作りたいバーガーのクラスを作ります。

```php
class Burger
{
    protected $size;

    protected $cheese = false;
    protected $pepperoni = false;
    protected $lettuce = false;
    protected $tomato = false;

    public function __construct(BurgerBuilder $builder)
    {
        $this->size = $builder->size;
        $this->cheese = $builder->cheese;
        $this->pepperoni = $builder->pepperoni;
        $this->lettuce = $builder->lettuce;
        $this->tomato = $builder->tomato;
    }
}
```

そして、ビルダーを作ります。

```php
class BurgerBuilder
{
    public $size;

    public $cheese = false;
    public $pepperoni = false;
    public $lettuce = false;
    public $tomato = false;

    public function __construct(int $size)
    {
        $this->size = $size;
    }

    public function addPepperoni()
    {
        $this->pepperoni = true;
        return $this;
    }

    public function addLettuce()
    {
        $this->lettuce = true;
        return $this;
    }

    public function addCheese()
    {
        $this->cheese = true;
        return $this;
    }

    public function addTomato()
    {
        $this->tomato = true;
        return $this;
    }

    public function build(): Burger
    {
        return new Burger($this);
    }
}
```
以下のように使用します。

```php
$burger = (new BurgerBuilder(14))
                    ->addPepperoni()
                    ->addLettuce()
                    ->addTomato()
                    ->build();
```

**いつ使う？**

オブジェクトに複数のフレーバーがある可能性があり、テレスコープコンストラクタを避ける場合。ファクトリーパターンとの主な違いは、ファクトリーパターンは生成が1ステップで済む場合に使用され、ビルダーパターンは生成が複数ステップに及ぶ場合に使用することです。

🐑 プロトタイプ
------------
現実世界の例
> ドリーを覚えていますか？羊のクローンです！詳細は省きますが、ここで重要なのは「クローン化」がテーマとだという点です。

簡単に言えば
> クローン化することで、既存のオブジェクトに基づき新しいオブジェクトを作成します。

Wikipediaによれば
> プロトタイプパターンはソフトウェア開発における生成のデザインパターンです。生成するオブジェクトのタイプがプロトタイプから決定され、そのインスタンスがクローンされて新しいオブジェクトが生成される場合に使われます。

つまり、オブジェクトを１から作成し設定する手間をかけるのではなく、既存のオブジェクトのコピーを作成し必要に応じて変更を加えることです。

**プログラム例**

PHPでは、`clone`を使うことで簡単に実行できます。

```php
class Sheep
{
    protected $name;
    protected $category;

    public function __construct(string $name, string $category = 'ビッグホーン')
    {
        $this->name = $name;
        $this->category = $category;
    }

    public function setName(string $name)
    {
        $this->name = $name;
    }

    public function getName()
    {
        return $this->name;
    }

    public function setCategory(string $category)
    {
        $this->category = $category;
    }

    public function getCategory()
    {
        return $this->category;
    }
}
```
このオブジェクトは以下のようにクローンできます。
```php
$original = new Sheep('ジョリー');
echo $original->getName(); // ジョリー
echo $original->getCategory(); // ビッグホーン

// クローンし、必要な変更を行います
$cloned = clone $original;
$cloned->setName('ドリー');
echo $cloned->getName(); // ドリー
echo $cloned->getCategory(); // ビッグホーン
```

また、マジックメソッド`__clone`を使用してクローンの動作を変更することも可能です。

**いつ使う？**

既存のオブジェクトと似ているオブジェクトが必要な場合。もしくは、クローン化と比べてオブジェクト生成にかかるコストが高い場合。

💍 シングルトン
------------
現実世界の例
> 国の大統領は一度に1人だけなることができます。任務を行うときはいつでも、同じ大統領が行動を起こさなければなりません。ここでの大統領はシングルトンです。

簡単に言えば
> 特定のクラスが常に１つだけ作成されるようにします。

Wikipediaによれば
> ソフトウェア開発において、シングルトンパターンはクラスのインスタンス化を１つのオブジェクトのみになるよう制限するデザインパターンです。これはシステム全体の調整をするため１つのオブジェクトだけが必要な場合に役立ちます。

シングルトンパターンは実際のところアンチパターンと考えられており、過度の使用は避けるべきです。必ずしも悪いわけではなく、有効な使い方もあるかもしれませんが、注意して使用する必要があります。なぜなら、シングルトンはアプリケーションのグロ‐バルな状態であり、１つの場所でシングルトンを変更すると他の場所にも影響があるからです。これによりデバッグがかなり難しくなります。もう１つの欠点として、コードを密結合にし、シングルトンのモック化を困難にすることが挙げられます。

**プログラム例**

シングルトンを作成するためには、プライベートコンストラクタを作り、クローン化と継承を無効化し、インスタンスを格納する静的な変数を作ります。
```php
final class President
{
    private static $instance;

    private function __construct()
    {
        // コンストラクタを隠す。
    }

    public static function getInstance(): President
    {
        if (!self::$instance) {
            self::$instance = new self();
        }

        return self::$instance;
    }

    private function __clone()
    {
        // クローンを無効にする
    }

    private function __wakeup()
    {
        // unserializeを無効にする
    }
}
```
以下のように利用します。
```php
$president1 = President::getInstance();
$president2 = President::getInstance();

var_dump($president1 === $president2); // true
```

構造に関するデザインパターン
==========================
簡単に言えば
> 構造に関するパターンは主にオブジェクトの構成、言い換えるとエンティティがお互いをどのように利用するかに関係しています。別の説明をすると、これらは「ソフトウェアの構成要素をどのように組み立てていくか」に答えるのに役立ちます。

Wikipediaによれば
> ソフトウェアエンジニアリングにおいて、構造に関するデザインパターンはエンティティ同士をシンプルに構築する方法を見つけ、設計を容易にするパターンです。

 * [アダプター](#-adapter)
 * [ブリッジ](#-bridge)
 * [コンポジット](#-composite)
 * [デコレーター](#-decorator)
 * [ファサード](#-facade)
 * [フライウェイト](#-flyweight)
 * [プロキシ](#-proxy)

🔌 アダプター
-------
現実世界の例
> SDカードに写真があり、パソコンに転送する必要がある場面を考えてください。写真を転送するため、パソコンのポートと互換性があるアダプターが必要です。これによりパソコンにSDカードを接続することができます。この場合、カードリーダーがアダプターとなります。
> 別のよく知られる例として、電源アダプターがあります。三本脚のプラグは、2つの穴しかないコンセントには接続できません。2つ穴のコンセントに適合する電源アタプターを使う必要があります。
> さらに別の例として、ある人が話した言葉を別の人に翻訳する翻訳者が挙げられます。

簡単に言えば
> アダプターパターンは互換性のないオブジェクトをアダプターで包み、別のクラスと互換性を持たせることができます。

Wikipediaによれば
> ソフトウェア開発において、アダプターパターンは既存のクラスのインターフェースを別のクラスのインターフェースとして扱えるようにするデザインパターンです。これは、ソースコードを変更せずに既存のクラスと他のクラスを連携させる際によく使われます。

**プログラム例**

ハンターがいて、ライオンを狩るゲームを考えてみましょう。

まず、すべての種類のライオンのクラスが利用する必要がある`Lion`インターフェースがあります。

```php
interface Lion
{
    public function roar();
}

class AfricanLion implements Lion
{
    public function roar()
    {
    }
}

class AsianLion implements Lion
{
    public function roar()
    {
    }
}
```
ハンターは狩りを行うため、`Lion`インターフェースが実装されていることを期待します。
```php
class Hunter
{
    public function hunt(Lion $lion)
    {
        $lion->roar();
    }
}
```

今、ハンターにとって狩猟対象である、野犬（`WildDog`クラス）をゲームに追加するとします。しかし、犬はライオンとは異なるインターフェースを持つため、そのまま追加することはできません。ハンターと互換性を持たせるため、適合するアダプターを作成する必要があるでしょう。

```php
// これをゲームに追加する必要がある。
class WildDog
{
    public function bark()
    {
    }
}

// ゲームとの互換性を与えるための、犬クラスのアダプター
class WildDogAdapter implements Lion
{
    protected $dog;

    public function __construct(WildDog $dog)
    {
        $this->dog = $dog;
    }

    public function roar()
    {
        $this->dog->bark();
    }
}
```
これで、`WildDog`は`WildDogAdapter`を通してゲームで使用できるようになりました。

```php
$wildDog = new WildDog();
$wildDogAdapter = new WildDogAdapter($wildDog);

$hunter = new Hunter();
$hunter->hunt($wildDogAdapter);
```

🚡 ブリッジ
------
現実世界の例
> 複数のページがあるWebサイトがあり、ユーザーがテーマを変えられるようにしたい場合を考えてください。どのように実装しますか？各ページを、各テーマ分複製しますか？それともテーマだけを作成し、ユーザーの好みに応じてテーマを読み込むようにしますか？ブリッジパターンを利用すると、2つ目の例のことが可能になります。

![With and without the bridge pattern](https://cloud.githubusercontent.com/assets/11269635/23065293/33b7aea0-f515-11e6-983f-98823c9845ee.png)

簡単に言えば
> ブリッジパターンは継承よりも合成を優先します。詳細の実装はある階層から分割された階層をもつ別のオブジェクトへと送られます。

Wikipediaによれば
> ブリッジパターンはソフトウェア開発で利用されるデザインパターンです。抽象と実装を切り離すことで、それぞれが独立して変化できるようにすることを目的としています。

**プログラム例**

上のWebサイトの例をコードにしていきましょう。Webページの階層である`WebPage`とその実装を作ります。

```php
interface WebPage
{
    public function __construct(Theme $theme);
    public function getContent();
}

class About implements WebPage
{
    protected $theme;

    public function __construct(Theme $theme)
    {
        $this->theme = $theme;
    }

    public function getContent()
    {
        return "アバウトページのテーマ：" . $this->theme->getColor();
    }
}

class Careers implements WebPage
{
    protected $theme;

    public function __construct(Theme $theme)
    {
        $this->theme = $theme;
    }

    public function getContent()
    {
        return "キャリアページのテーマ：" . $this->theme->getColor();
    }
}
```
そして、テーマの階層を分割し作成します。
```php

interface Theme
{
    public function getColor();
}

class DarkTheme implements Theme
{
    public function getColor()
    {
        return 'ダークブラック';
    }
}
class LightTheme implements Theme
{
    public function getColor()
    {
        return 'オフホワイト';
    }
}
class AquaTheme implements Theme
{
    public function getColor()
    {
        return 'ライトブルー';
    }
}
```
2つの階層を利用します。
```php
$darkTheme = new DarkTheme();

$about = new About($darkTheme);
$careers = new Careers($darkTheme);

echo $about->getContent(); // "アバウトページのテーマ：ダークブラック";
echo $careers->getContent(); // "キャリアページのテーマ：ダークブラック;
```

🌿 コンポジット
-----------------

現実世界の例
> すべての組織は従業員で構成されています。各従業員は同じ特徴があります。例えば、給料がある、何らかの責任がある、誰にかに報告する/しない、部下を持つ/もたない、などです。

簡単に言えば
> コンポジットパターンを利用すると、利用者は個々のオブジェクトを均一的な方法で処理できます。

Wikipediaによれば
> ソフトウェア開発において、コンポジットパターンは分類を行うデザインパターンです。コンポジットパターンを用いることで、オブジェクトのグループを、単一のオブジェクトのインスタンスのように同じ方法で処理できます。コンポジットパターンの目的はオブジェクトをツリー構造になるように「構成する」ことで、部分ー全体の関係をもつ階層構造を表現することです。コンポジットパターンを利用することで、利用者は個々のオブジェクトや構成を均一的に処理できます。

**プログラム例**

上の従業員の例を実装していきましょう。異なる型をもつ従業員を作成します。

```php
interface Employee
{
    public function __construct(string $name, float $salary);
    public function getName(): string;
    public function setSalary(float $salary);
    public function getSalary(): float;
    public function getRoles(): array;
}

class Developer implements Employee
{
    protected $salary;
    protected $name;
    protected $roles;
    
    public function __construct(string $name, float $salary)
    {
        $this->name = $name;
        $this->salary = $salary;
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function setSalary(float $salary)
    {
        $this->salary = $salary;
    }

    public function getSalary(): float
    {
        return $this->salary;
    }

    public function getRoles(): array
    {
        return $this->roles;
    }
}

class Designer implements Employee
{
    protected $salary;
    protected $name;
    protected $roles;

    public function __construct(string $name, float $salary)
    {
        $this->name = $name;
        $this->salary = $salary;
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function setSalary(float $salary)
    {
        $this->salary = $salary;
    }

    public function getSalary(): float
    {
        return $this->salary;
    }

    public function getRoles(): array
    {
        return $this->roles;
    }
}
```

次に、何種類かの違った型をもつ従業員から構成される組織をつくります。

```php
class Organization
{
    protected $employees;

    public function addEmployee(Employee $employee)
    {
        $this->employees[] = $employee;
    }

    public function getNetSalaries(): float
    {
        $netSalary = 0;

        foreach ($this->employees as $employee) {
            $netSalary += $employee->getSalary();
        }

        return $netSalary;
    }
}
```

これらは以下のように利用できます。

```php
// 従業員を準備する
$john = new Developer('John Doe', 12000);
$jane = new Designer('Jane Doe', 15000);

// 組織に従業員を追加する
$organization = new Organization();
$organization->addEmployee($john);
$organization->addEmployee($jane);

echo "給与の手取り: " . $organization->getNetSalaries(); // 給与の手取り: 27000
```

☕ デコレーター
-------------

現実世界の例

> 複数のサービスを提供する自動車サービス店を経営することを想像してください。請求額をどのように計算しますか？1つのサービスを選び、提供されたサービスの価格を動的に追加し続けることで、最終的な金額を得ることができます。ここでの各サービスの種類がデコレーターです。

簡単に言えば
> デコレーターパターンは対象のオブジェクトをデコレータークラスで包むことにより、振る舞いを動的に変化させることを可能とします。

Wikipediaによれば
> オブジェクト指向プログラミングにおいて、デコレーターパターンは、同じクラスから作られた他のオブジェクトの振る舞いに影響を与えることなく、静的もしくは動的に個々のオブジェクトに振る舞いを追加することを可能とします。デコレーターパターンは機能を固有の関心事をもつクラスに分けられるため、単一責任の原則を守ることに役立ちます。

**プログラム例**

コーヒーを例に考えてみましょう。まず、コーヒーのインターフェースを実装したシンプルなコーヒークラスを作成します。

```php
interface Coffee
{
    public function getCost();
    public function getDescription();
}

class SimpleCoffee implements Coffee
{
    public function getCost()
    {
        return 10;
    }

    public function getDescription()
    {
        return 'シンプルなコーヒー';
    }
}
```
あなたは必要があれば変更可能なオプションをつけるため、コードを拡張したくなりました。いくつか、アドオン（デコレーター）を作りましょう。
```php
class MilkCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 2;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', ミルク';
    }
}

class WhipCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 5;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', ホイップクリーム';
    }
}

class VanillaCoffee implements Coffee
{
    protected $coffee;

    public function __construct(Coffee $coffee)
    {
        $this->coffee = $coffee;
    }

    public function getCost()
    {
        return $this->coffee->getCost() + 3;
    }

    public function getDescription()
    {
        return $this->coffee->getDescription() . ', バニラ';
    }
}
```

それではコーヒーを作りましょう。

```php
$someCoffee = new SimpleCoffee();
echo $someCoffee->getCost(); // 10
echo $someCoffee->getDescription(); // シンプルなコーヒー

$someCoffee = new MilkCoffee($someCoffee);
echo $someCoffee->getCost(); // 12
echo $someCoffee->getDescription(); // シンプルなコーヒー, ミルク

$someCoffee = new WhipCoffee($someCoffee);
echo $someCoffee->getCost(); // 17
echo $someCoffee->getDescription(); // シンプルなコーヒー, ミルク, ホイップクリーム

$someCoffee = new VanillaCoffee($someCoffee);
echo $someCoffee->getCost(); // 20
echo $someCoffee->getDescription(); // シンプルなコーヒー, ミルク, ホイップクリーム, バニラ
```

📦 ファサード
----------------

現実世界の例
> コンピュータの電源をつけるときどうしますか？「電源ボタンを押します」とあなたは答えるでしょう。あなたがそのように信じているのは、コンピュータが外部に提供しているシンプルなインターフェースを利用しているからです。内部では、電源をつけるためたくさんの事を実行しなければいけません。複雑なシステムのシンプルなインターフェースがファサード(Facade/外観)です。

簡単に言えば
> ファサードパターンは複雑なサブシステムに、単純化されたインターフェースを与えます。

Wikipediaによれば
> ファサードはクラスライブラリのような大量のコードに単純化されたインターフェースを与えるオブジェクトです。

**プログラム例**

上のコンピュータを例に挙げます。コンピュータクラスを作成します。

```php
class Computer
{
    public function getElectricShock()
    {
        echo "Ouch!";
    }

    public function makeSound()
    {
        echo "Beep beep!";
    }

    public function showLoadingScreen()
    {
        echo "Loading..";
    }

    public function bam()
    {
        echo "準備完了!";
    }

    public function closeEverything()
    {
        echo "Bup bup bup buzzzz!";
    }

    public function sooth()
    {
        echo "Zzzzz";
    }

    public function pullCurrent()
    {
        echo "Haaah!";
    }
}
```
ファサードを作成します。
```php
class ComputerFacade
{
    protected $computer;

    public function __construct(Computer $computer)
    {
        $this->computer = $computer;
    }

    public function turnOn()
    {
        $this->computer->getElectricShock();
        $this->computer->makeSound();
        $this->computer->showLoadingScreen();
        $this->computer->bam();
    }

    public function turnOff()
    {
        $this->computer->closeEverything();
        $this->computer->pullCurrent();
        $this->computer->sooth();
    }
}
```
ファサードを利用しましょう。
```php
$computer = new ComputerFacade(new Computer());
$computer->turnOn(); // Ouch! Beep beep! Loading.. 準備完了!
$computer->turnOff(); // Bup bup buzzz! Haah! Zzzzz
```

🍃 フライウェイト
---------

現実世界の例
> 屋台で淹れたてのお茶を飲んだことはありますか？屋台はたいてい、あなたが注文した量よりも多くお茶を作り、残りをほかのお客さんのための取っておきます。そうすることで、燃料などを節約できます。フライウェイトパターンはまさにこれ、つまりシェアすることです。

簡単に言えば
> フライウェイトパターンは似たようなオブジェクトと可能な限り共有を行うことで、メモリ使用量や計算コストを最小限に抑えるため使用されます。

Wikipediaによれば
> コンピュータープログラミングにおいて、フライウェイトはソフトウェアデザインパターンです。フライウェイトは他の似たオブジェクトとデータを可能な限り共有することでメモリ使用量を最小限にするオブジェクトです。単純な繰り返しで表現すると許容できない量のメモリが使用される場合に、大量のオブジェクトを使用する方法です。

**プログラム例**

上のお茶の例をコードにしていきましょう。まず、お茶の型とお茶の製造機を作ります。

```php
// キャッシュされるものはすべてフライウェイトです。
// ここのお茶の型はフライウェイトです。
class KarakTea
{
}

// ファクトリーとして振る舞い、作ったお茶を保存します。
class TeaMaker
{
    protected $availableTea = [];

    public function make($preference)
    {
        if (empty($this->availableTea[$preference])) {
            $this->availableTea[$preference] = new KarakTea();
        }

        return $this->availableTea[$preference];
    }
}
```

次に、注文を受け取り、お茶を提供する`TeaShop`を作ります。

```php
class TeaShop
{
    protected $orders;
    protected $teaMaker;

    public function __construct(TeaMaker $teaMaker)
    {
        $this->teaMaker = $teaMaker;
    }

    public function takeOrder(string $teaType, int $table)
    {
        $this->orders[$table] = $this->teaMaker->make($teaType);
    }

    public function serve()
    {
        foreach ($this->orders as $table => $tea) {
            echo "お茶をこのテーブルに提供します： " . $table;
        }
    }
}
```
以下のように使用できます。

```php
$teaMaker = new TeaMaker();
$shop = new TeaShop($teaMaker);

$shop->takeOrder('砂糖少なめ', 1);
$shop->takeOrder('ミルク多め', 2);
$shop->takeOrder('砂糖なし', 5);

$shop->serve();
// お茶をこのテーブルに提供します： 1
// お茶をこのテーブルに提供します： 2
// お茶をこのテーブルに提供します： 5
```

🎱 プロキシ
-------------------
現実世界の例
> ドアを通るためのアクセスカードを使ったことはありますか？ドアを開ける方法は複数あります。例えば、アクセスカードを使う他、セキュリティを迂回できるボタンを押すなどです。ドアの主な機能は開くことですが、追加機能を入れるためのプロキシ（代理人）を加えています。下のコード例でより詳しい説明をします。

簡単に言えば
> プロキシパターンを使うことで、あるクラスを別のクラスの機能として表現できます。

Wikipediaによれば
> 最も一般的な形式でのプロキシは他の何かへのインターフェースとして機能するクラスです。プロキシはクライアントによって呼び出され、舞台裏で実際のサービスオブジェクトにアクセスするためのラッパー、もしくはエージェント（代理人）オブジェクトです。プロキシを使うことで実際のオブジェクトをシンプルに転送したり、追加ロジックを提供することができます。プロキシを使うことで、例えば実際のオブジェクトの処理がリソースを大量に消費する場合のキャッシュや、実際のオブジェクトの処理が実行される前に前提条件をチェックするなど、追加の機能を提供できます。

**プログラム例**

上のセキュリティドアの例を使いましょう。まず、ドアのインターフェースとその実装を作成します。

```php
interface Door
{
    public function open();
    public function close();
}

class LabDoor implements Door
{
    public function open()
    {
        echo "研究室のドアが開く";
    }

    public function close()
    {
        echo "研究室のドアが閉じる";
    }
}
```
次に、ドアを必要に応じてセキュアにするためのプロキシを作ります。
```php
class SecuredDoor implements Door
{
    protected $door;

    public function __construct(Door $door)
    {
        $this->door = $door;
    }

    public function open($password)
    {
        if ($this->authenticate($password)) {
            $this->door->open();
        } else {
            echo "ドアを開けることは絶対にできない！";
        }
    }

    public function authenticate($password)
    {
        return $password === '$ecr@t';
    }

    public function close()
    {
        $this->door->close();
    }
}
```
次のように使用できます。
```php
$door = new SecuredDoor(new LabDoor());
$door->open('invalid'); // ドアを開けることは絶対にできない！

$door->open('$ecr@t'); // 研究室のドアが開く
$door->close(); // 研究室のドアが閉じる
```
もう一つ別の例として、何らかのデータマッパーの実装が挙げられます。例えば、私は最近プロキシパターンを利用してMongoDBのODM(オブジェクト・データ・マッパー)を作成しました。このパターンでは、マジックメソッド`__call()`を活用し、MongoDB公式のクラスの周りにプロキシを書きました。全てのメソッドの呼び出しは元のMongoDB公式のクラスに中継され、取得された結果はそのまま返されます。しかし、`find`もしくは`findOne`を利用しデータを見つける場合、取得したデータはクラスオブジェクトに紐づけられ、そのオブジェクトが`Cursor`(※MongoDBが提供するクラス)の代わりに返されます。

振る舞いに関するパターン
==========================

簡単に言えば
> オブジェクト間の責任の割り当てに関係します。構造に関するパターンと異なるのは、単にオブジェクトの構造を決めるだけでなく、オブジェクト間のメッセージの受け渡し/通信も示す点です。言い換えると、これらは「ソフトウェアコンポーネントの中でどのように振る舞い(動作)を実行するか」という問いに答えるのに役立ちます。

Wikipediaによれば
> ソフトウェア開発において、振る舞いに関するデザインパターンとはオブジェクト間の共通的な通信パターンを識別し、これらを実現するパターンです。このパターンを用いる事で、通信を実施する際の柔軟性を高めることができます。

* [責任の連鎖](#-責任の連鎖)
* [コマンド](#-コマンド)
* [イテレーター](#-イテレーター)
* [メディエーター](#-メディエーター)
* [メメント](#-メメント)
* [オブザーバー](#-オブザーバー)
* [ビジター](#-ビジター)
* [ストラテジ](#-ストラテジ)
* [ステート](#-ステート)
* [テンプレートメソッド](#-テンプレートメソッド)

🔗 責任の連鎖
-----------------------

現実世界の例
> 例えば、あなたは3つの支払い方法のアカウント（`A`, `B`, `C`）を持っているとします。それぞれ、支払える金額が異なります。`A`は100ドル、`B`は300ドル、`C`は1000ドルです。また、支払い方法の優先順位は`A`→ `B`→`C`となっています。今、あなたは210ドルのものを買おうとしています。「責任の連鎖」を使用すると、初めにアカウント`A`で購入可能かどうかチェックされます。もし可能であれば商品を購入し、それ以上リクエストは転送されません。もし不可能であれば、アカウント`B`にリクエストは転送され、金額をチェックされます。購入可能ならリクエストの転送はされませんが、不可能な場合、適切なアカウントを見つけるまでリクエストは転送されつづけます。これら`A`,`B`,`C`は連鎖するように繋がっています。この全体的な現象が「責任の連鎖」です。

簡単に言えば
> オブジェクトの連鎖の順番を作成するのに役立ちます。リクエストがある1つの箇所に入力されると、適切なハンドラが見つかるまでオブジェクト間を移動し続けます。

Wikipediaによれば
> オブジェクト指向デザインにおいて、責任の連鎖パターンはコマンドオブジェクトと一連の処理オブジェクトで構成されるパターンです。各処理オブジェクトには扱えるコマンドの種類を定義するロジックが含まれており、残りはチェーンの中の次の処理オブジェクトへと渡されます。

**プログラム例**

上の口座の例をコードにしてみましょう。まず、アカウントを連鎖するロジックを持つベースとなるアカウントと、いくつかのアカウントを作ります。

```php
abstract class Account
{
    protected $successor;
    protected $balance;

    public function setNext(Account $account)
    {
        $this->successor = $account;
    }

    public function pay(float $amountToPay)
    {
        if ($this->canPay($amountToPay)) {
            echo sprintf('%sを%sを利用し支払いました。' . PHP_EOL, $amountToPay, get_called_class());
        } elseif ($this->successor) {
            echo sprintf('%sでは支払えませんでした。 進行中 ..' . PHP_EOL, get_called_class());
            $this->successor->pay($amountToPay);
        } else {
            throw new Exception('どのアカウントも資金が足りません');
        }
    }

    public function canPay($amount): bool
    {
        return $this->balance >= $amount;
    }
}

class Bank extends Account
{
    protected $balance;

    public function __construct(float $balance)
    {
        $this->balance = $balance;
    }
}

class Paypal extends Account
{
    protected $balance;

    public function __construct(float $balance)
    {
        $this->balance = $balance;
    }
}

class Bitcoin extends Account
{
    protected $balance;

    public function __construct(float $balance)
    {
        $this->balance = $balance;
    }
}
```

それでは、上で定義したリンク（銀行、Paypal、ビットコイン）を使って連鎖を準備しましょう。

```php
// 以下のような連鎖を準備しましょう。
//      $bank->$paypal->$bitcoin
//
// 優先順位の1番目は銀行
//      もし銀行で支払えなければPaypal
//      もしPaypalで支払えなければビットコイン

$bank = new Bank(100);          // 銀行の資金は100
$paypal = new Paypal(200);      // Paypalの資金は200
$bitcoin = new Bitcoin(300);    // ビットコインの資金は300

$bank->setNext($paypal);
$paypal->setNext($bitcoin);

// 優先順位が1番の銀行を利用して支払いできるか試してみます。
$bank->pay(259);

// 出力
// ==============
// Bankでは支払えませんでした。 進行中 ..
// Paypalでは支払えませんでした。 進行中 ..
// 259をBitcoinで支払いました。
```

👮 コマンド
-------

現実世界の例
> 一般的な例は、レストランで食事を注文する場面です。あなた(=`利用者/Client`)はウェイター(=`起動者/Invoker`)に食事を持ってきてと頼みます(=`コマンド/Command`)。そしてウェイターは何をどのように調理するか知っているシェフ(=`受信者/Receiver`)に注文を通します。
> 別の例として、あなた(=`利用者/Client`)がテレビ(=`受信者/Receiver`)の電源をオンにする(=`コマンド/Command`)ため、リモコン(=`起動者/Invoker`)を使うことが挙げられます。

簡単に言えば
> 行動をオブジェクトにカプセル化することができます。このパターンの背景にある重要なアイディアは、クライアントと受信者を切り離す手段を提供することです。

Wikipediaによれば
> オブジェクト指向プログラミングにおいて、コマンドパターンはオブジェクトを利用し、アクションを実行したり、イベントを後で発火させるための情報すべてをカプセル化する、振る舞いに関するデザインパターンです。この情報にはメソッド名、メソッドを所有するオブジェクト、メソッドの引数の値が含まれます。

**プログラム例**

まず、実行可能な全てのアクションを実装した受信者(Receiver)を作成します。
```php
// 受信者
class Bulb
{
    public function turnOn()
    {
        echo "灯がつきました!";
    }

    public function turnOff()
    {
        echo "真っ暗です！";
    }
}
```
次に、コマンドのインターフェースを作り、その後コマンドを実装します。
```php
interface Command
{
    public function execute();
    public function undo();
    public function redo();
}

// コマンド
class TurnOn implements Command
{
    protected $bulb;

    public function __construct(Bulb $bulb)
    {
        $this->bulb = $bulb;
    }

    public function execute()
    {
        $this->bulb->turnOn();
    }

    public function undo()
    {
        $this->bulb->turnOff();
    }

    public function redo()
    {
        $this->execute();
    }
}

class TurnOff implements Command
{
    protected $bulb;

    public function __construct(Bulb $bulb)
    {
        $this->bulb = $bulb;
    }

    public function execute()
    {
        $this->bulb->turnOff();
    }

    public function undo()
    {
        $this->bulb->turnOn();
    }

    public function redo()
    {
        $this->execute();
    }
}
```
そして、利用者がコマンドを実行するために対話する起動者(Invoker)を追加します。
```php
// Invoker
class RemoteControl
{
    public function submit(Command $command)
    {
        $command->execute();
    }
}
```
最後に、利用者(client)を作ります。どのように起動者を利用するか確認しましょう。
```php
$bulb = new Bulb();

$turnOn = new TurnOn($bulb);
$turnOff = new TurnOff($bulb);

$remote = new RemoteControl();
$remote->submit($turnOn); // 灯がつきました!
$remote->submit($turnOff); // 真っ暗です!
```

コマンドパターンはトランザクションが必要なシステムを実装する際にも用いられます。コマンドを実行するとすぐに、コマンドの履歴が保存されます。最後のコマンドが成功した場合問題ありませんが、それ以外の場合、履歴を遡り、実行されたすべてのコマンドに`元に戻す/undo`を行うことができます。

➿ イテレーター
--------

現実世界の例
> 古いラジオはイテレーターのいい例です。ユーザーはあるチャンネルからスタートし、 次、もしくは前ボタンでそれぞれのチャンネルに移動できます。もしくは、次、前ボタンで連続したチャンネルの移動ができるMP3プレイヤーかTVもいい例です。これらはすべて、曲もしくはラジオステーションのようなチャンネルそれぞれを繰り返しながら移動できるインターフェースを提供しています。

簡単に言えば
> オブジェクトの内部表現を公開することなく、要素にアクセスする方法を提供します。

Wikipediaによれば
> オブジェクト指向プログラミングにおいて、イテレーターパターンはコンテナを横断し、コンテナの要素にアクセスするためにイテレーターを用いるデザインパターンです。イテレーターパターンはコンテナからアルゴリズムを分離します。場合によっては、アルゴリズムは必然的にコンテナ固有であるため、分離することができないこともあります。

**プログラム例**

PHPではSPL(Standard PHP Library/スタンダート・PHP・ライブラリ)を用いることでとても簡単に実装することができます。上のラジオステーションの例をコードにしてみましょう。まず、`RadioStation`クラスを作成します。

```php
class RadioStation
{
    // 周波数
    protected $frequency;

    public function __construct(float $frequency)
    {
        $this->frequency = $frequency;
    }

    public function getFrequency(): float
    {
        return $this->frequency;
    }
}
```
次にイテレーターを作ります。

```php
use Countable;
use Iterator;

class StationList implements Countable, Iterator
{
    /** @var RadioStation[] $stations */
    protected $stations = [];

    /** @var int $counter */
    protected $counter;

    public function addStation(RadioStation $station)
    {
        $this->stations[] = $station;
    }

    public function removeStation(RadioStation $toRemove)
    {
        $toRemoveFrequency = $toRemove->getFrequency();
        $this->stations = array_filter($this->stations, function (RadioStation $station) use ($toRemoveFrequency) {
            return $station->getFrequency() !== $toRemoveFrequency;
        });
    }

    public function count(): int
    {
        return count($this->stations);
    }

    public function current(): RadioStation
    {
        return $this->stations[$this->counter];
    }

    public function key()
    {
        return $this->counter;
    }

    public function next()
    {
        $this->counter++;
    }

    public function rewind()
    {
        $this->counter = 0;
    }

    public function valid(): bool
    {
        return isset($this->stations[$this->counter]);
    }
}
```
これらをは以下のように使用できます。
```php
$stationList = new StationList();

$stationList->addStation(new RadioStation(89));
$stationList->addStation(new RadioStation(101));
$stationList->addStation(new RadioStation(102));
$stationList->addStation(new RadioStation(103.2));

foreach($stationList as $station) {
    echo $station->getFrequency() . PHP_EOL;
}

$stationList->removeStation(new RadioStation(89)); // ステーション89が削除される
```

👽 メディエーター
========

現実世界の例
> 一般的な例として、スマートフォンで誰かと通話している状況が挙げられます。このとき、ネットワークプロバイダーがあなたと通話相手の間にいて、会話は直接相手に届けられるのではなく、このネットワークプロバイダーを経由して届きます。このネットワークプロバイダーがメディエーター(mediator/仲介者)です。

簡単に言えば
> メディエーターパターンは2つのオブジェクト（colleagues/同僚と呼ばれる）同士の通信をコントロールするためサードパーティオブジェクト（mediator/仲介者と呼ばれる）を追加します。このパターンはお互いにコミュニケーションを行うクラスの結合度を減らすことに役立ちます。なぜなら、これらのクラスはお互いの実装の詳細を知っている必要がないからです。

Wikipediaによれば
> ソフトウェア開発において、メディエーターパターンは一連のオブジェクトの通信方法をカプセル化するオブジェクトを定義します。このパターンはプログラム実行時の振る舞いを置き換える方法であるため、振る舞いに関するパターンであると考えられています。

**プログラム例**

チャットルーム（すなわちmediator）で、ユーザー（すなわちcolleagues）がお互いにメッセージを送るシンプルな例を考えてみましょう。

まず、チャットルーム、つまりmediatorをつくります。

```php
interface ChatRoomMediator 
{
    public function showMessage(User $user, string $message);
}

// Mediator
class ChatRoom implements ChatRoomMediator
{
    public function showMessage(User $user, string $message)
    {
        $time = date('M d, y H:i');
        $sender = $user->getName();

        echo $time . '[' . $sender . ']:' . $message;
    }
}
```

次にユーザー、つまりcolleaguesをつくります。
```php
class User {
    protected $name;
    protected $chatMediator;

    public function __construct(string $name, ChatRoomMediator $chatMediator) {
        $this->name = $name;
        $this->chatMediator = $chatMediator;
    }

    public function getName() {
        return $this->name;
    }

    public function send($message) {
        $this->chatMediator->showMessage($this, $message);
    }
}
```
以下が使用方法です。
```php
$mediator = new ChatRoom();

$john = new User('ジョン・ドゥ', $mediator);
$jane = new User('ジェーン・ドゥ', $mediator);

$john->send('やあ!');
$jane->send('こんにちは!');

// 出力
// Feb 14, 10:58 [ジョン・ドゥ]: やあ!
// Feb 14, 10:58 [ジェーン・ドゥ]: こんにちは!
```

💾 メメント
-------
現実世界の例
> 電卓(=originator/オリジネーター)を例にとって考えてみましょう。電卓で計算を行う旅、最後の計算結果がメモリ（=memento/メメント）に保持されます。これにより、保持された結果に戻ったり、操作ボタン（=caretaker/ケアテーカー）を使って結果を復元することが可能になります。

簡単に言えば
> メメントパターンは、後でスムーズに復元できるようにするため、オブジェクトの現在の状態をキャプチャし保管しておく方法です。

Wikipediaによれば
> メメントパターンは以前の状態にオブジェクトを復元する（ロールバックを通して元に戻す）方法を提供するデザインパターンです。

一般的に、元に戻すような機能が必要な場合に役に立ちます。

**プログラム例**

時折状態を保存し続け、状態を復元することができるテキストエディタを例に見てみましょう。

まず、エディタの状態を保持できるmementoオブジェクトを作成します。

```php
class EditorMemento
{
    protected $content;

    public function __construct(string $content)
    {
        $this->content = $content;
    }

    public function getContent()
    {
        return $this->content;
    }
}
```

次に、mementoオブジェクトを利用することになるエディタ（=originator）を作成します。

```php
class Editor
{
    protected $content = '';

    public function type(string $words)
    {
        $this->content = $this->content . ' ' . $words;
    }

    public function getContent()
    {
        return $this->content;
    }

    public function save()
    {
        return new EditorMemento($this->content);
    }

    public function restore(EditorMemento $memento)
    {
        $this->content = $memento->getContent();
    }
}
```

これらは以下のように利用できます。

```php
$editor = new Editor();

// 何か入力する
$editor->type('これは最初の文章です。');
$editor->type('これは2番目です。');

// 「これは最初の文章です。これは2番目です。」を復元するために状態を保存する。
$saved = $editor->save();

// さらに入力する
$editor->type('そして3番目です。');

// 出力：保存する前のテキストコンテンツ
echo $editor->getContent(); // これは最初の文章です。これは2番目です。そして3番目です。

// 最後に保存した状態を復元
$editor->restore($saved);

$editor->getContent(); // これは最初の文章です。これは2番目です。
```

😎 オブザーバー
--------
現実世界の例
> 職を探している人がいい例でしょう。彼らは求人サイトに登録しており、マッチする仕事があればその都度通知が届きます。

簡単に言えば
> オブジェクト間の依存関係を定義することで、ある1つのオブジェクトの状態が変更されたとき、すべての依存オブジェクトに通知されます。

Wikipediaによれば
> オブザーバーパターンは、サブジェクトと呼ばれるオブジェクトが依存オブジェクト（オブザーバーと呼ばれる）のリストを保持し、通常オブザーバーのメソッドを呼ぶことにより、状態の変更を自動的に通知するソフトウェアデザインパターンです。

**プログラム例**

上の例をコードに置き換えてみましょう。まず、求人情報の通知が必要な求職者をつくります。
```php
class JobPost
{
    protected $title;

    public function __construct(string $title)
    {
        $this->title = $title;
    }

    public function getTitle()
    {
        return $this->title;
    }
}

class JobSeeker implements Observer
{
    protected $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function onJobPosted(JobPost $job)
    {
        // 求人情報が入ってきた場合に処理を実行する
        echo 'こんにちは、' . $this->name . '! 新しい求人情報が見つかりました: '. $job->getTitle();
    }
}
```
次に求職者が登録する就職エージェントを作成します。
```php
class EmploymentAgency implements Observable
{
    protected $observers = [];

    protected function notify(JobPost $jobPosting)
    {
        foreach ($this->observers as $observer) {
            $observer->onJobPosted($jobPosting);
        }
    }

    public function attach(Observer $observer)
    {
        $this->observers[] = $observer;
    }

    public function addJob(JobPost $jobPosting)
    {
        $this->notify($jobPosting);
    }
}
```
これらは以下のように使用できます。
```php
// 購読者を作成します。
$johnDoe = new JobSeeker('ジョン・ドゥ');
$janeDoe = new JobSeeker('ジェーン・ドゥ');

// 発行者を作成し、購読者を登録します。
$jobPostings = new EmploymentAgency();
$jobPostings->attach($johnDoe);
$jobPostings->attach($janeDoe);

// 新しい求人を登録し、購読者が通知を受け取るか確認します。
$jobPostings->addJob(new JobPost('ソフトウェアエンジニア'));

// Output
// こんにちは、ジョン・ドゥ! 新しい仕事が見つかりました: ソフトウェアエンジニア
// こんにちは、ジェーン・ドゥ! : 新しい仕事が見つかりました: ソフトウェアエンジニア
```

🏃 ビジター
-------
現実世界の例
> ドバイを訪問しようとしている人を考えてみましょう。彼に必要なのはドバイに入る方法（例えば入国ビザ）だけです。到着した後は、ドバイのどこへでも、許可を求めたり事前準備することなく、自由に訪れることができます。場所を知るだけで訪れることができます。ビジターパターンを使用するとまさにそれが可能になります。訪問する場所を追加することで、訪問者が多くの場所を手間をかけずに訪れることができるようになります。

簡単に言えば
> ビジターパターンはオブジェクトに変更を加えることなく、より多くの操作を追加することができます。

Wikipediaによれば
> オブジェクト指向プログラミングやソフトウェア開発において、ビジターデザインパターンはアルゴリズムと、そのアルゴリズムが操作するオブジェクト構造を分離するものです。この分離の実際の結果として、既存のオブジェクト構造に変更を加えることなく、新しい操作を追加できるようになります。これはオープン・クローズドの原則に従う方法の１つです。

**プログラム例**

いろんな種類の動物がおり、鳴き声を聞くことができる動物園のシミュレーションを例に取ります。ビジターパターンを使って実装してみましょう。

```php
// 訪問される側
interface Animal
{
    public function accept(AnimalOperation $operation);
}

// 訪問者
interface AnimalOperation
{
    public function visitMonkey(Monkey $monkey);
    public function visitLion(Lion $lion);
    public function visitDolphin(Dolphin $dolphin);
}
```
動物の実装を作ります。
```php
class Monkey implements Animal
{
    public function shout()
    {
        echo 'ウキキ!';
    }

    public function accept(AnimalOperation $operation)
    {
        $operation->visitMonkey($this);
    }
}

class Lion implements Animal
{
    public function roar()
    {
        echo 'ガオー!';
    }

    public function accept(AnimalOperation $operation)
    {
        $operation->visitLion($this);
    }
}

class Dolphin implements Animal
{
    public function speak()
    {
        echo 'ピィーピィー!';
    }

    public function accept(AnimalOperation $operation)
    {
        $operation->visitDolphin($this);
    }
}
```
訪問者を実装しましょう。
```php
class Speak implements AnimalOperation
{
    public function visitMonkey(Monkey $monkey)
    {
        $monkey->shout();
    }

    public function visitLion(Lion $lion)
    {
        $lion->roar();
    }

    public function visitDolphin(Dolphin $dolphin)
    {
        $dolphin->speak();
    }
}
```

以下のように使用します。
```php
$monkey = new Monkey();
$lion = new Lion();
$dolphin = new Dolphin();

$speak = new Speak();

$monkey->accept($speak);    // ウキキ!    
$lion->accept($speak);      // ガオー!
$dolphin->accept($speak);   // ピィーピィー!
```
単純に、動物に継承階層を持たせることでこれを実現することもできます。しかしその後、新しい行動を動物に追加する必要がある度、動物オブジェクトを修正する必要がでてくるでしょう。ですが今は動物オブジェクトを修正する必要はありません。例えば、動物オブジェクトにジャンプする行動を追加したいと言われたときは、新しい訪問者オブジェクトを作ることでシンプルに作ることができます。

```php
class Jump implements AnimalOperation
{
    public function visitMonkey(Monkey $monkey)
    {
        echo '6メートルのジャンプ!木の上に飛び乗った！';
    }

    public function visitLion(Lion $lion)
    {
        echo '2メートルのジャンプ！地面に戻った！';
    }

    public function visitDolphin(Dolphin $dolphin)
    {
        echo '水面を少し歩いて消えた';
    }
}
```
使用例はこちらです。
```php
$jump = new Jump();

$monkey->accept($speak);   // ウキキ!
$monkey->accept($jump);    // 6メートルのジャンプ!木の上に飛び乗った！

$lion->accept($speak);     // ガオー!
$lion->accept($jump);      // 2メートルのジャンプ！地面に戻った！

$dolphin->accept($speak);  // ピィーピィー!
$dolphin->accept($jump);   // 水面を少し歩いて消えた
```

💡 ストラテジ
--------

現実世界の例
> ソートについて考えてみましょう。私たちは最初、バブルソートを実装しました。しかし、データが大きくなり始め、バブルソートはとても遅くなりました。この問題に対処するため、私たちはクイックソートを実装しました。しかし、大きなデータセットには効果的だったクイックソートですが、小さなデータセットではとても遅いです。これに対処するため、小さなデータセットではバブルソートを、大きなデータセットではクイックソートを使う戦略(strategy/ストラテジ)を取ることにしました。

簡単に言えば
> ストラテジパターンは状況に応じてアルゴリズム、もしくは戦略を切り替えることを可能にします。

Wikipediaによれば
> コンピュータープログラミングにおいて、ストラテジパターン（ポリシーパターンとしても知られる）は振る舞いに関するデザインパターンです。実行時にアルゴリズムの動作を選択することが可能になります。

**プログラム例**

上の例をコードにしてみましょう。まず、戦略のインターフェースを作り、いくつかの戦略を実装します。

```php
interface SortStrategy
{
    public function sort(array $dataset): array;
}

class BubbleSortStrategy implements SortStrategy
{
    public function sort(array $dataset): array
    {
        echo "バブルソートでソートします";

        // ソートを実行する
        return $dataset;
    }
}

class QuickSortStrategy implements SortStrategy
{
    public function sort(array $dataset): array
    {
        echo "クイックソートでソートします";

        // ソートを実行する
        return $dataset;
    }
}
```

そして、戦略を利用することになるクライアントを実装します。
```php
class Sorter
{
    protected $sorterSmall;
    protected $sorterBig;

    public function __construct(SortStrategy $sorterSmall, SortStrategy $sorterBig)
    {
        $this->sorterSmall = $sorterSmall;
        $this->sorterBig = $sorterBig;
    }

    public function sort(array $dataset): array
    {
        if (count($dataset) > 5) {
            return $this->sorterBig->sort($dataset);
        } else {
            return $this->sorterSmall->sort($dataset);
        }
    }
}
```
これは以下のように使用できます。
```php
// 小さなデータセット
$smalldataset = [1, 3, 4, 2];

// 大きなデータセット
$bigdataset = [1, 4, 3, 2, 8, 10, 5, 6, 9, 7];

$sorter = new Sorter(new BubbleSortStrategy(), new QuickSortStrategy());

$sorter->sort($smalldataset); // 出力 : バブルソートでソートします

$sorter->sort($bigdataset); // 出力 : クイックソートでソートします
```

💢 ステート
-----
現実世界の例
> 絵を描くアプリケーションを使っていて、ペイントブラシを選択したところを想像してください。ブラシは選択した色によってその振る舞いを変化させます。例えば、あなたが赤色を選択したら赤色で描写され、青色を選択したら青色で描写されます。

簡単に言えば
> 状態（state/ステート）が変化したときにクラスの振る舞いを変化させることができます。

Wikipediaによれば
> ステートパターンはオブジェクト指向な方法でステートマシンを実装する、振る舞いにかんするソフトウェアデザインパターンです。ステートパターンでは、個々の状態をステートパターンのインターフェースの派生クラスで作り、状態の遷移をステートパターンのスーパークラスで定義されるメソッドの呼び出しとして作ることで、ステートマシンを実装します。
> ステートパターンは、パターンのインターフェースで定義されるメソッドの呼び出しによって現在の戦略を切り替えられるため、ストラテジパターンの一種であると解釈することもできます。

**プログラム例**

電話を例にしてみましょう。まず、状態のインターフェースとその実装を作成します。

```php
interface PhoneState {
    public function pickUp(): PhoneState;
    public function hangUp(): PhoneState;
    public function dial(): PhoneState;
}

// 状態の実装

// アイドル：受話器を置いている状態。
class PhoneStateIdle implements PhoneState {
    public function pickUp(): PhoneState {
        return new PhoneStatePickedUp();
    }
    public function hangUp(): PhoneState {
        throw new Exception("すでにアイドル中です");
    }
    public function dial(): PhoneState {
        throw new Exception("アイドル中に電話をかけることはできません。");
    }
}

// ピックアップ：受話器を取っている状態
class PhoneStatePickedUp implements PhoneState {
    public function pickUp(): PhoneState {
        throw new Exception("すでに受話器を取っています。");
    }
    public function hangUp(): PhoneState {
        return new PhoneStateIdle();
    }
    public function dial(): PhoneState {
        return new PhoneStateCalling();
    }
}

// コーリング：電話をかけている状態
class PhoneStateCalling implements PhoneState {
    public function pickUp(): PhoneState {
        throw new Exception("すでに受話器を取っています。");
    }
    public function hangUp(): PhoneState {
        return new PhoneStateIdle();
    }
    public function dial(): PhoneState {
        throw new Exception("すでに電話をかけています。");
    }
}
```

次に、さまざまな動作の呼び出しがあったときに状態を変更する、電話クラスを実装します。

```php
class Phone {
    private $state;

    public function __construct() {
        $this->state = new PhoneStateIdle();
    }
    public function pickUp() {
        $this->state = $this->state->pickUp();
    }
    public function hangUp() {
        $this->state = $this->state->hangUp();
    }
    public function dial() {
        $this->state = $this->state->dial();
    }
}
```

以下のように使用することで、関連する状態のメソッドを呼び出します。

```php
$phone = new Phone();

$phone->pickUp();
$phone->dial();
```

📒 テンプレートメソッド
---------------

現実世界の例
> これから家を建てるとします。建築する手順は以下のようになります：
> - 家の基礎を用意する
> - 壁を作る
> - 屋根をつける
> - 他のフロアを追加する

> この手順の並び順は変えることはできません。例えば、壁を作る前に屋根をつけることはできないでしょう。しかし、それぞれの手順自体は変更することができます。例えば、壁の材料を木、ポリエステル、石などに変更することが可能です。

簡単に言えば
> テンプレートメソッドはあるアルゴリズムがどのように実行されるかの骨組みを定義しますが、各ステップの実装は子クラスに委ねます。

Wikipediaによれば
> ソフトウェアエンジニアリングにおいて、テンプレートメソッドパターンは、操作内のアルゴリズムの骨組みを定義し、いくつかのステップをサブクラスに委ねる、振る舞いに関するデザインパターンです。これは、アルゴリズムの構造を変えることなく、アルゴリズムのあるステップを再定義することを可能とします。

**プログラム例**

あるビルドツールを考えてみましょう。このツールはテスト、コードリント、ビルド、ビルドレポートの作成（例えばコードカバレッジや、リンティングレポートなど）、そしてテストサーバへのデプロイを行います。

最初に、ビルドアルゴリズムの骨組みを指定するベースクラスを作成します。
```php
abstract class Builder
{

    // テンプレートメソッド
    final public function build()
    {
        $this->test();
        $this->lint();
        $this->assemble();
        $this->deploy();
    }

    abstract public function test();
    abstract public function lint();
    abstract public function assemble();
    abstract public function deploy();
}
```

次に、この抽象クラスを実装します。

```php
class AndroidBuilder extends Builder
{
    public function test()
    {
        echo 'Androidのテスト';
    }

    public function lint()
    {
        echo 'Androidのコードのリント';
    }

    public function assemble()
    {
        echo 'Androidビルドのアセンブル';
    }

    public function deploy()
    {
        echo 'Androidビルドをサーバにデプロイ';
    }
}

class IosBuilder extends Builder
{
    public function test()
    {
        echo 'iOSのテスト';
    }

    public function lint()
    {
        echo 'iOSのコードのリント';
    }

    public function assemble()
    {
        echo 'iOSビルドのアセンブル';
    }

    public function deploy()
    {
        echo 'iOSビルドをサーバにデプロイ';
    }
}
```
以下のように使用します。

```php
$androidBuilder = new AndroidBuilder();
$androidBuilder->build();

// 出力:
// Androidのテスト
// Androidのコードのリント
// Androidビルドのアセンブル
// Androidビルドをサーバにデプロイ

$iosBuilder = new IosBuilder();
$iosBuilder->build();

// 出力:
// iOSのテスト
// iOSのコードのリント
// iOSビルドのアセンブル
// iOSビルドをサーバにデプロイ
```

## 🚦 最後に

これで終わりです。これからもこの記事を改良し続けいくつもりなので、見直すためにこのレポジトリをwatch/starするといいかもしれません。さらに、アーキテクチャのパターンについて同じような記事を書く計画をしています。ご期待ください。

## 👬 コントリビュート

- issuesに報告
- 実装しプルリクエストを開く
- 評判を広める
- フィードバックを連絡 [![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/kamrify.svg?style=social&label=Follow%20%40kamrify)](https://twitter.com/kamrify)

## ライセンス

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)


## 翻訳者追記

英語は決して得意ではありませんが、なんとか翻訳できました。もし翻訳の間違いがあれば遠慮なく連絡してください。