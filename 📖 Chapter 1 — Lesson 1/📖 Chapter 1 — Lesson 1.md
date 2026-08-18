📖 Chapter 1 — Lesson 1
☸️ Kubernetes چیست و چرا به وجود آمد؟

⭐ این اولین و مهم‌ترین درس دوره است.

اگر این درس را به‌خوبی یاد بگیری، دلیل وجود Kubernetes و فلسفه طراحی آن را درک خواهی کرد و یادگیری مباحث بعدی برایت بسیار ساده‌تر خواهد شد.

🎯 هدف درس

در پایان این درس باید بتوانی:

Kubernetes را با زبان خودت توضیح بدهی.
دلیل به وجود آمدن Kubernetes را بدانی.
مفهوم Container Orchestration را درک کنی.
تفاوت Docker و Kubernetes را توضیح بدهی.
مفهوم Desired State و Actual State را بفهمی.
🧠 مفهوم اصلی

Kubernetes یک پلتفرم متن‌باز (Open Source) برای مدیریت و هماهنگ‌سازی (Orchestration) برنامه‌های Containerized است.

به زبان ساده:

Kubernetes خودش برنامه اجرا نمی‌کند؛ بلکه مدیریت می‌کند که برنامه‌ها چگونه اجرا شوند، کجا اجرا شوند، چند نسخه از آن‌ها اجرا شود و اگر مشکلی پیش آمد چگونه دوباره به حالت عادی برگردند.

📚 توضیح ساده

فرض کن فقط یک Container داری.

اجرای آن بسیار راحت است.

اما حالا تصور کن:

۱۰۰ Container داری.
روی ۱۰ سرور مختلف اجرا شده‌اند.
هر لحظه ممکن است یکی Crash کند.
کاربران دائماً در حال افزایش هستند.
باید همیشه سرویس در دسترس باشد.

مدیریت این شرایط به‌صورت دستی تقریباً غیرممکن است.

اینجاست که Kubernetes وارد عمل می‌شود.

Kubernetes مانند یک مدیر حرفه‌ای عمل می‌کند و همه چیز را به‌صورت خودکار مدیریت می‌کند.

⚙️ تعریف فنی

Kubernetes یک Container Orchestration Platform است.

وظایف اصلی آن:

Deploy کردن برنامه‌ها
مدیریت Podها
Scaling
Self-Healing
Load Balancing
مدیریت وضعیت Cluster
🧠 Container Orchestration یعنی چه؟

Orchestration یعنی:

هماهنگ‌سازی و مدیریت خودکار Containerها.

Kubernetes تصمیم می‌گیرد:

برنامه روی کدام سرور اجرا شود.
چند نسخه از آن اجرا شود.
اگر خراب شد چه اتفاقی بیفتد.
چگونه بین چند سرور توزیع شود.
⚙️ Desired State و Actual State

یکی از مهم‌ترین مفاهیم Kubernetes همین است.

Desired State

وضعیتی که ما می‌خواهیم.

مثال:

همیشه ۳ Pod اجرا شود.
Actual State

وضعیت واقعی Cluster در همین لحظه.

مثال:

الان فقط ۲ Pod در حال اجرا هستند.

اگر این دو با هم برابر نباشند، Kubernetes تلاش می‌کند آن‌ها را یکسان کند.

به این فرآیند گفته می‌شود:

Reconciliation

🔍 مثال واقعی

فرض کن Backend یک فروشگاه اینترنتی را روی Kubernetes اجرا کرده‌ای.

تعریف کرده‌ای:

همیشه ۵ Pod اجرا شوند.

یکی از Podها Crash می‌کند.

اتفاقی که می‌افتد:

Desired State = 5 Pods

↓

Actual State = 4 Pods

↓

Kubernetes متوجه اختلاف می‌شود

↓

یک Pod جدید ایجاد می‌کند

↓

Actual State = Desired State

کاربران حتی متوجه این خرابی نمی‌شوند.

🐳 Docker یا Kubernetes؟
Docker	Kubernetes
ساخت Image	مدیریت Podها
اجرای Container	مدیریت Cluster
بسته‌بندی برنامه	Scaling
اجرای برنامه	Self-Healing

به زبان ساده:

Docker برنامه را اجرا می‌کند، Kubernetes برنامه‌ها را مدیریت می‌کند.

⚠️ اشتباهات رایج

❌ Kubernetes جای Docker را می‌گیرد.

✅ خیر؛ Kubernetes معمولاً از یک Container Runtime برای اجرای Containerها استفاده می‌کند.

❌ Kubernetes فقط برنامه اجرا می‌کند.

✅ خیر؛ وظیفه اصلی آن مدیریت و هماهنگی است.

❌ Desired State فقط یک‌بار بررسی می‌شود.

✅ Kubernetes دائماً وضعیت Cluster را بررسی می‌کند.

📝 خلاصه
Kubernetes یک Container Orchestrator است.
متن‌باز (Open Source) است.
برای مدیریت برنامه‌های Containerized ساخته شده است.
همیشه تلاش می‌کند Actual State را به Desired State برساند.
یکی از مهم‌ترین قابلیت‌های آن Self-Healing است.
🧠 کلمات کلیدی
Kubernetes
Container
Docker
Container Orchestration
Desired State
Actual State
Reconciliation
Self-Healing
Pod
Cluster
❓ سؤالات ارزیابی
سؤالات مفهومی
۱. Kubernetes چیست؟
۲. چرا Kubernetes به وجود آمد؟
۳. Container Orchestration یعنی چه؟
۴. تفاوت Docker و Kubernetes چیست؟
۵. Desired State چیست؟
۶. Actual State چیست؟
۷. چرا Kubernetes دائماً وضعیت Cluster را بررسی می‌کند؟
🧩 سؤال سناریویی

فرض کن گفته‌ای:

همیشه ۳ Pod در حال اجرا باشند.

اکنون یکی از Podها Crash می‌کند.

پاسخ بده:

Kubernetes چه چیزی را تشخیص می‌دهد؟
چرا متوجه می‌شود مشکلی وجود دارد؟
چه کاری انجام می‌دهد؟
در نهایت چه اتفاقی می‌افتد؟
✅ پاسخ سؤالات
۱. Kubernetes چیست؟

Kubernetes یک پلتفرم متن‌باز برای مدیریت و هماهنگ‌سازی (Orchestration) برنامه‌های Containerized است.

۲. چرا Kubernetes به وجود آمد؟

برای اینکه مدیریت تعداد زیادی Container و سرور به‌صورت خودکار انجام شود و نیازی به مدیریت دستی نباشد.

۳. Container Orchestration یعنی چه؟

یعنی مدیریت و هماهنگ‌سازی خودکار Containerها؛ مانند تعیین محل اجرا، تعداد نسخه‌ها، بازیابی در صورت خرابی و توزیع بار.

۴. تفاوت Docker و Kubernetes چیست؟

Docker برای ساخت Image و اجرای Container استفاده می‌شود.

Kubernetes برای مدیریت Containerها، Podها و کل Cluster استفاده می‌شود.

۵. Desired State چیست؟

وضعیتی که کاربر از Kubernetes انتظار دارد.

مثال:

همیشه ۳ Pod اجرا شوند.
۶. Actual State چیست؟

وضعیت واقعی Cluster در همان لحظه.

مثال:

در حال حاضر فقط ۲ Pod اجرا هستند.
۷. چرا Kubernetes دائماً وضعیت Cluster را بررسی می‌کند؟

تا اگر Actual State با Desired State متفاوت شد، بتواند آن را اصلاح کند و سیستم را به وضعیت مطلوب بازگرداند.

✅ پاسخ سؤال سناریویی
۱. Kubernetes چه چیزی را تشخیص می‌دهد؟

تشخیص می‌دهد که یکی از Podها از کار افتاده و تعداد Podهای در حال اجرا کمتر از مقدار موردنظر شده است.

۲. چرا متوجه می‌شود مشکلی وجود دارد؟

چون Desired State با Actual State برابر نیست.

۳. چه کاری انجام می‌دهد؟

یک Pod جدید روی یک Worker Node سالم ایجاد می‌کند تا اختلاف را برطرف کند.

۴. در نهایت چه اتفاقی می‌افتد؟

تعداد Podها دوباره به مقدار تعریف‌شده می‌رسد و Actual State با Desired State برابر می‌شود.

💡 نکات طلایی این درس

⭐ Kubernetes یک Container Orchestrator است، نه یک Container Runtime.

⭐ مهم‌ترین هدف Kubernetes حفظ Desired State است.

⭐ Docker و Kubernetes مکمل یکدیگر هستند، نه رقیب.

⭐ یکی از مهم‌ترین قابلیت‌های Kubernetes، Self-Healing است.

⭐ Kubernetes دائماً وضعیت Cluster را بررسی می‌کند و در صورت نیاز آن را اصلاح می‌کند.

➡️ پیش‌نیاز درس بعد

در درس دوم با معماری Kubernetes (Kubernetes Architecture) آشنا می‌شوی و یاد می‌گیری که یک Cluster از چه بخش‌هایی تشکیل شده است، تفاوت Control Plane و Worker Node چیست و هر کدام چه وظیفه‌ای دارند.
