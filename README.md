<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ALANHAR Sistemi - Döviz ve Havale Yönetimi</title>
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
            @page {
                size: A4;
                margin: 1.5cm;
            }

            .no-print {
                display: none !important;
            }

            body {
                background: white;
                padding: 0;
                font-size: 12pt;
            }

            .container {
                max-width: 100%;
                padding: 0;
            }

            .card, .real-surplus-box, .summary-card, .profits-card {
                break-inside: avoid;
                box-shadow: none !important;
                border: 1px solid #ddd !important;
                background: white !important;
            }

            .report-table th {
                background-color: #f0f0f0 !important;
                color: black !important;
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            .summary-box, .profit-category {
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            .positive, .negative {
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            .profits-card {
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            header, footer, .tabs, .actions, .warning, .info-box, .add-expense-btn {
                display: none !important;
            }
        }

        header {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 15px;
        }

        .logo i {
            font-size: 2.8rem;
            margin-left: 15px;
            color: #FFD700;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .subtitle-tr {
            font-size: 1.1rem;
            opacity: 0.8;
            margin-top: 5px;
        }

        .tabs {
            display: flex;
            background-color: #fff;
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
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

        .tab:hover {
            background-color: #f8f9fa;
        }

        .tab.active {
            color: #1a2980;
            border-bottom: 3px solid #1a2980;
            background-color: #f0f7ff;
        }

        .monthly-tab {
            background: linear-gradient(135deg, #8e24aa, #ab47bc);
            color: white;
        }

        .monthly-tab.active {
            color: #8e24aa;
            border-bottom: 3px solid #8e24aa;
            background-color: #f3e5f5;
        }

        .content-section {
            display: none;
            animation: fadeIn 0.5s;
        }

        .content-section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .card {
            background-color: white;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
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

        .card-title i {
            margin-left: 10px;
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

        .label-tr {
            font-size: 0.9rem;
            color: #777;
            font-weight: normal;
        }

        .input-group input, .input-group select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border 0.3s;
        }

        .input-group input:focus, .input-group select:focus {
            outline: none;
            border-color: #1a2980;
            box-shadow: 0 0 0 2px rgba(26, 41, 128, 0.1);
        }

        .result-box {
            padding: 15px;
            border-radius: 8px;
            margin-top: 10px;
            text-align: center;
            font-weight: bold;
            font-size: 1.3rem;
        }

        .positive {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
        }

        .negative {
            background: linear-gradient(135deg, #d32f2f, #b71c1c);
            color: white;
        }

        .btn {
            padding: 14px 25px;
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 7px 14px rgba(26, 41, 128, 0.2);
        }

        .btn i {
            margin-left: 8px;
        }

        .btn-print {
            background: linear-gradient(135deg, #4caf50, #2e7d32);
        }

        .btn-save {
            background: linear-gradient(135deg, #2196f3, #0d47a1);
        }

        .btn-reset {
            background: linear-gradient(135deg, #ff9800, #ef6c00);
        }

        .actions {
            display: flex;
            gap: 15px;
            margin-top: 25px;
            flex-wrap: wrap;
        }

        .expense-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 20px;
        }

        .expense-item {
            flex: 1;
            min-width: 200px;
            background-color: #fff3e0;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #ff9800;
        }

        .expense-total-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
        }

        .expense-total-box {
            flex: 1;
            min-width: 200px;
            background-color: #ffebee;
            padding: 15px;
            border-radius: 8px;
            border: 2px solid #f44336;
            text-align: center;
        }

        .expense-currency {
            font-weight: bold;
            font-size: 1.2rem;
            color: #c62828;
            margin-top: 5px;
        }

        .report-container {
            overflow-x: auto;
        }

        .report-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        .report-table th {
            background-color: #1a2980;
            color: white;
            padding: 15px;
            text-align: right;
        }

        .report-table td {
            padding: 12px 15px;
            border-bottom: 1px solid #eee;
        }

        .report-table tr:nth-child(even) {
            background-color: #f8f9fa;
        }

        .report-table tr:hover {
            background-color: #f0f7ff;
        }

        .report-summary {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 30px;
        }

        .summary-box {
            flex: 1;
            min-width: 250px;
            padding: 20px;
            border-radius: 10px;
            color: white;
            text-align: center;
        }

        .summary-box.usd {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
        }

        .summary-box.eur {
            background: linear-gradient(135deg, #004d40, #00796b);
        }

        .summary-box.try {
            background: linear-gradient(135deg, #b71c1c, #d32f2f);
        }

        .summary-value {
            font-size: 2rem;
            margin: 10px 0;
            font-weight: bold;
        }

        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #666;
            border-top: 1px solid #eee;
        }

        .warning {
            background-color: #fff3e0;
            padding: 15px;
            border-radius: 8px;
            border-right: 5px solid #ff9800;
            margin-bottom: 20px;
        }

        .info-box {
            background-color: #e3f2fd;
            padding: 10px 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            border-right: 4px solid #2196f3;
        }

        .add-expense-btn {
            background-color: #f0f7ff;
            border: 2px dashed #1a2980;
            color: #1a2980;
            padding: 12px;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            margin-top: 10px;
            transition: all 0.3s;
        }

        .add-expense-btn:hover {
            background-color: #e1edff;
        }

        .report-header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #1a2980;
        }

        .report-header h2 {
            color: #1a2980;
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        .report-header .date {
            font-size: 1.2rem;
            color: #666;
        }

        /* قسم حساب الصلج */
        .saljog-box {
            background: linear-gradient(135deg, #b3e5fc, #81d4fa);
            border-left: 5px solid #0288d1;
        }

        .saljog-title {
            color: #01579b;
        }

        .saljog-icon {
            background-color: #0288d1;
        }

        /* مصروفات وفوائد */
        .expense-profit-row {
            display: flex;
            gap: 15px;
            margin: 10px 0;
        }

        .expense-profit-item {
            flex: 1;
            background: white;
            padding: 10px;
            border-radius: 8px;
        }

        .expense-profit-item input {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .item-total-box {
            background: #4caf50;
            color: white;
            padding: 10px;
            border-radius: 6px;
            text-align: center;
            font-weight: bold;
            margin-top: 10px;
        }

        .real-surplus-box {
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
            border: 2px solid #4caf50;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            text-align: center;
        }

        .real-surplus-value {
            font-size: 1.8rem;
            font-weight: bold;
            color: #2e7d32;
            margin: 10px 0;
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

        .summary-card-title {
            font-size: 1.1rem;
            color: #666;
            margin-bottom: 10px;
        }

        .summary-card-value {
            font-size: 1.8rem;
            font-weight: bold;
        }

        .summary-card.usd {
            border-top: 4px solid #1a2980;
        }

        .summary-card.saljog {
            border-top: 4px solid #0288d1;
        }

        .summary-card.total {
            border: 2px solid #4caf50;
        }

        /* قسم الأرباح اليومية الجديد */
        .profits-card {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            border: 2px solid #8e24aa;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 25px;
        }

        .profits-title {
            color: #8e24aa;
            font-size: 1.4rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #ce93d8;
            display: flex;
            align-items: center;
        }

        .profits-title i {
            margin-left: 10px;
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
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            border-right: 4px solid #8e24aa;
        }

        .profit-category-title {
            font-weight: bold;
            color: #8e24aa;
            margin-bottom: 15px;
            font-size: 1.2rem;
            border-bottom: 1px solid #eee;
            padding-bottom: 5px;
        }

        .profit-row {
            display: flex;
            gap: 15px;
            margin-bottom: 10px;
        }

        .profit-field {
            flex: 1;
        }

        .profit-field label {
            display: block;
            font-size: 0.9rem;
            color: #666;
            margin-bottom: 5px;
        }

        .profit-field input {
            width: 100%;
            padding: 8px 10px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 0.95rem;
        }

        .profit-field input:focus {
            outline: none;
            border-color: #8e24aa;
            box-shadow: 0 0 0 2px rgba(142, 36, 170, 0.1);
        }

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

        .profit-currency-row {
            display: flex;
            justify-content: space-around;
            margin-top: 10px;
            padding: 10px;
            background: #f8f9fa;
            border-radius: 6px;
        }

        .profit-currency-item {
            text-align: center;
        }

        .profit-currency-label {
            font-size: 0.9rem;
            color: #666;
        }

        .profit-currency-value {
            font-size: 1.3rem;
            font-weight: bold;
            color: #8e24aa;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-money-check-alt"></i>
                <div>
                    <h1>نظام ALANHAR - ALANHAR Sistemi</h1>
                    <div class="subtitle">نظام متطور لإدارة محلات الصرافة والحوالات</div>
                    <div class="subtitle-tr">Döviz ve Havale Yönetimi için Gelişmiş Sistem</div>
                </div>
            </div>
        </header>

        <div class="tabs no-print">
            <div class="tab active" data-tab="input">
                <i class="fas fa-calculator"></i> إدخال البيانات اليومية / Günlük Veri Girişi
            </div>
            <div class="tab" data-tab="report">
                <i class="fas fa-chart-line"></i> التقرير اليومي / Günlük Rapor
            </div>
            <div class="tab" data-tab="history">
                <i class="fas fa-history"></i> السجلات السابقة / Önceki Kayıtlar
            </div>
        </div>

        <!-- قسم إدخال البيانات اليومية -->
        <div id="input" class="content-section active">
            <div class="warning no-print">
                <i class="fas fa-exclamation-circle"></i>
                <strong>ملاحظة / Not:</strong> يرجى إدخال جميع البيانات المطلوبة لتوليد تقرير يومي كامل. / Lütfen tam bir günlük rapor oluşturmak için tüm gerekli verileri girin.
            </div>

            <div class="info-box">
                <p><strong>تفسير:</strong> الفائض = المدين (الخروج) - الدائن (الدخول). إذا كانت النتيجة موجبة فهذا ربح (أزرق)، وإذا كانت سالبة فهذا خسارة (أحمر).</p>
                <p><strong>الفائض الحقيقي = فائض الدولار - مجموع حساب الصلج</strong></p>
                <p><strong>Açıklama:</strong> Gerçek Kar/Zarar = Dolar Kar/Zarar - Saljoğ Toplam</p>
            </div>

            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-money-bill-wave"></i> إدخال المدين والدائن / Borçlu ve Alacaklı Girişi</span>
                </h2>

                <div class="currency-container">
                    <!-- الدولار الأمريكي -->
                    <div class="currency-box">
                        <div class="currency-title">
                            <div class="currency-icon">$</div>
                            <div>الدولار الأمريكي (USD) / Amerikan Doları</div>
                        </div>

                        <div class="input-group">
                            <label for="usd-debtor">المدين (الخروج) / Borçlu (Çıkış)</label>
                            <div class="label-tr">Çıkan para miktarı</div>
                            <input type="number" id="usd-debtor" placeholder="أدخل قيمة المدين بالدولار / Dolar cinsinden borçlu değerini girin" step="0.01" min="0">
                        </div>

                        <div class="input-group">
                            <label for="usd-creditor">الدائن (الدخول) / Alacaklı (Giriş)</label>
                            <div class="label-tr">Giren para miktarı</div>
                            <input type="number" id="usd-creditor" placeholder="أدخل قيمة الدائن بالدولار / Dolar cinsinden alacaklı değerini girin" step="0.01" min="0">
                        </div>

                        <div id="usd-surplus" class="result-box">
                            الفائض / Kar-Zarar: $0.00
                        </div>
                    </div>

                    <!-- اليورو -->
                    <div class="currency-box">
                        <div class="currency-title">
                            <div class="currency-icon">€</div>
                            <div>اليورو الأوروبي (EUR) / Euro</div>
                        </div>

                        <div class="input-group">
                            <label for="eur-debtor">المدين (الخروج) / Borçlu (Çıkış)</label>
                            <div class="label-tr">Çıkan para miktarı</div>
                            <input type="number" id="eur-debtor" placeholder="أدخل قيمة المدين باليورو / Euro cinsinden borçlu değerini girin" step="0.01" min="0">
                        </div>

                        <div class="input-group">
                            <label for="eur-creditor">الدائن (الدخول) / Alacaklı (Giriş)</label>
                            <div class="label-tr">Giren para miktarı</div>
                            <input type="number" id="eur-creditor" placeholder="أدخل قيمة الدائن باليورو / Euro cinsinden alacaklı değerini girin" step="0.01" min="0">
                        </div>

                        <div id="eur-surplus" class="result-box">
                            الفائض / Kar-Zarar: €0.00
                        </div>
                    </div>

                    <!-- الليرة التركية -->
                    <div class="currency-box">
                        <div class="currency-title">
                            <div class="currency-icon">₺</div>
                            <div>الليرة التركية (TRY) / Türk Lirası</div>
                        </div>

                        <div class="input-group">
                            <label for="try-debtor">المدين (الخروج) / Borçlu (Çıkış)</label>
                            <div class="label-tr">Çıkan para miktarı</div>
                            <input type="number" id="try-debtor" placeholder="أدخل قيمة المدين بالليرة / Lira cinsinden borçlu değerini girin" step="0.01" min="0">
                        </div>

                        <div class="input-group">
                            <label for="try-creditor">الدائن (الدخول) / Alacaklı (Giriş)</label>
                            <div class="label-tr">Giren para miktarı</div>
                            <input type="number" id="try-creditor" placeholder="أدخل قيمة الدائن بالليرة / Lira cinsinden alacaklı değerini girin" step="0.01" min="0">
                        </div>

                        <div id="try-surplus" class="result-box">
                            الفائض / Kar-Zarar: ₺0.00
                        </div>
                    </div>
                </div>
            </div>

            <!-- قسم حساب الصلج -->
            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-wallet"></i> حساب الصلج (Saljoğ) - الرصيد والمصروف والمكسب</span>
                </h2>
                <div class="currency-box saljog-box">
                    <div class="currency-title saljog-title">
                        <div class="currency-icon saljog-icon">
                            <i class="fas fa-wallet"></i>
                        </div>
                        <div>حساب الصلج (Saljoğ Hesapları)</div>
                    </div>

                    <div class="input-group">
                        <label for="saljog-amount">الرصيد الأساسي ($) / Temel Bakiye ($)</label>
                        <div class="label-tr">Saljoğ hesabındaki temel para miktarı</div>
                        <input type="number" id="saljog-amount" placeholder="أدخل رصيد حساب الصلج بالدولار / Saljoğ hesabındaki dolar miktarını girin" step="0.01" min="0">
                    </div>

                    <div class="expense-profit-row">
                        <div class="expense-profit-item">
                            <label for="saljog-expense">المصروف ($) / Gider ($)</label>
                            <input type="number" id="saljog-expense" placeholder="مصروف من الصلج" step="0.01" min="0">
                        </div>
                        <div class="expense-profit-item">
                            <label for="saljog-profit">المكسب ($) / Kâr ($)</label>
                            <input type="number" id="saljog-profit" placeholder="مكسب للصلج" step="0.01" min="0">
                        </div>
                    </div>

                    <div id="saljog-total" class="item-total-box">
                        مجموع الصلج: $0.00 (الرصيد - المصروف + المكسب)
                    </div>
                </div>
            </div>

            <!-- الفائض الحقيقي (فائض الدولار - مجموع الصلج) -->
            <div class="real-surplus-box">
                <div style="font-size: 1.2rem; margin-bottom: 15px;">
                    <i class="fas fa-calculator"></i> الفائض الحقيقي = فائض الدولار - مجموع الصلج
                </div>
                <div class="summary-grid">
                    <div class="summary-card usd">
                        <div class="summary-card-title">فائض الدولار</div>
                        <div class="summary-card-value" id="display-usd-surplus">$0.00</div>
                    </div>
                    <div class="summary-card saljog">
                        <div class="summary-card-title">مجموع الصلج</div>
                        <div class="summary-card-value" id="display-saljog-total">$0.00</div>
                    </div>
                    <div class="summary-card total">
                        <div class="summary-card-title">الفائض الحقيقي</div>
                        <div class="summary-card-value" id="real-surplus">$0.00</div>
                    </div>
                </div>
            </div>

            <!-- قسم الأرباح اليومية الجديد -->
            <div class="profits-card">
                <div class="profits-title">
                    <i class="fas fa-coins"></i> الأرباح اليومية (للمعلومية) / Günlük Kârlar (Bilgi İçin)
                </div>

                <div class="profits-grid">
                    <!-- أرباح Swift -->
                    <div class="profit-category">
                        <div class="profit-category-title">
                            <i class="fas fa-bolt"></i> أرباح Swift / Swift Kârları
                        </div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <label>الدولار ($) / USD</label>
                                <input type="number" id="swift-profit-usd" placeholder="0.00" step="0.01" min="0">
                            </div>
                            <div class="profit-field">
                                <label>اليورو (€) / EUR</label>
                                <input type="number" id="swift-profit-eur" placeholder="0.00" step="0.01" min="0">
                            </div>
                        </div>
                    </div>

                    <!-- أرباح Havala -->
                    <div class="profit-category">
                        <div class="profit-category-title">
                            <i class="fas fa-exchange-alt"></i> أرباح Havala / Havale Kârları
                        </div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <label>الدولار ($) / USD</label>
                                <input type="number" id="havala-profit-usd" placeholder="0.00" step="0.01" min="0">
                            </div>
                            <div class="profit-field">
                                <label>اليورو (€) / EUR</label>
                                <input type="number" id="havala-profit-eur" placeholder="0.00" step="0.01" min="0">
                            </div>
                        </div>
                    </div>

                    <!-- أرباح الفضة -->
                    <div class="profit-category">
                        <div class="profit-category-title">
                            <i class="fas fa-gem"></i> أرباح الفضة / Gümüş Kârları
                        </div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <label>الدولار ($) / USD</label>
                                <input type="number" id="silver-profit-usd" placeholder="0.00" step="0.01" min="0">
                            </div>
                            <div class="profit-field">
                                <label>اليورو (€) / EUR</label>
                                <input type="number" id="silver-profit-eur" placeholder="0.00" step="0.01" min="0">
                            </div>
                        </div>
                    </div>

                    <!-- أرباح النحاس -->
                    <div class="profit-category">
                        <div class="profit-category-title">
                            <i class="fas fa-cubes"></i> أرباح النحاس / Bakır Kârları
                        </div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <label>الدولار ($) / USD</label>
                                <input type="number" id="copper-profit-usd" placeholder="0.00" step="0.01" min="0">
                            </div>
                            <div class="profit-field">
                                <label>اليورو (€) / EUR</label>
                                <input type="number" id="copper-profit-eur" placeholder="0.00" step="0.01" min="0">
                            </div>
                        </div>
                    </div>

                    <!-- أرباح خارجية -->
                    <div class="profit-category">
                        <div class="profit-category-title">
                            <i class="fas fa-globe"></i> أرباح خارجية / Dış Kârlar
                        </div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <label>الدولار ($) / USD</label>
                                <input type="number" id="external-profit-usd" placeholder="0.00" step="0.01" min="0">
                            </div>
                            <div class="profit-field">
                                <label>اليورو (€) / EUR</label>
                                <input type="number" id="external-profit-eur" placeholder="0.00" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                </div>

                <!-- إجمالي الأرباح -->
                <div class="profit-total-box" id="total-profits">
                    إجمالي الأرباح: $0.00 / €0.00
                </div>

                <div class="profit-currency-row">
                    <div class="profit-currency-item">
                        <div class="profit-currency-label">إجمالي الدولار</div>
                        <div class="profit-currency-value" id="total-profit-usd">$0.00</div>
                    </div>
                    <div class="profit-currency-item">
                        <div class="profit-currency-label">إجمالي اليورو</div>
                        <div class="profit-currency-value" id="total-profit-eur">€0.00</div>
                    </div>
                </div>
            </div>

            <!-- المصروفات اليومية -->
            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-receipt"></i> المصروفات اليومية / Günlük Giderler</span>
                </h2>

                <div id="expenses-container">
                    <div class="expense-container" id="expenses-list">
                        <div class="expense-item" id="expense-item-1">
                            <div class="input-group">
                                <label for="expense-name-1">وصف المصروف / Gider Açıklaması</label>
                                <input type="text" id="expense-name-1" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                            </div>

                            <div class="input-group">
                                <label for="expense-amount-1">القيمة / Tutar</label>
                                <input type="number" id="expense-amount-1" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                            </div>

                            <div class="input-group">
                                <label for="expense-currency-1">العملة / Para Birimi</label>
                                <select id="expense-currency-1">
                                    <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                                    <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                                    <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                                </select>
                            </div>

                            <button class="btn btn-reset remove-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="1">
                                <i class="fas fa-trash"></i> حذف / Sil
                            </button>
                        </div>
                    </div>
                </div>

                <div class="add-expense-btn no-print" id="add-expense">
                    <i class="fas fa-plus-circle"></i> إضافة مصروف جديد / Yeni Gider Ekle
                </div>

                <div id="total-expense" class="expense-total-container"></div>
            </div>

            <div class="actions no-print">
                <button class="btn btn-save" id="save-data">
                    <i class="fas fa-save"></i> حفظ البيانات / Verileri Kaydet
                </button>
                <button class="btn btn-print" id="generate-report">
                    <i class="fas fa-file-alt"></i> توليد التقرير / Rapor Oluştur
                </button>
                <button class="btn btn-reset" id="reset-data">
                    <i class="fas fa-redo"></i> مسح البيانات / Verileri Temizle
                </button>
            </div>
        </div>

        <!-- قسم التقرير اليومي -->
        <div id="report" class="content-section">
            <div class="report-header">
                <h2>تقرير يومي مفصل - نظام ALANHAR</h2>
                <div class="date" id="report-date"></div>
                <div class="subtitle-tr">Detaylı Günlük Rapor - ALANHAR Sistemi</div>
            </div>

            <!-- ملخص الفائض من المدين والدائن -->
            <div class="card">
                <h3 class="card-title">
                    <span><i class="fas fa-chart-line"></i> فائض العملات (المدين - الدائن) / Döviz Kar-Zarar (Borçlu - Alacaklı)</span>
                </h3>
                <div class="report-summary">
                    <div class="summary-box usd">
                        <div class="summary-label">الدولار / USD</div>
                        <div class="summary-value" id="report-usd-surplus">$0.00</div>
                    </div>
                    <div class="summary-box eur">
                        <div class="summary-label">اليورو / EUR</div>
                        <div class="summary-value" id="report-eur-surplus">€0.00</div>
                    </div>
                    <div class="summary-box try">
                        <div class="summary-label">الليرة / TRY</div>
                        <div class="summary-value" id="report-try-surplus">₺0.00</div>
                    </div>
                </div>

                <div class="report-container">
                    <table class="report-table">
                        <thead>
                            <tr>
                                <th>العملة / Para Birimi</th>
                                <th>المدين (الخروج) / Borçlu (Çıkış)</th>
                                <th>الدائن (الدخول) / Alacaklı (Giriş)</th>
                                <th>الفائض / Kar-Zarar</th>
                                <th>الحالة / Durum</th>
                            </tr>
                        </thead>
                        <tbody id="report-table-body"></tbody>
                    </table>
                </div>
            </div>

            <!-- قسم حساب الصلج في التقرير -->
            <div class="card" style="background: linear-gradient(135deg, #b3e5fc, #81d4fa);">
                <h3 class="card-title" style="color: #01579b;">
                    <span><i class="fas fa-wallet"></i> تقرير حساب الصلج / Saljoğ Raporu</span>
                </h3>
                
                <div class="summary-grid">
                    <div class="summary-card">
                        <div class="summary-card-title">الرصيد الأساسي / Temel Bakiye</div>
                        <div class="summary-card-value" style="color: #0288d1;" id="report-saljog-amount">$0.00</div>
                    </div>
                    <div class="summary-card">
                        <div class="summary-card-title">المصروف / Gider</div>
                        <div class="summary-card-value" style="color: #d32f2f;" id="report-saljog-expense">$0.00</div>
                    </div>
                    <div class="summary-card">
                        <div class="summary-card-title">المكسب / Kâr</div>
                        <div class="summary-card-value" style="color: #4caf50;" id="report-saljog-profit">$0.00</div>
                    </div>
                    <div class="summary-card total">
                        <div class="summary-card-title">مجموع الصلج / Saljoğ Toplam</div>
                        <div class="summary-card-value" style="color: #0288d1;" id="report-saljog-total">$0.00</div>
                    </div>
                </div>
            </div>

            <!-- المجموع الكلي (فائض الدولار - مجموع الصلج) -->
            <div class="real-surplus-box">
                <h3 style="margin-bottom: 15px;">الفائض الحقيقي = فائض الدولار - مجموع الصلج / Gerçek Kar-Zarar = Dolar Kar-Zarar - Saljoğ Toplam</h3>
                <div class="summary-grid">
                    <div class="summary-card usd">
                        <div class="summary-card-title">فائض الدولار / Dolar Kar-Zarar</div>
                        <div class="summary-card-value" id="report-display-usd-surplus">$0.00</div>
                    </div>
                    <div class="summary-card saljog">
                        <div class="summary-card-title">مجموع الصلج / Saljoğ Toplam</div>
                        <div class="summary-card-value" id="report-display-saljog-total">$0.00</div>
                    </div>
                    <div class="summary-card total">
                        <div class="summary-card-title">الفائض الحقيقي / Gerçek Kar-Zarar</div>
                        <div class="summary-card-value" id="report-real-surplus">$0.00</div>
                    </div>
                </div>
            </div>

            <!-- قسم الأرباح اليومية في التقرير -->
            <div class="profits-card">
                <div class="profits-title">
                    <i class="fas fa-coins"></i> الأرباح اليومية (للمعلومية) / Günlük Kârlar (Bilgi İçin)
                </div>

                <div class="profits-grid">
                    <!-- أرباح Swift -->
                    <div class="profit-category">
                        <div class="profit-category-title">أرباح Swift / Swift Kârları</div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <span id="report-swift-usd">$0.00</span>
                            </div>
                            <div class="profit-field">
                                <span id="report-swift-eur">€0.00</span>
                            </div>
                        </div>
                    </div>

                    <!-- أرباح Havala -->
                    <div class="profit-category">
                        <div class="profit-category-title">أرباح Havala / Havale Kârları</div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <span id="report-havala-usd">$0.00</span>
                            </div>
                            <div class="profit-field">
                                <span id="report-havala-eur">€0.00</span>
                            </div>
                        </div>
                    </div>

                    <!-- أرباح الفضة -->
                    <div class="profit-category">
                        <div class="profit-category-title">أرباح الفضة / Gümüş Kârları</div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <span id="report-silver-profit-usd">$0.00</span>
                            </div>
                            <div class="profit-field">
                                <span id="report-silver-profit-eur">€0.00</span>
                            </div>
                        </div>
                    </div>

                    <!-- أرباح النحاس -->
                    <div class="profit-category">
                        <div class="profit-category-title">أرباح النحاس / Bakır Kârları</div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <span id="report-copper-profit-usd">$0.00</span>
                            </div>
                            <div class="profit-field">
                                <span id="report-copper-profit-eur">€0.00</span>
                            </div>
                        </div>
                    </div>

                    <!-- أرباح خارجية -->
                    <div class="profit-category">
                        <div class="profit-category-title">أرباح خارجية / Dış Kârlar</div>
                        <div class="profit-row">
                            <div class="profit-field">
                                <span id="report-external-profit-usd">$0.00</span>
                            </div>
                            <div class="profit-field">
                                <span id="report-external-profit-eur">€0.00</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="profit-total-box" id="report-total-profits">
                    إجمالي الأرباح: $0.00 / €0.00
                </div>
            </div>

            <!-- المصروفات اليومية -->
            <div class="card">
                <h3 class="card-title">
                    <span><i class="fas fa-receipt"></i> المصروفات اليومية / Günlük Giderler</span>
                </h3>
                <div class="report-container">
                    <table class="report-table">
                        <thead>
                            <tr>
                                <th>وصف المصروف / Gider Açıklaması</th>
                                <th>القيمة / Tutar</th>
                                <th>العملة / Para Birimi</th>
                            </tr>
                        </thead>
                        <tbody id="expenses-report-body"></tbody>
                    </table>
                </div>
                <div id="report-expense-total" class="expense-total-container"></div>
            </div>

            <div class="actions no-print">
                <button class="btn btn-print" id="print-report">
                    <i class="fas fa-print"></i> طباعة التقرير / Raporu Yazdır
                </button>
                <button class="btn btn-save" id="back-to-input">
                    <i class="fas fa-edit"></i> العودة للإدخال / Girişe Dön
                </button>
            </div>
        </div>

        <!-- قسم السجلات السابقة -->
        <div id="history" class="content-section">
            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-history"></i> سجلات الأيام السابقة / Önceki Gün Kayıtları</span>
                </h2>

                <div class="input-group no-print" style="max-width: 300px; margin-bottom: 20px;">
                    <label for="filter-date">فلترة حسب التاريخ / Tarihe Göre Filtrele</label>
                    <input type="date" id="filter-date">
                </div>

                <div class="report-container">
                    <table class="report-table">
                        <thead>
                            <tr>
                                <th>التاريخ / Tarih</th>
                                <th>فائض الدولار / Dolar Kar-Zarar</th>
                                <th>فائض اليورو / Euro Kar-Zarar</th>
                                <th>فائض الليرة / Lira Kar-Zarar</th>
                                <th>رصيد الصلج / Saljoğ Bakiyesi</th>
                                <th>مصروف الصلج / Saljoğ Gider</th>
                                <th>مكسب الصلج / Saljoğ Kâr</th>
                                <th>مجموع الصلج / Saljoğ Toplam</th>
                                <th>الفائض الحقيقي / Gerçek Kar-Zarar</th>
                                <th>إجمالي الأرباح / Toplam Kâr</th>
                                <th>المصروفات / Giderler</th>
                                <th class="no-print">الإجراءات / İşlemler</th>
                            </tr>
                        </thead>
                        <tbody id="history-table-body">
                            <tr id="no-history">
                                <td colspan="12" style="text-align: center; padding: 30px;">لا توجد سجلات سابقة. ابدأ بإدخال بيانات اليوم. / Önceki kayıt yok. Bugünün verilerini girmeye başlayın.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <div class="actions no-print">
                    <button class="btn btn-reset" id="clear-history">
                        <i class="fas fa-trash-alt"></i> مسح السجلات / Kayıtları Temizle
                    </button>
                </div>
            </div>
        </div>

        <footer class="no-print">
            <p>نظام ALANHAR لإدارة محلات الصرافة والحوالات &copy; 2023</p>
            <p>ALANHAR Sistemi - Döviz ve Havale Yönetimi &copy; 2023</p>
        </footer>
    </div>

    <script>
        // بيانات التطبيق
        let appData = {
            usd: { debtor: 0, creditor: 0, surplus: 0 },
            eur: { debtor: 0, creditor: 0, surplus: 0 },
            try: { debtor: 0, creditor: 0, surplus: 0 },
            saljog: { amount: 0, expense: 0, profit: 0, total: 0 },
            realSurplus: 0,
            profits: {
                swift: { usd: 0, eur: 0 },
                havana: { usd: 0, eur: 0 },
                silver: { usd: 0, eur: 0 },
                copper: { usd: 0, eur: 0 },
                external: { usd: 0, eur: 0 },
                total: { usd: 0, eur: 0 }
            },
            expenses: [],
            date: new Date().toISOString().split('T')[0],
            timestamp: new Date().getTime()
        };

        let historyRecords = JSON.parse(localStorage.getItem('alanhar_history')) || [];
        let expenseCounter = 1;

        document.addEventListener('DOMContentLoaded', function() {
            initializeApp();
            setupEventListeners();
            loadHistory();
            updateCalculations();
        });

        function initializeApp() {
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('report-date').textContent = `التاريخ: ${formatDate(today)} / Tarih: ${formatDate(today)}`;
        }

        function setupEventListeners() {
            document.getElementById('add-expense').addEventListener('click', addNewExpense);
            document.getElementById('save-data').addEventListener('click', saveData);
            document.getElementById('generate-report').addEventListener('click', generateReport);
            document.getElementById('print-report').addEventListener('click', printDailyReport);
            document.getElementById('reset-data').addEventListener('click', resetData);
            document.getElementById('back-to-input').addEventListener('click', () => switchTab('input'));
            document.getElementById('clear-history').addEventListener('click', clearHistory);
            document.getElementById('filter-date').addEventListener('change', filterHistory);

            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });

            setupInputListeners();
        }

        function setupInputListeners() {
            const inputs = [
                'usd-debtor', 'usd-creditor',
                'eur-debtor', 'eur-creditor',
                'try-debtor', 'try-creditor',
                'saljog-amount', 'saljog-expense', 'saljog-profit',
                'swift-profit-usd', 'swift-profit-eur',
                'havala-profit-usd', 'havala-profit-eur',
                'silver-profit-usd', 'silver-profit-eur',
                'copper-profit-usd', 'copper-profit-eur',
                'external-profit-usd', 'external-profit-eur'
            ];

            inputs.forEach(id => {
                const input = document.getElementById(id);
                if (input) {
                    input.addEventListener('input', updateCalculations);
                }
            });

            for (let i = 1; i <= expenseCounter; i++) {
                setupExpenseInputListeners(i);
            }
        }

        function setupExpenseInputListeners(id) {
            const nameInput = document.getElementById(`expense-name-${id}`);
            const amountInput = document.getElementById(`expense-amount-${id}`);
            const currencySelect = document.getElementById(`expense-currency-${id}`);

            if (nameInput) nameInput.addEventListener('input', updateExpensesTotal);
            if (amountInput) amountInput.addEventListener('input', updateExpensesTotal);
            if (currencySelect) currencySelect.addEventListener('change', updateExpensesTotal);
        }

        function updateCalculations() {
            // دولار
            const usdDebtor = parseFloat(document.getElementById('usd-debtor').value) || 0;
            const usdCreditor = parseFloat(document.getElementById('usd-creditor').value) || 0;
            const usdSurplus = usdDebtor - usdCreditor;
            appData.usd = { debtor: usdDebtor, creditor: usdCreditor, surplus: usdSurplus };

            const usdSurplusElement = document.getElementById('usd-surplus');
            usdSurplusElement.textContent = `الفائض / Kar-Zarar: $${formatNumber(usdSurplus)}`;
            usdSurplusElement.className = 'result-box ' + (usdSurplus >= 0 ? 'positive' : 'negative');

            // يورو
            const eurDebtor = parseFloat(document.getElementById('eur-debtor').value) || 0;
            const eurCreditor = parseFloat(document.getElementById('eur-creditor').value) || 0;
            const eurSurplus = eurDebtor - eurCreditor;
            appData.eur = { debtor: eurDebtor, creditor: eurCreditor, surplus: eurSurplus };

            const eurSurplusElement = document.getElementById('eur-surplus');
            eurSurplusElement.textContent = `الفائض / Kar-Zarar: €${formatNumber(eurSurplus)}`;
            eurSurplusElement.className = 'result-box ' + (eurSurplus >= 0 ? 'positive' : 'negative');

            // ليرة
            const tryDebtor = parseFloat(document.getElementById('try-debtor').value) || 0;
            const tryCreditor = parseFloat(document.getElementById('try-creditor').value) || 0;
            const trySurplus = tryDebtor - tryCreditor;
            appData.try = { debtor: tryDebtor, creditor: tryCreditor, surplus: trySurplus };

            const trySurplusElement = document.getElementById('try-surplus');
            trySurplusElement.textContent = `الفائض / Kar-Zarar: ₺${formatNumber(trySurplus)}`;
            trySurplusElement.className = 'result-box ' + (trySurplus >= 0 ? 'positive' : 'negative');

            // حساب الصلج
            const saljogAmount = parseFloat(document.getElementById('saljog-amount').value) || 0;
            const saljogExpense = parseFloat(document.getElementById('saljog-expense').value) || 0;
            const saljogProfit = parseFloat(document.getElementById('saljog-profit').value) || 0;
            const saljogTotal = saljogAmount - saljogExpense + saljogProfit;
            appData.saljog = { amount: saljogAmount, expense: saljogExpense, profit: saljogProfit, total: saljogTotal };

            document.getElementById('saljog-total').textContent = `مجموع الصلج: $${formatNumber(saljogTotal)} (الرصيد - المصروف + المكسب)`;

            // الأرباح
            const swiftProfitUSD = parseFloat(document.getElementById('swift-profit-usd').value) || 0;
            const swiftProfitEUR = parseFloat(document.getElementById('swift-profit-eur').value) || 0;
            const havanaProfitUSD = parseFloat(document.getElementById('havala-profit-usd').value) || 0;
            const havanaProfitEUR = parseFloat(document.getElementById('havala-profit-eur').value) || 0;
            const silverProfitUSD = parseFloat(document.getElementById('silver-profit-usd').value) || 0;
            const silverProfitEUR = parseFloat(document.getElementById('silver-profit-eur').value) || 0;
            const copperProfitUSD = parseFloat(document.getElementById('copper-profit-usd').value) || 0;
            const copperProfitEUR = parseFloat(document.getElementById('copper-profit-eur').value) || 0;
            const externalProfitUSD = parseFloat(document.getElementById('external-profit-usd').value) || 0;
            const externalProfitEUR = parseFloat(document.getElementById('external-profit-eur').value) || 0;

            const totalProfitUSD = swiftProfitUSD + havanaProfitUSD + silverProfitUSD + copperProfitUSD + externalProfitUSD;
            const totalProfitEUR = swiftProfitEUR + havanaProfitEUR + silverProfitEUR + copperProfitEUR + externalProfitEUR;

            appData.profits = {
                swift: { usd: swiftProfitUSD, eur: swiftProfitEUR },
                havana: { usd: havanaProfitUSD, eur: havanaProfitEUR },
                silver: { usd: silverProfitUSD, eur: silverProfitEUR },
                copper: { usd: copperProfitUSD, eur: copperProfitEUR },
                external: { usd: externalProfitUSD, eur: externalProfitEUR },
                total: { usd: totalProfitUSD, eur: totalProfitEUR }
            };

            // تحديث عرض إجمالي الأرباح
            document.getElementById('total-profit-usd').textContent = `$${formatNumber(totalProfitUSD)}`;
            document.getElementById('total-profit-eur').textContent = `€${formatNumber(totalProfitEUR)}`;
            document.getElementById('total-profits').innerHTML = `إجمالي الأرباح: $${formatNumber(totalProfitUSD)} / €${formatNumber(totalProfitEUR)}`;

            // الفائض الحقيقي = فائض الدولار - مجموع الصلج
            appData.realSurplus = usdSurplus - saljogTotal;

            // تحديث العرض
            document.getElementById('display-usd-surplus').textContent = `$${formatNumber(usdSurplus)}`;
            document.getElementById('display-saljog-total').textContent = `$${formatNumber(saljogTotal)}`;
            document.getElementById('real-surplus').textContent = `$${formatNumber(appData.realSurplus)}`;

            updateExpensesTotal();
        }

        function updateExpensesTotal() {
            let totalExpenseUSD = 0, totalExpenseEUR = 0, totalExpenseTRY = 0;
            appData.expenses = [];

            for (let i = 1; i <= expenseCounter; i++) {
                const nameInput = document.getElementById(`expense-name-${i}`);
                const amountInput = document.getElementById(`expense-amount-${i}`);
                const currencySelect = document.getElementById(`expense-currency-${i}`);

                if (nameInput && amountInput && currencySelect) {
                    const name = nameInput.value;
                    const amount = parseFloat(amountInput.value) || 0;
                    const currency = currencySelect.value;

                    if (name && amount > 0) {
                        appData.expenses.push({ name, amount, currency });

                        if (currency === 'USD') totalExpenseUSD += amount;
                        else if (currency === 'EUR') totalExpenseEUR += amount;
                        else if (currency === 'TRY') totalExpenseTRY += amount;
                    }
                }
            }

            const container = document.getElementById('total-expense');
            if (!container) return;

            container.innerHTML = '';

            if (totalExpenseUSD > 0) {
                container.innerHTML += `
                    <div class="expense-total-box">
                        <div>إجمالي مصروفات الدولار / Toplam Dolar Giderler</div>
                        <div class="expense-currency">$${formatNumber(totalExpenseUSD)}</div>
                    </div>
                `;
            }

            if (totalExpenseEUR > 0) {
                container.innerHTML += `
                    <div class="expense-total-box">
                        <div>إجمالي مصروفات اليورو / Toplam Euro Giderler</div>
                        <div class="expense-currency">€${formatNumber(totalExpenseEUR)}</div>
                    </div>
                `;
            }

            if (totalExpenseTRY > 0) {
                container.innerHTML += `
                    <div class="expense-total-box">
                        <div>إجمالي مصروفات الليرة / Toplam Lira Giderler</div>
                        <div class="expense-currency">₺${formatNumber(totalExpenseTRY)}</div>
                    </div>
                `;
            }

            if (totalExpenseUSD === 0 && totalExpenseEUR === 0 && totalExpenseTRY === 0) {
                container.innerHTML = `
                    <div class="expense-total-box">
                        <div>لا توجد مصروفات مسجلة / Kayıtlı gider yok</div>
                        <div class="expense-currency">$0.00 / €0.00 / ₺0.00</div>
                    </div>
                `;
            }
        }

        function printDailyReport() {
            if (!document.getElementById('report').classList.contains('active')) {
                generateReport();
            }

            setTimeout(() => {
                window.print();
            }, 100);
        }

        function generateReport() {
            updateCalculations();

            document.getElementById('report-usd-surplus').textContent = `$${formatNumber(appData.usd.surplus)}`;
            document.getElementById('report-eur-surplus').textContent = `€${formatNumber(appData.eur.surplus)}`;
            document.getElementById('report-try-surplus').textContent = `₺${formatNumber(appData.try.surplus)}`;

            const tableBody = document.getElementById('report-table-body');
            if (tableBody) {
                tableBody.innerHTML = `
                    <tr>
                        <td>الدولار الأمريكي (USD) / Amerikan Doları</td>
                        <td>$${formatNumber(appData.usd.debtor)}</td>
                        <td>$${formatNumber(appData.usd.creditor)}</td>
                        <td style="color: ${appData.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            $${formatNumber(appData.usd.surplus)}
                        </td>
                        <td>
                            <span style="color: ${appData.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                                ${appData.usd.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                            </span>
                        </td>
                    </tr>
                    <tr>
                        <td>اليورو الأوروبي (EUR) / Euro</td>
                        <td>€${formatNumber(appData.eur.debtor)}</td>
                        <td>€${formatNumber(appData.eur.creditor)}</td>
                        <td style="color: ${appData.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            €${formatNumber(appData.eur.surplus)}
                        </td>
                        <td>
                            <span style="color: ${appData.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                                ${appData.eur.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                            </span>
                        </td>
                    </tr>
                    <tr>
                        <td>الليرة التركية (TRY) / Türk Lirası</td>
                        <td>₺${formatNumber(appData.try.debtor)}</td>
                        <td>₺${formatNumber(appData.try.creditor)}</td>
                        <td style="color: ${appData.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ₺${formatNumber(appData.try.surplus)}
                        </td>
                        <td>
                            <span style="color: ${appData.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                                ${appData.try.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                            </span>
                        </td>
                    </tr>
                `;
            }

            // حساب الصلج
            document.getElementById('report-saljog-amount').textContent = `$${formatNumber(appData.saljog.amount)}`;
            document.getElementById('report-saljog-expense').textContent = `$${formatNumber(appData.saljog.expense)}`;
            document.getElementById('report-saljog-profit').textContent = `$${formatNumber(appData.saljog.profit)}`;
            document.getElementById('report-saljog-total').textContent = `$${formatNumber(appData.saljog.total)}`;

            // الملخص
            document.getElementById('report-display-usd-surplus').textContent = `$${formatNumber(appData.usd.surplus)}`;
            document.getElementById('report-display-saljog-total').textContent = `$${formatNumber(appData.saljog.total)}`;
            document.getElementById('report-real-surplus').textContent = `$${formatNumber(appData.realSurplus)}`;

            // الأرباح
            document.getElementById('report-swift-usd').textContent = `$${formatNumber(appData.profits.swift.usd)}`;
            document.getElementById('report-swift-eur').textContent = `€${formatNumber(appData.profits.swift.eur)}`;
            document.getElementById('report-havala-usd').textContent = `$${formatNumber(appData.profits.havana.usd)}`;
            document.getElementById('report-havala-eur').textContent = `€${formatNumber(appData.profits.havana.eur)}`;
            document.getElementById('report-silver-profit-usd').textContent = `$${formatNumber(appData.profits.silver.usd)}`;
            document.getElementById('report-silver-profit-eur').textContent = `€${formatNumber(appData.profits.silver.eur)}`;
            document.getElementById('report-copper-profit-usd').textContent = `$${formatNumber(appData.profits.copper.usd)}`;
            document.getElementById('report-copper-profit-eur').textContent = `€${formatNumber(appData.profits.copper.eur)}`;
            document.getElementById('report-external-profit-usd').textContent = `$${formatNumber(appData.profits.external.usd)}`;
            document.getElementById('report-external-profit-eur').textContent = `€${formatNumber(appData.profits.external.eur)}`;
            document.getElementById('report-total-profits').innerHTML = `إجمالي الأرباح: $${formatNumber(appData.profits.total.usd)} / €${formatNumber(appData.profits.total.eur)}`;

            updateReportExpenses();

            switchTab('report');
        }

        function updateReportExpenses() {
            const tableBody = document.getElementById('expenses-report-body');
            if (!tableBody) return;

            tableBody.innerHTML = '';

            if (appData.expenses.length === 0) {
                tableBody.innerHTML = `
                    <tr>
                        <td colspan="3" style="text-align: center; padding: 20px; color: #666;">
                            لا توجد مصروفات مسجلة / Kayıtlı gider yok
                        </td>
                    </tr>
                `;
                return;
            }

            let totalUSD = 0, totalEUR = 0, totalTRY = 0;

            appData.expenses.forEach(expense => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${expense.name}</td>
                    <td>${formatNumber(expense.amount)}</td>
                    <td>${expense.currency === 'USD' ? '$' : expense.currency === 'EUR' ? '€' : '₺'}</td>
                `;
                tableBody.appendChild(row);

                if (expense.currency === 'USD') totalUSD += expense.amount;
                else if (expense.currency === 'EUR') totalEUR += expense.amount;
                else if (expense.currency === 'TRY') totalTRY += expense.amount;
            });

            const totalContainer = document.getElementById('report-expense-total');
            if (!totalContainer) return;

            totalContainer.innerHTML = '';

            if (totalUSD > 0) {
                totalContainer.innerHTML += `
                    <div class="expense-total-box">
                        <div>إجمالي مصروفات الدولار / Toplam Dolar Giderler</div>
                        <div class="expense-currency">$${formatNumber(totalUSD)}</div>
                    </div>
                `;
            }

            if (totalEUR > 0) {
                totalContainer.innerHTML += `
                    <div class="expense-total-box">
                        <div>إجمالي مصروفات اليورو / Toplam Euro Giderler</div>
                        <div class="expense-currency">€${formatNumber(totalEUR)}</div>
                    </div>
                `;
            }

            if (totalTRY > 0) {
                totalContainer.innerHTML += `
                    <div class="expense-total-box">
                        <div>إجمالي مصروفات الليرة / Toplam Lira Giderler</div>
                        <div class="expense-currency">₺${formatNumber(totalTRY)}</div>
                    </div>
                `;
            }
        }

        function formatNumber(number, decimals = 2) {
            return number.toFixed(decimals).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }

        function addNewExpense() {
            expenseCounter++;

            const container = document.getElementById('expenses-list');
            if (!container) return;

            const expenseItem = document.createElement('div');
            expenseItem.className = 'expense-item';
            expenseItem.id = `expense-item-${expenseCounter}`;
            expenseItem.innerHTML = `
                <div class="input-group">
                    <label for="expense-name-${expenseCounter}">وصف المصروف / Gider Açıklaması</label>
                    <input type="text" id="expense-name-${expenseCounter}" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                </div>

                <div class="input-group">
                    <label for="expense-amount-${expenseCounter}">القيمة / Tutar</label>
                    <input type="number" id="expense-amount-${expenseCounter}" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                </div>

                <div class="input-group">
                    <label for="expense-currency-${expenseCounter}">العملة / Para Birimi</label>
                    <select id="expense-currency-${expenseCounter}">
                        <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                        <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                        <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                    </select>
                </div>

                <button class="btn btn-reset remove-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="${expenseCounter}">
                    <i class="fas fa-trash"></i> حذف / Sil
                </button>
            `;

            container.appendChild(expenseItem);

            setupExpenseInputListeners(expenseCounter);

            const removeBtn = expenseItem.querySelector('.remove-expense-btn');
            if (removeBtn) {
                removeBtn.addEventListener('click', function() {
                    removeExpense(expenseCounter);
                });
            }

            updateExpensesTotal();
        }

        function removeExpense(id) {
            const item = document.getElementById(`expense-item-${id}`);
            if (item) {
                item.remove();
                updateExpensesTotal();
            }
        }

        function saveData() {
            updateCalculations();

            if (confirm("هل تريد حفظ بيانات اليوم؟ / Bugünün verilerini kaydetmek istiyor musunuz?")) {
                const record = {
                    date: appData.date,
                    timestamp: new Date().getTime(),
                    data: { ...appData }
                };

                historyRecords.push(record);
                localStorage.setItem('alanhar_history', JSON.stringify(historyRecords));

                alert("تم حفظ بيانات اليوم بنجاح! / Bugünün verileri başarıyla kaydedildi!");
                loadHistory();
                resetData();
            }
        }

        function resetData() {
            if (confirm("هل تريد مسح جميع بيانات اليوم؟ / Bugünün tüm verilerini temizlemek istiyor musunuz?")) {
                const inputs = [
                    'usd-debtor', 'usd-creditor',
                    'eur-debtor', 'eur-creditor',
                    'try-debtor', 'try-creditor',
                    'saljog-amount', 'saljog-expense', 'saljog-profit',
                    'swift-profit-usd', 'swift-profit-eur',
                    'havala-profit-usd', 'havala-profit-eur',
                    'silver-profit-usd', 'silver-profit-eur',
                    'copper-profit-usd', 'copper-profit-eur',
                    'external-profit-usd', 'external-profit-eur'
                ];

                inputs.forEach(id => {
                    const input = document.getElementById(id);
                    if (input) input.value = '';
                });

                const expensesList = document.getElementById('expenses-list');
                if (expensesList) {
                    expensesList.innerHTML = '';
                    expenseCounter = 1;
                    addNewExpense();
                }

                appData = {
                    usd: { debtor: 0, creditor: 0, surplus: 0 },
                    eur: { debtor: 0, creditor: 0, surplus: 0 },
                    try: { debtor: 0, creditor: 0, surplus: 0 },
                    saljog: { amount: 0, expense: 0, profit: 0, total: 0 },
                    realSurplus: 0,
                    profits: {
                        swift: { usd: 0, eur: 0 },
                        havana: { usd: 0, eur: 0 },
                        silver: { usd: 0, eur: 0 },
                        copper: { usd: 0, eur: 0 },
                        external: { usd: 0, eur: 0 },
                        total: { usd: 0, eur: 0 }
                    },
                    expenses: [],
                    date: new Date().toISOString().split('T')[0],
                    timestamp: new Date().getTime()
                };

                updateCalculations();

                alert("تم مسح جميع بيانات اليوم بنجاح! / Bugünün tüm verileri başarıyla temizlendi!");
            }
        }

        function loadHistory() {
            const tableBody = document.getElementById('history-table-body');
            if (!tableBody) return;

            const noHistoryRow = document.getElementById('no-history');

            if (historyRecords.length === 0) {
                if (noHistoryRow) noHistoryRow.style.display = '';
                return;
            }

            if (noHistoryRow) noHistoryRow.style.display = 'none';

            tableBody.innerHTML = '';

            const sortedRecords = [...historyRecords].sort((a, b) => b.timestamp - a.timestamp);

            sortedRecords.forEach((record, index) => {
                const originalIndex = historyRecords.indexOf(record);

                let expenseDisplay = '';
                let totalExpenseUSD = 0, totalExpenseEUR = 0, totalExpenseTRY = 0;

                record.data.expenses.forEach(expense => {
                    if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                    else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                    else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
                });

                if (totalExpenseUSD > 0) expenseDisplay += `$${formatNumber(totalExpenseUSD)} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${formatNumber(totalExpenseEUR)} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${formatNumber(totalExpenseTRY)}`;
                if (!expenseDisplay) expenseDisplay = '-';

                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${formatDate(record.date)}</td>
                    <td style="color: ${record.data.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumber(record.data.usd.surplus)}
                    </td>
                    <td style="color: ${record.data.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${formatNumber(record.data.eur.surplus)}
                    </td>
                    <td style="color: ${record.data.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${formatNumber(record.data.try.surplus)}
                    </td>
                    <td>$${formatNumber(record.data.saljog.amount)}</td>
                    <td>$${formatNumber(record.data.saljog.expense)}</td>
                    <td>$${formatNumber(record.data.saljog.profit)}</td>
                    <td style="font-weight: bold; color: #0288d1;">$${formatNumber(record.data.saljog.total)}</td>
                    <td style="color: ${record.data.realSurplus >= 0 ? '#2e7d32' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumber(record.data.realSurplus)}
                    </td>
                    <td>$${formatNumber(record.data.profits.total.usd)} / €${formatNumber(record.data.profits.total.eur)}</td>
                    <td>${expenseDisplay}</td>
                    <td class="no-print">
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem;" onclick="viewRecord(${originalIndex})">
                            <i class="fas fa-eye"></i> عرض / Görüntüle
                        </button>
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem; background: linear-gradient(135deg, #f44336, #c62828);" onclick="deleteRecord(${originalIndex})">
                            <i class="fas fa-trash"></i> حذف / Sil
                        </button>
                    </td>
                `;
                tableBody.appendChild(row);
            });
        }

        function viewRecord(index) {
            const record = historyRecords[index];

            if (!record) return;

            document.getElementById('usd-debtor').value = record.data.usd.debtor;
            document.getElementById('usd-creditor').value = record.data.usd.creditor;
            document.getElementById('eur-debtor').value = record.data.eur.debtor;
            document.getElementById('eur-creditor').value = record.data.eur.creditor;
            document.getElementById('try-debtor').value = record.data.try.debtor;
            document.getElementById('try-creditor').value = record.data.try.creditor;

            document.getElementById('saljog-amount').value = record.data.saljog.amount;
            document.getElementById('saljog-expense').value = record.data.saljog.expense;
            document.getElementById('saljog-profit').value = record.data.saljog.profit;

            document.getElementById('swift-profit-usd').value = record.data.profits.swift.usd;
            document.getElementById('swift-profit-eur').value = record.data.profits.swift.eur;
            document.getElementById('havala-profit-usd').value = record.data.profits.havana.usd;
            document.getElementById('havala-profit-eur').value = record.data.profits.havana.eur;
            document.getElementById('silver-profit-usd').value = record.data.profits.silver.usd;
            document.getElementById('silver-profit-eur').value = record.data.profits.silver.eur;
            document.getElementById('copper-profit-usd').value = record.data.profits.copper.usd;
            document.getElementById('copper-profit-eur').value = record.data.profits.copper.eur;
            document.getElementById('external-profit-usd').value = record.data.profits.external.usd;
            document.getElementById('external-profit-eur').value = record.data.profits.external.eur;

            updateCalculations();
            switchTab('input');

            alert("تم تحميل بيانات السجل المحدد. / Seçilen kayıt verileri yüklendi.");
        }

        function deleteRecord(index) {
            if (confirm("هل تريد حذف هذا السجل؟ / Bu kaydı silmek istiyor musunuz?")) {
                historyRecords.splice(index, 1);
                localStorage.setItem('alanhar_history', JSON.stringify(historyRecords));
                loadHistory();
                alert("تم حذف السجل بنجاح! / Kayıt başarıyla silindi!");
            }
        }

        function filterHistory() {
            const filterDate = document.getElementById('filter-date').value;

            if (!filterDate) {
                loadHistory();
                return;
            }

            const filteredRecords = historyRecords.filter(record => record.date === filterDate);

            const tableBody = document.getElementById('history-table-body');
            if (!tableBody) return;

            const noHistoryRow = document.getElementById('no-history');

            if (filteredRecords.length === 0) {
                tableBody.innerHTML = '';
                if (noHistoryRow) {
                    noHistoryRow.style.display = '';
                    noHistoryRow.innerHTML = `
                        <td colspan="12" style="text-align: center; padding: 30px;">
                            لا توجد سجلات للتاريخ ${formatDate(filterDate)} / 
                            ${formatDate(filterDate)} tarihi için kayıt bulunamadı.
                        </td>
                    `;
                }
                return;
            }

            if (noHistoryRow) noHistoryRow.style.display = 'none';

            tableBody.innerHTML = '';

            filteredRecords.forEach((record, index) => {
                const originalIndex = historyRecords.indexOf(record);

                let expenseDisplay = '';
                let totalExpenseUSD = 0, totalExpenseEUR = 0, totalExpenseTRY = 0;

                record.data.expenses.forEach(expense => {
                    if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                    else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                    else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
                });

                if (totalExpenseUSD > 0) expenseDisplay += `$${formatNumber(totalExpenseUSD)} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${formatNumber(totalExpenseEUR)} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${formatNumber(totalExpenseTRY)}`;
                if (!expenseDisplay) expenseDisplay = '-';

                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${formatDate(record.date)}</td>
                    <td style="color: ${record.data.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumber(record.data.usd.surplus)}
                    </td>
                    <td style="color: ${record.data.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${formatNumber(record.data.eur.surplus)}
                    </td>
                    <td style="color: ${record.data.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${formatNumber(record.data.try.surplus)}
                    </td>
                    <td>$${formatNumber(record.data.saljog.amount)}</td>
                    <td>$${formatNumber(record.data.saljog.expense)}</td>
                    <td>$${formatNumber(record.data.saljog.profit)}</td>
                    <td style="font-weight: bold; color: #0288d1;">$${formatNumber(record.data.saljog.total)}</td>
                    <td style="color: ${record.data.realSurplus >= 0 ? '#2e7d32' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumber(record.data.realSurplus)}
                    </td>
                    <td>$${formatNumber(record.data.profits.total.usd)} / €${formatNumber(record.data.profits.total.eur)}</td>
                    <td>${expenseDisplay}</td>
                    <td class="no-print">
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem;" onclick="viewRecord(${originalIndex})">
                            <i class="fas fa-eye"></i> عرض / Görüntüle
                        </button>
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem; background: linear-gradient(135deg, #f44336, #c62828);" onclick="deleteRecord(${originalIndex})">
                            <i class="fas fa-trash"></i> حذف / Sil
                        </button>
                    </td>
                `;
                tableBody.appendChild(row);
            });
        }

        function clearHistory() {
            if (confirm("هل تريد مسح جميع السجلات السابقة؟ لا يمكن التراجع عن هذا الإجراء. / Tüm önceki kayıtları temizlemek istiyor musunuz? Bu işlem geri alınamaz.")) {
                historyRecords = [];
                localStorage.removeItem('alanhar_history');
                loadHistory();
                alert("تم مسح جميع السجلات بنجاح! / Tüm kayıtlar başarıyla temizlendi!");
            }
        }

        function switchTab(tabId) {
            document.querySelectorAll('.content-section').forEach(section => {
                section.classList.remove('active');
            });

            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
            });

            document.getElementById(tabId).classList.add('active');
            document.querySelector(`[data-tab="${tabId}"]`).classList.add('active');

            if (tabId === 'report') {
                generateReport();
            }
        }

        function formatDate(dateString) {
            const date = new Date(dateString);
            return date.toLocaleDateString('ar-EG', {
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            });
        }

        window.viewRecord = viewRecord;
        window.deleteRecord = deleteRecord;
    </script>
</body>
</html>
