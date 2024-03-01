# PHP Coding Handbook

ほとんどのセクションは 2 つの部分に分かれています:

1. すべてのルールの概要と簡単な例
2. 各ルールでは、「すべきこと」と「してはいけないこと」の例が示されています

**Icon Legend**:

`·` Space, `⇥` Tab, `↵` Enter/Return

<!-- ---------------------------------------------------------------------- -->

## Table of Contents

1. [**一般的なルール**](#1-一般的なルール)
    1. [基本的なコーディング](#11-基本的なコーディング仕様)
    2. [ファイル様](#12-ファイル)
    3. [行](#13-行)
    4. [インデント](#14-インデント)
    5. [キーワード](#15-キーワード処理)
3. [**スケルトン**](#2-スケルトン)
3. [**宣言文と名前空間とインポート文**](#3-宣言文と名前空間とインポート文)
4. [**クラスとプロパティとメソッド**](#4-クラスとプロパティとメソッド)
    1. [継承と実装](#41-継承と実装)
    2. [トレイトの利用](#42-トレイトの利用)
    3. [プロパティと定数](#43-プロパティと定数)
    4. [メソッドと関数](#44-メソッドと関数)
    5. [メソッドと関数の引数](#45-メソッドと関数の引数)
    6. [abstractとfinalとstatic](#46-abstractとfinalとstatic)
    7. [メソッドと関数の呼び出し](#47-メソッドと関数の呼び出し)
5. [**制御構造**](#5-制御構造)
	1. [ifとelseifとelse](#51-ifとelseifとelse)
	2. [switchとcase](#52-switchとcase)
	3. [whileとdo-while](#53-whileとdo-while)
	4. [for](#54-for)
    5. [foreach](#55-foreach)
    6. [try-catch-finally](#56-try-catch-finally)
6. [**演算子**](#6-演算子)
	1. [単項演算子](#61-単項演算子)
	2. [二項演算子](#62-二項演算子)
	3. [三項演算子](#63-三項演算子)
7. [**無名関数クロージャ**](#7-無名関数クロージャ)
8. [**無名クラス**](#8-無名クラス)
9. [**コメント**](#9-コメント)
    1. [一行コメント](#91-一行コメント)
    2. [複数行のコメント](#92-複数行のコメント)
    3. [ヘッダーコメント](#93-ヘッダーコメント)
    4. [区切りコメント](#94-区切りコメント)
    5. [コメント](#95-コメント)
    6. [コードのブロック](#96-コードのブロック)
    7. [曖昧な数字](#97-曖昧な数字)
    8. [外部変数](#98-外部変数)

<!-- ---------------------------------------------------------------------- -->

## 1. 一般的なルール

1. **[基本的なコーディング仕様](#11-基本的なコーディング仕様)**
2. **[ファイル](#12-ファイル)**
3. **[行](#13-行)**
4. **[インデント](#14-インデント)**
5. **[キーワードと型](#15-キーワードと型)**

&#9650; [Table of Contents](#table-of-contents)

### 1.1 基本的なコーディング仕様

- ファイルでは`<?php`タグと`<?=`タグのみを使用しなければいけません。

- ファイルではBOMなしのUTF-8のみを使用しなければいけません。

- ファイルはシンボル(クラス、関数、定数など)の宣言*か*副作用のある処理(出力の生成や.iniの設定など)の*いずれか*である必要があり、両方を含まないほうが望ましいです(SHOULD NOT)。

- 名前空間とクラスについてはオートロードに関するPSR([[PSR-0], [PSR-4]])に従わなければいけません。

- クラス名は`StudlyCaps`(スタッドリーキャプス)で宣言しなければいけません。

- クラス定数は大文字とアンダースコアの区切り文字で宣言しなければいけません。

- メソッド名は`camelCase`(キャメルケース)で宣言しなければいけません。

&#9650; [一般的なルール](#1-一般的なルール)

<!-- ------------------------------ -->

### 1.2 ファイル

すべてのPHPファイルは行の末尾をUnix式のLF(ラインフィード)で終わらせなければいけません。

すべてのPHPファイルはLFで終わる空ではない行で終わらせなければいけません。

PHPのコードのみで構成されるファイルは閉じタグの `?>`を省略しなければいけません。

&#9650; [一般的なルール](#1-一般的なルール)

<!-- ------------------------------ -->

### 1.3 行

1行の文字数にハードリミットを設けてはいけません。

1行の文字数のソフトリミットは120文字でなければいけません。

1行の文字数は80字を超えないことが望ましく(SHOUD NOT)、それを越える場合は80文字を超えないように複数の行に分割した方が望ましいです(SHOUD)。

行末に空白文字があってはいけません。

明示的に禁止されている場合を除き、可読性を上げる目的で関係のあるコードブロックを示すために空行を挿入しても構いません。

1つの行に複数の処理を記述してはいけません。

&#9650; [一般的なルール](#1-一般的なルール)

<!-- ------------------------------ -->

### 1.4 インデント

コードは各レベルごとにスペース4つで表現しなければなりません、またインデントにタブを使用してはいけません。

&#9650; [一般的なルール](#1-一般的なルール)

<!-- ------------------------------ -->

### 1.5 キーワードと型

全てのPHPの予約語と型 [[1]][keywords][[2]][types]は小文字で記述しなければなりません。

将来のPHPにおいて新しく追加される型やキーワードは小文字で記述しなければなりません。

型のキーワードは短いものを使わなければなりません。
例: `boolean`の代わりに`bool`、`integer`の代わりに`int`

<!-- ---------------------------------------------------------------------- -->

## 2. スケルトン

このセクションでは、最小限の PHP ファイルとその最小要件を紹介します。

行ごとの内訳:

* **Line 1**: PHPのオープンタグ
* **Line 2**: 空白行
* **Line 3**: あなたのコード
* **Line 4**: 空白行
* **Line 5**: End-of-fileコメント
* **Line 6**: 空白行

<pre lang=php>
&lt;?php

// your code

// EOF
 
</pre>

<!-- ---------------------------------------------------------------------- -->

## 3. 宣言文と名前空間とインポート文

PHPファイルのヘッダはいくつかのブロックから成り立つ可能性があります。もし存在するならば、以下に示すそれぞれのブロックは1つの空行で分けられていなければならず、またそれぞれのブロックの中に空行を含んではいけません。それぞれのブロックは以下に示す順に並んでいなければいけませんが、関係のないものは省略しても構いません。

* PHPの開始タグ `<?php`
* ファイルレベルのphpDocブロック
* 1つ以上の宣言文
* ファイルのネームスペース宣言
* 1つ以上のクラス`use` インポート文
* 1つ以上の関数`use`インポート文
* 1つ以上の定数`use`インポート文
* 以降はコード

ファイルにHTMLとPHPが混ざって含まれている場合、上記の内容は引き続き適用可能ですが、その場合はたとえ残りのコード部分にPHPの閉じタグが含まれていて、HTMLとPHPが混在していてもヘッダ部分をファイルの冒頭に配置しなければいけません。

PHPの開始タグがファイルの最初の行に含まれる場合、PHPの開始・終了タグの外側でマークアップの記述がない限り、その行は開始タグ以外の記述を含まないようにしなければいけません。

インポート文は先頭をバックスラッシュで始めず、常に完全修飾名で記述してください。

以下にこの節全体の記述例を示します。

~~~php
<?php

/**
 * This file contains an example of coding styles.
 */

declare(strict_types=1);

namespace Vendor\Package;

use Vendor\Package\{ClassA as A, ClassB, ClassC as C};
use Vendor\Package\SomeNamespace\ClassD as D;
use Vendor\Package\AnotherNamespace\ClassE as E;

use function Vendor\Package\{functionA, functionB, functionC};
use function Another\Vendor\functionD;

use const Vendor\Package\{CONSTANT_A, CONSTANT_B, CONSTANT_C};
use const Another\Vendor\CONSTANT_D;

/**
 * FooBar is an example class.
 */
class FooBar
{
    // ... additional PHP code ...
}

~~~

名前空間をグループ化するときに2階層を超えてはいけません。したがって、以下に示すものが許容されるもっとも深い階層となります。

~~~php
<?php

use Vendor\Package\SomeNamespace\{
    SubnamespaceOne\ClassA,
    SubnamespaceOne\ClassB,
    SubnamespaceTwo\ClassY,
    ClassZ,
};
~~~

また、以下のものは許容されません。

~~~php
<?php

use Vendor\Package\SomeNamespace\{
    SubnamespaceOne\AnotherNamespace\ClassA,
    SubnamespaceOne\ClassB,
    ClassZ,
};
~~~

strict_typesの定義をPHPタグの外でマークアップの記述を含むファイルで宣言したい場合、その宣言はファイルの先頭でPHPの開始タグ、strict_typeの宣言、PHPの閉じタグを含んでいなければいけません。

例えば、

~~~php
<?php declare(strict_types=1) ?>
<html>
<body>
    <?php
        // ... additional PHP code ...
    ?>
</body>
</html>
~~~

declare文は空白文字を含まないようにしなければならず、かつ`declare(strict_types=1)`と正確に一致していなければいけません。(セミコロンの区切り文字は任意)

declareブロック文は下記の通りのフォーマットで書かなければいけません。括弧やスペースの位置に注意してください。

~~~php
declare(ticks=1) {
    // some code
}
~~~

<!-- ---------------------------------------------------------------------- -->

## 4. クラスとプロパティとメソッド

「クラス(class)」という用語はクラス、インターフェース、トレイトの全てを指します。

閉じ中括弧のあと、同じ行にコメントや文が続いてはいけません

クラスをインスタンス化するとき、コンストラクタに渡す引数がなかったとしても括弧はかならず必要です。

~~~php
new Foo();
~~~

1. **[継承と実装](#41-継承と実装)**
2. **[トレイトの利用](#42-トレイトの利用)**
3. **[プロパティと定数](#43-プロパティと定数)**
4. **[メソッドと関数](#44-メソッドと関数)**
5. **[メソッドと関数の引数](#45-メソッドと関数の引数)**
6. **[abstractとfinalとstatic](#46-abstractとfinalとstatic)**
7. **[メソッドと関数の呼び出し](#47-メソッドと関数の呼び出し)**

&#9650; [Table of Contents](#table-of-contents)

### 4.1 継承と実装

`extends`と`implements`のキーワードはクラス名の宣言と同じ行にしなければいけません。

クラス開始の中括弧は独立した行に記述されなければならず、終了の中括弧はクラス本文の次の行に記述する必要があります。

開始の中括弧は独立した行に記述されなければならず、かつその前後に空行があってはいけません。

終了の中括弧は独立した行に記述されなければならず、かつその前に空行があってはいけません。

~~~php
<?php

namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
~~~

インターフェースの`implements`のリストと`extends`は複数行に分割することができ、その場合はそれぞれの行を1段階インデントしてください。その場合、最初の要素を次の行に置く必要があり、1行あたりインターフェースを1つずつ書く必要があります。

~~~php
<?php

namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
~~~

&#9650; [クラスとプロパティとメソッド](#4-クラスとプロパティとメソッド)

<!-- ------------------------------ -->

### 4.2 トレイトの利用

`use`キーワードを用いてトレイトを実装する時はクラス本文の中、開始の中括弧の次の行に定義しなければいけません。

~~~php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;
}
~~~

複数のトレイトをインポートする場合、1行に1つずつ、それぞれ`use`キーワードを単独で用いて宣言しなければいけません。

~~~php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;
use Vendor\Package\SecondTrait;
use Vendor\Package\ThirdTrait;

class ClassName
{
    use FirstTrait;
    use SecondTrait;
    use ThirdTrait;
}
~~~

`use`を用いたインポート以降に何も記述がない場合、終了の中括弧は`use`文の直後になければいけません。

~~~php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;
}
~~~

それ以外の場合、`use`インポート文の後は空行が必要です。

~~~php
<?php

namespace Vendor\Package;

use Vendor\Package\FirstTrait;

class ClassName
{
    use FirstTrait;

    private $property;
}
~~~

`insteadof`や`as`演算子を使用する場合は下記に示すようにインデント、スペース、改行を使用してください。

~~~php
<?php

class Talker
{
    use A, B, C {
        B::smallTalk insteadof A;
        A::bigTalk insteadof C;
        C::mediumTalk as FooBar;
    }
}
~~~

&#9650; [クラスとプロパティとメソッド](#4-クラスとプロパティとメソッド)

<!-- ------------------------------ -->

### 4.3 プロパティと定数

すべてのプロパティにおいてアクセス権の定義は必須です。

定数のアクセス権をサポートしているPHPバージョン(PHP7.1以上)ではアクセス権の定義は必須です。

プロパティの定義に`var`キーワードを使用してはいけません。

1つの文で2つ以上のプロパティを定義してはいけません。

protectedやprivateであることを示すためにプロパティ名をアンダースコア1つで始めてはいけません。すなわち、アンダースコアのプレフィックスは明示的に何の意味も持ちません。

型宣言とプロパティ名の間は1つのスペースで区切られていなければいけません。

プロパティの宣言は以下のようになります。

~~~php
<?php

namespace Vendor\Package;

class ClassName
{
    public $foo = null;
    public static int $bar = 0;
}
~~~

&#9650; [クラスとプロパティとメソッド](#4-クラスとプロパティとメソッド)

<!-- ------------------------------ -->

### 4.4 メソッドと関数

すべてのメソッドにおいてアクセス権の定義は必須です。

protectedやprivateであることを示すためにメソッド名をアンダースコア1つで始めてはいけません。すなわち、アンダースコアのプレフィックスは明示的に何の意味も持ちません。

メソッドや関数の定義部分において、メソッド名や関数名の後にスペースがあってはいけません。開始の中括弧は独立した行にある必要があり、終了の中括弧はメソッドや関数本文の次の行にある必要があります。引数列開始の括弧の後にスペースがあってはならず、また引数列終了の括弧の前にスペースがあってはいけません。

メソッドの定義は以下のような形式となります。括弧、カンマ、スペース、中括弧の配置に注意してください。

~~~php
<?php

namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
~~~

関数の定義は以下のような形式となります。括弧、カンマ、スペース、中括弧の配置に注意してください。

~~~php
<?php

function fooBarBaz($arg1, &$arg2, $arg3 = [])
{
    // function body
}
~~~

&#9650; [クラスとプロパティとメソッド](#4-クラスとプロパティとメソッド)

<!-- ------------------------------ -->

### 4.5 メソッドと関数の引数

引数のリストでは、カンマの前にスペースがあってはならず、カンマの後には1つのみスペースがなければいけません。

メソッドと関数の引数において、デフォルト値を持つものは引数リストの末尾になければいけません。

~~~php
<?php

namespace Vendor\Package;

class ClassName
{
    public function foo(int $arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
~~~

引数リストは複数の行に分割しても構いません、その場合は分割した行を1段階ずつインデントしなけければならず、1行につき引数1個ずつ記載しなければいけません。

引数リストを複数の行に分割す流場合、引数列の閉じ括弧と本文開始の中括弧はそれのみの同じ行に配置し、間に1個のみスペースがなければいけません。

~~~php
<?php

namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
~~~

戻り値の型宣言が存在する場合、コロンの後に1個のスペースを置き、その後に型宣言を記載しなければいけません。コロンと型定義は引数リストの閉じ括弧とスペースを挟まず同じ行に置かなければいけません。

~~~php
<?php

declare(strict_types=1);

namespace Vendor\Package;

class ReturnTypeVariations
{
    public function functionName(int $arg1, $arg2): string
    {
        return 'foo';
    }

    public function anotherFunction(
        string $foo,
        string $bar,
        int $baz
    ): string {
        return 'foo';
    }
}
~~~

nullを許容する場合、`?`と型の間にスペースを挟んではいけません。

~~~php
<?php

declare(strict_types=1);

namespace Vendor\Package;

class ReturnTypeVariations
{
    public function functionName(?string $arg1, ?int &$arg2): ?string
    {
        return 'foo';
    }
}
~~~

リファレンス渡しの`&`記号を使用する場合は上記に示した例のように引数の前に置き、記号の後にスペースを置いてはいけません。

可変引数の`...`演算子と引数名の間にスペースがあってはいけません。

```php
public function process(string $algorithm, ...$parts)
{
    // processing
}
```

リファレンス渡しの記号と可変引数の演算子を組み合わせて使用する場合、それらの間にスペースを置いてはいけません。

```php
public function process(string $algorithm, &...$parts)
{
    // processing
}
```

&#9650; [クラスとプロパティとメソッド](#4-クラスとプロパティとメソッド)

<!-- ------------------------------ -->

### 4.6 `abstract`と`final`と`static`

`abstract`や`final`の宣言を行う場合、アクセス権の定義の前に記述しなければいけません。

`static`の宣言を行う場合、アクセス権の定義の後に記述しなければいけません。

~~~php
<?php

namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
~~~

&#9650; [クラスとプロパティとメソッド](#4-クラスとプロパティとメソッド)

<!-- ------------------------------ -->

### 4.7 メソッドと関数の呼び出し

メソッドや関数の呼び出しを行う場合、メソッド・関数名と引数の開始の括弧の間にスペースを挟んではならず、開始の括弧の後にスペースを置いてはならず、終了の括弧の前にスペースを置いてはいけません。引数リストにおいて、それぞれのカンマの前にスペースを置いてはならず、またカンマの後に1つだけスペースを置かなければいけません。

~~~php
<?php

bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
~~~

引数リストは複数の行に分割しても構いません、その場合は分割した行を1段階ずつインデントしなけければいけません。その場合、先頭の要素を次の行に置かなければならず、1行につき引数1個ずつ記載しなければいけません。(無名関数や配列のような場合に)1つの引数のみを複数行に分割する場合は他の要素の分割に影響しません。

~~~php
<?php

$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
~~~

~~~php
<?php

somefunction($foo, $bar, [
  // ...
], $baz);

$app->get('/hello/{name}', function ($name) use ($app) {
    return 'Hello ' . $app->escape($name);
});
~~~

<!-- ---------------------------------------------------------------------- -->

## 5. 制御構造

制御構造に関する一般的なスタイルルールは以下の通りです。

- 制御構造キーワードの後には1つのスペースが必要です
- 開始の括弧の後にスペースを置いてはいけません
- 終了の括弧の前にスペースを置いてはいけません
- 終了の括弧と開始の中括弧の間には1つのスペースを挟まなければいけません
- 本文は1段階インデントを下げなければいけません
-  本文は開始の中括弧の次の行から始めなくてはいけません
- 終了の中括弧は本文の次の行に置かなければいけません

それぞれの本文は中括弧で囲まれていなければいけません。この規約により、構造がどのように見えるかが標準化され、新しい行が追加されるときに問題が発生する可能性が低くなります。

1. **[ifとelseifとelse](#51-ifとelseifとelse)**
2. **[switchとcase](#52-switchとcase)**
3. **[whileとdo-while](#53-whileとdo-while)**
4. **[for](#54-for)**
5. **[foreach](#55-foreach)**
6. **[try-catch-finally](#56-try-catch-finally)**

&#9650; [Table of Contents](#table-of-contents)

### 5.1 `if`と`elseif`と`else`

`if`文のスタイルは以下の通りです。括弧、スペース、中括弧の配置に注意してください。また、`else`と`elseif`は前ブロックのボディの閉じ中括弧と同じ行に記述してください。

~~~php
<?php

if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
~~~

すべての制御キーワードが1つの単語に見えるように、`else if`の代わりに`elseif`を用いる必要があります。

括弧の中の式は複数の行に分割することができ、そのときは分割した行を最低1段階インデントしてください。その際、最初の条件文は括弧の次の行から開始しなければいけません。条件文終了の括弧と本文開始の中括弧はスペース1個を挟んで同じ行に記述しなければいけません。条件文の間の論理演算子は行頭か行末のいずれかに統一して配置しなければいけません。

~~~php
<?php

if (
    $expr1
    && $expr2
) {
    // if body
} elseif (
    $expr3
    && $expr4
) {
    // elseif body
}
~~~

&#9650; [制御構造](#5-制御構造)

<!-- ------------------------------ -->

### 5.2 `switch`と`case`

`switch`文は以下の通りに記述してください。括弧、スペース、中括弧の配置に注意してください。`case`文は`switch`より1段階インデントを下げて記述しなければならず、`break`キーワード(もしくは他の中断するキーワード)は`case`文の内容と同じレベルのインデントでなければいけません。`case`文の内容が空ではなく、意図的に後続の文を実行させたい場合は`// no break`のようなコメントを書かなければいけません。

~~~php
<?php

switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
~~~

括弧の中の式は複数の行に分割することができ、そのときは分割した行を最低1段階インデントしてください。その際、最初の条件文は括弧の次の行から開始しなければいけません。条件文終了の括弧と本文開始の中括弧はスペース1個を挟んで同じ行に記述しなければいけません。条件文の間の論理演算子は行頭か行末のいずれかに統一して配置しなければいけません。

~~~php
<?php

switch (
    $expr1
    && $expr2
) {
    // structure body
}
~~~

&#9650; [制御構造](#5-制御構造)

<!-- ------------------------------ -->

### 5.3 `while`と`do while`

`while`文のスタイルは以下の通りです。括弧、スペース、中括弧の配置に注意してください。

~~~php
<?php

while ($expr) {
    // structure body
}
~~~

括弧の中の式は複数の行に分割することができ、そのときは分割した行を最低1段階インデントしてください。その際、最初の条件文は括弧の次の行から開始しなければいけません。条件文終了の括弧と本文開始の中括弧はスペース1個を挟んで同じ行に記述しなければいけません。条件文の間の論理演算子は行頭か行末のいずれかに統一して配置しなければいけません。

~~~php
<?php

while (
    $expr1
    && $expr2
) {
    // structure body
}
~~~

同様に、`do while`文のスタイルは以下の通りです。括弧、スペース、中括弧の配置に注意してください。

~~~php
<?php

do {
    // structure body;
} while ($expr);
~~~

括弧の中の式は複数の行に分割することができ、そのときは分割した行を最低1段階インデントしてください。その際、最初の条件文は括弧の次の行から開始しなければいけません。条件文の間の論理演算子は行頭か行末のいずれかに統一して配置しなければいけません。

~~~php
<?php

do {
    // structure body;
} while (
    $expr1
    && $expr2
);
~~~

&#9650; [制御構造](#5-制御構造)

<!-- ------------------------------ -->

### 5.4 `for`

`for`文のスタイルは以下の通りです。括弧、スペース、中括弧の配置に注意してください。

~~~php
<?php

for ($i = 0; $i < 10; $i++) {
    // for body
}
~~~

括弧の中の式は複数の行に分割することができ、そのときは分割した行を最低1段階インデントしてください。その際、最初の条件文は括弧の次の行から開始しなければいけません。条件文終了の括弧と本文開始の中括弧はスペース1個を挟んで同じ行に記述しなければいけません。

~~~php
<?php

for (
    $i = 0;
    $i < 10;
    $i++
) {
    // for body
}
~~~

&#9650; [制御構造](#5-制御構造)

<!-- ------------------------------ -->

### 5.5 `foreach`

`foreach`文のスタイルは以下の通りです。括弧、スペース、中括弧の配置に注意してください。

~~~php
<?php

foreach ($iterable as $key => $value) {
    // foreach body
}
~~~

&#9650; [制御構造](#5-制御構造)

<!-- ------------------------------ -->

### 5.6 `try`, `catch`, `finally`

`try-catch-finally`ブロックのスタイルは以下の通りです。括弧、スペース、中括弧の配置に注意してください。

~~~php
<?php

try {
    // try body
} catch (FirstThrowableType $e) {
    // catch body
} catch (OtherThrowableType | AnotherThrowableType $e) {
    // catch body
} finally {
    // finally body
}
~~~

<!-- ---------------------------------------------------------------------- -->

## 6. 演算子

演算子のスタイルルールは項数(オペランドの数)でグルーピングされます。

演算子の周囲にスペースを使用することが認められており、可読性を目的として複数のスペースを使用しても構いません。

ここで説明されていない演算子はすべて未定義のままです。

### 6.1 単項演算子

インクリメント/デクリメント演算子は演算子とオペランドの間にスペースを挟んではいけません。

~~~php
$i++;
++$j;
~~~

型キャスト演算子は括弧の内側にスペースがあってはいけません。

~~~php
$intValue = (int) $input;
~~~

&#9650; [演算子](#6-演算子)

<!-- ------------------------------ -->

### 6.2 二項演算子

全ての[代数演算子][]、[比較演算子][]、[代入演算子][]、[ビット演算子][]、[論理演算子][]、[文字列演算子][]、[型演算子][]は前後に1個以上のスペースを置かなければいけません。

~~~php
if ($a === $b) {
    $foo = $bar ?? $a ?? $b;
} elseif ($a > $b) {
    $foo = $a + $b * $c;
}
~~~

&#9650; [演算子](#6-演算子)

<!-- ------------------------------ -->

### 6.3 三項演算子

三項演算子は`?`と`:`それぞれの前後に1個以上のスペースを置かなければいけません。

~~~php
$variable = $foo ? 'foo' : 'bar';
~~~

三項演算子の真ん中のオペランドが省略されている場合、演算子は二項の[比較演算子][]と同様のスタイルルールを適用しなければいけません。

~~~php
$variable = $foo ?: 'bar';
~~~

<!-- ---------------------------------------------------------------------- -->

## 7. 無名関数(クロージャ)

無名関数は`function`キーワードの後にスペース1個を置いた後に定義し、`use`キーワードの前後にスペースを1個ずつ置かなければいけません。

本文開始の中括弧は同じ行に配置しなければならず、終了の中括弧は本文の次の行に配置しなければいけません。

引数リストと変数リストの開始の括弧の後にスペースがあってはならず、終了の括弧の前にスペースがあってはいけません。

引数リストと変数リストにおいて、カンマの前にスペースを置いてはならず、カンマの後に1つスペースを置かなければいけません。

無名関数の引数において、デフォルト値を持つものは引数リストの末尾になければいけません。

戻り値の型宣言が存在する場合、通常の関数やメソッドのコーディングルールに従わなければいけません。`use`キーワードが存在する場合、コロンは`use`リストの閉じ括弧の後に置き、閉じ括弧とコロンの間にスペースを挟まず配置しなければいけません。

無名関数のスタイルは以下の通りです。括弧、スペース、中括弧の配置に注意してください。

~~~php
<?php

$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};

$closureWithArgsVarsAndReturn = function ($arg1, $arg2) use ($var1, $var2): bool {
    // body
};
~~~

引数と変数のリストは複数行に分割することができ、その場合はそれぞれの行を1段階インデントしてください。その場合、最初の要素を次の行に置く必要があり、1行あたりインターフェースを1つずつ書く必要があります。

末尾のリスト(変数リストがある場合はそちら、なければ引数リスト)が複数行に分割されている場合、リスト終了の括弧と本文開始の中括弧はスペース1個を挟んで同じ行に記述しなければいけません。

以下に引数リストと変数リストがそれぞれある場合とない場合の複数行に分割した例を示します。

~~~php
<?php

$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
~~~

関数やメソッドの引数として直接使用される場合にも同じルールが適用される点に注意してください。

~~~php
<?php

$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
~~~

<!-- ---------------------------------------------------------------------- -->

## 8. 無名クラス

無名クラスは前述の無名関数と同様のガイドラインと原則に従わなければいけません。

~~~php
<?php

$instance = new class {};
~~~

`implements`キーワードが改行されない限り、開始の中括弧は`class`のキーワードと同じ行にあっても構いません。もしインターフェースの箇所で改行されている場合、中括弧は最後のインターフェースの直後に記載されなければいけません。

~~~php
<?php

// Brace on the same line
$instance = new class extends \Foo implements \HandleableInterface {
    // Class content
};

// Brace on the next line
$instance = new class extends \Foo implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // Class content
};
~~~

<!-- ---------------------------------------------------------------------- -->

## 9. コメント

このセクションでは、コメントのフォーマットと使用方法について説明します。

1. **[一行コメント](#91-一行コメント)** 2つのスラッシュを使用する必要があります
	* e.g. `// My comment`
2. **[複数行のコメント](#92-複数行のコメント)** ブロック形式を使用しなければなりません
	* i.e. `/**` `↵` `* My comment` `↵` `*/`
3. **[ヘッダーコメント](#93-ヘッダーコメント)** ブロック形式を使用すべきです
	* i.e. `/**` `↵` `* Name of code section` `↵` `*/`
4. **[区切りコメント](#94-区切りコメント)** アスタリスクを間に入れたブロック形式を使用すべきです
	* i.e. `/**` `75 asterisks` `*/`
5. **[コメント](#95-コメント)** 独自の回線になければなりません
	* i.e. `↵` `// My comment`
6. **[コードのブロック](#96-コードのブロック)** 説明または要約する必要があります
	* e.g. `// Compare user accounts from export against expired accounts in system`
7. **[曖昧な数字](#97-曖昧な数字)** 明確にしなければなりません
	* e.g. `// 1,000 processable records per hour API limit`
8. **[外部変数](#98-外部変数)** 明確にしなければなりません
	* e.g. `// Database object included in file.php`

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 9.1 一行コメント

単一行のコメントには 2 つのスラッシュを使用する必要があります.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php

/* This is a comment */

// EOF
 
</pre>

&#8627; 単一行のコメントに `/*` と `*/` を使用しているため、不正解です。

#### &#10004; Correct

<pre lang=php>
&lt;?php

// This is a comment

// EOF
 
</pre>

&#9650; [コメント](#9-コメント)

<!-- ------------------------------ -->

### 9.2 複数行のコメント

複数行のコメントはブロック形式を使用する必要があります

#### &#10006; Incorrect

<pre lang=php>
&lt;?php

// This is a
// multi-line
// comment

// EOF
 
</pre>

&#8627; 複数行のコメントに `//` を使用しているため、不正解です

#### &#10004; Correct

<pre lang=php>
&lt;?php

/**
 * This is a
 * multi-line
 * comment
 */

// EOF
 
</pre>

&#9650; [コメント](#9-コメント)

<!-- ------------------------------ -->

### 9.3 ヘッダーコメント

ヘッダーコメントはブロック形式を使用すべきです

<pre lang=php>
&lt;?php

/**
 * Global application settings
 */

define('SETTING_ONE', '');
define('SETTING_TWO', '');
define('SETTING_THREE', '');

// EOF
 
</pre>

&#9650; [コメント](#9-コメント)

<!-- ------------------------------ -->

### 9.4 区切りコメント

区切りコメントは、間に 75 個のアスタリスクを含むブロック形式を使用する必要があります 。

#### &#10006; Incorrect

<pre lang=php>
&lt;?php

/**#######################################################################*/

// EOF
 
</pre>

&#8627; Incorrect because it uses `#` instead of `*`.

<pre lang=php>
&lt;?php

/*************/

// EOF
 
</pre>

&#8627; `*` の代わりに 10 を使用しているため、不正解です。

#### &#10004; Correct

<pre lang=php>
&lt;?php

/**
 * Beginning + Middle + End
 * 3 spaces + 75 spaces + 2 spaces = 80 character line limit
 */

/******************************************************************************/

// EOF
 
</pre>

&#9650; [コメント](#9-コメント)

<!-- ------------------------------ -->

### 9.5 コメント

コメントは単独の行に入力する必要があります

#### &#10006; Incorrect

<pre lang=php>
&lt;?php

print_welcome_message(); // Prints welcome message

// EOF
 
</pre>

&#8627; `// Prints welcome message` が単独の行にないため、不正解です

#### &#10004; Correct

<pre lang=php>
&lt;?php

// Prints welcome message
print_welcome_message();

// EOF
 
</pre>

&#9650; [コメント](#9-コメント)

<!-- ------------------------------ -->

### 9.6 コードのブロック

コードのブロックを説明または要約する必要があります 

#### ~ Acceptable

<pre lang=php>
&lt;?php

foreach ($users as $user) {
	if ($expr1) {
		// ...
	} else {
		// ...
	}
	if ($expr2) {
		// ...
	} elseif ($expr3) {
		// ...
	} else {
		// ...
	}
	// ...
}

// EOF
 
</pre>

&#8627; 許容可能ですが、コードのブロックを説明または要約する必要があります。

#### &#10004; Preferred

<pre lang=php>
&lt;?php

/**
 * Get active website bloggers with profile photo for author page.
 * If no photo exists on website, check intranet.
 * If neither location has photo, send user email to upload one.
 */
foreach ($users as $user) {
	if ($expr1) {
		// ...
	} else {
		// ...
	}
	if ($expr2) {
		// ...
	} elseif ($expr3) {
		// ...
	} else {
		// ...
	}
	// ...
}

// EOF
 
</pre>

&#9650; [コメント](#9-コメント)

<!-- ------------------------------ -->

### 9.7 曖昧な数字

曖昧な数字は明確にしなければなりません。

#### &#10006; Incorrect

<pre lang=php>
&lt;?php

while ($expr && $x &lt; 1000) {
	// ...
}

// EOF
 
</pre>

&#8627; 「1000」が明確になっていないため、不正解です

#### &#10004; Correct

<pre lang=php>
&lt;?php

// Script times out after 1,000 records
while ($expr && $x &lt; 1000) {
	// ...
}

// EOF
 
</pre>

&#9650; [コメント](#9-コメント)

<!-- ------------------------------ -->

### 9.8 外部変数

外部変数を明確にする必要があります

#### &#10006; Incorrect

<pre lang=php>
&lt;?php

include_once 'some-file.php';

// ...

foreach($users as $user) {
	// ...
}

// EOF
 
</pre>

&#8627; `$users` のソースが明確ではないため、不正解です

#### &#10004; Correct

<pre lang=php>
&lt;?php

include_once 'some-file.php';

// ...

// $users from some-file.php
foreach($users as $user) {
	// ...
}

// EOF
 
</pre>

[PSR-1]: http://www.php-fig.org/psr/psr-1/
[PSR-2]: http://www.php-fig.org/psr/psr-2/
[keywords]: http://php.net/manual/ja/reserved.keywords.php
[types]: http://php.net/manual/ja/reserved.other-reserved-words.php
[代数演算子]: http://php.net/manual/ja/language.operators.arithmetic.php
[代入演算子]: http://php.net/manual/ja/language.operators.assignment.php
[比較演算子]: http://php.net/manual/ja/language.operators.comparison.php
[ビット演算子]: http://php.net/manual/ja/language.operators.bitwise.php
[論理演算子]: http://php.net/manual/ja/language.operators.logical.php
[文字列演算子]: http://php.net/manual/ja/language.operators.string.php
[型演算子]: http://php.net/manual/ja/language.operators.type.php