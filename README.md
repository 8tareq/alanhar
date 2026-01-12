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
        
        .title-tr {
            font-size: 1rem;
            color: #666;
            font-weight: normal;
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
        
        .profit-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .profit-item {
            flex: 1;
            min-width: 200px;
            background-color: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            border-top: 4px solid #26d0ce;
        }
        
        .profit-total {
            background-color: #e8f5e9;
            padding: 20px;
            border-radius: 8px;
            border: 2px solid #4caf50;
            text-align: center;
            font-weight: bold;
            font-size: 1.3rem;
            color: #2e7d32;
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
        
        .date-display {
            text-align: center;
            margin: 20px 0;
            font-size: 1.2rem;
            color: #666;
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
        
        .summary-label {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        @media print {
            .no-print {
                display: none !important;
            }
            
            .container {
                width: 100%;
                max-width: 100%;
                padding: 10px;
            }
            
            .card {
                box-shadow: none;
                border: 1px solid #ddd;
                break-inside: avoid;
            }
            
            .report-table {
                font-size: 12px;
            }
            
            .summary-box {
                color: black;
                background: white !important;
                border: 1px solid #ddd;
            }
            
            .btn {
                display: none !important;
            }
            
            header {
                color: black;
                background: white !important;
                border: 1px solid #ddd;
            }
            
            .logo i {
                color: #1a2980;
            }
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #666;
            border-top: 1px solid #eee;
            font-size: 0.9rem;
        }
        
        .warning {
            background-color: #fff3e0;
            padding: 15px;
            border-radius: 8px;
            border-right: 5px solid #ff9800;
            margin-bottom: 20px;
        }
        
        .warning i {
            color: #ff9800;
            margin-left: 10px;
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
        
        .info-box {
            background-color: #e3f2fd;
            padding: 10px 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            border-right: 4px solid #2196f3;
        }
        
        .info-box p {
            margin: 5px 0;
            font-size: 0.95rem;
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
                <i class="fas fa-calculator"></i> إدخال البيانات / Veri Girişi
            </div>
            <div class="tab" data-tab="report">
                <i class="fas fa-chart-line"></i> التقرير اليومي / Günlük Rapor
            </div>
            <div class="tab" data-tab="history">
                <i class="fas fa-history"></i> السجلات السابقة / Önceki Kayıtlar
            </div>
        </div>
        
        <!-- قسم إدخال البيانات -->
        <div id="input" class="content-section active">
            <div class="warning no-print">
                <i class="fas fa-exclamation-circle"></i>
                <strong>ملاحظة / Not:</strong> يرجى إدخال جميع البيانات المطلوبة لتوليد تقرير يومي كامل. / Lütfen tam bir günlük rapor oluşturmak için tüm gerekli verileri girin.
            </div>
            
            <div class="info-box">
                <p><strong>تفسير:</strong> الفائض = المدين (الخروج) - الدائن (الدخول). إذا كانت النتيجة موجبة فهذا ربح (أزرق)، وإذا كانت سالبة فهذا خسارة (أحمر).</p>
                <p><strong>Açıklama:</strong> Kar/Zarar = Borçlu (Çıkış) - Alacaklı (Giriş). Sonuç pozitif ise kar (mavi), negatif ise zarar (kırmızı).</p>
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
                            <input type="number" id="usd-debtor" placeholder="أدخل قيمة المدين بالدولار / Dolar cinsinden borçlu değerini girin">
                        </div>
                        
                        <div class="input-group">
                            <label for="usd-creditor">الدائن (الدخول) / Alacaklı (Giriş)</label>
                            <div class="label-tr">Giren para miktarı</div>
                            <input type="number" id="usd-creditor" placeholder="أدخل قيمة الدائن بالدولار / Dolar cinsinden alacaklı değerini girin">
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
                            <input type="number" id="eur-debtor" placeholder="أدخل قيمة المدين باليورو / Euro cinsinden borçlu değerini girin">
                        </div>
                        
                        <div class="input-group">
                            <label for="eur-creditor">الدائن (الدخول) / Alacaklı (Giriş)</label>
                            <div class="label-tr">Giren para miktarı</div>
                            <input type="number" id="eur-creditor" placeholder="أدخل قيمة الدائن باليورو / Euro cinsinden alacaklı değerini girin">
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
                            <input type="number" id="try-debtor" placeholder="أدخل قيمة المدين بالليرة / Lira cinsinden borçlu değerini girin">
                        </div>
                        
                        <div class="input-group">
                            <label for="try-creditor">الدائن (الدخول) / Alacaklı (Giriş)</label>
                            <div class="label-tr">Giren para miktarı</div>
                            <input type="number" id="try-creditor" placeholder="أدخل قيمة الدائن بالليرة / Lira cinsinden alacaklı değerini girin">
                        </div>
                        
                        <div id="try-surplus" class="result-box">
                            الفائض / Kar-Zarar: ₺0.00
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-chart-bar"></i> الأرباح اليومية / Günlük Kârlar</span>
                </h2>
                
                <div class="profit-container">
                    <div class="profit-item">
                        <div class="input-group">
                            <label for="swift-profit">ربح Swift / Swift Kârı</label>
                            <div class="label-tr">Swift transfer kazancı</div>
                            <input type="number" id="swift-profit" placeholder="أدخل ربح Swift / Swift kârını girin">
                        </div>
                    </div>
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label for="havala-profit">ربح Havala / Havale Kârı</label>
                            <div class="label-tr">Havale transfer kazancı</div>
                            <input type="number" id="havala-profit" placeholder="أدخل ربح Havala / Havale kârını girin">
                        </div>
                    </div>
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label for="silver-profit">ربح الفضة / Gümüş Kârı</label>
                            <div class="label-tr">Gümüş alım-satım kazancı</div>
                            <input type="number" id="silver-profit" placeholder="أدخل ربح الفضة / Gümüş kârını girin">
                        </div>
                    </div>
                </div>
                
                <div id="total-profit" class="profit-total">
                    إجمالي الربح اليومي / Toplam Günlük Kâr: $0.00
                </div>
            </div>
            
            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-receipt"></i> المصروفات اليومية / Günlük Giderler</span>
                </h2>
                
                <div id="expenses-container">
                    <!-- سيتم إضافة مصروفات ديناميكياً هنا -->
                    <div class="expense-container">
                        <div class="expense-item">
                            <div class="input-group">
                                <label for="expense-name-1">وصف المصروف / Gider Açıklaması</label>
                                <input type="text" id="expense-name-1" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                            </div>
                            
                            <div class="input-group">
                                <label for="expense-amount-1">القيمة / Tutar</label>
                                <input type="number" id="expense-amount-1" placeholder="أدخل قيمة المصروف / Gider tutarını girin">
                            </div>
                            
                            <div class="input-group">
                                <label for="expense-currency-1">العملة / Para Birimi</label>
                                <select id="expense-currency-1">
                                    <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                                    <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                                    <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                                </select>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="add-expense-btn no-print" id="add-expense">
                    <i class="fas fa-plus-circle"></i> إضافة مصروف جديد / Yeni Gider Ekle
                </div>
                
                <div id="total-expense" class="expense-total-container">
                    <!-- إجماليات المصروفات ستظهر هنا حسب العملة -->
                </div>
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
                <div class="date" id="report-date">التاريخ: <!-- تاريخ التقرير سيتم إضافته ديناميكياً --></div>
                <div class="subtitle-tr">Detaylı Günlük Rapor - ALANHAR Sistemi</div>
            </div>
            
            <div class="card">
                <div class="report-summary">
                    <div class="summary-box usd">
                        <div class="summary-label">الدولار الأمريكي / Amerikan Doları</div>
                        <div class="summary-value" id="report-usd-surplus">$0.00</div>
                        <div>فائض اليوم / Günün Kar-Zararı</div>
                    </div>
                    
                    <div class="summary-box eur">
                        <div class="summary-label">اليورو الأوروبي / Euro</div>
                        <div class="summary-value" id="report-eur-surplus">€0.00</div>
                        <div>فائض اليوم / Günün Kar-Zararı</div>
                    </div>
                    
                    <div class="summary-box try">
                        <div class="summary-label">الليرة التركية / Türk Lirası</div>
                        <div class="summary-value" id="report-try-surplus">₺0.00</div>
                        <div>فائض اليوم / Günün Kar-Zararı</div>
                    </div>
                </div>
                
                <div class="report-container">
                    <table class="report-table">
                        <thead>
                            <tr>
                                <th>العملة / Para Birimi</th>
                                <th>المدين (الخروج) / Borçlu (Çıkış)</th>
                                <th>الدائن (الدخول) / Alacaklı (Giriş)</th>
                                <th>الفائض (الفرق) / Kar-Zarar (Fark)</th>
                                <th>الحالة / Durum</th>
                            </tr>
                        </thead>
                        <tbody id="report-table-body">
                            <!-- سيتم ملء الجدول ديناميكياً -->
                        </tbody>
                    </table>
                </div>
            </div>
            
            <div class="card">
                <h3 class="card-title">
                    <span><i class="fas fa-coins"></i> الأرباح اليومية / Günlük Kârlar</span>
                </h3>
                <div class="profit-container">
                    <div class="profit-item">
                        <h4>ربح Swift / Swift Kârı</h4>
                        <div id="report-swift">$0.00</div>
                    </div>
                    <div class="profit-item">
                        <h4>ربح Havala / Havale Kârı</h4>
                        <div id="report-havala">$0.00</div>
                    </div>
                    <div class="profit-item">
                        <h4>ربح الفضة / Gümüş Kârı</h4>
                        <div id="report-silver">$0.00</div>
                    </div>
                    <div class="profit-item" style="background-color: #e8f5e9;">
                        <h4>إجمالي الأرباح / Toplam Kâr</h4>
                        <div id="report-total-profit" style="font-weight: bold; color: #2e7d32; font-size: 1.2rem;">$0.00</div>
                    </div>
                </div>
            </div>
            
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
                        <tbody id="expenses-report-body">
                            <!-- سيتم ملء الجدول ديناميكياً -->
                        </tbody>
                    </table>
                </div>
                
                <div id="report-expense-total" class="expense-total-container" style="margin-top: 20px;">
                    <!-- إجماليات المصروفات حسب العملة ستظهر هنا -->
                </div>
            </div>
            
            <!-- تم إزالة قسم الإجمالي النهائي -->
            
            <div class="actions no-print" style="margin-top: 30px;">
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
                                <th>إجمالي الأرباح / Toplam Kâr</th>
                                <th>المصروفات / Giderler</th>
                                <th class="no-print">الإجراءات / İşlemler</th>
                            </tr>
                        </thead>
                        <tbody id="history-table-body">
                            <!-- سيتم ملء الجدول ديناميكياً -->
                            <tr id="no-history">
                                <td colspan="7" style="text-align: center; padding: 30px;">لا توجد سجلات سابقة. ابدأ بإدخال بيانات اليوم. / Önceki kayıt yok. Bugünün verilerini girmeye başlayın.</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                
                <div class="actions no-print" style="margin-top: 30px;">
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
            profits: { swift: 0, havana: 0, silver: 0, total: 0 },
            expenses: [],
            date: new Date().toISOString().split('T')[0]
        };

        // سجلات الأيام السابقة
        let historyRecords = JSON.parse(localStorage.getItem('alanhar_history')) || [];
        
        // عداد المصروفات
        let expenseCounter = 1;
        
        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            // تعيين تاريخ اليوم
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('report-date').textContent = `التاريخ: ${formatDate(today)} / Tarih: ${formatDate(today)}`;
            
            // تحميل السجلات السابقة
            loadHistory();
            
            // إضافة مصروف جديد
            document.getElementById('add-expense').addEventListener('click', addNewExpense);
            
            // حفظ البيانات
            document.getElementById('save-data').addEventListener('click', saveData);
            
            // توليد التقرير
            document.getElementById('generate-report').addEventListener('click', generateReport);
            
            // طباعة التقرير
            document.getElementById('print-report').addEventListener('click', printReport);
            
            // مسح البيانات
            document.getElementById('reset-data').addEventListener('click', resetData);
            
            // العودة للإدخال
            document.getElementById('back-to-input').addEventListener('click', () => switchTab('input'));
            
            // مسح السجلات
            document.getElementById('clear-history').addEventListener('click', clearHistory);
            
            // فلترة السجلات حسب التاريخ
            document.getElementById('filter-date').addEventListener('change', filterHistory);
            
            // تبديل التبويبات
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });
            
            // تحديث الحسابات عند إدخال البيانات
            setupInputListeners();
            
            // تحديث المصروفات عند التحميل
            updateExpensesTotal();
        });
        
        // إعداد مستمعي الإدخال
        function setupInputListeners() {
            // تحديث الفائض عند إدخال المدين والدائن
            document.querySelectorAll('input[type="number"]').forEach(input => {
                input.addEventListener('input', updateCalculations);
            });
            
            document.querySelectorAll('select').forEach(select => {
                select.addEventListener('change', updateCalculations);
            });
        }
        
        // تحديث الحسابات
        function updateCalculations() {
            // تحديث فائض الدولار (المدين - الدائن)
            const usdDebtor = parseFloat(document.getElementById('usd-debtor').value) || 0;
            const usdCreditor = parseFloat(document.getElementById('usd-creditor').value) || 0;
            const usdSurplus = usdDebtor - usdCreditor;
            appData.usd = { debtor: usdDebtor, creditor: usdCreditor, surplus: usdSurplus };
            
            const usdSurplusElement = document.getElementById('usd-surplus');
            usdSurplusElement.textContent = `الفائض / Kar-Zarar: $${usdSurplus.toFixed(2)}`;
            usdSurplusElement.className = 'result-box ' + (usdSurplus >= 0 ? 'positive' : 'negative');
            
            // تحديث فائض اليورو
            const eurDebtor = parseFloat(document.getElementById('eur-debtor').value) || 0;
            const eurCreditor = parseFloat(document.getElementById('eur-creditor').value) || 0;
            const eurSurplus = eurDebtor - eurCreditor;
            appData.eur = { debtor: eurDebtor, creditor: eurCreditor, surplus: eurSurplus };
            
            const eurSurplusElement = document.getElementById('eur-surplus');
            eurSurplusElement.textContent = `الفائض / Kar-Zarar: €${eurSurplus.toFixed(2)}`;
            eurSurplusElement.className = 'result-box ' + (eurSurplus >= 0 ? 'positive' : 'negative');
            
            // تحديث فائض الليرة
            const tryDebtor = parseFloat(document.getElementById('try-debtor').value) || 0;
            const tryCreditor = parseFloat(document.getElementById('try-creditor').value) || 0;
            const trySurplus = tryDebtor - tryCreditor;
            appData.try = { debtor: tryDebtor, creditor: tryCreditor, surplus: trySurplus };
            
            const trySurplusElement = document.getElementById('try-surplus');
            trySurplusElement.textContent = `الفائض / Kar-Zarar: ₺${trySurplus.toFixed(2)}`;
            trySurplusElement.className = 'result-box ' + (trySurplus >= 0 ? 'positive' : 'negative');
            
            // تحديث الأرباح
            const swiftProfit = parseFloat(document.getElementById('swift-profit').value) || 0;
            const havanaProfit = parseFloat(document.getElementById('havala-profit').value) || 0;
            const silverProfit = parseFloat(document.getElementById('silver-profit').value) || 0;
            const totalProfit = swiftProfit + havanaProfit + silverProfit;
            appData.profits = { swift: swiftProfit, havana: havanaProfit, silver: silverProfit, total: totalProfit };
            document.getElementById('total-profit').textContent = `إجمالي الربح اليومي / Toplam Günlük Kâr: $${totalProfit.toFixed(2)}`;
            
            // تحديث المصروفات
            updateExpensesTotal();
        }
        
        // تحديث إجمالي المصروفات حسب العملة
        function updateExpensesTotal() {
            let totalExpenseUSD = 0;
            let totalExpenseEUR = 0;
            let totalExpenseTRY = 0;
            
            appData.expenses = [];
            
            // جمع جميع المصروفات حسب العملة
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
                        
                        // جمع المصروفات حسب العملة
                        if (currency === 'USD') totalExpenseUSD += amount;
                        else if (currency === 'EUR') totalExpenseEUR += amount;
                        else if (currency === 'TRY') totalExpenseTRY += amount;
                    }
                }
            }
            
            // عرض إجماليات المصروفات حسب العملة
            const totalExpenseContainer = document.getElementById('total-expense');
            totalExpenseContainer.innerHTML = '';
            
            if (totalExpenseUSD > 0 || totalExpenseEUR > 0 || totalExpenseTRY > 0) {
                if (totalExpenseUSD > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الدولار / Toplam Dolar Giderler</div>
                            <div class="expense-currency">$${totalExpenseUSD.toFixed(2)}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseEUR > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات اليورو / Toplam Euro Giderler</div>
                            <div class="expense-currency">€${totalExpenseEUR.toFixed(2)}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseTRY > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الليرة / Toplam Lira Giderler</div>
                            <div class="expense-currency">₺${totalExpenseTRY.toFixed(2)}</div>
                        </div>
                    `;
                }
            }
        }
        
        // إضافة مصروف جديد
        function addNewExpense() {
            expenseCounter++;
            
            const expenseContainer = document.createElement('div');
            expenseContainer.className = 'expense-item';
            expenseContainer.innerHTML = `
                <div class="input-group">
                    <label for="expense-name-${expenseCounter}">وصف المصروف / Gider Açıklaması</label>
                    <input type="text" id="expense-name-${expenseCounter}" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                </div>
                
                <div class="input-group">
                    <label for="expense-amount-${expenseCounter}">القيمة / Tutar</label>
                    <input type="number" id="expense-amount-${expenseCounter}" placeholder="أدخل قيمة المصروف / Gider tutarını girin">
                </div>
                
                <div class="input-group">
                    <label for="expense-currency-${expenseCounter}">العملة / Para Birimi</label>
                    <select id="expense-currency-${expenseCounter}">
                        <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                        <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                        <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                    </select>
                </div>
            `;
            
            document.querySelector('.expense-container').appendChild(expenseContainer);
            
            // إضافة مستمعي الأحداث للحقول الجديدة
            document.getElementById(`expense-name-${expenseCounter}`).addEventListener('input', updateExpensesTotal);
            document.getElementById(`expense-amount-${expenseCounter}`).addEventListener('input', updateExpensesTotal);
            document.getElementById(`expense-currency-${expenseCounter}`).addEventListener('change', updateExpensesTotal);
        }
        
        // حفظ البيانات
        function saveData() {
            updateCalculations();
            
            // تأكيد الحفظ
            if (confirm("هل تريد حفظ بيانات اليوم؟ / Bugünün verilerini kaydetmek istiyor musunuz?")) {
                // إضافة إلى السجلات
                const record = {
                    date: appData.date,
                    data: { ...appData },
                    timestamp: new Date().toISOString()
                };
                
                historyRecords.push(record);
                localStorage.setItem('alanhar_history', JSON.stringify(historyRecords));
                
                alert("تم حفظ بيانات اليوم بنجاح! / Bugünün verileri başarıyla kaydedildi!");
                loadHistory();
            }
        }
        
        // توليد التقرير
        function generateReport() {
            updateCalculations();
            
            // تحديث عرض التقرير
            const usdSurplusElement = document.getElementById('report-usd-surplus');
            usdSurplusElement.textContent = `$${appData.usd.surplus.toFixed(2)}`;
            usdSurplusElement.parentElement.className = 'summary-box usd ' + (appData.usd.surplus >= 0 ? 'positive' : 'negative');
            
            const eurSurplusElement = document.getElementById('report-eur-surplus');
            eurSurplusElement.textContent = `€${appData.eur.surplus.toFixed(2)}`;
            eurSurplusElement.parentElement.className = 'summary-box eur ' + (appData.eur.surplus >= 0 ? 'positive' : 'negative');
            
            const trySurplusElement = document.getElementById('report-try-surplus');
            trySurplusElement.textContent = `₺${appData.try.surplus.toFixed(2)}`;
            trySurplusElement.parentElement.className = 'summary-box try ' + (appData.try.surplus >= 0 ? 'positive' : 'negative');
            
            // تحديث جدول التقرير الرئيسي
            const reportTableBody = document.getElementById('report-table-body');
            reportTableBody.innerHTML = `
                <tr>
                    <td>الدولار الأمريكي (USD) / Amerikan Doları</td>
                    <td>$${appData.usd.debtor.toFixed(2)}</td>
                    <td>$${appData.usd.creditor.toFixed(2)}</td>
                    <td style="color: ${appData.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${appData.usd.surplus.toFixed(2)}
                    </td>
                    <td>
                        <span style="color: ${appData.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${appData.usd.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
                <tr>
                    <td>اليورو الأوروبي (EUR) / Euro</td>
                    <td>€${appData.eur.debtor.toFixed(2)}</td>
                    <td>€${appData.eur.creditor.toFixed(2)}</td>
                    <td style="color: ${appData.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${appData.eur.surplus.toFixed(2)}
                    </td>
                    <td>
                        <span style="color: ${appData.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${appData.eur.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
                <tr>
                    <td>الليرة التركية (TRY) / Türk Lirası</td>
                    <td>₺${appData.try.debtor.toFixed(2)}</td>
                    <td>₺${appData.try.creditor.toFixed(2)}</td>
                    <td style="color: ${appData.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${appData.try.surplus.toFixed(2)}
                    </td>
                    <td>
                        <span style="color: ${appData.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${appData.try.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
            `;
            
            // تحديث الأرباح في التقرير
            document.getElementById('report-swift').textContent = `$${appData.profits.swift.toFixed(2)}`;
            document.getElementById('report-havala').textContent = `$${appData.profits.havana.toFixed(2)}`;
            document.getElementById('report-silver').textContent = `$${appData.profits.silver.toFixed(2)}`;
            document.getElementById('report-total-profit').textContent = `$${appData.profits.total.toFixed(2)}`;
            
            // تحديث المصروفات في التقرير
            const expensesReportBody = document.getElementById('expenses-report-body');
            expensesReportBody.innerHTML = '';
            
            let totalExpenseUSD = 0;
            let totalExpenseEUR = 0;
            let totalExpenseTRY = 0;
            
            appData.expenses.forEach(expense => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${expense.name}</td>
                    <td>${expense.amount.toFixed(2)}</td>
                    <td>${expense.currency === 'USD' ? '$' : expense.currency === 'EUR' ? '€' : '₺'}</td>
                `;
                expensesReportBody.appendChild(row);
                
                // جمع المصروفات حسب العملة
                if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
            });
            
            // عرض إجماليات المصروفات حسب العملة في التقرير
            const reportExpenseTotalContainer = document.getElementById('report-expense-total');
            reportExpenseTotalContainer.innerHTML = '';
            
            if (totalExpenseUSD > 0 || totalExpenseEUR > 0 || totalExpenseTRY > 0) {
                if (totalExpenseUSD > 0) {
                    reportExpenseTotalContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الدولار / Toplam Dolar Giderler</div>
                            <div class="expense-currency">$${totalExpenseUSD.toFixed(2)}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseEUR > 0) {
                    reportExpenseTotalContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات اليورو / Toplam Euro Giderler</div>
                            <div class="expense-currency">€${totalExpenseEUR.toFixed(2)}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseTRY > 0) {
                    reportExpenseTotalContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الليرة / Toplam Lira Giderler</div>
                            <div class="expense-currency">₺${totalExpenseTRY.toFixed(2)}</div>
                        </div>
                    `;
                }
            }
            
            // التبديل إلى تبويب التقرير
            switchTab('report');
        }
        
        // طباعة التقرير
        function printReport() {
            window.print();
        }
        
        // مسح البيانات
        function resetData() {
            if (confirm("هل تريد مسح جميع بيانات اليوم؟ / Bugünün tüm verilerini temizlemek istiyor musunuz?")) {
                // مسح حقول الإدخال
                document.querySelectorAll('input').forEach(input => {
                    if (input.type === 'number' || input.type === 'text') {
                        input.value = '';
                    }
                });
                
                // إعادة تعيين المصروفات
                const expensesContainer = document.querySelector('.expense-container');
                expensesContainer.innerHTML = '';
                
                // إضافة مصروف افتراضي واحد
                expenseCounter = 1;
                const expenseItem = document.createElement('div');
                expenseItem.className = 'expense-item';
                expenseItem.innerHTML = `
                    <div class="input-group">
                        <label for="expense-name-1">وصف المصروف / Gider Açıklaması</label>
                        <input type="text" id="expense-name-1" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                    </div>
                    
                    <div class="input-group">
                        <label for="expense-amount-1">القيمة / Tutar</label>
                        <input type="number" id="expense-amount-1" placeholder="أدخل قيمة المصروف / Gider tutarını girin">
                    </div>
                    
                    <div class="input-group">
                        <label for="expense-currency-1">العملة / Para Birimi</label>
                        <select id="expense-currency-1">
                            <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                            <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                            <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                        </select>
                    </div>
                `;
                expensesContainer.appendChild(expenseItem);
                
                // إعادة تعيين البيانات
                appData = {
                    usd: { debtor: 0, creditor: 0, surplus: 0 },
                    eur: { debtor: 0, creditor: 0, surplus: 0 },
                    try: { debtor: 0, creditor: 0, surplus: 0 },
                    profits: { swift: 0, havana: 0, silver: 0, total: 0 },
                    expenses: [],
                    date: new Date().toISOString().split('T')[0]
                };
                
                // تحديث الحسابات
                updateCalculations();
                
                // إعادة إعداد مستمعي الأحداث
                setupInputListeners();
                
                alert("تم مسح جميع بيانات اليوم بنجاح! / Bugünün tüm verileri başarıyla temizlendi!");
            }
        }
        
        // تحميل السجلات السابقة
        function loadHistory() {
            const historyTableBody = document.getElementById('history-table-body');
            const noHistoryRow = document.getElementById('no-history');
            
            if (historyRecords.length === 0) {
                noHistoryRow.style.display = '';
                return;
            }
            
            noHistoryRow.style.display = 'none';
            historyTableBody.innerHTML = '';
            
            historyRecords.forEach((record, index) => {
                const row = document.createElement('tr');
                
                // حساب إجمالي المصروفات بالدولار
                let totalExpenseUSD = 0;
                let totalExpenseEUR = 0;
                let totalExpenseTRY = 0;
                
                record.data.expenses.forEach(expense => {
                    if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                    else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                    else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
                });
                
                // عرض المصروفات بالعملات المختلفة
                let expenseDisplay = '';
                if (totalExpenseUSD > 0) expenseDisplay += `$${totalExpenseUSD.toFixed(2)} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${totalExpenseEUR.toFixed(2)} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${totalExpenseTRY.toFixed(2)}`;
                
                row.innerHTML = `
                    <td>${formatDate(record.date)}</td>
                    <td style="color: ${record.data.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${record.data.usd.surplus.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${record.data.eur.surplus.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${record.data.try.surplus.toFixed(2)}
                    </td>
                    <td>$${record.data.profits.total.toFixed(2)}</td>
                    <td>${expenseDisplay || '-'}</td>
                    <td class="no-print">
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem;" onclick="viewRecord(${index})">
                            <i class="fas fa-eye"></i> عرض / Görüntüle
                        </button>
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem; background: linear-gradient(135deg, #f44336, #c62828);" onclick="deleteRecord(${index})">
                            <i class="fas fa-trash"></i> حذف / Sil
                        </button>
                    </td>
                `;
                historyTableBody.appendChild(row);
            });
        }
        
        // عرض سجل محدد
        function viewRecord(index) {
            const record = historyRecords[index];
            
            // تحميل البيانات في نموذج الإدخال
            document.getElementById('usd-debtor').value = record.data.usd.debtor;
            document.getElementById('usd-creditor').value = record.data.usd.creditor;
            document.getElementById('eur-debtor').value = record.data.eur.debtor;
            document.getElementById('eur-creditor').value = record.data.eur.creditor;
            document.getElementById('try-debtor').value = record.data.try.debtor;
            document.getElementById('try-creditor').value = record.data.try.creditor;
            document.getElementById('swift-profit').value = record.data.profits.swift;
            document.getElementById('havala-profit').value = record.data.profits.havana;
            document.getElementById('silver-profit').value = record.data.profits.silver;
            
            // تحديث الحسابات
            updateCalculations();
            
            // التبديل إلى تبويب الإدخال
            switchTab('input');
            
            alert("تم تحميل بيانات السجل المحدد. يمكنك تعديلها وتوليد تقرير جديد. / Seçilen kayıt verileri yüklendi. Düzenleyebilir ve yeni rapor oluşturabilirsiniz.");
        }
        
        // حذف سجل
        function deleteRecord(index) {
            if (confirm("هل تريد حذف هذا السجل؟ / Bu kaydı silmek istiyor musunuz?")) {
                historyRecords.splice(index, 1);
                localStorage.setItem('alanhar_history', JSON.stringify(historyRecords));
                loadHistory();
                alert("تم حذف السجل بنجاح! / Kayıt başarıyla silindi!");
            }
        }
        
        // فلترة السجلات حسب التاريخ
        function filterHistory() {
            const filterDate = document.getElementById('filter-date').value;
            
            if (!filterDate) {
                loadHistory();
                return;
            }
            
            const filteredRecords = historyRecords.filter(record => record.date === filterDate);
            const historyTableBody = document.getElementById('history-table-body');
            const noHistoryRow = document.getElementById('no-history');
            
            if (filteredRecords.length === 0) {
                noHistoryRow.style.display = '';
                noHistoryRow.innerHTML = `<td colspan="7" style="text-align: center; padding: 30px;">لا توجد سجلات للتاريخ ${formatDate(filterDate)} / ${formatDate(filterDate)} tarihi için kayıt bulunamadı.</td>`;
                return;
            }
            
            noHistoryRow.style.display = 'none';
            historyTableBody.innerHTML = '';
            
            filteredRecords.forEach((record, index) => {
                const row = document.createElement('tr');
                
                // حساب إجمالي المصروفات بالدولار
                let totalExpenseUSD = 0;
                let totalExpenseEUR = 0;
                let totalExpenseTRY = 0;
                
                record.data.expenses.forEach(expense => {
                    if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                    else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                    else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
                });
                
                // عرض المصروفات بالعملات المختلفة
                let expenseDisplay = '';
                if (totalExpenseUSD > 0) expenseDisplay += `$${totalExpenseUSD.toFixed(2)} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${totalExpenseEUR.toFixed(2)} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${totalExpenseTRY.toFixed(2)}`;
                
                row.innerHTML = `
                    <td>${formatDate(record.date)}</td>
                    <td style="color: ${record.data.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${record.data.usd.surplus.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${record.data.eur.surplus.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${record.data.try.surplus.toFixed(2)}
                    </td>
                    <td>$${record.data.profits.total.toFixed(2)}</td>
                    <td>${expenseDisplay || '-'}</td>
                    <td class="no-print">
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem;" onclick="viewRecord(${historyRecords.indexOf(record)})">
                            <i class="fas fa-eye"></i> عرض / Görüntüle
                        </button>
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem; background: linear-gradient(135deg, #f44336, #c62828);" onclick="deleteRecord(${historyRecords.indexOf(record)})">
                            <i class="fas fa-trash"></i> حذف / Sil
                        </button>
                    </td>
                `;
                historyTableBody.appendChild(row);
            });
        }
        
        // مسح جميع السجلات
        function clearHistory() {
            if (confirm("هل تريد مسح جميع السجلات السابقة؟ لا يمكن التراجع عن هذا الإجراء. / Tüm önceki kayıtları temizlemek istiyor musunuz? Bu işlem geri alınamaz.")) {
                historyRecords = [];
                localStorage.removeItem('alanhar_history');
                loadHistory();
                alert("تم مسح جميع السجلات بنجاح! / Tüm kayıtlar başarıyla temizlendi!");
            }
        }
        
        // تبديل التبويبات
        function switchTab(tabId) {
            // إخفاء جميع الأقسام
            document.querySelectorAll('.content-section').forEach(section => {
                section.classList.remove('active');
            });
            
            // إزالة النشاط من جميع التبويبات
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // إظهار القسم المحدد
            document.getElementById(tabId).classList.add('active');
            
            // تفعيل التبويب المحدد
            document.querySelector(`[data-tab="${tabId}"]`).classList.add('active');
            
            // إذا كان التبويب هو التقرير، قم بتوليد التقرير تلقائياً
            if (tabId === 'report') {
                generateReport();
            }
        }
        
        // تنسيق التاريخ
        function formatDate(dateString) {
            const date = new Date(dateString);
            return date.toLocaleDateString('ar-EG', {
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            });
        }
    </script>
</body>
</html>
