# راه‌اندازی Git روی Windows

این سند برای شروع از صفر نوشته شده. ابزار خط فرمان این دوره **Git Bash** است تا دستورهای اصلی یکدست باشند. مثال‌های `PowerShell` فقط وقتی مشخص شده‌اند به کار می‌روند.

## ۱. نصب Git

روش ساده: از [صفحه رسمی Git for Windows](https://git-scm.com/install/windows) نصب‌کننده متناسب با معماری دستگاه را دریافت و نصب کن. در تنظیمات نصب، برای شروع گزینه‌های پیش‌فرض مناسب‌اند؛ اگر گزینه‌ای را نمی‌فهمی، تغییرش نده.

روش جایگزین در `PowerShell` (اگر `winget` نصب است):

```powershell
winget install --id Git.Git -e --source winget
```

**نکته:** بسته `winget` لزوماً توسط تیم Git for Windows نگهداری نمی‌شود. مسیر رسمی دانلود بالا مرجع اصلی ماست.

## ۲. باز کردن ترمینال

از Start، برنامه `Git Bash` را باز کن. علامت `$` که در آموزش‌های اینترنتی می‌بینی، معمولاً بخشی از دستور نیست و نباید تایپ شود.

```bash
git --version
pwd
ls
```

- `git --version`: نمایش نسخه نصب‌شده.
- `pwd`: نمایش مسیر پوشه فعلی.
- `ls`: نمایش فایل‌ها و پوشه‌ها.

اگر پیام `git: command not found` دیدی، نصب را بررسی کن و پنجره ترمینال را دوباره باز کن.

## ۳. تنظیم هویت برای Commit

نام و ایمیلی که Git داخل Commit ثبت می‌کند باید آگاهانه انتخاب شوند. برای مخزن عمومی می‌توانی از ایمیل `noreply` حساب GitHub استفاده کنی (GitHub Settings → Emails).

```bash
git config --global user.name "Your Display Name"
git config --global user.email "YOUR_GITHUB_NOREPLY_EMAIL"
git config --global init.defaultBranch main
git config --global --list
```

**خیلی مهم:** متن‌های داخل کوتیشن نمونه‌اند؛ مقدار واقعی خودت را قرار بده. ایمیل ثبت‌شده در تاریخچه یک مخزن عمومی ممکن است قابل مشاهده باشد. هیچ رمز یا توکنی در `git config` ذخیره نکن.

## ۴. ساخت پوشه و دریافت مخزن دوره

```bash
cd ~
mkdir -p git-learning
cd git-learning
git clone https://github.com/arash13/LearningGitAndGithub-ZerotoHero.git
cd LearningGitAndGithub-ZerotoHero
git status
git remote -v
git log --oneline -3
```

**معنی عملیات:** `clone` نسخه‌ای از مخزن آنلاین را روی دستگاه می‌سازد. در پوشه‌ای که Clone کرده‌ای دوباره `git init` نزن. `status` وضعیت فایل‌های این مخزن محلی را نمایش می‌دهد.

اگر پوشه مقصد از قبل وجود دارد، قبل از اجرای مجدد `clone` بررسی کن آیا قبلاً مخزن را دانلود کرده‌ای. اجرای دوباره با همان نام ممکن است خطای `destination path already exists` بدهد.

## ۵. حل خطاهای متداول

| علامت | احتمال | اقدام ایمن |
|---|---|---|
| `git: command not found` | نصب یا PATH درست نیست | ترمینال تازه باز کن؛ نصب را بررسی کن |
| `not a git repository` | در پوشه اشتباه هستی | `pwd` و `ls` بزن؛ به پوشه Clone شده برو |
| `destination path already exists` | پوشه مقصد موجود است | محتویات را بررسی کن؛ پوشه دیگری انتخاب کن |
| `Permission denied` هنگام push | دسترسی یا احراز هویت کامل نیست | فعلاً طبق درس ۷ راهکار امنیتی را یاد بگیر |

## ۶. تفاوت Git و GitHub

`Git` تاریخچه نسخه‌ها را در دستگاه تو مدیریت می‌کند؛ `GitHub` یک میزبان و بستر همکاری برای مخزن‌های Git است. ذخیره Commit محلی با فرستادن آن به GitHub دو عملیات متفاوت‌اند.

**گام بعد:** [هفته ۱](../lessons/phase-01/week-01.md).

مراجع: [Git for Windows](https://git-scm.com/install/windows) و [First-Time Git Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup).
