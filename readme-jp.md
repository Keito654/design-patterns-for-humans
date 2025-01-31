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

|[生成に関するデザインパターン](#creational-design-patterns)|[構造に関するデザインパターン](#structural-design-patterns)|[振る舞いに関するデザインパターン](#behavioral-design-patterns)|
|:-|:-|:-|
|[シンプルファクトリー](#-simple-factory)|[アダプター](#-adapter)|[責任の連鎖/チェイン・レスポンシビリティ](#-chain-of-responsibility)|
|[ファクトリーメソッド](#-factory-method)|[ブリッジ](#-bridge)|[コマンド](#-command)|
|[アブストラクトファクトリー](#-abstract-factory)|[コンポジット](#-composite)|[イテレーター](#-iterator)|
|[ビルダー](#-builder)|[デコレーター](#-decorator)|[メディエーター](#-mediator)|
|[プロトタイプ](#-prototype)|[ファサード](#-facade)|[メメント](#-memento)|
|[シングルトン](#-singleton)|[フライウェイト](#-flyweight)|[オブザーバー](#-observer)|
||[プロキシ](#-proxy)|[ビジター](#-visitor)|
|||[ストラテジ](#-strategy)|
|||[ステート](#-state)|
|||[テンプレートメソッド](#-template-method)|

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

* [生成](#creational-design-patterns)
* [構造](#structural-design-patterns)
* [振る舞い](#behavioral-design-patterns)

生成に関するデザインパターン
==========================

簡単に言えば
> 生成に関するパターンは、オブジェクトまたは関連するオブジェクトのグループをインスタンス化する方法に重点を置いています。

Wikipediaによれば
> ソフトウェア エンジニアリングにおいて、生成に関するデザインパターンは、オブジェクトを作成するメカニズムを扱い、状況に適した方法でオブジェクトを作成しようとするデザインパターンです。オブジェクト生成の基本的な形式は、設計上の問題や設計の複雑さの増加につながる可能性があります。生成に関するデザインパターンは、オブジェクト生成を何らかの方法で制御することでこの問題を解決します。

 * [シンプルファクトリー](#-simple-factory)
 * [ファクトリーメソッド](#-factory-method)
 * [アブストラクトファクトリー](#-abstract-factory)
 * [ビルダー](#-builder)
 * [プロトタイプ](#-prototype)
 * [シングルトン](#-singleton)

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

Structural Design Patterns
==========================
簡単に言えば
> Structural patterns are mostly concerned with object composition or in other words how the entities can use each other. Or yet another explanation would be, they help in answering "How to build a software component?"

Wikipediaによれば
> In software engineering, structural design patterns are design patterns that ease the design by identifying a simple way to realize relationships between entities.

 * [Adapter](#-adapter)
 * [Bridge](#-bridge)
 * [Composite](#-composite)
 * [Decorator](#-decorator)
 * [Facade](#-facade)
 * [Flyweight](#-flyweight)
 * [Proxy](#-proxy)

🔌 Adapter
-------
現実世界の例
> Consider that you have some pictures in your memory card and you need to transfer them to your computer. In order to transfer them you need some kind of adapter that is compatible with your computer ports so that you can attach memory card to your computer. In this case card reader is an adapter.
> Another example would be the famous power adapter; a three legged plug can't be connected to a two pronged outlet, it needs to use a power adapter that makes it compatible with the two pronged outlet.
> Yet another example would be a translator translating words spoken by one person to another

簡単に言えば
> Adapter pattern lets you wrap an otherwise incompatible object in an adapter to make it compatible with another class.

Wikipediaによれば
> In software engineering, the adapter pattern is a software design pattern that allows the interface of an existing class to be used as another interface. It is often used to make existing classes work with others without modifying their source code.

**プログラム例**

Consider a game where there is a hunter and he hunts lions.

First we have an interface `Lion` that all types of lions have to implement

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
And hunter expects any implementation of `Lion` interface to hunt.
```php
class Hunter
{
    public function hunt(Lion $lion)
    {
        $lion->roar();
    }
}
```

Now let's say we have to add a `WildDog` in our game so that hunter can hunt that also. But we can't do that directly because dog has a different interface. To make it compatible for our hunter, we will have to create an adapter that is compatible

```php
// This needs to be added to the game
class WildDog
{
    public function bark()
    {
    }
}

// Adapter around wild dog to make it compatible with our game
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
And now the `WildDog` can be used in our game using `WildDogAdapter`.

```php
$wildDog = new WildDog();
$wildDogAdapter = new WildDogAdapter($wildDog);

$hunter = new Hunter();
$hunter->hunt($wildDogAdapter);
```

🚡 Bridge
------
現実世界の例
> Consider you have a website with different pages and you are supposed to allow the user to change the theme. What would you do? Create multiple copies of each of the pages for each of the themes or would you just create separate theme and load them based on the user's preferences? Bridge pattern allows you to do the second i.e.

![With and without the bridge pattern](https://cloud.githubusercontent.com/assets/11269635/23065293/33b7aea0-f515-11e6-983f-98823c9845ee.png)

簡単に言えば
> Bridge pattern is about preferring composition over inheritance. Implementation details are pushed from a hierarchy to another object with a separate hierarchy.

Wikipediaによれば
> The bridge pattern is a design pattern used in software engineering that is meant to "decouple an abstraction from its implementation so that the two can vary independently"

**プログラム例**

Translating our WebPage example from above. Here we have the `WebPage` hierarchy

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
        return "About page in " . $this->theme->getColor();
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
        return "Careers page in " . $this->theme->getColor();
    }
}
```
And the separate theme hierarchy
```php

interface Theme
{
    public function getColor();
}

class DarkTheme implements Theme
{
    public function getColor()
    {
        return 'Dark Black';
    }
}
class LightTheme implements Theme
{
    public function getColor()
    {
        return 'Off white';
    }
}
class AquaTheme implements Theme
{
    public function getColor()
    {
        return 'Light blue';
    }
}
```
And both the hierarchies
```php
$darkTheme = new DarkTheme();

$about = new About($darkTheme);
$careers = new Careers($darkTheme);

echo $about->getContent(); // "About page in Dark Black";
echo $careers->getContent(); // "Careers page in Dark Black";
```

🌿 Composite
-----------------

現実世界の例
> Every organization is composed of employees. Each of the employees has the same features i.e. has a salary, has some responsibilities, may or may not report to someone, may or may not have some subordinates etc.

簡単に言えば
> Composite pattern lets clients treat the individual objects in a uniform manner.

Wikipediaによれば
> In software engineering, the composite pattern is a partitioning design pattern. The composite pattern describes that a group of objects is to be treated in the same way as a single instance of an object. The intent of a composite is to "compose" objects into tree structures to represent part-whole hierarchies. Implementing the composite pattern lets clients treat individual objects and compositions uniformly.

**プログラム例**

Taking our employees example from above. Here we have different employee types

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

Then we have an organization which consists of several different types of employees

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

And then it can be used as

```php
// Prepare the employees
$john = new Developer('John Doe', 12000);
$jane = new Designer('Jane Doe', 15000);

// Add them to organization
$organization = new Organization();
$organization->addEmployee($john);
$organization->addEmployee($jane);

echo "Net salaries: " . $organization->getNetSalaries(); // Net Salaries: 27000
```

☕ Decorator
-------------

現実世界の例

> Imagine you run a car service shop offering multiple services. Now how do you calculate the bill to be charged? You pick one service and dynamically keep adding to it the prices for the provided services till you get the final cost. Here each type of service is a decorator.

簡単に言えば
> Decorator pattern lets you dynamically change the behavior of an object at run time by wrapping them in an object of a decorator class.

Wikipediaによれば
> In object-oriented programming, the decorator pattern is a design pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class. The decorator pattern is often useful for adhering to the Single Responsibility Principle, as it allows functionality to be divided between classes with unique areas of concern.

**プログラム例**

Lets take coffee for example. First of all we have a simple coffee implementing the coffee interface

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
        return 'Simple coffee';
    }
}
```
We want to make the code extensible to allow options to modify it if required. Lets make some add-ons (decorators)
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
        return $this->coffee->getDescription() . ', milk';
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
        return $this->coffee->getDescription() . ', whip';
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
        return $this->coffee->getDescription() . ', vanilla';
    }
}
```

Lets make a coffee now

```php
$someCoffee = new SimpleCoffee();
echo $someCoffee->getCost(); // 10
echo $someCoffee->getDescription(); // Simple Coffee

$someCoffee = new MilkCoffee($someCoffee);
echo $someCoffee->getCost(); // 12
echo $someCoffee->getDescription(); // Simple Coffee, milk

$someCoffee = new WhipCoffee($someCoffee);
echo $someCoffee->getCost(); // 17
echo $someCoffee->getDescription(); // Simple Coffee, milk, whip

$someCoffee = new VanillaCoffee($someCoffee);
echo $someCoffee->getCost(); // 20
echo $someCoffee->getDescription(); // Simple Coffee, milk, whip, vanilla
```

📦 Facade
----------------

現実世界の例
> How do you turn on the computer? "Hit the power button" you say! That is what you believe because you are using a simple interface that computer provides on the outside, internally it has to do a lot of stuff to make it happen. This simple interface to the complex subsystem is a facade.

簡単に言えば
> Facade pattern provides a simplified interface to a complex subsystem.

Wikipediaによれば
> A facade is an object that provides a simplified interface to a larger body of code, such as a class library.

**プログラム例**

Taking our computer example from above. Here we have the computer class

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
        echo "Ready to be used!";
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
Here we have the facade
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
Now to use the facade
```php
$computer = new ComputerFacade(new Computer());
$computer->turnOn(); // Ouch! Beep beep! Loading.. Ready to be used!
$computer->turnOff(); // Bup bup buzzz! Haah! Zzzzz
```

🍃 Flyweight
---------

現実世界の例
> Did you ever have fresh tea from some stall? They often make more than one cup that you demanded and save the rest for any other customer so to save the resources e.g. gas etc. Flyweight pattern is all about that i.e. sharing.

簡単に言えば
> It is used to minimize memory usage or computational expenses by sharing as much as possible with similar objects.

Wikipediaによれば
> In computer programming, flyweight is a software design pattern. A flyweight is an object that minimizes memory use by sharing as much data as possible with other similar objects; it is a way to use objects in large numbers when a simple repeated representation would use an unacceptable amount of memory.

**プログラム例**

Translating our tea example from above. First of all we have tea types and tea maker

```php
// Anything that will be cached is flyweight.
// Types of tea here will be flyweights.
class KarakTea
{
}

// Acts as a factory and saves the tea
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

Then we have the `TeaShop` which takes orders and serves them

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
            echo "Serving tea to table# " . $table;
        }
    }
}
```
And it can be used as below

```php
$teaMaker = new TeaMaker();
$shop = new TeaShop($teaMaker);

$shop->takeOrder('less sugar', 1);
$shop->takeOrder('more milk', 2);
$shop->takeOrder('without sugar', 5);

$shop->serve();
// Serving tea to table# 1
// Serving tea to table# 2
// Serving tea to table# 5
```

🎱 Proxy
-------------------
現実世界の例
> Have you ever used an access card to go through a door? There are multiple options to open that door i.e. it can be opened either using access card or by pressing a button that bypasses the security. The door's main functionality is to open but there is a proxy added on top of it to add some functionality. Let me better explain it using the code example below.

簡単に言えば
> Using the proxy pattern, a class represents the functionality of another class.

Wikipediaによれば
> A proxy, in its most general form, is a class functioning as an interface to something else. A proxy is a wrapper or agent object that is being called by the client to access the real serving object behind the scenes. Use of the proxy can simply be forwarding to the real object, or can provide additional logic. In the proxy extra functionality can be provided, for example caching when operations on the real object are resource intensive, or checking preconditions before operations on the real object are invoked.

**プログラム例**

Taking our security door example from above. Firstly we have the door interface and an implementation of door

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
        echo "Opening lab door";
    }

    public function close()
    {
        echo "Closing the lab door";
    }
}
```
Then we have a proxy to secure any doors that we want
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
            echo "Big no! It ain't possible.";
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
And here is how it can be used
```php
$door = new SecuredDoor(new LabDoor());
$door->open('invalid'); // Big no! It ain't possible.

$door->open('$ecr@t'); // Opening lab door
$door->close(); // Closing lab door
```
Yet another example would be some sort of data-mapper implementation. For example, I recently made an ODM (Object Data Mapper) for MongoDB using this pattern where I wrote a proxy around mongo classes while utilizing the magic method `__call()`. All the method calls were proxied to the original mongo class and result retrieved was returned as it is but in case of `find` or `findOne` data was mapped to the required class objects and the object was returned instead of `Cursor`.

Behavioral Design Patterns
==========================

簡単に言えば
> It is concerned with assignment of responsibilities between the objects. What makes them different from structural patterns is they don't just specify the structure but also outline the patterns for message passing/communication between them. Or in other words, they assist in answering "How to run a behavior in software component?"

Wikipediaによれば
> In software engineering, behavioral design patterns are design patterns that identify common communication patterns between objects and realize these patterns. By doing so, these patterns increase flexibility in carrying out this communication.

* [Chain of Responsibility](#-chain-of-responsibility)
* [Command](#-command)
* [Iterator](#-iterator)
* [Mediator](#-mediator)
* [Memento](#-memento)
* [Observer](#-observer)
* [Visitor](#-visitor)
* [Strategy](#-strategy)
* [State](#-state)
* [Template Method](#-template-method)

🔗 Chain of Responsibility
-----------------------

現実世界の例
> For example, you have three payment methods (`A`, `B` and `C`) setup in your account; each having a different amount in it. `A` has 100 USD, `B` has 300 USD and `C` having 1000 USD and the preference for payments is chosen as `A` then `B` then `C`. You try to purchase something that is worth 210 USD. Using Chain of Responsibility, first of all account `A` will be checked if it can make the purchase, if yes purchase will be made and the chain will be broken. If not, request will move forward to account `B` checking for amount if yes chain will be broken otherwise the request will keep forwarding till it finds the suitable handler. Here `A`, `B` and `C` are links of the chain and the whole phenomenon is Chain of Responsibility.

簡単に言えば
> It helps building a chain of objects. Request enters from one end and keeps going from object to object till it finds the suitable handler.

Wikipediaによれば
> In object-oriented design, the chain-of-responsibility pattern is a design pattern consisting of a source of command objects and a series of processing objects. Each processing object contains logic that defines the types of command objects that it can handle; the rest are passed to the next processing object in the chain.

**プログラム例**

Translating our account example above. First of all we have a base account having the logic for chaining the accounts together and some accounts

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
            echo sprintf('Paid %s using %s' . PHP_EOL, $amountToPay, get_called_class());
        } elseif ($this->successor) {
            echo sprintf('Cannot pay using %s. Proceeding ..' . PHP_EOL, get_called_class());
            $this->successor->pay($amountToPay);
        } else {
            throw new Exception('None of the accounts have enough balance');
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

Now let's prepare the chain using the links defined above (i.e. Bank, Paypal, Bitcoin)

```php
// Let's prepare a chain like below
//      $bank->$paypal->$bitcoin
//
// First priority bank
//      If bank can't pay then paypal
//      If paypal can't pay then bit coin

$bank = new Bank(100);          // Bank with balance 100
$paypal = new Paypal(200);      // Paypal with balance 200
$bitcoin = new Bitcoin(300);    // Bitcoin with balance 300

$bank->setNext($paypal);
$paypal->setNext($bitcoin);

// Let's try to pay using the first priority i.e. bank
$bank->pay(259);

// Output will be
// ==============
// Cannot pay using bank. Proceeding ..
// Cannot pay using paypal. Proceeding ..:
// Paid 259 using Bitcoin!
```

👮 Command
-------

現実世界の例
> A generic example would be you ordering food at a restaurant. You (i.e. `Client`) ask the waiter (i.e. `Invoker`) to bring some food (i.e. `Command`) and waiter simply forwards the request to Chef (i.e. `Receiver`) who has the knowledge of what and how to cook.
> Another example would be you (i.e. `Client`) switching on (i.e. `Command`) the television (i.e. `Receiver`) using a remote control (`Invoker`).

簡単に言えば
> Allows you to encapsulate actions in objects. The key idea behind this pattern is to provide the means to decouple client from receiver.

Wikipediaによれば
> In object-oriented programming, the command pattern is a behavioral design pattern in which an object is used to encapsulate all information needed to perform an action or trigger an event at a later time. This information includes the method name, the object that owns the method and values for the method parameters.

**プログラム例**

First of all we have the receiver that has the implementation of every action that could be performed
```php
// Receiver
class Bulb
{
    public function turnOn()
    {
        echo "Bulb has been lit";
    }

    public function turnOff()
    {
        echo "Darkness!";
    }
}
```
then we have an interface that each of the commands are going to implement and then we have a set of commands
```php
interface Command
{
    public function execute();
    public function undo();
    public function redo();
}

// Command
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
Then we have an `Invoker` with whom the client will interact to process any commands
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
Finally let's see how we can use it in our client
```php
$bulb = new Bulb();

$turnOn = new TurnOn($bulb);
$turnOff = new TurnOff($bulb);

$remote = new RemoteControl();
$remote->submit($turnOn); // Bulb has been lit!
$remote->submit($turnOff); // Darkness!
```

Command pattern can also be used to implement a transaction based system. Where you keep maintaining the history of commands as soon as you execute them. If the final command is successfully executed, all good otherwise just iterate through the history and keep executing the `undo` on all the executed commands.

➿ Iterator
--------

現実世界の例
> An old radio set will be a good example of iterator, where user could start at some channel and then use next or previous buttons to go through the respective channels. Or take an example of MP3 player or a TV set where you could press the next and previous buttons to go through the consecutive channels or in other words they all provide an interface to iterate through the respective channels, songs or radio stations.  

簡単に言えば
> It presents a way to access the elements of an object without exposing the underlying presentation.

Wikipediaによれば
> In object-oriented programming, the iterator pattern is a design pattern in which an iterator is used to traverse a container and access the container's elements. The iterator pattern decouples algorithms from containers; in some cases, algorithms are necessarily container-specific and thus cannot be decoupled.

**プログラム例**

In PHP it is quite easy to implement using SPL (Standard PHP Library). Translating our radio stations example from above. First of all we have `RadioStation`

```php
class RadioStation
{
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
Then we have our iterator

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
And then it can be used as
```php
$stationList = new StationList();

$stationList->addStation(new RadioStation(89));
$stationList->addStation(new RadioStation(101));
$stationList->addStation(new RadioStation(102));
$stationList->addStation(new RadioStation(103.2));

foreach($stationList as $station) {
    echo $station->getFrequency() . PHP_EOL;
}

$stationList->removeStation(new RadioStation(89)); // Will remove station 89
```

👽 Mediator
========

現実世界の例
> A general example would be when you talk to someone on your mobile phone, there is a network provider sitting between you and them and your conversation goes through it instead of being directly sent. In this case network provider is mediator.

簡単に言えば
> Mediator pattern adds a third party object (called mediator) to control the interaction between two objects (called colleagues). It helps reduce the coupling between the classes communicating with each other. Because now they don't need to have the knowledge of each other's implementation.

Wikipediaによれば
> In software engineering, the mediator pattern defines an object that encapsulates how a set of objects interact. This pattern is considered to be a behavioral pattern due to the way it can alter the program's running behavior.

**プログラム例**

Here is the simplest example of a chat room (i.e. mediator) with users (i.e. colleagues) sending messages to each other.

First of all, we have the mediator i.e. the chat room

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

Then we have our users i.e. colleagues
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
And the usage
```php
$mediator = new ChatRoom();

$john = new User('John Doe', $mediator);
$jane = new User('Jane Doe', $mediator);

$john->send('Hi there!');
$jane->send('Hey!');

// Output will be
// Feb 14, 10:58 [John]: Hi there!
// Feb 14, 10:58 [Jane]: Hey!
```

💾 Memento
-------
現実世界の例
> Take the example of calculator (i.e. originator), where whenever you perform some calculation the last calculation is saved in memory (i.e. memento) so that you can get back to it and maybe get it restored using some action buttons (i.e. caretaker).

簡単に言えば
> Memento pattern is about capturing and storing the current state of an object in a manner that it can be restored later on in a smooth manner.

Wikipediaによれば
> The memento pattern is a software design pattern that provides the ability to restore an object to its previous state (undo via rollback).

Usually useful when you need to provide some sort of undo functionality.

**プログラム例**

Lets take an example of text editor which keeps saving the state from time to time and that you can restore if you want.

First of all we have our memento object that will be able to hold the editor state

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

Then we have our editor i.e. originator that is going to use memento object

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

And then it can be used as

```php
$editor = new Editor();

// Type some stuff
$editor->type('This is the first sentence.');
$editor->type('This is second.');

// Save the state to restore to : This is the first sentence. This is second.
$saved = $editor->save();

// Type some more
$editor->type('And this is third.');

// Output: Content before Saving
echo $editor->getContent(); // This is the first sentence. This is second. And this is third.

// Restoring to last saved state
$editor->restore($saved);

$editor->getContent(); // This is the first sentence. This is second.
```

😎 Observer
--------
現実世界の例
> A good example would be the job seekers where they subscribe to some job posting site and they are notified whenever there is a matching job opportunity.   

簡単に言えば
> Defines a dependency between objects so that whenever an object changes its state, all its dependents are notified.

Wikipediaによれば
> The observer pattern is a software design pattern in which an object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.

**プログラム例**

Translating our example from above. First of all we have job seekers that need to be notified for a job posting
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
        // Do something with the job posting
        echo 'Hi ' . $this->name . '! New job posted: '. $job->getTitle();
    }
}
```
Then we have our job postings to which the job seekers will subscribe
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
Then it can be used as
```php
// Create subscribers
$johnDoe = new JobSeeker('John Doe');
$janeDoe = new JobSeeker('Jane Doe');

// Create publisher and attach subscribers
$jobPostings = new EmploymentAgency();
$jobPostings->attach($johnDoe);
$jobPostings->attach($janeDoe);

// Add a new job and see if subscribers get notified
$jobPostings->addJob(new JobPost('Software Engineer'));

// Output
// Hi John Doe! New job posted: Software Engineer
// Hi Jane Doe! New job posted: Software Engineer
```

🏃 Visitor
-------
現実世界の例
> Consider someone visiting Dubai. They just need a way (i.e. visa) to enter Dubai. After arrival, they can come and visit any place in Dubai on their own without having to ask for permission or to do some leg work in order to visit any place here; just let them know of a place and they can visit it. Visitor pattern lets you do just that, it helps you add places to visit so that they can visit as much as they can without having to do any legwork.

簡単に言えば
> Visitor pattern lets you add further operations to objects without having to modify them.

Wikipediaによれば
> In object-oriented programming and software engineering, the visitor design pattern is a way of separating an algorithm from an object structure on which it operates. A practical result of this separation is the ability to add new operations to existing object structures without modifying those structures. It is one way to follow the open/closed principle.

**プログラム例**

Let's take an example of a zoo simulation where we have several different kinds of animals and we have to make them Sound. Let's translate this using visitor pattern

```php
// Visitee
interface Animal
{
    public function accept(AnimalOperation $operation);
}

// Visitor
interface AnimalOperation
{
    public function visitMonkey(Monkey $monkey);
    public function visitLion(Lion $lion);
    public function visitDolphin(Dolphin $dolphin);
}
```
Then we have our implementations for the animals
```php
class Monkey implements Animal
{
    public function shout()
    {
        echo 'Ooh oo aa aa!';
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
        echo 'Roaaar!';
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
        echo 'Tuut tuttu tuutt!';
    }

    public function accept(AnimalOperation $operation)
    {
        $operation->visitDolphin($this);
    }
}
```
Let's implement our visitor
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

And then it can be used as
```php
$monkey = new Monkey();
$lion = new Lion();
$dolphin = new Dolphin();

$speak = new Speak();

$monkey->accept($speak);    // Ooh oo aa aa!    
$lion->accept($speak);      // Roaaar!
$dolphin->accept($speak);   // Tuut tutt tuutt!
```
We could have done this simply by having an inheritance hierarchy for the animals but then we would have to modify the animals whenever we would have to add new actions to animals. But now we will not have to change them. For example, let's say we are asked to add the jump behavior to the animals, we can simply add that by creating a new visitor i.e.

```php
class Jump implements AnimalOperation
{
    public function visitMonkey(Monkey $monkey)
    {
        echo 'Jumped 20 feet high! on to the tree!';
    }

    public function visitLion(Lion $lion)
    {
        echo 'Jumped 7 feet! Back on the ground!';
    }

    public function visitDolphin(Dolphin $dolphin)
    {
        echo 'Walked on water a little and disappeared';
    }
}
```
And for the usage
```php
$jump = new Jump();

$monkey->accept($speak);   // Ooh oo aa aa!
$monkey->accept($jump);    // Jumped 20 feet high! on to the tree!

$lion->accept($speak);     // Roaaar!
$lion->accept($jump);      // Jumped 7 feet! Back on the ground!

$dolphin->accept($speak);  // Tuut tutt tuutt!
$dolphin->accept($jump);   // Walked on water a little and disappeared
```

💡 Strategy
--------

現実世界の例
> Consider the example of sorting, we implemented bubble sort but the data started to grow and bubble sort started getting very slow. In order to tackle this we implemented Quick sort. But now although the quick sort algorithm was doing better for large datasets, it was very slow for smaller datasets. In order to handle this we implemented a strategy where for small datasets, bubble sort will be used and for larger, quick sort.

簡単に言えば
> Strategy pattern allows you to switch the algorithm or strategy based upon the situation.

Wikipediaによれば
> In computer programming, the strategy pattern (also known as the policy pattern) is a behavioural software design pattern that enables an algorithm's behavior to be selected at runtime.

**プログラム例**

Translating our example from above. First of all we have our strategy interface and different strategy implementations

```php
interface SortStrategy
{
    public function sort(array $dataset): array;
}

class BubbleSortStrategy implements SortStrategy
{
    public function sort(array $dataset): array
    {
        echo "Sorting using bubble sort";

        // Do sorting
        return $dataset;
    }
}

class QuickSortStrategy implements SortStrategy
{
    public function sort(array $dataset): array
    {
        echo "Sorting using quick sort";

        // Do sorting
        return $dataset;
    }
}
```

And then we have our client that is going to use any strategy
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
And it can be used as
```php
$smalldataset = [1, 3, 4, 2];
$bigdataset = [1, 4, 3, 2, 8, 10, 5, 6, 9, 7];

$sorter = new Sorter(new BubbleSortStrategy(), new QuickSortStrategy());

$sorter->sort($dataset); // Output : Sorting using bubble sort

$sorter->sort($bigdataset); // Output : Sorting using quick sort
```

💢 State
-----
現実世界の例
> Imagine you are using some drawing application, you choose the paint brush to draw. Now the brush changes its behavior based on the selected color i.e. if you have chosen red color it will draw in red, if blue then it will be in blue etc.  

簡単に言えば
> It lets you change the behavior of a class when the state changes.

Wikipediaによれば
> The state pattern is a behavioral software design pattern that implements a state machine in an object-oriented way. With the state pattern, a state machine is implemented by implementing each individual state as a derived class of the state pattern interface, and implementing state transitions by invoking methods defined by the pattern's superclass.
> The state pattern can be interpreted as a strategy pattern which is able to switch the current strategy through invocations of methods defined in the pattern's interface.

**プログラム例**

Let's take an example of a phone. First of all we have our state interface and some state implementations

```php
interface PhoneState {
    public function pickUp(): PhoneState;
    public function hangUp(): PhoneState;
    public function dial(): PhoneState;
}

// states implementation
class PhoneStateIdle implements PhoneState {
    public function pickUp(): PhoneState {
        return new PhoneStatePickedUp();
    }
    public function hangUp(): PhoneState {
        throw new Exception("already idle");
    }
    public function dial(): PhoneState {
        throw new Exception("unable to dial in idle state");
    }
}

class PhoneStatePickedUp implements PhoneState {
    public function pickUp(): PhoneState {
        throw new Exception("already picked up");
    }
    public function hangUp(): PhoneState {
        return new PhoneStateIdle();
    }
    public function dial(): PhoneState {
        return new PhoneStateCalling();
    }
}

class PhoneStateCalling implements PhoneState {
    public function pickUp(): PhoneState {
        throw new Exception("already picked up");
    }
    public function hangUp(): PhoneState {
        return new PhoneStateIdle();
    }
    public function dial(): PhoneState {
        throw new Exception("already dialing");
    }
}
```

Then we have our Phone class that changes the state on different behavior calls

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

And then it can be used as follows and it will call the relevant state methods:

```php
$phone = new Phone();

$phone->pickUp();
$phone->dial();
```

📒 Template Method
---------------

現実世界の例
> Suppose we are getting some house built. The steps for building might look like
> - Prepare the base of house
> - Build the walls
> - Add roof
> - Add other floors

> The order of these steps could never be changed i.e. you can't build the roof before building the walls etc but each of the steps could be modified for example walls can be made of wood or polyester or stone.

簡単に言えば
> Template method defines the skeleton of how a certain algorithm could be performed, but defers the implementation of those steps to the children classes.

Wikipediaによれば
> In software engineering, the template method pattern is a behavioral design pattern that defines the program skeleton of an algorithm in an operation, deferring some steps to subclasses. It lets one redefine certain steps of an algorithm without changing the algorithm's structure.

**プログラム例**

Imagine we have a build tool that helps us test, lint, build, generate build reports (i.e. code coverage reports, linting report etc) and deploy our app on the test server.

First of all we have our base class that specifies the skeleton for the build algorithm
```php
abstract class Builder
{

    // Template method
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

Then we can have our implementations

```php
class AndroidBuilder extends Builder
{
    public function test()
    {
        echo 'Running android tests';
    }

    public function lint()
    {
        echo 'Linting the android code';
    }

    public function assemble()
    {
        echo 'Assembling the android build';
    }

    public function deploy()
    {
        echo 'Deploying android build to server';
    }
}

class IosBuilder extends Builder
{
    public function test()
    {
        echo 'Running ios tests';
    }

    public function lint()
    {
        echo 'Linting the ios code';
    }

    public function assemble()
    {
        echo 'Assembling the ios build';
    }

    public function deploy()
    {
        echo 'Deploying ios build to server';
    }
}
```
And then it can be used as

```php
$androidBuilder = new AndroidBuilder();
$androidBuilder->build();

// Output:
// Running android tests
// Linting the android code
// Assembling the android build
// Deploying android build to server

$iosBuilder = new IosBuilder();
$iosBuilder->build();

// Output:
// Running ios tests
// Linting the ios code
// Assembling the ios build
// Deploying ios build to server
```

## 🚦 Wrap Up Folks

And that about wraps it up. I will continue to improve this, so you might want to watch/star this repository to revisit. Also, I have plans on writing the same about the architectural patterns, stay tuned for it.

## 👬 Contribution

- Report issues
- Open pull request with improvements
- Spread the word
- Reach out with any feedback [![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/kamrify.svg?style=social&label=Follow%20%40kamrify)](https://twitter.com/kamrify)

## License

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
