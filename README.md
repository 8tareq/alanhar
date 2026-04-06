<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ALANHAR Sistemi - Döviz ve Havale Yönetimi (Gelişmiş)</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        @media print {
            @page { size: A4; margin: 1.5cm; }
            .no-print { display: none !important; }
            body { background: white; padding: 0; font-size: 12pt; }
            .container { max-width: 100%; padding: 0; }
            .card, .real-surplus-box, .summary-card, .profits-card, .expense-grid-card { break-inside: avoid; box-shadow: none !important; border: 1px solid #ddd !important; background: white !important; }
            .report-table th { background-color: #f0f0f0 !important; color: black !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
            .positive, .negative { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
        }
        header {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            text-align: center;
        }
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 15px;
        }
        .logo i { font-size: 2.8rem; margin-left: 15px; color: #FFD700; }
        h1 { font-size: 2.5rem; margin-bottom: 10px; }
        .subtitle { font-size: 1.2rem; opacity: 0.9; }
        .subtitle-tr { font-size: 1.1rem; opacity: 0.8; margin-top: 5px; }
        .tabs {
            display: flex;
            background-color: #fff;
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }
        .tab {
            flex: 1;
            padding: 18px;
            text-align: center;
            cursor: pointer;
            font-weight: bold;
            font-size: 1.1rem;
            transition: all 0.3s;
            border-bottom: 3px solid transparent;
        }
        .tab.active {
            color: #1a2980;
            border-bottom: 3px solid #1a2980;
            background-color: #f0f7ff;
        }
        .content-section {
            display: none;
            animation: fadeIn 0.5s;
        }
        .content-section.active { display: block; }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .card {
            background-color: white;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }
        .card-title {
            font-size: 1.4rem;
            color: #1a2980;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .currency-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 25px;
        }
        .currency-box {
            flex: 1;
            min-width: 300px;
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            border-radius: 10px;
            padding: 20px;
            border-left: 5px solid #1a2980;
        }
        .currency-title {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            color: #1a2980;
            font-weight: bold;
            font-size: 1.2rem;
        }
        .currency-icon {
            width: 40px;
            height: 40px;
            background-color: #1a2980;
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-left: 10px;
        }
        .input-group {
            margin-bottom: 15px;
        }
        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }
        .input-group input, .input-group select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
        }
        .result-box {
            padding: 15px;
            border-radius: 8px;
            margin-top: 10px;
            text-align: center;
            font-weight: bold;
            font-size: 1.3rem;
        }
        .positive { background: linear-gradient(135deg, #1a2980, #26d0ce); color: white; }
        .negative { background: linear-gradient(135deg, #d32f2f, #b71c1c); color: white; }
        .btn {
            padding: 14px 25px;
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        .btn-print { background: linear-gradient(135deg, #4caf50, #2e7d32); }
        .btn-save { background: linear-gradient(135deg, #2196f3, #0d47a1); }
        .btn-reset { background: linear-gradient(135deg, #ff9800, #ef6c00); }
        .actions { display: flex; gap: 15px; margin-top: 25px; flex-wrap: wrap; }
        .saljog-box {
            background: linear-gradient(135deg, #b3e5fc, #81d4fa);
            border-left: 5px solid #0288d1;
        }
        .saljog-row {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }
        .saljog-card {
            flex: 1;
            background: white;
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        .real-surplus-box {
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
            border: 2px solid #4caf50;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            text-align: center;
        }
        .summary-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .summary-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            text-align: center;
        }
        .profits-card {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            border: 2px solid #8e24aa;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 25px;
        }
        .profits-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        .profit-category {
            background: white;
            border-radius: 10px;
            padding: 15px;
            border-right: 4px solid #8e24aa;
        }
        .profit-row {
            display: flex;
            gap: 15px;
            margin-bottom: 10px;
        }
        .profit-field { flex: 1; }
        .profit-field label { display: block; font-size: 0.9rem; color: #666; margin-bottom: 5px; }
        .profit-field input { width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 6px; }
        .profit-total-box {
            background: #4caf50;
            color: white;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2rem;
            margin-top: 15px;
        }
        /* مصروفات جاهزة - واضحة */
        .expense-grid-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }
        .expense-category-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        .expense-item-card {
            background: #fff8e1;
            border-right: 5px solid #ff9800;
            padding: 18px;
            border-radius: 12px;
            transition: 0.2s;
        }
        .expense-item-card label {
            font-weight: bold;
            display: block;
            margin-bottom: 8px;
            color: #e65100;
        }
        .expense-item-row {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-top: 10px;
        }
        .expense-item-row input, .expense-item-row select {
            flex: 1;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid #ccc;
        }
        .report-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        .report-table th {
            background-color: #1a2980;
            color: white;
            padding: 12px;
            text-align: right;
        }
        .report-table td {
            padding: 10px;
            border-bottom: 1px solid #eee;
        }
        .expense-total-box {
            background-color: #ffebee;
            padding: 12px;
            border-radius: 8px;
            text-align: center;
            font-weight: bold;
        }
        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #666;
        }
        .warning {
            background-color: #fff3e0;
            padding: 15px;
            border-radius: 8px;
            border-right: 5px solid #ff9800;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
<div class="container">
    <header>
        <div class="logo"><i class="fas fa-money-check-alt"></i><div><h1>نظام ALANHAR - ALANHAR Sistemi</h1><div class="subtitle">نظام متطور لإدارة محلات الصرافة والحوالات</div><div class="subtitle-tr">Döviz ve Havale Yönetimi için Gelişmiş Sistem</div></div></div>
    </header>
    <div class="tabs no-print">
        <div class="tab active" data-tab="input"><i class="fas fa-calculator"></i> إدخال البيانات اليومية</div>
        <div class="tab" data-tab="report"><i class="fas fa-chart-line"></i> التقرير اليومي</div>
        <div class="tab" data-tab="history"><i class="fas fa-history"></i> السجلات السابقة</div>
        <div class="tab" data-tab="monthly"><i class="fas fa-calendar-alt"></i> التقرير الشهري</div>
    </div>

    <!-- قسم الإدخال اليومي -->
    <div id="input" class="content-section active">
        <div class="warning"><i class="fas fa-exclamation-circle"></i> <strong>ملاحظة:</strong> إدخال جميع البيانات المطلوبة لتوليد تقرير يومي كامل.</div>
        <div class="card">
            <h2 class="card-title"><span><i class="fas fa-money-bill-wave"></i> المدين والدائن</span></h2>
            <div class="currency-container">
                <div class="currency-box"><div class="currency-title"><div class="currency-icon">$</div><div>الدولار (USD)</div></div>
                    <div class="input-group"><label>المدين (الخروج)</label><input type="number" id="usd-debtor" step="0.01" min="0"></div>
                    <div class="input-group"><label>الدائن (الدخول)</label><input type="number" id="usd-creditor" step="0.01" min="0"></div>
                    <div id="usd-surplus" class="result-box">الفائض: $0.00</div>
                </div>
                <div class="currency-box"><div class="currency-title"><div class="currency-icon">€</div><div>اليورو (EUR)</div></div>
                    <div class="input-group"><label>المدين (الخروج)</label><input type="number" id="eur-debtor" step="0.01" min="0"></div>
                    <div class="input-group"><label>الدائن (الدخول)</label><input type="number" id="eur-creditor" step="0.01" min="0"></div>
                    <div id="eur-surplus" class="result-box">الفائض: €0.00</div>
                </div>
                <div class="currency-box"><div class="currency-title"><div class="currency-icon">₺</div><div>الليرة (TRY)</div></div>
                    <div class="input-group"><label>المدين (الخروج)</label><input type="number" id="try-debtor" step="0.01" min="0"></div>
                    <div class="input-group"><label>الدائن (الدخول)</label><input type="number" id="try-creditor" step="0.01" min="0"></div>
                    <div id="try-surplus" class="result-box">الفائض: ₺0.00</div>
                </div>
            </div>
        </div>

        <!-- حساب الصلج بالدولار واليورو -->
        <div class="card">
            <h2 class="card-title"><span><i class="fas fa-wallet"></i> حساب الصلج (Saljoğ)</span></h2>
            <div class="saljog-row">
                <div class="saljog-card"><div class="currency-title"><i class="fas fa-dollar-sign"></i> صلج دولار (USD)</div>
                    <div class="input-group"><label>الرصيد الأساسي ($)</label><input type="number" id="saljog-amount-usd" step="0.01" value="0"></div>
                    <div class="input-group"><label>المصروف ($)</label><input type="number" id="saljog-expense-usd" step="0.01" value="0"></div>
                    <div class="input-group"><label>المكسب ($)</label><input type="number" id="saljog-profit-usd" step="0.01" value="0"></div>
                    <div id="saljog-total-usd" class="item-total-box" style="background:#0288d1;color:white;padding:10px;border-radius:8px;text-align:center;">المجموع: $0.00</div>
                </div>
                <div class="saljog-card"><div class="currency-title"><i class="fas fa-euro-sign"></i> صلج يورو (EUR)</div>
                    <div class="input-group"><label>الرصيد الأساسي (€)</label><input type="number" id="saljog-amount-eur" step="0.01" value="0"></div>
                    <div class="input-group"><label>المصروف (€)</label><input type="number" id="saljog-expense-eur" step="0.01" value="0"></div>
                    <div class="input-group"><label>المكسب (€)</label><input type="number" id="saljog-profit-eur" step="0.01" value="0"></div>
                    <div id="saljog-total-eur" class="item-total-box" style="background:#0288d1;color:white;padding:10px;border-radius:8px;text-align:center;">المجموع: €0.00</div>
                </div>
            </div>
        </div>

        <!-- الأرباح اليومية (تظهر فقط القيم المدخلة) -->
        <div class="profits-card">
            <div class="profits-title"><i class="fas fa-coins"></i> الأرباح اليومية (تظهر القيم المدخلة فقط)</div>
            <div class="profits-grid">
                <div class="profit-category"><div class="profit-category-title">Swift</div><div class="profit-row"><div class="profit-field"><label>$ USD</label><input type="number" id="swift-usd" step="0.01"></div><div class="profit-field"><label>€ EUR</label><input type="number" id="swift-eur" step="0.01"></div></div></div>
                <div class="profit-category"><div class="profit-category-title">Havala</div><div class="profit-row"><div class="profit-field"><label>$ USD</label><input type="number" id="havala-usd" step="0.01"></div><div class="profit-field"><label>€ EUR</label><input type="number" id="havala-eur" step="0.01"></div></div></div>
                <div class="profit-category"><div class="profit-category-title">الفضة</div><div class="profit-row"><div class="profit-field"><label>$ USD</label><input type="number" id="silver-usd" step="0.01"></div><div class="profit-field"><label>€ EUR</label><input type="number" id="silver-eur" step="0.01"></div></div></div>
                <div class="profit-category"><div class="profit-category-title">النحاس</div><div class="profit-row"><div class="profit-field"><label>$ USD</label><input type="number" id="copper-usd" step="0.01"></div><div class="profit-field"><label>€ EUR</label><input type="number" id="copper-eur" step="0.01"></div></div></div>
                <div class="profit-category"><div class="profit-category-title">خارجية</div><div class="profit-row"><div class="profit-field"><label>$ USD</label><input type="number" id="external-usd" step="0.01"></div><div class="profit-field"><label>€ EUR</label><input type="number" id="external-eur" step="0.01"></div></div></div>
            </div>
            <div class="profit-total-box" id="daily-profits-total">إجمالي الأرباح: $0.00 / €0.00</div>
        </div>

        <!-- مصروفات جاهزة (واضحة) -->
        <div class="expense-grid-card">
            <h2 class="card-title"><span><i class="fas fa-receipt"></i> المصروفات الجاهزة (Giderler)</span></h2>
            <div id="preset-expenses-container" class="expense-category-grid"></div>
            <div class="actions" style="margin-top:15px;"><button id="add-preset-expense" class="btn btn-save"><i class="fas fa-plus"></i> إضافة مصروف جديد</button></div>
            <div id="total-preset-expenses" class="expense-total-container" style="margin-top:20px;"></div>
        </div>

        <div class="actions no-print">
            <button id="save-data" class="btn btn-save"><i class="fas fa-save"></i> حفظ اليوم</button>
            <button id="generate-report" class="btn btn-print"><i class="fas fa-file-alt"></i> عرض التقرير</button>
            <button id="reset-data" class="btn btn-reset"><i class="fas fa-redo"></i> مسح اليوم</button>
        </div>
    </div>

    <!-- التقرير اليومي (نفس المنطق مع عرض الأرباح غير الصفرية فقط) -->
    <div id="report" class="content-section"><div class="report-header"><h2>تقرير يومي مفصل</h2><div id="report-date"></div></div>
        <div class="card"><h3>فائض العملات</h3><div id="report-summary-box"></div><table class="report-table" id="report-table"></table></div>
        <div class="card"><h3>تقرير الصلج</h3><div id="report-saljog-details"></div></div>
        <div class="real-surplus-box"><h3>الفائض الحقيقي (دولار - صلج دولار)</h3><div id="real-surplus-report">$0.00</div></div>
        <div class="profits-card"><h3>الأرباح اليومية (المسجلة فقط)</h3><div id="report-profits-nonzero"></div><div id="report-profits-total"></div></div>
        <div class="card"><h3>المصروفات</h3><table class="report-table" id="report-expenses-table"></table><div id="report-expenses-total"></div></div>
        <div class="actions"><button id="print-report" class="btn btn-print"><i class="fas fa-print"></i> طباعة</button><button id="back-to-input" class="btn btn-save">العودة</button></div>
    </div>

    <!-- السجلات السابقة مع إمكانية التعديل -->
    <div id="history" class="content-section"><div class="card"><h2>السجلات السابقة</h2><input type="date" id="filter-date" style="margin-bottom:15px;padding:8px;"><table class="report-table" id="history-table"><thead><tr><th>التاريخ</th><th>فائض دولار</th><th>صلج دولار</th><th>صلج يورو</th><th>الربح الحقيقي</th><th>الإجراءات</th></tr></thead><tbody></tbody></table><button id="clear-history" class="btn btn-reset">مسح الكل</button></div></div>

    <!-- التقرير الشهري (تجميع و تعديل يدوي) -->
    <div id="monthly" class="content-section"><div class="card"><h2>تقرير شهري - تجميع و تعديل يدوي</h2><div class="input-group"><label>اختر الشهر</label><input type="month" id="month-picker"></div><button id="load-month-report" class="btn">عرض التقرير</button><div id="monthly-summary"></div><div id="monthly-editable-grid"></div><button id="save-monthly-changes" class="btn btn-save">حفظ التعديلات</button></div></div>

    <footer class="no-print"><p>ALANHAR Sistemi - Döviz ve Havale Yönetimi</p></footer>
</div>

<script>
    // -------- البيانات العامة ----------
    let currentDailyData = null;
    let expenseCategories = []; // { id, nameAr, nameTr }
    let presetExpenses = [];    // { id, nameAr, nameTr, amount, currency }
    let expenseCounterId = 1;
    let historyRecords = JSON.parse(localStorage.getItem('alanhar_history')) || [];

    const presetNames = [{ar:"الاكل", tr:"Yemek"},{ar:"المكتب", tr:"Ofis"},{ar:"مصروفات الضيافة", tr:"Misafirperverlik"},{ar:"الكهرباء", tr:"Elektrik"},{ar:"الغاز", tr:"Gaz"},{ar:"عائدات المبنى", tr:"Bina Gelirleri"}];
    
    function initPresets() {
        if(localStorage.getItem('presetExpensesList')) {
            presetExpenses = JSON.parse(localStorage.getItem('presetExpensesList'));
            expenseCounterId = Math.max(...presetExpenses.map(e=>e.id),0)+1;
        } else {
            presetExpenses = presetNames.map((n,idx)=>({ id:idx+1, nameAr:n.ar, nameTr:n.tr, amount:0, currency:"USD" }));
            expenseCounterId = presetExpenses.length+1;
        }
        renderPresetExpensesUI();
    }
    function renderPresetExpensesUI() {
        const container = document.getElementById('preset-expenses-container');
        if(!container) return;
        container.innerHTML = '';
        presetExpenses.forEach(exp => {
            const div = document.createElement('div');
            div.className = 'expense-item-card';
            div.innerHTML = `
                <label><i class="fas fa-tag"></i> ${exp.nameAr} / ${exp.nameTr}</label>
                <div class="expense-item-row">
                    <input type="number" class="expense-amount" data-id="${exp.id}" value="${exp.amount||0}" step="0.01" placeholder="القيمة">
                    <select class="expense-currency" data-id="${exp.id}">
                        <option value="USD" ${exp.currency=='USD'?'selected':''}>USD $</option>
                        <option value="EUR" ${exp.currency=='EUR'?'selected':''}>EUR €</option>
                        <option value="TRY" ${exp.currency=='TRY'?'selected':''}>TRY ₺</option>
                    </select>
                    <button class="btn btn-reset remove-expense-preset" data-id="${exp.id}" style="padding:6px 12px;">حذف</button>
                </div>
            `;
            container.appendChild(div);
        });
        document.querySelectorAll('.expense-amount').forEach(inp => inp.addEventListener('change', updatePresetExpenses));
        document.querySelectorAll('.expense-currency').forEach(sel => sel.addEventListener('change', updatePresetExpenses));
        document.querySelectorAll('.remove-expense-preset').forEach(btn => btn.addEventListener('click', (e) => { let id = parseInt(btn.dataset.id); presetExpenses = presetExpenses.filter(e=>e.id!==id); savePresetsToLocal(); renderPresetExpensesUI(); updateDailyFromInputs(); }));
        updateTotalPresetExpenses();
    }
    function updatePresetExpenses() {
        presetExpenses.forEach(exp => {
            const amountInput = document.querySelector(`.expense-amount[data-id='${exp.id}']`);
            const currencySelect = document.querySelector(`.expense-currency[data-id='${exp.id}']`);
            if(amountInput) exp.amount = parseFloat(amountInput.value) || 0;
            if(currencySelect) exp.currency = currencySelect.value;
        });
        savePresetsToLocal();
        updateTotalPresetExpenses();
        if(currentDailyData) currentDailyData.presetExpenses = JSON.parse(JSON.stringify(presetExpenses));
    }
    function savePresetsToLocal() { localStorage.setItem('presetExpensesList', JSON.stringify(presetExpenses)); }
    function updateTotalPresetExpenses() {
        let totals = {USD:0, EUR:0, TRY:0};
        presetExpenses.forEach(e=>{ if(e.amount>0) totals[e.currency] += e.amount; });
        const container = document.getElementById('total-preset-expenses');
        if(container) container.innerHTML = `<div class="expense-total-box">🇺🇸 دولار: $${totals.USD.toFixed(2)} &nbsp;| 🇪🇺 يورو: €${totals.EUR.toFixed(2)} &nbsp;| 🇹🇷 ليرة: ₺${totals.TRY.toFixed(2)}</div>`;
    }
    document.getElementById('add-preset-expense')?.addEventListener('click',()=>{
        let newName = prompt("اسم المصروف (عربي / Türkçe) مثلاً: إنترنت / İnternet");
        if(newName){ presetExpenses.push({ id:expenseCounterId++, nameAr:newName, nameTr:newName, amount:0, currency:"USD" }); savePresetsToLocal(); renderPresetExpensesUI(); updateDailyFromInputs(); }
    });

    function updateDailyFromInputs() {
        let usdDebtor = parseFloat(document.getElementById('usd-debtor')?.value)||0;
        let usdCreditor = parseFloat(document.getElementById('usd-creditor')?.value)||0;
        let usdSurplus = usdDebtor - usdCreditor;
        document.getElementById('usd-surplus').innerHTML = `الفائض: $${usdSurplus.toFixed(2)}`;
        document.getElementById('usd-surplus').className = 'result-box '+(usdSurplus>=0?'positive':'negative');
        let eurDebtor = parseFloat(document.getElementById('eur-debtor')?.value)||0;
        let eurCreditor = parseFloat(document.getElementById('eur-creditor')?.value)||0;
        let eurSurplus = eurDebtor - eurCreditor;
        document.getElementById('eur-surplus').innerHTML = `الفائض: €${eurSurplus.toFixed(2)}`;
        document.getElementById('eur-surplus').className = 'result-box '+(eurSurplus>=0?'positive':'negative');
        let tryDebtor = parseFloat(document.getElementById('try-debtor')?.value)||0;
        let tryCreditor = parseFloat(document.getElementById('try-creditor')?.value)||0;
        let trySurplus = tryDebtor - tryCreditor;
        document.getElementById('try-surplus').innerHTML = `الفائض: ₺${trySurplus.toFixed(2)}`;
        document.getElementById('try-surplus').className = 'result-box '+(trySurplus>=0?'positive':'negative');
        
        let saljogUsdAmount = parseFloat(document.getElementById('saljog-amount-usd')?.value)||0;
        let saljogUsdExp = parseFloat(document.getElementById('saljog-expense-usd')?.value)||0;
        let saljogUsdProfit = parseFloat(document.getElementById('saljog-profit-usd')?.value)||0;
        let saljogUsdTotal = saljogUsdAmount - saljogUsdExp + saljogUsdProfit;
        document.getElementById('saljog-total-usd').innerHTML = `المجموع: $${saljogUsdTotal.toFixed(2)}`;
        
        let saljogEurAmount = parseFloat(document.getElementById('saljog-amount-eur')?.value)||0;
        let saljogEurExp = parseFloat(document.getElementById('saljog-expense-eur')?.value)||0;
        let saljogEurProfit = parseFloat(document.getElementById('saljog-profit-eur')?.value)||0;
        let saljogEurTotal = saljogEurAmount - saljogEurExp + saljogEurProfit;
        document.getElementById('saljog-total-eur').innerHTML = `المجموع: €${saljogEurTotal.toFixed(2)}`;
        
        let profits = { swift:{usd:parseFloat(document.getElementById('swift-usd')?.value)||0, eur:parseFloat(document.getElementById('swift-eur')?.value)||0}, havala:{usd:parseFloat(document.getElementById('havala-usd')?.value)||0, eur:parseFloat(document.getElementById('havala-eur')?.value)||0}, silver:{usd:parseFloat(document.getElementById('silver-usd')?.value)||0, eur:parseFloat(document.getElementById('silver-eur')?.value)||0}, copper:{usd:parseFloat(document.getElementById('copper-usd')?.value)||0, eur:parseFloat(document.getElementById('copper-eur')?.value)||0}, external:{usd:parseFloat(document.getElementById('external-usd')?.value)||0, eur:parseFloat(document.getElementById('external-eur')?.value)||0} };
        let totalUsdProfit = Object.values(profits).reduce((s,p)=>s+p.usd,0);
        let totalEurProfit = Object.values(profits).reduce((s,p)=>s+p.eur,0);
        document.getElementById('daily-profits-total').innerHTML = `إجمالي الأرباح: $${totalUsdProfit.toFixed(2)} / €${totalEurProfit.toFixed(2)}`;
        let realSurplus = usdSurplus - saljogUsdTotal;
        currentDailyData = { date: new Date().toISOString().split('T')[0], timestamp: Date.now(), usd:{debtor:usdDebtor,creditor:usdCreditor,surplus:usdSurplus}, eur:{debtor:eurDebtor,creditor:eurCreditor,surplus:eurSurplus}, try:{debtor:tryDebtor,creditor:tryCreditor,surplus:trySurplus}, saljog:{usd:{amount:saljogUsdAmount,expense:saljogUsdExp,profit:saljogUsdProfit,total:saljogUsdTotal}, eur:{amount:saljogEurAmount,expense:saljogEurExp,profit:saljogEurProfit,total:saljogEurTotal}}, profits, realSurplus, presetExpenses: JSON.parse(JSON.stringify(presetExpenses)) };
    }
    function saveData() {
        updateDailyFromInputs();
        if(!currentDailyData) return;
        let existingIndex = historyRecords.findIndex(r=>r.date === currentDailyData.date);
        if(existingIndex!==-1) historyRecords[existingIndex] = currentDailyData;
        else historyRecords.push(currentDailyData);
        localStorage.setItem('alanhar_history', JSON.stringify(historyRecords));
        alert("تم حفظ البيانات");
        loadHistoryTable();
    }
    function resetData() { if(confirm("مسح اليوم؟")){ location.reload(); } }
    function generateReport() {
        updateDailyFromInputs();
        document.getElementById('report-date').innerHTML = `التاريخ: ${currentDailyData.date}`;
        let summaryHtml = `<div class="summary-grid"><div class="summary-box usd">دولار: $${currentDailyData.usd.surplus.toFixed(2)}</div><div class="summary-box eur">يورو: €${currentDailyData.eur.surplus.toFixed(2)}</div><div class="summary-box try">ليرة: ₺${currentDailyData.try.surplus.toFixed(2)}</div></div>`;
        document.getElementById('report-summary-box').innerHTML = summaryHtml;
        document.getElementById('report-table').innerHTML = `<thead><tr><th>العملة</th><th>المدين</th><th>الدائن</th><th>الفائض</th></tr></thead><tbody><tr><td>USD</td><td>$${currentDailyData.usd.debtor.toFixed(2)}</td><td>$${currentDailyData.usd.creditor.toFixed(2)}</td><td>$${currentDailyData.usd.surplus.toFixed(2)}</td></tr><tr><td>EUR</td><td>€${currentDailyData.eur.debtor.toFixed(2)}</td><td>€${currentDailyData.eur.creditor.toFixed(2)}</td><td>€${currentDailyData.eur.surplus.toFixed(2)}</td></tr><tr><td>TRY</td><td>₺${currentDailyData.try.debtor.toFixed(2)}</td><td>₺${currentDailyData.try.creditor.toFixed(2)}</td><td>₺${currentDailyData.try.surplus.toFixed(2)}</td></tr></tbody>`;
        document.getElementById('report-saljog-details').innerHTML = `<div class="summary-grid"><div class="summary-card">صلج دولار: $${currentDailyData.saljog.usd.total.toFixed(2)} (رصيد:$${currentDailyData.saljog.usd.amount} - مصروف:$${currentDailyData.saljog.usd.expense} + مكسب:$${currentDailyData.saljog.usd.profit})</div><div class="summary-card">صلج يورو: €${currentDailyData.saljog.eur.total.toFixed(2)}</div></div>`;
        document.getElementById('real-surplus-report').innerHTML = `<span class="summary-value">الفائض الحقيقي: $${currentDailyData.realSurplus.toFixed(2)}</span>`;
        let profitsNonZero = [];
        for(let [cat,vals] of Object.entries(currentDailyData.profits)){ if(vals.usd>0) profitsNonZero.push(`${cat} USD: $${vals.usd}`); if(vals.eur>0) profitsNonZero.push(`${cat} EUR: €${vals.eur}`); }
        document.getElementById('report-profits-nonzero').innerHTML = profitsNonZero.length? `<ul>${profitsNonZero.map(p=>`<li>${p}</li>`).join('')}</ul>` : "<p>لا توجد أرباح مسجلة اليوم</p>";
        let totalP = Object.values(currentDailyData.profits).reduce((s,p)=>s+p.usd,0);
        let totalPe = Object.values(currentDailyData.profits).reduce((s,p)=>s+p.eur,0);
        document.getElementById('report-profits-total').innerHTML = `<div class="profit-total-box">إجمالي الأرباح: $${totalP.toFixed(2)} / €${totalPe.toFixed(2)}</div>`;
        let expenseRows = currentDailyData.presetExpenses.filter(e=>e.amount>0).map(e=>`<tr><td>${e.nameAr}</td><td>${e.amount.toFixed(2)}</td><td>${e.currency}</td></tr>`).join('');
        document.getElementById('report-expenses-table').innerHTML = `<thead><tr><th>الوصف</th><th>القيمة</th><th>العملة</th></tr></thead><tbody>${expenseRows||'<tr><td colspan="3">لا توجد مصروفات</td></tr>'}</tbody>`;
        let totalExp = {USD:0,EUR:0,TRY:0}; currentDailyData.presetExpenses.forEach(e=>{if(e.amount>0) totalExp[e.currency]+=e.amount;});
        document.getElementById('report-expenses-total').innerHTML = `<div class="expense-total-box">إجمالي المصروفات: $${totalExp.USD.toFixed(2)} / €${totalExp.EUR.toFixed(2)} / ₺${totalExp.TRY.toFixed(2)}</div>`;
        switchTab('report');
    }
    function loadHistoryTable() {
        let tbody = document.querySelector('#history-table tbody');
        tbody.innerHTML = '';
        historyRecords.slice().reverse().forEach((rec,idx)=>{
            let row = tbody.insertRow();
            row.insertCell(0).innerText = rec.date;
            row.insertCell(1).innerHTML = `$${rec.usd.surplus.toFixed(2)}`;
            row.insertCell(2).innerHTML = `$${rec.saljog.usd.total.toFixed(2)}`;
            row.insertCell(3).innerHTML = `€${rec.saljog.eur.total.toFixed(2)}`;
            row.insertCell(4).innerHTML = `$${rec.realSurplus.toFixed(2)}`;
            let btnCell = row.insertCell(5);
            let editBtn = document.createElement('button'); editBtn.innerText='تعديل'; editBtn.className='btn'; editBtn.style.padding='4px 8px'; editBtn.onclick=()=>loadRecordToInput(rec);
            let delBtn = document.createElement('button'); delBtn.innerText='حذف'; delBtn.className='btn btn-reset'; delBtn.style.padding='4px 8px'; delBtn.onclick=()=>{historyRecords.splice(historyRecords.length-1-idx,1); localStorage.setItem('alanhar_history',JSON.stringify(historyRecords)); loadHistoryTable();};
            btnCell.appendChild(editBtn); btnCell.appendChild(delBtn);
        });
    }
    function loadRecordToInput(rec) {
        document.getElementById('usd-debtor').value = rec.usd.debtor;
        document.getElementById('usd-creditor').value = rec.usd.creditor;
        document.getElementById('eur-debtor').value = rec.eur.debtor;
        document.getElementById('eur-creditor').value = rec.eur.creditor;
        document.getElementById('try-debtor').value = rec.try.debtor;
        document.getElementById('try-creditor').value = rec.try.creditor;
        document.getElementById('saljog-amount-usd').value = rec.saljog.usd.amount;
        document.getElementById('saljog-expense-usd').value = rec.saljog.usd.expense;
        document.getElementById('saljog-profit-usd').value = rec.saljog.usd.profit;
        document.getElementById('saljog-amount-eur').value = rec.saljog.eur.amount;
        document.getElementById('saljog-expense-eur').value = rec.saljog.eur.expense;
        document.getElementById('saljog-profit-eur').value = rec.saljog.eur.profit;
        if(rec.profits){
            document.getElementById('swift-usd').value = rec.profits.swift.usd||0; document.getElementById('swift-eur').value = rec.profits.swift.eur||0;
            document.getElementById('havala-usd').value = rec.profits.havala.usd||0; document.getElementById('havala-eur').value = rec.profits.havala.eur||0;
            document.getElementById('silver-usd').value = rec.profits.silver.usd||0; document.getElementById('silver-eur').value = rec.profits.silver.eur||0;
            document.getElementById('copper-usd').value = rec.profits.copper.usd||0; document.getElementById('copper-eur').value = rec.profits.copper.eur||0;
            document.getElementById('external-usd').value = rec.profits.external.usd||0; document.getElementById('external-eur').value = rec.profits.external.eur||0;
        }
        if(rec.presetExpenses) { presetExpenses = rec.presetExpenses; savePresetsToLocal(); renderPresetExpensesUI(); }
        updateDailyFromInputs();
        switchTab('input');
    }
    function monthlyReport() {
        let month = document.getElementById('month-picker').value;
        if(!month) return;
        let filtered = historyRecords.filter(r=>r.date.startsWith(month));
        let summary = { usdSurplus:0, eurSurplus:0, realSurplusTotal:0, expensesByCurrency:{USD:0,EUR:0,TRY:0} };
        filtered.forEach(r=>{ summary.usdSurplus += r.usd.surplus; summary.eurSurplus += r.eur.surplus; summary.realSurplusTotal += r.realSurplus; r.presetExpenses?.forEach(e=>{ if(e.amount>0) summary.expensesByCurrency[e.currency] += e.amount; }); });
        document.getElementById('monthly-summary').innerHTML = `<div class="summary-grid"><div class="summary-card">إجمالي فائض دولار: $${summary.usdSurplus.toFixed(2)}</div><div class="summary-card">إجمالي فائض يورو: €${summary.eurSurplus.toFixed(2)}</div><div class="summary-card">صافي الربح الحقيقي: $${summary.realSurplusTotal.toFixed(2)}</div><div class="summary-card">إجمالي المصروفات: $${summary.expensesByCurrency.USD.toFixed(2)} / €${summary.expensesByCurrency.EUR.toFixed(2)} / ₺${summary.expensesByCurrency.TRY.toFixed(2)}</div></div>`;
        let editableHtml = `<h4>تعديل المصروفات الشهرية (قابلة للتعديل)</h4><div class="expense-category-grid" id="monthly-editable-list"></div>`;
        document.getElementById('monthly-editable-grid').innerHTML = editableHtml;
        let container = document.getElementById('monthly-editable-list');
        container.innerHTML = '';
        let monthExpenses = {};
        filtered.forEach(r=>{ r.presetExpenses?.forEach(e=>{ if(e.amount>0){ let key=e.nameAr; if(!monthExpenses[key]) monthExpenses[key]={name:e.nameAr, amountUSD:0, amountEUR:0, amountTRY:0}; if(e.currency=='USD') monthExpenses[key].amountUSD+=e.amount; if(e.currency=='EUR') monthExpenses[key].amountEUR+=e.amount; if(e.currency=='TRY') monthExpenses[key].amountTRY+=e.amount; } }); });
        for(let [key,val] of Object.entries(monthExpenses)){
            let div = document.createElement('div'); div.className='expense-item-card';
            div.innerHTML = `<label>${val.name}</label><div class="expense-item-row"><input type="number" class="monthly-edit-usd" data-name="${val.name}" placeholder="USD" value="${val.amountUSD}"><input type="number" class="monthly-edit-eur" data-name="${val.name}" placeholder="EUR" value="${val.amountEUR}"><input type="number" class="monthly-edit-try" data-name="${val.name}" placeholder="TRY" value="${val.amountTRY}"></div>`;
            container.appendChild(div);
        }
        window.monthlyTempData = { filtered, monthExpenses };
    }
    function saveMonthlyEdits() {
        if(!window.monthlyTempData) return;
        let updates = {};
        document.querySelectorAll('.monthly-edit-usd').forEach(inp=>{ let name=inp.dataset.name; if(!updates[name]) updates[name]={}; updates[name].usd=parseFloat(inp.value)||0; });
        document.querySelectorAll('.monthly-edit-eur').forEach(inp=>{ let name=inp.dataset.name; if(!updates[name]) updates[name]={}; updates[name].eur=parseFloat(inp.value)||0; });
        document.querySelectorAll('.monthly-edit-try').forEach(inp=>{ let name=inp.dataset.name; if(!updates[name]) updates[name]={}; updates[name].try=parseFloat(inp.value)||0; });
        for(let rec of window.monthlyTempData.filtered){
            rec.presetExpenses.forEach(exp=>{ if(updates[exp.nameAr]){ if(exp.currency=='USD') exp.amount = updates[exp.nameAr].usd ||0; if(exp.currency=='EUR') exp.amount = updates[exp.nameAr].eur ||0; if(exp.currency=='TRY') exp.amount = updates[exp.nameAr].try ||0; } });
        }
        localStorage.setItem('alanhar_history', JSON.stringify(historyRecords));
        alert("تم حفظ التعديلات الشهرية");
        monthlyReport();
    }
    function switchTab(id){ document.querySelectorAll('.content-section').forEach(s=>s.classList.remove('active')); document.getElementById(id).classList.add('active'); document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active')); document.querySelector(`[data-tab="${id}"]`).classList.add('active'); if(id=='history') loadHistoryTable(); if(id=='monthly') monthlyReport(); }
    document.getElementById('save-data')?.addEventListener('click',saveData);
    document.getElementById('reset-data')?.addEventListener('click',resetData);
    document.getElementById('generate-report')?.addEventListener('click',generateReport);
    document.getElementById('print-report')?.addEventListener('click',()=>{ generateReport(); setTimeout(()=>window.print(),200); });
    document.getElementById('back-to-input')?.addEventListener('click',()=>switchTab('input'));
    document.getElementById('clear-history')?.addEventListener('click',()=>{ if(confirm("مسح الكل؟")){ historyRecords=[]; localStorage.removeItem('alanhar_history'); loadHistoryTable(); } });
    document.getElementById('load-month-report')?.addEventListener('click',monthlyReport);
    document.getElementById('save-monthly-changes')?.addEventListener('click',saveMonthlyEdits);
    document.getElementById('filter-date')?.addEventListener('change',()=>loadHistoryTable());
    document.querySelectorAll('.tab').forEach(t=>t.addEventListener('click',function(){ switchTab(this.dataset.tab); }));
    function attachInputs(){ let ids=['usd-debtor','usd-creditor','eur-debtor','eur-creditor','try-debtor','try-creditor','saljog-amount-usd','saljog-expense-usd','saljog-profit-usd','saljog-amount-eur','saljog-expense-eur','saljog-profit-eur','swift-usd','swift-eur','havala-usd','havala-eur','silver-usd','silver-eur','copper-usd','copper-eur','external-usd','external-eur']; ids.forEach(id=>{ let el=document.getElementById(id); if(el) el.addEventListener('input',updateDailyFromInputs); }); }
    initPresets(); attachInputs(); updateDailyFromInputs(); loadHistoryTable();
</script>
</body>
</html>
