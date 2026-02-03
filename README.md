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
        
        .monthly-card {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            border-left: 5px solid #8e24aa;
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
        
        .monthly-title {
            color: #8e24aa;
            border-bottom-color: #e1bee7;
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
        
        .monthly-currency-box {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            border-left: 5px solid #8e24aa;
        }
        
        .currency-title {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            color: #1a2980;
            font-weight: bold;
            font-size: 1.2rem;
        }
        
        .monthly-currency-title {
            color: #8e24aa;
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
        
        .monthly-currency-icon {
            background-color: #8e24aa;
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
        
        .monthly-input:focus, .monthly-select:focus {
            border-color: #8e24aa;
            box-shadow: 0 0 0 2px rgba(142, 36, 170, 0.1);
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
        
        .monthly-positive {
            background: linear-gradient(135deg, #8e24aa, #ab47bc);
            color: white;
        }
        
        .monthly-negative {
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
        
        .monthly-profit-item {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            border-top: 4px solid #8e24aa;
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
        
        .monthly-profit-total {
            background: linear-gradient(135deg, #c8e6c9, #a5d6a7);
            border: 2px solid #388e3c;
            color: #1b5e20;
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
            background: linear-gradient(135deg, #8e24aa, #6a1b9a);
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
        
        .monthly-expense-item {
            background: linear-gradient(135deg, #ffecb3, #ffd54f);
            border-left: 4px solid #ff8f00;
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
        
        .monthly-expense-total-box {
            background: linear-gradient(135deg, #ffcdd2, #ef9a9a);
            border: 2px solid #d32f2f;
        }
        
        .expense-currency {
            font-weight: bold;
            font-size: 1.2rem;
            color: #c62828;
            margin-top: 5px;
        }
        
        .monthly-expense-currency {
            color: #d32f2f;
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
        
        .monthly-table th {
            background-color: #8e24aa;
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
        
        .monthly-table tr:nth-child(even) {
            background-color: #f3e5f5;
        }
        
        .monthly-table tr:hover {
            background-color: #e1bee7;
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
        
        .monthly-summary-box {
            background: linear-gradient(135deg, #8e24aa, #ab47bc);
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
        
        /* تصميم التقرير الشهري المختصر الجديد */
        .compact-monthly-report {
            background: white;
            border-radius: 15px;
            padding: 0;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        .compact-report-header {
            background: linear-gradient(135deg, #8e24aa, #ab47bc);
            color: white;
            padding: 25px 30px;
            text-align: center;
        }
        
        .compact-report-header h2 {
            font-size: 2rem;
            margin-bottom: 10px;
        }
        
        .compact-date-range {
            font-size: 1.3rem;
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .compact-report-content {
            padding: 30px;
        }
        
        .compact-section {
            margin-bottom: 25px;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid;
        }
        
        .compact-section-title {
            font-size: 1.4rem;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid;
            display: flex;
            align-items: center;
        }
        
        .compact-section-title i {
            margin-left: 10px;
        }
        
        .compact-currency-section {
            border-color: #4caf50;
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
        }
        
        .compact-currency-title {
            color: #2e7d32;
            border-bottom-color: #a5d6a7;
        }
        
        .compact-profit-section {
            border-color: #ff9800;
            background: linear-gradient(135deg, #fff3e0, #ffe0b2);
        }
        
        .compact-profit-title {
            color: #ef6c00;
            border-bottom-color: #ffb74d;
        }
        
        .compact-expense-section {
            border-color: #f44336;
            background: linear-gradient(135deg, #ffebee, #ffcdd2);
        }
        
        .compact-expense-title {
            color: #d32f2f;
            border-bottom-color: #ef9a9a;
        }
        
        .compact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 15px;
        }
        
        .compact-grid-item {
            padding: 15px;
            border-radius: 8px;
            background: white;
            border: 1px solid #ddd;
        }
        
        .compact-grid-title {
            font-weight: bold;
            margin-bottom: 10px;
            padding-bottom: 5px;
            border-bottom: 1px solid #eee;
            color: #8e24aa;
        }
        
        .compact-value {
            font-size: 1.5rem;
            font-weight: bold;
            margin: 10px 0;
            text-align: center;
        }
        
        .compact-currency-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px 0;
            border-bottom: 1px dashed #eee;
        }
        
        .compact-currency-row:last-child {
            border-bottom: none;
        }
        
        .compact-total-row {
            background: rgba(142, 36, 170, 0.1);
            padding: 12px;
            border-radius: 8px;
            margin-top: 10px;
            font-weight: bold;
            border: 2px solid #8e24aa;
        }
        
        .compact-report-footer {
            padding: 20px 30px;
            border-top: 2px solid #8e24aa;
            text-align: center;
            color: #666;
            background: #f9f7fd;
        }
        
        .compact-note {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            padding: 15px;
            border-radius: 8px;
            border: 1px solid #8e24aa;
            text-align: center;
            margin-top: 20px;
            font-size: 0.95rem;
        }
        
        @media print {
            .no-print {
                display: none !important;
            }
            
            .container {
                width: 100%;
                max-width: 100%;
                padding: 0;
            }
            
            header, .tabs, footer, .actions, .warning, .info-box, .no-print {
                display: none !important;
            }
            
            .compact-monthly-report {
                box-shadow: none;
                border: 1px solid #ddd;
                page-break-inside: avoid;
                margin: 0;
                padding: 0;
                width: 100%;
                height: auto;
            }
            
            .compact-report-header {
                color: #8e24aa;
                background: white !important;
                border-bottom: 3px solid #8e24aa;
            }
            
            .compact-report-header h2 {
                color: #8e24aa;
            }
            
            .compact-date-range {
                color: #666;
            }
            
            .compact-section {
                page-break-inside: avoid;
                break-inside: avoid;
            }
            
            .compact-grid-item {
                page-break-inside: avoid;
                break-inside: avoid;
            }
            
            body {
                background: white;
                padding: 10px;
                font-size: 12pt;
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
        
        .monthly-warning {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            border-right: 5px solid #8e24aa;
        }
        
        .warning i {
            color: #ff9800;
            margin-left: 10px;
        }
        
        .monthly-warning i {
            color: #8e24aa;
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
        
        .monthly-add-btn {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            border: 2px dashed #8e24aa;
            color: #8e24aa;
        }
        
        .add-expense-btn:hover {
            background-color: #e1edff;
        }
        
        .monthly-add-btn:hover {
            background: linear-gradient(135deg, #e1bee7, #ce93d8);
        }
        
        .info-box {
            background-color: #e3f2fd;
            padding: 10px 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            border-right: 4px solid #2196f3;
        }
        
        .monthly-info-box {
            background: linear-gradient(135deg, #e1bee7, #ce93d8);
            border-right: 4px solid #8e24aa;
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
        
        .monthly-header {
            border-bottom: 2px solid #8e24aa;
        }
        
        .report-header h2 {
            color: #1a2980;
            font-size: 1.8rem;
            margin-bottom: 10px;
        }
        
        .monthly-header h2 {
            color: #8e24aa;
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
        
        .monthly-profit-label {
            color: #8e24aa;
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
        
        .monthly-profit-display {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
        }

        .profit-display-total {
            background: #e8f5e9;
            font-weight: bold;
            color: #2e7d32;
            border: 1px solid #4caf50;
        }
        
        .monthly-profit-total-display {
            background: linear-gradient(135deg, #c8e6c9, #a5d6a7);
            border: 1px solid #388e3c;
            color: #1b5e20;
        }
        
        .monthly-section {
            background: linear-gradient(135deg, #f9f7fd, #f3e5f5);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 25px;
            border: 2px solid #8e24aa;
        }
        
        .monthly-section-title {
            color: #8e24aa;
            font-size: 1.5rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #e1bee7;
            display: flex;
            align-items: center;
        }
        
        .monthly-section-title i {
            margin-left: 10px;
        }
        
        .month-selection {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }
        
        .month-selector {
            flex: 1;
            min-width: 200px;
        }
        
        .date-range-selector {
            display: flex;
            gap: 10px;
            align-items: center;
        }
        
        .date-range-box {
            flex: 1;
            min-width: 200px;
        }
        
        .date-range-info {
            background: linear-gradient(135deg, #e3f2fd, #bbdefb);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            border-right: 5px solid #2196f3;
            text-align: center;
            font-weight: bold;
        }
        
        .monthly-data-section {
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 2px solid #4caf50;
        }
        
        .monthly-data-title {
            color: #2e7d32;
            font-size: 1.4rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #a5d6a7;
            display: flex;
            align-items: center;
        }
        
        .monthly-data-title i {
            margin-left: 10px;
        }
        
        .auto-profit-section {
            background: linear-gradient(135deg, #fff3e0, #ffe0b2);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 2px solid #ff9800;
        }
        
        .auto-profit-title {
            color: #ef6c00;
            font-size: 1.4rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #ffb74d;
            display: flex;
            align-items: center;
        }
        
        .auto-profit-title i {
            margin-left: 10px;
        }
        
        .summary-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 15px;
            margin: 5px 0;
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.7);
        }
        
        .summary-row-total {
            background: rgba(255, 255, 255, 0.9);
            font-weight: bold;
            border: 2px solid #8e24aa;
        }
        
        .print-only {
            display: none;
        }
        
        @media print {
            .print-only {
                display: block;
            }
        }
        
        /* قسم تفاصيل الأرباح اليومية المجمعة */
        .detailed-profit-section {
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 2px solid #4caf50;
        }
        
        .detailed-profit-title {
            color: #2e7d32;
            font-size: 1.4rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #a5d6a7;
            display: flex;
            align-items: center;
        }
        
        .detailed-profit-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        
        .detailed-profit-table th {
            background-color: #4caf50;
            color: white;
            padding: 12px;
            text-align: right;
        }
        
        .detailed-profit-table td {
            padding: 10px 12px;
            border-bottom: 1px solid #c8e6c9;
        }
        
        .detailed-profit-table tr:nth-child(even) {
            background-color: rgba(255, 255, 255, 0.5);
        }
        
        .profit-summary-box {
            background: linear-gradient(135deg, #4caf50, #2e7d32);
            color: white;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            text-align: center;
        }
        
        .profit-summary-value {
            font-size: 2rem;
            margin: 10px 0;
            font-weight: bold;
        }
        
        .day-profit-item {
            background: linear-gradient(135deg, #f3e5f5, #e1bee7);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 10px;
            border-left: 4px solid #8e24aa;
        }
        
        .day-profit-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            padding-bottom: 5px;
            border-bottom: 1px solid #ce93d8;
        }
        
        .day-profit-date {
            font-weight: bold;
            color: #8e24aa;
            font-size: 1.1rem;
        }
        
        .day-profit-total {
            font-weight: bold;
            color: #4caf50;
        }
        
        .day-profit-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 10px;
            margin-top: 10px;
        }
        
        .profit-type-item {
            background: white;
            padding: 10px;
            border-radius: 6px;
            border: 1px solid #e0e0e0;
        }
        
        .profit-type-title {
            font-weight: bold;
            color: #8e24aa;
            margin-bottom: 5px;
        }
        
        /* قسم تلقائي لتجميع الأرباح */
        .auto-collect-section {
            background: linear-gradient(135deg, #bbdefb, #90caf9);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 2px solid #2196f3;
        }
        
        .auto-collect-title {
            color: #0d47a1;
            font-size: 1.4rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #64b5f6;
            display: flex;
            align-items: center;
        }
        
        .auto-collect-title i {
            margin-left: 10px;
        }
        
        .auto-collect-info {
            background: rgba(255, 255, 255, 0.9);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            border-right: 4px solid #2196f3;
        }
        
        .auto-collect-stats {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 15px;
        }
        
        .collect-stat-item {
            flex: 1;
            min-width: 150px;
            background: white;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            border-top: 4px solid #2196f3;
        }
        
        .collect-stat-value {
            font-size: 1.8rem;
            font-weight: bold;
            color: #0d47a1;
            margin: 10px 0;
        }
        
        .collect-stat-label {
            color: #666;
            font-size: 0.9rem;
        }

        /* قسم الفضة الجديد */
        .silver-box {
            background: linear-gradient(135deg, #fff8e1, #ffecb3);
            border-left: 5px solid #ff9800;
        }
        
        .silver-title {
            color: #ff8f00;
        }
        
        .silver-icon {
            background-color: #ff9800;
        }
        
        .silver-value-box {
            background: linear-gradient(135deg, #fff3e0, #ffe0b2);
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2rem;
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
        
        /* أنماط التقرير للفضة */
        .report-silver-section {
            background: linear-gradient(135deg, #fff8e1, #ffecb3);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 2px solid #ff9800;
        }
        
        .report-silver-title {
            color: #ff8f00;
            font-size: 1.4rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #ffcc80;
            display: flex;
            align-items: center;
        }
        
        .report-silver-title i {
            margin-left: 10px;
        }
        
        /* أنماط طباعة الفضة */
        @media print {
            .report-silver-section {
                background: #fff8e1 !important;
                border: 1px solid #ff9800;
            }
            
            .real-surplus-box {
                background: #e8f5e9 !important;
                border: 1px solid #4caf50;
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
                <i class="fas fa-calculator"></i> إدخال البيانات اليومية / Günlük Veri Girişi
            </div>
            <div class="tab" data-tab="report">
                <i class="fas fa-chart-line"></i> التقرير اليومي / Günlük Rapor
            </div>
            <div class="tab monthly-tab" data-tab="monthly">
                <i class="fas fa-calendar-alt"></i> التقرير الشهري / Aylık Rapor
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
                    
                    <!-- الفضة الجديدة (معدلة بالكيلو والإجمالي) -->
                    <div class="currency-box silver-box">
                        <div class="currency-title silver-title">
                            <div class="currency-icon silver-icon">
                                <i class="fas fa-gem"></i>
                            </div>
                            <div>الفضة (بالكيلو) / Gümüş (kg)</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="silver-quantity">الكمية (كيلو) / Miktar (kg)</label>
                            <div class="label-tr">Gümüş miktarı kilogram cinsinden</div>
                            <input type="number" id="silver-quantity" placeholder="أدخل كمية الفضة بالكيلو / Gümüş miktarını kilogram olarak girin" step="0.001" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="silver-total-input">القيمة الإجمالية ($) / Toplam Değer ($)</label>
                            <div class="label-tr">Toplam dolar değeri</div>
                            <input type="number" id="silver-total-input" placeholder="أدخل القيمة الإجمالية بالدولار / Toplam değeri dolar olarak girin" step="0.01" min="0">
                        </div>
                        
                        <div id="silver-value" class="silver-value-box">
                            القيمة الإجمالية للفضة: $<span id="silver-total-display">0.00</span>
                        </div>
                    </div>
                </div>
                
                <!-- مربع الفائض الحقيقي -->
                <div id="real-surplus-box" class="real-surplus-box">
                    <div style="font-size: 1.2rem; margin-bottom: 10px;">
                        <i class="fas fa-calculator"></i> الفائض الحقيقي / Gerçek Kar-Zarar
                    </div>
                    <div style="display: flex; justify-content: space-around; flex-wrap: wrap;">
                        <div style="text-align: center; margin: 10px;">
                            <div>فائض الدولار / Dolar Kar-Zarar</div>
                            <div style="font-size: 1.5rem; font-weight: bold; color: #1a2980;" id="display-usd-surplus">$0.00</div>
                        </div>
                        <div style="text-align: center; margin: 10px;">
                            <div>ناقص قيمة الفضة / Eksi Gümüş Değeri</div>
                            <div style="font-size: 1.5rem; font-weight: bold; color: #ff9800;" id="display-silver-value">$0.00</div>
                        </div>
                        <div style="text-align: center; margin: 10px;">
                            <div>الفائض الحقيقي / Gerçek Kar-Zarar</div>
                            <div class="real-surplus-value" id="real-surplus">$0.00</div>
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
                        <!-- سيتم إضافة مصروفات ديناميكياً هنا -->
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
            
            <!-- قسم الفضة الجديد في التقرير -->
            <div class="report-silver-section">
                <div class="report-silver-title">
                    <i class="fas fa-gem"></i> بيانات الفضة / Gümüş Verileri
                </div>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px;">
                    <div style="background: white; padding: 20px; border-radius: 10px; border: 1px solid #ffcc80;">
                        <div style="font-weight: bold; color: #ff8f00; margin-bottom: 10px;">الكمية (كيلو) / Miktar (kg)</div>
                        <div style="font-size: 1.5rem; text-align: center;">
                            <span id="report-silver-quantity">0.00</span> كيلو / kg
                        </div>
                    </div>
                    <div style="background: white; padding: 20px; border-radius: 10px; border: 1px solid #ffcc80;">
                        <div style="font-weight: bold; color: #ff8f00; margin-bottom: 10px;">القيمة الإجمالية / Toplam Değer</div>
                        <div style="font-size: 1.5rem; text-align: center; font-weight: bold; color: #ff9800;">
                            $<span id="report-silver-total">0.00</span>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- قسم الفائض الحقيقي في التقرير -->
            <div class="real-surplus-box" style="margin-top: 20px;">
                <div style="font-size: 1.3rem; margin-bottom: 15px; display: flex; align-items: center; justify-content: center;">
                    <i class="fas fa-calculator" style="margin-left: 10px;"></i>
                    <span>الفائض الحقيقي / Gerçek Kar-Zarar</span>
                </div>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px;">
                    <div style="text-align: center; padding: 15px; background: rgba(26, 41, 128, 0.1); border-radius: 8px;">
                        <div style="font-size: 1.1rem; margin-bottom: 10px;">فائض الدولار / Dolar Kar-Zarar</div>
                        <div style="font-size: 1.8rem; font-weight: bold; color: #1a2980;" id="report-display-usd-surplus">$0.00</div>
                    </div>
                    <div style="text-align: center; padding: 15px; background: rgba(255, 152, 0, 0.1); border-radius: 8px;">
                        <div style="font-size: 1.1rem; margin-bottom: 10px;">ناقص قيمة الفضة / Eksi Gümüş Değeri</div>
                        <div style="font-size: 1.8rem; font-weight: bold; color: #ff9800;" id="report-display-silver-value">$0.00</div>
                    </div>
                    <div style="text-align: center; padding: 15px; background: rgba(76, 175, 80, 0.1); border-radius: 8px; border: 2px solid #4caf50;">
                        <div style="font-size: 1.1rem; margin-bottom: 10px; font-weight: bold;">الفائض الحقيقي / Gerçek Kar-Zarar</div>
                        <div class="real-surplus-value" id="report-real-surplus">$0.00</div>
                    </div>
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
                            <span id="report-silver-profit-usd">0.00</span>
                        </div>
                        <div class="profit-display">
                            <span>€</span>
                            <span id="report-silver-profit-eur">0.00</span>
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
            <div class="report-header monthly-header">
                <h2>تقرير شهري مختصر - نظام ALANHAR</h2>
                <div class="date" id="monthly-report-date">التقرير الشهري / Aylık Rapor</div>
                <div class="subtitle-tr">Özet Aylık Rapor - ALANHAR Sistemi</div>
            </div>
            
            <div class="monthly-warning no-print">
                <i class="fas fa-calendar-alt"></i>
                <strong>ملاحظة / Not:</strong> أدخل بيانات المدين والدائن يدوياً، وسيتم جمع أرباح Swift والفضة والحوالة تلقائياً من السجلات السابقة. المصاريف والأرباح التلقائية للمعلومية فقط ولا تزيد أو تنقص من الفائض. / Borçlu ve Alacaklı verilerini elle girin, Swift, Gümüş ve Havale kârları otomatik olarak önceki kayıtlardan toplanacaktır. Giderler ve otomatik kârlar sadece bilgi amaçlıdır ve kar-zarardan eklenmez veya çıkarılmaz.
            </div>
            
            <!-- قسم التجميع التلقائي للأرباح -->
            <div class="auto-collect-section">
                <div class="auto-collect-title">
                    <i class="fas fa-calculator"></i> التجميع التلقائي للأرباح / Otomatik Kâr Toplama
                </div>
                
                <div class="auto-collect-info">
                    <p><strong>تفسير:</strong> سيتم تجميع جميع عمليات الربح (Swift، Havala، الفضة) تلقائياً عند اختيار الفترة الزمنية. كل عملية حفظ يومية يتم تجميعها مع العمليات السابقة.</p>
                    <p><strong>Açıklama:</strong> Tüm kâr işlemleri (Swift, Havale, Gümüş) otomatik olarak zaman aralığı seçildiğinde toplanacaktır. Her günlük kayıt işlemi, önceki işlemlerle toplanır.</p>
                </div>
                
                <div class="date-range-selector">
                    <div class="date-range-box">
                        <div class="input-group">
                            <label for="monthly-start-date">تاريخ البداية / Başlangıç Tarihi</label>
                            <input type="date" id="monthly-start-date" class="monthly-input">
                        </div>
                    </div>
                    
                    <div style="display: flex; align-items: center; padding-top: 20px;">
                        <i class="fas fa-arrow-left" style="font-size: 1.5rem; color: #2196f3;"></i>
                    </div>
                    
                    <div class="date-range-box">
                        <div class="input-group">
                            <label for="monthly-end-date">تاريخ النهاية / Bitiş Tarihi</label>
                            <input type="date" id="monthly-end-date" class="monthly-input">
                        </div>
                    </div>
                </div>
                
                <div id="date-range-info" class="date-range-info">
                    <!-- سيتم عرض معلومات الفترة الزمنية هنا -->
                </div>
                
                <div id="auto-collect-stats" class="auto-collect-stats">
                    <!-- ستظهر إحصائيات التجميع التلقائي هنا -->
                </div>
            </div>
            
            <!-- قسم تفاصيل الأرباح اليومية المجمعة -->
            <div class="detailed-profit-section">
                <div class="detailed-profit-title">
                    <i class="fas fa-coins"></i> تفاصيل الأرباح اليومية المجمعة / Günlük Kârların Detaylı Özeti
                </div>
                
                <div id="detailed-profits-container">
                    <!-- سيتم عرض تفاصيل الأرباح هنا -->
                    <div style="text-align: center; padding: 20px; color: #666;">
                        قم بتحديد الفترة الزمنية لعرض الأرباح المجمعة / Zaman aralığını seçerek toplanan kârları görüntüleyin.
                    </div>
                </div>
                
                <div id="profit-summary" class="profit-summary-box" style="display: none;">
                    <div class="summary-label">إجمالي الأرباح المجمعة / Toplam Birikmiş Kâr</div>
                    <div class="profit-summary-value">
                        <span id="total-monthly-profit-usd">$0.00</span> /
                        <span id="total-monthly-profit-eur">€0.00</span>
                    </div>
                    <div>من <span id="profit-days-count">0</span> يوم / <span id="profit-days-count-tr">0</span> gün</div>
                    <div>عدد العمليات: <span id="profit-operations-count">0</span> / İşlem Sayısı: <span id="profit-operations-count-tr">0</span></div>
                </div>
            </div>
            
            <!-- نموذج إدخال بيانات المدين والدائن الشهرية -->
            <div class="monthly-data-section no-print">
                <div class="monthly-data-title">
                    <i class="fas fa-money-bill-wave"></i> إدخال بيانات المدين والدائن الشهرية / Aylık Borçlu ve Alacaklı Veri Girişi
                </div>
                
                <div class="currency-container">
                    <!-- الدولار الأمريكي -->
                    <div class="currency-box monthly-currency-box">
                        <div class="currency-title monthly-currency-title">
                            <div class="currency-icon monthly-currency-icon">$</div>
                            <div>الدولار الأمريكي (USD) / Amerikan Doları</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-usd-debtor">المدين الشهري (الخروج) / Aylık Borçlu (Çıkış)</label>
                            <div class="label-tr">Aylık çıkan para miktarı</div>
                            <input type="number" id="monthly-usd-debtor" class="monthly-input" placeholder="أدخل قيمة المدين الشهري بالدولار / Aylık dolar borçlu değerini girin" step="0.01" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-usd-creditor">الدائن الشهري (الدخول) / Aylık Alacaklı (Giriş)</label>
                            <div class="label-tr">Aylık giren para miktarı</div>
                            <input type="number" id="monthly-usd-creditor" class="monthly-input" placeholder="أدخل قيمة الدائن الشهري بالدولار / Aylık dolar alacaklı değerini girin" step="0.01" min="0">
                        </div>
                        
                        <div id="monthly-usd-surplus" class="result-box monthly-positive">
                            الفائض الشهري / Aylık Kar-Zarar: $0.00
                        </div>
                    </div>
                    
                    <!-- اليورو -->
                    <div class="currency-box monthly-currency-box">
                        <div class="currency-title monthly-currency-title">
                            <div class="currency-icon monthly-currency-icon">€</div>
                            <div>اليورو الأوروبي (EUR) / Euro</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-eur-debtor">المدين الشهري (الخروج) / Aylık Borçlu (Çıkış)</label>
                            <div class="label-tr">Aylık çıkan para miktarı</div>
                            <input type="number" id="monthly-eur-debtor" class="monthly-input" placeholder="أدخل قيمة المدين الشهري باليورو / Aylık euro borçlu değerini girin" step="0.01" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-eur-creditor">الدائن الشهري (الدخول) / Aylık Alacaklı (Giriş)</label>
                            <div class="label-tr">Aylık giren para miktarı</div>
                            <input type="number" id="monthly-eur-creditor" class="monthly-input" placeholder="أدخل قيمة الدائن الشهري باليورو / Aylık euro alacaklı değerini girin" step="0.01" min="0">
                        </div>
                        
                        <div id="monthly-eur-surplus" class="result-box monthly-positive">
                            الفائض الشهري / Aylık Kar-Zarar: €0.00
                        </div>
                    </div>
                    
                    <!-- الليرة التركية -->
                    <div class="currency-box monthly-currency-box">
                        <div class="currency-title monthly-currency-title">
                            <div class="currency-icon monthly-currency-icon">₺</div>
                            <div>الليرة التركية (TRY) / Türk Lirası</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-try-debtor">المدين الشهري (الخروج) / Aylık Borçlu (Çıkış)</label>
                            <div class="label-tr">Aylık çıkan para miktarı</div>
                            <input type="number" id="monthly-try-debtor" class="monthly-input" placeholder="أدخل قيمة المدين الشهري بالليرة / Aylık lira borçlu değerini girin" step="0.01" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="monthly-try-creditor">الدائن الشهري (الدخول) / Aylık Alacaklı (Giriş)</label>
                            <div class="label-tr">Aylık giren para miktarı</div>
                            <input type="number" id="monthly-try-creditor" class="monthly-input" placeholder="أدخل قيمة الدائن الشهري بالليرة / Aylık lira alacaklı değerini girin" step="0.01" min="0">
                        </div>
                        
                        <div id="monthly-try-surplus" class="result-box monthly-positive">
                            الفائض الشهري / Aylık Kar-Zarar: ₺0.00
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- قسم تحميل الأرباح التلقائية -->
            <div class="auto-profit-section no-print">
                <div class="auto-profit-title">
                    <i class="fas fa-coins"></i> الأرباح التلقائية من السجلات السابقة / Önceki Kayıtlardan Otomatik Kârlar
                </div>
                
                <div class="profit-container">
                    <div class="profit-item monthly-profit-item">
                        <h4>ربح Swift المجمع / Toplanan Swift Kârı</h4>
                        <div class="summary-row">
                            <span>من <span id="auto-swift-start">--</span> إلى <span id="auto-swift-end">--</span></span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>$</span>
                            <span id="auto-swift-usd">0.00</span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>€</span>
                            <span id="auto-swift-eur">0.00</span>
                        </div>
                    </div>
                    <div class="profit-item monthly-profit-item">
                        <h4>ربح Havala المجمع / Toplanan Havale Kârı</h4>
                        <div class="summary-row">
                            <span>من <span id="auto-havala-start">--</span> إلى <span id="auto-havala-end">--</span></span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>$</span>
                            <span id="auto-havala-usd">0.00</span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>€</span>
                            <span id="auto-havala-eur">0.00</span>
                        </div>
                    </div>
                    <div class="profit-item monthly-profit-item">
                        <h4>ربح الفضة المجمع / Toplanan Gümüş Kârı</h4>
                        <div class="summary-row">
                            <span>من <span id="auto-silver-start">--</span> إلى <span id="auto-silver-end">--</span></span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>$</span>
                            <span id="auto-silver-usd">0.00</span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>€</span>
                            <span id="auto-silver-eur">0.00</span>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- قسم المصروفات الشهرية -->
            <div class="monthly-section no-print">
                <div class="monthly-section-title">
                    <i class="fas fa-receipt"></i> المصروفات الشهرية / Aylık Giderler
                </div>
                
                <div id="monthly-expenses-container">
                    <div class="expense-container" id="monthly-expenses-list">
                        <!-- سيتم إضافة مصروفات شهرية ديناميكياً هنا -->
                        <div class="expense-item monthly-expense-item" id="monthly-expense-item-1">
                            <div class="input-group">
                                <label for="monthly-expense-name-1">وصف المصروف / Gider Açıklaması</label>
                                <select id="monthly-expense-name-1" class="monthly-select monthly-expense-type">
                                    <option value="rent">إيجار المحل / Dükkan Kirası</option>
                                    <option value="electricity">كهرباء / Elektrik</option>
                                    <option value="water">ماء / Su</option>
                                    <option value="salary">رواتب / Maaşlar</option>
                                    <option value="food">مصاريف أكل / Yemek Masrafları</option>
                                    <option value="living">مصاريف معيشة / Yaşam Masrafları</option>
                                    <option value="other">أخرى / Diğer</option>
                                </select>
                            </div>
                            
                            <div class="input-group">
                                <label for="monthly-expense-amount-1">القيمة / Tutar</label>
                                <input type="number" id="monthly-expense-amount-1" class="monthly-input" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                            </div>
                            
                            <div class="input-group">
                                <label for="monthly-expense-currency-1">العملة / Para Birimi</label>
                                <select id="monthly-expense-currency-1" class="monthly-select">
                                    <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                                    <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                                    <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                                </select>
                            </div>
                            
                            <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="1">
                                <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                            </button>
                        </div>
                    </div>
                </div>
                
                <div class="add-expense-btn monthly-add-btn no-print" id="add-monthly-expense">
                    <i class="fas fa-plus-circle"></i> إضافة مصروف شهري جديد / Yeni Aylık Gider Ekle
                </div>
            </div>
            
            <!-- التقرير الشهري المختصر الجديد -->
            <div id="compact-monthly-report" class="compact-monthly-report" style="display: none;">
                <div class="compact-report-header">
                    <h2>تقرير شهري مختصر - نظام ALANHAR</h2>
                    <div class="compact-date-range" id="compact-date-range">الفترة: من -- إلى --</div>
                    <div style="margin-top: 5px; font-size: 1.1rem;">Aylık Özet Rapor - ALANHAR Sistemi</div>
                </div>
                
                <div class="compact-report-content">
                    <!-- قسم فائض العملات -->
                    <div class="compact-section compact-currency-section">
                        <div class="compact-section-title compact-currency-title">
                            <i class="fas fa-money-bill-wave"></i> فائض العملات الشهري / Aylık Döviz Kar-Zarar
                        </div>
                        <div class="compact-grid">
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">الدولار الأمريكي (USD) / Amerikan Doları</div>
                                <div class="compact-currency-row">
                                    <span>المدين (الخروج) / Borçlu (Çıkış)</span>
                                    <span id="compact-usd-debtor">$0.00</span>
                                </div>
                                <div class="compact-currency-row">
                                    <span>الدائن (الدخول) / Alacaklı (Giriş)</span>
                                    <span id="compact-usd-creditor">$0.00</span>
                                </div>
                                <div class="compact-currency-row compact-total-row">
                                    <span>الفائض / Kar-Zarar</span>
                                    <span id="compact-usd-surplus">$0.00</span>
                                </div>
                            </div>
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">اليورو الأوروبي (EUR) / Euro</div>
                                <div class="compact-currency-row">
                                    <span>المدين (الخروج) / Borçlu (Çıkış)</span>
                                    <span id="compact-eur-debtor">€0.00</span>
                                </div>
                                <div class="compact-currency-row">
                                    <span>الدائن (الدخول) / Alacaklı (Giriş)</span>
                                    <span id="compact-eur-creditor">€0.00</span>
                                </div>
                                <div class="compact-currency-row compact-total-row">
                                    <span>الفائض / Kar-Zarar</span>
                                    <span id="compact-eur-surplus">€0.00</span>
                                </div>
                            </div>
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">الليرة التركية (TRY) / Türk Lirası</div>
                                <div class="compact-currency-row">
                                    <span>المدين (الخروج) / Borçlu (Çıkış)</span>
                                    <span id="compact-try-debtor">₺0.00</span>
                                </div>
                                <div class="compact-currency-row">
                                    <span>الدائن (الدخول) / Alacaklı (Giriş)</span>
                                    <span id="compact-try-creditor">₺0.00</span>
                                </div>
                                <div class="compact-currency-row compact-total-row">
                                    <span>الفائض / Kar-Zarar</span>
                                    <span id="compact-try-surplus">₺0.00</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- قسم الأرباح التلقائية -->
                    <div class="compact-section compact-profit-section">
                        <div class="compact-section-title compact-profit-title">
                            <i class="fas fa-coins"></i> الأرباح التلقائية / Otomatik Kârlar
                        </div>
                        <div class="compact-grid">
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">ربح Swift / Swift Kârı</div>
                                <div class="compact-value" id="compact-swift-usd">$0.00</div>
                                <div class="compact-value" id="compact-swift-eur">€0.00</div>
                            </div>
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">ربح Havala / Havale Kârı</div>
                                <div class="compact-value" id="compact-havala-usd">$0.00</div>
                                <div class="compact-value" id="compact-havala-eur">€0.00</div>
                            </div>
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">ربح الفضة / Gümüş Kârı</div>
                                <div class="compact-value" id="compact-silver-usd">$0.00</div>
                                <div class="compact-value" id="compact-silver-eur">€0.00</div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- قسم المصروفات -->
                    <div class="compact-section compact-expense-section">
                        <div class="compact-section-title compact-expense-title">
                            <i class="fas fa-receipt"></i> المصروفات الشهرية / Aylık Giderler
                        </div>
                        <div class="compact-grid" id="compact-expenses-list">
                            <!-- سيتم إضافة المصروفات ديناميكياً هنا -->
                            <div style="text-align: center; padding: 20px; color: #666; grid-column: 1 / -1;">
                                لا توجد مصروفات مسجلة / Kayıtlı gider yok
                            </div>
                        </div>
                    </div>
                    
                    <!-- ملاحظة -->
                    <div class="compact-note">
                        <strong>ملاحظة:</strong> المصاريف والأرباح التلقائية للمعلومية فقط ولا تزيد أو تنقص من الفائض.<br>
                        <strong>Not:</strong> Giderler ve otomatik kârlar sadece bilgi amaçlıdır ve kar-zarardan eklenmez veya çıkarılmaz.
                    </div>
                </div>
                
                <!-- تذييل التقرير -->
                <div class="compact-report-footer">
                    <div>نظام ALANHAR لإدارة محلات الصرافة والحوالات</div>
                    <div>ALANHAR Sistemi - Döviz ve Havale Yönetimi</div>
                    <div style="margin-top: 10px;">تم الإنشاء في: <span id="compact-creation-date">--</span> / Oluşturulma Tarihi: <span id="compact-creation-date-tr">--</span></div>
                </div>
            </div>
            
            <div class="actions no-print" style="margin-top: 30px;">
                <button class="btn btn-print" id="print-monthly-report">
                    <i class="fas fa-print"></i> طباعة التقرير الشهري / Aylık Raporu Yazdır
                </button>
                <button class="btn btn-save" id="save-monthly-data">
                    <i class="fas fa-save"></i> حفظ البيانات / Verileri Kaydet
                </button>
                <button class="btn btn-reset" id="reset-monthly-data">
                    <i class="fas fa-redo"></i> مسح البيانات / Verileri Temizle
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
                                <th>قيمة الفضة / Gümüş Değeri</th>
                                <th>الفائض الحقيقي / Gerçek Kar-Zarar</th>
                                <th>إجمالي الأرباح / Toplam Kâr</th>
                                <th>المصروفات / Giderler</th>
                                <th class="no-print">الإجراءات / İşlemler</th>
                            </tr>
                        </thead>
                        <tbody id="history-table-body">
                            <!-- سيتم ملء الجدول ديناميكياً -->
                            <tr id="no-history">
                                <td colspan="9" style="text-align: center; padding: 30px;">لا توجد سجلات سابقة. ابدأ بإدخال بيانات اليوم. / Önceki kayıt yok. Bugünün verilerini girmeye başlayın.</td>
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
            silver: { quantity: 0, total: 0 }, // تغيير: total بدلاً من price
            realSurplus: 0, // الفائض الحقيقي
            profits: { 
                swift: { usd: 0, eur: 0 }, 
                havana: { usd: 0, eur: 0 }, 
                silver: { usd: 0, eur: 0 },
                total: { usd: 0, eur: 0 }
            },
            expenses: [],
            date: new Date().toISOString().split('T')[0],
            timestamp: new Date().getTime()
        };

        // بيانات التقرير الشهري
        let monthlyData = {
            startDate: '',
            endDate: '',
            usd: { debtor: 0, creditor: 0, surplus: 0 },
            eur: { debtor: 0, creditor: 0, surplus: 0 },
            try: { debtor: 0, creditor: 0, surplus: 0 },
            autoProfits: {
                swift: { usd: 0, eur: 0 },
                havana: { usd: 0, eur: 0 },
                silver: { usd: 0, eur: 0 }
            },
            monthlyExpenses: [],
            detailedProfits: []
        };

        // سجلات الأيام السابقة
        let historyRecords = JSON.parse(localStorage.getItem('alanhar_history')) || [];
        
        // سجلات التقارير الشهرية
        let monthlyRecords = JSON.parse(localStorage.getItem('alanhar_monthly')) || [];
        
        // سجلات الأرباح اليومية (كل عملية حفظ)
        let dailyProfitOperations = JSON.parse(localStorage.getItem('alanhar_daily_profit_operations')) || [];
        
        // عداد المصروفات
        let expenseCounter = 1;
        let monthlyExpenseCounter = 1;
        
        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('report-date').textContent = `التاريخ: ${formatDate(today)} / Tarih: ${formatDate(today)}`;
            
            const currentDate = new Date();
            const firstDayOfMonth = new Date(currentDate.getFullYear(), currentDate.getMonth(), 1);
            const lastDayOfMonth = new Date(currentDate.getFullYear(), currentDate.getMonth() + 1, 0);
            
            const startDateStr = firstDayOfMonth.toISOString().split('T')[0];
            const endDateStr = lastDayOfMonth.toISOString().split('T')[0];
            
            document.getElementById('monthly-start-date').value = startDateStr;
            document.getElementById('monthly-end-date').value = endDateStr;
            
            monthlyData.startDate = startDateStr;
            monthlyData.endDate = endDateStr;
            
            updateDateRangeInfo();
            loadHistory();
            document.getElementById('add-expense').addEventListener('click', addNewExpense);
            document.getElementById('add-monthly-expense').addEventListener('click', addNewMonthlyExpense);
            document.getElementById('save-data').addEventListener('click', saveData);
            document.getElementById('generate-report').addEventListener('click', generateReport);
            document.getElementById('print-monthly-report').addEventListener('click', printMonthlyReport);
            document.getElementById('print-report').addEventListener('click', function() {
                printDailyReport(); // استدعاء الدالة الجديدة
            });
            document.getElementById('save-monthly-data').addEventListener('click', saveMonthlyData);
            document.getElementById('reset-data').addEventListener('click', resetData);
            document.getElementById('reset-monthly-data').addEventListener('click', resetMonthlyData);
            document.getElementById('back-to-input').addEventListener('click', () => switchTab('input'));
            document.getElementById('clear-history').addEventListener('click', clearHistory);
            document.getElementById('filter-date').addEventListener('change', filterHistory);
            
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });
            
            setupRemoveExpenseListeners();
            setupRemoveMonthlyExpenseListeners();
            setupInputListeners();
            updateExpensesTotal();
            updateCalculations();
            setupMonthlyInputListeners();
            document.getElementById('monthly-start-date').addEventListener('change', autoCollectProfits);
            document.getElementById('monthly-end-date').addEventListener('change', autoCollectProfits);
            updateDailyProfitsCount();
            setTimeout(autoCollectProfits, 500);
        });
        
        function updateDailyProfitsCount() {
            console.log(`عدد عمليات الربح اليومية: ${dailyProfitOperations.length}`);
        }
        
        function setupMonthlyInputListeners() {
            document.getElementById('monthly-usd-debtor').addEventListener('input', updateMonthlyCalculations);
            document.getElementById('monthly-usd-creditor').addEventListener('input', updateMonthlyCalculations);
            document.getElementById('monthly-eur-debtor').addEventListener('input', updateMonthlyCalculations);
            document.getElementById('monthly-eur-creditor').addEventListener('input', updateMonthlyCalculations);
            document.getElementById('monthly-try-debtor').addEventListener('input', updateMonthlyCalculations);
            document.getElementById('monthly-try-creditor').addEventListener('input', updateMonthlyCalculations);
        }
        
        function updateDateRangeInfo() {
            const startDate = monthlyData.startDate;
            const endDate = monthlyData.endDate;
            
            if (startDate && endDate) {
                const startFormatted = formatDate(startDate);
                const endFormatted = formatDate(endDate);
                
                document.getElementById('date-range-info').innerHTML = `
                    <i class="fas fa-calendar-check"></i> 
                    الفترة المحددة: من ${startFormatted} إلى ${endFormatted} / 
                    Seçilen Dönem: ${startFormatted} - ${endFormatted}
                `;
                
                document.getElementById('auto-swift-start').textContent = formatDateShort(startDate);
                document.getElementById('auto-swift-end').textContent = formatDateShort(endDate);
                document.getElementById('auto-havala-start').textContent = formatDateShort(startDate);
                document.getElementById('auto-havala-end').textContent = formatDateShort(endDate);
                document.getElementById('auto-silver-start').textContent = formatDateShort(startDate);
                document.getElementById('auto-silver-end').textContent = formatDateShort(endDate);
            }
        }
        
        function formatDateShort(dateString) {
            const date = new Date(dateString);
            return date.toLocaleDateString('ar-EG', {
                month: 'short',
                day: 'numeric'
            });
        }
        
        function setupInputListeners() {
            document.querySelectorAll('input[type="number"]').forEach(input => {
                input.addEventListener('input', updateCalculations);
            });
            
            document.querySelectorAll('select').forEach(select => {
                select.addEventListener('change', updateCalculations);
            });
        }
        
        function setupRemoveExpenseListeners() {
            document.querySelectorAll('.remove-expense-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const expenseId = this.getAttribute('data-id');
                    removeExpense(expenseId);
                });
            });
        }
        
        function setupRemoveMonthlyExpenseListeners() {
            document.querySelectorAll('.remove-monthly-expense-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const expenseId = this.getAttribute('data-id');
                    removeMonthlyExpense(expenseId);
                });
            });
        }
        
        function removeExpense(expenseId) {
            const expenseItem = document.getElementById(`expense-item-${expenseId}`);
            if (expenseItem) {
                expenseItem.remove();
                updateExpensesTotal();
                updateCalculations();
            }
        }
        
        function removeMonthlyExpense(expenseId) {
            const expenseItem = document.getElementById(`monthly-expense-item-${expenseId}`);
            if (expenseItem) {
                expenseItem.remove();
                updateMonthlyExpenses();
            }
        }
        
        function updateMonthlyCalculations() {
            const usdDebtor = parseFloat(document.getElementById('monthly-usd-debtor').value) || 0;
            const usdCreditor = parseFloat(document.getElementById('monthly-usd-creditor').value) || 0;
            const usdSurplus = usdDebtor - usdCreditor;
            monthlyData.usd = { debtor: usdDebtor, creditor: usdCreditor, surplus: usdSurplus };
            
            const usdSurplusElement = document.getElementById('monthly-usd-surplus');
            usdSurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: $${formatNumberWithCommas(usdSurplus.toFixed(2))}`;
            usdSurplusElement.className = 'result-box ' + (usdSurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
            
            const eurDebtor = parseFloat(document.getElementById('monthly-eur-debtor').value) || 0;
            const eurCreditor = parseFloat(document.getElementById('monthly-eur-creditor').value) || 0;
            const eurSurplus = eurDebtor - eurCreditor;
            monthlyData.eur = { debtor: eurDebtor, creditor: eurCreditor, surplus: eurSurplus };
            
            const eurSurplusElement = document.getElementById('monthly-eur-surplus');
            eurSurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: €${formatNumberWithCommas(eurSurplus.toFixed(2))}`;
            eurSurplusElement.className = 'result-box ' + (eurSurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
            
            const tryDebtor = parseFloat(document.getElementById('monthly-try-debtor').value) || 0;
            const tryCreditor = parseFloat(document.getElementById('monthly-try-creditor').value) || 0;
            const trySurplus = tryDebtor - tryCreditor;
            monthlyData.try = { debtor: tryDebtor, creditor: tryCreditor, surplus: trySurplus };
            
            const trySurplusElement = document.getElementById('monthly-try-surplus');
            trySurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: ₺${formatNumberWithCommas(trySurplus.toFixed(2))}`;
            trySurplusElement.className = 'result-box ' + (trySurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
        }
        
        function updateMonthlyExpenses() {
            monthlyData.monthlyExpenses = [];
            
            for (let i = 1; i <= monthlyExpenseCounter; i++) {
                const typeSelect = document.getElementById(`monthly-expense-name-${i}`);
                const amountInput = document.getElementById(`monthly-expense-amount-${i}`);
                const currencySelect = document.getElementById(`monthly-expense-currency-${i}`);
                
                if (typeSelect && amountInput && currencySelect) {
                    const type = typeSelect.value;
                    const amount = parseFloat(amountInput.value) || 0;
                    const currency = currencySelect.value;
                    
                    if (amount > 0) {
                        const typeNames = {
                            'rent': 'إيجار المحل / Dükkan Kirası',
                            'electricity': 'كهرباء / Elektrik',
                            'water': 'ماء / Su',
                            'salary': 'رواتب / Maaşlar',
                            'food': 'مصاريف أكل / Yemek Masrafları',
                            'living': 'مصاريف معيشة / Yaşam Masrafları',
                            'other': 'أخرى / Diğer'
                        };
                        
                        const name = typeNames[type] || type;
                        monthlyData.monthlyExpenses.push({ name, type, amount, currency });
                    }
                }
            }
        }
        
        // التعديل الرئيسي: تحديث الحسابات للفضة بالكيلو والإجمالي
        function updateCalculations() {
            // تحديث فائض الدولار
            const usdDebtor = parseFloat(document.getElementById('usd-debtor').value) || 0;
            const usdCreditor = parseFloat(document.getElementById('usd-creditor').value) || 0;
            const usdSurplus = usdDebtor - usdCreditor;
            appData.usd = { debtor: usdDebtor, creditor: usdCreditor, surplus: usdSurplus };
            
            const usdSurplusElement = document.getElementById('usd-surplus');
            usdSurplusElement.textContent = `الفائض / Kar-Zarar: $${formatNumberWithCommas(usdSurplus.toFixed(2))}`;
            usdSurplusElement.className = 'result-box ' + (usdSurplus >= 0 ? 'positive' : 'negative');
            
            // تحديث فائض اليورو
            const eurDebtor = parseFloat(document.getElementById('eur-debtor').value) || 0;
            const eurCreditor = parseFloat(document.getElementById('eur-creditor').value) || 0;
            const eurSurplus = eurDebtor - eurCreditor;
            appData.eur = { debtor: eurDebtor, creditor: eurCreditor, surplus: eurSurplus };
            
            const eurSurplusElement = document.getElementById('eur-surplus');
            eurSurplusElement.textContent = `الفائض / Kar-Zarar: €${formatNumberWithCommas(eurSurplus.toFixed(2))}`;
            eurSurplusElement.className = 'result-box ' + (eurSurplus >= 0 ? 'positive' : 'negative');
            
            // تحديث فائض الليرة
            const tryDebtor = parseFloat(document.getElementById('try-debtor').value) || 0;
            const tryCreditor = parseFloat(document.getElementById('try-creditor').value) || 0;
            const trySurplus = tryDebtor - tryCreditor;
            appData.try = { debtor: tryDebtor, creditor: tryCreditor, surplus: trySurplus };
            
            const trySurplusElement = document.getElementById('try-surplus');
            trySurplusElement.textContent = `الفائض / Kar-Zarar: ₺${formatNumberWithCommas(trySurplus.toFixed(2))}`;
            trySurplusElement.className = 'result-box ' + (trySurplus >= 0 ? 'positive' : 'negative');
            
            // تحديث بيانات الفضة (معدل)
            const silverQuantity = parseFloat(document.getElementById('silver-quantity').value) || 0;
            const silverTotal = parseFloat(document.getElementById('silver-total-input').value) || 0;
            appData.silver = { quantity: silverQuantity, total: silverTotal }; // total بدلاً من price
            
            // عرض القيمة الإجمالية للفضة
            document.getElementById('silver-total-display').textContent = formatNumberWithCommas(silverTotal.toFixed(2));
            
            // تحديث الفائض الحقيقي (فائض الدولار - قيمة الفضة)
            appData.realSurplus = usdSurplus - silverTotal;
            
            // تحديث عرض الفائض الحقيقي
            document.getElementById('display-usd-surplus').textContent = `$${formatNumberWithCommas(usdSurplus.toFixed(2))}`;
            document.getElementById('display-silver-value').textContent = `$${formatNumberWithCommas(silverTotal.toFixed(2))}`;
            document.getElementById('real-surplus').textContent = `$${formatNumberWithCommas(appData.realSurplus.toFixed(2))}`;
            
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
            document.getElementById('total-profit-usd').textContent = formatNumberWithCommas(totalProfitUSD.toFixed(2));
            document.getElementById('total-profit-eur').textContent = formatNumberWithCommas(totalProfitEUR.toFixed(2));
            
            // تحديث المصروفات
            updateExpensesTotal();
        }
        
        function updateExpensesTotal() {
            let totalExpenseUSD = 0;
            let totalExpenseEUR = 0;
            let totalExpenseTRY = 0;
            
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
            
            const totalExpenseContainer = document.getElementById('total-expense');
            totalExpenseContainer.innerHTML = '';
            
            if (totalExpenseUSD > 0 || totalExpenseEUR > 0 || totalExpenseTRY > 0) {
                if (totalExpenseUSD > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الدولار / Toplam Dolar Giderler</div>
                            <div class="expense-currency">$${formatNumberWithCommas(totalExpenseUSD.toFixed(2))}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseEUR > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات اليورو / Toplam Euro Giderler</div>
                            <div class="expense-currency">€${formatNumberWithCommas(totalExpenseEUR.toFixed(2))}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseTRY > 0) {
                    totalExpenseContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الليرة / Toplam Lira Giderler</div>
                            <div class="expense-currency">₺${formatNumberWithCommas(totalExpenseTRY.toFixed(2))}</div>
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
        
        function autoCollectProfits() {
            const startDate = document.getElementById('monthly-start-date').value;
            const endDate = document.getElementById('monthly-end-date').value;
            
            if (!startDate || !endDate) {
                return;
            }
            
            monthlyData.startDate = startDate;
            monthlyData.endDate = endDate;
            
            updateDateRangeInfo();
            
            const filteredOperations = dailyProfitOperations.filter(operation => {
                const operationDate = operation.date;
                return operationDate >= startDate && operationDate <= endDate;
            });
            
            if (filteredOperations.length === 0) {
                document.getElementById('detailed-profits-container').innerHTML = `
                    <div style="text-align: center; padding: 30px; color: #666;">
                        <i class="fas fa-info-circle" style="font-size: 2rem; margin-bottom: 15px;"></i><br>
                        لا توجد سجلات للأرباح للفترة من ${formatDate(startDate)} إلى ${formatDate(endDate)}<br>
                        ${formatDate(startDate)} - ${formatDate(endDate)} tarihleri arasında kâr kaydı bulunamadı.
                    </div>
                `;
                
                document.getElementById('profit-summary').style.display = 'none';
                document.getElementById('auto-collect-stats').innerHTML = '';
                
                monthlyData.autoProfits = {
                    swift: { usd: 0, eur: 0 },
                    havana: { usd: 0, eur: 0 },
                    silver: { usd: 0, eur: 0 }
                };
                
                updateAutoProfitsDisplay();
                return;
            }
            
            filteredOperations.sort((a, b) => a.timestamp - b.timestamp);
            
            let totalSwiftUSD = 0, totalSwiftEUR = 0;
            let totalHavanaUSD = 0, totalHavanaEUR = 0;
            let totalSilverUSD = 0, totalSilverEUR = 0;
            let grandTotalUSD = 0, grandTotalEUR = 0;
            
            let detailsHtml = '';
            let operationsByDate = {};
            
            filteredOperations.forEach((operation, index) => {
                const date = operation.date;
                if (!operationsByDate[date]) {
                    operationsByDate[date] = [];
                }
                operationsByDate[date].push(operation);
            });
            
            Object.keys(operationsByDate).sort().forEach(date => {
                const dateOperations = operationsByDate[date];
                let dateTotalUSD = 0;
                let dateTotalEUR = 0;
                let dateSwiftUSD = 0, dateSwiftEUR = 0;
                let dateHavanaUSD = 0, dateHavanaEUR = 0;
                let dateSilverUSD = 0, dateSilverEUR = 0;
                
                dateOperations.forEach(operation => {
                    const opSwiftUSD = operation.profits.swift.usd || 0;
                    const opSwiftEUR = operation.profits.swift.eur || 0;
                    const opHavanaUSD = operation.profits.havana.usd || 0;
                    const opHavanaEUR = operation.profits.havana.eur || 0;
                    const opSilverUSD = operation.profits.silver.usd || 0;
                    const opSilverEUR = operation.profits.silver.eur || 0;
                    
                    dateSwiftUSD += opSwiftUSD;
                    dateSwiftEUR += opSwiftEUR;
                    dateHavanaUSD += opHavanaUSD;
                    dateHavanaEUR += opHavanaEUR;
                    dateSilverUSD += opSilverUSD;
                    dateSilverEUR += opSilverEUR;
                    
                    dateTotalUSD += opSwiftUSD + opHavanaUSD + opSilverUSD;
                    dateTotalEUR += opSwiftEUR + opHavanaEUR + opSilverEUR;
                });
                
                totalSwiftUSD += dateSwiftUSD;
                totalSwiftEUR += dateSwiftEUR;
                totalHavanaUSD += dateHavanaUSD;
                totalHavanaEUR += dateHavanaEUR;
                totalSilverUSD += dateSilverUSD;
                totalSilverEUR += dateSilverEUR;
                grandTotalUSD += dateTotalUSD;
                grandTotalEUR += dateTotalEUR;
                
                const time = new Date(dateOperations[0].timestamp).toLocaleTimeString('ar-EG', { 
                    hour: '2-digit', 
                    minute: '2-digit' 
                });
                
                detailsHtml += `
                    <div class="day-profit-item">
                        <div class="day-profit-header">
                            <div class="day-profit-date">${formatDate(date)} (${dateOperations.length} عملية)</div>
                            <div class="day-profit-total">$${formatNumberWithCommas(dateTotalUSD.toFixed(2))} / €${formatNumberWithCommas(dateTotalEUR.toFixed(2))}</div>
                        </div>
                        <div class="day-profit-details">
                            <div class="profit-type-item">
                                <div class="profit-type-title">ربح Swift</div>
                                <div>$${formatNumberWithCommas(dateSwiftUSD.toFixed(2))}</div>
                                <div>€${formatNumberWithCommas(dateSwiftEUR.toFixed(2))}</div>
                            </div>
                            <div class="profit-type-item">
                                <div class="profit-type-title">ربح Havala</div>
                                <div>$${formatNumberWithCommas(dateHavanaUSD.toFixed(2))}</div>
                                <div>€${formatNumberWithCommas(dateHavanaEUR.toFixed(2))}</div>
                            </div>
                            <div class="profit-type-item">
                                <div class="profit-type-title">ربح الفضة</div>
                                <div>$${formatNumberWithCommas(dateSilverUSD.toFixed(2))}</div>
                                <div>€${formatNumberWithCommas(dateSilverEUR.toFixed(2))}</div>
                            </div>
                        </div>
                    </div>
                `;
            });
            
            document.getElementById('detailed-profits-container').innerHTML = detailsHtml;
            
            document.getElementById('total-monthly-profit-usd').textContent = `$${formatNumberWithCommas(grandTotalUSD.toFixed(2))}`;
            document.getElementById('total-monthly-profit-eur').textContent = `€${formatNumberWithCommas(grandTotalEUR.toFixed(2))}`;
            
            const uniqueDates = Object.keys(operationsByDate).length;
            document.getElementById('profit-days-count').textContent = uniqueDates;
            document.getElementById('profit-days-count-tr').textContent = uniqueDates;
            
            document.getElementById('profit-operations-count').textContent = filteredOperations.length;
            document.getElementById('profit-operations-count-tr').textContent = filteredOperations.length;
            
            document.getElementById('profit-summary').style.display = 'block';
            
            monthlyData.detailedProfits = filteredOperations;
            monthlyData.autoProfits = {
                swift: { usd: totalSwiftUSD, eur: totalSwiftEUR },
                havana: { usd: totalHavanaUSD, eur: totalHavanaEUR },
                silver: { usd: totalSilverUSD, eur: totalSilverEUR }
            };
            
            updateAutoProfitsDisplay();
            updateAutoCollectStats(filteredOperations.length, uniqueDates, grandTotalUSD, grandTotalEUR);
        }
        
        function updateAutoCollectStats(operationsCount, daysCount, totalUSD, totalEUR) {
            const statsHtml = `
                <div class="collect-stat-item">
                    <div class="collect-stat-label">عدد العمليات / İşlem Sayısı</div>
                    <div class="collect-stat-value">${operationsCount}</div>
                </div>
                <div class="collect-stat-item">
                    <div class="collect-stat-label">عدد الأيام / Gün Sayısı</div>
                    <div class="collect-stat-value">${daysCount}</div>
                </div>
                <div class="collect-stat-item">
                    <div class="collect-stat-label">إجمالي USD / Toplam USD</div>
                    <div class="collect-stat-value">$${formatNumberWithCommas(totalUSD.toFixed(2))}</div>
                </div>
                <div class="collect-stat-item">
                    <div class="collect-stat-label">إجمالي EUR / Toplam EUR</div>
                    <div class="collect-stat-value">€${formatNumberWithCommas(totalEUR.toFixed(2))}</div>
                </div>
            `;
            
            document.getElementById('auto-collect-stats').innerHTML = statsHtml;
        }
        
        function updateAutoProfitsDisplay() {
            document.getElementById('auto-swift-usd').textContent = formatNumberWithCommas(monthlyData.autoProfits.swift.usd.toFixed(2));
            document.getElementById('auto-swift-eur').textContent = formatNumberWithCommas(monthlyData.autoProfits.swift.eur.toFixed(2));
            document.getElementById('auto-havala-usd').textContent = formatNumberWithCommas(monthlyData.autoProfits.havana.usd.toFixed(2));
            document.getElementById('auto-havala-eur').textContent = formatNumberWithCommas(monthlyData.autoProfits.havana.eur.toFixed(2));
            document.getElementById('auto-silver-usd').textContent = formatNumberWithCommas(monthlyData.autoProfits.silver.usd.toFixed(2));
            document.getElementById('auto-silver-eur').textContent = formatNumberWithCommas(monthlyData.autoProfits.silver.eur.toFixed(2));
            
            updateCompactMonthlyReport();
        }
        
        function saveDailyProfits() {
            const today = new Date().toISOString().split('T')[0];
            
            const swiftProfitUSD = parseFloat(document.getElementById('swift-profit-usd').value) || 0;
            const swiftProfitEUR = parseFloat(document.getElementById('swift-profit-eur').value) || 0;
            const havanaProfitUSD = parseFloat(document.getElementById('havala-profit-usd').value) || 0;
            const havanaProfitEUR = parseFloat(document.getElementById('havala-profit-eur').value) || 0;
            const silverProfitUSD = parseFloat(document.getElementById('silver-profit-usd').value) || 0;
            const silverProfitEUR = parseFloat(document.getElementById('silver-profit-eur').value) || 0;
            
            const totalProfit = swiftProfitUSD + swiftProfitEUR + havanaProfitUSD + havanaProfitEUR + silverProfitUSD + silverProfitEUR;
            
            if (totalProfit === 0) {
                console.log("لا توجد أرباح ليتم حفظها في هذه العملية.");
                return;
            }
            
            const profitOperation = {
                date: today,
                timestamp: new Date().getTime(),
                profits: {
                    swift: { usd: swiftProfitUSD, eur: swiftProfitEUR },
                    havana: { usd: havanaProfitUSD, eur: havanaProfitEUR },
                    silver: { usd: silverProfitUSD, eur: silverProfitEUR },
                    total: { 
                        usd: swiftProfitUSD + havanaProfitUSD + silverProfitUSD, 
                        eur: swiftProfitEUR + havanaProfitEUR + silverProfitEUR 
                    }
                }
            };
            
            dailyProfitOperations.push(profitOperation);
            localStorage.setItem('alanhar_daily_profit_operations', JSON.stringify(dailyProfitOperations));
            updateDailyProfitsCount();
            console.log("تم حفظ عملية الربح بنجاح. إجمالي العمليات:", dailyProfitOperations.length);
            
            if (document.getElementById('monthly').classList.contains('active')) {
                autoCollectProfits();
            }
        }
        
        function generateMonthlyReport() {
            updateMonthlyCalculations();
            updateMonthlyExpenses();
            document.getElementById('compact-monthly-report').style.display = 'block';
            
            const startFormatted = formatDate(monthlyData.startDate);
            const endFormatted = formatDate(monthlyData.endDate);
            document.getElementById('compact-date-range').textContent = `الفترة: من ${startFormatted} إلى ${endFormatted}`;
            
            document.getElementById('compact-usd-debtor').textContent = `$${formatNumberWithCommas(monthlyData.usd.debtor.toFixed(2))}`;
            document.getElementById('compact-usd-creditor').textContent = `$${formatNumberWithCommas(monthlyData.usd.creditor.toFixed(2))}`;
            document.getElementById('compact-usd-surplus').textContent = `$${formatNumberWithCommas(monthlyData.usd.surplus.toFixed(2))}`;
            
            document.getElementById('compact-eur-debtor').textContent = `€${formatNumberWithCommas(monthlyData.eur.debtor.toFixed(2))}`;
            document.getElementById('compact-eur-creditor').textContent = `€${formatNumberWithCommas(monthlyData.eur.creditor.toFixed(2))}`;
            document.getElementById('compact-eur-surplus').textContent = `€${formatNumberWithCommas(monthlyData.eur.surplus.toFixed(2))}`;
            
            document.getElementById('compact-try-debtor').textContent = `₺${formatNumberWithCommas(monthlyData.try.debtor.toFixed(2))}`;
            document.getElementById('compact-try-creditor').textContent = `₺${formatNumberWithCommas(monthlyData.try.creditor.toFixed(2))}`;
            document.getElementById('compact-try-surplus').textContent = `₺${formatNumberWithCommas(monthlyData.try.surplus.toFixed(2))}`;
            
            document.getElementById('compact-swift-usd').textContent = `$${formatNumberWithCommas(monthlyData.autoProfits.swift.usd.toFixed(2))}`;
            document.getElementById('compact-swift-eur').textContent = `€${formatNumberWithCommas(monthlyData.autoProfits.swift.eur.toFixed(2))}`;
            document.getElementById('compact-havala-usd').textContent = `$${formatNumberWithCommas(monthlyData.autoProfits.havana.usd.toFixed(2))}`;
            document.getElementById('compact-havala-eur').textContent = `€${formatNumberWithCommas(monthlyData.autoProfits.havana.eur.toFixed(2))}`;
            document.getElementById('compact-silver-usd').textContent = `$${formatNumberWithCommas(monthlyData.autoProfits.silver.usd.toFixed(2))}`;
            document.getElementById('compact-silver-eur').textContent = `€${formatNumberWithCommas(monthlyData.autoProfits.silver.eur.toFixed(2))}`;
            
            const expensesList = document.getElementById('compact-expenses-list');
            expensesList.innerHTML = '';
            
            if (monthlyData.monthlyExpenses.length > 0) {
                const expensesByCurrency = {
                    USD: [],
                    EUR: [],
                    TRY: []
                };
                
                monthlyData.monthlyExpenses.forEach(expense => {
                    if (expensesByCurrency[expense.currency]) {
                        expensesByCurrency[expense.currency].push(expense);
                    }
                });
                
                ['USD', 'EUR', 'TRY'].forEach(currency => {
                    if (expensesByCurrency[currency].length > 0) {
                        const currencyBox = document.createElement('div');
                        currencyBox.className = 'compact-grid-item';
                        
                        const currencySymbol = currency === 'USD' ? '$' : currency === 'EUR' ? '€' : '₺';
                        const currencyTitle = currency === 'USD' ? 'الدولار الأمريكي' : currency === 'EUR' ? 'اليورو الأوروبي' : 'الليرة التركية';
                        const currencyTitleTr = currency === 'USD' ? 'Amerikan Doları' : currency === 'EUR' ? 'Euro' : 'Türk Lirası';
                        
                        let expensesHtml = `<div class="compact-grid-title">${currencyTitle} / ${currencyTitleTr}</div>`;
                        
                        let total = 0;
                        expensesByCurrency[currency].forEach(expense => {
                            expensesHtml += `
                                <div class="compact-currency-row">
                                    <span>${expense.name}</span>
                                    <span>${currencySymbol}${formatNumberWithCommas(expense.amount.toFixed(2))}</span>
                                </div>
                            `;
                            total += expense.amount;
                        });
                        
                        expensesHtml += `
                            <div class="compact-currency-row compact-total-row">
                                <span>الإجمالي / Toplam</span>
                                <span>${currencySymbol}${formatNumberWithCommas(total.toFixed(2))}</span>
                            </div>
                        `;
                        
                        currencyBox.innerHTML = expensesHtml;
                        expensesList.appendChild(currencyBox);
                    }
                });
            } else {
                expensesList.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666; grid-column: 1 / -1;">
                        لا توجد مصروفات مسجلة / Kayıtlı gider yok
                    </div>
                `;
            }
            
            const now = new Date();
            const creationDate = formatDate(now.toISOString().split('T')[0]);
            document.getElementById('compact-creation-date').textContent = creationDate;
            document.getElementById('compact-creation-date-tr').textContent = creationDate;
            
            document.getElementById('compact-monthly-report').scrollIntoView({ behavior: 'smooth' });
        }
        
        function updateCompactMonthlyReport() {
            if (document.getElementById('compact-swift-usd')) {
                document.getElementById('compact-swift-usd').textContent = `$${formatNumberWithCommas(monthlyData.autoProfits.swift.usd.toFixed(2))}`;
                document.getElementById('compact-swift-eur').textContent = `€${formatNumberWithCommas(monthlyData.autoProfits.swift.eur.toFixed(2))}`;
                document.getElementById('compact-havala-usd').textContent = `$${formatNumberWithCommas(monthlyData.autoProfits.havana.usd.toFixed(2))}`;
                document.getElementById('compact-havala-eur').textContent = `€${formatNumberWithCommas(monthlyData.autoProfits.havana.eur.toFixed(2))}`;
                document.getElementById('compact-silver-usd').textContent = `$${formatNumberWithCommas(monthlyData.autoProfits.silver.usd.toFixed(2))}`;
                document.getElementById('compact-silver-eur').textContent = `€${formatNumberWithCommas(monthlyData.autoProfits.silver.eur.toFixed(2))}`;
            }
        }
        
        // إصلاح زر طباعة التقرير الشهري
        function printMonthlyReport() {
            generateMonthlyReport();
            
            setTimeout(() => {
                const printContent = document.getElementById('compact-monthly-report').innerHTML;
                const originalContent = document.body.innerHTML;
                
                document.body.innerHTML = `
                    <!DOCTYPE html>
                    <html dir="rtl" lang="ar">
                    <head>
                        <title>تقرير شهري مختصر - نظام ALANHAR</title>
                        <meta charset="UTF-8">
                        <style>
                            body {
                                font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
                                margin: 0;
                                padding: 20px;
                                color: #333;
                                direction: rtl;
                                font-size: 12pt;
                                background: white;
                            }
                            .compact-monthly-report {
                                background: white;
                                border-radius: 15px;
                                padding: 0;
                                margin: 0;
                                box-shadow: none;
                                border: 1px solid #ddd;
                                width: 100%;
                                height: auto;
                            }
                            .compact-report-header {
                                color: #8e24aa;
                                background: white !important;
                                padding: 25px 30px;
                                text-align: center;
                                border-bottom: 3px solid #8e24aa;
                            }
                            .compact-report-header h2 {
                                font-size: 1.8rem;
                                margin-bottom: 10px;
                                color: #8e24aa;
                            }
                            .compact-date-range {
                                font-size: 1.2rem;
                                font-weight: bold;
                                margin-bottom: 5px;
                                color: #666;
                            }
                            .compact-report-content {
                                padding: 25px;
                            }
                            .compact-section {
                                margin-bottom: 20px;
                                padding: 15px;
                                border-radius: 8px;
                                border: 1px solid;
                                page-break-inside: avoid;
                            }
                            .compact-section-title {
                                font-size: 1.2rem;
                                margin-bottom: 12px;
                                padding-bottom: 8px;
                                border-bottom: 1px solid;
                                display: flex;
                                align-items: center;
                            }
                            .compact-currency-section {
                                border-color: #4caf50;
                                background: #e8f5e9;
                            }
                            .compact-currency-title {
                                color: #2e7d32;
                                border-bottom-color: #a5d6a7;
                            }
                            .compact-profit-section {
                                border-color: #ff9800;
                                background: #fff3e0;
                            }
                            .compact-profit-title {
                                color: #ef6c00;
                                border-bottom-color: #ffb74d;
                            }
                            .compact-expense-section {
                                border-color: #f44336;
                                background: #ffebee;
                            }
                            .compact-expense-title {
                                color: #d32f2f;
                                border-bottom-color: #ef9a9a;
                            }
                            .compact-grid {
                                display: grid;
                                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
                                gap: 15px;
                                margin-top: 12px;
                            }
                            .compact-grid-item {
                                padding: 12px;
                                border-radius: 6px;
                                background: white;
                                border: 1px solid #ddd;
                                page-break-inside: avoid;
                            }
                            .compact-grid-title {
                                font-weight: bold;
                                margin-bottom: 8px;
                                padding-bottom: 4px;
                                border-bottom: 1px solid #eee;
                                color: #8e24aa;
                                font-size: 1.1rem;
                            }
                            .compact-value {
                                font-size: 1.3rem;
                                font-weight: bold;
                                margin: 8px 0;
                                text-align: center;
                            }
                            .compact-currency-row {
                                display: flex;
                                justify-content: space-between;
                                align-items: center;
                                padding: 6px 0;
                                border-bottom: 1px dashed #eee;
                                font-size: 0.95rem;
                            }
                            .compact-currency-row:last-child {
                                border-bottom: none;
                            }
                            .compact-total-row {
                                background: rgba(142, 36, 170, 0.1);
                                padding: 10px;
                                border-radius: 6px;
                                margin-top: 8px;
                                font-weight: bold;
                                border: 1px solid #8e24aa;
                            }
                            .compact-note {
                                background: #f3e5f5;
                                padding: 12px;
                                border-radius: 6px;
                                border: 1px solid #8e24aa;
                                text-align: center;
                                margin-top: 15px;
                                font-size: 0.9rem;
                            }
                            .compact-report-footer {
                                padding: 15px 25px;
                                border-top: 1px solid #8e24aa;
                                text-align: center;
                                color: #666;
                                background: #f9f7fd;
                                font-size: 0.9rem;
                            }
                            @media print {
                                body {
                                    padding: 10px;
                                    font-size: 10pt;
                                }
                                .compact-monthly-report {
                                    box-shadow: none;
                                    border: none;
                                    page-break-before: always;
                                }
                                .no-print {
                                    display: none !important;
                                }
                            }
                            .print-actions {
                                text-align: center;
                                margin-top: 20px;
                                padding-top: 20px;
                                border-top: 1px solid #ddd;
                            }
                            .print-btn {
                                padding: 10px 20px;
                                background: #8e24aa;
                                color: white;
                                border: none;
                                border-radius: 6px;
                                font-size: 1rem;
                                cursor: pointer;
                                margin: 0 10px;
                            }
                            .close-btn {
                                padding: 10px 20px;
                                background: #666;
                                color: white;
                                border: none;
                                border-radius: 6px;
                                font-size: 1rem;
                                cursor: pointer;
                                margin: 0 10px;
                            }
                        </style>
                    </head>
                    <body>
                        <div class="compact-monthly-report">
                            ${printContent}
                        </div>
                        <div class="print-actions no-print">
                            <button class="print-btn" onclick="window.print()">
                                <i class="fas fa-print"></i> طباعة التقرير
                            </button>
                            <button class="close-btn" onclick="window.close()">
                                <i class="fas fa-times"></i> إغلاق النافذة
                            </button>
                        </div>
                        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
                        <script>
                            window.onload = function() {
                                setTimeout(function() {
                                    window.print();
                                }, 500);
                            };
                        <\/script>
                    </body>
                    </html>
                `;
                
                setTimeout(() => {
                    window.print();
                    
                    setTimeout(() => {
                        document.body.innerHTML = originalContent;
                        window.location.reload();
                    }, 1000);
                }, 1000);
            }, 500);
        }
        
        // دالة جديدة لطباعة التقرير اليومي
        function printDailyReport() {
            generateReport();
            
            setTimeout(() => {
                const reportContent = document.getElementById('report').innerHTML;
                const originalContent = document.body.innerHTML;
                
                document.body.innerHTML = `
                    <!DOCTYPE html>
                    <html dir="rtl" lang="ar">
                    <head>
                        <title>تقرير يومي - نظام ALANHAR</title>
                        <meta charset="UTF-8">
                        <style>
                            body {
                                font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
                                margin: 0;
                                padding: 20px;
                                color: #333;
                                direction: rtl;
                                font-size: 12pt;
                                background: white;
                            }
                            .no-print {
                                display: none !important;
                            }
                            .card {
                                background: white;
                                border-radius: 8px;
                                padding: 15px;
                                margin-bottom: 15px;
                                border: 1px solid #ddd;
                            }
                            .report-header {
                                text-align: center;
                                margin-bottom: 20px;
                                padding-bottom: 15px;
                                border-bottom: 2px solid #1a2980;
                            }
                            .report-header h2 {
                                color: #1a2980;
                                font-size: 1.5rem;
                                margin-bottom: 10px;
                            }
                            table {
                                width: 100%;
                                border-collapse: collapse;
                                margin-top: 15px;
                                font-size: 10pt;
                            }
                            th {
                                background-color: #1a2980;
                                color: white;
                                padding: 8px;
                                text-align: right;
                            }
                            td {
                                padding: 6px 8px;
                                border-bottom: 1px solid #eee;
                            }
                            tr:nth-child(even) {
                                background-color: #f8f9fa;
                            }
                            @media print {
                                body {
                                    padding: 10px;
                                    font-size: 10pt;
                                }
                                .card {
                                    box-shadow: none;
                                    border: 1px solid #ccc;
                                }
                            }
                        </style>
                    </head>
                    <body>
                        ${reportContent}
                        <div style="text-align: center; margin-top: 20px;">
                            <button onclick="window.print()" style="padding: 10px 20px; background: #4caf50; color: white; border: none; border-radius: 6px; font-size: 1rem; cursor: pointer;">
                                <i class="fas fa-print"></i> طباعة التقرير
                            </button>
                        </div>
                        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
                        <script>
                            window.onload = function() {
                                setTimeout(function() {
                                    window.print();
                                }, 500);
                            };
                        <\/script>
                    </body>
                    </html>
                `;
                
                setTimeout(() => {
                    window.print();
                    
                    setTimeout(() => {
                        document.body.innerHTML = originalContent;
                        window.location.reload();
                    }, 1000);
                }, 500);
            }, 500);
        }
        
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
            
            document.getElementById(`expense-name-${expenseCounter}`).addEventListener('input', updateExpensesTotal);
            document.getElementById(`expense-amount-${expenseCounter}`).addEventListener('input', updateExpensesTotal);
            document.getElementById(`expense-currency-${expenseCounter}`).addEventListener('change', updateExpensesTotal);
            
            document.querySelector(`.remove-expense-btn[data-id="${expenseCounter}"]`).addEventListener('click', function() {
                removeExpense(expenseCounter);
            });
            
            updateExpensesTotal();
        }
        
        function addNewMonthlyExpense() {
            monthlyExpenseCounter++;
            
            const expenseContainer = document.getElementById('monthly-expenses-list');
            const expenseItem = document.createElement('div');
            expenseItem.className = 'expense-item monthly-expense-item';
            expenseItem.id = `monthly-expense-item-${monthlyExpenseCounter}`;
            expenseItem.innerHTML = `
                <div class="input-group">
                    <label for="monthly-expense-name-${monthlyExpenseCounter}">وصف المصروف / Gider Açıklaması</label>
                    <select id="monthly-expense-name-${monthlyExpenseCounter}" class="monthly-select monthly-expense-type">
                        <option value="rent">إيجار المحل / Dükkan Kirası</option>
                        <option value="electricity">كهرباء / Elektrik</option>
                        <option value="water">ماء / Su</option>
                        <option value="salary">رواتب / Maaşlar</option>
                        <option value="food">مصاريف أكل / Yemek Masrafları</option>
                        <option value="living">مصاريف معيشة / Yaşam Masrafları</option>
                        <option value="other">أخرى / Diğer</option>
                    </select>
                </div>
                
                <div class="input-group">
                    <label for="monthly-expense-amount-${monthlyExpenseCounter}">القيمة / Tutar</label>
                    <input type="number" id="monthly-expense-amount-${monthlyExpenseCounter}" class="monthly-input" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                </div>
                
                <div class="input-group">
                    <label for="monthly-expense-currency-${monthlyExpenseCounter}">العملة / Para Birimi</label>
                    <select id="monthly-expense-currency-${monthlyExpenseCounter}" class="monthly-select">
                        <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                        <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                        <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                    </select>
                </div>
                
                <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="${monthlyExpenseCounter}">
                    <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                </button>
            `;
            
            expenseContainer.appendChild(expenseItem);
            
            document.querySelector(`.remove-monthly-expense-btn[data-id="${monthlyExpenseCounter}"]`).addEventListener('click', function() {
                removeMonthlyExpense(monthlyExpenseCounter);
            });
        }
        
        function saveMonthlyData() {
            updateMonthlyCalculations();
            updateMonthlyExpenses();
            
            if (monthlyData.startDate && monthlyData.endDate) {
                const monthlyReport = {
                    startDate: monthlyData.startDate,
                    endDate: monthlyData.endDate,
                    usd: { ...monthlyData.usd },
                    eur: { ...monthlyData.eur },
                    try: { ...monthlyData.try },
                    autoProfits: { ...monthlyData.autoProfits },
                    monthlyExpenses: [...monthlyData.monthlyExpenses],
                    timestamp: new Date().toISOString()
                };
                
                const existingIndex = monthlyRecords.findIndex(record => 
                    record.startDate === monthlyData.startDate && 
                    record.endDate === monthlyData.endDate
                );
                
                if (existingIndex !== -1) {
                    monthlyRecords[existingIndex] = monthlyReport;
                    alert("تم تحديث التقرير الشهري بنجاح! / Aylık rapor başarıyla güncellendi!");
                } else {
                    monthlyRecords.push(monthlyReport);
                    alert("تم حفظ التقرير الشهري بنجاح! / Aylık rapor başarıyla kaydedildi!");
                }
                
                localStorage.setItem('alanhar_monthly', JSON.stringify(monthlyRecords));
            } else {
                alert("يرجى تحديد تاريخ البداية والنهاية أولاً. / Lütfen önce başlangıç ve bitiş tarihlerini seçin.");
            }
        }
        
        function saveData() {
            updateCalculations();
            
            if (confirm("هل تريد حفظ بيانات اليوم؟ / Bugünün verilerini kaydetmek istiyor musunuz?")) {
                saveDailyProfits();
                
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
        
        function generateReport() {
            updateCalculations();
            
            const usdSurplusElement = document.getElementById('report-usd-surplus');
            usdSurplusElement.textContent = `$${formatNumberWithCommas(appData.usd.surplus.toFixed(2))}`;
            
            const eurSurplusElement = document.getElementById('report-eur-surplus');
            eurSurplusElement.textContent = `€${formatNumberWithCommas(appData.eur.surplus.toFixed(2))}`;
            
            const trySurplusElement = document.getElementById('report-try-surplus');
            trySurplusElement.textContent = `₺${formatNumberWithCommas(appData.try.surplus.toFixed(2))}`;
            
            const reportTableBody = document.getElementById('report-table-body');
            reportTableBody.innerHTML = `
                <tr>
                    <td>الدولار الأمريكي (USD) / Amerikan Doları</td>
                    <td>$${formatNumberWithCommas(appData.usd.debtor.toFixed(2))}</td>
                    <td>$${formatNumberWithCommas(appData.usd.creditor.toFixed(2))}</td>
                    <td style="color: ${appData.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumberWithCommas(appData.usd.surplus.toFixed(2))}
                    </td>
                    <td>
                        <span style="color: ${appData.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${appData.usd.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
                <tr>
                    <td>اليورو الأوروبي (EUR) / Euro</td>
                    <td>€${formatNumberWithCommas(appData.eur.debtor.toFixed(2))}</td>
                    <td>€${formatNumberWithCommas(appData.eur.creditor.toFixed(2))}</td>
                    <td style="color: ${appData.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${formatNumberWithCommas(appData.eur.surplus.toFixed(2))}
                    </td>
                    <td>
                        <span style="color: ${appData.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${appData.eur.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
                <tr>
                    <td>الليرة التركية (TRY) / Türk Lirası</td>
                    <td>₺${formatNumberWithCommas(appData.try.debtor.toFixed(2))}</td>
                    <td>₺${formatNumberWithCommas(appData.try.creditor.toFixed(2))}</td>
                    <td style="color: ${appData.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${formatNumberWithCommas(appData.try.surplus.toFixed(2))}
                    </td>
                    <td>
                        <span style="color: ${appData.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                            ${appData.try.surplus >= 0 ? 'ربح / Kâr' : 'خسارة / Zarar'}
                        </span>
                    </td>
                </tr>
            `;
            
            // تحديث بيانات الفضة في التقرير (معدل)
            document.getElementById('report-silver-quantity').textContent = formatNumberWithCommas(appData.silver.quantity.toFixed(3)); // 3 منازل عشرية للكيلو
            document.getElementById('report-silver-total').textContent = formatNumberWithCommas(appData.silver.total.toFixed(2));
            
            // تحديث الفائض الحقيقي في التقرير
            document.getElementById('report-display-usd-surplus').textContent = `$${formatNumberWithCommas(appData.usd.surplus.toFixed(2))}`;
            document.getElementById('report-display-silver-value').textContent = `$${formatNumberWithCommas(appData.silver.total.toFixed(2))}`;
            document.getElementById('report-real-surplus').textContent = `$${formatNumberWithCommas(appData.realSurplus.toFixed(2))}`;
            
            // تحديث الأرباح في التقرير
            document.getElementById('report-swift-usd').textContent = formatNumberWithCommas(appData.profits.swift.usd.toFixed(2));
            document.getElementById('report-swift-eur').textContent = formatNumberWithCommas(appData.profits.swift.eur.toFixed(2));
            document.getElementById('report-havala-usd').textContent = formatNumberWithCommas(appData.profits.havana.usd.toFixed(2));
            document.getElementById('report-havala-eur').textContent = formatNumberWithCommas(appData.profits.havana.eur.toFixed(2));
            document.getElementById('report-silver-profit-usd').textContent = formatNumberWithCommas(appData.profits.silver.usd.toFixed(2));
            document.getElementById('report-silver-profit-eur').textContent = formatNumberWithCommas(appData.profits.silver.eur.toFixed(2));
            document.getElementById('report-total-profit-usd').textContent = formatNumberWithCommas(appData.profits.total.usd.toFixed(2));
            document.getElementById('report-total-profit-eur').textContent = formatNumberWithCommas(appData.profits.total.eur.toFixed(2));
            
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
                    <td>${formatNumberWithCommas(expense.amount.toFixed(2))}</td>
                    <td>${expense.currency === 'USD' ? '$' : expense.currency === 'EUR' ? '€' : '₺'}</td>
                `;
                expensesReportBody.appendChild(row);
                
                if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
            });
            
            if (appData.expenses.length === 0) {
                expensesReportBody.innerHTML = `
                    <tr>
                        <td colspan="3" style="text-align: center; padding: 20px; color: #666;">
                            لا توجد مصروفات مسجلة / Kayıtlı gider yok
                        </td>
                    </tr>
                `;
            }
            
            const reportExpenseTotalContainer = document.getElementById('report-expense-total');
            reportExpenseTotalContainer.innerHTML = '';
            
            if (totalExpenseUSD > 0 || totalExpenseEUR > 0 || totalExpenseTRY > 0) {
                if (totalExpenseUSD > 0) {
                    reportExpenseTotalContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الدولار / Toplam Dolar Giderler</div>
                            <div class="expense-currency">$${formatNumberWithCommas(totalExpenseUSD.toFixed(2))}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseEUR > 0) {
                    reportExpenseTotalContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات اليورو / Toplam Euro Giderler</div>
                            <div class="expense-currency">€${formatNumberWithCommas(totalExpenseEUR.toFixed(2))}</div>
                        </div>
                    `;
                }
                
                if (totalExpenseTRY > 0) {
                    reportExpenseTotalContainer.innerHTML += `
                        <div class="expense-total-box">
                            <div>إجمالي مصروفات الليرة / Toplam Lira Giderler</div>
                            <div class="expense-currency">₺${formatNumberWithCommas(totalExpenseTRY.toFixed(2))}</div>
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
            
            switchTab('report');
        }
        
        // وظيفة لإضافة فواصل الآلاف للأرقام
        function formatNumberWithCommas(number) {
            // تحويل الرقم إلى سلسلة نصية
            let numStr = number.toString();
            
            // فصل العدد الصحيح عن الكسور
            let parts = numStr.split('.');
            let integerPart = parts[0];
            let decimalPart = parts.length > 1 ? '.' + parts[1] : '';
            
            // إضافة فواصل كل 3 أرقام
            let formattedInteger = integerPart.replace(/\B(?=(\d{3})+(?!\d))/g, ",");
            
            // إرجاع العدد مع الكسور
            return formattedInteger + decimalPart;
        }
        
        function resetData() {
            if (confirm("هل تريد مسح جميع بيانات اليوم؟ / Bugünün tüm verilerini temizlemek istiyor musunuz?")) {
                document.querySelectorAll('input[type="number"], input[type="text"]').forEach(input => {
                    if (input.id.includes('profit') || input.id.includes('debtor') || input.id.includes('creditor') || 
                        input.id.includes('silver-quantity') || input.id.includes('silver-total-input')) {
                        input.value = '';
                    }
                });
                
                const expensesList = document.getElementById('expenses-list');
                expensesList.innerHTML = '';
                
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
                
                setupRemoveExpenseListeners();
                setupInputListeners();
                
                appData = {
                    usd: { debtor: 0, creditor: 0, surplus: 0 },
                    eur: { debtor: 0, creditor: 0, surplus: 0 },
                    try: { debtor: 0, creditor: 0, surplus: 0 },
                    silver: { quantity: 0, total: 0 },
                    realSurplus: 0,
                    profits: { 
                        swift: { usd: 0, eur: 0 }, 
                        havana: { usd: 0, eur: 0 }, 
                        silver: { usd: 0, eur: 0 },
                        total: { usd: 0, eur: 0 }
                    },
                    expenses: [],
                    date: new Date().toISOString().split('T')[0],
                    timestamp: new Date().getTime()
                };
                
                updateCalculations();
                
                if (document.getElementById('report').classList.contains('active')) {
                    generateReport();
                }
                
                alert("تم مسح جميع بيانات اليوم بنجاح! / Bugünün tüm verileri başarıyla temizlendi!");
            }
        }
        
        function resetMonthlyData() {
            if (confirm("هل تريد مسح جميع بيانات التقرير الشهري؟ / Tüm aylık rapor verilerini temizlemek istiyor musunuz?")) {
                document.getElementById('monthly-usd-debtor').value = '';
                document.getElementById('monthly-usd-creditor').value = '';
                document.getElementById('monthly-eur-debtor').value = '';
                document.getElementById('monthly-eur-creditor').value = '';
                document.getElementById('monthly-try-debtor').value = '';
                document.getElementById('monthly-try-creditor').value = '';
                
                const expensesList = document.getElementById('monthly-expenses-list');
                expensesList.innerHTML = '';
                
                monthlyExpenseCounter = 1;
                const expenseItem = document.createElement('div');
                expenseItem.className = 'expense-item monthly-expense-item';
                expenseItem.id = 'monthly-expense-item-1';
                expenseItem.innerHTML = `
                    <div class="input-group">
                        <label for="monthly-expense-name-1">وصف المصروف / Gider Açıklaması</label>
                        <select id="monthly-expense-name-1" class="monthly-select monthly-expense-type">
                            <option value="rent">إيجار المحل / Dükkan Kirası</option>
                            <option value="electricity">كهرباء / Elektrik</option>
                            <option value="water">ماء / Su</option>
                            <option value="salary">رواتب / Maaşlar</option>
                            <option value="food">مصاريف أكل / Yemek Masrafları</option>
                            <option value="living">مصاريف معيشة / Yaşam Masrafları</option>
                            <option value="other">أخرى / Diğer</option>
                        </select>
                    </div>
                    
                    <div class="input-group">
                        <label for="monthly-expense-amount-1">القيمة / Tutar</label>
                        <input type="number" id="monthly-expense-amount-1" class="monthly-input" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                    </div>
                    
                    <div class="input-group">
                        <label for="monthly-expense-currency-1">العملة / Para Birimi</label>
                        <select id="monthly-expense-currency-1" class="monthly-select">
                            <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                            <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                            <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                        </select>
                    </div>
                    
                    <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="1">
                        <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                    </button>
                `;
                expensesList.appendChild(expenseItem);
                
                setupRemoveMonthlyExpenseListeners();
                setupMonthlyInputListeners();
                
                monthlyData = {
                    startDate: monthlyData.startDate,
                    endDate: monthlyData.endDate,
                    usd: { debtor: 0, creditor: 0, surplus: 0 },
                    eur: { debtor: 0, creditor: 0, surplus: 0 },
                    try: { debtor: 0, creditor: 0, surplus: 0 },
                    autoProfits: {
                        swift: { usd: 0, eur: 0 },
                        havana: { usd: 0, eur: 0 },
                        silver: { usd: 0, eur: 0 }
                    },
                    monthlyExpenses: [],
                    detailedProfits: []
                };
                
                updateMonthlyCalculations();
                
                document.getElementById('auto-swift-usd').textContent = '0.00';
                document.getElementById('auto-swift-eur').textContent = '0.00';
                document.getElementById('auto-havala-usd').textContent = '0.00';
                document.getElementById('auto-havala-eur').textContent = '0.00';
                document.getElementById('auto-silver-usd').textContent = '0.00';
                document.getElementById('auto-silver-eur').textContent = '0.00';
                
                document.getElementById('detailed-profits-container').innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666;">
                        قم بتحديد الفترة الزمنية لعرض الأرباح المجمعة / Zaman aralığını seçerek toplanan kârları görüntüleyin.
                    </div>
                `;
                document.getElementById('profit-summary').style.display = 'none';
                
                document.getElementById('compact-monthly-report').style.display = 'none';
                
                alert("تم مسح جميع بيانات التقرير الشهري بنجاح! / Tüm aylık rapor verileri başarıyla temizlendi!");
            }
        }
        
        function loadHistory() {
            const historyTableBody = document.getElementById('history-table-body');
            const noHistoryRow = document.getElementById('no-history');
            
            if (historyRecords.length === 0) {
                noHistoryRow.style.display = '';
                return;
            }
            
            noHistoryRow.style.display = 'none';
            historyTableBody.innerHTML = '';
            
            const sortedRecords = [...historyRecords].sort((a, b) => b.timestamp - a.timestamp);
            
            sortedRecords.forEach((record, index) => {
                const originalIndex = historyRecords.indexOf(record);
                const row = document.createElement('tr');
                
                let totalExpenseUSD = 0;
                let totalExpenseEUR = 0;
                let totalExpenseTRY = 0;
                
                record.data.expenses.forEach(expense => {
                    if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                    else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                    else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
                });
                
                let expenseDisplay = '';
                if (totalExpenseUSD > 0) expenseDisplay += `$${formatNumberWithCommas(totalExpenseUSD.toFixed(2))} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${formatNumberWithCommas(totalExpenseEUR.toFixed(2))} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${formatNumberWithCommas(totalExpenseTRY.toFixed(2))}`;
                if (!expenseDisplay) expenseDisplay = '-';
                
                const totalProfitUSD = record.data.profits.total.usd;
                const totalProfitEUR = record.data.profits.total.eur;
                let totalProfitDisplay = `$${formatNumberWithCommas(totalProfitUSD.toFixed(2))}`;
                if (totalProfitEUR > 0) {
                    totalProfitDisplay += ` / €${formatNumberWithCommas(totalProfitEUR.toFixed(2))}`;
                }
                
                row.innerHTML = `
                    <td>${formatDate(record.date)}</td>
                    <td style="color: ${record.data.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumberWithCommas(record.data.usd.surplus.toFixed(2))}
                    </td>
                    <td style="color: ${record.data.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${formatNumberWithCommas(record.data.eur.surplus.toFixed(2))}
                    </td>
                    <td style="color: ${record.data.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${formatNumberWithCommas(record.data.try.surplus.toFixed(2))}
                    </td>
                    <td>$${formatNumberWithCommas(record.data.silver.total.toFixed(2))}</td>
                    <td style="color: ${record.data.realSurplus >= 0 ? '#2e7d32' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumberWithCommas(record.data.realSurplus.toFixed(2))}
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
        
        function viewRecord(index) {
            const record = historyRecords[index];
            
            document.getElementById('usd-debtor').value = record.data.usd.debtor;
            document.getElementById('usd-creditor').value = record.data.usd.creditor;
            document.getElementById('eur-debtor').value = record.data.eur.debtor;
            document.getElementById('eur-creditor').value = record.data.eur.creditor;
            document.getElementById('try-debtor').value = record.data.try.debtor;
            document.getElementById('try-creditor').value = record.data.try.creditor;
            
            // تحميل بيانات الفضة المعدلة
            document.getElementById('silver-quantity').value = record.data.silver.quantity;
            document.getElementById('silver-total-input').value = record.data.silver.total;
            
            document.getElementById('swift-profit-usd').value = record.data.profits.swift.usd;
            document.getElementById('swift-profit-eur').value = record.data.profits.swift.eur;
            document.getElementById('havala-profit-usd').value = record.data.profits.havana.usd;
            document.getElementById('havala-profit-eur').value = record.data.profits.havana.eur;
            document.getElementById('silver-profit-usd').value = record.data.profits.silver.usd;
            document.getElementById('silver-profit-eur').value = record.data.profits.silver.eur;
            
            updateCalculations();
            switchTab('input');
            
            alert("تم تحميل بيانات السجل المحدد. يمكنك تعديلها وتوليد تقرير جديد. / Seçilen kayıt verileri yüklendi. Düzenleyebilir ve yeni rapor oluşturabilirsiniz.");
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
            const historyTableBody = document.getElementById('history-table-body');
            const noHistoryRow = document.getElementById('no-history');
            
            if (filteredRecords.length === 0) {
                noHistoryRow.style.display = '';
                noHistoryRow.innerHTML = `<td colspan="9" style="text-align: center; padding: 30px;">لا توجد سجلات للتاريخ ${formatDate(filterDate)} / ${formatDate(filterDate)} tarihi için kayıt bulunamadı.</td>`;
                return;
            }
            
            noHistoryRow.style.display = 'none';
            historyTableBody.innerHTML = '';
            
            filteredRecords.forEach((record, index) => {
                const originalIndex = historyRecords.indexOf(record);
                const row = document.createElement('tr');
                
                let totalExpenseUSD = 0;
                let totalExpenseEUR = 0;
                let totalExpenseTRY = 0;
                
                record.data.expenses.forEach(expense => {
                    if (expense.currency === 'USD') totalExpenseUSD += expense.amount;
                    else if (expense.currency === 'EUR') totalExpenseEUR += expense.amount;
                    else if (expense.currency === 'TRY') totalExpenseTRY += expense.amount;
                });
                
                let expenseDisplay = '';
                if (totalExpenseUSD > 0) expenseDisplay += `$${formatNumberWithCommas(totalExpenseUSD.toFixed(2))} `;
                if (totalExpenseEUR > 0) expenseDisplay += `€${formatNumberWithCommas(totalExpenseEUR.toFixed(2))} `;
                if (totalExpenseTRY > 0) expenseDisplay += `₺${formatNumberWithCommas(totalExpenseTRY.toFixed(2))}`;
                if (!expenseDisplay) expenseDisplay = '-';
                
                const totalProfitUSD = record.data.profits.total.usd;
                const totalProfitEUR = record.data.profits.total.eur;
                let totalProfitDisplay = `$${formatNumberWithCommas(totalProfitUSD.toFixed(2))}`;
                if (totalProfitEUR > 0) {
                    totalProfitDisplay += ` / €${formatNumberWithCommas(totalProfitEUR.toFixed(2))}`;
                }
                
                row.innerHTML = `
                    <td>${formatDate(record.date)}</td>
                    <td style="color: ${record.data.usd.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumberWithCommas(record.data.usd.surplus.toFixed(2))}
                    </td>
                    <td style="color: ${record.data.eur.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        €${formatNumberWithCommas(record.data.eur.surplus.toFixed(2))}
                    </td>
                    <td style="color: ${record.data.try.surplus >= 0 ? '#1a2980' : '#d32f2f'}; font-weight: bold;">
                        ₺${formatNumberWithCommas(record.data.try.surplus.toFixed(2))}
                    </td>
                    <td>$${formatNumberWithCommas(record.data.silver.total.toFixed(2))}</td>
                    <td style="color: ${record.data.realSurplus >= 0 ? '#2e7d32' : '#d32f2f'}; font-weight: bold;">
                        $${formatNumberWithCommas(record.data.realSurplus.toFixed(2))}
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
            
            if (tabId === 'monthly') {
                updateDateRangeInfo();
                document.getElementById('compact-monthly-report').style.display = 'none';
                setTimeout(autoCollectProfits, 100);
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
    </script>
</body>
</html>
