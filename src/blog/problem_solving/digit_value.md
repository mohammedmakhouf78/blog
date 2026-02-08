---
slug: "برنامج لكتابة القيمة المكانية (الخانات) لرقم"
title: "برنامج لكتابة القيمة المكانية (الخانات) لرقم"
description: كتابة دالة تقوم باستقبال رقم وطباعة القيمة المكانية لكل أرقامه.
date: 2025-12-15
author: Mo.Makhlouf
tags: ["problem_solving","computer science"]
featured: true
editable: true
---

<hr />

## المطلوب:

كتابة دالة تقوم باستقبال رقم وطباعة القيمة المكانية لكل أرقامه.


## المعطيات:

رقم : 46095

النتيجة:

طباعة التالي :

```
5 ones
9 tens
0 hundreds
6 thousands
4 ten thousands
```

## الحل مع الشرح :

علينا أن نحصل على كل رقم من الأرقام وحده ثم طباعة مكانه.

يمكننا تخزين الأماكن المتاحة بالترتيب في array ثم المرور عليها.

```ts
let placeValues = ["ones", "tens", "hundreds", "thousands", "ten thousands", "hundred thousands", "millions", "ten millions", "hundred millions"];
```

وللحصول على كل رقم على حده يمكننا استخدام الطريقة المعروفة وهي إيجاد باقي قسمة الرقم على 10.


```ts
let firstNumber = num % 10;
```

لاحظ أن 46095 % 10 = 5

فماذا عن الرقم التالي ؟ حسناً سنقوم بقسمة الرقم على 10 وحذف الأرقام العشرية.

لاحظ أن 46095 / 10 = 4609.5 ثم نحذف القسم العشري فيكون الناتج 4609 .

```ts
num = Math.floor(num / 10);
```

الآن لدينا الرقم الأول وهو 5 نقوم بطباعته مع الخانة الأولى يمككنا عمل مؤشر يشير إلى الخانة الأولى في ال array التي قمنا بصناعتها لتخيزن الخانات المتاحة وكل مره نحركه بمقدار خطوة واحده.

ثم نكرر نفس الخطوات لنحصل على النتيجة المرادة.

```ts
function numberPlaceValues(num: number) {
    let placeValues = ["ones", "tens", "hundreds", "thousands", "ten thousands", "hundred thousands", "millions", "ten millions", "hundred millions"];

    let ptr = 0;
    while (num > 0) {
        let firstNumber = num % 10;
        console.log(firstNumber + " " + placeValues[ptr]);
        num = Math.floor(num / 10);
        ptr++
    }
}
```

في الكود السابق تعمل ال while loop حتى يكون الرقم = صفر.