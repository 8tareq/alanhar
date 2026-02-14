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
        
        .input-group input, .input-group select, .input-group textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border 0.3s;
        }
        
        .input-group textarea {
            min-height: 80px;
            resize: vertical;
        }
        
        .input-group input:focus, .input-group select:focus, .input-group textarea:focus {
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

        /* قسم الفضة */
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
        
        /* قسم النحاس الجديد */
        .copper-box {
            background: linear-gradient(135deg, #e0f2f1, #b2dfdb);
            border-left: 5px solid #009688;
        }
        
        .copper-title {
            color: #00695c;
        }
        
        .copper-icon {
            background-color: #009688;
        }
        
        .copper-value-box {
            background: linear-gradient(135deg, #e0f2f1, #b2dfdb);
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2rem;
            margin-top: 10px;
            border: 2px solid #009688;
        }
        
        /* قسم المصروفات بالدولار بجانب الفضة */
        .usd-expense-box {
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
            border-left: 5px solid #4caf50;
        }
        
        .usd-expense-title {
            color: #2e7d32;
        }
        
        .usd-expense-icon {
            background-color: #4caf50;
        }
        
        .usd-expense-value-box {
            background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2rem;
            margin-top: 10px;
            border: 2px solid #4caf50;
        }
        
        /* زر إضافة مصروف جديد */
        .add-usd-expense-btn {
            background-color: #e8f5e9;
            border: 2px dashed #4caf50;
            color: #2e7d32;
            padding: 10px;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            margin-top: 10px;
            transition: all 0.3s;
        }
        
        .add-usd-expense-btn:hover {
            background-color: #c8e6c9;
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
        
        /* أنماط التقرير للفضة والنحاس */
        .report-silver-section, .report-copper-section {
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            border: 2px solid;
        }
        
        .report-silver-section {
            background: linear-gradient(135deg, #fff8e1, #ffecb3);
            border-color: #ff9800;
        }
        
        .report-copper-section {
            background: linear-gradient(135deg, #e0f2f1, #b2dfdb);
            border-color: #009688;
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
        
        .report-copper-title {
            color: #00695c;
            font-size: 1.4rem;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #80cbc4;
            display: flex;
            align-items: center;
        }
        
        .report-silver-title i, .report-copper-title i {
            margin-left: 10px;
        }
        
        /* أنماط الطباعة */
        @media print {
            .report-silver-section {
                background: #fff8e1 !important;
                border: 1px solid #ff9800;
            }
            
            .report-copper-section {
                background: #e0f2f1 !important;
                border: 1px solid #009688;
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
                    
                    <!-- الفضة -->
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
                    
                    <!-- النحاس -->
                    <div class="currency-box copper-box">
                        <div class="currency-title copper-title">
                            <div class="currency-icon copper-icon">
                                <i class="fas fa-cubes"></i>
                            </div>
                            <div>النحاس (بالكيلو) / Bakır (kg)</div>
                        </div>
                        
                        <div class="input-group">
                            <label for="copper-quantity">الكمية (كيلو) / Miktar (kg)</label>
                            <div class="label-tr">Bakır miktarı kilogram cinsinden</div>
                            <input type="number" id="copper-quantity" placeholder="أدخل كمية النحاس بالكيلو / Bakır miktarını kilogram olarak girin" step="0.001" min="0">
                        </div>
                        
                        <div class="input-group">
                            <label for="copper-total-input">القيمة الإجمالية ($) / Toplam Değer ($)</label>
                            <div class="label-tr">Toplam dolar değeri</div>
                            <input type="number" id="copper-total-input" placeholder="أدخل القيمة الإجمالية بالدولار / Toplam değeri dolar olarak girin" step="0.01" min="0">
                        </div>
                        
                        <div id="copper-value" class="copper-value-box">
                            القيمة الإجمالية للنحاس: $<span id="copper-total-display">0.00</span>
                        </div>
                    </div>
                    
                    <!-- مصروفات الدولار -->
                    <div class="currency-box usd-expense-box">
                        <div class="currency-title usd-expense-title">
                            <div class="currency-icon usd-expense-icon">
                                <i class="fas fa-file-invoice-dollar"></i>
                            </div>
                            <div>مصروفات الدولار / Dolar Giderleri</div>
                        </div>
                        
                        <div id="usd-expenses-container">
                            <!-- مصروفات الدولار ستظهر هنا ديناميكياً -->
                            <div class="usd-expense-item" id="usd-expense-item-1">
                                <div class="input-group">
                                    <label for="usd-expense-name-1">وصف المصروف / Gider Açıklaması</label>
                                    <input type="text" id="usd-expense-name-1" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                                </div>
                                
                                <div class="input-group">
                                    <label for="usd-expense-amount-1">القيمة ($) / Tutar ($)</label>
                                    <input type="number" id="usd-expense-amount-1" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                                </div>
                                
                                <button class="btn btn-reset remove-usd-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="1">
                                    <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                                </button>
                            </div>
                        </div>
                        
                        <div class="add-usd-expense-btn no-print" id="add-usd-expense">
                            <i class="fas fa-plus-circle"></i> إضافة مصروف بالدولار / Yeni Dolar Gideri Ekle
                        </div>
                        
                        <div id="total-usd-expense" class="usd-expense-value-box">
                            إجمالي مصروفات الدولار: $<span id="usd-expense-total-display">0.00</span>
                        </div>
                    </div>
                </div>
                
                <!-- مربع الفائض الحقيقي المعدل مع الفضة والنحاس -->
                <div id="real-surplus-box" class="real-surplus-box">
                    <div style="font-size: 1.2rem; margin-bottom: 10px;">
                        <i class="fas fa-calculator"></i> الفائض الحقيقي / Gerçek Kar-Zarar
                    </div>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px;">
                        <div style="text-align: center; padding: 10px; background: rgba(26, 41, 128, 0.1); border-radius: 8px;">
                            <div>فائض الدولار / Dolar Kar-Zarar</div>
                            <div style="font-size: 1.5rem; font-weight: bold; color: #1a2980;" id="display-usd-surplus">$0.00</div>
                        </div>
                        <div style="text-align: center; padding: 10px; background: rgba(255, 152, 0, 0.1); border-radius: 8px;">
                            <div>ناقص قيمة الفضة / Eksi Gümüş Değeri</div>
                            <div style="font-size: 1.5rem; font-weight: bold; color: #ff9800;" id="display-silver-value">$0.00</div>
                        </div>
                        <div style="text-align: center; padding: 10px; background: rgba(0, 150, 136, 0.1); border-radius: 8px;">
                            <div>ناقص قيمة النحاس / Eksi Bakır Değeri</div>
                            <div style="font-size: 1.5rem; font-weight: bold; color: #009688;" id="display-copper-value">$0.00</div>
                        </div>
                        <div style="text-align: center; padding: 10px; background: rgba(76, 175, 80, 0.1); border-radius: 8px;">
                            <div>ناقص مصروفات الدولار / Eksi Dolar Giderleri</div>
                            <div style="font-size: 1.5rem; font-weight: bold; color: #4caf50;" id="display-usd-expense">$0.00</div>
                        </div>
                        <div style="text-align: center; padding: 10px; background: rgba(46, 125, 50, 0.2); border-radius: 8px; border: 2px solid #4caf50;">
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
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label>ربح النحاس / Bakır Kârı</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="copper-profit-usd" placeholder="أدخل ربح النحاس بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="copper-profit-eur" placeholder="أدخل ربح النحاس باليورو" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                    </div>
                    
                    <div class="profit-item">
                        <div class="input-group">
                            <label>أرباح خارجية / Dış Kârlar</label>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">$</span>
                            <div class="profit-amount">
                                <input type="number" id="external-profit-usd" placeholder="أدخل الأرباح الخارجية بالدولار" class="profit-input" step="0.01" min="0">
                            </div>
                        </div>
                        <div class="profit-currency-row">
                            <span class="profit-currency-label">€</span>
                            <div class="profit-amount">
                                <input type="number" id="external-profit-eur" placeholder="أدخل الأرباح الخارجية باليورو" class="profit-input" step="0.01" min="0">
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
            
            <!-- قسم الفضة في التقرير -->
            <div class="report-silver-section">
                <div class="report-silver-title">
                    <i class="fas fa-gem"></i> بيانات الفضة / Gümüş Verileri
                </div>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px;">
                    <div style="background: white; padding: 20px; border-radius: 10px; border: 1px solid #ffcc80;">
                        <div style="font-weight: bold; color: #ff8f00; margin-bottom: 10px;">الفضة / Gümüş</div>
                        <div style="margin-bottom: 15px;">
                            <div>الكمية (كيلو) / Miktar (kg)</div>
                            <div style="font-size: 1.3rem; text-align: center; font-weight: bold;">
                                <span id="report-silver-quantity">0.00</span> كيلو / kg
                            </div>
                        </div>
                        <div>
                            <div>القيمة الإجمالية / Toplam Değer</div>
                            <div style="font-size: 1.5rem; text-align: center; font-weight: bold; color: #ff9800;">
                                $<span id="report-silver-total">0.00</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- قسم النحاس في التقرير -->
            <div class="report-copper-section">
                <div class="report-copper-title">
                    <i class="fas fa-cubes"></i> بيانات النحاس / Bakır Verileri
                </div>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px;">
                    <div style="background: white; padding: 20px; border-radius: 10px; border: 1px solid #80cbc4;">
                        <div style="font-weight: bold; color: #00695c; margin-bottom: 10px;">النحاس / Bakır</div>
                        <div style="margin-bottom: 15px;">
                            <div>الكمية (كيلو) / Miktar (kg)</div>
                            <div style="font-size: 1.3rem; text-align: center; font-weight: bold;">
                                <span id="report-copper-quantity">0.00</span> كيلو / kg
                            </div>
                        </div>
                        <div>
                            <div>القيمة الإجمالية / Toplam Değer</div>
                            <div style="font-size: 1.5rem; text-align: center; font-weight: bold; color: #009688;">
                                $<span id="report-copper-total">0.00</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- قسم مصروفات الدولار في التقرير -->
            <div style="background: linear-gradient(135deg, #e8f5e9, #c8e6c9); padding: 20px; border-radius: 12px; margin-bottom: 25px; border: 2px solid #4caf50;">
                <div style="font-weight: bold; color: #2e7d32; margin-bottom: 10px;">مصروفات الدولار / Dolar Giderleri</div>
                <div id="report-usd-expenses-list" style="max-height: 200px; overflow-y: auto;">
                    <!-- مصروفات الدولار ستظهر هنا -->
                    <div style="text-align: center; padding: 20px; color: #666;">
                        لا توجد مصروفات مسجلة / Kayıtlı gider yok
                    </div>
                </div>
                <div style="margin-top: 15px; padding-top: 10px; border-top: 2px solid #c8e6c9;">
                    <div>الإجمالي / Toplam</div>
                    <div style="font-size: 1.5rem; text-align: center; font-weight: bold; color: #4caf50;">
                        $<span id="report-usd-expense-total">0.00</span>
                    </div>
                </div>
            </div>
            
            <!-- قسم الفائض الحقيقي في التقرير مع الفضة والنحاس -->
            <div class="real-surplus-box" style="margin-top: 20px;">
                <div style="font-size: 1.3rem; margin-bottom: 15px; display: flex; align-items: center; justify-content: center;">
                    <i class="fas fa-calculator" style="margin-left: 10px;"></i>
                    <span>الفائض الحقيقي / Gerçek Kar-Zarar</span>
                </div>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 15px;">
                    <div style="text-align: center; padding: 15px; background: rgba(26, 41, 128, 0.1); border-radius: 8px;">
                        <div style="font-size: 1.1rem; margin-bottom: 10px;">فائض الدولار / Dolar Kar-Zarar</div>
                        <div style="font-size: 1.8rem; font-weight: bold; color: #1a2980;" id="report-display-usd-surplus">$0.00</div>
                    </div>
                    <div style="text-align: center; padding: 15px; background: rgba(255, 152, 0, 0.1); border-radius: 8px;">
                        <div style="font-size: 1.1rem; margin-bottom: 10px;">ناقص قيمة الفضة / Eksi Gümüş Değeri</div>
                        <div style="font-size: 1.8rem; font-weight: bold; color: #ff9800;" id="report-display-silver-value">$0.00</div>
                    </div>
                    <div style="text-align: center; padding: 15px; background: rgba(0, 150, 136, 0.1); border-radius: 8px;">
                        <div style="font-size: 1.1rem; margin-bottom: 10px;">ناقص قيمة النحاس / Eksi Bakır Değeri</div>
                        <div style="font-size: 1.8rem; font-weight: bold; color: #009688;" id="report-display-copper-value">$0.00</div>
                    </div>
                    <div style="text-align: center; padding: 15px; background: rgba(76, 175, 80, 0.1); border-radius: 8px;">
                        <div style="font-size: 1.1rem; margin-bottom: 10px;">ناقص مصروفات الدولار / Eksi Dolar Giderleri</div>
                        <div style="font-size: 1.8rem; font-weight: bold; color: #4caf50;" id="report-display-usd-expense">$0.00</div>
                    </div>
                    <div style="text-align: center; padding: 15px; background: rgba(46, 125, 50, 0.2); border-radius: 8px; border: 2px solid #4caf50;">
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
                    <div class="profit-item">
                        <h4>ربح النحاس / Bakır Kârı</h4>
                        <div class="profit-display">
                            <span>$</span>
                            <span id="report-copper-profit-usd">0.00</span>
                        </div>
                        <div class="profit-display">
                            <span>€</span>
                            <span id="report-copper-profit-eur">0.00</span>
                        </div>
                    </div>
                    <div class="profit-item">
                        <h4>أرباح خارجية / Dış Kârlar</h4>
                        <div class="profit-display">
                            <span>$</span>
                            <span id="report-external-profit-usd">0.00</span>
                        </div>
                        <div class="profit-display">
                            <span>€</span>
                            <span id="report-external-profit-eur">0.00</span>
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
                <strong>ملاحظة / Not:</strong> أدخل بيانات المدين والدائن يدوياً، وسيتم جمع الأرباح تلقائياً من السجلات السابقة. المصاريف والأرباح التلقائية للمعلومية فقط ولا تزيد أو تنقص من الفائض. / Borçlu ve Alacaklı verilerini elle girin, kârlar otomatik olarak önceki kayıtlardan toplanacaktır. Giderler ve otomatik kârlar sadece bilgi amaçlıdır ve kar-zarardan eklenmez veya çıkarılmaz.
            </div>
            
            <!-- قسم التجميع التلقائي للأرباح -->
            <div class="auto-collect-section">
                <div class="auto-collect-title">
                    <i class="fas fa-calculator"></i> التجميع التلقائي للأرباح / Otomatik Kâr Toplama
                </div>
                
                <div class="auto-collect-info">
                    <p><strong>تفسير:</strong> سيتم تجميع جميع عمليات الربح (Swift، Havala، الفضة، النحاس، الأرباح الخارجية) تلقائياً عند اختيار الفترة الزمنية.</p>
                    <p><strong>Açıklama:</strong> Tüm kâr işlemleri (Swift, Havale, Gümüş, Bakır, Dış Kârlar) otomatik olarak zaman aralığı seçildiğinde toplanacaktır.</p>
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
                    <div class="profit-item monthly-profit-item">
                        <h4>ربح النحاس المجمع / Toplanan Bakır Kârı</h4>
                        <div class="summary-row">
                            <span>من <span id="auto-copper-start">--</span> إلى <span id="auto-copper-end">--</span></span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>$</span>
                            <span id="auto-copper-usd">0.00</span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>€</span>
                            <span id="auto-copper-eur">0.00</span>
                        </div>
                    </div>
                    <div class="profit-item monthly-profit-item">
                        <h4>الأرباح الخارجية المجمعة / Toplanan Dış Kârlar</h4>
                        <div class="summary-row">
                            <span>من <span id="auto-external-start">--</span> إلى <span id="auto-external-end">--</span></span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>$</span>
                            <span id="auto-external-usd">0.00</span>
                        </div>
                        <div class="profit-display monthly-profit-display">
                            <span>€</span>
                            <span id="auto-external-eur">0.00</span>
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
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">ربح النحاس / Bakır Kârı</div>
                                <div class="compact-value" id="compact-copper-usd">$0.00</div>
                                <div class="compact-value" id="compact-copper-eur">€0.00</div>
                            </div>
                            <div class="compact-grid-item">
                                <div class="compact-grid-title">أرباح خارجية / Dış Kârlar</div>
                                <div class="compact-value" id="compact-external-usd">$0.00</div>
                                <div class="compact-value" id="compact-external-eur">€0.00</div>
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
                                <th>قيمة النحاس / Bakır Değeri</th>
                                <th>مصروفات الدولار / Dolar Giderleri</th>
                                <th>الفائض الحقيقي / Gerçek Kar-Zarar</th>
                                <th>إجمالي الأرباح / Toplam Kâr</th>
                                <th>المصروفات / Giderler</th>
                                <th class="no-print">الإجراءات / İşlemler</th>
                            </tr>
                        </thead>
                        <tbody id="history-table-body">
                            <!-- سيتم ملء الجدول ديناميكياً -->
                            <tr id="no-history">
                                <td colspan="11" style="text-align: center; padding: 30px;">لا توجد سجلات سابقة. ابدأ بإدخال بيانات اليوم. / Önceki kayıt yok. Bugünün verilerini girmeye başlayın.</td>
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
            silver: { quantity: 0, total: 0 },
            copper: { quantity: 0, total: 0 },
            usdExpenses: [],
            usdExpenseTotal: 0,
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
                silver: { usd: 0, eur: 0 },
                copper: { usd: 0, eur: 0 },
                external: { usd: 0, eur: 0 }
            },
            monthlyExpenses: [],
            detailedProfits: []
        };

        // سجلات الأيام السابقة
        let historyRecords = JSON.parse(localStorage.getItem('alanhar_history')) || [];
        
        // سجلات التقارير الشهرية
        let monthlyRecords = JSON.parse(localStorage.getItem('alanhar_monthly')) || [];
        
        // سجلات الأرباح اليومية
        let dailyProfitOperations = JSON.parse(localStorage.getItem('alanhar_daily_profit_operations')) || [];
        
        // عداد المصروفات
        let expenseCounter = 1;
        let monthlyExpenseCounter = 1;
        let usdExpenseCounter = 1;
        
        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            initializeApp();
            setupEventListeners();
            loadHistory();
            updateCalculations();
            autoCollectProfits();
        });
        
        function initializeApp() {
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
            
            // إضافة مصروف دولار افتراضي
            setupUsdExpenseInputListeners(1);
        }
        
        function setupEventListeners() {
            // أزرار الإضافة
            document.getElementById('add-expense').addEventListener('click', addNewExpense);
            document.getElementById('add-monthly-expense').addEventListener('click', addNewMonthlyExpense);
            document.getElementById('add-usd-expense').addEventListener('click', addNewUsdExpense);
            
            // أزرار الحفظ
            document.getElementById('save-data').addEventListener('click', saveData);
            document.getElementById('save-monthly-data').addEventListener('click', saveMonthlyData);
            
            // أزرار التقرير
            document.getElementById('generate-report').addEventListener('click', generateReport);
            document.getElementById('print-report').addEventListener('click', printDailyReport);
            document.getElementById('print-monthly-report').addEventListener('click', printMonthlyReport);
            
            // أزرار إعادة التعيين
            document.getElementById('reset-data').addEventListener('click', resetData);
            document.getElementById('reset-monthly-data').addEventListener('click', resetMonthlyData);
            
            // أزرار التنقل
            document.getElementById('back-to-input').addEventListener('click', () => switchTab('input'));
            document.getElementById('clear-history').addEventListener('click', clearHistory);
            
            // التبويبات
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });
            
            // المدخلات الرئيسية
            setupInputListeners();
            
            // المدخلات الشهرية
            setupMonthlyInputListeners();
            
            // الفلترة
            document.getElementById('filter-date').addEventListener('change', filterHistory);
            
            // التجميع التلقائي
            document.getElementById('monthly-start-date').addEventListener('change', autoCollectProfits);
            document.getElementById('monthly-end-date').addEventListener('change', autoCollectProfits);
        }
        
        function setupInputListeners() {
            const inputs = [
                'usd-debtor', 'usd-creditor',
                'eur-debtor', 'eur-creditor',
                'try-debtor', 'try-creditor',
                'silver-quantity', 'silver-total-input',
                'copper-quantity', 'copper-total-input',
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
            
            // مصروفات
            for (let i = 1; i <= expenseCounter; i++) {
                setupExpenseInputListeners(i);
            }
            
            // مصروفات الدولار
            for (let i = 1; i <= usdExpenseCounter; i++) {
                setupUsdExpenseInputListeners(i);
            }
        }
        
        function setupMonthlyInputListeners() {
            const inputs = [
                'monthly-usd-debtor', 'monthly-usd-creditor',
                'monthly-eur-debtor', 'monthly-eur-creditor',
                'monthly-try-debtor', 'monthly-try-creditor'
            ];
            
            inputs.forEach(id => {
                const input = document.getElementById(id);
                if (input) {
                    input.addEventListener('input', updateMonthlyCalculations);
                }
            });
        }
        
        function setupExpenseInputListeners(id) {
            const nameInput = document.getElementById(`expense-name-${id}`);
            const amountInput = document.getElementById(`expense-amount-${id}`);
            const currencySelect = document.getElementById(`expense-currency-${id}`);
            
            if (nameInput) nameInput.addEventListener('input', updateExpensesTotal);
            if (amountInput) amountInput.addEventListener('input', updateExpensesTotal);
            if (currencySelect) currencySelect.addEventListener('change', updateExpensesTotal);
        }
        
        function setupUsdExpenseInputListeners(id) {
            const nameInput = document.getElementById(`usd-expense-name-${id}`);
            const amountInput = document.getElementById(`usd-expense-amount-${id}`);
            
            if (nameInput) nameInput.addEventListener('input', updateUsdExpensesTotal);
            if (amountInput) amountInput.addEventListener('input', updateUsdExpensesTotal);
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
            }
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
            
            // فضة
            const silverQuantity = parseFloat(document.getElementById('silver-quantity').value) || 0;
            const silverTotal = parseFloat(document.getElementById('silver-total-input').value) || 0;
            appData.silver = { quantity: silverQuantity, total: silverTotal };
            
            document.getElementById('silver-total-display').textContent = formatNumber(silverTotal);
            
            // نحاس
            const copperQuantity = parseFloat(document.getElementById('copper-quantity').value) || 0;
            const copperTotal = parseFloat(document.getElementById('copper-total-input').value) || 0;
            appData.copper = { quantity: copperQuantity, total: copperTotal };
            
            document.getElementById('copper-total-display').textContent = formatNumber(copperTotal);
            
            // فائض حقيقي
            updateUsdExpensesTotal(); // تحديث مصروفات الدولار أولاً
            appData.realSurplus = usdSurplus - silverTotal - copperTotal - appData.usdExpenseTotal;
            
            document.getElementById('display-usd-surplus').textContent = `$${formatNumber(usdSurplus)}`;
            document.getElementById('display-silver-value').textContent = `$${formatNumber(silverTotal)}`;
            document.getElementById('display-copper-value').textContent = `$${formatNumber(copperTotal)}`;
            document.getElementById('display-usd-expense').textContent = `$${formatNumber(appData.usdExpenseTotal)}`;
            document.getElementById('real-surplus').textContent = `$${formatNumber(appData.realSurplus)}`;
            
            // أرباح
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
            
            document.getElementById('total-profit-usd').textContent = formatNumber(totalProfitUSD);
            document.getElementById('total-profit-eur').textContent = formatNumber(totalProfitEUR);
            
            updateExpensesTotal();
        }
        
        function updateMonthlyCalculations() {
            // دولار
            const usdDebtor = parseFloat(document.getElementById('monthly-usd-debtor').value) || 0;
            const usdCreditor = parseFloat(document.getElementById('monthly-usd-creditor').value) || 0;
            const usdSurplus = usdDebtor - usdCreditor;
            monthlyData.usd = { debtor: usdDebtor, creditor: usdCreditor, surplus: usdSurplus };
            
            const usdSurplusElement = document.getElementById('monthly-usd-surplus');
            if (usdSurplusElement) {
                usdSurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: $${formatNumber(usdSurplus)}`;
                usdSurplusElement.className = 'result-box ' + (usdSurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
            }
            
            // يورو
            const eurDebtor = parseFloat(document.getElementById('monthly-eur-debtor').value) || 0;
            const eurCreditor = parseFloat(document.getElementById('monthly-eur-creditor').value) || 0;
            const eurSurplus = eurDebtor - eurCreditor;
            monthlyData.eur = { debtor: eurDebtor, creditor: eurCreditor, surplus: eurSurplus };
            
            const eurSurplusElement = document.getElementById('monthly-eur-surplus');
            if (eurSurplusElement) {
                eurSurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: €${formatNumber(eurSurplus)}`;
                eurSurplusElement.className = 'result-box ' + (eurSurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
            }
            
            // ليرة
            const tryDebtor = parseFloat(document.getElementById('monthly-try-debtor').value) || 0;
            const tryCreditor = parseFloat(document.getElementById('monthly-try-creditor').value) || 0;
            const trySurplus = tryDebtor - tryCreditor;
            monthlyData.try = { debtor: tryDebtor, creditor: tryCreditor, surplus: trySurplus };
            
            const trySurplusElement = document.getElementById('monthly-try-surplus');
            if (trySurplusElement) {
                trySurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: ₺${formatNumber(trySurplus)}`;
                trySurplusElement.className = 'result-box ' + (trySurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
            }
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
        
        function updateUsdExpensesTotal() {
            let totalUsdExpense = 0;
            
            appData.usdExpenses = [];
            
            for (let i = 1; i <= usdExpenseCounter; i++) {
                const nameInput = document.getElementById(`usd-expense-name-${i}`);
                const amountInput = document.getElementById(`usd-expense-amount-${i}`);
                
                if (nameInput && amountInput) {
                    const name = nameInput.value;
                    const amount = parseFloat(amountInput.value) || 0;
                    
                    if (name && amount > 0) {
                        appData.usdExpenses.push({ name, amount });
                        totalUsdExpense += amount;
                    }
                }
            }
            
            appData.usdExpenseTotal = totalUsdExpense;
            
            document.getElementById('usd-expense-total-display').textContent = formatNumber(totalUsdExpense);
            document.getElementById('display-usd-expense').textContent = `$${formatNumber(totalUsdExpense)}`;
        }
        
        function autoCollectProfits() {
            const startDate = document.getElementById('monthly-start-date').value;
            const endDate = document.getElementById('monthly-end-date').value;
            
            if (!startDate || !endDate) return;
            
            monthlyData.startDate = startDate;
            monthlyData.endDate = endDate;
            
            updateDateRangeInfo();
            
            const filteredOperations = dailyProfitOperations.filter(operation => {
                return operation.date >= startDate && operation.date <= endDate;
            });
            
            if (filteredOperations.length === 0) {
                document.getElementById('detailed-profits-container').innerHTML = `
                    <div style="text-align: center; padding: 30px; color: #666;">
                        <i class="fas fa-info-circle" style="font-size: 2rem; margin-bottom: 15px;"></i><br>
                        لا توجد سجلات للأرباح للفترة المحددة<br>
                        Seçilen dönem için kâr kaydı bulunamadı.
                    </div>
                `;
                
                document.getElementById('profit-summary').style.display = 'none';
                document.getElementById('auto-collect-stats').innerHTML = '';
                
                monthlyData.autoProfits = {
                    swift: { usd: 0, eur: 0 },
                    havana: { usd: 0, eur: 0 },
                    silver: { usd: 0, eur: 0 },
                    copper: { usd: 0, eur: 0 },
                    external: { usd: 0, eur: 0 }
                };
                
                updateAutoProfitsDisplay();
                return;
            }
            
            let totalSwiftUSD = 0, totalSwiftEUR = 0;
            let totalHavanaUSD = 0, totalHavanaEUR = 0;
            let totalSilverUSD = 0, totalSilverEUR = 0;
            let totalCopperUSD = 0, totalCopperEUR = 0;
            let totalExternalUSD = 0, totalExternalEUR = 0;
            let grandTotalUSD = 0, grandTotalEUR = 0;
            
            let detailsHtml = '';
            let operationsByDate = {};
            
            filteredOperations.forEach(operation => {
                const date = operation.date;
                if (!operationsByDate[date]) operationsByDate[date] = [];
                operationsByDate[date].push(operation);
            });
            
            Object.keys(operationsByDate).sort().forEach(date => {
                const dateOperations = operationsByDate[date];
                let dateTotalUSD = 0;
                let dateTotalEUR = 0;
                let dateSwiftUSD = 0, dateSwiftEUR = 0;
                let dateHavanaUSD = 0, dateHavanaEUR = 0;
                let dateSilverUSD = 0, dateSilverEUR = 0;
                let dateCopperUSD = 0, dateCopperEUR = 0;
                let dateExternalUSD = 0, dateExternalEUR = 0;
                
                dateOperations.forEach(operation => {
                    dateSwiftUSD += operation.profits.swift.usd || 0;
                    dateSwiftEUR += operation.profits.swift.eur || 0;
                    dateHavanaUSD += operation.profits.havana.usd || 0;
                    dateHavanaEUR += operation.profits.havana.eur || 0;
                    dateSilverUSD += operation.profits.silver.usd || 0;
                    dateSilverEUR += operation.profits.silver.eur || 0;
                    dateCopperUSD += operation.profits.copper?.usd || 0;
                    dateCopperEUR += operation.profits.copper?.eur || 0;
                    dateExternalUSD += operation.profits.external?.usd || 0;
                    dateExternalEUR += operation.profits.external?.eur || 0;
                });
                
                totalSwiftUSD += dateSwiftUSD;
                totalSwiftEUR += dateSwiftEUR;
                totalHavanaUSD += dateHavanaUSD;
                totalHavanaEUR += dateHavanaEUR;
                totalSilverUSD += dateSilverUSD;
                totalSilverEUR += dateSilverEUR;
                totalCopperUSD += dateCopperUSD;
                totalCopperEUR += dateCopperEUR;
                totalExternalUSD += dateExternalUSD;
                totalExternalEUR += dateExternalEUR;
                
                dateTotalUSD = dateSwiftUSD + dateHavanaUSD + dateSilverUSD + dateCopperUSD + dateExternalUSD;
                dateTotalEUR = dateSwiftEUR + dateHavanaEUR + dateSilverEUR + dateCopperEUR + dateExternalEUR;
                grandTotalUSD += dateTotalUSD;
                grandTotalEUR += dateTotalEUR;
                
                detailsHtml += `
                    <div class="day-profit-item">
                        <div class="day-profit-header">
                            <div class="day-profit-date">${formatDate(date)}</div>
                            <div class="day-profit-total">$${formatNumber(dateTotalUSD)} / €${formatNumber(dateTotalEUR)}</div>
                        </div>
                        <div class="day-profit-details">
                            <div class="profit-type-item">
                                <div class="profit-type-title">ربح Swift</div>
                                <div>$${formatNumber(dateSwiftUSD)}</div>
                                <div>€${formatNumber(dateSwiftEUR)}</div>
                            </div>
                            <div class="profit-type-item">
                                <div class="profit-type-title">ربح Havala</div>
                                <div>$${formatNumber(dateHavanaUSD)}</div>
                                <div>€${formatNumber(dateHavanaEUR)}</div>
                            </div>
                            <div class="profit-type-item">
                                <div class="profit-type-title">ربح الفضة</div>
                                <div>$${formatNumber(dateSilverUSD)}</div>
                                <div>€${formatNumber(dateSilverEUR)}</div>
                            </div>
                            <div class="profit-type-item">
                                <div class="profit-type-title">ربح النحاس</div>
                                <div>$${formatNumber(dateCopperUSD)}</div>
                                <div>€${formatNumber(dateCopperEUR)}</div>
                            </div>
                            <div class="profit-type-item">
                                <div class="profit-type-title">أرباح خارجية</div>
                                <div>$${formatNumber(dateExternalUSD)}</div>
                                <div>€${formatNumber(dateExternalEUR)}</div>
                            </div>
                        </div>
                    </div>
                `;
            });
            
            document.getElementById('detailed-profits-container').innerHTML = detailsHtml;
            
            document.getElementById('total-monthly-profit-usd').textContent = `$${formatNumber(grandTotalUSD)}`;
            document.getElementById('total-monthly-profit-eur').textContent = `€${formatNumber(grandTotalEUR)}`;
            
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
                silver: { usd: totalSilverUSD, eur: totalSilverEUR },
                copper: { usd: totalCopperUSD, eur: totalCopperEUR },
                external: { usd: totalExternalUSD, eur: totalExternalEUR }
            };
            
            updateAutoProfitsDisplay();
            updateAutoCollectStats(filteredOperations.length, uniqueDates, grandTotalUSD, grandTotalEUR);
        }
        
        function updateAutoCollectStats(operations, days, totalUSD, totalEUR) {
            const statsHtml = `
                <div class="collect-stat-item">
                    <div class="collect-stat-label">عدد العمليات / İşlem Sayısı</div>
                    <div class="collect-stat-value">${operations}</div>
                </div>
                <div class="collect-stat-item">
                    <div class="collect-stat-label">عدد الأيام / Gün Sayısı</div>
                    <div class="collect-stat-value">${days}</div>
                </div>
                <div class="collect-stat-item">
                    <div class="collect-stat-label">إجمالي USD / Toplam USD</div>
                    <div class="collect-stat-value">$${formatNumber(totalUSD)}</div>
                </div>
                <div class="collect-stat-item">
                    <div class="collect-stat-label">إجمالي EUR / Toplam EUR</div>
                    <div class="collect-stat-value">€${formatNumber(totalEUR)}</div>
                </div>
            `;
            
            document.getElementById('auto-collect-stats').innerHTML = statsHtml;
        }
        
        function updateAutoProfitsDisplay() {
            const elements = [
                { id: 'auto-swift-usd', value: monthlyData.autoProfits.swift.usd },
                { id: 'auto-swift-eur', value: monthlyData.autoProfits.swift.eur },
                { id: 'auto-havala-usd', value: monthlyData.autoProfits.havana.usd },
                { id: 'auto-havala-eur', value: monthlyData.autoProfits.havana.eur },
                { id: 'auto-silver-usd', value: monthlyData.autoProfits.silver.usd },
                { id: 'auto-silver-eur', value: monthlyData.autoProfits.silver.eur },
                { id: 'auto-copper-usd', value: monthlyData.autoProfits.copper.usd },
                { id: 'auto-copper-eur', value: monthlyData.autoProfits.copper.eur },
                { id: 'auto-external-usd', value: monthlyData.autoProfits.external.usd },
                { id: 'auto-external-eur', value: monthlyData.autoProfits.external.eur }
            ];
            
            elements.forEach(element => {
                const el = document.getElementById(element.id);
                if (el) el.textContent = formatNumber(element.value);
            });
            
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
            const copperProfitUSD = parseFloat(document.getElementById('copper-profit-usd').value) || 0;
            const copperProfitEUR = parseFloat(document.getElementById('copper-profit-eur').value) || 0;
            const externalProfitUSD = parseFloat(document.getElementById('external-profit-usd').value) || 0;
            const externalProfitEUR = parseFloat(document.getElementById('external-profit-eur').value) || 0;
            
            const profitOperation = {
                date: today,
                timestamp: new Date().getTime(),
                profits: {
                    swift: { usd: swiftProfitUSD, eur: swiftProfitEUR },
                    havana: { usd: havanaProfitUSD, eur: havanaProfitEUR },
                    silver: { usd: silverProfitUSD, eur: silverProfitEUR },
                    copper: { usd: copperProfitUSD, eur: copperProfitEUR },
                    external: { usd: externalProfitUSD, eur: externalProfitEUR }
                }
            };
            
            dailyProfitOperations.push(profitOperation);
            localStorage.setItem('alanhar_daily_profit_operations', JSON.stringify(dailyProfitOperations));
            
            if (document.getElementById('monthly').classList.contains('active')) {
                autoCollectProfits();
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
        
        function printMonthlyReport() {
            generateMonthlyReport();
            
            setTimeout(() => {
                window.print();
            }, 100);
        }
        
        function generateMonthlyReport() {
            updateMonthlyCalculations();
            
            const report = document.getElementById('compact-monthly-report');
            if (report) report.style.display = 'block';
            
            const startFormatted = formatDate(monthlyData.startDate);
            const endFormatted = formatDate(monthlyData.endDate);
            document.getElementById('compact-date-range').textContent = `الفترة: من ${startFormatted} إلى ${endFormatted}`;
            
            document.getElementById('compact-usd-debtor').textContent = `$${formatNumber(monthlyData.usd.debtor)}`;
            document.getElementById('compact-usd-creditor').textContent = `$${formatNumber(monthlyData.usd.creditor)}`;
            document.getElementById('compact-usd-surplus').textContent = `$${formatNumber(monthlyData.usd.surplus)}`;
            
            document.getElementById('compact-eur-debtor').textContent = `€${formatNumber(monthlyData.eur.debtor)}`;
            document.getElementById('compact-eur-creditor').textContent = `€${formatNumber(monthlyData.eur.creditor)}`;
            document.getElementById('compact-eur-surplus').textContent = `€${formatNumber(monthlyData.eur.surplus)}`;
            
            document.getElementById('compact-try-debtor').textContent = `₺${formatNumber(monthlyData.try.debtor)}`;
            document.getElementById('compact-try-creditor').textContent = `₺${formatNumber(monthlyData.try.creditor)}`;
            document.getElementById('compact-try-surplus').textContent = `₺${formatNumber(monthlyData.try.surplus)}`;
            
            document.getElementById('compact-swift-usd').textContent = `$${formatNumber(monthlyData.autoProfits.swift.usd)}`;
            document.getElementById('compact-swift-eur').textContent = `€${formatNumber(monthlyData.autoProfits.swift.eur)}`;
            document.getElementById('compact-havala-usd').textContent = `$${formatNumber(monthlyData.autoProfits.havana.usd)}`;
            document.getElementById('compact-havala-eur').textContent = `€${formatNumber(monthlyData.autoProfits.havana.eur)}`;
            document.getElementById('compact-silver-usd').textContent = `$${formatNumber(monthlyData.autoProfits.silver.usd)}`;
            document.getElementById('compact-silver-eur').textContent = `€${formatNumber(monthlyData.autoProfits.silver.eur)}`;
            document.getElementById('compact-copper-usd').textContent = `$${formatNumber(monthlyData.autoProfits.copper.usd)}`;
            document.getElementById('compact-copper-eur').textContent = `€${formatNumber(monthlyData.autoProfits.copper.eur)}`;
            document.getElementById('compact-external-usd').textContent = `$${formatNumber(monthlyData.autoProfits.external.usd)}`;
            document.getElementById('compact-external-eur').textContent = `€${formatNumber(monthlyData.autoProfits.external.eur)}`;
            
            updateCompactExpenses();
            
            const now = new Date();
            document.getElementById('compact-creation-date').textContent = formatDate(now);
            document.getElementById('compact-creation-date-tr').textContent = formatDate(now);
        }
        
        function updateCompactMonthlyReport() {
            const elements = [
                { id: 'compact-swift-usd', value: monthlyData.autoProfits.swift.usd, prefix: '$' },
                { id: 'compact-swift-eur', value: monthlyData.autoProfits.swift.eur, prefix: '€' },
                { id: 'compact-havala-usd', value: monthlyData.autoProfits.havana.usd, prefix: '$' },
                { id: 'compact-havala-eur', value: monthlyData.autoProfits.havana.eur, prefix: '€' },
                { id: 'compact-silver-usd', value: monthlyData.autoProfits.silver.usd, prefix: '$' },
                { id: 'compact-silver-eur', value: monthlyData.autoProfits.silver.eur, prefix: '€' },
                { id: 'compact-copper-usd', value: monthlyData.autoProfits.copper.usd, prefix: '$' },
                { id: 'compact-copper-eur', value: monthlyData.autoProfits.copper.eur, prefix: '€' },
                { id: 'compact-external-usd', value: monthlyData.autoProfits.external.usd, prefix: '$' },
                { id: 'compact-external-eur', value: monthlyData.autoProfits.external.eur, prefix: '€' }
            ];
            
            elements.forEach(element => {
                const el = document.getElementById(element.id);
                if (el) el.textContent = `${element.prefix}${formatNumber(element.value)}`;
            });
        }
        
        function updateCompactExpenses() {
            const container = document.getElementById('compact-expenses-list');
            if (!container) return;
            
            container.innerHTML = '';
            
            if (monthlyData.monthlyExpenses.length === 0) {
                container.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666; grid-column: 1 / -1;">
                        لا توجد مصروفات مسجلة / Kayıtlı gider yok
                    </div>
                `;
                return;
            }
            
            const expensesByCurrency = {
                USD: { total: 0, items: [] },
                EUR: { total: 0, items: [] },
                TRY: { total: 0, items: [] }
            };
            
            monthlyData.monthlyExpenses.forEach(expense => {
                if (expensesByCurrency[expense.currency]) {
                    expensesByCurrency[expense.currency].total += expense.amount;
                    expensesByCurrency[expense.currency].items.push(expense);
                }
            });
            
            Object.entries(expensesByCurrency).forEach(([currency, data]) => {
                if (data.items.length > 0) {
                    const symbol = currency === 'USD' ? '$' : currency === 'EUR' ? '€' : '₺';
                    const title = currency === 'USD' ? 'الدولار الأمريكي' : 
                                  currency === 'EUR' ? 'اليورو الأوروبي' : 'الليرة التركية';
                    const titleTr = currency === 'USD' ? 'Amerikan Doları' : 
                                    currency === 'EUR' ? 'Euro' : 'Türk Lirası';
                    
                    let itemsHtml = '';
                    data.items.forEach(expense => {
                        itemsHtml += `
                            <div class="compact-currency-row">
                                <span>${expense.name}</span>
                                <span>${symbol}${formatNumber(expense.amount)}</span>
                            </div>
                        `;
                    });
                    
                    const box = document.createElement('div');
                    box.className = 'compact-grid-item';
                    box.innerHTML = `
                        <div class="compact-grid-title">${title} / ${titleTr}</div>
                        ${itemsHtml}
                        <div class="compact-currency-row compact-total-row">
                            <span>الإجمالي / Toplam</span>
                            <span>${symbol}${formatNumber(data.total)}</span>
                        </div>
                    `;
                    
                    container.appendChild(box);
                }
            });
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
                    <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
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
        
        function addNewUsdExpense() {
            usdExpenseCounter++;
            
            const container = document.getElementById('usd-expenses-container');
            if (!container) return;
            
            const expenseItem = document.createElement('div');
            expenseItem.className = 'usd-expense-item';
            expenseItem.id = `usd-expense-item-${usdExpenseCounter}`;
            expenseItem.innerHTML = `
                <div class="input-group">
                    <label for="usd-expense-name-${usdExpenseCounter}">وصف المصروف / Gider Açıklaması</label>
                    <input type="text" id="usd-expense-name-${usdExpenseCounter}" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                </div>
                
                <div class="input-group">
                    <label for="usd-expense-amount-${usdExpenseCounter}">القيمة ($) / Tutar ($)</label>
                    <input type="number" id="usd-expense-amount-${usdExpenseCounter}" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                </div>
                
                <button class="btn btn-reset remove-usd-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="${usdExpenseCounter}">
                    <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                </button>
            `;
            
            container.appendChild(expenseItem);
            
            setupUsdExpenseInputListeners(usdExpenseCounter);
            
            const removeBtn = expenseItem.querySelector('.remove-usd-expense-btn');
            if (removeBtn) {
                removeBtn.addEventListener('click', function() {
                    removeUsdExpense(usdExpenseCounter);
                });
            }
            
            updateUsdExpensesTotal();
        }
        
        function removeUsdExpense(id) {
            const item = document.getElementById(`usd-expense-item-${id}`);
            if (item) {
                item.remove();
                updateUsdExpensesTotal();
            }
        }
        
        function addNewMonthlyExpense() {
            monthlyExpenseCounter++;
            
            const container = document.getElementById('monthly-expenses-list');
            if (!container) return;
            
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
            
            container.appendChild(expenseItem);
            
            const removeBtn = expenseItem.querySelector('.remove-monthly-expense-btn');
            if (removeBtn) {
                removeBtn.addEventListener('click', function() {
                    removeMonthlyExpense(monthlyExpenseCounter);
                });
            }
        }
        
        function removeMonthlyExpense(id) {
            const item = document.getElementById(`monthly-expense-item-${id}`);
            if (item) item.remove();
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
                
                monthlyRecords.push(monthlyReport);
                localStorage.setItem('alanhar_monthly', JSON.stringify(monthlyRecords));
                
                alert("تم حفظ التقرير الشهري بنجاح! / Aylık rapor başarıyla kaydedildi!");
            } else {
                alert("يرجى تحديد تاريخ البداية والنهاية أولاً. / Lütfen önce başlangıç ve bitiş tarihlerini seçin.");
            }
        }
        
        function updateMonthlyExpenses() {
            monthlyData.monthlyExpenses = [];
            
            for (let i = 1; i <= monthlyExpenseCounter; i++) {
                const nameSelect = document.getElementById(`monthly-expense-name-${i}`);
                const amountInput = document.getElementById(`monthly-expense-amount-${i}`);
                const currencySelect = document.getElementById(`monthly-expense-currency-${i}`);
                
                if (nameSelect && amountInput && currencySelect) {
                    const name = nameSelect.options[nameSelect.selectedIndex].text;
                    const amount = parseFloat(amountInput.value) || 0;
                    const currency = currencySelect.value;
                    
                    if (amount > 0) {
                        monthlyData.monthlyExpenses.push({ name, amount, currency });
                    }
                }
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
            
            document.getElementById('report-silver-quantity').textContent = formatNumber(appData.silver.quantity, 3);
            document.getElementById('report-silver-total').textContent = formatNumber(appData.silver.total);
            
            document.getElementById('report-copper-quantity').textContent = formatNumber(appData.copper.quantity, 3);
            document.getElementById('report-copper-total').textContent = formatNumber(appData.copper.total);
            
            document.getElementById('report-display-usd-surplus').textContent = `$${formatNumber(appData.usd.surplus)}`;
            document.getElementById('report-display-silver-value').textContent = `$${formatNumber(appData.silver.total)}`;
            document.getElementById('report-display-copper-value').textContent = `$${formatNumber(appData.copper.total)}`;
            document.getElementById('report-display-usd-expense').textContent = `$${formatNumber(appData.usdExpenseTotal)}`;
            document.getElementById('report-real-surplus').textContent = `$${formatNumber(appData.realSurplus)}`;
            
            document.getElementById('report-swift-usd').textContent = formatNumber(appData.profits.swift.usd);
            document.getElementById('report-swift-eur').textContent = formatNumber(appData.profits.swift.eur);
            document.getElementById('report-havala-usd').textContent = formatNumber(appData.profits.havana.usd);
            document.getElementById('report-havala-eur').textContent = formatNumber(appData.profits.havana.eur);
            document.getElementById('report-silver-profit-usd').textContent = formatNumber(appData.profits.silver.usd);
            document.getElementById('report-silver-profit-eur').textContent = formatNumber(appData.profits.silver.eur);
            document.getElementById('report-copper-profit-usd').textContent = formatNumber(appData.profits.copper.usd);
            document.getElementById('report-copper-profit-eur').textContent = formatNumber(appData.profits.copper.eur);
            document.getElementById('report-external-profit-usd').textContent = formatNumber(appData.profits.external.usd);
            document.getElementById('report-external-profit-eur').textContent = formatNumber(appData.profits.external.eur);
            document.getElementById('report-total-profit-usd').textContent = formatNumber(appData.profits.total.usd);
            document.getElementById('report-total-profit-eur').textContent = formatNumber(appData.profits.total.eur);
            
            updateReportUsdExpenses();
            updateReportExpenses();
            
            switchTab('report');
        }
        
        function updateReportUsdExpenses() {
            const container = document.getElementById('report-usd-expenses-list');
            if (!container) return;
            
            container.innerHTML = '';
            
            if (appData.usdExpenses.length === 0) {
                container.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666;">
                        لا توجد مصروفات مسجلة / Kayıtlı gider yok
                    </div>
                `;
                document.getElementById('report-usd-expense-total').textContent = '0.00';
                return;
            }
            
            appData.usdExpenses.forEach(expense => {
                const expenseDiv = document.createElement('div');
                expenseDiv.style.display = 'flex';
                expenseDiv.style.justifyContent = 'space-between';
                expenseDiv.style.padding = '8px 0';
                expenseDiv.style.borderBottom = '1px solid #eee';
                expenseDiv.innerHTML = `
                    <span>${expense.name}</span>
                    <span style="font-weight: bold; color: #4caf50;">$${formatNumber(expense.amount)}</span>
                `;
                container.appendChild(expenseDiv);
            });
            
            document.getElementById('report-usd-expense-total').textContent = formatNumber(appData.usdExpenseTotal);
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
        
        function resetData() {
            if (confirm("هل تريد مسح جميع بيانات اليوم؟ / Bugünün tüm verilerini temizlemek istiyor musunuz?")) {
                const inputs = [
                    'usd-debtor', 'usd-creditor',
                    'eur-debtor', 'eur-creditor',
                    'try-debtor', 'try-creditor',
                    'silver-quantity', 'silver-total-input',
                    'copper-quantity', 'copper-total-input',
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
                
                const usdExpensesContainer = document.getElementById('usd-expenses-container');
                if (usdExpensesContainer) {
                    usdExpensesContainer.innerHTML = '';
                    usdExpenseCounter = 1;
                    
                    const expenseItem = document.createElement('div');
                    expenseItem.className = 'usd-expense-item';
                    expenseItem.id = `usd-expense-item-1`;
                    expenseItem.innerHTML = `
                        <div class="input-group">
                            <label for="usd-expense-name-1">وصف المصروف / Gider Açıklaması</label>
                            <input type="text" id="usd-expense-name-1" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası">
                        </div>
                        
                        <div class="input-group">
                            <label for="usd-expense-amount-1">القيمة ($) / Tutar ($)</label>
                            <input type="number" id="usd-expense-amount-1" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0">
                        </div>
                        
                        <button class="btn btn-reset remove-usd-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="1">
                            <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                        </button>
                    `;
                    usdExpensesContainer.appendChild(expenseItem);
                    setupUsdExpenseInputListeners(1);
                }
                
                appData = {
                    usd: { debtor: 0, creditor: 0, surplus: 0 },
                    eur: { debtor: 0, creditor: 0, surplus: 0 },
                    try: { debtor: 0, creditor: 0, surplus: 0 },
                    silver: { quantity: 0, total: 0 },
                    copper: { quantity: 0, total: 0 },
                    usdExpenses: [],
                    usdExpenseTotal: 0,
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
        
        function resetMonthlyData() {
            if (confirm("هل تريد مسح جميع بيانات التقرير الشهري؟ / Tüm aylık rapor verilerini temizlemek istiyor musunuz?")) {
                const inputs = [
                    'monthly-usd-debtor', 'monthly-usd-creditor',
                    'monthly-eur-debtor', 'monthly-eur-creditor',
                    'monthly-try-debtor', 'monthly-try-creditor'
                ];
                
                inputs.forEach(id => {
                    const input = document.getElementById(id);
                    if (input) input.value = '';
                });
                
                const expensesList = document.getElementById('monthly-expenses-list');
                if (expensesList) {
                    expensesList.innerHTML = '';
                    monthlyExpenseCounter = 1;
                }
                
                monthlyData = {
                    startDate: monthlyData.startDate,
                    endDate: monthlyData.endDate,
                    usd: { debtor: 0, creditor: 0, surplus: 0 },
                    eur: { debtor: 0, creditor: 0, surplus: 0 },
                    try: { debtor: 0, creditor: 0, surplus: 0 },
                    autoProfits: {
                        swift: { usd: 0, eur: 0 },
                        havana: { usd: 0, eur: 0 },
                        silver: { usd: 0, eur: 0 },
                        copper: { usd: 0, eur: 0 },
                        external: { usd: 0, eur: 0 }
                    },
                    monthlyExpenses: [],
                    detailedProfits: []
                };
                
                updateMonthlyCalculations();
                
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
                
                // حساب إجمالي مصروفات الدولار
                let usdExpenseTotal = 0;
                if (record.data.usdExpenses) {
                    record.data.usdExpenses.forEach(expense => {
                        usdExpenseTotal += expense.amount || 0;
                    });
                } else {
                    usdExpenseTotal = record.data.usdExpenseTotal || 0;
                }
                
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
                    <td>$${formatNumber(record.data.silver.total)}</td>
                    <td>$${formatNumber(record.data.copper.total || 0)}</td>
                    <td>$${formatNumber(usdExpenseTotal)}</td>
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
            document.getElementById('silver-quantity').value = record.data.silver.quantity;
            document.getElementById('silver-total-input').value = record.data.silver.total;
            document.getElementById('copper-quantity').value = record.data.copper.quantity || 0;
            document.getElementById('copper-total-input').value = record.data.copper.total || 0;
            
            document.getElementById('swift-profit-usd').value = record.data.profits.swift.usd;
            document.getElementById('swift-profit-eur').value = record.data.profits.swift.eur;
            document.getElementById('havala-profit-usd').value = record.data.profits.havana.usd;
            document.getElementById('havala-profit-eur').value = record.data.profits.havana.eur;
            document.getElementById('silver-profit-usd').value = record.data.profits.silver.usd;
            document.getElementById('silver-profit-eur').value = record.data.profits.silver.eur;
            document.getElementById('copper-profit-usd').value = record.data.profits.copper?.usd || 0;
            document.getElementById('copper-profit-eur').value = record.data.profits.copper?.eur || 0;
            document.getElementById('external-profit-usd').value = record.data.profits.external?.usd || 0;
            document.getElementById('external-profit-eur').value = record.data.profits.external?.eur || 0;
            
            // تحميل مصروفات الدولار
            const usdExpensesContainer = document.getElementById('usd-expenses-container');
            if (usdExpensesContainer && record.data.usdExpenses) {
                usdExpensesContainer.innerHTML = '';
                usdExpenseCounter = 0;
                
                record.data.usdExpenses.forEach((expense, i) => {
                    usdExpenseCounter++;
                    const expenseItem = document.createElement('div');
                    expenseItem.className = 'usd-expense-item';
                    expenseItem.id = `usd-expense-item-${usdExpenseCounter}`;
                    expenseItem.innerHTML = `
                        <div class="input-group">
                            <label for="usd-expense-name-${usdExpenseCounter}">وصف المصروف / Gider Açıklaması</label>
                            <input type="text" id="usd-expense-name-${usdExpenseCounter}" placeholder="مثال: إيجار المحل / Örnek: Dükkan kirası" value="${expense.name || ''}">
                        </div>
                        
                        <div class="input-group">
                            <label for="usd-expense-amount-${usdExpenseCounter}">القيمة ($) / Tutar ($)</label>
                            <input type="number" id="usd-expense-amount-${usdExpenseCounter}" placeholder="أدخل قيمة المصروف / Gider tutarını girin" step="0.01" min="0" value="${expense.amount || 0}">
                        </div>
                        
                        <button class="btn btn-reset remove-usd-expense-btn" style="padding: 8px 15px; font-size: 0.9rem; margin-top: 10px;" data-id="${usdExpenseCounter}">
                            <i class="fas fa-trash"></i> حذف هذا المصروف / Bu Gideri Sil
                        </button>
                    `;
                    usdExpensesContainer.appendChild(expenseItem);
                    setupUsdExpenseInputListeners(usdExpenseCounter);
                    
                    const removeBtn = expenseItem.querySelector('.remove-usd-expense-btn');
                    if (removeBtn) {
                        removeBtn.addEventListener('click', function() {
                            removeUsdExpense(usdExpenseCounter);
                        });
                    }
                });
            }
            
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
                        <td colspan="11" style="text-align: center; padding: 30px;">
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
                
                // حساب إجمالي مصروفات الدولار
                let usdExpenseTotal = 0;
                if (record.data.usdExpenses) {
                    record.data.usdExpenses.forEach(expense => {
                        usdExpenseTotal += expense.amount || 0;
                    });
                } else {
                    usdExpenseTotal = record.data.usdExpenseTotal || 0;
                }
                
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
                    <td>$${formatNumber(record.data.silver.total)}</td>
                    <td>$${formatNumber(record.data.copper.total || 0)}</td>
                    <td>$${formatNumber(usdExpenseTotal)}</td>
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
            
            if (tabId === 'monthly') {
                updateDateRangeInfo();
                document.getElementById('compact-monthly-report').style.display = 'none';
                autoCollectProfits();
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
        
        // جعل الدوال متاحة عالمياً
        window.viewRecord = viewRecord;
        window.deleteRecord = deleteRecord;
    </script>
</body>
</html>
