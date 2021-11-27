<div dir="rtl">

# Clean Code PHP

## الفهرس

  1. [مقدمة](#مقدمة)
  2. [المتغيرات](#المتغيرات)
     * [استخدم أسماء متغيرات ذات معنى وقابلة للنطق](#استخدم-أسماء-متغيرات-ذات-معنى-وقابلة-للنطق)
     * [استخدم نفس المفردات لنفس النوع من المتغيرات](#استخدم-نفس-المفردات-لنفس-النوع-من-المتغيرات)
     * [استخدام أسماء قابلة للبحث (الجزء 1)](#استخدام-أسماء-قابلة-للبحث-الجزء-1)
     * [استخدام أسماء قابلة للبحث (الجزء 2)](#استخدام-أسماء-قابلة-للبحث-الجزء-2)
     * [استخدم متغيرات توضيحية](#استخدم-متغيرات-توضيحية)
     * [تجنب التداخل بعمق كبير (الجزء 1)](#تجنب-التداخل-بعمق-كبير-الجزء-1)
     * [تجنب التداخل بعمق كبير (الجزء 2)](#تجنب-التداخل-بعمق-كبير-الجزء-2)
     * [تجنب الخرائط الذهنية](#تجنب-الخرائط-الذهنية)
     * [لا تكرر اسم الكائن في المتغيرات](#لا-تكرر-اسم-الكائن-في-المتغيرات)
  3. [المقارنة](#مقارنة)
     * [استخدم مقارنة التطابق](#استخدم-مقارنة-التطابق)
     * [Null coalescing عامل](#null-coalescing-عامل)
  4. [الدوال](#الدوال)
     * [استخدم المعاملات الأفتراضية بدلا من الروابط المختصرة او الأوامر الشرطية](#استخدم-المعاملات-الأفتراضية-بدلا-من-الروابط-المختصرة-او-الأوامر-الشرطية)
     * [معاملات الدوال (أفضل شيئ معاملان أو أقل)](#معاملات-الدوال-أفضل-شيئ-معاملان-أو-أقل)
     * [يجب أن تعبر أسماء الدوال عن ما تفعل](#يجب-أن-تعبر-أسماء-الدوال-عن-ما-تفعل)
     * [يجب أن تكون الدوال على مستوى واحد فقط من التجريد](#يجب-أن-تكون-الدوال-على-مستوى-واحد-فقط-من-التجريد)
     * [لا تستخدم العلامات كمعاملات للدالة](#لا-تستخدم-العلامات-كمعاملات-للدالة)
     * [تجنب الآثار الجانبية](#تجنب-الآثار-الجانبية)
     * [لا تكتب دوال عالمية](#لا-تكتب-دوال-عالمية)
     * [لا تستخدم نمط Singleton](#لا-تستخدم-نمط-singleton)
     * [غلف الأوامر الشرطية](#غلف-الأوامر-الشرطية)
     * [تجنب الأوامر الشرطية السلبية](#تجنب-الأوامر-الشرطية-السلبية)
     * [تجنب الأوامر الشرطية](#تجنب-الأوامر-الشرطية)
     * [تجنب فحص النوع (الجزء 1)](#تجنب-فحص-النوع-الجزء-1)
     * [تجنب فحص النوع (الجزء 2)](#تجنب-فحص-النوع-الجزء-2)
     * [أزل الكود الميت](#أزل-الكود-الميت)
  5. [الكائنات وهياكل البيانات](#الكائنات-وهياكل-البيانات)
     * [استخدم تغليف الكائن](#استخدم-تغليف-الكائن)
     * [اجعل الكائنات لها خصائص private/protected](#اجعل-الكائنات-لها-خصائص-privateprotected)
  6. [الكلاسات](#الكلاسات)
     * [فضل التكوين (composition) على الوراثة (inheritance)](#فضل-التكوين-composition-على-الوراثة-inheritance)
     * [تجنب الواجهات الطليقة (fluent interfaces)](#تجنب-الواجهات-الطليقة-fluent-interfaces)
     * [فضل الكلاسات النهائية (final classes)](#فضل-الكلاسات-النهائية-final-classes)
  7. [SOLID](#solid)
     * [مبدأ المسؤولية الواحدة (Single Responsibility Principle, SRP)](#مبدأ-المسؤولية-الواحدة-single-responsibility-principle-srp)
     * [مبدأ مفتوح / مغلق (Open / Closed Principle، OCP)](#مبدأ-مفتوح-مغلق-open-closed-principle،-ocp)
     * [مبدأ تبديل ليسكوف (Liskov Substitution Principle, LSP)](#مبدأ-تبديل-ليسكوف-liskov-substitution-principle-lsp)
     * [مبدأ فصل الواجهة (Interface Segregation Principle, ISP)](#مبدأ-فصل-الواجهة-interface-segregation-principle-isp)
     * [مبدأ انعكاس التبعية (Dependency Inversion Principle, DIP)](#مبدأ-انعكاس-التبعية-dependency-inversion-principle-dip)
  8. [لا تكرر نفسك (Don’t repeat yourself, DRY)](#لا-تكرر-نفسك-dont-repeat-yourself-dry)
  9. [الترجمات](#الترجمات)

## مقدمة

مبادئ هندسة البرمجيات ، من كتاب روبرت سي مارتن
[*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882),
معدل ليناسب لغة PHP. هذا ليس دليلا لأسلوب ما. بل دليل لإنتاج
برمجيات قابلة للقراءة وإعادة الاستخدام وإعادة البناء في لغة PHP.


لا يجب اتباع جميع المبادئ بشكل صارم، بل هناك عدد قليل يتفق عليه عالميا بين جميع المطورين. هذه مجرد إرشادات وليس أكثر, لكن تم تقنينها وفقًا للتجربة الجماعية لمؤلفي كتاب *Clean Code* على مدار سنوات عديدة.


مستوحى من [clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript).

على الرغم من أن العديد من المطورين لا يزالون يستخدمون اصدار PHP 5, تعمل معظم الأمثلة في هذه المقالة فقط مع اصدارات PHP 7.1+.

## المتغيرات

### استخدم أسماء متغيرات ذات معنى وقابلة للنطق

**سيء:**
</div>

```php
$ymdstr = $moment->format('y-m-d');
```
<div dir="rtl">
**جيد:**
</div>

```php
$currentDate = $moment->format('y-m-d');
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### استخدم نفس المفردات لنفس النوع من المتغيرات

**سيء:**
</div>

```php
getUserInfo();
getUserData();
getUserRecord();
getUserProfile();
```

<div dir="rtl">
**جيد:**
</div>

```php
getUser();
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### استخدام أسماء قابلة للبحث (الجزء 1)

نحن نقرأ كود أكثر مما نكتب. من المهم أن يكون الكود الذي نكتبه قابل للقراءة والبحث. نحن نؤذي قرائ كودنا من خلال عدم كتابة أسماء متغيرة لها معنى لفهم برنامجنا. قم بإنشاء أسماء يمكن البحث عنها.

**سيء:**
</div>

```php
// What the heck is 448 for?
$result = $serializer->serialize($data, 448);
```

<div dir="rtl">
**جيد:**
</div>

```php
$json = $serializer->serialize($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);
```
<div dir="rtl">

### استخدام أسماء قابلة للبحث (الجزء 2)

**سيء:**
</div>

```php
class User
{
    // What the heck is 7 for?
    public $access = 7;
}

// What the heck is 4 for?
if ($user->access & 4) {
    // ...
}

// What's going on here?
$user->access ^= 2;
```

<div dir="rtl">
**جيد:**
</div>

```php
class User
{
    public const ACCESS_READ = 1;

    public const ACCESS_CREATE = 2;

    public const ACCESS_UPDATE = 4;

    public const ACCESS_DELETE = 8;

// User as default can read, create and update something
    public $access = self::ACCESS_READ | self::ACCESS_CREATE | self::ACCESS_UPDATE;
}

if ($user->access & User::ACCESS_UPDATE) {
    // do edit ...
}

// Deny access rights to create something
$user->access ^= User::ACCESS_CREATE;
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### استخدم متغيرات توضيحية

**سيء:**
</div>

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches[1], $matches[2]);
```
<div dir="rtl">
**ليس سيئا:**

إنه أفضل ، لكننا ما زلنا نعتمد بشدة على regex.
</div>

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

[, $city, $zipCode] = $matches;
saveCityZipCode($city, $zipCode);
```

<div dir="rtl">
**جيد:**
</div>

تقليل الاعتماد على regex من خلال تسمية أنماط فرعية.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(?<city>.+?)\s*(?<zipCode>\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches['city'], $matches['zipCode']);
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب التداخل بعمق كبير (الجزء 1)

يمكن أن يؤدي وجود عدد كبير جدًا من عبارات if-else إلى صعوبة متابعة الأوامر البرمجية. حاول أن تكون صريح وواضح.

**سيء:**
</div>

```php
function isShopOpen($day): bool
{
    if ($day) {
        if (is_string($day)) {
            $day = strtolower($day);
            if ($day === 'friday') {
                return true;
            } elseif ($day === 'saturday') {
                return true;
            } elseif ($day === 'sunday') {
                return true;
            }
            return false;
        }
        return false;
    }
    return false;
}
```

<div dir="rtl">
**جيد:**
</div>

```php
function isShopOpen(string $day): bool
{
    if (empty($day)) {
        return false;
    }

    $openingDays = ['friday', 'saturday', 'sunday'];

    return in_array(strtolower($day), $openingDays, true);
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب التداخل بعمق كبير (الجزء 2)

**سيء:**
</div>

```php
function fibonacci(int $n)
{
    if ($n < 50) {
        if ($n !== 0) {
            if ($n !== 1) {
                return fibonacci($n - 1) + fibonacci($n - 2);
            }
            return 1;
        }
        return 0;
    }
    return 'Not supported';
}
```

<div dir="rtl">
**جيد:**
</div>

```php
function fibonacci(int $n): int
{
    if ($n === 0 || $n === 1) {
        return $n;
    }

    if ($n >= 50) {
        throw new Exception('Not supported');
    }

    return fibonacci($n - 1) + fibonacci($n - 2);
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب الخرائط الذهنية

لا تجبر قارئ الكود على ترجمة ماذا يعني المتغير. حاول أن تكون صريح وواضح

**سيء:**
</div>

```php
$l = ['Austin', 'New York', 'San Francisco'];

for ($i = 0; $i < count($l); $i++) {
    $li = $l[$i];
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    // Wait, what is `$li` for again?
    dispatch($li);
}
```

<div dir="rtl">
**جيد:**
</div>

```php
$locations = ['Austin', 'New York', 'San Francisco'];

foreach ($locations as $location) {
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    dispatch($location);
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### لا تكرر اسم الكائن في المتغيرات

إذا أخبرك اسم الكلاس / الكائن بشيء ما ، فلا تكرر ذلك في اسم المتغير.

**سيء:**
</div>

```php
class Car
{
    public $carMake;

    public $carModel;

    public $carColor;

    //...
}
```

<div dir="rtl">
**جيد:**
</div>

```php
class Car
{
    public $make;

    public $model;

    public $color;

    //...
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

## المقارنة

### استخدم [مقارنة التطابق](http://php.net/manual/en/language.operators.comparison.php)

**ليس جيد:**

في المقارنة البسيطة باستعمال علامتان, يعتبر النص والرقم متشابه.
</div>

```php
$a = '42';
$b = 42;

if ($a != $b) {
    // The expression is verified
}
```
<div dir="rtl">

المقارنة `$a != $b` سوف تقوم بإرجاع `FALSE`؟ لكن في الحقيقة انها  `TRUE`!
النص `42` مختلف عن الرقم `42`.

**جيد:**

ستقارن المقارنة المتطابقة باستعمال ثلاث علامات بين النوعين والقيمتين
</div>

```php
$a = '42';
$b = 42;

if ($a !== $b) {
    // The expression is verified
}
```
<div dir="rtl">

المقارنة `$a !== $b` سوف تقوم بإرجاع `TRUE`.

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### Null coalescing عامل

Null coalescing هوا عامل جديد [في PHP 7](https://www.php.net/manual/en/migration70.new-features.php). عامل null coalescing `??` تمت اضافته كبديل ل `isset()`. يُعيد مُعامله الأول إذا كان موجود; وإلا فإنه يُعيد مُعامله الثاني إذا كان `null`.

**سيء:**
</div>

```php
if (isset($_GET['name'])) {
    $name = $_GET['name'];
} elseif (isset($_POST['name'])) {
    $name = $_POST['name'];
} else {
    $name = 'nobody';
}
```

<div dir="rtl">
**جيد:**
</div>

```php
$name = $_GET['name'] ?? $_POST['name'] ?? 'nobody';
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

## الدوال

### استخدم المعاملات الأفتراضية بدلا من الروابط المختصرة او الأوامر الشرطية

**Not good:**

هذا ليس جيدًا لأن `$breweryName` يمكن أن يكون` NULL`.
</div>

```php
function createMicrobrewery($breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**ليس سيئا:**

هذا الرأي مفهوم أكثر من الكود السابق ، لأنه يتحكم بشكل أفضل في قيمة المتغير.

```php
function createMicrobrewery($name = null): void
{
    $breweryName = $name ?: 'Hipster Brew Co.';
    // ...
}
```

<div dir="rtl">
**جيد:**

يمكنك استخدام [type hinting](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration) والتأكد من أن `$breweryName` لن يكون `NULL`.
</div>

```php
function createMicrobrewery(string $breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### معاملات الدوال (أفضل شيئ معاملان أو أقل)


يعد تحديد عدد معاملات الدالة أمرًا مهمًا للغاية لأنه يصنع اختبار الدالة أسهل. وجود أكثر من ثلاثة يؤدي إلى انفجار اندماجي حيث يتعين عليك اختبار العديد من الحالات المختلفة مع كل عامل منفصل.

الدالات التي ليس لها أي معامل هي الحالة المثالية. لا يوجد مشكلة بوجود معامل أو اثنين ، ويجب تجنب ثلاث معاملات. أي شيء أكثر من ذلك يجب أن يتم تجميعه. عادة ، إذا كان لديك أكثر من معاملان فالدالة تحاول أن تفعل الكثير من الأشياء. في حين انها عليها فعل شيء واحد ،في معظم الأحيان ، يكفي كائن مستوى أعلى كوسيط.

**سيء:**
</div>

```php
class Questionnaire
{
    public function __construct(
        string $firstname,
        string $lastname,
        string $patronymic,
        string $region,
        string $district,
        string $city,
        string $phone,
        string $email
    ) {
        // ...
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
class Name
{
    private $firstname;

    private $lastname;

    private $patronymic;

    public function __construct(string $firstname, string $lastname, string $patronymic)
    {
        $this->firstname = $firstname;
        $this->lastname = $lastname;
        $this->patronymic = $patronymic;
    }

    // getters ...
}

class City
{
    private $region;

    private $district;

    private $city;

    public function __construct(string $region, string $district, string $city)
    {
        $this->region = $region;
        $this->district = $district;
        $this->city = $city;
    }

    // getters ...
}

class Contact
{
    private $phone;

    private $email;

    public function __construct(string $phone, string $email)
    {
        $this->phone = $phone;
        $this->email = $email;
    }

    // getters ...
}

class Questionnaire
{
    public function __construct(Name $name, City $city, Contact $contact)
    {
        // ...
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### يجب أن تعبر أسماء الدوال عن ما تفعل

**سيء:**
</div>

```php
class Email
{
    //...

    public function handle(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// What is this? A handle for the message? Are we writing to a file now?
$message->handle();
```

<div dir="rtl">
**جيد:**
</div>

```php
class Email
{
    //...

    public function send(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// Clear and obvious
$message->send();
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### يجب أن تكون الدوال على مستوى واحد فقط من التجريد

عندما يكون لديك أكثر من مستوى من التجريد تكون الدالة عادة تفعل الكثير. يؤدي تقسيم الدوال إلى إعادة الاستخدام وسهولة اختبارات.

**سيء:**
</div>

```php
function parseBetterPHPAlternative(string $code): void
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            // ...
        }
    }

    $ast = [];
    foreach ($tokens as $token) {
        // lex...
    }

    foreach ($ast as $node) {
        // parse...
    }
}
```
<div dir="rtl">

**سيء أيضا:**

لقد قمنا بعمل بعض الدوال الخارجية ، لكن الدالة `parseBetterPHPAlternative ()` لا تزال معقدة للغاية وغير قابلة للاختبار.
</div>

```php
function tokenize(string $code): array
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            $tokens[] = /* ... */;
        }
    }

    return $tokens;
}

function lexer(array $tokens): array
{
    $ast = [];
    foreach ($tokens as $token) {
        $ast[] = /* ... */;
    }

    return $ast;
}

function parseBetterPHPAlternative(string $code): void
{
    $tokens = tokenize($code);
    $ast = lexer($tokens);
    foreach ($ast as $node) {
        // parse...
    }
}
```

<div dir="rtl">
**جيد:**

أفضل حل هو إزالة اعتمادات دالة `parseBetterPHPAlternative ()`.
</div>

```php
class Tokenizer
{
    public function tokenize(string $code): array
    {
        $regexes = [
            // ...
        ];

        $statements = explode(' ', $code);
        $tokens = [];
        foreach ($regexes as $regex) {
            foreach ($statements as $statement) {
                $tokens[] = /* ... */;
            }
        }

        return $tokens;
    }
}

class Lexer
{
    public function lexify(array $tokens): array
    {
        $ast = [];
        foreach ($tokens as $token) {
            $ast[] = /* ... */;
        }

        return $ast;
    }
}

class BetterPHPAlternative
{
    private $tokenizer;
    private $lexer;

    public function __construct(Tokenizer $tokenizer, Lexer $lexer)
    {
        $this->tokenizer = $tokenizer;
        $this->lexer = $lexer;
    }

    public function parse(string $code): void
    {
        $tokens = $this->tokenizer->tokenize($code);
        $ast = $this->lexer->lexify($tokens);
        foreach ($ast as $node) {
            // parse...
        }
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### لا تستخدم العلامات كمعاملات للدالة

تدل العلامات على أن هذه الدالة تقوم بأكثر من شيء. يجب أن تفعل الدوال شيئا واحدا. قسّم دوالك إذا كانت تتبع مسارات كود مختلفة على أساس قيمة منطقية.

**سيء:**
</div>

```php
function createFile(string $name, bool $temp = false): void
{
    if ($temp) {
        touch('./temp/' . $name);
    } else {
        touch($name);
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
function createFile(string $name): void
{
    touch($name);
}

function createTempFile(string $name): void
{
    touch('./temp/' . $name);
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب الآثار الجانبية


تنتج الدالة تأثيرًا جانبيًا إذا فعلت أي شيء بخلاف أخذ قيمة وإرجاع قيمة أو قيم أخرى. قد يكون أحد الآثار الجانبية هو الكتابة إلى ملف ، أو تعديل بعض المتغيرات العالمية ، أو تحويل كل أموالك بطريق الخطأ إلى شخص غريب.


الآن ، أنت بحاجة إلى أن يكون لديك آثار جانبية في البرنامج في بعض الأحيان. مثل المثال السابق ، قد تحتاج إلى الكتابة إلى ملف. ما تريد القيام به هو التركيز على مكان قيامك بذلك. لا تعمل العديد من الدوال والكلاسات التي تكتب إلى ملف معين. لديك خدمة واحدة تفعل ذلك. واحد فقط لا غير.


النقطة الأساسية هي تجنب المزالق الشائعة مثل مشاركة الحالة بين الكائنات بدون أي بنية ، باستخدام أنواع البيانات القابلة للتغيير التي يمكن الكتابة إليها بأي شيء ، وليس التركيز على مكان حدوث الآثار الجانبية. إذا تمكنت من القيام بذلك ، فستكون أكثر سعادة من الغالبية العظمى من المبرمجين الآخرين.

**سيء:**
</div>

```php
// متغير عالمي مشار إليه من خلال الدالة التالية.
// إذا كانت لدينا دالة أخرى تستخدم هذا الاسم ، فستكون الآن مصفوفة ويمكن أن تكسرها.
$name = 'Ryan McDermott';

function splitIntoFirstAndLastName(): void
{
    global $name;

    $name = explode(' ', $name);
}

splitIntoFirstAndLastName();

var_dump($name);
// ['Ryan', 'McDermott'];
```

<div dir="rtl">
**جيد:**
</div>

```php
function splitIntoFirstAndLastName(string $name): array
{
    return explode(' ', $name);
}

$name = 'Ryan McDermott';
$newName = splitIntoFirstAndLastName($name);

var_dump($name);
// 'Ryan McDermott';

var_dump($newName);
// ['Ryan', 'McDermott'];
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### لا تكتب دوال عالمية


يعد مفهوم (Polluting globals) (كتابة دوال عالمة) ممارسة سيئة في العديد من لغات البرمجة لأنه يمكنك التعارض مع مكتبة أو واجهة برمجة تطبيقات (API) أخرى على سبيل المثال: ماذا تفعل إذا كنت تريد إنشاء مصفوفة إعدادات؟ يمكنك كتابة دالة عالمية مثل `config()` ، لكنها قد تتعارض مع مكتبة أخرى حاولت أن تفعل الشيء نفسه.

**سيء:**
</div>

```php
function config(): array
{
    return [
        'foo' => 'bar',
    ];
}
```

<div dir="rtl">
**جيد:**
</div>

```php
class Configuration
{
    private $configuration = [];

    public function __construct(array $configuration)
    {
        $this->configuration = $configuration;
    }

    public function get(string $key): ?string
    {
        // null coalescing operator
        return $this->configuration[$key] ?? null;
    }
}
```
<div dir="rtl">

إنشئ نسخة من كلاس `Configuration`
</div>

```php
$configuration = new Configuration([
    'foo' => 'bar',
]);
```
<div dir="rtl">

والآن يجب عليك استخدام نسخة من `Configuration` في التطبيق.

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### لا تستخدم نمط Singleton

Singleton هو [نمط مضاد](https://ar.wikipedia.org/wiki/%D8%A7%D9%84%D9%86%D9%85%D8%B7_%D8%A7%D9%84%D9%85%D9%81%D8%B1%D8%AF). مقتبس من Brian Button:
 1. يتم استخدامها بشكل عام ك **نسخة عالمية**, لماذا هذا سيء جدا؟ لأنك **تخفي الاعتمادات** للتطبيق في الكود، بدلاً من كشفها من خلال الواجهات (interfaces). قم بعمل شيئًا عالميًا لتجنب شيء مثل [رائحة الكود](https://ar.wikipedia.org/wiki/%D8%B1%D8%A7%D8%A6%D8%AD%D8%A9_%D8%A7%D9%84%D9%83%D9%88%D8%AF) (code smell).
 2. ينتهك [مبدأ المسؤولية الواحدة (Single Responsibility Principle)](#مبدأ-المسؤولية-الواحدة-single-responsibility-principle-srp): بحكم حقيقة أنهم **يتحكمون في إنشاء انفسهم ودورة حياتهم**.
 3. بطبيعته يتسبب بأن يكون الكود [مقترن](https://ar.wikipedia.org/wiki/%D8%A7%D9%82%D8%AA%D8%B1%D8%A7%D9%86_(%D8%AD%D8%A7%D8%B3%D9%88%D8%A8)) بشكل كبير. هذا يجعل تزويرها تحت **اختبار صعبًا إلى حد ما** في كثير من الحالات.
 4. إنها تحمل حالة طوال عمر التطبيق. ضربة أخرى للاختبار منذ ** يمكن أن ينتهي بك الأمر بموقف يلزم فيه طلب الاختبارات ** وهو ما يتعارض بشكل كبير مع اختبارات الوحدة (unit tests). لماذا ا؟ لأن كل اختبار وحدة (unit test) يجب أن يكون مستقلاً عن الآخر.

هناك أيضا أفكار جيدة جدا من قبل [Misko Hevery](http://misko.hevery.com/about/) عن [جذر المشكلة](http://misko.hevery.com/2008/08/25/root-cause-of-singletons/).

**سيء:**
</div>

```php
class DBConnection
{
    private static $instance;

    private function __construct(string $dsn)
    {
        // ...
    }

    public static function getInstance(): self
    {
        if (self::$instance === null) {
            self::$instance = new self();
        }

        return self::$instance;
    }

    // ...
}

$singleton = DBConnection::getInstance();
```

<div dir="rtl">
**جيد:**
</div>

```php
class DBConnection
{
    public function __construct(string $dsn)
    {
        // ...
    }

    // ...
}
```
<div dir="rtl">

قم بإنشاء مثيل لفئة `DBConnection` وقم تهيئته باستخدام [DSN](http://php.net/manual/en/pdo.construct.php#refsect1-pdo.construct-parameters).
</div>

```php
$connection = new DBConnection($dsn);
```
<div dir="rtl">

والآن يجب عليك استخدام نسخة من `DBConnection` في التطبيق.

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### غلف الأوامر الشرطية

**سيء:**
</div>

```php
if ($article->state === 'published') {
    // ...
}
```

<div dir="rtl">
**جيد:**
</div>

```php
if ($article->isPublished()) {
    // ...
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب الأوامر الشرطية السلبية

**سيء:**
</div>

```php
function isDOMNodeNotPresent(DOMNode $node): bool
{
    // ...
}

if (! isDOMNodeNotPresent($node)) {
    // ...
}
```

<div dir="rtl">
**جيد:**
</div>

```php
function isDOMNodePresent(DOMNode $node): bool
{
    // ...
}

if (isDOMNodePresent($node)) {
    // ...
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب الأوامر الشرطية


تبدو هذه مهمة مستحيلة. عند سماع هذا لأول مرة ، يقول معظم الناس ، "كيف يفترض بي أن أفعل أي شيء بدون عبارة`if` ؟" الجواب هو أنه يمكنك استخدام تعدد الأشكال (polymorphism) لتحقيق نفس المهمة في كثير من الحالات. السؤال الثاني هو عادة ، "حسنًا هذا رائع ولكن لماذا أرغب في القيام بذلك؟" الإجابة هي مفهوم كود نظيف سابق تعلمناه: يجب أن تقوم الدالة بشيء واحد فقط. عندما يكون لديك كلاسات ودوال تحتوي على عبارات `if` ، فأنت تخبر المستخدم أن الدالة تقوم بأكثر من شيء. تذكر ، افعل شيئًا واحدًا فقط.

**سيء:**
</div>

```php
class Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        switch ($this->type) {
            case '777':
                return $this->getMaxAltitude() - $this->getPassengerCount();
            case 'Air Force One':
                return $this->getMaxAltitude();
            case 'Cessna':
                return $this->getMaxAltitude() - $this->getFuelExpenditure();
        }
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
interface Airplane
{
    // ...

    public function getCruisingAltitude(): int;
}

class Boeing777 implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getPassengerCount();
    }
}

class AirForceOne implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude();
    }
}

class Cessna implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getFuelExpenditure();
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب فحص النوع (الجزء 1)

لغة الPHP هي غير نوعية، مما يعني أن الدوال يمكن أن تأخذ أي نوع من المعاملات. أحيانًا تلدغك هذه الحرية ويصبح من المغري القيام بفحص النوع في الدالة. هناك العديد من الطرق لتجنب الاضطرار إلى القيام بذلك. أول شيء يجب مراعاته هو واجهات برمجة التطبيقات (APIs) المتسقة.

**سيء:**
</div>


```php
function travelToTexas($vehicle): void
{
    if ($vehicle instanceof Bicycle) {
        $vehicle->pedalTo(new Location('texas'));
    } elseif ($vehicle instanceof Car) {
        $vehicle->driveTo(new Location('texas'));
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
function travelToTexas(Vehicle $vehicle): void
{
    $vehicle->travelTo(new Location('texas'));
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب فحص النوع (الجزء 2)

 إذا كنت تعمل مع قيم أولية أساسية مثل النصوص (strings)  أو الأعداد الصحيحة (integers) أو المصفوفات (arrays)، وكنت تستخدم PHP 7+ ولا يمكنك استخدام تعدد الأشكال (polymorphism) ولكنك ما زلت تشعر بالحاجة إلى التحقق من النوع ، فعليك التفكير في استخدام تعريف النوع [(type declaration)](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration) أو الوضع الصارم (strict mode).  يوفر لك كتابة ثابتة (static) مع syntax PHP القياسي. تكمن مشكلة فحص النوع يدويًا في أن القيام بذلك يتطلب الكثير من الكود الإضافي بأن `سلامة الأنماط` الزائف الذي تحصل عليه لا يعوض ما فقده من قابلية القرائة. ابقي الكود نظيف, اكتب اختبارات جيدة, وأحصل على مراجعات جيدة للكود بخلاف ذلك ، افعل كل ذلك ولكن باستخدام تعريف النوع (ype declaration) أو  الوضع الصارم(strict mode)

**سيء:**
</div>

```php
function combine($val1, $val2): int
{
    if (! is_numeric($val1) || ! is_numeric($val2)) {
        throw new Exception('Must be of type Number');
    }

    return $val1 + $val2;
}
```

<div dir="rtl">
**جيد:**
</div>

```php
function combine(int $val1, int $val2): int
{
    return $val1 + $val2;
}
```

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### أزل الكود الميت


الكود الميت سيئ مثل الكود المكرر. لا يوجد سبب للاحتفاظ به
في المشرع. إذا لن يتم استخدامة، فتخلص منه! سيظل آمنا
في سجل الاصدارات إذا كنت لا تزال بحاجة إليه.

**سيء:**

```php
function oldRequestModule(string $url): void
{
    // ...
}

function newRequestModule(string $url): void
{
    // ...
}

$request = newRequestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

<div dir="rtl">
**جيد:**
</div>

```php
function requestModule(string $url): void
{
    // ...
}

$request = requestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**


## الكائنات وهياكل البيانات

### استخدم تغليف الكائن

في PHP يمكنك أستخدام الكلمات التالية `public` أو `protected` أو `private` للدوال.
باستخدام تلك الكلمات, يمكنك التحكم في تعديل خصائص الكائن.

* عندما تريد القيام بأكثر من مجرد الحصول على خاصية الكائن ، فلن تحتاج إلى البحث عن كل ملحق في المشروع واستبداله.
* يجعل إضافة التحقق أمرًا بسيطًا عند عمل `set`.
* أخفاء التفاصيل الداخلية.
* من السهل إضافة (loging) ومعالجة الأخطاء (errors) عند الحصول او تغير قيم الخصائص..
* بوراثة هذه الكلاس ، يمكنك تعديل الوظائف الافتراضية.
* يمكنك التحميل البطيء (lazy load) لخصائص الكائن ، دعنا نقول الحصول عليه من
خادم.

بالإضافة إلى أن هذا جزء من [مبدأ مفتوح / مغلق (Open / Closed Principle)](#مبدأ-مفتوح-مغلق-open-closed-principle،-ocp).

**سيء:**
</div>

```php
class BankAccount
{
    public $balance = 1000;
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->balance -= 100;
```

<div dir="rtl">
**جيد:**
</div>

```php
class BankAccount
{
    private $balance;

    public function __construct(int $balance = 1000)
    {
      $this->balance = $balance;
    }

    public function withdraw(int $amount): void
    {
        if ($amount > $this->balance) {
            throw new \Exception('Amount greater than available balance.');
        }

        $this->balance -= $amount;
    }

    public function deposit(int $amount): void
    {
        $this->balance += $amount;
    }

    public function getBalance(): int
    {
        return $this->balance;
    }
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->withdraw($shoesPrice);

// Get balance
$balance = $bankAccount->getBalance();
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### اجعل الكائنات لها خصائص private/protected

* تعد الدوال والخصائص `public` الأكثر خطورة بالنسبة للتغييرات ، لأن بعض التعليمات البرمجية الخارجية قد تعتمد عليها بسهولة ولا يمكنك التحكم في الكود الذي يعتمد عليها **التعديلات في الكلاس تشكل خطورة على جميع مستخدمي الكلاس.**
*تعد `private` خطيرة مثل public ، لأنها متوفرة في نطاق أي كلاس فرعي. هذا يعني بشكل فعال أن الاختلاف بين public وprivate يكون فقط في آلية الوصول ، لكن ضمان التغليف يظل كما هو. **التعديلات في الكلاس تشكل خطورة على جميع الكلاسات التابعة.**
* يضمن `private` أن يكون الكود **من الخطر تعديله في حدود كلاس واحد فقط** (أنت آمن لإجراء التعديلات ولن يكون عليك ذلك [Jenga effect](http://www.urbandictionary.com/define.php?term=Jengaphobia&defid=2494196)).

لذلك ، استخدم `private` افتراضيًا و `public/protected` عندما تحتاج إلى توفير وصول للكلاسات الخارجية.
لمزيد من المعلومات يمكنك قراءة [مقال مدونة](http://fabien.potencier.org/pragmatism-over-theory-protected-vs-private.html) حول هذا الموضوع بواسطة [Fabien Potencier](https://github.com/fabpot).

**سيء:**
</div>

```php
class Employee
{
    public $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }
}

$employee = new Employee('John Doe');
// Employee name: John Doe
echo 'Employee name: ' . $employee->name;
```

<div dir="rtl">
**جيد:**
</div>

```php
class Employee
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}

$employee = new Employee('John Doe');
// Employee name: John Doe
echo 'Employee name: ' . $employee->getName();
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

## الكلاسات

### فضل التكوين (composition) على الوراثة (inheritance)


كما هو مذكور في [*نماذج التصميم (هندسة البرمجيات)*](https://ar.wikipedia.org/wiki/%D9%86%D9%85%D8%A7%D8%B0%D8%AC_%D8%A7%D9%84%D8%AA%D8%B5%D9%85%D9%8A%D9%85_(%D9%87%D9%86%D8%AF%D8%B3%D8%A9_%D8%A7%D9%84%D8%A8%D8%B1%D9%85%D8%AC%D9%8A%D8%A7%D8%AA)) بواسطة Gang of Four ، يجب أن تفضل التكوين (composition) على الوراثة (inheritance) حيث يمكنك ذلك. هناك الكثير من الأسباب الوجيهة لاستخدام الوراثة (inheritance) والعديد من الأسباب الوجيهة لاستخدام التكوين (composition). النقطة الأساسية في هذا المبدأ هي أنه إذا ذهب عقلك غريزيًا إلى الوراثة (inheritance) ، فحاول التفكير فيما إذا كان التركيب يمكن أن يصوغ مشكلتك بشكل أفضل. في بعض الحالات يمكن ذلك.


قد تتساءل إذن ، "متى يمكنني استخدام الوراثة (inheritance)" يعتمد ذلك على مشكلتك التي تواجهها ، ولكن هذه قائمة جيدة عندما يكون الوراثة (inheritance) أكثر منطقية من التكوين:

1. ميراثك يمثل علاقة `is-a` وليس `has-a`
العلاقة (الإنسان-> الحيوان مقابل المستخدم-> تفاصيل المستخدم).
2. يمكنك إعادة استخدام الاكواد من الكلاسات الرئيسية (يمكن للبشر التحرك مثل جميع الحيوانات).
3. تريد إجراء تغييرات عامة على الكلاسات المشتقة عن تغيير الكلاس الرئيسي.
(تغيير إنفاق السعرات الحرارية لجميع الحيوانات عندما تتحرك).

**سيء:**
</div>

```php
class Employee
{
    private $name;

    private $email;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    // ...
}

// Bad because Employees "have" tax data.
// EmployeeTaxData is not a type of Employee

class EmployeeTaxData extends Employee
{
    private $ssn;

    private $salary;

    public function __construct(string $name, string $email, string $ssn, string $salary)
    {
        parent::__construct($name, $email);

        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}
```

<div dir="rtl">
**جيد:**
</div>

```php
class EmployeeTaxData
{
    private $ssn;

    private $salary;

    public function __construct(string $ssn, string $salary)
    {
        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}

class Employee
{
    private $name;

    private $email;

    private $taxData;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    public function setTaxData(EmployeeTaxData $taxData): void
    {
        $this->taxData = $taxData;
    }

    // ...
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### تجنب الواجهات الطليقة (fluent interfaces)

[الواجهات الطليقة (fluent interfaces)](https://en.wikipedia.org/wiki/Fluent_interface) هوا object oriented API تهدف إلى تحسين قابلية قراءة الكود باستخدام [Method chaining](https://en.wikipedia.org/wiki/Method_chaining).

بينما يمكن أن يكون هناك بعض السياقات ، كثيرًا ما تقوم ببناء الكائنات ، حيث يكون هذا يقلل النمط من كتابة الكثير من الكود (على سبيل المثال [PHPUnit Mock Builder](https://phpunit.de/manual/current/en/test-doubles.html)
أو [Doctrine Query Builder](http://docs.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html)),

في كثير من الأحيان يكون له بعض التكاليف:

1. يخرق [تغليف](https://ar.wikipedia.org/wiki/%D8%AA%D8%BA%D9%84%D9%8A%D9%81_(%D8%B9%D9%84%D9%88%D9%85_%D8%AD%D8%A7%D8%B3%D9%88%D8%A8)).
2. يخرق [نموذج التصميم ديكور](https://ar.wikipedia.org/wiki/%D9%86%D9%85%D9%88%D8%B0%D8%AC_%D8%A7%D9%84%D8%AA%D8%B5%D9%85%D9%8A%D9%85_%D8%AF%D9%8A%D9%83%D9%88%D8%B1).
3. أصعب لكي [mock](https://en.wikipedia.org/wiki/Mock_object) in الاختبار.
4. يجعل اختلافات الاكواد أصعب في القراءة.

لمزيد من المعلومات ، يمكنك قراءة [منشور المدونة](https://ocramius.github.io/blog/fluent-interfaces-are-evil/) الكامل حول هذا الموضوع بواسطة [Marco Pivetta](https://github.com/Ocramius).

**سيء:**
</div>

```php
class Car
{
    private $make = 'Honda';

    private $model = 'Accord';

    private $color = 'white';

    public function setMake(string $make): self
    {
        $this->make = $make;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setModel(string $model): self
    {
        $this->model = $model;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setColor(string $color): self
    {
        $this->color = $color;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = (new Car())
    ->setColor('pink')
    ->setMake('Ford')
    ->setModel('F-150')
    ->dump();
```

<div dir="rtl">
**جيد:**
</div>

```php
class Car
{
    private $make = 'Honda';

    private $model = 'Accord';

    private $color = 'white';

    public function setMake(string $make): void
    {
        $this->make = $make;
    }

    public function setModel(string $model): void
    {
        $this->model = $model;
    }

    public function setColor(string $color): void
    {
        $this->color = $color;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = new Car();
$car->setColor('pink');
$car->setMake('Ford');
$car->setModel('F-150');
$car->dump();
```

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

<div dir="rtl">

### فضل الكلاسات النهائية (final classes)

The `final` keyword should be used whenever possible:
يجب استخدام `final` كلما أمكن ذلك:

1. يمنع سلسلة الوراثة غير المنضبط.
2. تتماشى مع [التكوين (composition)](#prefer-composition-over-inheritance).
3. تتماشى مع [مبدأ المسؤولية الواحدة (Single Responsibility Principle)](#مبدأ-المسؤولية-الواحدة-single-responsibility-principle-srp) 
4.  تحث المطورين على استخدام دوال public بدلاً من توسيع الكلاس للوصول إلى الدوال private.
5. تسمح لك بتغيير الكود دون تعطيل التطبيقات التي تستخدم الكلاس.

The only condition is that your class should implement an interface and no other public methods are defined.
الشرط الوحيد هو أن الكلاس يجب أن ينفذ واجهة ولا يتم تحديد أي دوال public أخرى.

لمزيد من المعلومات يمكنك أن تقرأ [منشور المدونة](https://ocramius.github.io/blog/when-to-declare-classes-final/) حول هذا الموضوع بواسطة [Marco Pivetta (Ocramius)](https://ocramius.github.io/).

**سيء:**
</div>

```php
final class Car
{
    private $color;

    public function __construct($color)
    {
        $this->color = $color;
    }

    /**
     * @return string The color of the vehicle
     */
    public function getColor()
    {
        return $this->color;
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
interface Vehicle
{
    /**
     * @return string The color of the vehicle
     */
    public function getColor();
}

final class Car implements Vehicle
{
    private $color;

    public function __construct($color)
    {
        $this->color = $color;
    }

    public function getColor()
    {
        return $this->color;
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

## SOLID

**SOLID** هو اختصار ذاكري قدمه مايكل فيذرز للمبادئ الخمسة الأولى التي أطلقها روبرت مارتن ، وهو ما يعني خمسة مبادئ أساسية للبرمجة والتصميم الموجهين للكائنات.

 * [S: مبدأ المسؤولية الواحدة (Single Responsibility Principle, SRP)](#مبدأ-المسؤولية-الواحدة-single-responsibility-principle-srp)
 * [O: مبدأ مفتوح / مغلق (Open / Closed Principle، OCP)](#مبدأ-مفتوح-مغلق-open-closed-principle،-ocp)
 * [L: مبدأ تبديل ليسكوف (Liskov Substitution Principle, LSP)](#مبدأ-تبديل-ليسكوف-liskov-substitution-principle-lsp)
 * [I: مبدأ فصل الواجهة (Interface Segregation Principle, ISP)](#interface-segregation-principle-isp)
 * [D: مبدأ انعكاس التبعية (Dependency Inversion Principle, DIP)](#مبدأ-انعكاس-التبعية-dependency-inversion-principle-dip)

### مبدأ المسؤولية الواحدة (Single Responsibility Principle, SRP)

كما هو مذكور في Clean Code ، "يجب ألا يكون هناك أكثر من سبب لتغيير الكلاس". من المغري أن تقوم بتعبئة كلاس بالعديد من الوظائف ، مثل عندما يمكنك أن تأخذ حقيبة سفر واحدة فقط على متن رحلتك. تكمن المشكلة في أن الكلاس لن يكون متماسكًا من الناحية المفاهيمية وسيكون له العديد من الأسباب للتغيير. من المهم تقليل عدد المرات التي تحتاج فيها لتغيير الكلاس. إنه أمر مهم لأنه إذا كان هناك الكثير من الوظائف في كلاس واحدة وقمت بتعديل جزء منها ، فقد يكون من الصعب فهم كيف سيؤثر ذلك على الوحدات التابعة الأخرى في مشروعك.

**سيء:**
</div>

```php
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function changeSettings(array $settings): void
    {
        if ($this->verifyCredentials()) {
            // ...
        }
    }

    private function verifyCredentials(): bool
    {
        // ...
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
class UserAuth
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function verifyCredentials(): bool
    {
        // ...
    }
}

class UserSettings
{
    private $user;

    private $auth;

    public function __construct(User $user)
    {
        $this->user = $user;
        $this->auth = new UserAuth($user);
    }

    public function changeSettings(array $settings): void
    {
        if ($this->auth->verifyCredentials()) {
            // ...
        }
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### مبدأ مفتوح / مغلق (Open / Closed Principle، OCP)

كما ذكر برتراند ماير ، "يجب أن تكون الكيانات البرمجية (الكلاسات ، والوحدات ، والدوال ، وما إلى ذلك) مفتوحة للتمديد ، ولكنها مغلقة للتعديل." ماذا يعني ذلك ؟ ينص هذا المبدأ بشكل أساسي على أنه يجب عليك السماح للمستخدمين بإضافة وظائف جديدة دون تغيير الكود الحالي.

**سيء:**
</div>

```php
abstract class Adapter
{
    protected $name;

    public function getName(): string
    {
        return $this->name;
    }
}

class AjaxAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'ajaxAdapter';
    }
}

class NodeAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'nodeAdapter';
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        $adapterName = $this->adapter->getName();

        if ($adapterName === 'ajaxAdapter') {
            return $this->makeAjaxCall($url);
        } elseif ($adapterName === 'httpNodeAdapter') {
            return $this->makeHttpCall($url);
        }
    }

    private function makeAjaxCall(string $url): Promise
    {
        // request and return promise
    }

    private function makeHttpCall(string $url): Promise
    {
        // request and return promise
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
interface Adapter
{
    public function request(string $url): Promise;
}

class AjaxAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class NodeAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        return $this->adapter->request($url);
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### مبدأ تبديل ليسكوف (Liskov Substitution Principle, LSP)


هذا مصطلح مخيف لمفهوم بسيط للغاية. يتم تعريفه رسميًا على أنه "إذا كان S نوعًا فرعيًا من T ، فيمكن استبدال كائنات من النوع T بكائنات من النوع S (على سبيل المثال ، قد تحل كائنات من النوع S محل كائنات من النوع T) دون تغيير أي من الخصائص المرغوبة لهذا البرنامج (صحة ، مهمة تم أداؤها ، إلخ). ".


أفضل تفسير لذلك هو إذا كان لديك كلاس رئيسي وكلاس فرعي ، فيمكن استخدام الكلاس الرئيسي والكلاس الفرعي بالتبادل دون الحصول على نتائج غير صحيحة. قد يكون هذا محيرًا ، لذلك دعونا نلقي نظرة على مثال Square-Rectangle الكلاسيكي. من الناحية الحسابية ، يعتبر المربع مستطيلًا ، ولكن إذا قمت بنمذجه باستخدام علاقة "is-a" عبر الوراثة ، فسوف تقع في مشكلة بسرعة.

**سيء:**
</div>

```php
class Rectangle
{
    protected $width = 0;

    protected $height = 0;

    public function setWidth(int $width): void
    {
        $this->width = $width;
    }

    public function setHeight(int $height): void
    {
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Rectangle
{
    public function setWidth(int $width): void
    {
        $this->width = $this->height = $width;
    }

    public function setHeight(int $height): void
    {
        $this->width = $this->height = $height;
    }
}

function printArea(Rectangle $rectangle): void
{
    $rectangle->setWidth(4);
    $rectangle->setHeight(5);

    // BAD: Will return 25 for Square. Should be 20.
    echo sprintf('%s has area %d.', get_class($rectangle), $rectangle->getArea()) . PHP_EOL;
}

$rectangles = [new Rectangle(), new Square()];

foreach ($rectangles as $rectangle) {
    printArea($rectangle);
}
```

<div dir="rtl">
**جيد:**

أفضل طريقة هي فصل المربعات وتخصيص نوع فرعي أكثر عمومية لكلا الشكلين.

على الرغم من التشابه الواضح بين المربع والمستطيل ، إلا أنهما مختلفان.
يشترك المربع كثيرًا مع المعين ، والمستطيل بمتوازي أضلاع ، لكنهما ليسا أنواعًا فرعية.
المربع ، المستطيل ، المعين ، متوازي الأضلاع هي أشكال منفصلة لها خصائصها الخاصة ، وإن كانت متشابهة.
</div>

```php
interface Shape
{
    public function getArea(): int;
}

class Rectangle implements Shape
{
    private $width = 0;
    private $height = 0;

    public function __construct(int $width, int $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square implements Shape
{
    private $length = 0;

    public function __construct(int $length)
    {
        $this->length = $length;
    }

    public function getArea(): int
    {
        return $this->length ** 2;
    }
}

function printArea(Shape $shape): void
{
    echo sprintf('%s has area %d.', get_class($shape), $shape->getArea()).PHP_EOL;
}

$shapes = [new Rectangle(4, 5), new Square(5)];

foreach ($shapes as $shape) {
    printArea($shape);
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### مبدأ فصل الواجهة (Interface Segregation Principle, ISP)

ينص ISP على أنه "لا ينبغي إجبار اجزاء الكود على الاعتماد على الواجهات التي لا يستخدمونها."

من الأمثلة الجيدة التي يجب النظر إليها والتي توضح هذا المبدأ هي الكلاسات التي تتطلب إعدادات كبيرة. يعد عدم مطالبة الكود بإعداد كميات هائلة من الخيارات أمرًا مفيدًا ، لأنهم في معظم الأوقات لن يحتاجوا إلى جميع الإعدادات. يساعد جعلها اختيارية على منع وجود "واجهة سمينة" (fat interface).

**سيء:**
</div>

```php
interface Employee
{
    public function work(): void;

    public function eat(): void;
}

class HumanEmployee implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        // ...... eating in lunch break
    }
}

class RobotEmployee implements Employee
{
    public function work(): void
    {
        //.... working much more
    }

    public function eat(): void
    {
        //.... robot can't eat, but it must implement this method
    }
}
```

<div dir="rtl">
**جيد:**

ليس كل عامل موظفًا ، لكن كل موظف عامل.
</div>

```php
interface Workable
{
    public function work(): void;
}

interface Feedable
{
    public function eat(): void;
}

interface Employee extends Feedable, Workable
{
}

class HumanEmployee implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        //.... eating in lunch break
    }
}

// robot can only work
class RobotEmployee implements Workable
{
    public function work(): void
    {
        // ....working
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

### مبدأ انعكاس التبعية (Dependency Inversion Principle, DIP)

ينص هذا المبدأ على شيئين أساسيين:
1. يجب ألا تعتمد الوحدات عالية المستوى على وحدات المستوى المنخفض. كلاهما يجب أن يعتمد على الأفكار المجردة
2. يجب ألا تعتمد التجريدات على التفاصيل. بل يجب أن تعتمد التفاصيل على
التجريد.

قد يكون من الصعب فهم هذا في البداية ، ولكن إذا كنت قد عملت مع أطر عمل PHP (مثل Symfony) ، فقد رأيت تطبيقًا لهذا المبدأ في شكل Dependency Injection (DI). على الرغم من أنها ليست مفاهيم متطابقة ، إلا أن DIP تمنع الوحدات عالية المستوى من معرفة تفاصيل الوحدات ذات المستوى المنخفض وإعدادها. يمكنه تحقيق ذلك من خلال DI. فائدة كبيرة من هذا هو أنه يقلل من الاقتران بين الوحدات. يعتبر الاقتران نمط تطوير سيئًا للغاية لأنه يجعل من الصعب إعادة بناء الكود الخاص بك.

**سيء:**
</div>

```php
class Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot extends Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
interface Employee
{
    public function work(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

## لا تكرر نفسك (Don’t repeat yourself, DRY)

حاول مراعاة مبدأ [لا تكرر نفسك (DRY)](https://ar.wikipedia.org/wiki/%D9%84%D8%A7_%D8%AA%D9%83%D8%B1%D8%B1_%D9%86%D9%81%D8%B3%D9%83).

ابذل قصارى جهدك لتجنب تكرار الكود. يعد الكود المكرر أمرًا سيئًا لأنه يعني أن هناك أكثر من مكان واحد لتغيير شيء ما إذا كنت بحاجة إلى تغيير بعض المنطق.

تخيل أنك تدير مطعمًا وتتابع مخزونك: كل الطماطم ، والبصل ، والثوم ، والتوابل ، وما إلى ذلك. إذا كانت لديك قوائم متعددة تحتفظ بها ، فيجب تحديثها جميعًا عند تقديم طبق فيه طماطم. إذا كان لديك قائمة واحدة فقط ، فهناك مكان واحد فقط لتحديثه!

غالبًا ما يكون لديك كود مكرر لأن لديك شيئين مختلفين أو أكثر قليلاً ، يشتركان في الكثير من القواسم المشتركة ، لكن الاختلافات بينهما تجبرك على وجود دالتين منفصلتين أو أكثر تقومان بالكثير من الأشياء نفسها. إزالة الكود المكرر تعني إنشاء تجريد يمكنه التعامل مع هذه المجموعة من الأشياء المختلفة بدالة / وحدة / كلاس واحد فقط.

يعد الحصول على فكرة التجريد أمرًا بالغ الأهمية ، ولهذا السبب يجب عليك اتباع مبادئ SOLID الموضحة في قسم [الكلاسات](#الكلاسات). يمكن أن تكون التجريدات السيئة أسوأ من الاكواد المكررة ، لذا كن حذرًا! بعد قولي هذا ، إذا كان بإمكانك عمل فكرة تجريدية جيدة ، فافعل ذلك! لا تكرر نفسك ، وإلا ستجد نفسك تقوم بتحديث أماكن متعددة في أي وقت تريد تغيير شيء واحد.

**سيء:**
</div>

```php
function showDeveloperList(array $developers): void
{
    foreach ($developers as $developer) {
        $expectedSalary = $developer->calculateExpectedSalary();
        $experience = $developer->getExperience();
        $githubLink = $developer->getGithubLink();
        $data = [$expectedSalary, $experience, $githubLink];

        render($data);
    }
}

function showManagerList(array $managers): void
{
    foreach ($managers as $manager) {
        $expectedSalary = $manager->calculateExpectedSalary();
        $experience = $manager->getExperience();
        $githubLink = $manager->getGithubLink();
        $data = [$expectedSalary, $experience, $githubLink];

        render($data);
    }
}
```

<div dir="rtl">
**جيد:**
</div>

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        $expectedSalary = $employee->calculateExpectedSalary();
        $experience = $employee->getExperience();
        $githubLink = $employee->getGithubLink();
        $data = [$expectedSalary, $experience, $githubLink];

        render($data);
    }
}
```
<div dir="rtl">

**جيد جدا:**

It is better to use a compact version of the code.
</div>

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        render([$employee->calculateExpectedSalary(), $employee->getExperience(), $employee->getGithubLink()]);
    }
}
```
<div dir="rtl">

**[⬆ الرجوع إلى الأعلى](#الفهرس)**

## الترجمات

اللغات الأخرى المتاحة:


* :uk: **الإنجليزية:**
   * [jupeter/clean-code-php](https://github.com/jupeter/clean-code-php)
* :cn: **الصينية:**
   * [php-cpm/clean-code-php](https://github.com/php-cpm/clean-code-php)
* :ru: **الروسية:**
   * [peter-gribanov/clean-code-php](https://github.com/peter-gribanov/clean-code-php)
* :es: **الأسبانية:**
   * [fikoborquez/clean-code-php](https://github.com/fikoborquez/clean-code-php)
* :brazil: **البرتغالية:**
   * [fabioars/clean-code-php](https://github.com/fabioars/clean-code-php)
   * [jeanjar/clean-code-php](https://github.com/jeanjar/clean-code-php/tree/pt-br)
* :thailand: **التايلاندية:**
   * [panuwizzle/clean-code-php](https://github.com/panuwizzle/clean-code-php)
* :fr: **الفرنسية:**
   * [errorname/clean-code-php](https://github.com/errorname/clean-code-php)
* :vietnam: **الفيتنامية:**
   * [viethuongdev/clean-code-php](https://github.com/viethuongdev/clean-code-php)
* :kr: **الكورية:**
   * [yujineeee/clean-code-php](https://github.com/yujineeee/clean-code-php)
* :tr: **التركية:**
   * [anilozmen/clean-code-php](https://github.com/anilozmen/clean-code-php)
* :iran: **الفارسية:**
   * [amirshnll/clean-code-php](https://github.com/amirshnll/clean-code-php)
* :bangladesh: **البنغالية:**
   * [nayeemdev/clean-code-php](https://github.com/nayeemdev/clean-code-php)


**[⬆ الرجوع إلى الأعلى](#الفهرس)**

</div>