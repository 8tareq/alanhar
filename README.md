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
        
        .btn-monthly {
            background: linear-gradient(135deg, #9c27b0, #6a1b9a);
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
            
            /* تصميم طباعة التقرير الشهري */
            .monthly-print-only {
                display: block !important;
            }
            
            .monthly-print-header {
                text-align: center;
                border-bottom: 3px solid #ff9800;
                padding-bottom: 15px;
                margin-bottom: 20px;
                page-break-after: avoid;
            }
            
            .monthly-print-header h2 {
                color: #ff9800;
                font-size: 24px;
                margin-bottom: 10px;
            }
            
            .monthly-print-summary {
                display: flex;
                justify-content: space-around;
                margin: 20px 0;
                page-break-inside: avoid;
            }
            
            .monthly-print-currency-box {
                text-align: center;
                border: 2px solid #ff9800;
                border-radius: 10px;
                padding: 15px;
                min-width: 200px;
            }
            
            .monthly-print-currency-value {
                font-size: 22px;
                font-weight: bold;
                margin: 10px 0;
            }
            
            .monthly-print-profit-section {
                margin: 25px 0;
                page-break-inside: avoid;
            }
            
            .monthly-print-profit-box {
                background: #f9f9f9;
                border-left: 5px solid #4caf50;
                padding: 15px;
                margin: 10px 0;
                border-radius: 5px;
            }
            
            .monthly-print-expenses-table {
                width: 100%;
                border-collapse: collapse;
                margin: 20px 0;
                page-break-inside: avoid;
            }
            
            .monthly-print-expenses-table th {
                background-color: #ff9800;
                color: white;
                padding: 10px;
                text-align: right;
            }
            
            .monthly-print-expenses-table td {
                padding: 8px 10px;
                border-bottom: 1px solid #ddd;
            }
            
            .monthly-print-total-box {
                background: #e8f5e9;
                border: 3px solid #4caf50;
                padding: 20px;
                text-align: center;
                font-size: 20px;
                font-weight: bold;
                margin: 30px 0;
                page-break-inside: avoid;
                border-radius: 10px;
            }
            
            .monthly-print-footer {
                text-align: center;
                margin-top: 40px;
                padding-top: 20px;
                border-top: 1px solid #ddd;
                font-size: 12px;
                color: #666;
                page-break-before: avoid;
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

        .profit-currency-row {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
            align-items: center;
        }

        .profit-currency-label {
            font-weight: bold;
            color: #1a2980;
            min-width: 30px;
        }

        .profit-amount {
            flex: 1;
        }

        .profit-display {
            margin: 5px 0;
            padding: 5px 10px;
            background: #f8f9fa;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
        }

        .profit-display-total {
            background: #e8f5e9;
            font-weight: bold;
            color: #2e7d32;
            border: 1px solid #4caf50;
        }
        
        /* تصميم التقرير الشهري */
        .monthly-header {
            background: linear-gradient(135deg, #ff9800, #ff5722);
            color: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 30px;
            text-align: center;
            box-shadow: 0 8px 16px rgba(255, 152, 0, 0.2);
        }
        
        .monthly-header h2 {
            font-size: 2.2rem;
            margin-bottom: 10px;
        }
        
        .monthly-card {
            background-color: white;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            border-top: 5px solid #ff9800;
        }
        
        .monthly-card-title {
            font-size: 1.4rem;
            color: #ff9800;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #ffecb3;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .monthly-card-title i {
            margin-left: 10px;
            color: #ff9800;
        }
        
        .monthly-summary-box {
            flex: 1;
            min-width: 250px;
            padding: 20px;
            border-radius: 10px;
            color: white;
            text-align: center;
        }
        
        .monthly-summary-box.usd {
            background: linear-gradient(135deg, #ff9800, #ff5722);
        }
        
        .monthly-summary-box.eur {
            background: linear-gradient(135deg, #ff9800, #ff5722);
        }
        
        .monthly-summary-box.try {
            background: linear-gradient(135deg, #ff9800, #ff5722);
        }
        
        .monthly-expense-item {
            flex: 1;
            min-width: 200px;
            background-color: #fff8e1;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #ff9800;
        }
        
        .monthly-total-box {
            background-color: #fff3e0;
            padding: 20px;
            border-radius: 8px;
            border: 2px solid #ff9800;
            text-align: center;
            font-weight: bold;
            font-size: 1.3rem;
            color: #ff6f00;
        }
        
        .monthly-net-profit {
            background-color: #e8f5e9;
            padding: 25px;
            border-radius: 10px;
            border: 3px solid #4caf50;
            text-align: center;
            font-weight: bold;
            font-size: 1.5rem;
            color: #2e7d32;
            margin-top: 20px;
        }
        
        .monthly-report-table th {
            background-color: #ff9800;
        }
        
        .monthly-actions .btn {
            background: linear-gradient(135deg, #ff9800, #ff5722);
        }
        
        .monthly-selection {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            align-items: center;
            flex-wrap: wrap;
        }
        
        .monthly-selection .input-group {
            flex: 1;
            min-width: 200px;
        }
        
        .monthly-result {
            padding: 15px;
            border-radius: 8px;
            margin-top: 10px;
            text-align: center;
            font-weight: bold;
            font-size: 1.3rem;
            background: linear-gradient(135deg, #ff9800, #ff5722);
            color: white;
        }
        
        /* تبويبات السجلات */
        .history-tabs {
            display: flex;
            background-color: #fff;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 20px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
        }
        
        .history-tab {
            flex: 1;
            padding: 12px;
            text-align: center;
            cursor: pointer;
            font-weight: bold;
            font-size: 1rem;
            transition: all 0.3s;
            border-bottom: 3px solid transparent;
        }
        
        .history-tab:hover {
            background-color: #f8f9fa;
        }
        
        .history-tab.active {
            color: #ff9800;
            border-bottom: 3px solid #ff9800;
            background-color: #fff3e0;
        }
        
        .history-section {
            display: none;
        }
        
        .history-section.active {
            display: block;
        }
        
        /* الطباعة الشهرية - مخفية في العرض العادي */
        .monthly-print-only {
            display: none;
        }
        
        /* تصميم خاص للطباعة الشهرية */
        @media print {
            body * {
                visibility: hidden;
            }
            
            #monthly-print-content, #monthly-print-content * {
                visibility: visible;
            }
            
            #monthly-print-content {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                padding: 20px;
            }
            
            .container {
                width: 100%;
                max-width: 100%;
                padding: 0;
                margin: 0;
            }
            
            .monthly-print-header {
                text-align: center;
                margin-bottom: 30px;
                border-bottom: 3px solid #ff9800;
                padding-bottom: 20px;
            }
            
            .monthly-print-header h1 {
                color: #ff9800;
                font-size: 28px;
                margin-bottom: 10px;
            }
            
            .monthly-print-header h2 {
                color: #333;
                font-size: 22px;
                margin-bottom: 5px;
            }
            
            .monthly-print-period {
                font-size: 18px;
                color: #666;
                margin-bottom: 10px;
            }
            
            .monthly-print-date {
                font-size: 16px;
                color: #666;
            }
            
            .monthly-print-summary {
                display: flex;
                justify-content: space-between;
                margin: 25px 0;
                flex-wrap: wrap;
            }
            
            .monthly-print-currency-box {
                flex: 1;
                min-width: 200px;
                border: 2px solid #ff9800;
                border-radius: 10px;
                padding: 15px;
                margin: 10px;
                text-align: center;
            }
            
            .monthly-print-currency-title {
                font-size: 18px;
                font-weight: bold;
                color: #ff9800;
                margin-bottom: 10px;
            }
            
            .monthly-print-currency-value {
                font-size: 24px;
                font-weight: bold;
                color: #333;
            }
            
            .monthly-print-profit-section {
                margin: 30px 0;
            }
            
            .monthly-print-profit-title {
                font-size: 20px;
                color: #ff9800;
                border-bottom: 2px solid #ff9800;
                padding-bottom: 10px;
                margin-bottom: 15px;
            }
            
            .monthly-print-profit-table {
                width: 100%;
                border-collapse: collapse;
            }
            
            .monthly-print-profit-table th {
                background-color: #ff9800;
                color: white;
                padding: 12px;
                text-align: right;
            }
            
            .monthly-print-profit-table td {
                padding: 10px;
                border-bottom: 1px solid #ddd;
            }
            
            .monthly-print-expenses-section {
                margin: 30px 0;
            }
            
            .monthly-print-expenses-title {
                font-size: 20px;
                color: #ff9800;
                border-bottom: 2px solid #ff9800;
                padding-bottom: 10px;
                margin-bottom: 15px;
            }
            
            .monthly-print-expenses-table {
                width: 100%;
                border-collapse: collapse;
            }
            
            .monthly-print-expenses-table th {
                background-color: #ff9800;
                color: white;
                padding: 12px;
                text-align: right;
            }
            
            .monthly-print-expenses-table td {
                padding: 10px;
                border-bottom: 1px solid #ddd;
            }
            
            .monthly-print-total-section {
                margin: 40px 0;
                text-align: center;
            }
            
            .monthly-print-total-box {
                display: inline-block;
                background-color: #e8f5e9;
                border: 3px solid #4caf50;
                padding: 25px 40px;
                border-radius: 15px;
                text-align: center;
            }
            
            .monthly-print-total-title {
                font-size: 22px;
                color: #2e7d32;
                margin-bottom: 15px;
                font-weight: bold;
            }
            
            .monthly-print-total-value {
                font-size: 28px;
                font-weight: bold;
                color: #2e7d32;
            }
            
            .monthly-print-footer {
                margin-top: 50px;
                text-align: center;
                border-top: 1px solid #ddd;
                padding-top: 20px;
                font-size: 14px;
                color: #666;
            }
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
            <div class="tab" data-tab="monthly">
                <i class="fas fa-calendar-alt"></i> التقرير الشهري / Aylık Rapor
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
            
            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-chart-bar"></i> الأرباح اليومية / Günlük Kârlar</span>
                </h2>
                
                <div class="profit-container">
                    <div class="profit-item">
                        <div class="input-group">
                            <label>ربح Swift / Swift Kârı</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="swift-profit-usd" placeholder="أدخل ربح Swift بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="swift-profit-eur" placeholder="أدخل ربح Swift باليورو" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label>ربح Havala / Havale Kârı</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="havala-profit-usd" placeholder="أدخل ربح Havala بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="havala-profit-eur" placeholder="أدخل ربح Havala باليورو" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label>ربح الفضة / Gümüş Kârı</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="silver-profit-usd" placeholder="أدخل ربح الفضة بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="silver-profit-eur" placeholder="أدخل ربح الفضة باليورو" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                </div>
                
                <div id="total-profit" class="profit-total">
                    <div>إجمالي الربح اليومي / Toplam Günlük Kâr</div>
                    <div><strong>$</strong> <span id="total-profit-usd">0.00</span></div>
                    <div><strong>€</strong> <span id="total-profit-eur">0.00</span></div>
                </div>
            </div>
            
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
                                <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                            </button>
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
                        <div class="profit-display">
                            <span>$</span>
                            <span id="report-swift-usd">0.00</span>
                        </div>
                        <div class="profit-display">
                            <span>€</span>
                            <span id="report-swift-eur">0.00</span>
                        </div>
                    </div>
                    <div class="profit-item">
                        <h4>ربح Havala / Havale Kârı</h4>
                        <div class="profit-display">
                            <span>$</span>
                            <span id="report-havala-usd">0.00</span>
                        </div>
                        <div class="profit-display">
                            <span>€</span>
                            <span id="report-havala-eur">0.00</span>
                        </div>
                    </div>
                    <div class="profit-item">
                        <h4>ربح الفضة / Gümüş Kârı</h4>
                        <div class="profit-display">
                            <span>$</span>
                            <span id="report-silver-usd">0.00</span>
                        </div>
                        <div class="profit-display">
                            <span>€</span>
                            <span id="report-silver-eur">0.00</span>
                        </div>
                    </div>
                    <div class="profit-item" style="background-color: #e8f5e9;">
                        <h4>إجمالي الأرباح / Toplam Kâr</h4>
                        <div class="profit-display profit-display-total">
                            <span><strong>$</strong></span>
                            <span id="report-total-profit-usd" style="font-weight: bold; color: #2e7d32;">0.00</span>
                        </div>
                        <div class="profit-display profit-display-total">
                            <span><strong>€</strong></span>
                            <span id="report-total-profit-eur" style="font-weight: bold; color: #2e7d32;">0.00</span>
                        </div>
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
            
            <div class="actions no-print" style="margin-top: 30px;">
                <button class="btn btn-print" id="print-report">
                    <i class="fas fa-print"></i> طباعة التقرير / Raporu Yazdır
                </button>
                <button class="btn btn-save" id="back-to-input">
                    <i class="fas fa-edit"></i> العودة للإدخال / Girişe Dön
                </button>
            </div>
        </div>
        
        <!-- قسم التقرير الشهري -->
        <div id="monthly" class="content-section">
            <div class="monthly-header">
                <h2>التقرير الشهري - نظام ALANHAR</h2>
                <div class="subtitle">تحليل شامل للأرباح والمصروفات الشهرية</div>
                <div class="subtitle-tr">Aylık Kâr ve Gider Analizi - ALANHAR Sistemi</div>
            </div>
            
            <div class="monthly-card">
                <h2 class="monthly-card-title">
                    <span><i class="fas fa-calendar-check"></i> تحديد الفترة الشهرية / Ay Seçimi</span>
                </h2>
                
                <div class="monthly-selection">
                    <div class="input-group">
                        <label for="month-select">اختر الشهر / Ay Seçin</label>
                        <select id="month-select">
                            <option value="1">يناير / Ocak</option>
                            <option value="2">فبراير / Şubat</option>
                            <option value="3">مارس / Mart</option>
                            <option value="4">أبريل / Nisan</option>
                            <option value="5">مايو / Mayıs</option>
                            <option value="6">يونيو / Haziran</option>
                            <option value="7">يوليو / Temmuz</option>
                            <option value="8">أغسطس / Ağustos</option>
                            <option value="9">سبتمبر / Eylül</option>
                            <option value="10">أكتوبر / Ekim</option>
                            <option value="11">نوفمبر / Kasım</option>
                            <option value="12">ديسمبر / Aralık</option>
                        </select>
                    </div>
                    
                    <div class="input-group">
                        <label for="year-select">اختر السنة / Yıl Seçin</label>
                        <select id="year-select">
                            <option value="2023">2023</option>
                            <option value="2024" selected>2024</option>
                            <option value="2025">2025</option>
                            <option value="2026">2026</option>
                        </select>
                    </div>
                    
                    <button class="btn btn-monthly" id="load-monthly-data">
                        <i class="fas fa-search"></i> تحميل بيانات الشهر / Ay Verilerini Yükle
                    </button>
                </div>
            </div>
            
            <div class="monthly-card">
                <h2 class="monthly-card-title">
                    <span><i class="fas fa-chart-pie"></i> إجمالي الأرباح الشهرية / Aylık Toplam Kârlar</span>
                </h2>
                
                <div class="currency-container">
                    <!-- الدولار الأمريكي -->
                    <div class="currency-box">
                        <div class="currency-title">
                            <div class="currency-icon">$</div>
                            <div>الدولار الأمريكي (USD) / Amerikan Doları</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-usd-debtor">إجمالي المدين الشهري / Aylık Toplam Borçlu</label>
                            <input type="number" id="monthly-usd-debtor" placeholder="أدخل إجمالي المدين بالدولار" step="0.01" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-usd-creditor">إجمالي الدائن الشهري / Aylık Toplam Alacaklı</label>
                            <input type="number" id="monthly-usd-creditor" placeholder="أدخل إجمالي الدائن بالدولار" step="0.01" min="0">
                        </div>
                        
                        <div id="monthly-usd-net" class="monthly-result">
                            صافي الربح الشهري / Aylık Net Kâr: $0.00
                        </div>
                    </div>
                    
                    <!-- اليورو -->
                    <div class="currency-box">
                        <div class="currency-title">
                            <div class="currency-icon">€</div>
                            <div>اليورو الأوروبي (EUR) / Euro</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-eur-debtor">إجمالي المدين الشهري / Aylık Toplam Borçlu</label>
                            <input type="number" id="monthly-eur-debtor" placeholder="أدخل إجمالي المدين باليورو" step="0.01" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-eur-creditor">إجمالي الدائن الشهري / Aylık Toplam Alacaklı</label>
                            <input type="number" id="monthly-eur-creditor" placeholder="أدخل إجمالي الدائن باليورو" step="0.01" min="0">
                        </div>
                        
                        <div id="monthly-eur-net" class="monthly-result">
                            صافي الربح الشهري / Aylık Net Kâr: €0.00
                        </div>
                    </div>
                    
                    <!-- الليرة التركية -->
                    <div class="currency-box">
                        <div class="currency-title">
                            <div class="currency-icon">₺</div>
                            <div>الليرة التركية (TRY) / Türk Lirası</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-try-debtor">إجمالي المدين الشهري / Aylık Toplam Borçlu</label>
                            <input type="number" id="monthly-try-debtor" placeholder="أدخل إجمالي المدين بالليرة" step="0.01" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-try-creditor">إجمالي الدائن الشهري / Aylık Toplam Alacaklı</label>
                            <input type="number" id="monthly-try-creditor" placeholder="أدخل إجمالي الدائن بالليرة" step="0.01" min="0">
                        </div>
                        
                        <div id="monthly-try-net" class="monthly-result">
                            صافي الربح الشهري / Aylık Net Kâr: ₺0.00
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="monthly-card">
                <h2 class="monthly-card-title">
                    <span><i class="fas fa-coins"></i> الأرباح الإضافية الشهرية / Aylık Ek Kârlar</span>
                </h2>
                
                <div class="profit-container">
                    <div class="profit-item">
                        <div class="input-group">
                            <label>ربح Swift الشهري / Aylık Swift Kârı</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="monthly-swift-profit-usd" placeholder="أدخل ربح Swift الشهري بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="monthly-swift-profit-eur" placeholder="أدخل ربح Swift الشهري باليورو" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label>ربح Havala الشهري / Aylık Havale Kârı</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="monthly-havala-profit-usd" placeholder="أدخل ربح Havala الشهري بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="monthly-havala-profit-eur" placeholder="أدخل ربح Havala الشهري باليورو" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label>ربح الفضة الشهري / Aylık Gümüş Kârı</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="monthly-silver-profit-usd" placeholder="أدخل ربح الفضة الشهري بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="monthly-silver-profit-eur" placeholder="أدخل ربح الفضة الشهري باليورو" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                </div>
                
                <div id="monthly-total-profit" class="profit-total">
                    <div>إجمالي الربح الإضافي الشهري / Aylık Toplam Ek Kâr</div>
                    <div><strong>$</strong> <span id="monthly-total-profit-usd">0.00</span></div>
                    <div><strong>€</strong> <span id="monthly-total-profit-eur">0.00</span></div>
                </div>
            </div>
            
            <div class="monthly-card">
                <h2 class="monthly-card-title">
                    <span><i class="fas fa-receipt"></i> المصروفات الشهرية / Aylık Giderler</span>
                </h2>
                
                <div id="monthly-expenses-container">
                    <div class="expense-container" id="monthly-expenses-list">
                        <div class="monthly-expense-item" id="monthly-expense-item-1">
                            <div class="input-group">
                                <label for="monthly-expense-name-1">وصف المصروف الشهري / Aylık Gider Açıklaması</label>
                                <input type="text" id="monthly-expense-name-1" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                            </div>
                            
                            <div class="input-group">
                                <label for="monthly-expense-amount-1">القيمة الشهرية / Aylık Tutar</label>
                                <input type="number" id="monthly-expense-amount-1" placeholder="أدخل قيمة المصروف الشهري" step="0.01" min="0">
                            </div>
                            
                            <div class="input-group">
                                <label for="monthly-expense-currency-1">العملة / Para Birimi</label>
                                <select id="monthly-expense-currency-1">
                                    <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                                    <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                                    <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                                </select>
                            </div>
                            
                            <div class="input-group">
                                <label for="monthly-expense-type-1">نوع المصروف / Gider Türü</label>
                                <select id="monthly-expense-type-1">
                                    <option value="rent">إيجار / Kira</option>
                                    <option value="electricity">كهرباء / Elektrik</option>
                                    <option value="water">ماء / Su</option>
                                    <option value="salary">رواتب / Maaşlar</option>
                                    <option value="food">أكل ومعيشة / Yemek ve Yaşam</option>
                                    <option value="other">أخرى / Diğer</option>
                                </select>
                            </div>
                            
                            <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="1">
                                <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                            </button>
                        </div>
                    </div>
                </div>
                
                <div class="add-expense-btn no-print" id="add-monthly-expense">
                    <i class="fas fa-plus-circle"></i> إضافة مصروف شهري جديد / Yeni Aylık Gider Ekle
                </div>
                
                <div id="monthly-total-expense" class="expense-total-container" style="margin-top: 20px;">
                    <!-- إجماليات المصروفات الشهرية ستظهر هنا حسب العملة -->
                </div>
            </div>
            
            <div class="monthly-card">
                <h2 class="monthly-card-title">
                    <span><i class="fas fa-calculator"></i> التقرير الشهري النهائي / Aylık Nihai Rapor</span>
                </h2>
                
                <div class="report-container">
                    <table class="report-table monthly-report-table">
                        <thead>
                            <tr>
                                <th>العملة / Para Birimi</th>
                                <th>صافي الربح الأساسي / Temel Net Kâr</th>
                                <th>الأرباح الإضافية / Ek Kârlar</th>
                                <th>إجمالي المصروفات / Toplam Gider</th>
                                <th>الصافي النهائي / Net Sonuç</th>
                                <th>الحالة / Durum</th>
                            </tr>
                        </thead>
                        <tbody id="monthly-report-table-body">
                            <!-- سيتم ملء الجدول ديناميكياً -->
                        </tbody>
                    </table>
                </div>
                
                <div id="monthly-net-profit" class="monthly-net-profit">
                    <div>إجمالي صافي الربح الشهري / Aylık Toplam Net Kâr</div>
                    <div><strong id="monthly-total-net">$0.00 / €0.00 / ₺0.00</strong></div>
                </div>
            </div>
            
            <div class="actions monthly-actions no-print">
                <button class="btn btn-save" id="save-monthly-data">
                    <i class="fas fa-save"></i> حفظ التقرير الشهري / Aylık Raporu Kaydet
                </button>
                <button class="btn btn-print" id="print-monthly-report">
                    <i class="fas fa-print"></i> طباعة التقرير الشهري / Aylık Raporu Yazdır
                </button>
                <button class="btn btn-reset" id="reset-monthly-data">
                    <i class="fas fa-redo"></i> مسح البيانات الشهرية / Aylık Verileri Temizle
                </button>
                <button class="btn" id="generate-monthly-summary">
                    <i class="fas fa-file-alt"></i> توليد ملخص شهري / Aylık Özet Oluştur
                </button>
            </div>
        </div>
        
        <!-- قسم السجلات السابقة -->
        <div id="history" class="content-section">
            <div class="card">
                <h2 class="card-title">
                    <span><i class="fas fa-history"></i> سجلات الأيام السابقة / Önceki Gün Kayıtları</span>
                </h2>
                
                <div class="history-tabs no-print">
                    <div class="history-tab active" data-history-type="daily">
                        السجلات اليومية / Günlük Kayıtlar
                    </div>
                    <div class="history-tab" data-history-type="monthly">
                        السجلات الشهرية / Aylık Kayıtlar
                    </div>
                </div>
                
                <div id="daily-history-section" class="history-section active">
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
                            <i class="fas fa-trash-alt"></i> مسح السجلات اليومية / Günlük Kayıtları Temizle
                        </button>
                    </div>
                </div>
                
                <div id="monthly-history-section" class="history-section">
                    <div class="input-group no-print" style="max-width: 300px; margin-bottom: 20px;">
                        <label for="filter-month">فلترة حسب الشهر / Aya Göre Filtrele</label>
                        <input type="month" id="filter-month">
                    </div>
                    
                    <div class="report-container">
                        <table class="report-table">
                            <thead>
                                <tr>
                                    <th>الشهر / Ay</th>
                                    <th>صافي ربح الدولار / Dolar Net Kâr</th>
                                    <th>صافي ربح اليورو / Euro Net Kâr</th>
                                    <th>صافي ربح الليرة / Lira Net Kâr</th>
                                    <th>إجمالي المصروفات / Toplam Gider</th>
                                    <th>الصافي النهائي / Net Sonuç</th>
                                    <th class="no-print">الإجراءات / İşlemler</th>
                                </tr>
                            </thead>
                            <tbody id="monthly-history-table-body">
                                <!-- سيتم ملء الجدول ديناميكياً -->
                                <tr id="no-monthly-history">
                                    <td colspan="7" style="text-align: center; padding: 30px;">لا توجد سجلات شهرية. ابدأ بإدخال بيانات شهرية. / Aylık kayıt yok. Aylık verileri girmeye başlayın.</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    
                    <div class="actions no-print" style="margin-top: 30px;">
                        <button class="btn btn-reset" id="clear-monthly-history">
                            <i class="fas fa-trash-alt"></i> مسح السجلات الشهرية / Aylık Kayıtları Temizle
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- محتوى الطباعة الشهرية (مخفى في العرض العادي) -->
        <div id="monthly-print-content" class="monthly-print-only">
            <div class="monthly-print-header">
                <h1>نظام ALANHAR - التقرير الشهري</h1>
                <h2>ALANHAR Sistemi - Aylık Rapor</h2>
                <div class="monthly-print-period" id="monthly-print-period">شهر / Ay: يناير 2024</div>
                <div class="monthly-print-date" id="monthly-print-date">تاريخ الطباعة / Yazdırma Tarihi: 1 يناير 2024</div>
            </div>
            
            <div class="monthly-print-summary">
                <div class="monthly-print-currency-box">
                    <div class="monthly-print-currency-title">الدولار الأمريكي (USD)</div>
                    <div class="monthly-print-currency-value" id="monthly-print-usd">$0.00</div>
                </div>
                <div class="monthly-print-currency-box">
                    <div class="monthly-print-currency-title">اليورو الأوروبي (EUR)</div>
                    <div class="monthly-print-currency-value" id="monthly-print-eur">€0.00</div>
                </div>
                <div class="monthly-print-currency-box">
                    <div class="monthly-print-currency-title">الليرة التركية (TRY)</div>
                    <div class="monthly-print-currency-value" id="monthly-print-try">₺0.00</div>
                </div>
            </div>
            
            <div class="monthly-print-profit-section">
                <div class="monthly-print-profit-title">الأرباح الشهرية / Aylık Kârlar</div>
                <table class="monthly-print-profit-table" id="monthly-print-profit-table">
                    <!-- سيتم ملء الجدول ديناميكياً -->
                </table>
            </div>
            
            <div class="monthly-print-expenses-section">
                <div class="monthly-print-expenses-title">المصروفات الشهرية / Aylık Giderler</div>
                <table class="monthly-print-expenses-table" id="monthly-print-expenses-table">
                    <!-- سيتم ملء الجدول ديناميكياً -->
                </table>
            </div>
            
            <div class="monthly-print-total-section">
                <div class="monthly-print-total-box">
                    <div class="monthly-print-total-title">الصافي النهائي الشهري / Aylık Net Sonuç</div>
                    <div class="monthly-print-total-value" id="monthly-print-total">$0.00 / €0.00 / ₺0.00</div>
                </div>
            </div>
            
            <div class="monthly-print-footer">
                <p>نظام ALANHAR لإدارة محلات الصرافة والحوالات &copy; 2024</p>
                <p>ALANHAR Sistemi - Döviz ve Havale Yönetimi &copy; 2024</p>
            </div>
        </div>
        
        <footer class="no-print">
            <p>نظام ALANHAR لإدارة محلات الصرافة والحوالات &copy; 2024</p>
            <p>ALANHAR Sistemi - Döviz ve Havale Yönetimi &copy; 2024</p>
        </footer>
    </div>

    <script>
        // بيانات التطبيق
        let appData = {
            usd: { debtor: 0, creditor: 0, surplus: 0 },
            eur: { debtor: 0, creditor: 0, surplus: 0 },
            try: { debtor: 0, creditor: 0, surplus: 0 },
            profits: { 
                swift: { usd: 0, eur: 0 }, 
                havana: { usd: 0, eur: 0 }, 
                silver: { usd: 0, eur: 0 },
                total: { usd: 0, eur: 0 }
            },
            expenses: [],
            date: new Date().toISOString().split('T')[0]
        };

        // بيانات التقرير الشهري
        let monthlyData = {
            month: new Date().getMonth() + 1,
            year: new Date().getFullYear(),
            usd: { debtor: 0, creditor: 0, net: 0 },
            eur: { debtor: 0, creditor: 0, net: 0 },
            try: { debtor: 0, creditor: 0, net: 0 },
            profits: {
                swift: { usd: 0, eur: 0 },
                havana: { usd: 0, eur: 0 },
                silver: { usd: 0, eur: 0 },
                total: { usd: 0, eur: 0 }
            },
            expenses: [],
            totalExpenses: { usd: 0, eur: 0, try: 0 },
            netProfit: { usd: 0, eur: 0, try: 0 }
        };
        
        // سجلات الأيام السابقة
        let historyRecords = JSON.parse(localStorage.getItem('alanhar_history')) || [];
        
        // سجلات التقارير الشهرية
        let monthlyHistoryRecords = JSON.parse(localStorage.getItem('alanhar_monthly_history')) || [];
        
        // عداد المصروفات
        let expenseCounter = 1;
        let monthlyExpenseCounter = 1;
        
        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            console.log("تم تحميل البرنامج بنجاح!");
            
            // تعيين تاريخ اليوم
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('report-date').textContent = `التاريخ: ${formatDate(today)} / Tarih: ${formatDate(today)}`;
            
            // تحميل السجلات السابقة
            loadHistory();
            loadMonthlyHistory();
            
            // إضافة مصروف جديد
            document.getElementById('add-expense').addEventListener('click', addNewExpense);
            
            // إضافة مصروف شهري جديد
            document.getElementById('add-monthly-expense').addEventListener('click', addNewMonthlyExpense);
            
            // حفظ البيانات
            document.getElementById('save-data').addEventListener('click', saveData);
            
            // حفظ البيانات الشهرية
            document.getElementById('save-monthly-data').addEventListener('click', saveMonthlyData);
            
            // توليد التقرير
            document.getElementById('generate-report').addEventListener('click', generateReport);
            
            // توليد الملخص الشهري
            document.getElementById('generate-monthly-summary').addEventListener('click', generateMonthlySummary);
            
            // طباعة التقرير
            document.getElementById('print-report').addEventListener('click', printReport);
            
            // طباعة التقرير الشهري
            document.getElementById('print-monthly-report').addEventListener('click', printMonthlyReport);
            
            // مسح البيانات
            document.getElementById('reset-data').addEventListener('click', resetData);
            
            // مسح البيانات الشهرية
            document.getElementById('reset-monthly-data').addEventListener('click', resetMonthlyData);
            
            // العودة للإدخال
            document.getElementById('back-to-input').addEventListener('click', () => switchTab('input'));
            
            // مسح السجلات
            document.getElementById('clear-history').addEventListener('click', clearHistory);
            
            // مسح السجلات الشهرية
            document.getElementById('clear-monthly-history').addEventListener('click', clearMonthlyHistory);
            
            // فلترة السجلس حسب التاريخ
            document.getElementById('filter-date').addEventListener('change', filterHistory);
            
            // فلترة السجلات الشهرية
            document.getElementById('filter-month').addEventListener('change', filterMonthlyHistory);
            
            // تحميل بيانات الشهر
            document.getElementById('load-monthly-data').addEventListener('click', loadMonthlyData);
            
            // تبديل التبويبات الرئيسية
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    console.log("نقر على تبويب:", tabId);
                    switchTab(tabId);
                });
            });
            
            // تبديل نوع السجلات
            document.querySelectorAll('.history-tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const historyType = this.getAttribute('data-history-type');
                    console.log("نقر على تبويب السجلات:", historyType);
                    switchHistoryType(historyType);
                });
            });
            
            // إضافة مستمعي الأحداث لحذف المصروفات
            setupRemoveExpenseListeners();
            setupRemoveMonthlyExpenseListeners();
            
            // تحديث الحسابات عند إدخال البيانات
            setupInputListeners();
            setupMonthlyInputListeners();
            
            // تحديث المصروفات عند التحميل
            updateExpensesTotal();
            updateMonthlyExpensesTotal();
            
            // تحديث الحسابات الأولية
            updateCalculations();
            updateMonthlyCalculations();
            
            // تعيين الشهر والسنة الحاليين
            const currentMonth = new Date().getMonth() + 1;
            const currentYear = new Date().getFullYear();
            document.getElementById('month-select').value = currentMonth;
            document.getElementById('year-select').value = currentYear;
            
            console.log("تمت تهيئة التطبيق بنجاح!");
        });
        
        // إعداد مستمعي الإدخال
        function setupInputListeners() {
            // تحديث الفائض عند إدخال المدين والدائن
            document.querySelectorAll('input[type="number"]').forEach(input => {
                if (!input.id.includes('monthly')) {
                    input.addEventListener('input', updateCalculations);
                }
            });
            
            document.querySelectorAll('select').forEach(select => {
                if (!select.id.includes('monthly')) {
                    select.addEventListener('change', updateCalculations);
                }
            });
        }
        
        // إعداد مستمعي الإدخال الشهري
        function setupMonthlyInputListeners() {
            // تحديث الحسابات الشهرية
            document.querySelectorAll('input[type="number"]').forEach(input => {
                if (input.id.includes('monthly')) {
                    input.addEventListener('input', updateMonthlyCalculations);
                }
            });
            
            document.querySelectorAll('select').forEach(select => {
                if (select.id.includes('monthly')) {
                    select.addEventListener('change', updateMonthlyCalculations);
                }
            });
        }
        
        // إعداد مستمعي الأحداث لحذف المصروفات
        function setupRemoveExpenseListeners() {
            document.querySelectorAll('.remove-expense-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const expenseId = this.getAttribute('data-id');
                    removeExpense(expenseId);
                });
            });
        }
        
        // إعداد مستمعي الأحداث لحذف المصروفات الشهرية
        function setupRemoveMonthlyExpenseListeners() {
            document.querySelectorAll('.remove-monthly-expense-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const expenseId = this.getAttribute('data-id');
                    removeMonthlyExpense(expenseId);
                });
            });
        }
        
        // حذف مصروف
        function removeExpense(expenseId) {
            const expenseItem = document.getElementById(`expense-item-${expenseId}`);
            if (expenseItem) {
                expenseItem.remove();
                updateExpensesTotal();
                updateCalculations();
            }
        }
        
        // حذف مصروف شهري
        function removeMonthlyExpense(expenseId) {
            const expenseItem = document.getElementById(`monthly-expense-item-${expenseId}`);
            if (expenseItem) {
                expenseItem.remove();
                updateMonthlyExpensesTotal();
                updateMonthlyCalculations();
            }
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
            
            // تحديث الأرباح بالدولار واليورو
            const swiftProfitUSD = parseFloat(document.getElementById('swift-profit-usd').value) || 0;
            const swiftProfitEUR = parseFloat(document.getElementById('swift-profit-eur').value) || 0;
            const havanaProfitUSD = parseFloat(document.getElementById('havala-profit-usd').value) || 0;
            const havanaProfitEUR = parseFloat(document.getElementById('havala-profit-eur').value) || 0;
            const silverProfitUSD = parseFloat(document.getElementById('silver-profit-usd').value) || 0;
            const silverProfitEUR = parseFloat(document.getElementById('silver-profit-eur').value) || 0;
            
            const totalProfitUSD = swiftProfitUSD + havanaProfitUSD + silverProfitUSD;
            const totalProfitEUR = swiftProfitEUR + havanaProfitEUR + silverProfitEUR;
            
            appData.profits = { 
                swift: { usd: swiftProfitUSD, eur: swiftProfitEUR }, 
                havana: { usd: havanaProfitUSD, eur: havanaProfitEUR }, 
                silver: { usd: silverProfitUSD, eur: silverProfitEUR },
                total: { usd: totalProfitUSD, eur: totalProfitEUR }
            };
            
            // تحديث عرض إجمالي الربح
            document.getElementById('total-profit-usd').textContent = totalProfitUSD.toFixed(2);
            document.getElementById('total-profit-eur').textContent = totalProfitEUR.toFixed(2);
            
            // تحديث المصروفات
            updateExpensesTotal();
        }
        
        // تحديث الحسابات الشهرية
        function updateMonthlyCalculations() {
            // تحديث صافي ربح الدولار الشهري
            const usdDebtor = parseFloat(document.getElementById('monthly-usd-debtor').value) || 0;
            const usdCreditor = parseFloat(document.getElementById('monthly-usd-creditor').value) || 0;
            const usdNet = usdDebtor - usdCreditor;
            monthlyData.usd = { debtor: usdDebtor, creditor: usdCreditor, net: usdNet };
            
            const usdNetElement = document.getElementById('monthly-usd-net');
            usdNetElement.textContent = `صافي الربح الشهري / Aylık Net Kâr: $${usdNet.toFixed(2)}`;
            
            // تحديث صافي ربح اليورو الشهري
            const eurDebtor = parseFloat(document.getElementById('monthly-eur-debtor').value) || 0;
            const eurCreditor = parseFloat(document.getElementById('monthly-eur-creditor').value) || 0;
            const eurNet = eurDebtor - eurCreditor;
            monthlyData.eur = { debtor: eurDebtor, creditor: eurCreditor, net: eurNet };
            
            const eurNetElement = document.getElementById('monthly-eur-net');
            eurNetElement.textContent = `صافي الربح الشهري / Aylık Net Kâr: €${eurNet.toFixed(2)}`;
            
            // تحديث صافي ربح الليرة الشهرية
            const tryDebtor = parseFloat(document.getElementById('monthly-try-debtor').value) || 0;
            const tryCreditor = parseFloat(document.getElementById('monthly-try-creditor').value) || 0;
            const tryNet = tryDebtor - tryCreditor;
            monthlyData.try = { debtor: tryDebtor, creditor: tryCreditor, net: tryNet };
            
            const tryNetElement = document.getElementById('monthly-try-net');
            tryNetElement.textContent = `صافي الربح الشهري / Aylık Net Kâr: ₺${tryNet.toFixed(2)}`;
            
            // تحديث الأرباح الإضافية الشهرية
            const swiftProfitUSD = parseFloat(document.getElementById('monthly-swift-profit-usd').value) || 0;
            const swiftProfitEUR = parseFloat(document.getElementById('monthly-swift-profit-eur').value) || 0;
            const havanaProfitUSD = parseFloat(document.getElementById('monthly-havala-profit-usd').value) || 0;
            const havanaProfitEUR = parseFloat(document.getElementById('monthly-havala-profit-eur').value) || 0;
            const silverProfitUSD = parseFloat(document.getElementById('monthly-silver-profit-usd').value) || 0;
            const silverProfitEUR = parseFloat(document.getElementById('monthly-silver-profit-eur').value) || 0;
            
            const totalProfitUSD = swiftProfitUSD + havanaProfitUSD + silverProfitUSD;
            const totalProfitEUR = swiftProfitEUR + havanaProfitEUR + silverProfitEUR;
            
            monthlyData.profits = {
                swift: { usd: swiftProfitUSD, eur: swiftProfitEUR },
                havana: { usd: havanaProfitUSD, eur: havanaProfitEUR },
                silver: { usd: silverProfitUSD, eur: silverProfitEUR },
                total: { usd: totalProfitUSD, eur: totalProfitEUR }
            };
            
            // تحديث عرض إجمالي الربح الإضافي
            document.getElementById('monthly-total-profit-usd').textContent = totalProfitUSD.toFixed(2);
            document.getElementById('monthly-total-profit-eur').textContent = totalProfitEUR.toFixed(2);
            
            // تحديث المصروفات الشهرية
            updateMonthlyExpensesTotal();
            
            // تحديث التقرير الشهري
            updateMonthlyReport();
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
            } else {
                totalExpenseContainer.innerHTML = `
                    <div class="expense-total-box">
                        <div>لا توجد مصروفات مسجلة / Kayıtlı gider yok</div>
                        <div class="expense-currency">$0.00 / €0.00 / ₺0.00</div>
                    </div>
                `;
            }
        }
        
        // تحديث إجمالي المصروفات الشهرية
        function updateMonthlyExpensesTotal() {
            let totalExpenseUSD = 0;
            let totalExpenseEUR = 0;
            let totalExpenseTRY = 0;
            
            monthlyData.expenses = [];
            
            // جمع جميع المصروفات الشهرية حسب العملة
            for (let i = 1; i <= monthlyExpenseCounter; i++) {
                const nameInput = document.getElementById(`monthly-expense-name-${i}`);
                const amountInput = document.getElementById(`monthly-expense-amount-${i}`);
                const currencySelect = document.getElementById(`monthly-expense-currency-${i}`);
                const typeSelect = document.getElementById(`monthly-expense-type-${i}`);
                
                if (nameInput && amountInput && currencySelect && typeSelect) {
                    const name = nameInput.value;
                    const amount = parseFloat(amountInput.value) || 0;
                    const currency = currencySelect.value;
                    const type = typeSelect.value;
                    
                    if (name && amount > 0) {
                        monthlyData.expenses.push({ name, amount, currency, type });
                        
                        // جمع المصروفات حسب العملة
                        if (currency === 'USD') totalExpenseUSD += amount;
                        else if (currency === 'EUR') totalExpenseEUR += amount;
                        else if (currency === 'TRY') totalExpenseTRY += amount;
                    }
                }
            }
            
            monthlyData.totalExpenses = { usd: totalExpenseUSD, eur: totalExpenseEUR, try: totalExpenseTRY };
            
            // عرض إجماليات المصروفات الشهرية حسب العملة
            const totalExpenseContainer = document.getElementById('monthly-total-expense');
            totalExpenseContainer.innerHTML = '';
            
            if (totalExpenseUSD > 0 || totalExpenseEUR > 0 || totalExpenseTRY > 0) {
                if (totalExpenseUSD > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الدولار الشهرية / Aylık Toplam Dolar Giderler</div>
                            <div class="expense-currency">$${totalExpenseUSD.toFixed(2)}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseEUR > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات اليورو الشهرية / Aylık Toplam Euro Giderler</div>
                            <div class="expense-currency">€${totalExpenseEUR.toFixed(2)}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseTRY > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الليرة الشهرية / Aylık Toplam Lira Giderler</div>
                            <div class="expense-currency">₺${totalExpenseTRY.toFixed(2)}</div>
                        </div>
                    `;
                }
            } else {
                totalExpenseContainer.innerHTML = `
                    <div class="expense-total-box">
                        <div>لا توجد مصروفات شهرية مسجلة / Kayıtlı aylık gider yok</div>
                        <div class="expense-currency">$0.00 / €0.00 / ₺0.00</div>
                    </div>
                `;
            }
        }
        
        // تحديث التقرير الشهري
        function updateMonthlyReport() {
            // حساب الصافي النهائي لكل عملة
            const usdNetProfit = monthlyData.usd.net + monthlyData.profits.total.usd - monthlyData.totalExpenses.usd;
            const eurNetProfit = monthlyData.eur.net + monthlyData.profits.total.eur - monthlyData.totalExpenses.eur;
            const tryNetProfit = monthlyData.try.net - monthlyData.totalExpenses.try;
            
            monthlyData.netProfit = { usd: usdNetProfit, eur: eurNetProfit, try: tryNetProfit };
            
            // تحديث جدول التقرير الشهري
            const monthlyTableBody = document.getElementById('monthly-report-table-body');
            monthlyTableBody.innerHTML = `
                <tr>
                    <td>الدولار الأمريكي (USD) / Amerikan Doları</td>
                    <td>$${monthlyData.usd.net.toFixed(2)}</td>
                    <td>$${monthlyData.profits.total.usd.toFixed(2)}</td>
                    <td>$${monthlyData.totalExpenses.usd.toFixed(2)}</td>
                    <td style="color: ${usdNetProfit >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${usdNetProfit.toFixed(2)}
                    </td>
                    <td>
                        <span style="color: ${usdNetProfit >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${usdNetProfit >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
                <tr>
                    <td>اليورو الأوروبي (EUR) / Euro</td>
                    <td>€${monthlyData.eur.net.toFixed(2)}</td>
                    <td>€${monthlyData.profits.total.eur.toFixed(2)}</td>
                    <td>€${monthlyData.totalExpenses.eur.toFixed(2)}</td>
                    <td style="color: ${eurNetProfit >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${eurNetProfit.toFixed(2)}
                    </td>
                    <td>
                        <span style="color: ${eurNetProfit >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${eurNetProfit >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
                <tr>
                    <td>الليرة التركية (TRY) / Türk Lirası</td>
                    <td>₺${monthlyData.try.net.toFixed(2)}</td>
                    <td>₺0.00</td>
                    <td>₺${monthlyData.totalExpenses.try.toFixed(2)}</td>
                    <td style="color: ${tryNetProfit >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${tryNetProfit.toFixed(2)}
                    </td>
                    <td>
                        <span style="color: ${tryNetProfit >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${tryNetProfit >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
            `;
            
            // تحديث إجمالي الصافي النهائي
            document.getElementById('monthly-total-net').textContent = 
                `$${usdNetProfit.toFixed(2)} / €${eurNetProfit.toFixed(2)} / ₺${tryNetProfit.toFixed(2)}`;
        }
        
        // إضافة مصروف جديد
        function addNewExpense() {
            expenseCounter++;
            
            const expenseContainer = document.getElementById('expenses-list');
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
                    <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                </button>
            `;
            
            expenseContainer.appendChild(expenseItem);
            
            // إضافة مستمعي الأحداث للحقول الجديدة
            document.getElementById(`expense-name-${expenseCounter}`).addEventListener('input', updateExpensesTotal);
            document.getElementById(`expense-amount-${expenseCounter}`).addEventListener('input', updateExpensesTotal);
            document.getElementById(`expense-currency-${expenseCounter}`).addEventListener('change', updateExpensesTotal);
            
            // إضافة مستمع للأحداث لحذف المصروف
            document.querySelector(`.remove-expense-btn[data-id="${expenseCounter}"]`).addEventListener('click', function() {
                removeExpense(expenseCounter);
            });
            
            // تحديث الحسابات
            updateExpensesTotal();
        }
        
        // إضافة مصروف شهري جديد
        function addNewMonthlyExpense() {
            monthlyExpenseCounter++;
            
            const expenseContainer = document.getElementById('monthly-expenses-list');
            const expenseItem = document.createElement('div');
            expenseItem.className = 'monthly-expense-item';
            expenseItem.id = `monthly-expense-item-${monthlyExpenseCounter}`;
            expenseItem.innerHTML = `
                <div class="input-group">
                    <label for="monthly-expense-name-${monthlyExpenseCounter}">وصف المصروف الشهري / Aylık Gider Açıklaması</label>
                    <input type="text" id="monthly-expense-name-${monthlyExpenseCounter}" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                </div>
                
                <div class="input-group">
                    <label for="monthly-expense-amount-${monthlyExpenseCounter}">القيمة الشهرية / Aylık Tutar</label>
                    <input type="number" id="monthly-expense-amount-${monthlyExpenseCounter}" placeholder="أدخل قيمة المصروف الشهري" step="0.01" min="0">
                </div>
                
                <div class="input-group">
                    <label for="monthly-expense-currency-${monthlyExpenseCounter}">العملة / Para Birimi</label>
                    <select id="monthly-expense-currency-${monthlyExpenseCounter}">
                        <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                        <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                        <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                    </select>
                </div>
                
                <div class="input-group">
                    <label for="monthly-expense-type-${monthlyExpenseCounter}">نوع المصروف / Gider Türü</label>
                    <select id="monthly-expense-type-${monthlyExpenseCounter}">
                        <option value="rent">إيجار / Kira</option>
                        <option value="electricity">كهرباء / Elektrik</option>
                        <option value="water">ماء / Su</option>
                        <option value="salary">رواتب / Maaşlar</option>
                        <option value="food">أكل ومعيشة / Yemek ve Yaşam</option>
                        <option value="other">أخرى / Diğer</option>
                    </select>
                </div>
                
                <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="${monthlyExpenseCounter}">
                    <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                </button>
            `;
            
            expenseContainer.appendChild(expenseItem);
            
            // إضافة مستمعي الأحداث للحقول الجديدة
            document.getElementById(`monthly-expense-name-${monthlyExpenseCounter}`).addEventListener('input', updateMonthlyExpensesTotal);
            document.getElementById(`monthly-expense-amount-${monthlyExpenseCounter}`).addEventListener('input', updateMonthlyExpensesTotal);
            document.getElementById(`monthly-expense-currency-${monthlyExpenseCounter}`).addEventListener('change', updateMonthlyExpensesTotal);
            document.getElementById(`monthly-expense-type-${monthlyExpenseCounter}`).addEventListener('change', updateMonthlyExpensesTotal);
            
            // إضافة مستمع للأحداث لحذف المصروف
            document.querySelector(`.remove-monthly-expense-btn[data-id="${monthlyExpenseCounter}"]`).addEventListener('click', function() {
                removeMonthlyExpense(monthlyExpenseCounter);
            });
            
            // تحديث الحسابات
            updateMonthlyExpensesTotal();
            updateMonthlyCalculations();
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
                
                // مسح البيانات بعد الحفظ
                resetData();
            }
        }
        
        // حفظ البيانات الشهرية
        function saveMonthlyData() {
            updateMonthlyCalculations();
            
            // تحديث الشهر والسنة في البيانات
            monthlyData.month = parseInt(document.getElementById('month-select').value);
            monthlyData.year = parseInt(document.getElementById('year-select').value);
            
            // تأكيد الحفظ
            if (confirm("هل تريد حفظ التقرير الشهري؟ / Aylık raporu kaydetmek istiyor musunuz?")) {
                // إضافة إلى السجلات الشهرية
                const record = {
                    month: monthlyData.month,
                    year: monthlyData.year,
                    data: { ...monthlyData },
                    timestamp: new Date().toISOString()
                };
                
                monthlyHistoryRecords.push(record);
                localStorage.setItem('alanhar_monthly_history', JSON.stringify(monthlyHistoryRecords));
                
                alert("تم حفظ التقرير الشهري بنجاح! / Aylık rapor başarıyla kaydedildi!");
                loadMonthlyHistory();
                
                // مسح البيانات بعد الحفظ
                resetMonthlyData();
            }
        }
        
        // توليد التقرير
        function generateReport() {
            console.log("توليد التقرير...");
            updateCalculations();
            
            // تحديث عرض التقرير
            const usdSurplusElement = document.getElementById('report-usd-surplus');
            usdSurplusElement.textContent = `$${appData.usd.surplus.toFixed(2)}`;
            
            const eurSurplusElement = document.getElementById('report-eur-surplus');
            eurSurplusElement.textContent = `€${appData.eur.surplus.toFixed(2)}`;
            
            const trySurplusElement = document.getElementById('report-try-surplus');
            trySurplusElement.textContent = `₺${appData.try.surplus.toFixed(2)}`;
            
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
            document.getElementById('report-swift-usd').textContent = appData.profits.swift.usd.toFixed(2);
            document.getElementById('report-swift-eur').textContent = appData.profits.swift.eur.toFixed(2);
            document.getElementById('report-havala-usd').textContent = appData.profits.havana.usd.toFixed(2);
            document.getElementById('report-havala-eur').textContent = appData.profits.havana.eur.toFixed(2);
            document.getElementById('report-silver-usd').textContent = appData.profits.silver.usd.toFixed(2);
            document.getElementById('report-silver-eur').textContent = appData.profits.silver.eur.toFixed(2);
            document.getElementById('report-total-profit-usd').textContent = appData.profits.total.usd.toFixed(2);
            document.getElementById('report-total-profit-eur').textContent = appData.profits.total.eur.toFixed(2);
            
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
            
            // إذا لم توجد مصروفات
            if (appData.expenses.length === 0) {
                expensesReportBody.innerHTML = `
                    <tr>
                        <td colspan="3" style="text-align: center; padding: 20px; color: #666;">
                            لا توجد مصروفات مسجلة / Kayıtlı gider yok
                        </td>
                    </tr>
                `;
            }
            
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
            } else {
                reportExpenseTotalContainer.innerHTML = `
                    <div class="expense-total-box">
                        <div>لا توجد مصروفات مسجلة / Kayıtlı gider yok</div>
                        <div class="expense-currency">$0.00 / €0.00 / ₺0.00</div>
                    </div>
                `;
            }
            
            // التبديل إلى تبويب التقرير
            switchTab('report');
            console.log("تم توليد التقرير بنجاح!");
        }
        
        // توليد الملخص الشهري
        function generateMonthlySummary() {
            console.log("توليد الملخص الشهري...");
            updateMonthlyCalculations();
            
            // التبديل إلى تبويب التقرير الشهري
            switchTab('monthly');
            
            alert("تم توليد التقرير الشهري بنجاح! / Aylık rapor başarıyla oluşturuldu!");
        }
        
        // طباعة التقرير
        function printReport() {
            window.print();
        }
        
        // طباعة التقرير الشهري
        function printMonthlyReport() {
            // تحديث التقرير أولاً
            updateMonthlyCalculations();
            
            // تحديث محتوى الطباعة الشهرية
            updateMonthlyPrintContent();
            
            // طباعة التقرير الشهري
            window.print();
        }
        
        // تحديث محتوى الطباعة الشهرية
        function updateMonthlyPrintContent() {
            const month = document.getElementById('month-select').value;
            const year = document.getElementById('year-select').value;
            const monthName = getMonthName(month);
            
            // تحديث رأس الطباعة
            document.getElementById('monthly-print-period').textContent = `شهر / Ay: ${monthName} ${year}`;
            document.getElementById('monthly-print-date').textContent = `تاريخ الطباعة / Yazdırma Tarihi: ${formatDate(new Date().toISOString())}`;
            
            // تحديث صافي الأرباح
            const usdNetProfit = monthlyData.usd.net + monthlyData.profits.total.usd - monthlyData.totalExpenses.usd;
            const eurNetProfit = monthlyData.eur.net + monthlyData.profits.total.eur - monthlyData.totalExpenses.eur;
            const tryNetProfit = monthlyData.try.net - monthlyData.totalExpenses.try;
            
            document.getElementById('monthly-print-usd').textContent = `$${usdNetProfit.toFixed(2)}`;
            document.getElementById('monthly-print-eur').textContent = `€${eurNetProfit.toFixed(2)}`;
            document.getElementById('monthly-print-try').textContent = `₺${tryNetProfit.toFixed(2)}`;
            
            // تحديث جدول الأرباح
            const profitTable = document.getElementById('monthly-print-profit-table');
            profitTable.innerHTML = `
                <thead>
                    <tr>
                        <th>نوع الربح / Kâr Türü</th>
                        <th>الدولار (USD)</th>
                        <th>اليورو (EUR)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>ربح Swift / Swift Kârı</td>
                        <td>$${monthlyData.profits.swift.usd.toFixed(2)}</td>
                        <td>€${monthlyData.profits.swift.eur.toFixed(2)}</td>
                    </tr>
                    <tr>
                        <td>ربح Havala / Havale Kârı</td>
                        <td>$${monthlyData.profits.havana.usd.toFixed(2)}</td>
                        <td>€${monthlyData.profits.havana.eur.toFixed(2)}</td>
                    </tr>
                    <tr>
                        <td>ربح الفضة / Gümüş Kârı</td>
                        <td>$${monthlyData.profits.silver.usd.toFixed(2)}</td>
                        <td>€${monthlyData.profits.silver.eur.toFixed(2)}</td>
                    </tr>
                    <tr style="font-weight: bold; background-color: #f9f9f9;">
                        <td>الإجمالي / Toplam</td>
                        <td>$${monthlyData.profits.total.usd.toFixed(2)}</td>
                        <td>€${monthlyData.profits.total.eur.toFixed(2)}</td>
                    </tr>
                </tbody>
            `;
            
            // تحديث جدول المصروفات
            const expensesTable = document.getElementById('monthly-print-expenses-table');
            
            if (monthlyData.expenses.length > 0) {
                expensesTable.innerHTML = `
                    <thead>
                        <tr>
                            <th>وصف المصروف / Gider Açıklaması</th>
                            <th>القيمة / Tutar</th>
                            <th>العملة / Para Birimi</th>
                            <th>النوع / Tür</th>
                        </tr>
                    </thead>
                    <tbody>
                        ${monthlyData.expenses.map(expense => `
                            <tr>
                                <td>${expense.name}</td>
                                <td>${expense.amount.toFixed(2)}</td>
                                <td>${expense.currency === 'USD' ? '$' : expense.currency === 'EUR' ? '€' : '₺'}</td>
                                <td>${getExpenseTypeName(expense.type)}</td>
                            </tr>
                        `).join('')}
                        <tr style="font-weight: bold; background-color: #f9f9f9;">
                            <td colspan="3">إجمالي المصروفات / Toplam Gider</td>
                            <td>$${monthlyData.totalExpenses.usd.toFixed(2)} / €${monthlyData.totalExpenses.eur.toFixed(2)} / ₺${monthlyData.totalExpenses.try.toFixed(2)}</td>
                        </tr>
                    </tbody>
                `;
            } else {
                expensesTable.innerHTML = `
                    <tr>
                        <td colspan="4" style="text-align: center; padding: 20px; color: #666;">
                            لا توجد مصروفات شهرية مسجلة / Kayıtlı aylık gider yok
                        </td>
                    </tr>
                `;
            }
            
            // تحديث الإجمالي النهائي
            document.getElementById('monthly-print-total').textContent = 
                `$${usdNetProfit.toFixed(2)} / €${eurNetProfit.toFixed(2)} / ₺${tryNetProfit.toFixed(2)}`;
        }
        
        // الحصول على اسم نوع المصروف
        function getExpenseTypeName(type) {
            const types = {
                'rent': 'إيجار / Kira',
                'electricity': 'كهرباء / Elektrik',
                'water': 'ماء / Su',
                'salary': 'رواتب / Maaşlar',
                'food': 'أكل ومعيشة / Yemek ve Yaşam',
                'other': 'أخرى / Diğer'
            };
            return types[type] || type;
        }
        
        // مسح البيانات
        function resetData() {
            if (confirm("هل تريد مسح جميع بيانات اليوم؟ / Bugünün tüm verilerini temizlemek istiyor musunuz?")) {
                // مسح حقول الإدخال
                document.querySelectorAll('input[type="number"], input[type="text"]').forEach(input => {
                    if (input.id.includes('profit') || input.id.includes('debtor') || input.id.includes('creditor')) {
                        input.value = '';
                    }
                });
                
                // إعادة تعيين المصروفات
                const expensesList = document.getElementById('expenses-list');
                expensesList.innerHTML = '';
                
                // إضافة مصروف افتراضي واحد
                expenseCounter = 1;
                const expenseItem = document.createElement('div');
                expenseItem.className = 'expense-item';
                expenseItem.id = 'expense-item-1';
                expenseItem.innerHTML = `
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
                        <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                    </button>
                `;
                expensesList.appendChild(expenseItem);
                
                // إعادة إعداد مستمعي الأحداث
                setupRemoveExpenseListeners();
                setupInputListeners();
                
                // إعادة تعيين البيانات
                appData = {
                    usd: { debtor: 0, creditor: 0, surplus: 0 },
                    eur: { debtor: 0, creditor: 0, surplus: 0 },
                    try: { debtor: 0, creditor: 0, surplus: 0 },
                    profits: { 
                        swift: { usd: 0, eur: 0 }, 
                        havana: { usd: 0, eur: 0 }, 
                        silver: { usd: 0, eur: 0 },
                        total: { usd: 0, eur: 0 }
                    },
                    expenses: [],
                    date: new Date().toISOString().split('T')[0]
                };
                
                // تحديث الحسابات
                updateCalculations();
                
                // تحديث التقرير إذا كان مفتوحاً
                if (document.getElementById('report').classList.contains('active')) {
                    generateReport();
                }
                
                alert("تم مسح جميع بيانات اليوم بنجاح! / Bugünün tüm verileri başarıyla temizlendi!");
            }
        }
        
        // مسح البيانات الشهرية
        function resetMonthlyData() {
            if (confirm("هل تريد مسح جميع بيانات الشهر الحالي؟ / Mevcut ayın tüm verilerini temizlemek istiyor musunuz?")) {
                // مسح حقول الإدخال الشهرية
                document.getElementById('monthly-usd-debtor').value = '';
                document.getElementById('monthly-usd-creditor').value = '';
                document.getElementById('monthly-eur-debtor').value = '';
                document.getElementById('monthly-eur-creditor').value = '';
                document.getElementById('monthly-try-debtor').value = '';
                document.getElementById('monthly-try-creditor').value = '';
                
                // مسح حقول الأرباح الإضافية
                document.getElementById('monthly-swift-profit-usd').value = '';
                document.getElementById('monthly-swift-profit-eur').value = '';
                document.getElementById('monthly-havala-profit-usd').value = '';
                document.getElementById('monthly-havala-profit-eur').value = '';
                document.getElementById('monthly-silver-profit-usd').value = '';
                document.getElementById('monthly-silver-profit-eur').value = '';
                
                // إعادة تعيين المصروفات الشهرية
                const expensesList = document.getElementById('monthly-expenses-list');
                expensesList.innerHTML = '';
                
                // إضافة مصروف افتراضي واحد
                monthlyExpenseCounter = 1;
                const expenseItem = document.createElement('div');
                expenseItem.className = 'monthly-expense-item';
                expenseItem.id = 'monthly-expense-item-1';
                expenseItem.innerHTML = `
                    <div class="input-group">
                        <label for="monthly-expense-name-1">وصف المصروف الشهري / Aylık Gider Açıklaması</label>
                        <input type="text" id="monthly-expense-name-1" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                    </div>
                    
                    <div class="input-group">
                        <label for="monthly-expense-amount-1">القيمة الشهرية / Aylık Tutar</label>
                        <input type="number" id="monthly-expense-amount-1" placeholder="أدخل قيمة المصروف الشهري" step="0.01" min="0">
                    </div>
                    
                    <div class="input-group">
                        <label for="monthly-expense-currency-1">العملة / Para Birimi</label>
                        <select id="monthly-expense-currency-1">
                            <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                            <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                            <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                        </select>
                    </div>
                    
                    <div class="input-group">
                        <label for="monthly-expense-type-1">نوع المصروف / Gider Türü</label>
                        <select id="monthly-expense-type-1">
                            <option value="rent">إيجار / Kira</option>
                            <option value="electricity">كهرباء / Elektrik</option>
                            <option value="water">ماء / Su</option>
                            <option value="salary">رواتب / Maaşlar</option>
                            <option value="food">أكل ومعيشة / Yemek ve Yaşam</option>
                            <option value="other">أخرى / Diğer</option>
                        </select>
                    </div>
                    
                    <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="1">
                        <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                    </button>
                `;
                expensesList.appendChild(expenseItem);
                
                // إعادة إعداد مستمعي الأحداث
                setupRemoveMonthlyExpenseListeners();
                setupMonthlyInputListeners();
                
                // إعادة تعيين البيانات
                monthlyData = {
                    month: new Date().getMonth() + 1,
                    year: new Date().getFullYear(),
                    usd: { debtor: 0, creditor: 0, net: 0 },
                    eur: { debtor: 0, creditor: 0, net: 0 },
                    try: { debtor: 0, creditor: 0, net: 0 },
                    profits: {
                        swift: { usd: 0, eur: 0 },
                        havana: { usd: 0, eur: 0 },
                        silver: { usd: 0, eur: 0 },
                        total: { usd: 0, eur: 0 }
                    },
                    expenses: [],
                    totalExpenses: { usd: 0, eur: 0, try: 0 },
                    netProfit: { usd: 0, eur: 0, try: 0 }
                };
                
                // تحديث الحسابات
                updateMonthlyCalculations();
                
                alert("تم مسح جميع بيانات الشهر بنجاح! / Ayın tüm verileri başarıyla temizlendi!");
            }
        }
        
        // تحميل بيانات الشهر
        function loadMonthlyData() {
            const month = document.getElementById('month-select').value;
            const year = document.getElementById('year-select').value;
            
            // البحث عن سجل لهذا الشهر
            const existingRecord = monthlyHistoryRecords.find(record => 
                record.month == month && record.year == year
            );
            
            if (existingRecord) {
                // تحميل البيانات الموجودة
                monthlyData = { ...existingRecord.data };
                
                // تعبئة حقول الإدخال
                document.getElementById('monthly-usd-debtor').value = monthlyData.usd.debtor;
                document.getElementById('monthly-usd-creditor').value = monthlyData.usd.creditor;
                document.getElementById('monthly-eur-debtor').value = monthlyData.eur.debtor;
                document.getElementById('monthly-eur-creditor').value = monthlyData.eur.creditor;
                document.getElementById('monthly-try-debtor').value = monthlyData.try.debtor;
                document.getElementById('monthly-try-creditor').value = monthlyData.try.creditor;
                
                // تعبئة حقول الأرباح الإضافية
                document.getElementById('monthly-swift-profit-usd').value = monthlyData.profits.swift.usd;
                document.getElementById('monthly-swift-profit-eur').value = monthlyData.profits.swift.eur;
                document.getElementById('monthly-havala-profit-usd').value = monthlyData.profits.havana.usd;
                document.getElementById('monthly-havala-profit-eur').value = monthlyData.profits.havana.eur;
                document.getElementById('monthly-silver-profit-usd').value = monthlyData.profits.silver.usd;
                document.getElementById('monthly-silver-profit-eur').value = monthlyData.profits.silver.eur;
                
                // مسح المصروفات الحالية وإضافة المصروفات المحفوظة
                const expensesList = document.getElementById('monthly-expenses-list');
                expensesList.innerHTML = '';
                monthlyExpenseCounter = 0;
                
                monthlyData.expenses.forEach((expense, index) => {
                    monthlyExpenseCounter++;
                    const expenseItem = document.createElement('div');
                    expenseItem.className = 'monthly-expense-item';
                    expenseItem.id = `monthly-expense-item-${monthlyExpenseCounter}`;
                    expenseItem.innerHTML = `
                        <div class="input-group">
                            <label for="monthly-expense-name-${monthlyExpenseCounter}">وصف المصروف الشهري / Aylık Gider Açıklaması</label>
                            <input type="text" id="monthly-expense-name-${monthlyExpenseCounter}" value="${expense.name}">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-expense-amount-${monthlyExpenseCounter}">القيمة الشهرية / Aylık Tutar</label>
                            <input type="number" id="monthly-expense-amount-${monthlyExpenseCounter}" value="${expense.amount}" step="0.01" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-expense-currency-${monthlyExpenseCounter}">العملة / Para Birimi</label>
                            <select id="monthly-expense-currency-${monthlyExpenseCounter}">
                                <option value="USD" ${expense.currency === 'USD' ? 'selected' : ''}>الدولار الأمريكي ($) / Amerikan Doları</option>
                                <option value="EUR" ${expense.currency === 'EUR' ? 'selected' : ''}>اليورو الأوروبي (€) / Euro</option>
                                <option value="TRY" ${expense.currency === 'TRY' ? 'selected' : ''}>الليرة التركية (₺) / Türk Lirası</option>
                            </select>
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-expense-type-${monthlyExpenseCounter}">نوع المصروف / Gider Türü</label>
                            <select id="monthly-expense-type-${monthlyExpenseCounter}">
                                <option value="rent" ${expense.type === 'rent' ? 'selected' : ''}>إيجار / Kira</option>
                                <option value="electricity" ${expense.type === 'electricity' ? 'selected' : ''}>كهرباء / Elektrik</option>
                                <option value="water" ${expense.type === 'water' ? 'selected' : ''}>ماء / Su</option>
                                <option value="salary" ${expense.type === 'salary' ? 'selected' : ''}>رواتب / Maaşlar</option>
                                <option value="food" ${expense.type === 'food' ? 'selected' : ''}>أكل ومعيشة / Yemek ve Yaşam</option>
                                <option value="other" ${expense.type === 'other' ? 'selected' : ''}>أخرى / Diğer</option>
                            </select>
                        </div>
                        
                        <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="${monthlyExpenseCounter}">
                            <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                        </button>
                    `;
                    expensesList.appendChild(expenseItem);
                });
                
                // إعادة إعداد مستمعي الأحداث
                setupRemoveMonthlyExpenseListeners();
                setupMonthlyInputListeners();
                
                // تحديث الحسابات
                updateMonthlyExpensesTotal();
                updateMonthlyCalculations();
                
                alert(`تم تحميل بيانات ${getMonthName(month)} ${year} بنجاح! / ${getMonthName(month)} ${year} verileri başarıyla yüklendi!`);
            } else {
                alert(`لا توجد بيانات محفوظة لشهر ${getMonthName(month)} ${year}. يمكنك إدخال بيانات جديدة. / ${getMonthName(month)} ${year} için kayıtlı veri yok. Yeni veri girebilirsiniz.`);
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
            
            // عرض السجلس بترتيب تاريخي (الأحدث أولاً)
            const sortedRecords = [...historyRecords].sort((a, b) => new Date(b.date) - new Date(a.date));
            
            sortedRecords.forEach((record, index) => {
                const originalIndex = historyRecords.indexOf(record);
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
                if (!expenseDisplay) expenseDisplay = '-';
                
                // حساب إجمالي الأرباح بالدولار واليورو
                const totalProfitUSD = record.data.profits.total.usd;
                const totalProfitEUR = record.data.profits.total.eur;
                let totalProfitDisplay = `$${totalProfitUSD.toFixed(2)}`;
                if (totalProfitEUR > 0) {
                    totalProfitDisplay += ` / €${totalProfitEUR.toFixed(2)}`;
                }
                
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
                    <td>${totalProfitDisplay}</td>
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
                historyTableBody.appendChild(row);
            });
        }
        
        // تحميل السجلات الشهرية
        function loadMonthlyHistory() {
            const monthlyHistoryTableBody = document.getElementById('monthly-history-table-body');
            const noMonthlyHistoryRow = document.getElementById('no-monthly-history');
            
            if (monthlyHistoryRecords.length === 0) {
                noMonthlyHistoryRow.style.display = '';
                return;
            }
            
            noMonthlyHistoryRow.style.display = 'none';
            monthlyHistoryTableBody.innerHTML = '';
            
            // عرض السجلس بترتيب تاريخي (الأحدث أولاً)
            const sortedRecords = [...monthlyHistoryRecords].sort((a, b) => {
                const dateA = new Date(a.year, a.month - 1);
                const dateB = new Date(b.year, b.month - 1);
                return dateB - dateA;
            });
            
            sortedRecords.forEach((record, index) => {
                const originalIndex = monthlyHistoryRecords.indexOf(record);
                const row = document.createElement('tr');
                
                // حساب إجمالي المصروفات بالدولار
                const totalExpenseUSD = record.data.totalExpenses.usd;
                const totalExpenseEUR = record.data.totalExpenses.eur;
                const totalExpenseTRY = record.data.totalExpenses.try;
                
                // عرض المصروفات بالعملات المختلفة
                let expenseDisplay = '';
                if (totalExpenseUSD > 0) expenseDisplay += `$${totalExpenseUSD.toFixed(2)} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${totalExpenseEUR.toFixed(2)} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${totalExpenseTRY.toFixed(2)}`;
                if (!expenseDisplay) expenseDisplay = '-';
                
                // حساب الصافي النهائي
                const usdNet = record.data.netProfit.usd;
                const eurNet = record.data.netProfit.eur;
                const tryNet = record.data.netProfit.try;
                
                let netDisplay = '';
                if (usdNet !== 0) netDisplay += `$${usdNet.toFixed(2)} `;
                if (eurNet !== 0) netDisplay += `€${eurNet.toFixed(2)} `;
                if (tryNet !== 0) netDisplay += `₺${tryNet.toFixed(2)}`;
                
                row.innerHTML = `
                    <td>${getMonthName(record.month)} ${record.year}</td>
                    <td style="color: ${record.data.netProfit.usd >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${record.data.netProfit.usd.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.netProfit.eur >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${record.data.netProfit.eur.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.netProfit.try >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${record.data.netProfit.try.toFixed(2)}
                    </td>
                    <td>${expenseDisplay}</td>
                    <td>${netDisplay}</td>
                    <td class="no-print">
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem;" onclick="viewMonthlyRecord(${originalIndex})">
                            <i class="fas fa-eye"></i> عرض / Görüntüle
                        </button>
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem; background: linear-gradient(135deg, #f44336, #c62828);" onclick="deleteMonthlyRecord(${originalIndex})">
                            <i class="fas fa-trash"></i> حذف / Sil
                        </button>
                    </td>
                `;
                monthlyHistoryTableBody.appendChild(row);
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
            
            // تحميل الأرباح
            document.getElementById('swift-profit-usd').value = record.data.profits.swift.usd;
            document.getElementById('swift-profit-eur').value = record.data.profits.swift.eur;
            document.getElementById('havala-profit-usd').value = record.data.profits.havana.usd;
            document.getElementById('havala-profit-eur').value = record.data.profits.havana.eur;
            document.getElementById('silver-profit-usd').value = record.data.profits.silver.usd;
            document.getElementById('silver-profit-eur').value = record.data.profits.silver.eur;
            
            // تحديث الحسابات
            updateCalculations();
            
            // التبديل إلى تبويب الإدخال
            switchTab('input');
            
            alert("تم تحميل بيانات السجل المحدد. يمكنك تعديلها وتوليد تقرير جديد. / Seçilen kayıt verileri yüklendi. Düzenleyebilir ve yeni rapor oluşturabilirsiniz.");
        }
        
        // عرض سجل شهري محدد
        function viewMonthlyRecord(index) {
            const record = monthlyHistoryRecords[index];
            
            // تعيين الشهر والسنة
            document.getElementById('month-select').value = record.month;
            document.getElementById('year-select').value = record.year;
            
            // تحميل البيانات
            loadMonthlyData();
            
            // التبديل إلى تبويب التقرير الشهري
            switchTab('monthly');
            
            alert("تم تحميل التقرير الشهري المحدد. / Seçilen aylık rapor yüklendi.");
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
        
        // حذف سجل شهري
        function deleteMonthlyRecord(index) {
            if (confirm("هل تريد حذف هذا السجل الشهري؟ / Bu aylık kaydı silmek istiyor musunuz?")) {
                monthlyHistoryRecords.splice(index, 1);
                localStorage.setItem('alanhar_monthly_history', JSON.stringify(monthlyHistoryRecords));
                loadMonthlyHistory();
                alert("تم حذف السجل الشهري بنجاح! / Aylık kayıt başarıyla silindi!");
            }
        }
        
        // فلترة السجلس حسب التاريخ
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
                const originalIndex = historyRecords.indexOf(record);
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
                if (!expenseDisplay) expenseDisplay = '-';
                
                // حساب إجمالي الأرباح بالدولار واليورو
                const totalProfitUSD = record.data.profits.total.usd;
                const totalProfitEUR = record.data.profits.total.eur;
                let totalProfitDisplay = `$${totalProfitUSD.toFixed(2)}`;
                if (totalProfitEUR > 0) {
                    totalProfitDisplay += ` / €${totalProfitEUR.toFixed(2)}`;
                }
                
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
                    <td>${totalProfitDisplay}</td>
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
                historyTableBody.appendChild(row);
            });
        }
        
        // فلترة السجلات الشهرية
        function filterMonthlyHistory() {
            const filterMonth = document.getElementById('filter-month').value;
            
            if (!filterMonth) {
                loadMonthlyHistory();
                return;
            }
            
            const [year, month] = filterMonth.split('-');
            const filteredRecords = monthlyHistoryRecords.filter(record => 
                record.year == year && record.month == month
            );
            
            const monthlyHistoryTableBody = document.getElementById('monthly-history-table-body');
            const noMonthlyHistoryRow = document.getElementById('no-monthly-history');
            
            if (filteredRecords.length === 0) {
                noMonthlyHistoryRow.style.display = '';
                noMonthlyHistoryRow.innerHTML = `<td colspan="7" style="text-align: center; padding: 30px;">لا توجد سجلات لشهر ${getMonthName(month)} ${year} / ${getMonthName(month)} ${year} için kayıt bulunamadı.</td>`;
                return;
            }
            
            noMonthlyHistoryRow.style.display = 'none';
            monthlyHistoryTableBody.innerHTML = '';
            
            filteredRecords.forEach((record, index) => {
                const originalIndex = monthlyHistoryRecords.indexOf(record);
                const row = document.createElement('tr');
                
                // حساب إجمالي المصروفات بالدولار
                const totalExpenseUSD = record.data.totalExpenses.usd;
                const totalExpenseEUR = record.data.totalExpenses.eur;
                const totalExpenseTRY = record.data.totalExpenses.try;
                
                // عرض المصروفات بالعملات المختلفة
                let expenseDisplay = '';
                if (totalExpenseUSD > 0) expenseDisplay += `$${totalExpenseUSD.toFixed(2)} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${totalExpenseEUR.toFixed(2)} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${totalExpenseTRY.toFixed(2)}`;
                if (!expenseDisplay) expenseDisplay = '-';
                
                // حساب الصافي النهائي
                const usdNet = record.data.netProfit.usd;
                const eurNet = record.data.netProfit.eur;
                const tryNet = record.data.netProfit.try;
                
                let netDisplay = '';
                if (usdNet !== 0) netDisplay += `$${usdNet.toFixed(2)} `;
                if (eurNet !== 0) netDisplay += `€${eurNet.toFixed(2)} `;
                if (tryNet !== 0) netDisplay += `₺${tryNet.toFixed(2)}`;
                
                row.innerHTML = `
                    <td>${getMonthName(record.month)} ${record.year}</td>
                    <td style="color: ${record.data.netProfit.usd >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${record.data.netProfit.usd.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.netProfit.eur >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${record.data.netProfit.eur.toFixed(2)}
                    </td>
                    <td style="color: ${record.data.netProfit.try >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${record.data.netProfit.try.toFixed(2)}
                    </td>
                    <td>${expenseDisplay}</td>
                    <td>${netDisplay}</td>
                    <td class="no-print">
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem;" onclick="viewMonthlyRecord(${originalIndex})">
                            <i class="fas fa-eye"></i> عرض / Görüntüle
                        </button>
                        <button class="btn" style="padding: 5px 10px; font-size: 0.9rem; background: linear-gradient(135deg, #f44336, #c62828);" onclick="deleteMonthlyRecord(${originalIndex})">
                            <i class="fas fa-trash"></i> حذف / Sil
                        </button>
                    </td>
                `;
                monthlyHistoryTableBody.appendChild(row);
            });
        }
        
        // مسح جميع السجلس
        function clearHistory() {
            if (confirm("هل تريد مسح جميع السجلس السابقة؟ لا يمكن التراجع عن هذا الإجراء. / Tüm önceki kayıtları temizlemek istiyor musunuz? Bu işlem geri alınamaz.")) {
                historyRecords = [];
                localStorage.removeItem('alanhar_history');
                loadHistory();
                alert("تم مسح جميع السجلس بنجاح! / Tüm kayıtlar başarıyla temizlendi!");
            }
        }
        
        // مسح جميع السجلات الشهرية
        function clearMonthlyHistory() {
            if (confirm("هل تريد مسح جميع السجلات الشهرية؟ لا يمكن التراجع عن هذا الإجراء. / Tüm aylık kayıtları temizlemek istiyor musunuz? Bu işlem geri alınamaz.")) {
                monthlyHistoryRecords = [];
                localStorage.removeItem('alanhar_monthly_history');
                loadMonthlyHistory();
                alert("تم مسح جميع السجلات الشهرية بنجاح! / Tüm aylık kayıtlar başarıyla temizlendi!");
            }
        }
        
        // تبديل التبويبات
        function switchTab(tabId) {
            console.log("تبديل إلى تبويب:", tabId);
            
            // إخفاء جميع الأقسام
            document.querySelectorAll('.content-section').forEach(section => {
                section.classList.remove('active');
            });
            
            // إزالة النشاط من جميع التبويبات
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // إظهار القسم المحدد
            const targetSection = document.getElementById(tabId);
            if (targetSection) {
                targetSection.classList.add('active');
            } else {
                console.error("القسم غير موجود:", tabId);
            }
            
            // تفعيل التبويب المحدد
            const targetTab = document.querySelector(`[data-tab="${tabId}"]`);
            if (targetTab) {
                targetTab.classList.add('active');
            }
            
            // إذا كان التبويب هو التقرير، قم بتوليد التقرير تلقائياً
            if (tabId === 'report') {
                generateReport();
            }
            
            // إذا كان التبويب هو التقرير الشهري، قم بتحديث الحسابات
            if (tabId === 'monthly') {
                updateMonthlyCalculations();
            }
        }
        
        // تبديل نوع السجلات
        function switchHistoryType(type) {
            // إخفاء جميع أقسام السجلات
            document.getElementById('daily-history-section').classList.remove('active');
            document.getElementById('monthly-history-section').classList.remove('active');
            
            // إزالة النشاط من جميع تبويبات السجلات
            document.querySelectorAll('.history-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // إظهار القسم المحدد
            document.getElementById(`${type}-history-section`).classList.add('active');
            
            // تفعيل التبويب المحدد
            document.querySelector(`[data-history-type="${type}"]`).classList.add('active');
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
        
        // الحصول على اسم الشهر
        function getMonthName(monthNumber) {
            const months = [
                'يناير', 'فبراير', 'مارس', 'أبريل', 'مايو', 'يونيو',
                'يوليو', 'أغسطس', 'سبتمبر', 'أكتوبر', 'نوفمبر', 'ديسمبر'
            ];
            return months[monthNumber - 1] || '';
        }
    </script>
</body>
</html>
