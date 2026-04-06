<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ALANHAR - نظام إدارة الصرافة والحوالات (دولي متكامل)</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Tahoma', system-ui, sans-serif;
        }
        body {
            background-color: #f0f2f5;
            color: #1e2a3e;
            line-height: 1.5;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        @media print {
            @page { size: A4; margin: 1.2cm; }
            .no-print { display: none !important; }
            body { background: white; padding: 0; font-size: 11pt; }
            .card, .profit-card, .expense-card, .saljog-card { break-inside: avoid; border: 1px solid #ccc; box-shadow: none; }
            .report-table th { background: #e9ecef !important; color: black; }
        }
        header {
            background: linear-gradient(135deg, #0b2b5c, #1a6d7c);
            color: white;
            padding: 25px;
            border-radius: 24px;
            margin-bottom: 30px;
            box-shadow: 0 12px 20px rgba(0,0,0,0.1);
            text-align: center;
        }
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }
        .logo i { font-size: 3rem; color: #FFD966; }
        h1 { font-size: 2.2rem; letter-spacing: -0.5px; }
        .subtitle { font-size: 1rem; opacity: 0.9; margin-top: 5px; }
        .tabs {
            display: flex;
            background: white;
            border-radius: 60px;
            overflow: hidden;
            margin-bottom: 30px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            flex-wrap: wrap;
        }
        .tab {
            flex: 1;
            padding: 14px 12px;
            text-align: center;
            cursor: pointer;
            font-weight: 700;
            font-size: 1rem;
            transition: all 0.2s;
            background: #f8fafc;
            border-bottom: 3px solid transparent;
        }
        .tab.active {
            background: white;
            color: #0b2b5c;
            border-bottom: 3px solid #1a6d7c;
        }
        .content-section { display: none; animation: fade 0.3s ease; }
        .content-section.active { display: block; }
        @keyframes fade { from { opacity: 0; transform: translateY(8px);} to { opacity: 1; transform: translateY(0);} }
        .card {
            background: white;
            border-radius: 28px;
            padding: 24px;
            margin-bottom: 28px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.03);
            border: 1px solid #eef2f6;
        }
        .card-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: #0b2b5c;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #e2e8f0;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .currency-row {
            display: flex;
            flex-wrap: wrap;
            gap: 24px;
            margin-bottom: 20px;
        }
        .currency-card {
            flex: 1;
            min-width: 260px;
            background: #f9fbfd;
            border-radius: 20px;
            padding: 18px;
            border-right: 5px solid #2c7da0;
        }
        .input-group { margin-bottom: 14px; }
        .input-group label { display: block; font-weight: 600; margin-bottom: 6px; color: #334155; }
        .input-group input, .input-group select {
            width: 100%;
            padding: 12px 14px;
            border: 1px solid #cbd5e1;
            border-radius: 16px;
            font-size: 1rem;
            background: white;
        }
        .result-box {
            padding: 12px;
            border-radius: 20px;
            text-align: center;
            font-weight: bold;
            margin-top: 12px;
        }
        .positive { background: linear-gradient(95deg, #1e5f6b, #258f7f); color: white; }
        .negative { background: linear-gradient(95deg, #b91c1c, #991b1b); color: white; }
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 40px;
            font-weight: bold;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            transition: 0.2s;
            background: #1e5f6b;
            color: white;
        }
        .btn-primary { background: #0b2b5c; }
        .btn-success { background: #2b7a4b; }
        .btn-warning { background: #b45309; }
        .saljog-grid {
            display: flex;
            gap: 28px;
            flex-wrap: wrap;
        }
        .saljog-card {
            flex: 1;
            background: #eef7ff;
            border-radius: 24px;
            padding: 20px;
            border: 1px solid #bdd9e7;
        }
        /* أرباح - كل ربح بمربع */
        .profits-dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .profit-card {
            background: #fdf8f0;
            border-radius: 24px;
            padding: 18px;
            border-right: 6px solid #b45309;
            box-shadow: 0 4px 10px rgba(0,0,0,0.02);
        }
        .profit-card h4 {
            font-size: 1.2rem;
            margin-bottom: 12px;
            color: #92400e;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .profit-double-input {
            display: flex;
            gap: 12px;
            margin: 12px 0;
        }
        .profit-double-input div { flex: 1; }
        .expense-card {
            background: #fef9e8;
            border-radius: 20px;
            padding: 16px;
            border-bottom: 3px solid #d97706;
        }
        .total-badge {
            background: #2d6a4f;
            color: white;
            padding: 14px;
            border-radius: 28px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2rem;
            margin-top: 18px;
        }
        .summary-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        .stat-card {
            background: white;
            border-radius: 24px;
            padding: 18px;
            text-align: center;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
            border-top: 4px solid #1e5f6b;
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
            padding: 12px;
            text-align: center;
        }
        .report-table td {
            padding: 10px;
            border-bottom: 1px solid #e2e8f0;
            text-align: center;
        }
        footer { text-align: center; margin-top: 40px; color: #5b6e8c; }
        @media (max-width: 700px) { .container { padding: 12px; } }
    </style>
</head>
<body>
<div class="container">
    <header>
        <div class="logo">
            <i class="fas fa-landmark"></i>
            <div>
                <h1>نظام ALANHAR المتقدم</h1>
                <div class="subtitle">إدارة الصرافة والحوالات - دقيق واحترافي</div>
                <div class="subtitle">Gelişmiş Döviz ve Havale Yönetim Sistemi</div>
            </div>
        </div>
    </header>

    <div class="tabs no-print">
        <div class="tab active" data-tab="daily"><i class="fas fa-pen-alt"></i> البيانات اليومية / Günlük Veri</div>
        <div class="tab" data-tab="reportDaily"><i class="fas fa-chart-line"></i> التقرير اليومي / Günlük Rapor</div>
        <div class="tab" data-tab="history"><i class="fas fa-archive"></i> السجلات / Kayıtlar</div>
        <div class="tab" data-tab="monthlyReport"><i class="fas fa-calendar-week"></i> التقرير الشهري / Aylık Rapor</div>
    </div>

    <!-- ========================= قسم الإدخال اليومي ========================= -->
    <div id="daily" class="content-section active">
        <div class="card">
            <div class="card-title"><i class="fas fa-dollar-sign"></i> حركة المدين والدائن / Borç & Alacak</div>
            <div class="currency-row">
                <div class="currency-card"><label>🇺🇸 الدولار (USD)</label><div class="input-group"><label>المدين (çıkış)</label><input type="number" id="usdDebtor" step="0.01"></div><div class="input-group"><label>الدائن (giriş)</label><input type="number" id="usdCreditor" step="0.01"></div><div id="usdSurplus" class="result-box positive">فائض: $0.00</div></div>
                <div class="currency-card"><label>🇪🇺 اليورو (EUR)</label><div class="input-group"><label>المدين (çıkış)</label><input type="number" id="eurDebtor" step="0.01"></div><div class="input-group"><label>الدائن (giriş)</label><input type="number" id="eurCreditor" step="0.01"></div><div id="eurSurplus" class="result-box positive">فائض: €0.00</div></div>
                <div class="currency-card"><label>🇹🇷 الليرة (TRY)</label><div class="input-group"><label>المدين (çıkış)</label><input type="number" id="tryDebtor" step="0.01"></div><div class="input-group"><label>الدائن (giriş)</label><input type="number" id="tryCreditor" step="0.01"></div><div id="trySurplus" class="result-box positive">فائض: ₺0.00</div></div>
            </div>
        </div>

        <!-- حساب سلجوق بالدولار واليورو -->
        <div class="card">
            <div class="card-title"><i class="fas fa-wallet"></i> حساب الصلج (Saljoğ) - دولار / يورو</div>
            <div class="saljog-grid">
                <div class="saljog-card"><h3><i class="fas fa-dollar-sign"></i> صلج دولار (USD)</h3><div class="input-group"><label>الرصيد الأساسي / Temel Bakiye ($)</label><input type="number" id="saljogUsdAmount" step="0.01"></div><div class="input-group"><label>المصروف / Gider ($)</label><input type="number" id="saljogUsdExpense" step="0.01"></div><div class="input-group"><label>المكسب / Kâr ($)</label><input type="number" id="saljogUsdProfit" step="0.01"></div><div id="saljogUsdTotal" class="total-badge" style="background:#1e5f6b;">المجموع: $0.00</div></div>
                <div class="saljog-card"><h3><i class="fas fa-euro-sign"></i> صلج يورو (EUR)</h3><div class="input-group"><label>الرصيد الأساسي / Temel Bakiye (€)</label><input type="number" id="saljogEurAmount" step="0.01"></div><div class="input-group"><label>المصروف / Gider (€)</label><input type="number" id="saljogEurExpense" step="0.01"></div><div class="input-group"><label>المكسب / Kâr (€)</label><input type="number" id="saljogEurProfit" step="0.01"></div><div id="saljogEurTotal" class="total-badge" style="background:#1e5f6b;">المجموع: €0.00</div></div>
            </div>
        </div>

        <!-- الأرباح اليومية (كل ربح بمربع منفصل) -->
        <div class="card">
            <div class="card-title"><i class="fas fa-chart-simple"></i> الأرباح التفصيلية / Detaylı Kârlar</div>
            <div class="profits-dashboard" id="profitsContainer">
                <!-- سيتم إنشاؤها ديناميكياً -->
            </div>
            <div id="totalProfitsMain" class="total-badge" style="background:#0b3b3f;">إجمالي الأرباح الكلي: $0.00 / €0.00</div>
        </div>

        <!-- المصروفات اليومية الجاهزة (كل مصروف بمربع) -->
        <div class="card">
            <div class="card-title"><i class="fas fa-receipt"></i> المصروفات الثابتة / Sabit Giderler</div>
            <div id="expensesDynamicContainer" class="profits-dashboard"></div>
            <button id="addExpenseCat" class="btn btn-primary no-print" style="margin-top: 12px;"><i class="fas fa-plus"></i> إضافة مصروف جديد / Yeni Gider Ekle</button>
            <div id="totalExpensesMain" class="total-badge" style="background:#92400e;">إجمالي المصروفات: $0.00 / €0.00 / ₺0.00</div>
        </div>

        <div class="actions no-print" style="display: flex; gap: 15px; margin-top: 20px;">
            <button id="saveDailyBtn" class="btn btn-success"><i class="fas fa-save"></i> حفظ اليوم / Kaydet</button>
            <button id="resetDailyBtn" class="btn btn-warning"><i class="fas fa-undo-alt"></i> إعادة تعيين / Sıfırla</button>
            <button id="viewDailyReportBtn" class="btn btn-primary"><i class="fas fa-eye"></i> عرض التقرير اليومي</button>
        </div>
    </div>

    <!-- ========================= التقرير اليومي ========================= -->
    <div id="reportDaily" class="content-section">
        <div class="card"><div class="card-title"><i class="fas fa-chart-line"></i> ملخص اليوم</div><div id="dailyReportContent"></div></div>
        <div class="actions no-print"><button id="printDailyReportBtn" class="btn btn-success"><i class="fas fa-print"></i> طباعة التقرير</button><button id="backToDailyBtn" class="btn">العــودة</button></div>
    </div>

    <!-- ========================= السجلات السابقة ========================= -->
    <div id="history" class="content-section">
        <div class="card"><div class="card-title"><i class="fas fa-history"></i> السجلات المحفوظة</div><input type="date" id="historyFilter" style="margin-bottom: 16px; padding: 8px; border-radius: 30px;"><div id="historyTableContainer"></div><button id="clearAllHistory" class="btn btn-warning no-print">مسح الكل</button></div>
    </div>

    <!-- ========================= التقرير الشهري (مربعات الأرباح والمصروفات + إدخال يدوي) ========================= -->
    <div id="monthlyReport" class="content-section">
        <div class="card">
            <div class="card-title"><i class="fas fa-calendar-alt"></i> التقرير الشهري - Aylık Rapor</div>
            <div class="input-group" style="max-width: 280px;"><label>اختر الشهر / Ay Seçin</label><input type="month" id="monthPicker"></div>
            <button id="loadMonthlyBtn" class="btn btn-primary">عرض التقرير / Göster</button>
            <div id="monthlySummaryArea" class="summary-grid"></div>
            <div id="monthlyProfitsArea" style="margin-top: 30px;"><h3>📊 الأرباح الشهرية (كل صنف بمربع) / Aylık Kârlar</h3><div id="monthlyProfitsGrid" class="profits-dashboard"></div><div id="monthlyTotalProfits" class="total-badge"></div></div>
            <div id="monthlyExpensesArea" style="margin-top: 30px;"><h3>💰 المصروفات الشهرية (كل بند بمربع) / Aylık Giderler</h3><div id="monthlyExpensesGrid" class="profits-dashboard"></div><div id="monthlyTotalExpenses" class="total-badge"></div></div>
            <div class="no-print" style="margin-top: 30px;"><button id="printMonthlyBtn" class="btn btn-success"><i class="fas fa-print"></i> طباعة التقرير الشهري</button></div>
        </div>
    </div>
    <footer>ALANHAR Sistemi - İleri Döviz Yönetimi © 2025</footer>
</div>

<script>
    // -------------------  بيانات ثابتة --------------------
    let profitCategories = [
        { id: "swift", nameAr: "سويفت / Swift", nameTr: "Swift" },
        { id: "havale", nameAr: "حوالة / Havale", nameTr: "Havale" },
        { id: "silver", nameAr: "الفضة / Gümüş", nameTr: "Gümüş" },
        { id: "copper", nameAr: "النحاس / Bakır", nameTr: "Bakır" },
        { id: "external", nameAr: "خارجية / Dış", nameTr: "Dış Kâr" }
    ];
    let defaultExpenses = [
        { id: "food", nameAr: "الأكل / Yemek", nameTr: "Yemek", amount: 0, currency: "USD" },
        { id: "office", nameAr: "المكتب / Ofis", nameTr: "Ofis", amount: 0, currency: "USD" },
        { id: "hospitality", nameAr: "الضيافة / Misafirperverlik", nameTr: "Misafirperverlik", amount: 0, currency: "USD" },
        { id: "electricity", nameAr: "الكهرباء / Elektrik", nameTr: "Elektrik", amount: 0, currency: "USD" },
        { id: "gas", nameAr: "الغاز / Gaz", nameTr: "Gaz", amount: 0, currency: "USD" },
        { id: "building", nameAr: "عائدات المبنى / Bina Gelirleri", nameTr: "Bina Gelirleri", amount: 0, currency: "USD" }
    ];
    let customExpenses = []; // {id, nameAr, nameTr, amount, currency}

    let allHistory = JSON.parse(localStorage.getItem("alanhar_full_history")) || [];

    // ----  حفظ واسترجاع المصروفات المخصصة ----
    function saveExpensesToLocal() {
        let toStore = { defaultExpenses, customExpenses };
        localStorage.setItem("alanhar_expenses_structure", JSON.stringify(toStore));
    }
    function loadExpensesFromLocal() {
        let stored = localStorage.getItem("alanhar_expenses_structure");
        if(stored) {
            let data = JSON.parse(stored);
            defaultExpenses = data.defaultExpenses;
            customExpenses = data.customExpenses;
        }
    }
    loadExpensesFromLocal();

    // دالة بناء واجهة الأرباح والمصروفات
    function renderProfitInputs() {
        let container = document.getElementById("profitsContainer");
        if(!container) return;
        container.innerHTML = "";
        profitCategories.forEach(cat => {
            let div = document.createElement("div");
            div.className = "profit-card";
            div.innerHTML = `<h4><i class="fas fa-coins"></i> ${cat.nameAr} / ${cat.nameTr}</h4>
                            <div class="profit-double-input"><div><label>USD $</label><input type="number" id="profit_${cat.id}_usd" step="0.01" class="profit-input"></div>
                            <div><label>EUR €</label><input type="number" id="profit_${cat.id}_eur" step="0.01" class="profit-input"></div></div>`;
            container.appendChild(div);
        });
        attachProfitEvents();
    }
    function attachProfitEvents() {
        document.querySelectorAll(".profit-input").forEach(inp => inp.addEventListener("input", updateTotalsFromInputs));
    }

    function renderExpensesUI() {
        let container = document.getElementById("expensesDynamicContainer");
        if(!container) return;
        container.innerHTML = "";
        let allExp = [...defaultExpenses, ...customExpenses];
        allExp.forEach(exp => {
            let div = document.createElement("div");
            div.className = "expense-card";
            div.innerHTML = `<div style="display: flex; justify-content: space-between;"><strong><i class="fas fa-tag"></i> ${exp.nameAr} / ${exp.nameTr}</strong> <button class="removeExpenseBtn no-print" data-id="${exp.id}" style="background:transparent; border:none; color:#b91c1c;"><i class="fas fa-trash-alt"></i></button></div>
                            <div class="profit-double-input"><div><label>القيمة / Tutar</label><input type="number" id="expense_${exp.id}_amount" step="0.01" value="${exp.amount || 0}" class="expense-amount-input"></div>
                            <div><label>العملة / Para Birimi</label><select id="expense_${exp.id}_curr" class="expense-curr-select"><option value="USD" ${exp.currency=="USD"?"selected":""}>USD $</option><option value="EUR" ${exp.currency=="EUR"?"selected":""}>EUR €</option><option value="TRY" ${exp.currency=="TRY"?"selected":""}>TRY ₺</option></select></div></div>`;
            container.appendChild(div);
        });
        document.querySelectorAll(".expense-amount-input").forEach(inp => inp.addEventListener("input", updateTotalsFromInputs));
        document.querySelectorAll(".expense-curr-select").forEach(sel => sel.addEventListener("change", updateTotalsFromInputs));
        document.querySelectorAll(".removeExpenseBtn").forEach(btn => {
            btn.addEventListener("click", (e) => {
                let id = btn.dataset.id;
                customExpenses = customExpenses.filter(c => c.id != id);
                defaultExpenses = defaultExpenses.filter(d => d.id != id);
                saveExpensesToLocal();
                renderExpensesUI();
                updateTotalsFromInputs();
            });
        });
        updateTotalsFromInputs();
    }

    document.getElementById("addExpenseCat")?.addEventListener("click", () => {
        let newNameAr = prompt("اسم المصروف بالعربية / Arapça isim");
        let newNameTr = prompt("Türkçe isim / الاسم بالتركي");
        if(newNameAr && newNameTr){
            let newId = "custom_" + Date.now();
            customExpenses.push({ id: newId, nameAr: newNameAr, nameTr: newNameTr, amount: 0, currency: "USD" });
            saveExpensesToLocal();
            renderExpensesUI();
        }
    });

    // تحديث كل القيم والكل
    function updateTotalsFromInputs() {
        let usdDeb = parseFloat(document.getElementById("usdDebtor")?.value)||0;
        let usdCred = parseFloat(document.getElementById("usdCreditor")?.value)||0;
        let usdSurplus = usdDeb - usdCred;
        let usdDiv = document.getElementById("usdSurplus");
        if(usdDiv) { usdDiv.innerText = `الفائض / Kar-Zarar: $${usdSurplus.toFixed(2)}`; usdDiv.className = `result-box ${usdSurplus>=0?'positive':'negative'}`; }
        let eurDeb = parseFloat(document.getElementById("eurDebtor")?.value)||0;
        let eurCred = parseFloat(document.getElementById("eurCreditor")?.value)||0;
        let eurSurplus = eurDeb - eurCred;
        let eurDiv = document.getElementById("eurSurplus");
        if(eurDiv) { eurDiv.innerText = `الفائض / Kar-Zarar: €${eurSurplus.toFixed(2)}`; eurDiv.className = `result-box ${eurSurplus>=0?'positive':'negative'}`; }
        let tryDeb = parseFloat(document.getElementById("tryDebtor")?.value)||0;
        let tryCred = parseFloat(document.getElementById("tryCreditor")?.value)||0;
        let trySurplus = tryDeb - tryCred;
        let tryDiv = document.getElementById("trySurplus");
        if(tryDiv) { tryDiv.innerText = `الفائض / Kar-Zarar: ₺${trySurplus.toFixed(2)}`; tryDiv.className = `result-box ${trySurplus>=0?'positive':'negative'}`; }

        // صلج
        let sUsdAmt = parseFloat(document.getElementById("saljogUsdAmount")?.value)||0;
        let sUsdExp = parseFloat(document.getElementById("saljogUsdExpense")?.value)||0;
        let sUsdProfit = parseFloat(document.getElementById("saljogUsdProfit")?.value)||0;
        let sUsdTotal = sUsdAmt - sUsdExp + sUsdProfit;
        document.getElementById("saljogUsdTotal").innerText = `المجموع: $${sUsdTotal.toFixed(2)}`;
        let sEurAmt = parseFloat(document.getElementById("saljogEurAmount")?.value)||0;
        let sEurExp = parseFloat(document.getElementById("saljogEurExpense")?.value)||0;
        let sEurProfit = parseFloat(document.getElementById("saljogEurProfit")?.value)||0;
        let sEurTotal = sEurAmt - sEurExp + sEurProfit;
        document.getElementById("saljogEurTotal").innerText = `المجموع: €${sEurTotal.toFixed(2)}`;

        // جمع الأرباح
        let totalUsdProfit = 0, totalEurProfit = 0;
        profitCategories.forEach(cat => {
            let u = parseFloat(document.getElementById(`profit_${cat.id}_usd`)?.value)||0;
            let e = parseFloat(document.getElementById(`profit_${cat.id}_eur`)?.value)||0;
            totalUsdProfit += u; totalEurProfit += e;
        });
        document.getElementById("totalProfitsMain").innerHTML = `إجمالي الأرباح الكلي: $${totalUsdProfit.toFixed(2)} / €${totalEurProfit.toFixed(2)}`;

        // جمع المصروفات
        let allExp = [...defaultExpenses, ...customExpenses];
        let totalExpenses = { USD:0, EUR:0, TRY:0 };
        allExp.forEach(exp => {
            let amt = parseFloat(document.getElementById(`expense_${exp.id}_amount`)?.value)||0;
            let curr = document.getElementById(`expense_${exp.id}_curr`)?.value || "USD";
            if(amt>0) totalExpenses[curr] += amt;
            exp.amount = amt; exp.currency = curr;
        });
        document.getElementById("totalExpensesMain").innerHTML = `إجمالي المصروفات: $${totalExpenses.USD.toFixed(2)} / €${totalExpenses.EUR.toFixed(2)} / ₺${totalExpenses.TRY.toFixed(2)}`;
        saveExpensesToLocal();
    }

    function getCurrentDailyData() {
        let usdDeb = parseFloat(document.getElementById("usdDebtor")?.value)||0;
        let usdCred = parseFloat(document.getElementById("usdCreditor")?.value)||0;
        let eurDeb = parseFloat(document.getElementById("eurDebtor")?.value)||0;
        let eurCred = parseFloat(document.getElementById("eurCreditor")?.value)||0;
        let tryDeb = parseFloat(document.getElementById("tryDebtor")?.value)||0;
        let tryCred = parseFloat(document.getElementById("tryCreditor")?.value)||0;
        let sUsdTotal = parseFloat(document.getElementById("saljogUsdTotal")?.innerText.match(/[\d\.]+/)?.[0])||0;
        let sEurTotal = parseFloat(document.getElementById("saljogEurTotal")?.innerText.match(/[\d\.]+/)?.[0])||0;
        let profits = {};
        profitCategories.forEach(cat => { profits[cat.id] = { usd: parseFloat(document.getElementById(`profit_${cat.id}_usd`)?.value)||0, eur: parseFloat(document.getElementById(`profit_${cat.id}_eur`)?.value)||0 }; });
        let allExp = [...defaultExpenses, ...customExpenses];
        let expensesList = allExp.map(exp => ({ nameAr: exp.nameAr, nameTr: exp.nameTr, amount: exp.amount, currency: exp.currency }));
        return {
            date: new Date().toISOString().slice(0,10),
            timestamp: Date.now(),
            usd: { debtor: usdDeb, creditor: usdCred, surplus: usdDeb-usdCred },
            eur: { debtor: eurDeb, creditor: eurCred, surplus: eurDeb-eurCred },
            try: { debtor: tryDeb, creditor: tryCred, surplus: tryDeb-tryCred },
            saljog: { usdTotal: sUsdTotal, eurTotal: sEurTotal },
            profits: profits,
            expenses: expensesList,
            realSurplus: (usdDeb-usdCred) - sUsdTotal
        };
    }

    function saveToday() {
        let data = getCurrentDailyData();
        let existingIndex = allHistory.findIndex(r => r.date === data.date);
        if(existingIndex !== -1) allHistory[existingIndex] = data;
        else allHistory.push(data);
        localStorage.setItem("alanhar_full_history", JSON.stringify(allHistory));
        alert("تم حفظ اليوم بنجاح / Bugün kaydedildi");
        renderHistoryTable();
    }

    function renderHistoryTable() {
        let container = document.getElementById("historyTableContainer");
        if(!container) return;
        let filterDate = document.getElementById("historyFilter")?.value;
        let filtered = filterDate ? allHistory.filter(r => r.date === filterDate) : [...allHistory].reverse();
        if(filtered.length===0){ container.innerHTML = "<p class='card'>لا توجد سجلات</p>"; return; }
        let html = `<table class="report-table"><thead><tr><th>التاريخ</th><th>فائض دولار</th><th>صلج دولار</th><th>صلج يورو</th><th>الربح الحقيقي</th><th>الإجراء</th></tr></thead><tbody>`;
        filtered.forEach((rec, idx) => {
            html += `<tr><td>${rec.date}</td><td>$${rec.usd.surplus.toFixed(2)}</td><td>$${rec.saljog.usdTotal.toFixed(2)}</td><td>€${rec.saljog.eurTotal.toFixed(2)}</td><td>$${rec.realSurplus.toFixed(2)}</td><td><button class="btn editHistoryBtn" data-idx="${allHistory.indexOf(rec)}" style="padding:4px 12px;">تعديل</button> <button class="btn deleteHistoryBtn" data-idx="${allHistory.indexOf(rec)}" style="background:#b91c1c;">حذف</button></td></tr>`;
        });
        html += `</tbody></table>`;
        container.innerHTML = html;
        document.querySelectorAll(".editHistoryBtn").forEach(btn => btn.addEventListener("click", (e) => { let idx = btn.dataset.idx; loadToEdit(allHistory[idx]); }));
        document.querySelectorAll(".deleteHistoryBtn").forEach(btn => btn.addEventListener("click", (e) => { let idx = btn.dataset.idx; allHistory.splice(idx,1); localStorage.setItem("alanhar_full_history", JSON.stringify(allHistory)); renderHistoryTable(); }));
    }

    function loadToEdit(record) {
        if(!record) return;
        document.getElementById("usdDebtor").value = record.usd.debtor;
        document.getElementById("usdCreditor").value = record.usd.creditor;
        document.getElementById("eurDebtor").value = record.eur.debtor;
        document.getElementById("eurCreditor").value = record.eur.creditor;
        document.getElementById("tryDebtor").value = record.try.debtor;
        document.getElementById("tryCreditor").value = record.try.creditor;
        // صلج مخزن فقط المجموع ولكن نعيد تعيين قيم تقديرية
        for(let cat of profitCategories){
            if(record.profits[cat.id]){
                document.getElementById(`profit_${cat.id}_usd`).value = record.profits[cat.id].usd || 0;
                document.getElementById(`profit_${cat.id}_eur`).value = record.profits[cat.id].eur || 0;
            }
        }
        updateTotalsFromInputs();
        document.querySelector(".tab[data-tab='daily']").click();
        alert("تم تحميل البيانات للتعديل");
    }

    function showDailyReport() {
        let d = getCurrentDailyData();
        let profitHtml = `<div class="profits-dashboard">`;
        for(let cat of profitCategories){
            let usdVal = d.profits[cat.id]?.usd||0;
            let eurVal = d.profits[cat.id]?.eur||0;
            if(usdVal!==0 || eurVal!==0) profitHtml += `<div class="profit-card"><h4>${cat.nameAr}</h4><div>USD: $${usdVal.toFixed(2)}  EUR: €${eurVal.toFixed(2)}</div></div>`;
        }
        profitHtml += `</div><div class="total-badge">إجمالي الأرباح: $${Object.values(d.profits).reduce((s,p)=>s+p.usd,0).toFixed(2)} / €${Object.values(d.profits).reduce((s,p)=>s+p.eur,0).toFixed(2)}</div>`;
        let expHtml = `<div class="profits-dashboard">`;
        d.expenses.forEach(ex => { if(ex.amount>0) expHtml += `<div class="expense-card"><strong>${ex.nameAr}</strong> : ${ex.amount.toFixed(2)} ${ex.currency}</div>`; });
        expHtml += `</div>`;
        document.getElementById("dailyReportContent").innerHTML = `
            <div class="summary-grid"><div class="stat-card">🇺🇸 فائض دولار: $${d.usd.surplus.toFixed(2)}</div><div class="stat-card">🇪🇺 فائض يورو: €${d.eur.surplus.toFixed(2)}</div><div class="stat-card">صلج دولار: $${d.saljog.usdTotal.toFixed(2)}</div><div class="stat-card">صلج يورو: €${d.saljog.eurTotal.toFixed(2)}</div><div class="stat-card">⭐ الربح الحقيقي: $${d.realSurplus.toFixed(2)}</div></div>
            <h3>الأرباح التفصيلية</h3>${profitHtml}<h3>المصروفات</h3>${expHtml}
        `;
        document.querySelector(".tab[data-tab='reportDaily']").click();
    }

    // التقرير الشهري بمربعات منفصلة للأرباح والمصروفات
    function buildMonthlyReport() {
        let month = document.getElementById("monthPicker").value;
        if(!month) { alert("اختر شهراً"); return; }
        let filtered = allHistory.filter(r => r.date.startsWith(month));
        if(filtered.length===0){ document.getElementById("monthlySummaryArea").innerHTML = "<div class='card'>لا توجد بيانات لهذا الشهر</div>"; return; }
        let totalUsdSurplus = 0, totalEurSurplus = 0, totalReal = 0;
        let aggregatedProfits = {};
        profitCategories.forEach(c => { aggregatedProfits[c.id] = { usd:0, eur:0 }; });
        let aggregatedExpenses = {};
        filtered.forEach(rec => {
            totalUsdSurplus += rec.usd.surplus;
            totalEurSurplus += rec.eur.surplus;
            totalReal += rec.realSurplus;
            for(let cat of profitCategories){
                if(rec.profits[cat.id]){
                    aggregatedProfits[cat.id].usd += rec.profits[cat.id].usd || 0;
                    aggregatedProfits[cat.id].eur += rec.profits[cat.id].eur || 0;
                }
            }
            rec.expenses.forEach(exp => {
                if(!aggregatedExpenses[exp.nameAr]) aggregatedExpenses[exp.nameAr] = { nameAr: exp.nameAr, nameTr: exp.nameTr, USD:0, EUR:0, TRY:0 };
                if(exp.currency === "USD") aggregatedExpenses[exp.nameAr].USD += exp.amount;
                else if(exp.currency === "EUR") aggregatedExpenses[exp.nameAr].EUR += exp.amount;
                else if(exp.currency === "TRY") aggregatedExpenses[exp.nameAr].TRY += exp.amount;
            });
        });
        document.getElementById("monthlySummaryArea").innerHTML = `<div class="stat-card">إجمالي فائض دولار: $${totalUsdSurplus.toFixed(2)}</div><div class="stat-card">إجمالي فائض يورو: €${totalEurSurplus.toFixed(2)}</div><div class="stat-card">صافي الربح الحقيقي: $${totalReal.toFixed(2)}</div>`;
        // مربعات الأرباح
        let profitsGrid = "";
        for(let cat of profitCategories){
            let u = aggregatedProfits[cat.id].usd, e = aggregatedProfits[cat.id].eur;
            if(u!==0 || e!==0){
                profitsGrid += `<div class="profit-card"><h4>${cat.nameAr}</h4><div>USD: $${u.toFixed(2)}  |  EUR: €${e.toFixed(2)}</div></div>`;
            }
        }
        if(!profitsGrid) profitsGrid = "<div class='card'>لا توجد أرباح مسجلة</div>";
        document.getElementById("monthlyProfitsGrid").innerHTML = profitsGrid;
        let totalMonthProfitsUsd = Object.values(aggregatedProfits).reduce((s,p)=>s+p.usd,0);
        let totalMonthProfitsEur = Object.values(aggregatedProfits).reduce((s,p)=>s+p.eur,0);
        document.getElementById("monthlyTotalProfits").innerHTML = `إجمالي الأرباح الشهرية: $${totalMonthProfitsUsd.toFixed(2)} / €${totalMonthProfitsEur.toFixed(2)}`;
        // مربعات المصروفات
        let expGrid = "";
        for(let key in aggregatedExpenses){
            let ex = aggregatedExpenses[key];
            expGrid += `<div class="expense-card"><strong>${ex.nameAr}</strong><div>USD: $${ex.USD.toFixed(2)}  EUR: €${ex.EUR.toFixed(2)}  TRY: ₺${ex.TRY.toFixed(2)}</div></div>`;
        }
        if(!expGrid) expGrid = "<div class='card'>لا توجد مصروفات</div>";
        document.getElementById("monthlyExpensesGrid").innerHTML = expGrid;
        let totalExpUSD = Object.values(aggregatedExpenses).reduce((s,e)=>s+e.USD,0);
        let totalExpEUR = Object.values(aggregatedExpenses).reduce((s,e)=>s+e.EUR,0);
        let totalExpTRY = Object.values(aggregatedExpenses).reduce((s,e)=>s+e.TRY,0);
        document.getElementById("monthlyTotalExpenses").innerHTML = `إجمالي المصروفات الشهرية: $${totalExpUSD.toFixed(2)} / €${totalExpEUR.toFixed(2)} / ₺${totalExpTRY.toFixed(2)}`;
    }

    // الأحداث العامة
    document.getElementById("saveDailyBtn")?.addEventListener("click", saveToday);
    document.getElementById("resetDailyBtn")?.addEventListener("click", () => { if(confirm("مسح جميع حقول اليوم؟")) location.reload(); });
    document.getElementById("viewDailyReportBtn")?.addEventListener("click", showDailyReport);
    document.getElementById("backToDailyBtn")?.addEventListener("click", () => document.querySelector(".tab[data-tab='daily']").click());
    document.getElementById("printDailyReportBtn")?.addEventListener("click", () => { showDailyReport(); setTimeout(()=>window.print(), 300); });
    document.getElementById("printMonthlyBtn")?.addEventListener("click", () => { buildMonthlyReport(); setTimeout(()=>window.print(), 300); });
    document.getElementById("loadMonthlyBtn")?.addEventListener("click", buildMonthlyReport);
    document.getElementById("clearAllHistory")?.addEventListener("click", () => { if(confirm("مسح كل السجلات؟")){ allHistory=[]; localStorage.removeItem("alanhar_full_history"); renderHistoryTable(); } });
    document.getElementById("historyFilter")?.addEventListener("change", renderHistoryTable);
    document.querySelectorAll(".tab").forEach(t => t.addEventListener("click", function(){ let id=this.dataset.tab; document.querySelectorAll(".content-section").forEach(s=>s.classList.remove("active")); document.getElementById(id).classList.add("active"); if(id==="history") renderHistoryTable(); if(id==="monthlyReport" && document.getElementById("monthPicker").value) buildMonthlyReport(); }));
    renderProfitInputs();
    renderExpensesUI();
    updateTotalsFromInputs();
    renderHistoryTable();
</script>
</body>
</html>
