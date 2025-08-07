## گزارش

  
  

## پاسخ سوالات

<div dir="rtl">

<ol>
<li>
 پوشه‌ی .git چیست؟ چه اطلاعاتی در آن ذخیره می‌شود؟ با چه دستوری ساخته می‌شود؟
<br>
پوشه‌ی .git یک دایرکتوری مخفی است که هسته‌ی اصلی Git محسوب می‌شود و تمامی متادیتا و تاریخچه‌ی پروژه را ذخیره می‌کند. این پوشه با اجرای دستور git init ساخته می‌شود.
محتویات مهم این پوشه به صورت زیر هستند: <br>
<ul dir="rtl">
<li> <b>objects/</b> :
    حاوی تمام کامیت‌ها، فایل‌ها (Blobs)، و درخت‌ها (Trees) به صورت فشرده و هش‌شده.
<li> <b>refs/</b> : شامل اشاره‌گرها به کامیت‌ها (مانند برنچ‌ها و تگ‌ها).
<li> <b>HEAD</b> : اشاره گر به کامیت فعلی
<li> <b>config</b> : فایل پیکربندی (تنظیمات محلی ریپو).
<li> <b>logs/</b> : تاریخچه تغییرات 
<li> hooks و سایر اطلاعات داخلی
</ul>
</li>

<li>
  منظور از Atomic بودن در Atomic Commit و Atomic Pull-Request چیست؟
  Atomic Commit: به این معنی که هر کامیت به عنوان یک واحد کامل اعمال می‌شود. یا تمام تغییرات کامیت ذخیره می‌شوند یا هیچ‌کدام و در صورت بروز خطا کامیتی ذخیره نمی‌شود. <br>
  Atomic Pull-Request: تمام تغییرات موجود در PR یا به طور کامل ادغام می‌شوند یا اصلاً ادغام نمی‌شوند 
  (مانند تراکنش‌های بانکی).
</li>

<li>
تفاوت دستورهای fetch و pull و merge و rebase و cherry-pick را بیان کنید.
<table>
<tr> <td> دستور </td> <td> عملکرد </td> </tr>
<tr> <td> fetch </td>
<td> دریافت تغییرات از ریموت بدون merge کردن آن‌ها </td> </tr>
<tr> <td> pull </td>
<td> ترکیب دستور fetch و merge </td> </tr>
<tr> <td> merge </td>
<td> ادغام تغییرات دو برنچ با ایجاد کامیت جدید </td> </tr>
<tr> <td> rebase </td>
<td> بازنویسی تاریخچه با انتقال کامیت‌ها به پایه جدید </td> </tr>
<tr> <td> cherry-pick </td>
<td>انتخاب یک کامیت خاص از برنچ دیگر</td> </tr>
</table>
</li>

<li>
تفاوت دستورهای reset و revert و restore و switch و checkout را بیان کنید.
    <ul dir="rtl">
    <li>reset: 
    برای بازنشانی (reset) وضعیت پروژه به یک کامیت خاص استفاده می‌شود و سه حالت اصلی دارد:
        <ul>
        <li><code dir="ltr" style="unicode-bidi: isolate;">--soft</code>:
         فقط تاریخچهٔ کامیت‌ها را تغییر می‌دهد، اما تغییرات در Staging Area باقی می‌مانند و فایل‌ها حذف نمی‌شوند.
        <li><code dir="ltr" style="unicode-bidi: isolate;">--mixed</code> (پیشفرض):
         تاریخچه و Staging Area را بازنشانی می‌کند، اما تغییرات در Working Directory باقی می‌مانند.
        <li><code dir="ltr" style="unicode-bidi: isolate;">--hard:</code>
         همه چیز را بازنشانی می‌کند. (تاریخچه، Staging Area و Working Directory) و تمام تغییرات بعد از کامیت هدف حذف می‌شوند.
        </ul>
    <li>revert:
    این دستور تغییرات را به صورت ایمن خنثی می‌کند. تاریخچه را تغییر نمی‌دهد و با ایجاد یک کامیت جدید تغییرات پروژه را به کامیت مدنظر برمی‌گرداند.
    <li>restore:
    می‌تواند  بدون تأثیر بر تاریخچه کامیت‌ها تغییرات محلی را حذف کند، فایل‌ها را از حالت staged خارج کند یا نسخه‌های قدیمی فایل‌ها را بازیابی کند. 
    <li>switch:
    از این دستور برای جا‌به‌جایی بین برنچ‌ها استفاده می‌شود. در واقع جایگزین جدید و ایمن‌تر برای برخی از کاربرد‌های checkout به حساب می‌آید.
    <li>checkout:
    از دستورات پایه‌ای و چند منظوره است که دو کاربرد اصلی دارد:
    تغییر شاخه‌ها و
    بازگرداندن فایل‌ها به حالت قبل
    <br>
    نمونه‌هایی از کاربرد استفاده‌ی این دستور:
    <br>
    <ul>
    <li><code dir="ltr" style="unicode-bidi: isolate;">git checkout &lt;branch-name&gt;</code>: 
    جا‌به‌جا شدن و رفتن به شاخه‌ی دیگر
    <li><code dir="ltr" style="unicode-bidi: isolate;">git checkout -b &lt;new-branch&gt;</code>:
    ایجاد یک شاخه‌ی جدید و سوئیچ به آن
    <li><code dir="ltr" style="unicode-bidi: isolate;">git checkout &lt;commit-hash&gt;</code>: 
    برگرداندن پروژه به یک کامیت خاص و بررسی فایل‌ها در Working Directory
    <li><code dir="ltr" style="unicode-bidi: isolate;">git checkout --&lt;file&gt;</code>:
    بازگرداندن تغییرات یک فایل خاص به آخرین نسخه‌ی ذخیره‌شده در کامیت فعلی.
    </ul>
</li>

</ol>

  </div>


