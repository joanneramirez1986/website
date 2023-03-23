---
title: מגבלת אישור כפול
slug: מגבלת-אישור-כפול
top_graphic: 1
date: 2022-06-16
lastmod: 2022-06-16
show_lastmod: 1
---


# תיאור
כל בקשות ההנפקה כפופות למגבלת *כפל אישורים* של עד 5 בשבוע. אמורה להופיע הודעת שגיאה כמו זאת מלקוח ה־ACME שלך כשחרגת ממגבלת כפל האישורים:
```
כבר הונפקו יותר מדי (5) אישורים לקבוצת שמות התחום המסוימת הזאת ב־168 השעות האחרונות: example.com login.example.com: לפרטים נוספים נא לגשת אל https://letsencrypt.org/docs/duplicate-certificate-limit
```
„הקבוצה המסוימת” שהשגיאה הזאת מתייחסת אליה היא קבוצה של שמות תחום שהתבקשו לאישור הזה: בדוגמה הזאת `example.com` ו־`login.example.com`. אם האישור שלך הונפק לשם אחד בלבד, כגון example.com אז „הקבוצה המסוימת” של שמות תחום לאישור שלך תהיה `[example.com]`. מגבלת קצב זאת מגיעה לחריגה כאשר המנוי מבקש אישור לאותה „קבוצה מסוימת” של שמו תתחום למעלה מ־5 פעמים בשבוע יחיד.

# גורמים נפוצים

מנויים שמגיעים למגבלת כפל אישורים בדרך כלל עושים זאת תוך ניסיון לאתר תקלות בהטמעת היישום או השירות שלהם. למשל:

אם נתקלת בשגיאה מלקוח ה־ACME שלך שלא הצלחת לזהות וניסית להסיר ולהתקין את לקוח ה־ACME שלך מחדש מספר פעמים בחלק מניסיון לפתור את השגיאה, יכול להיות שעברת את מגבלת כפל האישורים.

מחיקת נתוני ההגדרות של לקוח ה־ACME שלך אחרי כל ניסיון כושל בהתקנת אישור תוביל אותך למגבלת קצב זאת לאחר חמישה ניסיונות כושלים. עדיף לשמור על עותק של נתוני ההגדרות בטרם מחיקתם, כדי שתהיה לך גישה לאישורים ומפתחות פרטיים שהונפקו בעבר למקרה הצורך.

בעת ניסיון לפתור תקלות או לבדוק את הטמעת היישומים שלך עדיף לנו שלקוח ה־ACME שלך יוגדר להשתמש ב[סביבת ההכנה להקמה שלנו](/docs/staging-environment/). מגבלות הקצב לסביבת ההכנה להקמה שלנו [גבוהות בהרבה](/docs/staging-environment/#rate-limits).

# בקשת עזרה

אם לא ברור לך איך להגדיר את לקוח ה־ACME שלך להשתמש בסביבת ההכנה להקמה או שנדרשת לך עזרה בניפוי שגיאות, אנו מזמינים אותך [לבקש עזרה בפורום הקהילתי שלנו](https://community.letsencrypt.org/c/help/13).

# בקשת מעקף

**אין** מעקפים זמינים למגבלת כפל האישורים.

# דרך לעקיפת המגבלה

שלילת אישורים שהונפקו בעבר לא תאפס את מגבלת כפל האישורים. עם זאת, אם גילית שחרגת מהמגבלה ועדיין נחוץ לך אישור נוסף לאותו שם התחום, תמיד אפשר לבקש אישור ל„קבוצה מסוימת” אחרת של שמות תחום. למשל, אם חרגת ממגבלת כפל אישורים עבור `[example.com]` אז הגשת בקשה לאישור עבור `[example.com, login.example.com]` תצליח. באופן דומה, אם חרגת ממגבלת כפל אישורים עבור `[example.com,
login.example.com]` אז הגשת בקשה לאישור נפרד עבור `[example.com]` ואחד נוסף עבור `[login.example.com]` תצליח.

# מעקב אחר מגבלות קצב

אנחנו לא מציעים דרך לעקוב אחר מגבלות קצב למנוי כרגע.