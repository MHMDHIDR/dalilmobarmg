---
title: تحويل اﻷنواع (Type Casting)
description: شرح تحويل أنواع البيانات وأهمية هذه العملية واستخداماتها
position: 9
category: intermediate
createdAt: 1614682578722
updatedAt: 1614682578722
new: false
updated: false
contributors:
  - ebrahimmaher
---

## مقدمة
تحويل اﻷنواع عملية مهمة يجب عليك فهمها، أثناء كتابتك للكود ستواجهك الكثير من المشاكل البرمجية التي سيكون من السهل عليك حلّها إن فهمت تحويل اﻷنواع وكيف يتم، أيضاً ستتجنب الوقوع في بعض اﻷخطاء، ركز في المشكلة التالية:

<base-alert type="warning">

تخيل أننا نطلب من المُستخدم أن يقوم بإدخال رقم في حقلٍ ما، ونقوم بتخزين ما يقوم المستخدم بإدخاله في متغير اسمه `num` لكن دائما هذه القيمة تكون نص (String) وليست عدد، الحقل نفسه يرسلها إلى المتغير `num` في صورة نصّ يعني **`"20"`** مثلاً بدلاً من **`20`** ، لكن المشكلة هنا أننا نريد طباعة ناتج جمع هذا العدد مع 10 `num + 10` وهذا لن يتم إن كان نوع المتغير نصّ (string)، لاحظ المثال التالي:

```js
var num = "2";
console.log(num + 10)
```
<code-result>
210
</code-result>

كان المتوقع أن يكون  الناتج 12 لكن ظهر الناتج 210 فما السبب؟
**السبب أننا نجمع متغير نوعه نص (string) مع آخر نوعه عدد (integer)** وهذا غير ممكن! فيقوم المفسر بتحويل المتغير الذي نوعه عدد إلى نص، ويتعامل مع العملية على أنها دمج نصوص وليست جمع عددين، كأنك كتبت `"2" + "12"` وبالتالي يكون الناتج **هو دمج النصين وليس جمعهم كأعداد!** إذن ما الحل؟ تابع....

</base-alert>

## تحويل اﻷعداد

### تحويل النصّ (string) إلى عدد (integer)
حل المشكلة السابقة هي أن نقوم أولاً بتحويل المتغير num إلى عدد بدلاً من نصّ، بالتالي عندما نقوم بعملية الجمع يتعامل المفسر معهم على أنهم عددين، فيقوم بعملية جمع عددين... ويمكننا إستخدام دالة تأتي مدمجة مع اللغة (مدمجة يعني جزء من اللغة، كدالة الطباعة مثلاً) ويختلف إسم هذه الدالة من لغة ﻷخرى، لكن تؤدي نفس الشيء...

#### الدالة `parseInt()`
يدخل لهذه الدالة مُدخل، وتقوم بإرجاع عدد من نوع integer

```js
var num = parseInt("2");
console.log(num + 10)
```
<code-result>
12
</code-result>

<base-alert type="tip">

في المثال السابق إفترضنا أننا لدينا القيمة `"2"` مكتوبة كنصّ ولا يمكننا كتابتها كعدد `2` حتى نتمكن من شرح المشكلة، لكن في اﻹستخدامات الحقيقية لن يكون اﻷمر هكذا، سيكون مثلاً هناك دالة تستدعيها لتحصل على ما أدخله المستخدم، وهذه الدالة تقوم بإرجاع ما ادخله المستخدم في نوع نصّ (string) وليس لك التحكم فيما تقوم بإرجاعه، وبالتالي ستكون مجبراً على تحويل ما تقوم بإرجاعه هذه الدالة.

</base-alert>

<base-alert type="info">
لاحظ أن المفسّر أحياناً يقوم بتحويل قيمة من نوع إلى نوع آخر تلقائياً إذا لزم اﻷمر، كما فعل مثلاً أثناء جمع نص مع عدد!، لكن هذا لا يحدث في كل اللغات!
</base-alert>

<base-alert type="error">
في بعض لغات البرمجة لن يقوم المفسر بتحويل اﻷنواع تلقائياً، فمثلاً ربما يقوم المفسر بإظهار خطأ إذا قمت بجمع نص مع عدد، أو دمج عدد مع نص وهكذا
</base-alert>

### تحويل العدد (integer) إلى نص (string)
في بعض اﻷحيان ستحتاج لتحويل العدد إلى نص، خصوصاً في لغات البرمجة الأخرى، هناك لغات برمجة لا تسمح لك مثلاً بدمج عدد مع نص، إما عدد مع عدد أو نص مع نص، بالتالي ستضطر وقتها لتحويل العدد إلى نص حتى تتمكن من دمجه مع أي نص.

#### الدالة `.toString()`
```js
var num = 2;
var numStr = num.toString();
console.log(num + 10);
console.log(numStr + 10);
```
<code-result>
12
<br>
210
</code-result>

> في السطر الثاني استخدمنا الدالة `.toString()` وهي طريقة كتابتها مختلفة قليلاً، فنكتب اسم المتغير الذي يحمل العدد ثم `.` ثم اسم الدالة `toString()`

> ناتج الطباعة اﻷول كان `12` ﻷننا قمنا بطباعة ناتج جمع المتغير `num` مع `10` والمتغير `num` هو عبارة عن عدد (integer) أما ناتج الطباعة الثاني كان `210` ﻷننا طبعنا ناتج جمع المتغير `numStr` وهو عبارة عن قيمة المتغير `num` بعد تحويلها إلى نصّ (string) بالتالي يكون ناتج الطباعة هو ناتج دمج نصوص وليس جمع أعداد. 


### تحويل النصّ (string) إلى عدد عشري (float)
كما درسنا في [درس أنواع البيانات](/tutorials/algorithms/fundamentals/datatypes) أن اﻷعداد لها نوعين من أنواع البيانات:
- **Integer**: العدد الصحيح (`1`, `2`, `3`, `4` ...)
- **Float**: العدد العشري (`1.5`, `0.75`, `2.5` ...)


واﻵن لنفرض في المشكلة التي ناقشناها باﻷعلى أننا لدينا نصّ `"2.5"` مثلاً ونريد تحويله إلى عدد، ولكن النصّ في هذه المرة يحتوي على عدد عشري! لاحظ ناتج المثال:

```js
var num = parseInt("2.5");
console.log(num);
```
<code-result>
2
</code-result>

في المثال السابق سيقوم المفسّر بتحويل العدد العشري إلى عدد صحيح، سيتجاهل العلامة العشرية وسيعتبر أن `"2.5"` هي العدد `2`


<base-alert type="error">

**ﻻ تستخدم `parseInt()` أبداً إذا كان العدد عشري!**

</base-alert>

<base-alert type="info">

**يجب استخدام `parseFloat()` مع اﻷعداد العشرية (float)**

</base-alert>


#### الدالة `parseFloat()`
هذه الدالة تقوم بنفس عمل الدالة `parseInt()` ولكن تُستخدم مع **اﻷعداد العشرية (float)** وتقوم دائماً بإرجاع عدد عشري!

```js
var num = parseFloat("2.5");
console.log(num);
console.log(num + 1);
```
<code-result>
2.5
<br>
3.5
</code-result>

<base-alert type="info">

يمكن أن تُستخدم الدالة `.toString()` أيضاً في تحويل العدد العشري إلى نصّ.

</base-alert>

### تحويل عدد عشري (float) إلى عدد (integer)
يمكن هنا استخدام الدالة `parseInt()` أيضاً للتحويل من عدد عشري إلى عدد صحيح
```js
var num = 7.25;
console.log(parseInt(num));
```
<code-result>
7
</code-result>


## التحويل المنطقي
التحويل المنطقي هي عملية تحويل القيم بكل أنواعها إلى القيم المنطقية (`true` or `false`) فمثلاً ربما قد سمعت سابقاً أن الحاسوب يعتبر أن **0** يعني **false** وأن **1** يعني **true** فهذا بالضبط ما سنتعلمه في التحويل المنطقي، وهذه العملية هامة جداً خصوصا في الشروط (if statements)، وتحتاج إلى تركيز وممارسة لفهمها والتعوّد عليها، لذلك سنتناولها في الدرس القادم!

<base-alert type="next">

سنستكمل تحويل اﻷنواع في الدرس القادم ونتحدث عن التحويل المنطقي...

</base-alert>