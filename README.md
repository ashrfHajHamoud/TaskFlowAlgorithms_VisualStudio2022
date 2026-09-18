# TaskFlow Algorithms

مشروع إدارة المهام والمشاريع لمادة **تحليل وتصميم الخوارزميات**، مبني بـ ASP.NET Core MVC ويعمل على Visual Studio 2022 Preview.

## التقنية

- .NET 8 / ASP.NET Core MVC
- Entity Framework Core 8
- SQLite
- Razor Views + CSS
- Session Authentication مبسط للمشروع الأكاديمي

## التشغيل على Visual Studio 2022 Preview

1. ثبّت workload: **ASP.NET and web development**.
2. فك ضغط المشروع وافتح `TaskFlowAlgorithms.sln`.
3. انتظر NuGet Restore. الحزمة الخارجية الوحيدة هي `Microsoft.EntityFrameworkCore.Sqlite`.
4. اختر Profile `https` أو `IIS Express`.
5. شغّل المشروع بـ **F5**.
6. قاعدة البيانات `taskflow.db` تُنشأ تلقائيًا عند أول تشغيل باستخدام `Database.EnsureCreated()`.

> إذا كان لديك إصدار أقدم من .NET 8 SDK، ثبّت .NET 8 SDK من Visual Studio Installer.

## حسابات تجريبية

يتم إنشاء 5 أعضاء تلقائيًا:

- `member1@team.local` / `123456`
- `member2@team.local` / `123456`
- `member3@team.local` / `123456`
- `member4@team.local` / `123456`
- `member5@team.local` / `123456`
- `member5@team.local` / `123456`

يمكن أيضًا تسجيل مستخدم جديد من صفحة التسجيل.

## الوظائف المنفذة

- إنشاء/تعديل/حذف المشاريع.
- إنشاء/تعديل/حذف المهام.
- أولويات: عالية/متوسطة/منخفضة.
- تاريخ تسليم وساعات متوقعة لكل مهمة.
- مهام فرعية متعددة المستويات عبر `ParentTaskId`.
- تعيين المهام لأعضاء الفريق.
- لوحة Kanban بثلاث حالات: جديد، قيد العمل، منتهي.
- Activity Log لكل تغيير حالة، مع المستخدم والتاريخ.
- تقرير نسبة الإنجاز وعدد المهام المنجزة لكل عضو.
- Merge Sort يدوي.
- Quick Sort يدوي.
- ترتيب حسب الأولوية أو تاريخ التسليم.
- عرض زمن التنفيذ بالميلي ثانية لكل خوارزمية.
- Divide & Conquer recursive لحساب إجمالي ساعات المشروع من شجرة المهام.

## أماكن الخوارزميات

- `Services/SortingService.cs`
- `Services/DivideAndConquerService.cs`
- الواجهة: `Views/Algorithms/Sorting.cshtml`
- التقرير: `Views/Reports/Index.cshtml`



## Git Flow المقترح

- `main`: النسخة المستقرة.
- `dev`: تجميع الميزات.
- Feature branches مثل:
  - `feature/projects-tasks`
  - `feature/auth-users`
  - `feature/kanban-activity`
  - `feature/sorting-algorithms`
  - `feature/divide-conquer-report`

كل عضو يفتح Pull Request إلى `dev` ويقوم عضو آخر بعمل Code Review قبل الدمج.

## بنية المشروع

```text
Controllers/       MVC controllers
Data/              EF Core DbContext + initial seed
Filters/           RequireLogin filter
Models/            Project, WorkTask, User, ActivityLog
Services/          Password, Sorting, Divide & Conquer
ViewModels/        Models الخاصة بالواجهات والتقارير
Views/             Razor pages
wwwroot/css/        التصميم
Docs/              تحليل الخوارزميات والتسليم
```

## تنظيف قاعدة البيانات

للبدء من الصفر، أوقف التطبيق واحذف ملف `taskflow.db` ثم شغّل المشروع مرة أخرى.
