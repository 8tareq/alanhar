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

        /* أنماط الطباعة A4 */
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

            .card, .monthly-card, .real-surplus-box, .summary-card {
                break-inside: avoid;
                box-shadow: none !important;
                border: 1px solid #ddd !important;
                background: white !important;
            }

            .report-table {
                border: 1px solid #ddd;
            }

            .report-table th {
                background-color: #f0f0f0 !important;
                color: black !important;
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            .summary-box {
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            .positive, .negative, .monthly-positive, .monthly-negative {
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            .saljog-box, .auto-collect-section, .monthly-data-section {
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }

            header, footer, .tabs, .actions, .warning, .info-box, .add-expense-btn {
                display: none !important;
            }

            .compact-monthly-report {
                display: block !important;
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

        .saljog-value-box {
            background: linear-gradient(135deg, #b3e5fc, #81d4fa);
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            font-weight: bold;
            font-size: 1.2rem;
            margin-top: 10px;
            border: 2px solid #0288d1;
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

        /* التقرير الشهري المختصر */
        .compact-monthly-report {
            background: white;
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .compact-report-header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #8e24aa;
        }

        .compact-report-header h2 {
            color: #8e24aa;
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        .compact-date-range {
            font-size: 1.2rem;
            color: #666;
        }

        .compact-section {
            margin-bottom: 30px;
        }

        .compact-section-title {
            font-size: 1.3rem;
            font-weight: bold;
            margin-bottom: 15px;
            padding-bottom: 5px;
            border-bottom: 2px solid;
        }

        .compact-currency-title {
            color: #1a2980;
            border-bottom-color: #1a2980;
        }

        .compact-profit-title {
            color: #ef6c00;
            border-bottom-color: #ffb74d;
        }

        .compact-expense-title {
            color: #d32f2f;
            border-bottom-color: #ffcdd2;
        }

        .compact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .compact-grid-item {
            border: 1px solid #ddd;
            padding: 15px;
            border-radius: 8px;
            background: #f9f9f9;
        }

        .compact-grid-title {
            font-weight: bold;
            margin-bottom: 10px;
            color: #1a2980;
        }

        .compact-currency-row {
            display: flex;
            justify-content: space-between;
            padding: 5px 0;
        }

        .compact-total-row {
            font-weight: bold;
            border-top: 1px solid #ddd;
            margin-top: 5px;
            padding-top: 5px;
        }

        .compact-value {
            font-size: 1.2rem;
            font-weight: bold;
            text-align: center;
            padding: 5px;
        }

        .compact-note {
            margin-top: 20px;
            padding: 15px;
            background: #fff3e0;
            border-radius: 8px;
            font-size: 0.9rem;
        }

        .compact-report-footer {
            margin-top: 30px;
            text-align: center;
            padding: 20px;
            border-top: 1px solid #ddd;
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

        <!-- قسم التقرير الشهري الكامل -->
        <div id="monthly" class="content-section">
            <div class="report-header monthly-header">
                <h2>تقرير شهري كامل - نظام ALANHAR</h2>
                <div class="date" id="monthly-report-date">التقرير الشهري / Aylık Rapor</div>
                <div class="subtitle-tr">Detaylı Aylık Rapor - ALANHAR Sistemi</div>
            </div>

            <div class="monthly-warning no-print">
                <i class="fas fa-calendar-alt"></i>
                <strong>ملاحظة / Not:</strong> اختر الفترة الزمنية لتجميع الأرباح التلقائية، وأدخل بيانات المدين والدائن والمصروفات الشهرية.
            </div>

            <div class="auto-collect-section">
                <div class="auto-collect-title">
                    <i class="fas fa-calculator"></i> التجميع التلقائي للأرباح / Otomatik Kâr Toplama
                </div>
                <div class="auto-collect-info">
                    <p><strong>تفسير:</strong> سيتم تجميع جميع عمليات الربح (Swift، Havala، الأرباح الخارجية) تلقائياً عند اختيار الفترة الزمنية.</p>
                    <p><strong>Açıklama:</strong> Tüm kâr işlemleri (Swift, Havale, Dış Kârlar) otomatik olarak zaman aralığı seçildiğinde toplanacaktır.</p>
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

                <div id="date-range-info" class="date-range-info"></div>
                <div id="auto-collect-stats" class="auto-collect-stats"></div>
            </div>

            <div class="detailed-profit-section">
                <div class="detailed-profit-title">
                    <i class="fas fa-coins"></i> تفاصيل الأرباح اليومية المجمعة / Günlük Kârların Detaylı Özeti
                </div>

                <div id="detailed-profits-container">
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

            <div class="monthly-data-section no-print">
                <div class="monthly-data-title">
                    <i class="fas fa-money-bill-wave"></i> إدخال بيانات المدين والدائن الشهرية / Aylık Borçlu ve Alacaklı Veri Girişi
                </div>

                <div class="currency-container">
                    <div class="currency-box monthly-currency-box">
                        <div class="currency-title monthly-currency-title">
                            <div class="currency-icon monthly-currency-icon">$</div>
                            <div>الدولار الأمريكي (USD) / Amerikan Doları</div>
                        </div>

                        <div class="input-group">
                            <label for="monthly-usd-debtor">المدين الشهري (الخروج) / Aylık Borçlu (Çıkış)</label>
                            <div class="label-tr">Aylık çıkan para miktarı</div>
                            <input type="number" id="monthly-usd-debtor" class="monthly-input" placeholder="أدخل قيمة المدين الشهري بالدولار" step="0.01" min="0">
                        </div>

                        <div class="input-group">
                            <label for="monthly-usd-creditor">الدائن الشهري (الدخول) / Aylık Alacaklı (Giriş)</label>
                            <div class="label-tr">Aylık giren para miktarı</div>
                            <input type="number" id="monthly-usd-creditor" class="monthly-input" placeholder="أدخل قيمة الدائن الشهري بالدولار" step="0.01" min="0">
                        </div>

                        <div id="monthly-usd-surplus" class="result-box monthly-positive">
                            الفائض الشهري / Aylık Kar-Zarar: $0.00
                        </div>
                    </div>

                    <div class="currency-box monthly-currency-box">
                        <div class="currency-title monthly-currency-title">
                            <div class="currency-icon monthly-currency-icon">€</div>
                            <div>اليورو الأوروبي (EUR) / Euro</div>
                        </div>

                        <div class="input-group">
                            <label for="monthly-eur-debtor">المدين الشهري (الخروج) / Aylık Borçlu (Çıkış)</label>
                            <div class="label-tr">Aylık çıkan para miktarı</div>
                            <input type="number" id="monthly-eur-debtor" class="monthly-input" placeholder="أدخل قيمة المدين الشهري باليورو" step="0.01" min="0">
                        </div>

                        <div class="input-group">
                            <label for="monthly-eur-creditor">الدائن الشهري (الدخول) / Aylık Alacaklı (Giriş)</label>
                            <div class="label-tr">Aylık giren para miktarı</div>
                            <input type="number" id="monthly-eur-creditor" class="monthly-input" placeholder="أدخل قيمة الدائن الشهري باليورو" step="0.01" min="0">
                        </div>

                        <div id="monthly-eur-surplus" class="result-box monthly-positive">
                            الفائض الشهري / Aylık Kar-Zarar: €0.00
                        </div>
                    </div>

                    <div class="currency-box monthly-currency-box">
                        <div class="currency-title monthly-currency-title">
                            <div class="currency-icon monthly-currency-icon">₺</div>
                            <div>الليرة التركية (TRY) / Türk Lirası</div>
                        </div>

                        <div class="input-group">
                            <label for="monthly-try-debtor">المدين الشهري (الخروج) / Aylık Borçlu (Çıkış)</label>
                            <div class="label-tr">Aylık çıkan para miktarı</div>
                            <input type="number" id="monthly-try-debtor" class="monthly-input" placeholder="أدخل قيمة المدين الشهري بالليرة" step="0.01" min="0">
                        </div>

                        <div class="input-group">
                            <label for="monthly-try-creditor">الدائن الشهري (الدخول) / Aylık Alacaklı (Giriş)</label>
                            <div class="label-tr">Aylık giren para miktarı</div>
                            <input type="number" id="monthly-try-creditor" class="monthly-input" placeholder="أدخل قيمة الدائن الشهري بالليرة" step="0.01" min="0">
                        </div>

                        <div id="monthly-try-surplus" class="result-box monthly-positive">
                            الفائض الشهري / Aylık Kar-Zarar: ₺0.00
                        </div>
                    </div>
                </div>
            </div>

            <div class="auto-profit-section no-print">
                <div class="auto-profit-title">
                    <i class="fas fa-coins"></i> الأرباح التلقائية من السجلات السابقة / Önceki Kayıtlardan Otomatik Kârlar
                </div>

                <div class="profit-container">
                    <div class="profit-item monthly-profit-item">
                        <h4>ربح Swift المجمع / Toplanan Swift Kârı</h4>
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
                        <h4>الأرباح الخارجية المجمعة / Toplanan Dış Kârlar</h4>
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

            <div class="monthly-section no-print">
                <div class="monthly-section-title">
                    <i class="fas fa-receipt"></i> المصروفات الشهرية / Aylık Giderler
                </div>

                <div id="monthly-expenses-container">
                    <div class="expense-container" id="monthly-expenses-list">
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
                                <input type="number" id="monthly-expense-amount-1" class="monthly-input" placeholder="أدخل قيمة المصروف" step="0.01" min="0">
                            </div>

                            <div class="input-group">
                                <label for="monthly-expense-currency-1">العملة / Para Birimi</label>
                                <select id="monthly-expense-currency-1" class="monthly-select">
                                    <option value="USD">الدولار الأمريكي ($) / Amerikan Doları</option>
                                    <option value="EUR">اليورو الأوروبي (€) / Euro</option>
                                    <option value="TRY">الليرة التركية (₺) / Türk Lirası</option>
                                </select>
                            </div>

                            <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px;" data-id="1">
                                <i class="fas fa-trash"></i> حذف / Sil
                            </button>
                        </div>
                    </div>
                </div>

                <div class="add-expense-btn monthly-add-btn no-print" id="add-monthly-expense">
                    <i class="fas fa-plus-circle"></i> إضافة مصروف شهري جديد / Yeni Aylık Gider Ekle
                </div>
            </div>

            <!-- التقرير الشهري المختصر للطباعة -->
            <div id="compact-monthly-report" class="compact-monthly-report" style="display: none;">
                <div class="compact-report-header">
                    <h2>تقرير شهري مختصر - نظام ALANHAR</h2>
                    <div class="compact-date-range" id="compact-date-range">الفترة: من -- إلى --</div>
                    <div style="margin-top: 5px; font-size: 1.1rem;">Aylık Özet Rapor - ALANHAR Sistemi</div>
                </div>

                <div class="compact-report-content">
                    <div class="compact-section">
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

                    <div class="compact-section">
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
                                <div class="compact-grid-title">أرباح خارجية / Dış Kârlar</div>
                                <div class="compact-value" id="compact-external-usd">$0.00</div>
                                <div class="compact-value" id="compact-external-eur">€0.00</div>
                            </div>
                        </div>
                    </div>

                    <div class="compact-section">
                        <div class="compact-section-title compact-expense-title">
                            <i class="fas fa-receipt"></i> المصروفات الشهرية / Aylık Giderler
                        </div>
                        <div class="compact-grid" id="compact-expenses-list">
                            <div style="text-align: center; padding: 20px; color: #666; grid-column: 1 / -1;">
                                لا توجد مصروفات مسجلة / Kayıtlı gider yok
                            </div>
                        </div>
                    </div>

                    <div class="compact-note">
                        <strong>ملاحظة:</strong> المصاريف والأرباح التلقائية للمعلومية فقط ولا تزيد أو تنقص من الفائض.<br>
                        <strong>Not:</strong> Giderler ve otomatik kârlar sadece bilgi amaçlıdır ve kar-zarardan eklenmez veya çıkarılmaz.
                    </div>
                </div>

                <div class="compact-report-footer">
                    <div>نظام ALANHAR لإدارة محلات الصرافة والحوالات</div>
                    <div>ALANHAR Sistemi - Döviz ve Havale Yönetimi</div>
                    <div style="margin-top: 10px;">تم الإنشاء في: <span id="compact-creation-date">--</span> / Oluşturulma Tarihi: <span id="compact-creation-date-tr">--</span></div>
                </div>
            </div>

            <div class="actions no-print">
                <button class="btn btn-print" id="print-monthly-report">
                    <i class="fas fa-print"></i> طباعة التقرير الشهري / Aylık Raporu Yazdır
                </button>
                <button class="btn btn-save" id="save-monthly-data">
                    <i class="fas fa-save"></i> حفظ البيانات الشهرية / Aylık Verileri Kaydet
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
                                <th>رصيد الصلج / Saljoğ Bakiyesi</th>
                                <th>مصروف الصلج / Saljoğ Gider</th>
                                <th>مكسب الصلج / Saljoğ Kâr</th>
                                <th>مجموع الصلج / Saljoğ Toplam</th>
                                <th>الفائض الحقيقي / Gerçek Kar-Zarar</th>
                                <th>المصروفات / Giderler</th>
                                <th class="no-print">الإجراءات / İşlemler</th>
                            </tr>
                        </thead>
                        <tbody id="history-table-body">
                            <tr id="no-history">
                                <td colspan="11" style="text-align: center; padding: 30px;">لا توجد سجلات سابقة. ابدأ بإدخال بيانات اليوم. / Önceki kayıt yok. Bugünün verilerini girmeye başlayın.</td>
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
                external: { usd: 0, eur: 0 },
                total: { usd: 0, eur: 0 }
            },
            expenses: [],
            date: new Date().toISOString().split('T')[0],
            timestamp: new Date().getTime()
        };

        let monthlyData = {
            startDate: '',
            endDate: '',
            usd: { debtor: 0, creditor: 0, surplus: 0 },
            eur: { debtor: 0, creditor: 0, surplus: 0 },
            try: { debtor: 0, creditor: 0, surplus: 0 },
            autoProfits: {
                swift: { usd: 0, eur: 0 },
                havana: { usd: 0, eur: 0 },
                external: { usd: 0, eur: 0 }
            },
            monthlyExpenses: [],
            detailedProfits: []
        };

        let historyRecords = JSON.parse(localStorage.getItem('alanhar_history')) || [];
        let monthlyRecords = JSON.parse(localStorage.getItem('alanhar_monthly')) || [];
        let dailyProfitOperations = JSON.parse(localStorage.getItem('alanhar_daily_profit_operations')) || [];

        let expenseCounter = 1;
        let monthlyExpenseCounter = 1;

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
        }

        function setupEventListeners() {
            document.getElementById('add-expense').addEventListener('click', addNewExpense);
            document.getElementById('add-monthly-expense').addEventListener('click', addNewMonthlyExpense);

            document.getElementById('save-data').addEventListener('click', saveData);
            document.getElementById('save-monthly-data').addEventListener('click', saveMonthlyData);

            document.getElementById('generate-report').addEventListener('click', generateReport);
            document.getElementById('print-report').addEventListener('click', printDailyReport);
            document.getElementById('print-monthly-report').addEventListener('click', printMonthlyReport);

            document.getElementById('reset-data').addEventListener('click', resetData);
            document.getElementById('reset-monthly-data').addEventListener('click', resetMonthlyData);

            document.getElementById('back-to-input').addEventListener('click', () => switchTab('input'));
            document.getElementById('clear-history').addEventListener('click', clearHistory);

            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });

            setupInputListeners();
            setupMonthlyInputListeners();

            document.getElementById('filter-date').addEventListener('change', filterHistory);

            document.getElementById('monthly-start-date').addEventListener('change', autoCollectProfits);
            document.getElementById('monthly-end-date').addEventListener('change', autoCollectProfits);
        }

        function setupInputListeners() {
            const inputs = [
                'usd-debtor', 'usd-creditor',
                'eur-debtor', 'eur-creditor',
                'try-debtor', 'try-creditor',
                'saljog-amount', 'saljog-expense', 'saljog-profit'
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

            // حساب الصلج
            const saljogAmount = parseFloat(document.getElementById('saljog-amount').value) || 0;
            const saljogExpense = parseFloat(document.getElementById('saljog-expense').value) || 0;
            const saljogProfit = parseFloat(document.getElementById('saljog-profit').value) || 0;
            const saljogTotal = saljogAmount - saljogExpense + saljogProfit;
            appData.saljog = { amount: saljogAmount, expense: saljogExpense, profit: saljogProfit, total: saljogTotal };

            document.getElementById('saljog-total').textContent = `مجموع الصلج: $${formatNumber(saljogTotal)} (الرصيد - المصروف + المكسب)`;

            // الفائض الحقيقي = فائض الدولار - مجموع الصلج
            appData.realSurplus = usdSurplus - saljogTotal;

            // تحديث العرض
            document.getElementById('display-usd-surplus').textContent = `$${formatNumber(usdSurplus)}`;
            document.getElementById('display-saljog-total').textContent = `$${formatNumber(saljogTotal)}`;
            document.getElementById('real-surplus').textContent = `$${formatNumber(appData.realSurplus)}`;

            updateExpensesTotal();
        }

        function updateMonthlyCalculations() {
            const usdDebtor = parseFloat(document.getElementById('monthly-usd-debtor').value) || 0;
            const usdCreditor = parseFloat(document.getElementById('monthly-usd-creditor').value) || 0;
            const usdSurplus = usdDebtor - usdCreditor;
            monthlyData.usd = { debtor: usdDebtor, creditor: usdCreditor, surplus: usdSurplus };

            const usdSurplusElement = document.getElementById('monthly-usd-surplus');
            if (usdSurplusElement) {
                usdSurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: $${formatNumber(usdSurplus)}`;
                usdSurplusElement.className = 'result-box ' + (usdSurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
            }

            const eurDebtor = parseFloat(document.getElementById('monthly-eur-debtor').value) || 0;
            const eurCreditor = parseFloat(document.getElementById('monthly-eur-creditor').value) || 0;
            const eurSurplus = eurDebtor - eurCreditor;
            monthlyData.eur = { debtor: eurDebtor, creditor: eurCreditor, surplus: eurSurplus };

            const eurSurplusElement = document.getElementById('monthly-eur-surplus');
            if (eurSurplusElement) {
                eurSurplusElement.textContent = `الفائض الشهري / Aylık Kar-Zarar: €${formatNumber(eurSurplus)}`;
                eurSurplusElement.className = 'result-box ' + (eurSurplus >= 0 ? 'monthly-positive' : 'monthly-negative');
            }

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
                    external: { usd: 0, eur: 0 }
                };

                updateAutoProfitsDisplay();
                return;
            }

            let totalSwiftUSD = 0, totalSwiftEUR = 0;
            let totalHavanaUSD = 0, totalHavanaEUR = 0;
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
                let dateExternalUSD = 0, dateExternalEUR = 0;

                dateOperations.forEach(operation => {
                    dateSwiftUSD += operation.profits.swift.usd || 0;
                    dateSwiftEUR += operation.profits.swift.eur || 0;
                    dateHavanaUSD += operation.profits.havana.usd || 0;
                    dateHavanaEUR += operation.profits.havana.eur || 0;
                    dateExternalUSD += operation.profits.external?.usd || 0;
                    dateExternalEUR += operation.profits.external?.eur || 0;
                });

                totalSwiftUSD += dateSwiftUSD;
                totalSwiftEUR += dateSwiftEUR;
                totalHavanaUSD += dateHavanaUSD;
                totalHavanaEUR += dateHavanaEUR;
                totalExternalUSD += dateExternalUSD;
                totalExternalEUR += dateExternalEUR;

                dateTotalUSD = dateSwiftUSD + dateHavanaUSD + dateExternalUSD;
                dateTotalEUR = dateSwiftEUR + dateHavanaEUR + dateExternalEUR;
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
            const externalProfitUSD = parseFloat(document.getElementById('external-profit-usd').value) || 0;
            const externalProfitEUR = parseFloat(document.getElementById('external-profit-eur').value) || 0;

            const profitOperation = {
                date: today,
                timestamp: new Date().getTime(),
                profits: {
                    swift: { usd: swiftProfitUSD, eur: swiftProfitEUR },
                    havana: { usd: havanaProfitUSD, eur: havanaProfitEUR },
                    external: { usd: externalProfitUSD, eur: externalProfitEUR }
                }
            };

            dailyProfitOperations.push(profitOperation);
            localStorage.setItem('alanhar_daily_profit_operations', JSON.stringify(dailyProfitOperations));
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
            updateMonthlyExpenses();

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
            document.getElementById('compact-external-usd').textContent = `$${formatNumber(monthlyData.autoProfits.external.usd)}`;
            document.getElementById('compact-external-eur').textContent = `€${formatNumber(monthlyData.autoProfits.external.eur)}`;

            updateCompactExpenses();

            const now = new Date();
            document.getElementById('compact-creation-date').textContent = formatDate(now);
            document.getElementById('compact-creation-date-tr').textContent = formatDate(now);
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

                <button class="btn btn-reset remove-monthly-expense-btn" style="padding: 8px 15px;" data-id="${monthlyExpenseCounter}">
                    <i class="fas fa-trash"></i> حذف / Sil
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

            // حساب الصلج
            document.getElementById('report-saljog-amount').textContent = `$${formatNumber(appData.saljog.amount)}`;
            document.getElementById('report-saljog-expense').textContent = `$${formatNumber(appData.saljog.expense)}`;
            document.getElementById('report-saljog-profit').textContent = `$${formatNumber(appData.saljog.profit)}`;
            document.getElementById('report-saljog-total').textContent = `$${formatNumber(appData.saljog.total)}`;

            // الملخص
            document.getElementById('report-display-usd-surplus').textContent = `$${formatNumber(appData.usd.surplus)}`;
            document.getElementById('report-display-saljog-total').textContent = `$${formatNumber(appData.saljog.total)}`;
            document.getElementById('report-real-surplus').textContent = `$${formatNumber(appData.realSurplus)}`;

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

        function resetData() {
            if (confirm("هل تريد مسح جميع بيانات اليوم؟ / Bugünün tüm verilerini temizlemek istiyor musunuz?")) {
                const inputs = [
                    'usd-debtor', 'usd-creditor',
                    'eur-debtor', 'eur-creditor',
                    'try-debtor', 'try-creditor',
                    'saljog-amount', 'saljog-expense', 'saljog-profit'
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

        window.viewRecord = viewRecord;
        window.deleteRecord = deleteRecord;
    </script>
</body>
</html>
