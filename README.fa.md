# ☸️ Kubernetes Zero to Pro

**آموزش Kubernetes از صفر تا حرفه‌ای**

[🇬🇧 English](README.md) | **🇮🇷 فارسی**

این مخزن شامل یک دوره‌ی **ساختاریافته، عملی و پروژه‌محور** برای یادگیری Kubernetes از مفاهیم پایه تا مباحث پیشرفته و استفاده در محیط‌های واقعی DevOps است.

---

## 🎯 هدف دوره

هدف این دوره این است که درک کاملی از Kubernetes از سطح مقدماتی تا حرفه‌ای ایجاد شود.

در پایان دوره باید بتوانید:

* معماری و مفاهیم اصلی Kubernetes را توضیح دهید.
* Applicationها را روی Kubernetes Deploy و مدیریت کنید.
* با Pod، Deployment، Service و سایر Workloadها کار کنید.
* Configuration و Secretها را مدیریت کنید.
* مفاهیم Networking و Storage در Kubernetes را درک کنید.
* Namespaceها و منابع سیستم را مدیریت کنید.
* Health Check و Auto Scaling را پیاده‌سازی کنید.
* مفاهیم امنیتی Kubernetes را درک کنید.
* Workloadهای Kubernetes را عیب‌یابی کنید.
* Kubernetes را در Workflowهای واقعی DevOps استفاده کنید.
* Applicationها را در محیط‌های واقعی Deploy و مدیریت کنید.

---

## 📚 ساختار دوره

دوره به چند **Chapter** تقسیم شده و هر درس داخل پوشه‌ی مخصوص خودش قرار دارد.

```text
Chapter-01/
├── Lesson-01/
│   ├── README.md
│   └── README.fa.md
├── Lesson-02/
│   ├── README.md
│   └── README.fa.md
└── ...
```

هر درس شامل توضیحات، مثال‌ها، دستورات و تمرین‌های عملی مربوط به همان موضوع است.

---

## 🗂️ فصل‌های دوره

### Chapter 01 — مبانی Kubernetes

آشنایی با Kubernetes، دلیل استفاده از آن، معماری، اجزای اصلی و مفاهیم پایه.

### Chapter 02 — Kubernetes Workloads

بررسی Pod، ReplicaSet، Deployment، Job، CronJob و مدیریت Workloadها.

### Chapter 03 — Networking

بررسی Service، DNS، Networking، Ingress و ارتباط بین Workloadها.

### Chapter 04 — Configuration & Secrets

بررسی ConfigMap، Secret، Environment Variables و مدیریت Configuration.

### Chapter 05 — Storage

بررسی Volume، PersistentVolume، PersistentVolumeClaim و مدیریت Storage.

### Chapter 06 — Scheduling & Resources

بررسی Resource Requests، Limits، Scheduling، Taints، Tolerations و مدیریت Nodeها.

### Chapter 07 — Health & Scaling

بررسی Liveness Probe، Readiness Probe، Startup Probe، HPA و Scaling.

### Chapter 08 — Security

بررسی RBAC، ServiceAccount، Security Context و مفاهیم امنیتی Kubernetes.

### Chapter 09 — Troubleshooting

بررسی Logs، Events، Debugging و عیب‌یابی مشکلات Kubernetes.

### Chapter 10 — Advanced Kubernetes

بررسی مفاهیم و قابلیت‌های پیشرفته موردنیاز برای کار حرفه‌ای با Kubernetes.

### Chapter 11 — Production & DevOps

بررسی استفاده از Kubernetes در محیط Production، CI/CD، Monitoring، Observability و عملیات زیرساخت.

### Chapter 12 — Real-World Projects

پروژه‌های عملی برای ترکیب مفاهیمی که در طول دوره یاد گرفته شده‌اند.

---

## 🧪 روش یادگیری

ساختار هر درس به شکل زیر خواهد بود:

1. **مفهوم** — توضیح ساده‌ی موضوع
2. **تعریف فنی** — تعریف رسمی Kubernetes
3. **معماری** — بررسی نحوه عملکرد Componentها
4. **مثال واقعی** — بررسی کاربرد در زیرساخت واقعی
5. **دستورات** — دستورات مرتبط Linux و Kubernetes
6. **تمرین عملی** — انجام Hands-on Lab
7. **جمع‌بندی** — مرور مفاهیم مهم
8. **سؤالات** — بررسی میزان یادگیری

---

## 🛠️ ابزارها و تکنولوژی‌ها

در این دوره ممکن است از تکنولوژی‌ها و ابزارهای زیر استفاده شود:

* Kubernetes
* Docker / Containerd
* Linux
* kubectl
* YAML
* Git & GitHub
* Helm
* Prometheus
* Grafana
* CI/CD
* Cloud Infrastructure

---

## 📌 پیش‌نیازها

برای شروع دوره نیازی به دانش قبلی Kubernetes ندارید.

مفاهیم از پایه شروع شده و به‌صورت تدریجی وارد مباحث پیشرفته می‌شویم.

آشنایی اولیه با موارد زیر مفید است:

* Linux
* Command Line
* Docker
* Networking
* Git

اما در صورت نیاز، مفاهیم لازم در طول دوره توضیح داده خواهند شد.

---

## 🚀 فلسفه دوره

هدف این دوره فقط **حفظ کردن دستورات Kubernetes** نیست.

هدف اصلی این است که بدانید:

> **Kubernetes چه کاری انجام می‌دهد، چرا این کار را انجام می‌دهد، چگونه کار می‌کند و چگونه باید آن را در یک زیرساخت واقعی مدیریت کرد.**

---

## 📖 مستندات

این Repository با رویکرد **Documentation First** ساخته شده است.

محتوای هر درس در پوشه‌ی مربوط به همان Chapter و Lesson قرار دارد.

هر درس دارای نسخه‌ی انگلیسی و فارسی است.

---

## 👨‍💻 نویسنده

**Saman Qasempour**

حوزه‌های تمرکز:

* DevOps
* Linux
* Kubernetes
* Cloud Infrastructure
* Automation
* Software Engineering

---

## ⭐ وضعیت پروژه

🚧 **در حال توسعه**

فصل‌ها، درس‌ها، تمرین‌ها و پروژه‌های جدید به‌صورت تدریجی به Repository اضافه خواهند شد.

---

## 📜 License

این Repository با هدف آموزش و یادگیری ایجاد شده است.

[🇬🇧 English](README.md) | **🇮🇷 فارسی**
