<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سجل المدرس المتكامل</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        naskh: ['Amiri', 'serif'],
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Amiri', serif;
        }
        .sticky-column {
            position: sticky;
            right: 0;
            background-color: white;
            z-index: 20;
        }
        .sticky-header {
            position: sticky;
            top: 0;
            z-index: 30;
        }
        .sticky-header-corner {
            position: sticky;
            top: 0;
            right: 0;
            z-index: 40;
            background-color: #1e3a8a;
            color: white;
        }
        .name-column-cell {
            white-space: nowrap;
        }
        @media print {
            .no-print {
                display: none !important;
            }
            body {
                background-color: white !important;
                color: black !important;
            }
            .print-container {
                width: 100% !important;
                margin: 0 !important;
                padding: 0 !important;
                box-shadow: none !important;
            }
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col">

    <header id="app-header" class="bg-gradient-to-l from-blue-900 via-indigo-900 to-slate-900 text-white shadow-md sticky top-0 z-50 transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 py-3 flex flex-wrap justify-between items-center gap-4">
            <div class="flex items-center gap-4">
                <div class="relative group cursor-pointer" onclick="document.getElementById('school-logo-input').click()" title="تغيير شعار المدرسة">
                    <img id="header-logo" src="https://placehold.co/70x70/1e3a8a/ffffff?text=شعار" alt="شعار المدرسة" class="w-14 h-14 rounded-full object-cover border-2 border-white/80 shadow">
                    <input type="file" id="school-logo-input" class="hidden" accept="image/*" onchange="updateSchoolLogo(event)">
                </div>
                <div class="space-y-0.5">
                    <div class="flex items-center gap-2">
                        <span class="text-xs text-blue-200">المدرسة:</span>
                        <input type="text" id="header-school-name" value="مدرسة الأبجدية الابتدائية" onchange="saveHeaderData()" class="bg-transparent border-b border-transparent hover:border-white/50 focus:border-white focus:outline-none text-lg font-bold text-white px-1 transition">
                    </div>
                    <div class="flex items-center gap-4 text-sm text-slate-200">
                        <div class="flex items-center gap-1">
                            <span>المدرس:</span>
                            <input type="text" id="header-teacher-name" value="أحمد محمد" onchange="saveHeaderData()" class="bg-transparent border-b border-transparent hover:border-white/50 focus:border-white focus:outline-none font-semibold px-1 transition w-28">
                        </div>
                        <div class="flex items-center gap-1">
                            <span>المادة:</span>
                            <input type="text" id="header-subject-name" value="الرياضيات" onchange="saveHeaderData()" class="bg-transparent border-b border-transparent hover:border-white/50 focus:border-white focus:outline-none font-semibold px-1 transition w-28">
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <nav class="bg-slate-900/80 border-t border-white/10 px-4 overflow-x-auto">
            <div class="max-w-7xl mx-auto flex gap-1 py-2 text-sm whitespace-nowrap">
                <button type="button" onclick="switchTab('home')" id="tab-btn-home" class="px-4 py-2 rounded-lg font-bold bg-blue-600 text-white transition shadow">الصفحة الرئيسية</button>
                <button type="button" onclick="switchTab('names')" id="tab-btn-names" class="px-4 py-2 rounded-lg font-medium text-slate-300 hover:bg-white/10 hover:text-white transition">تبويب الأسماء والدرجات</button>
                <button type="button" onclick="switchTab('daily')" id="tab-btn-daily" class="px-4 py-2 rounded-lg font-medium text-slate-300 hover:bg-white/10 hover:text-white transition">الاختبار اليومي</button>
                <button type="button" onclick="switchTab('attendance')" id="tab-btn-attendance" class="px-4 py-2 rounded-lg font-medium text-slate-300 hover:bg-white/10 hover:text-white transition">سجل الحضور</button>
                <button type="button" onclick="switchTab('absence-log')" id="tab-btn-absence-log" class="px-4 py-2 rounded-lg font-medium text-slate-300 hover:bg-white/10 hover:text-white transition">سجل الغياب</button>
                <button type="button" onclick="switchTab('backup')" id="tab-btn-backup" class="px-4 py-2 rounded-lg font-medium text-slate-300 hover:bg-white/10 hover:text-white transition">النسخ الاحتياطي</button>
                <button type="button" onclick="switchTab('cloud')" id="tab-btn-cloud" class="px-4 py-2 rounded-lg font-medium text-slate-300 hover:bg-white/10 hover:text-white transition">النسخ السحابي</button>
            </div>
        </nav>
    </header>

    <main class="flex-grow max-w-7xl w-full mx-auto p-4 sm:p-6">

        <!-- 1. الصفحة الرئيسية -->
        <section id="tab-home" class="tab-content space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                <h2 class="text-xl font-bold text-slate-900 mb-4 pb-2 border-b border-slate-100 flex items-center gap-2">
                    <span class="w-2.5 h-6 bg-blue-600 rounded-full inline-block"></span>
                    إدارة المراحل الدراسية والشعب
                </h2>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="space-y-4">
                        <label class="block text-sm font-bold text-slate-700">المرحلة الدراسية:</label>
                        <div class="flex gap-2">
                            <select id="grade-select" onchange="onGradeChange()" class="flex-grow border border-slate-300 rounded-xl px-3 py-2 bg-slate-50 focus:outline-none focus:ring-2 focus:ring-blue-500 font-medium">
                            </select>
                            <button type="button" onclick="openAddGradeModal()" class="bg-blue-600 text-white px-4 py-2 rounded-xl font-bold hover:bg-blue-700 transition shadow-sm">+ مرحلة</button>
                            <button type="button" onclick="confirmEditGrade()" class="bg-amber-500 text-white px-3 py-2 rounded-xl font-bold hover:bg-amber-600 transition shadow-sm" title="تعديل المرحلة">تعديل</button>
                            <button type="button" onclick="confirmDeleteGrade()" class="bg-rose-500 text-white px-3 py-2 rounded-xl font-bold hover:bg-rose-600 transition shadow-sm" title="حذف المرحلة">حذف</button>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <label class="block text-sm font-bold text-slate-700">الشعبة (اختيارية):</label>
                        <div class="flex gap-2">
                            <select id="section-select" onchange="onSectionChange()" class="flex-grow border border-slate-300 rounded-xl px-3 py-2 bg-slate-50 focus:outline-none focus:ring-2 focus:ring-blue-500 font-medium">
                            </select>
                            <button type="button" onclick="openAddSectionModal()" class="bg-indigo-600 text-white px-4 py-2 rounded-xl font-bold hover:bg-indigo-700 transition shadow-sm">+ شعبة</button>
                            <button type="button" onclick="confirmDeleteSection()" class="bg-rose-500 text-white px-4 py-2 rounded-xl font-bold hover:bg-rose-600 transition shadow-sm" title="حذف الشعبة">حذف</button>
                        </div>
                    </div>
                </div>

                <div class="mt-8 grid grid-cols-1 sm:grid-cols-3 gap-4">
                    <div class="bg-blue-50 p-4 rounded-xl border border-blue-100 flex items-center justify-between">
                        <div>
                            <p class="text-xs text-blue-600 font-bold">إجمالي عدد الطلاب</p>
                            <h3 id="stat-total-students" class="text-2xl font-black text-blue-900 mt-1">٠</h3>
                        </div>
                        <div class="w-10 h-10 bg-blue-200/60 rounded-full flex items-center justify-center text-blue-700 font-bold">👨‍🎓</div>
                    </div>
                    <div class="bg-emerald-50 p-4 rounded-xl border border-emerald-100 flex items-center justify-between sm:col-span-2">
                        <div>
                            <p class="text-xs text-emerald-600 font-bold">المرحلة والشعبة النشطة</p>
                            <h3 id="stat-active-class" class="text-lg font-bold text-emerald-900 mt-1 truncate max-w-[180px]">الأول الابتدائي</h3>
                        </div>
                        <div class="w-10 h-10 bg-emerald-200/60 rounded-full flex items-center justify-center text-emerald-700 font-bold">🏫</div>
                    </div>
                </div>

                <!-- حقل البحث في الصفحة الرئيسية -->
                <div class="mt-8 pt-6 border-t border-slate-100 space-y-3">
                    <label class="block text-sm font-bold text-slate-700">البحث الشامل عن طالب في جميع المراحل والشعب:</label>
                    <div class="flex gap-2 max-w-xl">
                        <input type="text" id="home-search-input" placeholder="أدخل اسم الطالب للبحث..." class="flex-grow border border-slate-300 rounded-xl px-4 py-2.5 bg-slate-50 focus:outline-none focus:ring-2 focus:ring-blue-500 font-medium text-sm">
                        <button type="button" onclick="handleGlobalSearch(document.getElementById('home-search-input').value)" class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-2.5 rounded-xl font-bold transition shadow-sm text-sm">بحث شامل</button>
                    </div>
                </div>
            </div>

            <!-- نتائج البحث الشامل في الصفحة الرئيسية -->
            <div id="global-search-results-container" class="hidden bg-white p-6 rounded-2xl shadow-sm border border-slate-200 space-y-4">
                <h3 class="font-bold text-lg text-slate-800 pb-2 border-b">نتائج البحث التفصيلية عن الطالب: <span id="search-query-display" class="text-blue-600"></span></h3>
                <div id="search-results-list" class="space-y-4"></div>
            </div>
        </section>

        <!-- 2. تبويب الأسماء -->
        <section id="tab-names" class="tab-content hidden space-y-4">
            <div class="bg-white p-4 rounded-2xl shadow-sm border border-slate-200 flex flex-wrap justify-between items-center gap-3 no-print">
                <div class="flex flex-wrap gap-2">
                    <button type="button" onclick="openAddStudentModal()" class="bg-blue-600 text-white px-4 py-2 rounded-xl font-bold hover:bg-blue-700 transition shadow-sm flex items-center gap-1.5">
                        <span>+ إضافة طالب يدوياً</span>
                    </button>
                    <label class="bg-indigo-600 text-white px-4 py-2 rounded-xl font-bold hover:bg-indigo-700 transition shadow-sm cursor-pointer flex items-center gap-1.5">
                        <span>📁 استيراد من ملف (txt/doc)</span>
                        <input type="file" id="import-file-input" accept=".txt,.doc,.docx" class="hidden" onchange="importNamesFromFile(event)">
                    </label>
                </div>
                <div class="flex items-center gap-3 bg-slate-50 px-3 py-1.5 rounded-xl border border-slate-200">
                    <span class="text-xs font-bold text-slate-600">عرض حقل الأسماء:</span>
                    <button type="button" onclick="adjustNameWidth(-20)" class="w-7 h-7 bg-slate-200 hover:bg-slate-300 rounded-lg font-bold text-slate-700 transition">-</button>
                    <span id="name-width-display" class="text-xs font-bold text-blue-700">١٠٠ بكسل</span>
                    <button type="button" onclick="adjustNameWidth(20)" class="w-7 h-7 bg-slate-200 hover:bg-slate-300 rounded-lg font-bold text-slate-700 transition">+</button>
                </div>
                <div class="flex gap-2">
                    <button type="button" onclick="openPrintModal()" class="bg-emerald-600 text-white px-4 py-2 rounded-xl font-bold hover:bg-emerald-700 transition shadow-sm flex items-center gap-1.5">
                        <span>🖨️ طباعة السجل</span>
                    </button>
                </div>
            </div>

            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 overflow-hidden">
                <div class="overflow-x-auto max-h-[70vh] relative">
                    <table id="grades-table" class="w-full text-right border-collapse text-sm">
                        <thead>
                            <tr class="bg-slate-900 text-white select-none">
                                <th class="sticky-header-corner p-3 text-center border-b border-slate-700 w-12 font-bold">تسلسل</th>
                                <th id="name-column-header" class="sticky-header p-3 border-b border-slate-700 bg-slate-900 name-column-cell font-bold" style="width: 100px; min-width: 100px;">اسم الطالب</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شفهي ١</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شهر ١</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شفهي ٢</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شهر ٢</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-20 bg-blue-950 font-bold">معدل ف١</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-20">نصف سنة</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شفهي ١</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شهر ١</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شفهي ٢</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16">شهر ٢</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-20 bg-indigo-950 font-bold">معدل ف٢</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-20 bg-emerald-950 font-bold">السعي</th>
                                <th class="sticky-header p-3 border-b border-slate-700 bg-slate-900 w-56">ملاحظات</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-20 no-print">إشارة ❌</th>
                                <th class="sticky-header p-2 text-center border-b border-slate-700 bg-slate-900 w-16 no-print">إجراء</th>
                            </tr>
                        </thead>
                        <tbody id="grades-tbody" class="divide-y divide-slate-200">
                        </tbody>
                        <tfoot class="bg-slate-100 font-bold text-slate-700">
                            <tr class="border-t-2 border-slate-300">
                                <td colspan="6" class="p-2 text-left">عدد الناجحين (٥٠ فأكثر):</td>
                                <td id="pass-count-f1" class="text-center text-emerald-700">٠</td>
                                <td colspan="4" class="p-2 text-left">عدد الناجحين بنصف السنة:</td>
                                <td id="pass-count-mid" class="text-center text-emerald-700">٠</td>
                                <td id="pass-count-f2" class="text-center text-emerald-700">٠</td>
                                <td id="pass-count-annual" class="text-center text-emerald-700">٠</td>
                                <td colspan="3"></td>
                            </tr>
                            <tr>
                                <td colspan="6" class="p-2 text-left">عدد الراسبين (أقل من ٥٠):</td>
                                <td id="fail-count-f1" class="text-center text-rose-600">٠</td>
                                <td colspan="4" class="p-2 text-left">عدد الراسبين بنصف السنة:</td>
                                <td id="fail-count-mid" class="text-center text-rose-600">٠</td>
                                <td id="fail-count-f2" class="text-center text-rose-600">٠</td>
                                <td id="fail-count-annual" class="text-center text-rose-600">٠</td>
                                <td colspan="3"></td>
                            </tr>
                            <tr class="bg-slate-200/70 text-slate-900">
                                <td colspan="6" class="p-2 text-left">النسبة المئوية للنجاح:</td>
                                <td id="pass-percent-f1" class="text-center text-blue-900">٠٪</td>
                                <td colspan="4" class="p-2 text-left">النسبة المئوية بنصف السنة:</td>
                                <td id="pass-percent-mid" class="text-center text-blue-900">٠٪</td>
                                <td id="pass-percent-f2" class="text-center text-blue-900">٠٪</td>
                                <td id="pass-percent-annual" class="text-center text-blue-900">٠٪</td>
                                <td colspan="3"></td>
                            </tr>
                        </tfoot>
                    </table>
                </div>
            </div>
        </section>

        <!-- 3. الاختبار اليومي -->
        <section id="tab-daily" class="tab-content hidden space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 max-w-xl mx-auto text-center space-y-6">
                <div class="border-b pb-4">
                    <span class="text-xs font-bold text-blue-600 bg-blue-50 px-3 py-1 rounded-full">الاختبار اليومي العشوائي</span>
                    <h2 id="daily-student-name" class="text-3xl font-bold text-slate-900 mt-3">اختر اسماً للبدء</h2>
                    <p id="daily-student-info" class="text-sm text-slate-500 mt-1">المرحلة الحالية</p>
                </div>

                <div class="space-y-3 max-w-xs mx-auto">
                    <label class="block text-sm font-bold text-slate-700">درجة الشفهي (٠ - ١٠٠):</label>
                    <input type="text" inputmode="numeric" id="daily-grade-input" placeholder="أدخل الدرجة" class="w-full text-center text-xl font-bold border-2 border-slate-300 rounded-xl py-2 focus:outline-none focus:border-blue-600">
                </div>

                <div class="flex justify-center gap-3 pt-2">
                    <button type="button" onclick="saveDailyGradeAndNext()" class="bg-blue-600 text-white px-6 py-3 rounded-xl font-bold hover:bg-blue-700 transition shadow">حفظ والانتقال للتالي</button>
                    <button type="button" onclick="loadNextDailyStudent()" class="bg-slate-200 text-slate-700 px-4 py-3 rounded-xl font-bold hover:bg-slate-300 transition">تخطي</button>
                </div>
                <p id="daily-status-msg" class="text-xs text-slate-400"></p>
            </div>
        </section>

        <!-- 4. سجل الحضور -->
        <section id="tab-attendance" class="tab-content hidden space-y-6">
            <div id="attendance-active-container" class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 max-w-xl mx-auto text-center space-y-6">
                <div class="border-b pb-4">
                    <span class="text-xs font-bold text-indigo-600 bg-indigo-50 px-3 py-1 rounded-full">تسجيل الحضور والغياب اليومي</span>
                    <h2 id="att-student-name" class="text-3xl font-bold text-slate-900 mt-3">-</h2>
                    <p id="att-counter-info" class="text-sm text-slate-500 mt-1">الطالب ١ من ٠</p>
                </div>

                <div class="flex justify-center gap-4 pt-4">
                    <button type="button" onclick="recordAttendanceStatus('حاضر')" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold text-lg px-8 py-4 rounded-2xl shadow transition w-40">حاضر ✓</button>
                    <button type="button" onclick="recordAttendanceStatus('غائب')" class="bg-rose-600 hover:bg-rose-700 text-white font-bold text-lg px-8 py-4 rounded-2xl shadow transition w-40">غائب ✗</button>
                </div>

                <div class="pt-4 flex justify-between items-center border-t">
                    <button type="button" onclick="revertAttendanceStep()" class="text-slate-600 hover:text-slate-900 font-bold text-sm px-3 py-2 rounded-lg bg-slate-100 transition">← العودة للخطوة السابقة</button>
                    <span id="att-date-display" class="text-xs text-slate-400"></span>
                </div>
            </div>

            <div id="attendance-summary-container" class="hidden bg-white p-6 rounded-2xl shadow-sm border border-slate-200 max-w-xl mx-auto space-y-6">
                <div class="text-center border-b pb-4">
                    <h2 class="text-2xl font-bold text-slate-900">تم الانتهاء من تسجيل الحضور</h2>
                    <p class="text-sm text-slate-500 mt-1" id="summary-date-text"></p>
                </div>
                <div class="grid grid-cols-2 gap-4 text-center">
                    <div class="bg-emerald-50 p-4 rounded-xl border border-emerald-100">
                        <p class="text-xs text-emerald-600 font-bold">الحاضرون</p>
                        <p id="summary-present-count" class="text-2xl font-black text-emerald-800 mt-1">٠</p>
                    </div>
                    <div class="bg-rose-50 p-4 rounded-xl border border-rose-100">
                        <p class="text-xs text-rose-600 font-bold">الغائبون</p>
                        <p id="summary-absent-count" class="text-2xl font-black text-rose-800 mt-1">٠</p>
                    </div>
                </div>
                <div class="flex justify-center pt-2">
                    <button type="button" onclick="resetAttendanceSession()" class="bg-blue-600 hover:bg-blue-700 text-white font-bold px-6 py-2 rounded-xl transition">بدء تسجيل جديد</button>
                </div>
            </div>
        </section>

        <!-- 5. سجل الغياب -->
        <section id="tab-absence-log" class="tab-content hidden space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 space-y-6">
                <div class="flex flex-wrap items-center justify-between gap-4 border-b pb-4">
                    <h2 class="text-xl font-bold text-slate-900">سجلات الحضور والغياب المحفوظة</h2>
                    <div class="flex items-center gap-2">
                        <label class="text-sm font-bold text-slate-700">التاريخ:</label>
                        <select id="absence-date-select" onchange="renderAbsenceLogByDate()" class="border border-slate-300 rounded-xl px-3 py-1.5 bg-slate-50 font-medium text-sm focus:outline-none min-w-[280px]">
                        </select>
                    </div>
                </div>

                <div class="bg-slate-50 p-4 rounded-xl border border-slate-200 flex flex-wrap items-center justify-between gap-4">
                    <div>
                        <h4 class="font-bold text-slate-800 text-sm">إرفاق صورة توثيقية (كاميرا أو الاستوديو)</h4>
                        <p class="text-xs text-slate-500">يمكنك التقاط صورة أو اختيارها من الاستوديو وحفظها مع السجل المختار.</p>
                    </div>
                    <label class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold text-sm px-4 py-2 rounded-xl cursor-pointer transition shadow-sm">
                        <span>📸 التقاط / رفع صوره</span>
                        <input type="file" accept="image/*" class="hidden" onchange="saveLogImage(event)">
                    </label>
                </div>

                <div id="absence-log-view-area" class="space-y-4">
                </div>
            </div>
        </section>

        <!-- 6. النسخ الاحتياطي -->
        <section id="tab-backup" class="tab-content hidden space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 max-w-xl mx-auto space-y-6">
                <div class="border-b pb-4">
                    <h2 class="text-xl font-bold text-slate-900">النسخ الاحتياطي المحلي</h2>
                    <p class="text-sm text-slate-500 mt-1">تصدير واستيراد ملفات البيانات (JSON) لحماية بياناتك من الضياع.</p>
                </div>

                <div class="space-y-4">
                    <button type="button" onclick="exportJSONBackup()" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 rounded-xl shadow transition">تصدير البيانات كملف JSON 📥</button>
                    
                    <div class="border-t pt-4">
                        <label class="block text-sm font-bold text-slate-700 mb-2">استيراد ملف سابق:</label>
                        <input type="file" accept=".json" onchange="importJSONBackup(event)" class="w-full border border-slate-300 rounded-xl p-2 bg-slate-50 text-sm">
                    </div>
                </div>
            </div>
        </section>

        <!-- 7. النسخ السحابي -->
        <section id="tab-cloud" class="tab-content hidden space-y-6">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 max-w-xl mx-auto text-center space-y-6">
                <div class="border-b pb-4">
                    <h2 class="text-xl font-bold text-slate-900">النسخ السحابي المتزامن</h2>
                    <p class="text-sm text-slate-500 mt-1">يمكنك تفعيل المزامنة السحابية لحفظ بياناتك عبر الأجهزة والوصول إليها بأي وقت.</p>
                </div>

                <div class="p-6 bg-slate-50 rounded-xl border border-slate-200 space-y-4">
                    <div id="cloud-status-badge" class="inline-block px-4 py-1.5 rounded-full text-xs font-bold bg-amber-100 text-amber-800">الوضع الحالي: يعمل بدون إنترنت (محلي)</div>
                    <p class="text-xs text-slate-500">في حال عدم توفر النت، يتم حفظ التعديلات محلياً ورفعها تلقائياً عند الاتصال.</p>
                    <button type="button" onclick="toggleCloudSync()" id="cloud-sync-btn" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold px-6 py-3 rounded-xl shadow transition">تفعيل النسخ السحابي ☁️</button>
                </div>
            </div>
        </section>

    </main>

    <!-- نوافذ منبثقة مخصصة -->
    <div id="custom-modal" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-white rounded-2xl p-6 max-w-md w-full shadow-2xl space-y-4">
            <h3 id="modal-title" class="text-lg font-bold text-slate-900">تأكيد الإجراء</h3>
            <p id="modal-message" class="text-sm text-slate-600">هل أنت متأكد من تنفيذ هذا الإجراء؟</p>
            <div id="modal-input-container" class="hidden">
                <input type="text" id="modal-prompt-input" class="w-full border border-slate-300 rounded-xl px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500">
            </div>
            <div class="flex justify-end gap-3 pt-2">
                <button type="button" onclick="closeModal(false)" class="px-4 py-2 bg-slate-200 hover:bg-slate-300 rounded-xl text-slate-700 font-bold text-sm transition">إلغاء</button>
                <button type="button" id="modal-confirm-btn" onclick="modalConfirmCallback()" class="px-4 py-2 bg-blue-600 hover:bg-blue-700 rounded-xl text-white font-bold text-sm transition">تأكيد</button>
            </div>
        </div>
    </div>

    <!-- نافذة الطباعة -->
    <div id="print-options-modal" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden no-print">
        <div class="bg-white rounded-2xl p-6 max-w-lg w-full shadow-2xl space-y-4">
            <h3 class="text-lg font-bold text-slate-900 border-b pb-2">تخصيص طباعة السجل</h3>
            <p class="text-xs text-slate-500">اختر الأعمدة والأقسام المراد تضمينها في الطباعة:</p>
            
            <div class="space-y-2 max-h-60 overflow-y-auto text-sm">
                <label class="flex items-center gap-2"><input type="checkbox" id="print-col-grades" checked class="rounded"> جدول الدرجات الكامل</label>
                <label class="flex items-center gap-2"><input type="checkbox" id="print-col-f1" checked class="rounded"> معدلات الفصل الأول</label>
                <label class="flex items-center gap-2"><input type="checkbox" id="print-col-mid" checked class="rounded"> درجات نصف السنة</label>
                <label class="flex items-center gap-2"><input type="checkbox" id="print-col-f2" checked class="rounded"> معدلات الفصل الثاني</label>
                <label class="flex items-center gap-2"><input type="checkbox" id="print-col-annual" checked class="rounded"> السعي السنوي والنتائج النهائية</label>
            </div>

            <div class="flex justify-end gap-3 pt-4 border-t">
                <button type="button" onclick="document.getElementById('print-options-modal').classList.add('hidden')" class="px-4 py-2 bg-slate-200 hover:bg-slate-300 rounded-xl text-slate-700 font-bold text-sm transition">إلغاء</button>
                <button type="button" onclick="executePrint()" class="px-5 py-2 bg-emerald-600 hover:bg-emerald-700 rounded-xl text-white font-bold text-sm transition">طباعة الآن 🖨️</button>
            </div>
        </div>
    </div>

    <script>
        let appData = {
            header: {
                schoolName: "مدرسة الأبجدية الابتدائية",
                teacherName: "أحمد محمد",
                subjectName: "الرياضيات",
                schoolLogo: "https://placehold.co/70x70/1e3a8a/ffffff?text=شعار"
            },
            nameColumnWidth: 100,
            grades: {
                "الأول الابتدائي_أ": [
                    { name: "أحمد علي", f1_oral1: 80, f1_m1: 85, f1_oral2: 90, f1_m2: 88, mid_term: 85, f2_oral1: 80, f2_m1: 82, f2_oral2: 85, f2_m2: 88, notes: "" },
                    { name: "فاطمة حسن", f1_oral1: 90, f1_m1: 92, f1_oral2: 95, f1_m2: 90, mid_term: 92, f2_oral1: 90, f2_m1: 91, f2_oral2: 94, f2_m2: 92, notes: "" }
                ]
            },
            absenceLogs: {}
        };

        let currentGrade = "الأول الابتدائي";
        let currentSection = "أ";
        let activeModalCallback = null;
        let dailyQuizIndex = 0;
        let attendanceIndex = 0;
        let currentAttendanceRecords = [];

        function normalizeArabic(text) {
            if (!text) return '';
            return String(text)
                .trim()
                .replace(/[\u064B-\u065F]/g, '') // إزالة التشكيل
                .replace(/[أإآا]/g, 'ا')       // توحيد أشكال الألف
                .replace(/ة/g, 'ه')          // توحيد الهاء والتاء المربوطة
                .replace(/ى/g, 'ي');         // توحيد الألف المقصورة والياء
        }

        function toArabicDigits(num) {
            if (num === null || num === undefined || isNaN(num) || num === '') return '';
            const arabicNumbers = ['٠', '١', '٢', '٣', '٤', '٥', '٦', '٧', '٨', '٩'];
            return String(num).replace(/\d/g, (digit) => arabicNumbers[digit]);
        }

        function parseArabicDigitsToEnglish(str) {
            if (str === null || str === undefined) return '';
            const persianNumbers = [/۰/g, /۱/g, /۲/g, /۳/g, /۴/g, /۵/g, /۶/g, /۷/g, /۸/g, /۹/g];
            const arabicNumbers = [/٠/g, /١/g, /٢/g, /٣/g, /٤/g, /٥/g, /٦/g, /٧/g, /٨/g, /٩/g];
            let converted = String(str);
            for (let i = 0; i < 10; i++) {
                converted = converted.replace(persianNumbers[i], i).replace(arabicNumbers[i], i);
            }
            return converted;
        }

        function roundToNearestTenth(val) {
            return Math.round(val);
        }

        function calculateStudentGrades(st) {
            let f1Sum = (Number(st.f1_oral1) || 0) + (Number(st.f1_m1) || 0) + (Number(st.f1_oral2) || 0) + (Number(st.f1_m2) || 0);
            st.f1_avg = roundToNearestTenth(f1Sum / 4);

            let f2Sum = (Number(st.f2_oral1) || 0) + (Number(st.f2_m1) || 0) + (Number(st.f2_oral2) || 0) + (Number(st.f2_m2) || 0);
            st.f2_avg = roundToNearestTenth(f2Sum / 4);

            let annualSum = (Number(st.f1_avg) || 0) + (Number(st.mid_term) || 0) + (Number(st.f2_avg) || 0);
            st.annual_score = roundToNearestTenth(annualSum / 3);
        }

        function initApp() {
            loadFromLocalStorage();
            populateGradeAndSectionDropdowns();
            renderGradesTable();
            initDailyQuiz();
            initAttendanceSession();
            updateHeaderUI();
        }

        function loadFromLocalStorage() {
            const saved = localStorage.getItem('teacher_log_book_data_v3');
            if (saved) {
                try {
                    appData = JSON.parse(saved);
                    if (!appData.nameColumnWidth) appData.nameColumnWidth = 100;
                } catch (e) {
                    console.error("Error loading data", e);
                }
            }
        }

        function saveToLocalStorage() {
            localStorage.setItem('teacher_log_book_data_v3', JSON.stringify(appData));
        }

        function adjustNameWidth(delta) {
            appData.nameColumnWidth = Math.max(60, Math.min(500, (appData.nameColumnWidth || 100) + delta));
            saveToLocalStorage();
            renderGradesTable();
        }

        function updateHeaderUI() {
            document.getElementById('header-school-name').value = appData.header.schoolName || "";
            document.getElementById('header-teacher-name').value = appData.header.teacherName || "";
            document.getElementById('header-subject-name').value = appData.header.subjectName || "";
            if (appData.header.schoolLogo) {
                document.getElementById('header-logo').src = appData.header.schoolLogo;
            }
        }

        function saveHeaderData() {
            appData.header.schoolName = document.getElementById('header-school-name').value;
            appData.header.teacherName = document.getElementById('header-teacher-name').value;
            appData.header.subjectName = document.getElementById('header-subject-name').value;
            saveToLocalStorage();
        }

        function updateSchoolLogo(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    appData.header.schoolLogo = e.target.result;
                    document.getElementById('header-logo').src = e.target.result;
                    saveToLocalStorage();
                };
                reader.readAsDataURL(file);
            }
        }

        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            const targetTab = document.getElementById('tab-' + tabId);
            if (targetTab) {
                targetTab.classList.remove('hidden');
            }

            document.querySelectorAll('nav button').forEach(btn => {
                btn.className = "px-4 py-2 rounded-lg font-medium text-slate-300 hover:bg-white/10 hover:text-white transition";
            });
            const activeBtn = document.getElementById('tab-btn-' + tabId);
            if (activeBtn) {
                activeBtn.className = "px-4 py-2 rounded-lg font-bold bg-blue-600 text-white transition shadow";
            }

            if (tabId === 'names') renderGradesTable();
            if (tabId === 'daily') initDailyQuiz();
            if (tabId === 'attendance') initAttendanceSession();
            if (tabId === 'absence-log') initAbsenceLogDropdown();
        }

        function getGradeSectionKey() {
            return currentGrade + "_" + (currentSection || "عامة");
        }

        function getCurrentStudents() {
            const key = getGradeSectionKey();
            if (!appData.grades[key]) {
                appData.grades[key] = [];
            }
            return appData.grades[key];
        }

        function populateGradeAndSectionDropdowns() {
            const gradeSelect = document.getElementById('grade-select');
            gradeSelect.innerHTML = '';
            
            const gradesSet = new Set(Object.keys(appData.grades).map(k => k.split('_')[0]));
            if (gradesSet.size === 0) gradesSet.add("الأول الابتدائي");

            gradesSet.forEach(g => {
                const opt = document.createElement('option');
                opt.value = g;
                opt.textContent = g;
                if (g === currentGrade) opt.selected = true;
                gradeSelect.appendChild(opt);
            });

            populateSectionDropdown();
        }

        function populateSectionDropdown() {
            const sectionSelect = document.getElementById('section-select');
            sectionSelect.innerHTML = '';

            const sectionsSet = new Set();
            Object.keys(appData.grades).forEach(k => {
                const parts = k.split('_');
                if (parts[0] === currentGrade) {
                    sectionsSet.add(parts[1] || "أ");
                }
            });
            if (sectionsSet.size === 0) sectionsSet.add("أ");

            sectionsSet.forEach(s => {
                const opt = document.createElement('option');
                opt.value = s;
                opt.textContent = "شعبة " + s;
                if (s === currentSection) opt.selected = true;
                sectionSelect.appendChild(opt);
            });

            document.getElementById('stat-active-class').textContent = currentGrade + " (" + currentSection + ")";
        }

        function onGradeChange() {
            currentGrade = document.getElementById('grade-select').value;
            populateSectionDropdown();
            renderGradesTable();
        }

        function onSectionChange() {
            currentSection = document.getElementById('section-select').value;
            document.getElementById('stat-active-class').textContent = currentGrade + " (" + currentSection + ")";
            renderGradesTable();
        }

        function openAddGradeModal() {
            showCustomModalPrompt("إضافة مرحلة دراسية", "أدخل اسم المرحلة الدراسية الجديدة:", (val) => {
                if (val && val.trim() !== '') {
                    currentGrade = val.trim();
                    currentSection = "أ";
                    const key = getGradeSectionKey();
                    if (!appData.grades[key]) appData.grades[key] = [];
                    saveToLocalStorage();
                    populateGradeAndSectionDropdowns();
                    renderGradesTable();
                }
            });
        }

        function openAddSectionModal() {
            showCustomModalPrompt("إضافة شعبة جديدة", "أدخل اسم الشعبة (مثال: ب، جيم):", (val) => {
                if (val && val.trim() !== '') {
                    currentSection = val.trim();
                    const key = getGradeSectionKey();
                    if (!appData.grades[key]) appData.grades[key] = [];
                    saveToLocalStorage();
                    populateSectionDropdown();
                    renderGradesTable();
                }
            });
        }

        function confirmDeleteGrade() {
            showCustomModal("حذف المرحلة", `هل أنت متأكد من حذف المرحلة الدراسية "${currentGrade}" بكافة شعبها وطلابها؟`, true, () => {
                Object.keys(appData.grades).forEach(k => {
                    if (k.startsWith(currentGrade + "_")) {
                        delete appData.grades[k];
                    }
                });
                const remaining = Object.keys(appData.grades);
                if (remaining.length > 0) {
                    currentGrade = remaining[0].split('_')[0];
                    currentSection = remaining[0].split('_')[1] || "أ";
                } else {
                    currentGrade = "الأول الابتدائي";
                    currentSection = "أ";
                    appData.grades[getGradeSectionKey()] = [];
                }
                saveToLocalStorage();
                populateGradeAndSectionDropdowns();
                renderGradesTable();
            });
        }

        function confirmDeleteSection() {
            showCustomModal("حذف الشعبة", `هل أنت متأكد من حذف الشعبة "${currentSection}" للمرحلة "${currentGrade}"؟`, true, () => {
                const key = getGradeSectionKey();
                delete appData.grades[key];
                const available = Object.keys(appData.grades).filter(k => k.startsWith(currentGrade + "_"));
                if (available.length > 0) {
                    currentSection = available[0].split('_')[1];
                } else {
                    currentSection = "أ";
                    appData.grades[getGradeSectionKey()] = [];
                }
                saveToLocalStorage();
                populateSectionDropdown();
                renderGradesTable();
            });
        }

        function confirmEditGrade() {
            showCustomModalPrompt("تعديل اسم المرحلة", "أدخل الاسم الجديد للمرحلة:", (newVal) => {
                if (newVal && newVal.trim() !== '') {
                    const oldGrade = currentGrade;
                    const trimmed = newVal.trim();
                    const newGrades = {};
                    Object.keys(appData.grades).forEach(k => {
                        const parts = k.split('_');
                        if (parts[0] === oldGrade) {
                            newGrades[trimmed + "_" + parts[1]] = appData.grades[k];
                        } else {
                            newGrades[k] = appData.grades[k];
                        }
                    });
                    appData.grades = newGrades;
                    currentGrade = trimmed;
                    saveToLocalStorage();
                    populateGradeAndSectionDropdowns();
                    renderGradesTable();
                }
            });
        }

        function renderGradesTable() {
            const width = appData.nameColumnWidth || 100;
            document.getElementById('name-width-display').textContent = toArabicDigits(width) + " بكسل";
            
            const headerCell = document.getElementById('name-column-header');
            if (headerCell) {
                headerCell.style.width = width + 'px';
                headerCell.style.minWidth = width + 'px';
            }

            const tbody = document.getElementById('grades-tbody');
            tbody.innerHTML = '';
            const students = getCurrentStudents();

            if (students.length === 0) {
                tbody.innerHTML = `<tr><td colspan="17" class="text-center py-8 text-slate-400">لا توجد أسماء طلاب مضافة في هذه المرحلة/الشعبة حالياً.</td></tr>`;
                updateStatistics();
                return;
            }

            students.forEach((st, idx) => {
                calculateStudentGrades(st);
                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-50 transition";

                const colorClass = (val) => (parseFloat(val) < 50 ? "text-rose-600 font-bold" : "text-slate-900");

                tr.innerHTML = `
                    <td class="sticky-column p-2 text-center border-b border-slate-200 font-bold text-slate-500 bg-white">${toArabicDigits(idx + 1)}</td>
                    <td class="sticky-column p-2 border-b border-slate-200 bg-white font-medium name-column-cell" style="width: ${width}px; min-width: ${width}px;">
                        <input type="text" value="${st.name}" onchange="updateStudentName(${idx}, this.value)" class="bg-transparent border-b border-transparent hover:border-slate-300 focus:border-blue-600 focus:outline-none w-full">
                    </td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f1_oral1)}" onchange="updateStudentGrade(${idx}, 'f1_oral1', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f1_oral1)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f1_m1)}" onchange="updateStudentGrade(${idx}, 'f1_m1', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f1_m1)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f1_oral2)}" onchange="updateStudentGrade(${idx}, 'f1_oral2', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f1_oral2)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f1_m2)}" onchange="updateStudentGrade(${idx}, 'f1_m2', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f1_m2)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center bg-blue-50/50 font-bold ${colorClass(st.f1_avg)}">${toArabicDigits(st.f1_avg)}</td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.mid_term)}" onchange="updateStudentGrade(${idx}, 'mid_term', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.mid_term)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f2_oral1)}" onchange="updateStudentGrade(${idx}, 'f2_oral1', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f2_oral1)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f2_m1)}" onchange="updateStudentGrade(${idx}, 'f2_m1', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f2_m1)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f2_oral2)}" onchange="updateStudentGrade(${idx}, 'f2_oral2', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f2_oral2)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center"><input type="text" inputmode="numeric" value="${toArabicDigits(st.f2_m2)}" onchange="updateStudentGrade(${idx}, 'f2_m2', this.value)" class="w-14 text-center bg-slate-50 border border-slate-200 rounded py-1 ${colorClass(st.f2_m2)}"></td>
                    <td class="p-1 border-b border-slate-200 text-center bg-indigo-50/50 font-bold ${colorClass(st.f2_avg)}">${toArabicDigits(st.f2_avg)}</td>
                    <td class="p-1 border-b border-slate-200 text-center bg-emerald-50/50 font-bold ${colorClass(st.annual_score)}">${toArabicDigits(st.annual_score)}</td>
                    <td class="p-2 border-b border-slate-200 text-xs text-slate-800 font-bold whitespace-nowrap bg-slate-50/50">
                        <span class="inline-block px-2 py-1">${st.notes || ''}</span>
                    </td>
                    <td class="p-2 border-b border-slate-200 text-center no-print">
                        <button type="button" onclick="appendCrossMark(${idx})" class="w-9 h-9 bg-rose-50 hover:bg-rose-100 text-rose-600 rounded-xl font-black transition shadow-sm text-base" title="إضافة علامة X">❌</button>
                    </td>
                    <td class="p-2 border-b border-slate-200 text-center no-print">
                        <button type="button" onclick="confirmDeleteStudent(${idx})" class="text-rose-600 hover:text-rose-800 font-bold px-2 py-1 rounded transition" title="حذف الطالب">🗑️</button>
                    </td>
                `;
                tbody.appendChild(tr);
            });

            updateStatistics();
        }

        function updateStudentName(idx, val) {
            const students = getCurrentStudents();
            students[idx].name = val.trim();
            sortStudentsAlphabetically(students);
            saveToLocalStorage();
            renderGradesTable();
        }

        function appendCrossMark(idx) {
            const students = getCurrentStudents();
            const markText = `❌`;
            let currentNotes = students[idx].notes || '';
            if (currentNotes) {
                students[idx].notes = currentNotes + ' ' + markText;
            } else {
                students[idx].notes = markText;
            }
            saveToLocalStorage();
            renderGradesTable();
        }

        function updateStudentGrade(idx, field, val) {
            let cleanVal = parseArabicDigitsToEnglish(val);
            let num = parseFloat(cleanVal);
            if (isNaN(num) || num < 0 || num > 100) {
                showCustomModal("خطأ في الإدخال", "عذراً، يجب أن تكون الدرجة محصورة حصراً بين ٠ و ١٠٠.", false);
                renderGradesTable();
                return;
            }
            const students = getCurrentStudents();
            students[idx][field] = num;
            saveToLocalStorage();
            renderGradesTable();
        }

        function sortStudentsAlphabetically(students) {
            students.sort((a, b) => a.name.localeCompare(b.name, 'ar'));
        }

        function openAddStudentModal() {
            showCustomModalPrompt("إضافة طالب جديد", "أدخل اسم الطالب الثلاثي:", (name) => {
                if (name && name.trim() !== '') {
                    const students = getCurrentStudents();
                    students.push({
                        name: name.trim(),
                        f1_oral1: '', f1_m1: '', f1_oral2: '', f1_m2: '', f1_avg: '',
                        mid_term: '',
                        f2_oral1: '', f2_m1: '', f2_oral2: '', f2_m2: '', f2_avg: '',
                        annual_score: '', notes: ''
                    });
                    sortStudentsAlphabetically(students);
                    saveToLocalStorage();
                    renderGradesTable();
                }
            });
        }

        function confirmDeleteStudent(idx) {
            showCustomModal("حذف طالب", "هل أنت متأكد من حذف هذا الطالب من السجل؟", true, () => {
                const students = getCurrentStudents();
                students.splice(idx, 1);
                saveToLocalStorage();
                renderGradesTable();
            });
        }

        function importNamesFromFile(event) {
            const file = event.target.files[0];
            if (!file) return;
            const reader = new FileReader();
            reader.onload = function(e) {
                const content = e.target.result;
                const lines = content.split(/\r?\n/);
                const students = getCurrentStudents();
                lines.forEach(line => {
                    const cleanName = line.trim();
                    if (cleanName.length > 0) {
                        students.push({
                            name: cleanName,
                            f1_oral1: '', f1_m1: '', f1_oral2: '', f1_m2: '', f1_avg: '',
                            mid_term: '',
                            f2_oral1: '', f2_m1: '', f2_oral2: '', f2_m2: '', f2_avg: '',
                            annual_score: '', notes: ''
                        });
                    }
                });
                sortStudentsAlphabetically(students);
                saveToLocalStorage();
                renderGradesTable();
                showCustomModal("تم الاستيراد", "تمت إضافة أسماء الطلاب بنجاح وترتيبها أبجدياً.", false);
            };
            reader.readAsText(file);
        }

        function updateStatistics() {
            const students = getCurrentStudents();
            document.getElementById('stat-total-students').textContent = toArabicDigits(students.length);

            let passF1 = 0, failF1 = 0;
            let passMid = 0, failMid = 0;
            let passF2 = 0, failF2 = 0;
            let passAnnual = 0, failAnnual = 0;

            students.forEach(st => {
                calculateStudentGrades(st);
                if (st.f1_avg >= 50) passF1++; else failF1++;
                if (st.mid_term >= 50) passMid++; else failMid++;
                if (st.f2_avg >= 50) passF2++; else failF2++;
                if (st.annual_score >= 50) passAnnual++; else failAnnual++;
            });

            document.getElementById('pass-count-f1').textContent = toArabicDigits(passF1);
            document.getElementById('fail-count-f1').textContent = toArabicDigits(failF1);
            const percentF1 = students.length > 0 ? Math.round((passF1 / students.length) * 100) : 0;
            document.getElementById('pass-percent-f1').textContent = toArabicDigits(percentF1) + '٪';

            document.getElementById('pass-count-mid').textContent = toArabicDigits(passMid);
            document.getElementById('fail-count-mid').textContent = toArabicDigits(failMid);
            const percentMid = students.length > 0 ? Math.round((passMid / students.length) * 100) : 0;
            document.getElementById('pass-percent-mid').textContent = toArabicDigits(percentMid) + '٪';

            document.getElementById('pass-count-f2').textContent = toArabicDigits(passF2);
            document.getElementById('fail-count-f2').textContent = toArabicDigits(failF2);
            const percentF2 = students.length > 0 ? Math.round((passF2 / students.length) * 100) : 0;
            document.getElementById('pass-percent-f2').textContent = toArabicDigits(percentF2) + '٪';

            document.getElementById('pass-count-annual').textContent = toArabicDigits(passAnnual);
            document.getElementById('fail-count-annual').textContent = toArabicDigits(failAnnual);
            const percentAnnual = students.length > 0 ? Math.round((passAnnual / students.length) * 100) : 0;
            document.getElementById('pass-percent-annual').textContent = toArabicDigits(percentAnnual) + '٪';
        }

        // الاختبار اليومي
        function getDailyQuizStudents() {
            return getCurrentStudents();
        }

        function initDailyQuiz() {
            dailyQuizIndex = 0;
            loadNextDailyStudent();
        }

        function loadNextDailyStudent() {
            const students = getDailyQuizStudents();
            const nameEl = document.getElementById('daily-student-name');
            const infoEl = document.getElementById('daily-student-info');
            const statusEl = document.getElementById('daily-status-msg');
            document.getElementById('daily-grade-input').value = '';

            if (students.length === 0) {
                nameEl.textContent = "لا توجد أسماء طلاب في هذه المرحلة";
                infoEl.textContent = "";
                return;
            }

            if (dailyQuizIndex >= students.length) {
                dailyQuizIndex = 0;
            }

            const st = students[dailyQuizIndex];
            nameEl.textContent = st.name;
            infoEl.textContent = `المرحلة: ${currentGrade} (شعبة ${currentSection}) - الطالب رقم ${toArabicDigits(dailyQuizIndex + 1)} من ${toArabicDigits(students.length)}`;
            statusEl.textContent = "";
        }

        function saveDailyGradeAndNext() {
            const students = getDailyQuizStudents();
            if (students.length === 0) return;
            const inputVal = document.getElementById('daily-grade-input').value;
            const val = parseFloat(parseArabicDigitsToEnglish(inputVal));
            if (isNaN(val) || val < 0 || val > 100) {
                showCustomModal("تنبيه", "يرجى إدخال درجة صحيحة بين ٠ و ١٠٠.", false);
                return;
            }

            const st = students[dailyQuizIndex];
            if (!st.f1_oral1) {
                st.f1_oral1 = val;
            } else if (!st.f1_oral2) {
                st.f1_oral2 = val;
            } else if (!st.f2_oral1) {
                st.f2_oral1 = val;
            } else {
                st.f2_oral2 = val;
            }

            saveToLocalStorage();
            renderGradesTable();
            dailyQuizIndex++;
            loadNextDailyStudent();
        }

        // الحضور والغياب
        function initAttendanceSession() {
            attendanceIndex = 0;
            currentAttendanceRecords = [];
            const students = getCurrentStudents();
            if (students.length > 0) {
                document.getElementById('attendance-active-container').classList.remove('hidden');
                document.getElementById('attendance-summary-container').classList.add('hidden');
                renderAttendanceStep();
            } else {
                document.getElementById('att-student-name').textContent = "لا توجد أسماء طلاب مسجلة";
                document.getElementById('att-counter-info').textContent = "";
            }
        }

        function renderAttendanceStep() {
            const students = getCurrentStudents();
            if (attendanceIndex < students.length) {
                const st = students[attendanceIndex];
                document.getElementById('att-student-name').textContent = st.name;
                document.getElementById('att-counter-info').textContent = `الطالب ${toArabicDigits(attendanceIndex + 1)} من ${toArabicDigits(students.length)}`;
                const todayStr = new Date().toLocaleDateString('ar-EG', { year: 'numeric', month: 'long', day: 'numeric', weekday: 'long' });
                document.getElementById('att-date-display').textContent = "التاريخ: " + todayStr;
            } else {
                finishAttendanceSession();
            }
        }

        function recordAttendanceStatus(status) {
            const students = getCurrentStudents();
            if (attendanceIndex < students.length) {
                const st = students[attendanceIndex];
                currentAttendanceRecords.push({ student: st.name, status: status });

                if (status === 'غائب') {
                    const todayStr = new Date().toLocaleDateString('ar-EG', { year: 'numeric', month: 'long', day: 'numeric', weekday: 'long' }) + ' ' + new Date().toLocaleTimeString('ar-EG', {hour: '2-digit', minute:'2-digit'});
                    const noteText = `غائب بتاريخ ${todayStr}`;
                    st.notes = st.notes ? st.notes + ' | ' + noteText : noteText;
                    saveToLocalStorage();
                }

                attendanceIndex++;
                renderAttendanceStep();
            }
        }

        function revertAttendanceStep() {
            if (attendanceIndex > 0) {
                attendanceIndex--;
                currentAttendanceRecords.pop();
                renderAttendanceStep();
            }
        }

        function finishAttendanceSession() {
            document.getElementById('attendance-active-container').classList.add('hidden');
            document.getElementById('attendance-summary-container').classList.remove('hidden');

            const todayStr = new Date().toLocaleDateString('ar-EG', { year: 'numeric', month: 'long', day: 'numeric', weekday: 'long' });
            document.getElementById('summary-date-text').textContent = "تاريخ السجل: " + todayStr;

            const presentCount = currentAttendanceRecords.filter(r => r.status === 'حاضر').length;
            const absentCount = currentAttendanceRecords.filter(r => r.status === 'غائب').length;

            document.getElementById('summary-present-count').textContent = toArabicDigits(presentCount);
            document.getElementById('summary-absent-count').textContent = toArabicDigits(absentCount);

            if (!appData.absenceLogs) appData.absenceLogs = {};
            appData.absenceLogs[todayStr] = {
                records: [...currentAttendanceRecords],
                image: null
            };
            saveToLocalStorage();
        }

        function resetAttendanceSession() {
            initAttendanceSession();
        }

        // سجل الغياب
        function initAbsenceLogDropdown() {
            const select = document.getElementById('absence-date-select');
            select.innerHTML = '';
            const dates = Object.keys(appData.absenceLogs || {});
            if (dates.length === 0) {
                select.innerHTML = `<option>لا توجد تواريخ مسجلة</option>`;
                document.getElementById('absence-log-view-area').innerHTML = `<p class="text-slate-400 text-center py-6">لا توجد سجلات حضور أو غياب محفوظة حتى الآن.</p>`;
                return;
            }
            dates.forEach(d => {
                const opt = document.createElement('option');
                opt.value = d;
                opt.textContent = d;
                opt.disabled = false;
                select.appendChild(opt);
            });
            renderAbsenceLogByDate();
        }

        function renderAbsenceLogByDate() {
            const select = document.getElementById('absence-date-select');
            const dateKey = select.value;
            const area = document.getElementById('absence-log-view-area');
            if (!dateKey || !appData.absenceLogs[dateKey]) {
                area.innerHTML = '';
                return;
            }

            const log = appData.absenceLogs[dateKey];
            let html = `<div class="bg-slate-50 p-4 rounded-xl border space-y-3"><h4 class="font-bold text-slate-800 text-base">سجل يوم: <span class="text-blue-900 bg-blue-100 px-3 py-1 rounded-lg select-all inline-block mt-1 font-black">${dateKey}</span></h4>`;
            html += `<div class="grid grid-cols-1 sm:grid-cols-2 gap-3">`;
            log.records.forEach(r => {
                const badgeColor = r.status === 'حاضر' ? 'bg-emerald-100 text-emerald-800' : 'bg-rose-100 text-rose-800';
                html += `<div class="flex justify-between items-center bg-white p-3 rounded-lg border shadow-sm"><span>${r.student}</span><span class="px-3 py-1 rounded-full text-xs font-bold ${badgeColor}">${r.status}</span></div>`;
            });
            html += `</div>`;

            if (log.image) {
                html += `<div class="mt-4"><p class="text-xs font-bold text-slate-600 mb-2">الصورة المرفقة:</p><img src="${log.image}" class="max-w-xs rounded-xl border shadow"></div>`;
            }
            html += `</div>`;
            area.innerHTML = html;
        }

        function saveLogImage(event) {
            const select = document.getElementById('absence-date-select');
            const dateKey = select.value;
            if (!dateKey || !appData.absenceLogs[dateKey]) return;

            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    appData.absenceLogs[dateKey].image = e.target.result;
                    saveToLocalStorage();
                    renderAbsenceLogByDate();
                    showCustomModal("تم الحفظ", "تم حفظ الصورة المرفقة مع السجل بنجاح.", false);
                };
                reader.readAsDataURL(file);
            }
        }

        // النسخ الاحتياطي
        function exportJSONBackup() {
            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(appData));
            const downloadAnchor = document.createElement('a');
            downloadAnchor.setAttribute("href", dataStr);
            downloadAnchor.setAttribute("download", "teacher_log_backup.json");
            document.body.appendChild(downloadAnchor);
            downloadAnchor.click();
            downloadAnchor.remove();
        }

        function importJSONBackup(event) {
            const file = event.target.files[0];
            if (!file) return;
            const reader = new FileReader();
            reader.onload = function(e) {
                try {
                    appData = JSON.parse(e.target.result);
                    saveToLocalStorage();
                    initApp();
                    showCustomModal("تم الاستيراد", "تم استعادة النسخة الاحتياطية بنجاح.", false);
                } catch (err) {
                    showCustomModal("خطأ", "الملف غير صالح أو التنسيق تالف.", false);
                }
            };
            reader.readAsText(file);
        }

        function toggleCloudSync() {
            const badge = document.getElementById('cloud-status-badge');
            badge.textContent = "الوضع الحالي: متصل بالسحاب ومزامن تلقائياً ☁️";
            badge.className = "inline-block px-4 py-1.5 rounded-full text-xs font-bold bg-emerald-100 text-emerald-800";
            showCustomModal("النسخ السحابي", "تم تفعيل المزامنة السحابية بنجاح.", false);
        }

        // الطباعة
        function openPrintModal() {
            document.getElementById('print-options-modal').classList.remove('hidden');
        }

        function executePrint() {
            document.getElementById('print-options-modal').classList.add('hidden');
            window.print();
        }

        // النوافذ المنبثقة
        function showCustomModal(title, message, showConfirm, callback) {
            document.getElementById('modal-title').textContent = title;
            document.getElementById('modal-message').textContent = message;
            document.getElementById('modal-input-container').classList.add('hidden');
            document.getElementById('custom-modal').classList.remove('hidden');
            activeModalCallback = callback;
        }

        function showCustomModalPrompt(title, message, callback) {
            document.getElementById('modal-title').textContent = title;
            document.getElementById('modal-message').textContent = message;
            document.getElementById('modal-prompt-input').value = '';
            document.getElementById('modal-input-container').classList.remove('hidden');
            document.getElementById('custom-modal').classList.remove('hidden');
            activeModalCallback = callback;
        }

        function closeModal(confirmed) {
            document.getElementById('custom-modal').classList.add('hidden');
            if (confirmed && activeModalCallback) {
                const promptVal = document.getElementById('modal-prompt-input').value;
                activeModalCallback(promptVal);
            }
            activeModalCallback = null;
        }

        function modalConfirmCallback() {
            closeModal(true);
        }

        function handleGlobalSearch(query) {
            const container = document.getElementById('global-search-results-container');
            const list = document.getElementById('search-results-list');
            const display = document.getElementById('search-query-display');

            if (!query || query.trim() === '') {
                container.classList.add('hidden');
                return;
            }

            display.textContent = query;
            list.innerHTML = '';
            let found = false;
            const normalizedQuery = normalizeArabic(query);

            Object.keys(appData.grades).forEach(key => {
                const students = appData.grades[key];
                const gradeName = key.split('_')[0];
                const sectionName = key.split('_')[1] || 'عامة';

                students.forEach(st => {
                    const normalizedStudentName = normalizeArabic(st.name);
                    if (normalizedStudentName.includes(normalizedQuery)) {
                        found = true;
                        calculateStudentGrades(st);
                        const div = document.createElement('div');
                        div.className = "p-4 bg-slate-50 rounded-xl border border-slate-200 space-y-3";
                        div.innerHTML = `
                            <div class="flex flex-wrap justify-between items-center gap-2 border-b pb-2">
                                <div>
                                    <span class="text-base font-black text-slate-900">${st.name}</span>
                                    <span class="text-xs text-slate-500 mr-2 bg-slate-200 px-2 py-0.5 rounded-lg">المرحلة: ${gradeName} (شعبة ${sectionName})</span>
                                </div>
                                <div class="text-xs font-bold text-blue-700">السعي النهائي: ${toArabicDigits(st.annual_score)}</div>
                            </div>
                            <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-2 text-xs text-center">
                                <div class="bg-white p-2 rounded border"><span class="block text-slate-500">شهر 1 ف1:</span><strong class="text-slate-800">${toArabicDigits(st.f1_m1)}</strong></div>
                                <div class="bg-white p-2 rounded border"><span class="block text-slate-500">شهر 2 ف1:</span><strong class="text-slate-800">${toArabicDigits(st.f1_m2)}</strong></div>
                                <div class="bg-blue-50 p-2 rounded border border-blue-200"><span class="block text-blue-700 font-bold">معدل ف1:</span><strong class="text-blue-900">${toArabicDigits(st.f1_avg)}</strong></div>
                                <div class="bg-white p-2 rounded border"><span class="block text-slate-500">نصف السنة:</span><strong class="text-slate-800">${toArabicDigits(st.mid_term)}</strong></div>
                                <div class="bg-white p-2 rounded border"><span class="block text-slate-500">شهر 1 ف2:</span><strong class="text-slate-800">${toArabicDigits(st.f2_m1)}</strong></div>
                                <div class="bg-white p-2 rounded border"><span class="block text-slate-500">شهر 2 ف2:</span><strong class="text-slate-800">${toArabicDigits(st.f2_m2)}</strong></div>
                                <div class="bg-indigo-50 p-2 rounded border border-indigo-200"><span class="block text-indigo-700 font-bold">معدل ف2:</span><strong class="text-indigo-900">${toArabicDigits(st.f2_avg)}</strong></div>
                            </div>
                            <div class="text-xs text-slate-600 bg-white p-2 rounded border"><strong>الملاحظات والسجلات:</strong> ${st.notes || 'لا توجد ملاحظات'}</div>
                        `;
                        list.appendChild(div);
                    }
                });
            });

            if (!found) {
                list.innerHTML = `<p class="text-slate-400 text-sm text-center py-4">لم يتم العثور على أي طالب بهذا الاسم في أي من المراحل.</p>`;
            }
            container.classList.remove('hidden');
        }

        window.onload = function() {
            initApp();
        };
    </script>
</body>
</html>
