📖 Chapter 1 — Lesson 2
🏗️ معماری Kubernetes (Kubernetes Architecture)

⭐ این مهم‌ترین درس کل دوره است.

اگر این درس را به‌خوبی یاد بگیری، حدود ۷۰٪ معماری Kubernetes را از نظر مفهومی درک خواهی کرد و یادگیری اجزای داخلی آن بسیار ساده‌تر می‌شود.

🎯 هدف درس

در پایان این درس باید بتوانی:

معماری Kubernetes را توضیح بدهی.
تفاوت Control Plane و Worker Node را بدانی.
بدانی Podها روی کجا اجرا می‌شوند.
مسیر اجرای یک برنامه در Kubernetes را توضیح بدهی.
یک Kubernetes Cluster را به‌صورت کلی رسم کنی.
🧠 مفهوم اصلی

یک Kubernetes Cluster از دو بخش اصلی تشکیل شده است.

Kubernetes Cluster
│
├── Control Plane
│
└── Worker Nodes

تقریباً تمام اجزایی که در آینده یاد می‌گیری داخل یکی از این دو بخش قرار می‌گیرند.

📚 توضیح ساده

فرض کن یک شرکت ساختمانی داری.

دو قسمت اصلی دارد.

۱) دفتر مدیریت

اینجا مدیران تصمیم می‌گیرند:

چه کسی کار کند.
کجا کار کند.
چه تعداد نیرو لازم باشد.
چه زمانی پروژه اجرا شود.

این قسمت همان Control Plane است.

۲) کارگاه ساختمانی

تمام کار واقعی اینجا انجام می‌شود.

کارگرها
ماشین‌آلات
ساخت ساختمان

این قسمت همان Worker Node است.

پس خیلی ساده:

Control Plane

↓

فکر می‌کند

↓

Worker Node

↓

کار انجام می‌دهد
⚙️ تعریف فنی

یک Kubernetes Cluster شامل دو بخش اصلی است.

Control Plane

بخش مدیریتی Kubernetes است.

وظایف آن:

مدیریت کل Cluster
تصمیم‌گیری
زمان‌بندی (Scheduling)
نگهداری Desired State
مدیریت API
Worker Node

بخشی است که:

Podها
Containerهای داخل Pod

واقعاً روی آن اجرا می‌شوند.

🔍 مثال واقعی

فرض کن Backend دیجی‌کالا روی Kubernetes اجرا شده است.

وقتی یک کاربر درخواست ارسال می‌کند، Kubernetes باید تصمیم بگیرد Backend روی کدام سرور اجرا شود.

ابتدا Control Plane تصمیم می‌گیرد.

سپس Worker Node آن Pod را اجرا می‌کند.

🏗️ معماری Kubernetes
                    Kubernetes Cluster

      ┌────────────────────────────────────┐
      │                                    │
      │          Control Plane             │
      │                                    │
      │  API Server                        │
      │  Scheduler                         │
      │  Controller Manager                │
      │  etcd                              │
      │                                    │
      └────────────────────────────────────┘
                     │
         ───────────────────────────
                     │
      ┌──────────────┴──────────────┐
      │                             │
┌─────────────┐             ┌─────────────┐
│ Worker Node │             │ Worker Node │
│             │             │             │
│ kubelet     │             │ kubelet     │
│ kube-proxy  │             │ kube-proxy  │
│ Pods        │             │ Pods        │
└─────────────┘             └─────────────┘
🧠 اجزایی که فعلاً فقط باید بشناسیم
داخل Control Plane
API Server
Scheduler
Controller Manager
etcd
داخل Worker Node
kubelet
kube-proxy
Container Runtime
Pods

فعلاً فقط اسم آن‌ها را به خاطر بسپار.

در درس‌های آینده تک‌تک آن‌ها را به‌صورت کامل یاد می‌گیریم.

📦 مثال مرحله‌به‌مرحله

فرض کن می‌گویی:

«می‌خواهم ۳ Pod اجرا شوند.»

اتفاقی که می‌افتد:

You

↓

API Server

↓

Scheduler

↓

Worker Node

↓

Pod

↓

Running
⚠️ اشتباهات رایج

❌ Control Plane برنامه‌ها را اجرا می‌کند.

✅ خیر؛ فقط مدیریت و تصمیم‌گیری می‌کند.

❌ Pod داخل Control Plane اجرا می‌شود.

✅ خیر؛ Podها روی Worker Node اجرا می‌شوند.

❌ هر Node یک Control Plane است.

✅ خیر؛ بیشتر Nodeها فقط Worker Node هستند.

❌ اگر یک Pod خراب شود، Kubernetes همیشه یک Worker Node جدید می‌سازد.

✅ خیر؛ معمولاً فقط Pod را روی یک Worker Node سالم دوباره اجرا می‌کند.

📝 خلاصه
Kubernetes Cluster از دو بخش تشکیل شده است.
Control Plane مغز Kubernetes است.
Worker Node محل اجرای Podها است.
Podها هرگز روی Control Plane اجرا نمی‌شوند.
Control Plane تصمیم می‌گیرد و Worker Node اجرا می‌کند.
🧠 کلمات کلیدی
Kubernetes Cluster
Control Plane
Worker Node
API Server
Scheduler
Controller Manager
etcd
kubelet
kube-proxy
Container Runtime
Pod
❓ سؤالات ارزیابی
سؤالات مفهومی
۱. Kubernetes Cluster از چند بخش اصلی تشکیل شده است؟
۲. وظیفه Control Plane چیست؟
۳. وظیفه Worker Node چیست؟
۴. Pod روی کدام بخش اجرا می‌شود؟
۵. چرا Control Plane و Worker Node از هم جدا هستند؟
🧩 سؤال سناریویی

فرض کن یک Cluster داری که شامل:

۱ Control Plane
۳ Worker Node

و تعریف کرده‌ای:

همیشه ۱۰ Pod در حال اجرا باشند.

حالا یکی از Podها روی Worker Node شماره ۲ از کار می‌افتد، اما خود Worker Node سالم است.

پاسخ بده:

Kubernetes ابتدا چه چیزی را تشخیص می‌دهد؟
چرا متوجه می‌شود مشکلی وجود دارد؟
چه بخشی تصمیم می‌گیرد Pod جدید کجا اجرا شود؟
Pod جدید روی کجا اجرا می‌شود؟
آیا Kubernetes یک Worker Node جدید می‌سازد؟
✅ پاسخ سؤالات
۱. Kubernetes Cluster از چند بخش اصلی تشکیل شده است؟

از دو بخش اصلی تشکیل شده است:

Control Plane
Worker Node
۲. وظیفه Control Plane چیست؟

Control Plane مغز Kubernetes است و وظیفه آن:

مدیریت Cluster
تصمیم‌گیری
زمان‌بندی (Scheduling)
نگهداری Desired State
مدیریت API
۳. وظیفه Worker Node چیست؟

Worker Node محل اجرای Podها و Containerهای داخل Pod است.

تمام پردازش واقعی برنامه‌ها روی Worker Node انجام می‌شود.

۴. Pod روی کدام بخش اجرا می‌شود؟

Podها فقط روی Worker Node اجرا می‌شوند.

۵. چرا Control Plane و Worker Node از هم جدا هستند؟

چون Kubernetes از اصل تفکیک مدیریت از اجرا (Separation of Control and Execution) استفاده می‌کند.

Control Plane فقط مدیریت و تصمیم‌گیری می‌کند.
Worker Node فقط برنامه‌ها را اجرا می‌کند.

این جداسازی باعث افزایش پایداری، مقیاس‌پذیری و مدیریت بهتر Cluster می‌شود.

✅ پاسخ سؤال سناریویی
۱. Kubernetes ابتدا چه چیزی را تشخیص می‌دهد؟

تشخیص می‌دهد که یکی از Podها از کار افتاده و تعداد Podهای در حال اجرا کمتر از مقدار موردنظر شده است.

۲. چرا متوجه می‌شود مشکلی وجود دارد؟

چون Desired State با Actual State برابر نیست.

مثلاً:

Desired State = 10 Pods

Actual State = 9 Pods
۳. چه بخشی تصمیم می‌گیرد Pod جدید کجا اجرا شود؟

داخل Control Plane، مؤلفه Scheduler تصمیم می‌گیرد Pod روی کدام Worker Node اجرا شود.

۴. Pod جدید روی کجا اجرا می‌شود؟

روی یکی از Worker Nodeهای سالم اجرا می‌شود.

۵. آیا Kubernetes یک Worker Node جدید می‌سازد؟

خیر.

در حالت عادی Kubernetes فقط یک Pod جدید ایجاد می‌کند.

ساخت Worker Node جدید به زیرساخت (مانند AWS، Azure، GCP یا ماشین‌های مجازی) بستگی دارد و در مباحث پیشرفته مانند Cluster Autoscaler با آن آشنا خواهیم شد.

💡 نکات طلایی این درس

⭐ Control Plane مغز Kubernetes است.

⭐ Worker Node محل اجرای Podها است.

⭐ Podها هرگز روی Control Plane اجرا نمی‌شوند.

⭐ Scheduler تصمیم می‌گیرد Pod روی کدام Worker Node اجرا شود.

⭐ Kubernetes در حالت عادی Node جدید نمی‌سازد؛ فقط Podها را برای رسیدن به Desired State دوباره اجرا می‌کند.

➡️ پیش‌نیاز درس بعد

در 📖 Chapter 1 — Lesson 3 وارد قلب Kubernetes می‌شویم و با API Server آشنا می‌شویم؛ مهم‌ترین مؤلفه Control Plane که تمام درخواست‌های Kubernetes ابتدا از آن عبور می‌کنند. این درس یکی از کلیدی‌ترین بخش‌های کل دوره خواهد بود.
