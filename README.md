<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no">
    <title>ALANHAR | نظام الصرافة المتطور - تقارير احترافية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Tahoma', system-ui, sans-serif;
        }
        body {
            background: #f0f4f8;
            color: #1e293b;
            line-height: 1.5;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        /* تنسيق الطباعة الاحترافي */
        @media print {
            @page {
                size: A4;
                margin: 1.8cm;
            }
            .no-print {
                display: none !important;
            }
            body, .container {
                background: white;
                padding: 0;
                margin: 0;
            }
            .card, .profit-card, .expense-card, .saljog-card, .summary-stat {
                break-inside: avoid;
                border: 1px solid #ccc !important;
                box-shadow: none !important;
                background: white !important;
            }
            .report-table th {
                background: #e2e8f0 !important;
                color: black !important;
                border: 1px solid #aaa;
            }
            .total-badge {
                background: #f1f5f9 !important;
                color: black !important;
                border: 1px solid #000;
            }
            header {
                background: none !important;
                color: black !important;
                box-shadow: none;
                border-bottom: 2px solid #ccc;
            }
            .positive, .negative {
                background: #f3f4f6 !important;
                color: black !important;
                border: 1px solid #333;
            }
            h1, h2, h3 {
                color: black !important;
            }
        }
        header {
            background: linear-gradient(135deg, #0f2b3d, #1b6b6b);
            color: white;
            padding: 24px;
            border-radius: 32px;
            margin-bottom: 30px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.08);
            text-align: center;
        }
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 18px;
            flex-wrap: wrap;
        }
        .logo i { font-size: 2.8rem; color: #FFD966; }
        h1 { font-size: 1.9rem; }
        .tabs {
            display: flex;
            background: white;
            border-radius: 48px;
            overflow-x: auto;
            margin-bottom: 28px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
        }
        .tab {
            padding: 12px 22px;
            cursor: pointer;
            font-weight: 700;
            background: #f8fafc;
            border-bottom: 3px solid transparent;
            white-space: nowrap;
        }
        .tab.active {
            background: white;
            color: #1b6b6b;
            border-bottom: 3px solid #1b6b6b;
        }
        .content-section { display: none; animation: fade 0.2s ease; }
        .content-section.active { display: block; }
        @keyframes fade { from { opacity: 0; } to { opacity: 1; } }
        .card {
            background: white;
            border-radius: 28px;
            padding: 24px;
            margin-bottom: 28px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.03);
            border: 1px solid #eef2f6;
        }
        .card-title {
            font-size: 1.4rem;
            font-weight: 700;
            color: #1b6b6b;
            margin-bottom: 20px;
            border-right: 5px solid #1b6b6b;
            padding-right: 18px;
        }
        .currency-row {
            display: flex;
            flex-wrap: wrap;
            gap: 24px;
        }
        .currency-card {
            flex: 1;
            background: #f9fbfe;
            border-radius: 24px;
            padding: 20px;
            border: 1px solid #dee4ec;
        }
        .input-group { margin-bottom: 14px; }
        .input-group label { font-weight: 600; display: block; margin-bottom: 6px; color: #2c3e5c; }
        .input-group input, .input-group select {
            width: 100%;
            padding: 12px 14px;
            border: 1px solid #cbd5e1;
            border-radius: 20px;
            font-size: 0.95rem;
        }
        .result-box {
            padding: 12px;
            border-radius: 20px;
            text-align: center;
            font-weight: bold;
            margin-top: 12px;
        }
        .positive { background: linear-gradient(95deg, #1b6b6b, #2b8c7a); color: white; }
        .negative { background: linear-gradient(95deg, #b91c1c, #a11313); color: white; }
        .btn {
            padding: 12px 22px;
            border: none;
            border-radius: 40px;
            font-weight: bold;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            transition: 0.2s;
            background: #1b6b6b;
            color: white;
        }
        .btn-success { background: #2b7a4b; }
        .btn-primary { background: #0f2b3d; }
        .saljog-grid {
            display: flex;
            gap: 28px;
            flex-wrap: wrap;
        }
        .saljog-card {
            flex: 1;
            background: #eef7ff;
            border-radius: 28px;
            padding: 22px;
            border: 1px solid #bdd9e7;
        }
        .profits-dashboard, .expenses-dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .profit-card {
            background: #fffaf2;
            border-radius: 24px;
            padding: 18px;
            border-right: 5px solid #e67e22;
        }
        .expense-card {
            background: #fff5e6;
            border-radius: 24px;
            padding: 16px;
            border-bottom: 3px solid #f39c12;
        }
        .total-badge {
            background: #1e5f6b;
            color: white;
            padding: 14px;
            border-radius: 40px;
            text-align: center;
            font-weight: bold;
            font-size: 1rem;
            margin-top: 20px;
        }
        .summary-stat {
            background: white;
            border-radius: 24px;
            padding: 18px;
            text-align: center;
            border-top: 4px solid #1b6b6b;
            box-shadow: 0 1px 4px rgba(0,0,0,0.05);
        }
        .report-table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: 20px;
            overflow: hidden;
        }
        .report-table th {
            background: #1e3a5f;
            color: white;
            padding: 10px;
        }
        .report-table td {
            padding: 8px;
            border-bottom: 1px solid #e2e8f0;
            text-align: center;
        }
        footer {
            text-align: center;
            margin-top: 40px;
            color: #5b6e8c;
            font-size: 0.8rem;
        }
    </style>
</head>
<body>
<div class="container">
    <header>
        <div class="logo"><i class="fas fa-chart-line"></i><div><h1>نظام ALANHAR - الصرافة الذكية</h1><div>دولار | يورو | ليرة | تقارير دقيقة</div><div>USD | EUR | TRY | Profesyonel Raporlama</div></div></div>
    </header>

    <div class="tabs no-print">
        <div class="tab active" data-tab="dailyInput"><i class="fas fa-keyboard"></i> البيانات اليومية</div>
        <div class="tab" data-tab="dailyReport"><i class="fas fa-chart-bar"></i> التقرير اليومي</div>
        <div class="tab" data-tab="historyTab"><i class="fas fa-database"></i> السجلات</div>
        <div class="tab" data-tab="monthlyTab"><i class="fas fa-calendar-alt"></i> التقرير الشهري</div>
    </div>

    <!-- قسم الإدخال اليومي -->
    <div id="dailyInput" class="content-section active">
        <div class="card"><div class="card-title"><i class="fas fa-dollar-sign"></i> حركة المدين والدائن</div>
            <div class="currency-row">
                <div class="currency-card"><label>🇺🇸 دولار USD</label><div class="input-group"><label>المدين (خروج)</label><input type="number" id="usdDebtor" step="0.01"></div><div class="input-group"><label>الدائن (دخول)</label><input type="number" id="usdCreditor" step="0.01"></div><div id="usdSurplusBox" class="result-box positive">الفائض: $0.00</div></div>
                <div class="currency-card"><label>🇪🇺 يورو EUR</label><div class="input-group"><label>المدين (خروج)</label><input type="number" id="eurDebtor" step="0.01"></div><div class="input-group"><label>الدائن (دخول)</label><input type="number" id="eurCreditor" step="0.01"></div><div id="eurSurplusBox" class="result-box positive">الفائض: €0.00</div></div>
                <div class="currency-card"><label>🇹🇷 ليرة TRY</label><div class="input-group"><label>المدين (خروج)</label><input type="number" id="tryDebtor" step="0.01"></div><div class="input-group"><label>الدائن (دخول)</label><input type="number" id="tryCreditor" step="0.01"></div><div id="trySurplusBox" class="result-box positive">الفائض: ₺0.00</div></div>
            </div>
        </div>

        <!-- حساب الصلج (سلجوق) دولار ويورو -->
        <div class="card"><div class="card-title"><i class="fas fa-wallet"></i> حساب الصلج / Saljoğ Hesabı</div>
            <div class="saljog-grid">
                <div class="saljog-card"><h3><i class="fas fa-dollar-sign"></i> صلج دولار (USD)</h3><div class="input-group"><label>الرصيد الأساسي</label><input type="number" id="saljogUsdAmount" step="0.01"></div><div class="input-group"><label>المصروف / Gider</label><input type="number" id="saljogUsdExpense" step="0.01"></div><div class="input-group"><label>المكسب / Kâr</label><input type="number" id="saljogUsdProfit" step="0.01"></div><div id="saljogUsdTotal" class="total-badge" style="background:#2c7da0;">المجموع: $0.00</div></div>
                <div class="saljog-card"><h3><i class="fas fa-euro-sign"></i> صلج يورو (EUR)</h3><div class="input-group"><label>الرصيد الأساسي</label><input type="number" id="saljogEurAmount" step="0.01"></div><div class="input-group"><label>المصروف / Gider</label><input type="number" id="saljogEurExpense" step="0.01"></div><div class="input-group"><label>المكسب / Kâr</label><input type="number" id="saljogEurProfit" step="0.01"></div><div id="saljogEurTotal" class="total-badge" style="background:#2c7da0;">المجموع: €0.00</div></div>
            </div>
        </div>

        <!-- الأرباح (كل ربح بمربع) -->
        <div class="card"><div class="card-title"><i class="fas fa-chart-simple"></i> الأرباح اليومية - تفصيل كامل</div><div id="profitsDynamicContainer" class="profits-dashboard"></div><div id="totalProfitsDisplay" class="total-badge">إجمالي الأرباح: $0.00 | €0.00</div></div>

        <!-- المصروفات الجاهزة (كل مصروف بمربع) -->
        <div class="card"><div class="card-title"><i class="fas fa-receipt"></i> المصروفات - بنود واضحة</div><div id="expensesDynamicContainer" class="expenses-dashboard"></div><button id="addExpenseItem" class="btn no-print"><i class="fas fa-plus"></i> إضافة بند مصروف جديد</button><div id="totalExpensesDisplay" class="total-badge">إجمالي المصروفات: $0.00 | €0.00 | ₺0.00</div></div>

        <div class="actions no-print" style="display: flex; gap: 16px; margin-top: 20px; flex-wrap:wrap;">
            <button id="saveDailyDataBtn" class="btn btn-success"><i class="fas fa-save"></i> حفظ اليوم</button>
            <button id="resetDailyBtn" class="btn btn-primary"><i class="fas fa-undo-alt"></i> إعادة تعيين</button>
            <button id="viewReportBtn" class="btn"><i class="fas fa-eye"></i> عرض التقرير اليومي</button>
        </div>
    </div>

    <!-- التقرير اليومي (للطباعة والعرض) -->
    <div id="dailyReport" class="content-section">
        <div class="card">
            <div class="card-title"><i class="fas fa-print"></i> التقرير اليومي المفصل - البيانات المدخلة</div>
            <div id="dailyReportContainer" class="print-friendly"></div>
        </div>
        <div class="actions no-print" style="display: flex; gap: 16px;">
            <button id="printDailyBtn" class="btn btn-success"><i class="fas fa-print"></i> طباعة التقرير</button>
            <button id="backToDailyBtn" class="btn">رجوع للإدخال</button>
        </div>
    </div>

    <!-- السجلات السابقة -->
    <div id="historyTab" class="content-section"><div class="card"><div class="card-title"><i class="fas fa-history"></i> السجلات المحفوظة</div><input type="date" id="historyFilterDate" style="margin-bottom: 16px; padding: 8px; border-radius: 30px;"><div id="historyListContainer"></div><button id="clearAllHistoryBtn" class="btn btn-primary no-print">مسح كل السجلات</button></div></div>

    <!-- التقرير الشهري -->
    <div id="monthlyTab" class="content-section"><div class="card"><div class="card-title"><i class="fas fa-chart-pie"></i> التقرير الشهري - Aylık Rapor</div><div class="input-group" style="max-width: 260px;"><label>اختر الشهر</label><input type="month" id="monthPicker"></div><button id="loadMonthlyReportBtn" class="btn">عرض التقرير</button>
        <div id="monthlySummaryStats" class="profits-dashboard" style="margin-top: 25px;"></div>
        <div style="margin-top: 25px;"><h3><i class="fas fa-landmark"></i> حساب الصلج (Saljoğ) الشهري</h3><div id="monthlySaljogBox" class="saljog-grid"></div></div>
        <div style="margin-top: 30px;"><h3>📊 الأرباح الشهرية (كل صنف بمربع)</h3><div id="monthlyProfitsGrid" class="profits-dashboard"></div><div id="monthlyTotalProfitsBox" class="total-badge"></div></div>
        <div style="margin-top: 30px;"><h3>💰 المصروفات الشهرية (كل بند بمربع)</h3><div id="monthlyExpensesGrid" class="expenses-dashboard"></div><div id="monthlyTotalExpensesBox" class="total-badge"></div></div>
        <div class="no-print" style="margin-top: 30px;"><button id="printMonthlyReportBtn" class="btn btn-success"><i class="fas fa-print"></i> طباعة التقرير الشهري</button></div>
    </div></div>
    <footer class="no-print">ALANHAR Sistemi | Döviz & Havale Yönetimi | تقارير دقيقة وقابلة للطباعة</footer>
</div>

<script>
    // ---------- بيانات الأرباح والمصروفات الثابتة ----------
    let profitCategories = [
        { id: "swift", nameAr: "سويفت / Swift", nameTr: "Swift" },
        { id: "havale", nameAr: "حوالة / Havale", nameTr: "Havale" },
        { id: "silver", nameAr: "الفضة / Gümüş", nameTr: "Gümüş" },
        { id: "copper", nameAr: "النحاس / Bakır", nameTr: "Bakır" },
        { id: "external", nameAr: "خارجية / Dış Kâr", nameTr: "Dış Kâr" }
    ];
    let defaultExpenses = [
        { id: "food", nameAr: "الأكل / Yemek", nameTr: "Yemek", amount: 0, currency: "USD" },
        { id: "office", nameAr: "المكتب / Ofis", nameTr: "Ofis", amount: 0, currency: "USD" },
        { id: "hospitality", nameAr: "الضيافة / Misafirperverlik", nameTr: "Misafirperverlik", amount: 0, currency: "USD" },
        { id: "electricity", nameAr: "الكهرباء / Elektrik", nameTr: "Elektrik", amount: 0, currency: "USD" },
        { id: "gas", nameAr: "الغاز / Gaz", nameTr: "Gaz", amount: 0, currency: "USD" },
        { id: "building", nameAr: "عائدات المبنى / Bina Gelirleri", nameTr: "Bina Gelirleri", amount: 0, currency: "USD" }
    ];
    let customExpenses = [];
    let allHistory = JSON.parse(localStorage.getItem("ALANHAR_MASTER")) || [];

    function saveMaster() { localStorage.setItem("ALANHAR_MASTER", JSON.stringify(allHistory)); }
    function saveExpensesStruct() { localStorage.setItem("ALANHAR_EXP_STRUCT", JSON.stringify({ defaultExpenses, customExpenses })); }
    function loadExpensesStruct() { let s = localStorage.getItem("ALANHAR_EXP_STRUCT"); if(s) { let d = JSON.parse(s); defaultExpenses = d.defaultExpenses; customExpenses = d.customExpenses; } }
    loadExpensesStruct();

    // رسم الأرباح
    function renderProfits() {
        let container = document.getElementById("profitsDynamicContainer");
        if(!container) return;
        container.innerHTML = "";
        profitCategories.forEach(cat => {
            let div = document.createElement("div"); div.className = "profit-card";
            div.innerHTML = `<h4><i class="fas fa-coins"></i> ${cat.nameAr}</h4><div style="display:flex; gap:12px;"><div style="flex:1"><label>$ USD</label><input type="number" id="profit_${cat.id}_usd" step="0.01" class="profit-input-val"></div><div style="flex:1"><label>€ EUR</label><input type="number" id="profit_${cat.id}_eur" step="0.01" class="profit-input-val"></div></div>`;
            container.appendChild(div);
        });
        attachProfitEvents();
    }
    function attachProfitEvents() { document.querySelectorAll(".profit-input-val").forEach(inp => inp.addEventListener("input", updateTotals)); }

    // رسم المصروفات
    function renderExpenses() {
        let container = document.getElementById("expensesDynamicContainer");
        if(!container) return;
        let allExp = [...defaultExpenses, ...customExpenses];
        container.innerHTML = "";
        allExp.forEach(exp => {
            let div = document.createElement("div"); div.className = "expense-card";
            div.innerHTML = `<div style="display:flex; justify-content:space-between;"><strong><i class="fas fa-tag"></i> ${exp.nameAr}</strong> <button class="removeExpenseBtn" data-id="${exp.id}" style="background:none; border:none; color:#b91c1c; cursor:pointer;"><i class="fas fa-trash-alt"></i></button></div>
                            <div style="display:flex; gap:12px; margin-top:8px;"><div style="flex:2"><input type="number" id="expense_${exp.id}_amt" step="0.01" value="${exp.amount||0}" class="expense-amount-field" placeholder="القيمة"></div>
                            <div style="flex:1"><select id="expense_${exp.id}_curr" class="expense-curr-field"><option value="USD" ${exp.currency=="USD"?"selected":""}>USD $</option><option value="EUR" ${exp.currency=="EUR"?"selected":""}>EUR €</option><option value="TRY" ${exp.currency=="TRY"?"selected":""}>TRY ₺</option></select></div></div>`;
            container.appendChild(div);
        });
        document.querySelectorAll(".expense-amount-field").forEach(inp => inp.addEventListener("input", updateTotals));
        document.querySelectorAll(".expense-curr-field").forEach(sel => sel.addEventListener("change", updateTotals));
        document.querySelectorAll(".removeExpenseBtn").forEach(btn => btn.addEventListener("click", (e) => { let id = btn.dataset.id; customExpenses = customExpenses.filter(c => c.id != id); defaultExpenses = defaultExpenses.filter(d => d.id != id); saveExpensesStruct(); renderExpenses(); updateTotals(); }));
        updateTotals();
    }
    document.getElementById("addExpenseItem")?.addEventListener("click", () => {
        let ar = prompt("اسم المصروف بالعربية");
        let tr = prompt("Türkçe isim");
        if(ar && tr) { customExpenses.push({ id: "cust_"+Date.now(), nameAr: ar, nameTr: tr, amount: 0, currency: "USD" }); saveExpensesStruct(); renderExpenses(); updateTotals(); }
    });

    function updateTotals() {
        // دولار
        let usdDeb = parseFloat(document.getElementById("usdDebtor")?.value)||0, usdCred = parseFloat(document.getElementById("usdCreditor")?.value)||0;
        let usdSur = usdDeb - usdCred; let usdBox = document.getElementById("usdSurplusBox"); if(usdBox){ usdBox.innerText = `الفائض: $${usdSur.toFixed(2)}`; usdBox.className = `result-box ${usdSur>=0?'positive':'negative'}`; }
        let eurDeb = parseFloat(document.getElementById("eurDebtor")?.value)||0, eurCred = parseFloat(document.getElementById("eurCreditor")?.value)||0;
        let eurSur = eurDeb - eurCred; let eurBox = document.getElementById("eurSurplusBox"); if(eurBox){ eurBox.innerText = `الفائض: €${eurSur.toFixed(2)}`; eurBox.className = `result-box ${eurSur>=0?'positive':'negative'}`; }
        let tryDeb = parseFloat(document.getElementById("tryDebtor")?.value)||0, tryCred = parseFloat(document.getElementById("tryCreditor")?.value)||0;
        let trySur = tryDeb - tryCred; let tryBox = document.getElementById("trySurplusBox"); if(tryBox){ tryBox.innerText = `الفائض: ₺${trySur.toFixed(2)}`; tryBox.className = `result-box ${trySur>=0?'positive':'negative'}`; }
        // صلج
        let sUsdAmt = parseFloat(document.getElementById("saljogUsdAmount")?.value)||0, sUsdExp = parseFloat(document.getElementById("saljogUsdExpense")?.value)||0, sUsdProf = parseFloat(document.getElementById("saljogUsdProfit")?.value)||0;
        let sUsdTotal = sUsdAmt - sUsdExp + sUsdProf; document.getElementById("saljogUsdTotal").innerHTML = `المجموع: $${sUsdTotal.toFixed(2)}`;
        let sEurAmt = parseFloat(document.getElementById("saljogEurAmount")?.value)||0, sEurExp = parseFloat(document.getElementById("saljogEurExpense")?.value)||0, sEurProf = parseFloat(document.getElementById("saljogEurProfit")?.value)||0;
        let sEurTotal = sEurAmt - sEurExp + sEurProf; document.getElementById("saljogEurTotal").innerHTML = `المجموع: €${sEurTotal.toFixed(2)}`;
        // أرباح
        let totalUsdProfit = 0, totalEurProfit = 0;
        profitCategories.forEach(cat => { let u = parseFloat(document.getElementById(`profit_${cat.id}_usd`)?.value)||0, e = parseFloat(document.getElementById(`profit_${cat.id}_eur`)?.value)||0; totalUsdProfit+=u; totalEurProfit+=e; });
        document.getElementById("totalProfitsDisplay").innerHTML = `إجمالي الأرباح: $${totalUsdProfit.toFixed(2)} | €${totalEurProfit.toFixed(2)}`;
        // مصروفات
        let allExp = [...defaultExpenses, ...customExpenses];
        let totalExp = { USD:0, EUR:0, TRY:0 };
        allExp.forEach(exp => { let amt = parseFloat(document.getElementById(`expense_${exp.id}_amt`)?.value)||0; let curr = document.getElementById(`expense_${exp.id}_curr`)?.value||"USD"; if(amt>0) totalExp[curr] += amt; exp.amount = amt; exp.currency = curr; });
        document.getElementById("totalExpensesDisplay").innerHTML = `إجمالي المصروفات: $${totalExp.USD.toFixed(2)} | €${totalExp.EUR.toFixed(2)} | ₺${totalExp.TRY.toFixed(2)}`;
        saveExpensesStruct();
    }

    function getCurrentData() {
        let usdDeb = parseFloat(document.getElementById("usdDebtor")?.value)||0, usdCred = parseFloat(document.getElementById("usdCreditor")?.value)||0;
        let eurDeb = parseFloat(document.getElementById("eurDebtor")?.value)||0, eurCred = parseFloat(document.getElementById("eurCreditor")?.value)||0;
        let tryDeb = parseFloat(document.getElementById("tryDebtor")?.value)||0, tryCred = parseFloat(document.getElementById("tryCreditor")?.value)||0;
        let sUsdTotal = parseFloat(document.getElementById("saljogUsdTotal")?.innerText.match(/[\d\.]+/)?.[0])||0;
        let sEurTotal = parseFloat(document.getElementById("saljogEurTotal")?.innerText.match(/[\d\.]+/)?.[0])||0;
        let profits = {};
        profitCategories.forEach(cat => { profits[cat.id] = { usd: parseFloat(document.getElementById(`profit_${cat.id}_usd`)?.value)||0, eur: parseFloat(document.getElementById(`profit_${cat.id}_eur`)?.value)||0 }; });
        let allExp = [...defaultExpenses, ...customExpenses];
        let expensesArr = allExp.map(e => ({ nameAr: e.nameAr, amount: e.amount, currency: e.currency }));
        return {
            date: new Date().toISOString().slice(0,10), timestamp: Date.now(),
            usd: { debtor: usdDeb, creditor: usdCred, surplus: usdDeb-usdCred },
            eur: { debtor: eurDeb, creditor: eurCred, surplus: eurDeb-eurCred },
            try: { debtor: tryDeb, creditor: tryCred, surplus: tryDeb-tryCred },
            saljog: { usdTotal: sUsdTotal, eurTotal: sEurTotal },
            profits: profits, expenses: expensesArr, realSurplus: (usdDeb-usdCred) - sUsdTotal
        };
    }

    function saveToday() {
        let data = getCurrentData();
        let idx = allHistory.findIndex(r => r.date === data.date);
        if(idx !== -1) allHistory[idx] = data;
        else allHistory.push(data);
        saveMaster();
        alert("تم حفظ اليوم بنجاح");
        renderHistoryTable();
    }
    function renderHistoryTable() {
        let container = document.getElementById("historyListContainer");
        if(!container) return;
        let filter = document.getElementById("historyFilterDate")?.value;
        let filtered = filter ? allHistory.filter(r=>r.date===filter) : [...allHistory].reverse();
        if(filtered.length===0){ container.innerHTML = "<div class='card'>لا توجد سجلات</div>"; return; }
        let html = `<table class="report-table"><thead><tr><th>التاريخ</th><th>فائض دولار</th><th>صلج دولار</th><th>صلج يورو</th><th>الربح الحقيقي</th><th>إجراء</th></tr></thead><tbody>`;
        filtered.forEach(rec => {
            let originalIdx = allHistory.findIndex(r=>r.timestamp===rec.timestamp);
            html += `<tr><td>${rec.date}</td><td>$${rec.usd.surplus.toFixed(2)}</td><td>$${rec.saljog.usdTotal.toFixed(2)}</td><td>€${rec.saljog.eurTotal.toFixed(2)}</td><td>$${rec.realSurplus.toFixed(2)}</td><td><button class="editHistoryBtn" data-idx="${originalIdx}" class="btn">تعديل</button> <button class="delHistoryBtn" data-idx="${originalIdx}" style="background:#b91c1c;">حذف</button></td></tr>`;
        });
        html += `</tbody></table>`;
        container.innerHTML = html;
        document.querySelectorAll(".editHistoryBtn").forEach(btn => btn.addEventListener("click", (e) => { let idx = btn.dataset.idx; loadRecordToEdit(allHistory[idx]); }));
        document.querySelectorAll(".delHistoryBtn").forEach(btn => btn.addEventListener("click", (e) => { let idx = btn.dataset.idx; allHistory.splice(idx,1); saveMaster(); renderHistoryTable(); }));
    }
    function loadRecordToEdit(rec) {
        if(!rec) return;
        document.getElementById("usdDebtor").value = rec.usd.debtor; document.getElementById("usdCreditor").value = rec.usd.creditor;
        document.getElementById("eurDebtor").value = rec.eur.debtor; document.getElementById("eurCreditor").value = rec.eur.creditor;
        document.getElementById("tryDebtor").value = rec.try.debtor; document.getElementById("tryCreditor").value = rec.try.creditor;
        for(let cat of profitCategories){
            if(rec.profits[cat.id]){ document.getElementById(`profit_${cat.id}_usd`).value = rec.profits[cat.id].usd; document.getElementById(`profit_${cat.id}_eur`).value = rec.profits[cat.id].eur; }
        }
        updateTotals();
        document.querySelector(".tab[data-tab='dailyInput']").click();
    }

    // عرض التقرير اليومي (للطباعة والعرض)
    function displayDailyReport() {
        let d = getCurrentData();
        // بناء الأرباح (فقط التي بها قيم >0 أو نعرضها بشكل منظم)
        let profitHtml = `<div class="profits-dashboard">`;
        for(let cat of profitCategories){
            let u = d.profits[cat.id]?.usd||0, e = d.profits[cat.id]?.eur||0;
            profitHtml += `<div class="profit-card"><h4>${cat.nameAr}</h4><div>$ ${u.toFixed(2)} &nbsp;&nbsp; € ${e.toFixed(2)}</div></div>`;
        }
        profitHtml += `</div>`;
        let expHtml = `<div class="expenses-dashboard">`;
        d.expenses.forEach(ex => { if(ex.amount>0) expHtml += `<div class="expense-card"><strong>${ex.nameAr}</strong> : ${ex.amount.toFixed(2)} ${ex.currency}</div>`; });
        if(d.expenses.filter(e=>e.amount>0).length===0) expHtml += `<div class="card">لا توجد مصروفات مسجلة</div>`;
        expHtml += `</div>`;
        let totalProfUSD = Object.values(d.profits).reduce((s,p)=>s+p.usd,0);
        let totalProfEUR = Object.values(d.profits).reduce((s,p)=>s+p.eur,0);
        let totalExpUSD = d.expenses.filter(e=>e.currency==='USD').reduce((s,e)=>s+e.amount,0);
        let totalExpEUR = d.expenses.filter(e=>e.currency==='EUR').reduce((s,e)=>s+e.amount,0);
        let totalExpTRY = d.expenses.filter(e=>e.currency==='TRY').reduce((s,e)=>s+e.amount,0);

        document.getElementById("dailyReportContainer").innerHTML = `
            <div style="margin-bottom: 30px; text-align:center;">
                <h2>تقرير اليوم: ${d.date}</h2>
                <p>ملخص حركة الصرافة - ALANHAR</p>
            </div>
            <div class="saljog-grid" style="margin-bottom:25px;">
                <div class="summary-stat">🇺🇸 فائض الدولار: $${d.usd.surplus.toFixed(2)}</div>
                <div class="summary-stat">🇪🇺 فائض اليورو: €${d.eur.surplus.toFixed(2)}</div>
                <div class="summary-stat">📌 صلج دولار: $${d.saljog.usdTotal.toFixed(2)}</div>
                <div class="summary-stat">📌 صلج يورو: €${d.saljog.eurTotal.toFixed(2)}</div>
                <div class="summary-stat">⭐ الربح الحقيقي: $${d.realSurplus.toFixed(2)}</div>
            </div>
            <h3 style="margin-top:20px;">🏆 الأرباح التفصيلية</h3>
            ${profitHtml}
            <div class="total-badge">إجمالي الأرباح: $${totalProfUSD.toFixed(2)} | €${totalProfEUR.toFixed(2)}</div>
            <h3 style="margin-top:25px;">📋 المصروفات</h3>
            ${expHtml}
            <div class="total-badge">إجمالي المصروفات: $${totalExpUSD.toFixed(2)} | €${totalExpEUR.toFixed(2)} | ₺${totalExpTRY.toFixed(2)}</div>
            <footer style="margin-top:30px;">تم إنشاؤه بواسطة نظام ALANHAR</footer>
        `;
        document.querySelector(".tab[data-tab='dailyReport']").click();
    }

    // التقرير الشهري
    function buildMonthly() {
        let month = document.getElementById("monthPicker").value;
        if(!month) { alert("اختر شهراً"); return; }
        let filtered = allHistory.filter(r => r.date.startsWith(month));
        if(filtered.length===0){ document.getElementById("monthlySummaryStats").innerHTML = "<div class='card'>لا توجد بيانات لهذا الشهر</div>"; return; }
        let totalUsdSurplus=0, totalEurSurplus=0, totalReal=0, totalSaljogUsd=0, totalSaljogEur=0;
        let aggProfits = {}; profitCategories.forEach(c=>aggProfits[c.id]={usd:0,eur:0});
        let aggExpenses = {};
        filtered.forEach(rec => {
            totalUsdSurplus += rec.usd.surplus; totalEurSurplus += rec.eur.surplus; totalReal += rec.realSurplus;
            totalSaljogUsd += rec.saljog.usdTotal; totalSaljogEur += rec.saljog.eurTotal;
            for(let cat of profitCategories){ if(rec.profits[cat.id]){ aggProfits[cat.id].usd += rec.profits[cat.id].usd; aggProfits[cat.id].eur += rec.profits[cat.id].eur; } }
            rec.expenses.forEach(ex => { if(!aggExpenses[ex.nameAr]) aggExpenses[ex.nameAr] = { nameAr:ex.nameAr, USD:0, EUR:0, TRY:0 }; if(ex.currency==='USD') aggExpenses[ex.nameAr].USD += ex.amount; else if(ex.currency==='EUR') aggExpenses[ex.nameAr].EUR += ex.amount; else aggExpenses[ex.nameAr].TRY += ex.amount; });
        });
        document.getElementById("monthlySummaryStats").innerHTML = `<div class="profit-card">🇺🇸 إجمالي فائض دولار: $${totalUsdSurplus.toFixed(2)}</div><div class="profit-card">🇪🇺 إجمالي فائض يورو: €${totalEurSurplus.toFixed(2)}</div><div class="profit-card">💰 صافي الربح الحقيقي: $${totalReal.toFixed(2)}</div>`;
        document.getElementById("monthlySaljogBox").innerHTML = `<div class="saljog-card"><h3>صلج دولار USD</h3><div class="total-badge">المجموع الشهري: $${totalSaljogUsd.toFixed(2)}</div></div><div class="saljog-card"><h3>صلج يورو EUR</h3><div class="total-badge">المجموع الشهري: €${totalSaljogEur.toFixed(2)}</div></div>`;
        let profitsHtml = ""; for(let cat of profitCategories){ let u=aggProfits[cat.id].usd, e=aggProfits[cat.id].eur; profitsHtml += `<div class="profit-card"><h4>${cat.nameAr}</h4><div>USD: $${u.toFixed(2)} | EUR: €${e.toFixed(2)}</div></div>`; }
        document.getElementById("monthlyProfitsGrid").innerHTML = profitsHtml;
        let totalPUSD = Object.values(aggProfits).reduce((s,p)=>s+p.usd,0); let totalPEUR = Object.values(aggProfits).reduce((s,p)=>s+p.eur,0);
        document.getElementById("monthlyTotalProfitsBox").innerHTML = `إجمالي الأرباح الشهرية: $${totalPUSD.toFixed(2)} | €${totalPEUR.toFixed(2)}`;
        let expHtml = ""; for(let key in aggExpenses){ let ex = aggExpenses[key]; expHtml += `<div class="expense-card"><strong>${ex.nameAr}</strong><div>USD: $${ex.USD.toFixed(2)}  EUR: €${ex.EUR.toFixed(2)}  TRY: ₺${ex.TRY.toFixed(2)}</div></div>`; }
        document.getElementById("monthlyExpensesGrid").innerHTML = expHtml || "<div class='card'>لا توجد مصروفات</div>";
        let totalExpUSD = Object.values(aggExpenses).reduce((s,e)=>s+e.USD,0); let totalExpEUR = Object.values(aggExpenses).reduce((s,e)=>s+e.EUR,0); let totalExpTRY = Object.values(aggExpenses).reduce((s,e)=>s+e.TRY,0);
        document.getElementById("monthlyTotalExpensesBox").innerHTML = `إجمالي المصروفات: $${totalExpUSD.toFixed(2)} / €${totalExpEUR.toFixed(2)} / ₺${totalExpTRY.toFixed(2)}`;
    }

    // أحداث
    document.getElementById("saveDailyDataBtn")?.addEventListener("click", saveToday);
    document.getElementById("resetDailyBtn")?.addEventListener("click", () => { if(confirm("مسح كل البيانات الحالية؟")) location.reload(); });
    document.getElementById("viewReportBtn")?.addEventListener("click", displayDailyReport);
    document.getElementById("backToDailyBtn")?.addEventListener("click", () => document.querySelector(".tab[data-tab='dailyInput']").click());
    document.getElementById("printDailyBtn")?.addEventListener("click", () => { displayDailyReport(); setTimeout(()=>window.print(), 400); });
    document.getElementById("printMonthlyReportBtn")?.addEventListener("click", () => { buildMonthly(); setTimeout(()=>window.print(), 400); });
    document.getElementById("loadMonthlyReportBtn")?.addEventListener("click", buildMonthly);
    document.getElementById("clearAllHistoryBtn")?.addEventListener("click", () => { if(confirm("مسح كل السجلات نهائياً؟")){ allHistory=[]; saveMaster(); renderHistoryTable(); } });
    document.getElementById("historyFilterDate")?.addEventListener("change", renderHistoryTable);
    document.querySelectorAll(".tab").forEach(t => t.addEventListener("click", function(){ let id=this.dataset.tab; document.querySelectorAll(".content-section").forEach(s=>s.classList.remove("active")); document.getElementById(id).classList.add("active"); if(id==="historyTab") renderHistoryTable(); if(id==="monthlyTab" && document.getElementById("monthPicker").value) buildMonthly(); }));
    renderProfits(); renderExpenses(); updateTotals(); renderHistoryTable();
</script>
</body>
</html>
