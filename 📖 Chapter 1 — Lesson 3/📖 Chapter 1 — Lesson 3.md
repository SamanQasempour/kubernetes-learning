# 📖 Chapter 1 — Lesson 3

# 🌐 API Server — قلب Kubernetes

⭐ **API Server یکی از مهم‌ترین مؤلفه‌های Kubernetes و دروازه اصلی ارتباط با Cluster است.**

اگر مفهوم API Server را خوب یاد بگیری، درک ارتباط بین `kubectl`، Scheduler، Controllerها، kubelet و `etcd` خیلی ساده‌تر می‌شود.

---

# 🎯 هدف درس

در پایان این درس باید بتوانی:

* API Server را توضیح بدهی.
* دلیل اهمیت API Server را بدانی.
* مسیر ورود یک درخواست به Kubernetes را توضیح بدهی.
* بدانی اجزای Kubernetes چگونه با API Server ارتباط برقرار می‌کنند.
* مفهوم Kubernetes API را درک کنی.
* تفاوت Authentication و Authorization را بدانی.
* نقش API Server در ارتباط با `etcd` را توضیح بدهی.

---

# 🧠 مفهوم اصلی

**API Server دروازه ورود به Kubernetes است.**

به‌صورت ساده:

```text
Client
   ↓
API Server
   ↓
Kubernetes
```

هرگاه بخواهیم از طریق Kubernetes API با Cluster کار کنیم، درخواست از API Server عبور می‌کند.

مثلاً:

```text
kubectl
   ↓
API Server
```

---

# 📚 توضیح ساده

فرض کن یک شرکت بزرگ داری.

همه کارمندان نمی‌توانند مستقیماً وارد اتاق مدیرعامل شوند.

آن‌ها ابتدا باید به **دفتر مرکزی** مراجعه کنند.

دفتر مرکزی:

* درخواست را دریافت می‌کند.
* هویت فرد را بررسی می‌کند.
* مجوز او را بررسی می‌کند.
* درخواست را بررسی می‌کند.
* آن را به سیستم مربوطه می‌رساند.

در Kubernetes، **API Server نقش این دروازه مرکزی را دارد.**

---

# ⚙️ تعریف فنی

**API Server** یکی از اجزای اصلی **Control Plane** است.

وظایف مهم آن:

* دریافت درخواست‌ها
* ارائه Kubernetes API
* Authentication
* Authorization
* Validation
* ارتباط با `etcd`
* پاسخ دادن به Clientها

می‌توانیم به‌صورت ساده تصور کنیم:

```text
Client
   ↓
API Server
   ↓
بررسی درخواست
   ↓
Kubernetes Components / etcd
```

---

# 🌐 API یعنی چه؟

API مخفف:

**Application Programming Interface**

است.

به زبان ساده:

> API یک رابط استاندارد برای ارتباط بین نرم‌افزارها و اجزای مختلف است.

در Kubernetes، **Kubernetes API** رابط اصلی برای مدیریت منابع Cluster است.

مثلاً منابعی مانند:

* Pod
* Deployment
* Service
* Node
* ConfigMap
* Secret

از طریق Kubernetes API قابل مدیریت هستند.

---

# 🖥️ kubectl چگونه کار می‌کند؟

فرض کن دستور زیر را اجرا می‌کنی:

```bash
kubectl get pods
```

مسیر درخواست:

```text
You
 ↓
kubectl
 ↓
API Server
 ↓
Kubernetes API
 ↓
اطلاعات Podها
 ↓
API Server
 ↓
kubectl
 ↓
You
```

⚠️ نکته بسیار مهم:

❌ `kubectl` مستقیماً با Pod ارتباط برقرار نمی‌کند.

✅ `kubectl` با **API Server** ارتباط برقرار می‌کند.

---

# 🔐 Authentication

**Authentication** یعنی:

> «تو چه کسی هستی؟»

API Server باید بتواند هویت درخواست‌کننده را مشخص کند.

به‌صورت ساده:

```text
Request
   ↓
Authentication
   ↓
چه کسی هستی؟
```

---

# 🔑 Authorization

**Authorization** یعنی:

> «آیا اجازه انجام این کار را داری؟»

مثلاً ممکن است یک کاربر اجازه مشاهده Podها را داشته باشد، اما اجازه حذف آن‌ها را نداشته باشد.

```text
Authentication
      ↓
تو چه کسی هستی؟
      ↓
Authorization
      ↓
چه اجازه‌ای داری؟
```

⭐ این دو را با هم اشتباه نکن:

| مفهوم          | سؤال              |
| -------------- | ----------------- |
| Authentication | تو چه کسی هستی؟   |
| Authorization  | چه اجازه‌ای داری؟ |

---

# ✅ Validation

API Server درخواست را از نظر اعتبار و قوانین Kubernetes نیز بررسی می‌کند.

مثلاً اگر یک Manifest دارای ساختار نامعتبر باشد، API Server می‌تواند درخواست را رد کند.

مسیر ساده:

```text
Request
   ↓
Authentication
   ↓
Authorization
   ↓
Validation
   ↓
Accepted / Rejected
```

---

# 🗄️ ارتباط API Server با etcd

`etcd` دیتاستور اصلی Kubernetes است.

اطلاعات و وضعیت منابع Kubernetes در آن نگهداری می‌شود.

مسیر ساده:

```text
Client
   ↓
API Server
   ↓
etcd
```

نه:

```text
Client
   ↓
etcd ❌
```

یعنی Clientها برای مدیریت Kubernetes نباید مستقیماً به `etcd` متصل شوند.

---

# 👥 چه کسانی با API Server صحبت می‌کنند؟

فقط `kubectl` نیست.

اجزای مختلف Kubernetes و ابزارهای خارجی می‌توانند با API Server ارتباط داشته باشند.

از جمله:

* `kubectl`
* Scheduler
* Controller Manager
* kubelet
* Dashboard
* Operatorها
* CI/CD
* برنامه‌های خارجی

به‌صورت ساده:

```text
                   API Server
                /      |       \
               /       |        \
          kubectl   Scheduler   Controller
             |         |            |
         Dashboard   kubelet     Operator
```

---

# 🏗️ مسیر یک درخواست در Kubernetes

فرض کن مدیر سیستم دستور زیر را اجرا می‌کند:

```bash
kubectl apply -f nginx.yaml
```

به‌صورت مفهومی:

```text
You
 ↓
kubectl
 ↓
API Server
 ↓
Authentication
 ↓
Authorization
 ↓
Validation
 ↓
etcd
 ↓
Scheduler
 ↓
Worker Node
 ↓
Pod
```

⭐ نکته مهم:

**Scheduler تصمیم می‌گیرد Pod روی کدام Node قرار بگیرد.**

اما Scheduler خودش Pod را اجرا نمی‌کند.

```text
Scheduler
    ↓
انتخاب Worker Node
    ↓
Worker Node
    ↓
اجرای Pod
```

---

# 🔒 چرا همه چیز از API Server عبور می‌کند؟

چند دلیل مهم دارد:

### 1. امنیت

درخواست‌ها می‌توانند بررسی و کنترل شوند.

### 2. کنترل دسترسی

مشخص می‌شود چه کسی چه کاری می‌تواند انجام دهد.

### 3. Validation

درخواست‌های نامعتبر می‌توانند رد شوند.

### 4. معماری استاندارد

اجزای مختلف یک روش استاندارد برای ارتباط با Kubernetes دارند.

### 5. کنترل مرکزی

API Server یک نقطه مرکزی برای دسترسی به Kubernetes API ایجاد می‌کند.

---

# ⚠️ اشتباهات رایج

### ❌ اشتباه ۱

`kubectl` مستقیماً با Pod ارتباط دارد.

### ✅ درست

```text
kubectl
   ↓
API Server
```

---

### ❌ اشتباه ۲

Scheduler مستقیماً Pod را روی Node اجرا می‌کند.

### ✅ درست

```text
Scheduler
   ↓
انتخاب Node
   ↓
Worker Node
   ↓
اجرای Pod
```

---

### ❌ اشتباه ۳

هر برنامه‌ای می‌تواند مستقیماً `etcd` را تغییر دهد.

### ✅ درست

```text
Client
   ↓
API Server
   ↓
etcd
```

---

### ❌ اشتباه ۴

Authentication و Authorization یکی هستند.

### ✅ درست

```text
Authentication → تو چه کسی هستی؟

Authorization → چه اجازه‌ای داری؟
```

---

# 📝 خلاصه

* API Server یکی از اجزای اصلی **Control Plane** است.
* API Server دروازه اصلی **Kubernetes API** است.
* Clientها برای کار با Kubernetes با API Server ارتباط برقرار می‌کنند.
* `kubectl` مستقیماً با Pod ارتباط ندارد.
* API Server درخواست‌ها را دریافت و بررسی می‌کند.
* Authentication هویت درخواست‌کننده را بررسی می‌کند.
* Authorization مجوزهای او را بررسی می‌کند.
* Validation اعتبار درخواست را بررسی می‌کند.
* API Server با `etcd` برای ذخیره و بازیابی وضعیت Cluster ارتباط دارد.
* Scheduler تصمیم می‌گیرد Pod روی کدام Worker Node قرار بگیرد.

---

# 🧠 کلمات کلیدی

* API Server
* Kubernetes API
* API
* Client
* `kubectl`
* Authentication
* Authorization
* Validation
* `etcd`
* Request
* Response
* Scheduler

---

# ❓ سؤالات ارزیابی

## سؤالات مفهومی

### ۱. API Server چیست؟

### ۲. چرا API Server یکی از مهم‌ترین اجزای Kubernetes است؟

### ۳. API مخفف چیست؟

### ۴. Kubernetes API چه کاربردی دارد؟

### ۵. آیا `kubectl` مستقیماً با Pod ارتباط برقرار می‌کند؟

### ۶. Authentication چیست؟

### ۷. Authorization چیست؟

### ۸. تفاوت Authentication و Authorization چیست؟

### ۹. Validation در API Server چه کاری انجام می‌دهد؟

### ۱۰. API Server با کدام مؤلفه برای ذخیره وضعیت Cluster ارتباط دارد؟

### ۱۱. چرا Clientها نباید مستقیماً با `etcd` کار کنند؟

---

# 🧩 سؤال سناریویی

فرض کن مدیر سیستم دستور زیر را اجرا می‌کند:

```bash
kubectl apply -f nginx.yaml
```

پاسخ بده:

### ۱. اولین مؤلفه Kubernetes که درخواست را دریافت می‌کند چیست؟

### ۲. API Server چه بررسی‌هایی روی درخواست انجام می‌دهد؟

### ۳. اطلاعات مربوط به وضعیت جدید کجا ذخیره می‌شود؟

### ۴. چه مؤلفه‌ای تصمیم می‌گیرد Pod روی کدام Worker Node قرار بگیرد؟

### ۵. آیا Scheduler خودش Pod را اجرا می‌کند؟

### ۶. Pod در نهایت روی کجا اجرا می‌شود؟

---

# 💡 نکات طلایی این درس

⭐ **API Server دروازه Kubernetes API است.**

⭐ **`kubectl` مستقیماً با Podها ارتباط ندارد.**

⭐ **Client → API Server**

⭐ **Authentication = تو چه کسی هستی؟**

⭐ **Authorization = چه اجازه‌ای داری؟**

⭐ **Validation = آیا درخواست معتبر است؟**

⭐ **etcd دیتاستور اصلی Kubernetes است.**

⭐ **Scheduler انتخاب می‌کند Pod روی کدام Node قرار بگیرد.**

⭐ **Worker Node محل اجرای Pod است.**

---

# 🔗 ارتباط Lesson 2 و Lesson 3

در درس قبل یاد گرفتیم:

```text
Control Plane
     ↓
مدیریت و تصمیم‌گیری

Worker Node
     ↓
اجرای Pod
```

حالا در Lesson 3 یکی از مهم‌ترین اجزای Control Plane را شناختیم:

```text
Control Plane
│
├── API Server   ← دروازه ارتباط
├── Scheduler
├── Controller Manager
└── etcd
```

و در درس بعد می‌رویم سراغ:

# 📖 Chapter 1 — Lesson 4

# 🗄️ etcd — حافظه Kubernetes

آنجا دقیقاً بررسی می‌کنیم که **Kubernetes اطلاعات و وضعیت Cluster را کجا نگه می‌دارد و etcd چه نقشی در این معماری دارد.**

