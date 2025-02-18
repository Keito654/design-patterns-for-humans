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

## 🚦 最後に

And that about wraps it up. I will continue to improve this, so you might want to watch/star this repository to revisit. Also, I have plans on writing the same about the architectural patterns, stay tuned for it.

## 👬 コントリビュート

- issuesに報告
- 実装と共にプルリクエストを開く
- 評判を広める
- フィードバックを連絡 [![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/kamrify.svg?style=social&label=Follow%20%40kamrify)](https://twitter.com/kamrify)

## ライセンス

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
