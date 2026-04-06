<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>TAREK Tickets - نظام إدارة التذاكر الذكي</title>
    <style>
        :root {
            /* نظام ألوان جديد عصري */
            --primary: #7C3AED;
            --primary-light: #8B5CF6;
            --primary-dark: #6D28D9;
            --secondary: #10B981;
            --secondary-light: #34D399;
            --secondary-dark: #059669;
            --accent: #F59E0B;
            --accent-light: #FBBF24;
            --accent-dark: #D97706;
            --danger: #EF4444;
            --danger-light: #F87171;
            --danger-dark: #DC2626;
            --warning: #F97316;
            --success: #10B981;
            --info: #3B82F6;
            
            /* تدرجات رمادية */
            --gray-50: #F9FAFB;
            --gray-100: #F3F4F6;
            --gray-200: #E5E7EB;
            --gray-300: #D1D5DB;
            --gray-400: #9CA3AF;
            --gray-500: #6B7280;
            --gray-600: #4B5563;
            --gray-700: #374151;
            --gray-800: #1F2937;
            --gray-900: #111827;
            
            /* تدرجات داكنة */
            --dark-1: #1A1A2E;
            --dark-2: #16213E;
            --dark-3: #0F3460;
            
            /* ألوان العملات */
            --lyd: #059669;
            --eur: #2563EB;
            --usd: #DC2626;
            
            /* ظلال متطورة */
            --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            --shadow-md: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
            --shadow-xl: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            
            /* زوايا دائرية */
            --radius-sm: 8px;
            --radius: 12px;
            --radius-md: 16px;
            --radius-lg: 20px;
            --radius-xl: 24px;
            --radius-full: 9999px;
            
            /* تأثيرات الحركة */
            --transition-fast: 150ms cubic-bezier(0.4, 0, 0.2, 1);
            --transition: 300ms cubic-bezier(0.4, 0, 0.2, 1);
            --transition-slow: 500ms cubic-bezier(0.4, 0, 0.2, 1);
            
            /* تدرجات لونية */
            --gradient-primary: linear-gradient(135deg, var(--primary) 0%, var(--primary-light) 100%);
            --gradient-secondary: linear-gradient(135deg, var(--secondary) 0%, var(--secondary-light) 100%);
            --gradient-accent: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
            --gradient-danger: linear-gradient(135deg, var(--danger) 0%, var(--danger-light) 100%);
            --gradient-dark: linear-gradient(135deg, var(--dark-1) 0%, var(--dark-2) 100%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', 'Tajawal', sans-serif;
        }

        body {
            background: var(--gray-50);
            color: var(--gray-800);
            line-height: 1.6;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        /* خلفية متطورة */
        .background-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background: 
                radial-gradient(circle at 20% 80%, rgba(124, 58, 237, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(16, 185, 129, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(245, 158, 11, 0.05) 0%, transparent 50%);
        }

        .background-pattern {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.03;
            background-image: 
                radial-gradient(var(--primary) 1px, transparent 1px),
                radial-gradient(var(--secondary) 1px, transparent 1px);
            background-size: 40px 40px;
            background-position: 0 0, 20px 20px;
        }

        /* ترويسة جديدة */
        .header {
            background: var(--gradient-dark);
            color: white;
            padding: 1.5rem 2rem;
            position: relative;
            overflow: hidden;
            box-shadow: var(--shadow-xl);
            border-bottom: 4px solid var(--primary);
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.1) 50%, transparent 70%);
            transform: translateX(100%);
            animation: shine 3s infinite;
        }

        @keyframes shine {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }

        .header-content {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 2rem;
        }

        .logo-section {
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .logo {
            width: 60px;
            height: 60px;
            background: var(--gradient-primary);
            border-radius: var(--radius-lg);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.8rem;
            box-shadow: var(--shadow-lg);
            position: relative;
            overflow: hidden;
        }

        .logo::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(transparent, rgba(255,255,255,0.1), transparent);
            transform: rotate(45deg);
            animation: logo-shine 6s infinite linear;
        }

        @keyframes logo-shine {
            0% { transform: rotate(45deg) translateX(-100%); }
            100% { transform: rotate(45deg) translateX(100%); }
        }

        .logo-text h1 {
            font-size: 2rem;
            font-weight: 800;
            margin-bottom: 0.25rem;
            background: linear-gradient(135deg, white, var(--gray-200));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .logo-text p {
            color: var(--gray-300);
            font-size: 0.9rem;
        }

        .header-stats {
            display: flex;
            gap: 1.5rem;
        }

        .stat-item {
            text-align: center;
            background: rgba(255,255,255,0.1);
            padding: 0.75rem 1.5rem;
            border-radius: var(--radius-md);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.1);
            transition: var(--transition);
        }

        .stat-item:hover {
            background: rgba(255,255,255,0.15);
            transform: translateY(-2px);
        }

        .stat-number {
            font-size: 1.5rem;
            font-weight: 700;
            color: white;
        }

        .stat-label {
            font-size: 0.8rem;
            color: var(--gray-300);
        }

        /* تنقل جديد */
        .nav-container {
            background: white;
            border-bottom: 1px solid var(--gray-200);
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            gap: 0.5rem;
            position: relative;
        }

        .nav-tab {
            padding: 1rem 2rem;
            background: transparent;
            border: none;
            color: var(--gray-600);
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            position: relative;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .nav-tab.active {
            color: var(--primary);
            background: var(--gray-50);
        }

        .nav-tab i {
            font-size: 1.2rem;
        }

        /* المحتوى الرئيسي */
        .main-content {
            max-width: 1400px;
            margin: 2rem auto;
            padding: 0 2rem;
        }

        .tab-content {
            display: none;
            animation: fadeIn 0.5s ease-out;
        }

        .tab-content.active {
            display: block;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* بطاقات جديدة */
        .card {
            background: white;
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow);
            border: 1px solid var(--gray-200);
            overflow: hidden;
            transition: var(--transition);
            margin-bottom: 2rem;
        }

        .card:hover {
            box-shadow: var(--shadow-lg);
            transform: translateY(-4px);
        }

        .card-header {
            padding: 1.5rem;
            border-bottom: 1px solid var(--gray-200);
            background: linear-gradient(to right, var(--gray-50), white);
        }

        .card-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--gray-900);
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .card-title i {
            color: var(--primary);
        }

        .card-body {
            padding: 1.5rem;
        }

        /* نموذج جديد */
        .form-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .form-label {
            font-weight: 600;
            color: var(--gray-700);
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .form-label i {
            color: var(--primary);
        }

        .form-input, .form-select, .form-textarea {
            padding: 0.75rem 1rem;
            border: 2px solid var(--gray-300);
            border-radius: var(--radius);
            font-size: 1rem;
            transition: var(--transition);
            background: white;
            color: var(--gray-800);
        }

        .form-input:focus, .form-select:focus, .form-textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(124, 58, 237, 0.1);
        }

        .form-input::placeholder, .form-textarea::placeholder {
            color: var(--gray-400);
        }

        /* أزرار جديدة */
        .btn {
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: var(--radius);
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transform: translateX(-100%);
            transition: transform 0.6s;
        }

        .btn:hover::before {
            transform: translateX(100%);
        }

        .btn-primary {
            background: var(--gradient-primary);
            color: white;
        }

        .btn-primary:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
            box-shadow: var(--shadow-md);
        }

        .btn-success {
            background: var(--gradient-secondary);
            color: white;
        }

        .btn-success:hover {
            background: var(--secondary-dark);
            transform: translateY(-2px);
            box-shadow: var(--shadow-md);
        }

        .btn-warning {
            background: var(--gradient-accent);
            color: white;
        }

        .btn-warning:hover {
            background: var(--accent-dark);
            transform: translateY(-2px);
            box-shadow: var(--shadow-md);
        }

        .btn-danger {
            background: var(--gradient-danger);
            color: white;
        }

        .btn-danger:hover {
            background: var(--danger-dark);
            transform: translateY(-2px);
            box-shadow: var(--shadow-md);
        }

        .btn-outline {
            background: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }

        .btn-outline:hover {
            background: var(--primary);
            color: white;
        }

        /* بطاقات الشركات */
        .company-card {
            background: white;
            border-radius: var(--radius-lg);
            padding: 1.5rem;
            border: 1px solid var(--gray-200);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .company-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 4px;
            height: 100%;
            background: var(--gradient-primary);
            transition: width 0.3s;
        }

        .company-card:hover::before {
            width: 8px;
        }

        .company-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-lg);
        }

        .company-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 1rem;
        }

        .company-name {
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--gray-900);
        }

        .company-balance {
            font-size: 1.5rem;
            font-weight: 800;
            padding: 0.5rem 1rem;
            border-radius: var(--radius);
            background: var(--gray-100);
        }

        .company-balance.positive {
            color: var(--success);
            background: rgba(16, 185, 129, 0.1);
        }

        .company-balance.negative {
            color: var(--danger);
            background: rgba(239, 68, 68, 0.1);
        }

        /* أزرار العملية */
        .transaction-type-buttons {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin: 1.5rem 0;
        }

        .type-btn {
            padding: 1.5rem 1rem;
            border: 2px solid var(--gray-200);
            background: white;
            border-radius: var(--radius-lg);
            cursor: pointer;
            transition: var(--transition);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .type-btn::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background: var(--gradient-primary);
            opacity: 0;
            transition: var(--transition);
        }

        .type-btn.active {
            border-color: var(--primary);
            background: linear-gradient(135deg, rgba(124, 58, 237, 0.05), transparent);
            transform: translateY(-4px);
            box-shadow: var(--shadow-md);
        }

        .type-btn.active::before {
            opacity: 0.05;
        }

        .type-icon {
            font-size: 2rem;
            margin-bottom: 0.5rem;
            color: var(--gray-600);
            position: relative;
            z-index: 1;
        }

        .type-btn.active .type-icon {
            color: var(--primary);
        }

        .type-label {
            font-weight: 600;
            color: var(--gray-700);
            position: relative;
            z-index: 1;
        }

        .type-btn.active .type-label {
            color: var(--primary);
        }

        /* الجداول الجديدة */
        .table-container {
            background: white;
            border-radius: var(--radius-lg);
            overflow: hidden;
            box-shadow: var(--shadow);
            border: 1px solid var(--gray-200);
            margin-top: 1rem;
        }

        .table {
            width: 100%;
            border-collapse: collapse;
        }

        .table thead {
            background: linear-gradient(to right, var(--gray-50), var(--gray-100));
        }

        .table th {
            padding: 1rem;
            text-align: right;
            font-weight: 600;
            color: var(--gray-700);
            border-bottom: 2px solid var(--gray-200);
            white-space: nowrap;
        }

        .table td {
            padding: 1rem;
            border-bottom: 1px solid var(--gray-200);
            color: var(--gray-700);
        }

        .table tbody tr {
            transition: var(--transition);
        }

        .table tbody tr:hover {
            background: var(--gray-50);
        }

        /* شارات العمليات */
        .badge {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            border-radius: var(--radius-full);
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .badge-ticket {
            background: rgba(16, 185, 129, 0.1);
            color: var(--success);
        }

        .badge-fine {
            background: rgba(245, 158, 11, 0.1);
            color: var(--warning);
        }

        .badge-payment {
            background: rgba(59, 130, 246, 0.1);
            color: var(--info);
        }

        .badge-cancel {
            background: rgba(239, 68, 68, 0.1);
            color: var(--danger);
        }

        .badge-initial {
            background: rgba(124, 58, 237, 0.1);
            color: var(--primary);
        }

        /* شارات العملات */
        .currency-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.25rem;
            padding: 0.25rem 0.75rem;
            border-radius: var(--radius-full);
            font-size: 0.75rem;
            font-weight: 600;
            background: var(--gray-100);
            color: var(--gray-700);
        }

        .currency-badge.lyd {
            background: rgba(5, 150, 105, 0.1);
            color: var(--lyd);
        }

        .currency-badge.eur {
            background: rgba(37, 99, 235, 0.1);
            color: var(--eur);
        }

        .currency-badge.usd {
            background: rgba(220, 38, 38, 0.1);
            color: var(--usd);
        }

        /* أزرار الإجراءات */
        .action-buttons {
            display: flex;
            gap: 0.5rem;
        }

        .action-btn {
            padding: 0.5rem;
            border: none;
            border-radius: var(--radius);
            background: var(--gray-100);
            color: var(--gray-600);
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .action-btn:hover {
            background: var(--gray-200);
            color: var(--gray-800);
        }

        .action-btn.edit:hover {
            background: rgba(245, 158, 11, 0.1);
            color: var(--warning);
        }

        .action-btn.delete:hover {
            background: rgba(239, 68, 68, 0.1);
            color: var(--danger);
        }

        .action-btn.cancel:hover {
            background: rgba(124, 58, 237, 0.1);
            color: var(--primary);
        }

        /* فلاتر */
        .filter-container {
            background: white;
            padding: 1.5rem;
            border-radius: var(--radius-lg);
            margin-bottom: 2rem;
            box-shadow: var(--shadow);
            border: 1px solid var(--gray-200);
        }

        .filter-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
        }

        /* ملخص العمليات */
        .summary-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .summary-card {
            background: white;
            padding: 1.5rem;
            border-radius: var(--radius-lg);
            border: 1px solid var(--gray-200);
            position: relative;
            overflow: hidden;
            transition: var(--transition);
        }

        .summary-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 4px;
            background: var(--gradient-primary);
        }

        .summary-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-lg);
        }

        .summary-icon {
            width: 48px;
            height: 48px;
            border-radius: var(--radius);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1rem;
            font-size: 1.5rem;
        }

        .summary-icon.lyd {
            background: rgba(5, 150, 105, 0.1);
            color: var(--lyd);
        }

        .summary-icon.eur {
            background: rgba(37, 99, 235, 0.1);
            color: var(--eur);
        }

        .summary-icon.usd {
            background: rgba(220, 38, 38, 0.1);
            color: var(--usd);
        }

        .summary-title {
            font-size: 0.9rem;
            color: var(--gray-500);
            margin-bottom: 0.5rem;
        }

        .summary-value {
            font-size: 1.75rem;
            font-weight: 800;
            color: var(--gray-900);
        }

        /* تذييل الصفحة */
        .footer {
            margin-top: 4rem;
            padding: 2rem;
            background: var(--dark-1);
            color: white;
            text-align: center;
            border-top: 4px solid var(--primary);
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
        }

        .footer p {
            color: var(--gray-400);
            margin-top: 0.5rem;
        }

        /* نافذة منبثقة جديدة */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(5px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
        }

        .modal-overlay.active {
            opacity: 1;
            visibility: visible;
        }

        .modal {
            background: white;
            border-radius: var(--radius-xl);
            width: 90%;
            max-width: 500px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: var(--shadow-xl);
            transform: scale(0.95);
            transition: transform var(--transition);
        }

        .modal-overlay.active .modal {
            transform: scale(1);
        }

        .modal-header {
            padding: 1.5rem;
            border-bottom: 1px solid var(--gray-200);
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(to right, var(--gray-50), white);
        }

        .modal-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--gray-900);
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--gray-500);
            width: 40px;
            height: 40px;
            border-radius: var(--radius);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }

        .modal-close:hover {
            background: var(--gray-100);
            color: var(--danger);
        }

        .modal-body {
            padding: 1.5rem;
        }

        /* إشعارات */
        .notification {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: white;
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow-xl);
            padding: 1rem 1.5rem;
            display: flex;
            align-items: center;
            gap: 1rem;
            z-index: 1001;
            animation: slideDown 0.3s ease-out;
            border-right: 4px solid var(--primary);
            min-width: 300px;
            max-width: 90%;
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateX(-50%) translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(-50%) translateY(0);
            }
        }

        .notification.success {
            border-right-color: var(--success);
        }

        .notification.error {
            border-right-color: var(--danger);
        }

        .notification.warning {
            border-right-color: var(--warning);
        }

        .notification.info {
            border-right-color: var(--info);
        }

        /* تنسيق خاص للهواتف */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
                gap: 1rem;
            }

            .logo-section {
                flex-direction: column;
                text-align: center;
            }

            .header-stats {
                flex-wrap: wrap;
                justify-content: center;
            }

            .nav {
                flex-direction: column;
                padding: 0;
            }

            .nav-tab {
                padding: 1rem;
                justify-content: center;
            }

            .main-content {
                padding: 0 1rem;
            }

            .form-container {
                grid-template-columns: 1fr;
            }

            .transaction-type-buttons {
                grid-template-columns: 1fr;
            }

            .table {
                display: block;
                overflow-x: auto;
            }

            .filter-grid {
                grid-template-columns: 1fr;
            }

            .summary-grid {
                grid-template-columns: 1fr;
            }

            .action-buttons {
                flex-direction: column;
            }

            .btn {
                width: 100%;
            }
        }

        /* تحسينات للطابعة */
        @media print {
            .no-print {
                display: none !important;
            }

            body {
                background: white;
                color: black;
            }

            .card, .table-container {
                box-shadow: none;
                border: 1px solid #ddd;
            }
        }

        /* مؤشر التحميل */
        .loader {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 2px solid var(--gray-200);
            border-top-color: var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* رسائل التنبيه */
        .alert {
            padding: 1rem 1.5rem;
            border-radius: var(--radius);
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 1rem;
            animation: slideIn 0.3s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .alert-success {
            background: rgba(16, 185, 129, 0.1);
            border: 1px solid rgba(16, 185, 129, 0.2);
            color: var(--success);
        }

        .alert-danger {
            background: rgba(239, 68, 68, 0.1);
            border: 1px solid rgba(239, 68, 68, 0.2);
            color: var(--danger);
        }

        .alert-warning {
            background: rgba(245, 158, 11, 0.1);
            border: 1px solid rgba(245, 158, 11, 0.2);
            color: var(--warning);
        }

        .alert-info {
            background: rgba(59, 130, 246, 0.1);
            border: 1px solid rgba(59, 130, 246, 0.2);
            color: var(--info);
        }

        /* تصميم شريط التمرير */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--gray-100);
            border-radius: var(--radius);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--gray-400);
            border-radius: var(--radius);
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--gray-500);
        }

        /* حالة فارغة */
        .empty-state {
            text-align: center;
            padding: 4rem 2rem;
            color: var(--gray-500);
        }

        .empty-state i {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: var(--gray-300);
        }

        /* ميزات متقدمة */
        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 30px;
        }

        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .toggle-slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: var(--gray-300);
            transition: .4s;
            border-radius: 34px;
        }

        .toggle-slider:before {
            position: absolute;
            content: "";
            height: 22px;
            width: 22px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }

        input:checked + .toggle-slider {
            background-color: var(--primary);
        }

        input:checked + .toggle-slider:before {
            transform: translateX(30px);
        }

        /* مؤشر النشاط */
        .active-indicator {
            display: inline-block;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: var(--success);
            margin-right: 8px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
</head>
<body>
    <!-- خلفية متطورة -->
    <div class="background-overlay"></div>
    <div class="background-pattern"></div>

    <!-- الترويسة الجديدة -->
    <header class="header no-print">
        <div class="header-content">
            <div class="logo-section">
                <div class="logo">
                    <i class="fas fa-plane-departure"></i>
                </div>
                <div class="logo-text">
                    <h1>TAREK Tickets</h1>
                    <p>نظام إدارة التذاكر الذكي</p>
                </div>
            </div>
            <div class="header-stats">
                <div class="stat-item">
                    <div class="stat-number" id="total-companies">0</div>
                    <div class="stat-label">شركة</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number" id="total-transactions">0</div>
                    <div class="stat-label">عملية</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number" id="total-balance">0 د</div>
                    <div class="stat-label">إجمالي الرصيد</div>
                </div>
            </div>
        </div>
    </header>

    <!-- شريط التنقل الجديد -->
    <nav class="nav-container no-print">
        <div class="nav">
            <button class="nav-tab active" data-tab="add">
                <i class="fas fa-plus-circle"></i>
                إضافة عملية
            </button>
            <button class="nav-tab" data-tab="report">
                <i class="fas fa-chart-line"></i>
                كشف الحساب
            </button>
            <button class="nav-tab" data-tab="manage">
                <i class="fas fa-cogs"></i>
                إدارة العمليات
            </button>
        </div>
    </nav>

    <!-- المحتوى الرئيسي -->
    <main class="main-content">
        <!-- تبويب إضافة عملية -->
        <div class="tab-content active" id="add-tab">
            <div class="card">
                <div class="card-header">
                    <h2 class="card-title">
                        <i class="fas fa-plus-circle"></i>
                        إضافة عملية جديدة
                    </h2>
                </div>
                <div class="card-body">
                    <div class="form-container">
                        <!-- إدارة الشركات -->
                        <div class="form-section">
                            <div class="form-group">
                                <button class="btn btn-primary" id="open-add-company-modal">
                                    <i class="fas fa-plus"></i>
                                    إضافة شركة جديدة
                                </button>
                            </div>
                            
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-building"></i>
                                    اختر الشركة
                                </label>
                                <select class="form-select" id="company">
                                    <option value="">-- اختر الشركة --</option>
                                </select>
                            </div>

                            <div id="company-info" class="company-card" style="display: none;">
                                <div class="company-header">
                                    <div class="company-name" id="current-company">--</div>
                                    <div class="company-balance" id="company-balance">0 دينار</div>
                                </div>
                                <p style="color: var(--gray-500); margin-top: 0.5rem; font-size: 0.9rem;">الرصيد الحالي</p>
                            </div>

                            <!-- نوع العملية -->
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-tag"></i>
                                    نوع العملية
                                </label>
                                <div class="transaction-type-buttons">
                                    <div class="type-btn active" data-type="ticket">
                                        <i class="fas fa-ticket-alt type-icon"></i>
                                        <div class="type-label">تذكرة</div>
                                    </div>
                                    <div class="type-btn" data-type="fine">
                                        <i class="fas fa-exclamation-triangle type-icon"></i>
                                        <div class="type-label">غرامة</div>
                                    </div>
                                    <div class="type-btn" data-type="payment">
                                        <i class="fas fa-money-bill-wave type-icon"></i>
                                        <div class="type-label">تسليم دفعة</div>
                                    </div>
                                </div>
                                <input type="hidden" id="transaction-type" value="ticket">
                            </div>
                        </div>

                        <!-- تفاصيل العملية -->
                        <div class="form-section">
                            <!-- العملة -->
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-coins"></i>
                                    العملة
                                </label>
                                <select class="form-select" id="currency">
                                    <option value="LYD">دينار ليبي (LYD)</option>
                                    <option value="EUR">يورو (EUR)</option>
                                    <option value="USD">دولار أمريكي (USD)</option>
                                </select>
                            </div>

                            <!-- حقول التذكرة والغرامة -->
                            <div id="ticket-fine-fields">
                                <div class="form-group">
                                    <label class="form-label">
                                        <i class="fas fa-user"></i>
                                        اسم المسافر
                                    </label>
                                    <input type="text" class="form-input" id="passenger-name" placeholder="أدخل اسم المسافر">
                                </div>
                                
                                <div class="form-group">
                                    <label class="form-label">
                                        <i class="fas fa-file-alt"></i>
                                        رقم المستند
                                    </label>
                                    <input type="text" class="form-input" id="document-number" placeholder="أدخل رقم المستند">
                                </div>
                                
                                <div class="form-group">
                                    <label class="form-label">
                                        <i class="fas fa-map-marker-alt"></i>
                                        الوجهة
                                    </label>
                                    <select class="form-select" id="destination">
                                        <option value="TIP - IST">(TIP - IST)</option>
                                        <option value="other">وجهة أخرى</option>
                                    </select>
                                    <input type="text" class="form-input mt-2" id="other-destination" placeholder="أدخل الوجهة (مثال: TIP - ROM)" style="display: none;">
                                </div>
                                
                                <div class="form-group">
                                    <label class="form-label">
                                        <i class="fas fa-plane"></i>
                                        نوع الرحلة
                                    </label>
                                    <select class="form-select" id="trip-type">
                                        <option value="ذهاب">ذهاب فقط</option>
                                        <option value="ذهاب وعودة">ذهاب وعودة</option>
                                    </select>
                                </div>
                            </div>

                            <!-- حقول الغرامة فقط -->
                            <div id="fine-only-fields" style="display: none;">
                                <div class="form-group">
                                    <label class="form-label">
                                        <i class="fas fa-exclamation-circle"></i>
                                        سبب الغرامة
                                    </label>
                                    <textarea class="form-textarea" id="fine-reason" placeholder="أدخل سبب الغرامة" rows="2"></textarea>
                                </div>
                            </div>

                            <!-- حقول التسليم -->
                            <div id="payment-fields" style="display: none;">
                                <div class="form-group">
                                    <label class="form-label">
                                        <i class="fas fa-receipt"></i>
                                        وصف الدفعة
                                    </label>
                                    <input type="text" class="form-input" id="payment-description" placeholder="مثال: تسليم دفعة شهر أكتوبر">
                                </div>
                            </div>

                            <!-- المبلغ والتاريخ -->
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-money-bill-wave"></i>
                                    المبلغ
                                </label>
                                <input type="number" class="form-input" id="amount" placeholder="أدخل المبلغ" min="0" step="0.001">
                                <small id="currency-symbol" style="color: var(--gray-500); margin-top: 0.25rem; display: block;">المبلغ بالعملة المختارة</small>
                            </div>

                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-calendar-alt"></i>
                                    تاريخ العملية
                                </label>
                                <input type="date" class="form-input" id="date" value="">
                            </div>

                            <div class="form-group" id="notes-group">
                                <label class="form-label">
                                    <i class="fas fa-sticky-note"></i>
                                    ملاحظات إضافية
                                </label>
                                <input type="text" class="form-input" id="notes" placeholder="ملاحظات (اختياري)">
                            </div>

                            <!-- أزرار الحفظ -->
                            <div class="form-group" style="margin-top: 1.5rem;">
                                <button class="btn btn-success" id="add-transaction" style="width: 100%;">
                                    <i class="fas fa-plus"></i>
                                    إضافة العملية
                                </button>
                                <button class="btn btn-outline mt-2" id="reset-form" style="width: 100%;">
                                    <i class="fas fa-redo"></i>
                                    مسح النموذج
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- قائمة الشركات -->
            <div class="card">
                <div class="card-header">
                    <h2 class="card-title">
                        <i class="fas fa-building"></i>
                        قائمة الشركات
                    </h2>
                </div>
                <div class="card-body">
                    <div id="company-list">
                        <div class="empty-state" id="no-companies">
                            <i class="fas fa-building"></i>
                            <p>لا توجد شركات مضافة بعد</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- تبويب كشف الحساب -->
        <div class="tab-content" id="report-tab">
            <div class="card">
                <div class="card-header">
                    <h2 class="card-title">
                        <i class="fas fa-chart-line"></i>
                        كشف الحساب
                    </h2>
                </div>
                <div class="card-body">
                    <div class="filter-container">
                        <div class="filter-grid">
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-building"></i>
                                    اختر الشركة
                                </label>
                                <select class="form-select" id="report-company">
                                    <option value="">-- اختر الشركة --</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-filter"></i>
                                    تصفية حسب العملة
                                </label>
                                <select class="form-select" id="report-currency-filter">
                                    <option value="all">جميع العملات</option>
                                    <option value="LYD">دينار ليبي</option>
                                    <option value="EUR">يورو</option>
                                    <option value="USD">دولار أمريكي</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <button class="btn btn-primary" id="print-report" style="margin-top: 1.75rem;">
                                    <i class="fas fa-print"></i>
                                    طباعة الكشف
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="table-container">
                        <table class="table" id="transactions-table">
                            <thead>
                                <tr>
                                    <th>#</th>
                                    <th>التاريخ</th>
                                    <th>العملة</th>
                                    <th>النوع</th>
                                    <th>المسافر</th>
                                    <th>المستند</th>
                                    <th>الوجهة</th>
                                    <th>المبلغ</th>
                                    <th>الرصيد</th>
                                </tr>
                            </thead>
                            <tbody id="transactions-body">
                                <!-- البيانات ستضاف هنا -->
                            </tbody>
                        </table>
                    </div>

                    <div id="no-data" class="empty-state" style="display: none;">
                        <i class="fas fa-chart-bar"></i>
                        <p>لا توجد عمليات مسجلة بعد. قم بإضافة عمليات جديدة باستخدام النموذج.</p>
                    </div>

                    <!-- ملخص العملات -->
                    <div class="summary-grid" id="currency-summaries">
                        <!-- سيتم تعبئته بواسطة الجافاسكريبت -->
                    </div>
                </div>
            </div>
        </div>

        <!-- تبويب إدارة العمليات -->
        <div class="tab-content" id="manage-tab">
            <div class="card">
                <div class="card-header">
                    <h2 class="card-title">
                        <i class="fas fa-cogs"></i>
                        إدارة العمليات
                    </h2>
                </div>
                <div class="card-body">
                    <div class="filter-container">
                        <div class="filter-grid">
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-building"></i>
                                    تصفية حسب الشركة
                                </label>
                                <select class="form-select" id="filter-company">
                                    <option value="">جميع الشركات</option>
                                </select>
                            </div>
                            
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-tag"></i>
                                    تصفية حسب النوع
                                </label>
                                <select class="form-select" id="filter-type">
                                    <option value="">جميع الأنواع</option>
                                    <option value="ticket">تذكرة</option>
                                    <option value="fine">غرامة</option>
                                    <option value="payment">تسليم دفعة</option>
                                </select>
                            </div>
                            
                            <div class="form-group">
                                <label class="form-label">
                                    <i class="fas fa-coins"></i>
                                    تصفية حسب العملة
                                </label>
                                <select class="form-select" id="filter-currency">
                                    <option value="">جميع العملات</option>
                                    <option value="LYD">دينار ليبي</option>
                                    <option value="EUR">يورو</option>
                                    <option value="USD">دولار أمريكي</option>
                                </select>
                            </div>
                            
                            <div class="form-group">
                                <button class="btn btn-outline" id="reset-filters" style="margin-top: 1.75rem;">
                                    <i class="fas fa-filter"></i>
                                    إعادة التعيين
                                </button>
                            </div>
                        </div>
                    </div>

                    <!-- نموذج التعديل -->
                    <div id="edit-form-container" class="card" style="display: none; margin-bottom: 1rem;">
                        <div class="card-header">
                            <h3 class="card-title">
                                <i class="fas fa-edit"></i>
                                تعديل العملية
                            </h3>
                            <button class="modal-close" id="cancel-edit">&times;</button>
                        </div>
                        <div class="card-body">
                            <div class="form-container">
                                <div class="form-section">
                                    <div class="form-group">
                                        <label class="form-label">نوع العملية</label>
                                        <select class="form-select" id="edit-transaction-type">
                                            <option value="ticket">تذكرة</option>
                                            <option value="fine">غرامة</option>
                                            <option value="payment">تسليم دفعة</option>
                                        </select>
                                    </div>
                                    
                                    <div class="form-group">
                                        <label class="form-label">العملة</label>
                                        <select class="form-select" id="edit-currency">
                                            <option value="LYD">دينار ليبي (LYD)</option>
                                            <option value="EUR">يورو (EUR)</option>
                                            <option value="USD">دولار أمريكي (USD)</option>
                                        </select>
                                    </div>
                                    
                                    <div id="edit-ticket-fields">
                                        <div class="form-group">
                                            <label class="form-label">اسم المسافر</label>
                                            <input type="text" class="form-input" id="edit-passenger-name">
                                        </div>
                                        
                                        <div class="form-group">
                                            <label class="form-label">رقم المستند</label>
                                            <input type="text" class="form-input" id="edit-document-number">
                                        </div>
                                    </div>
                                    
                                    <div id="edit-fine-only-fields" style="display: none;">
                                        <div class="form-group">
                                            <label class="form-label">سبب الغرامة</label>
                                            <textarea class="form-textarea" id="edit-fine-reason" rows="2"></textarea>
                                        </div>
                                    </div>
                                </div>
                                
                                <div class="form-section">
                                    <div id="edit-payment-fields" style="display: none;">
                                        <div class="form-group">
                                            <label class="form-label">وصف الدفعة</label>
                                            <input type="text" class="form-input" id="edit-payment-description">
                                        </div>
                                    </div>
                                    
                                    <div class="form-group">
                                        <label class="form-label">المبلغ</label>
                                        <input type="number" class="form-input" id="edit-amount" min="0" step="0.001">
                                    </div>
                                    
                                    <div class="form-group">
                                        <label class="form-label">تاريخ العملية</label>
                                        <input type="date" class="form-input" id="edit-date">
                                    </div>
                                    
                                    <div class="form-group">
                                        <label class="form-label">ملاحظات إضافية</label>
                                        <input type="text" class="form-input" id="edit-notes">
                                    </div>
                                    
                                    <div class="form-group" style="margin-top: 1.5rem;">
                                        <button class="btn btn-success" id="save-edit" style="width: 100%;">
                                            <i class="fas fa-save"></i>
                                            حفظ التعديلات
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- تأكيد الحذف -->
                    <div id="delete-confirm-container" class="card" style="display: none; margin-bottom: 1rem; border-color: var(--danger);">
                        <div class="card-header" style="background: rgba(239, 68, 68, 0.05);">
                            <h3 class="card-title" style="color: var(--danger);">
                                <i class="fas fa-exclamation-triangle"></i>
                                تأكيد الحذف
                            </h3>
                        </div>
                        <div class="card-body">
                            <p>هل أنت متأكد من حذف هذه العملية؟ هذا الإجراء لا يمكن التراجع عنه.</p>
                            <div class="form-group" style="margin-top: 1rem;">
                                <div style="display: flex; gap: 1rem;">
                                    <button class="btn btn-outline" id="cancel-delete" style="flex: 1;">
                                        <i class="fas fa-times"></i>
                                        إلغاء
                                    </button>
                                    <button class="btn btn-danger" id="confirm-delete" style="flex: 1;">
                                        <i class="fas fa-trash"></i>
                                        نعم، احذف
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- جدول العمليات -->
                    <div class="table-container">
                        <table class="table" id="manage-transactions-table">
                            <thead>
                                <tr>
                                    <th>#</th>
                                    <th>التاريخ</th>
                                    <th>الشركة</th>
                                    <th>العملة</th>
                                    <th>النوع</th>
                                    <th>المسافر</th>
                                    <th>المبلغ</th>
                                    <th>الإجراءات</th>
                                </tr>
                            </thead>
                            <tbody id="manage-transactions-body">
                                <!-- البيانات ستضاف هنا -->
                            </tbody>
                        </table>
                    </div>

                    <div id="no-transactions" class="empty-state" style="display: none;">
                        <i class="fas fa-cogs"></i>
                        <p>لا توجد عمليات مسجلة بعد. قم بإضافة عمليات جديدة باستخدام تبويب "إضافة عملية".</p>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- تذييل الصفحة -->
    <footer class="footer no-print">
        <div class="footer-content">
            <p>TAREK Tickets - نظام إدارة التذاكر الذكي</p>
            <p>جميع الحقوق محفوظة &copy; 2024</p>
        </div>
    </footer>

    <!-- نافذة إضافة شركة جديدة -->
    <div id="add-company-modal" class="modal-overlay">
        <div class="modal">
            <div class="modal-header">
                <h3 class="modal-title">
                    <i class="fas fa-building"></i>
                    إضافة شركة جديدة
                </h3>
                <button class="modal-close" id="close-add-company-modal">&times;</button>
            </div>
            <div class="modal-body">
                <div class="form-group">
                    <label class="form-label">اسم الشركة</label>
                    <input type="text" class="form-input" id="new-company-name" placeholder="أدخل اسم الشركة">
                </div>
                
                <div class="form-group">
                    <label class="form-label">نوع الرصيد الافتتاحي</label>
                    <div style="display: flex; gap: 1rem; margin-top: 0.5rem;">
                        <div class="type-btn" style="flex: 1;" data-balance-type="credit">
                            <i class="fas fa-hand-holding-usd type-icon"></i>
                            <div class="type-label">دائن</div>
                            <small style="color: var(--gray-500); margin-top: 0.25rem;">الشركة تحتاج منك</small>
                        </div>
                        <div class="type-btn" style="flex: 1;" data-balance-type="debit">
                            <i class="fas fa-money-bill-wave type-icon"></i>
                            <div class="type-label">مدين</div>
                            <small style="color: var(--gray-500); margin-top: 0.25rem;">أنت تحتاج من الشركة</small>
                        </div>
                    </div>
                    <input type="hidden" id="balance-type" value="credit">
                </div>
                
                <div class="form-group">
                    <label class="form-label">المبلغ (دينار)</label>
                    <input type="number" class="form-input" id="initial-balance" placeholder="أدخل المبلغ" min="0" step="0.001">
                </div>
                
                <div class="form-group" style="margin-top: 1.5rem;">
                    <button class="btn btn-success" id="save-new-company" style="width: 100%;">
                        <i class="fas fa-save"></i>
                        حفظ الشركة
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- نافذة تأكيد الإلغاء -->
    <div id="cancel-transaction-modal" class="modal-overlay">
        <div class="modal">
            <div class="modal-header">
                <h3 class="modal-title">
                    <i class="fas fa-exchange-alt"></i>
                    تأكيد إلغاء العملية
                </h3>
                <button class="modal-close" id="close-cancel-modal">&times;</button>
            </div>
            <div class="modal-body">
                <div id="cancel-details"></div>
                <div class="form-group" style="margin-top: 1.5rem;">
                    <div style="display: flex; gap: 1rem;">
                        <button class="btn btn-outline" id="cancel-cancel" style="flex: 1;">
                            <i class="fas fa-times"></i>
                            إلغاء
                        </button>
                        <button class="btn btn-warning" id="confirm-cancel" style="flex: 1;">
                            <i class="fas fa-exchange-alt"></i>
                            نعم، ألغ العملية
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- كود الجافاسكريبت الكامل -->
    <script>
        // بيانات التطبيق - نفسها تماماً
        let transactions = [];
        let companies = {};
        
        // حالة التطبيق
        let balanceType = 'credit';
        let initialBalance = 0;
        let currentEditTransactionId = null;
        let currentDeleteTransactionId = null;
        let currentCancelTransactionId = null;
        
        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            loadData();
            initializeApp();
            setupEventListeners();
            updateStats();
        });

        // تحميل البيانات
        function loadData() {
            const savedTransactions = localStorage.getItem('ticketSystem_transactions_multi');
            const savedCompanies = localStorage.getItem('ticketSystem_companies_multi');
            
            if (savedTransactions) {
                try {
                    transactions = JSON.parse(savedTransactions);
                } catch (e) {
                    console.error('Error loading transactions:', e);
                    transactions = [];
                }
            }
            
            if (savedCompanies) {
                try {
                    companies = JSON.parse(savedCompanies);
                } catch (e) {
                    console.error('Error loading companies:', e);
                    companies = {};
                }
            }
            
            // إذا لم تكن هناك بيانات، أضف بيانات تجريبية
            if (transactions.length === 0 && Object.keys(companies).length === 0) {
                initializeSampleData();
            }
        }

        // حفظ البيانات
        function saveData() {
            localStorage.setItem('ticketSystem_transactions_multi', JSON.stringify(transactions));
            localStorage.setItem('ticketSystem_companies_multi', JSON.stringify(companies));
        }

        // تهيئة البيانات التجريبية
        function initializeSampleData() {
            companies = {
                "شركة الطيران الوطنية": {
                    LYD: 1500,
                    EUR: 500,
                    USD: 0,
                    openingBalance: 1500
                },
                "وكالة سفر العالمية": {
                    LYD: -800,
                    EUR: 200,
                    USD: 300,
                    openingBalance: -800
                },
                "مكتب تذاكر المدينة": {
                    LYD: 2500,
                    EUR: 0,
                    USD: 0,
                    openingBalance: 2500
                }
            };
            
            transactions = [
                {
                    id: generateId(),
                    date: new Date().toISOString().split('T')[0],
                    type: "ticket",
                    company: "شركة الطيران الوطنية",
                    passengerName: "أحمد محمد",
                    documentNumber: "TKT-001",
                    destination: "TIP - IST",
                    tripType: "ذهاب",
                    amount: 350,
                    currency: "LYD",
                    notes: "تذكرة عادية"
                },
                {
                    id: generateId(),
                    date: new Date().toISOString().split('T')[0],
                    type: "payment",
                    company: "وكالة سفر العالمية",
                    description: "تسليم دفعة شهر أكتوبر",
                    amount: 200,
                    currency: "EUR"
                },
                {
                    id: generateId(),
                    date: new Date().toISOString().split('T')[0],
                    type: "fine",
                    company: "مكتب تذاكر المدينة",
                    passengerName: "محمد خالد",
                    documentNumber: "FNE-001",
                    destination: "TIP - IST",
                    tripType: "ذهاب",
                    reason: "تأخير في الحضور",
                    amount: 50,
                    currency: "USD"
                }
            ];
            
            saveData();
        }

        // تهيئة التطبيق
        function initializeApp() {
            // تعيين تاريخ اليوم
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('date').value = today;
            
            // تحديث واجهات الاختيار
            updateCompanySelect();
            updateReportCompanySelect();
            updateFilterCompanySelect();
            updateCompanyList();
            updateReport();
            updateManageTable();
            
            // تحديث رموز العملات
            updateCurrencySymbol();
        }

        // إعداد المستمعين للأحداث
        function setupEventListeners() {
            // التنقل بين التبويبات
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.addEventListener('click', () => {
                    const tabId = tab.dataset.tab;
                    
                    document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
                    tab.classList.add('active');
                    
                    document.querySelectorAll('.tab-content').forEach(content => {
                        content.classList.remove('active');
                        if (content.id === `${tabId}-tab`) {
                            content.classList.add('active');
                        }
                    });
                    
                    if (tabId === 'manage') updateManageTable();
                    if (tabId === 'report') updateReport();
                });
            });

            // اختيار نوع العملية
            document.querySelectorAll('.type-btn[data-type]').forEach(btn => {
                btn.addEventListener('click', () => {
                    document.querySelectorAll('.type-btn[data-type]').forEach(b => b.classList.remove('active'));
                    btn.classList.add('active');
                    const type = btn.dataset.type;
                    document.getElementById('transaction-type').value = type;
                    updateFormFields(type);
                });
            });

            // اختيار نوع الرصيد
            document.querySelectorAll('.type-btn[data-balance-type]').forEach(btn => {
                btn.addEventListener('click', () => {
                    document.querySelectorAll('.type-btn[data-balance-type]').forEach(b => b.classList.remove('active'));
                    btn.classList.add('active');
                    balanceType = btn.dataset.balanceType;
                    document.getElementById('balance-type').value = balanceType;
                });
            });

            // اختيار الشركة
            document.getElementById('company').addEventListener('change', function() {
                const company = this.value;
                updateCompanyInfo(company);
            });

            // العملة
            document.getElementById('currency').addEventListener('change', updateCurrencySymbol);

            // الوجهة
            document.getElementById('destination').addEventListener('change', function() {
                document.getElementById('other-destination').style.display = 
                    this.value === 'other' ? 'block' : 'none';
            });

            // الأزرار الرئيسية
            document.getElementById('add-transaction').addEventListener('click', addTransaction);
            document.getElementById('reset-form').addEventListener('click', resetForm);
            document.getElementById('open-add-company-modal').addEventListener('click', openAddCompanyModal);
            document.getElementById('close-add-company-modal').addEventListener('click', closeAddCompanyModal);
            document.getElementById('save-new-company').addEventListener('click', saveNewCompany);
            document.getElementById('print-report').addEventListener('click', printReport);
            
            // فلاتر التقرير
            document.getElementById('report-company').addEventListener('change', updateReport);
            document.getElementById('report-currency-filter').addEventListener('change', function() {
                filterReportByCurrency(this.value);
            });

            // فلاتر الإدارة
            document.getElementById('filter-company').addEventListener('change', updateManageTable);
            document.getElementById('filter-type').addEventListener('change', updateManageTable);
            document.getElementById('filter-currency').addEventListener('change', updateManageTable);
            document.getElementById('reset-filters').addEventListener('click', resetFilters);

            // التعديل
            document.getElementById('cancel-edit').addEventListener('click', cancelEdit);
            document.getElementById('save-edit').addEventListener('click', saveEdit);

            // الحذف
            document.getElementById('cancel-delete').addEventListener('click', cancelDelete);
            document.getElementById('confirm-delete').addEventListener('click', confirmDelete);

            // الإلغاء
            document.getElementById('close-cancel-modal').addEventListener('click', closeCancelModal);
            document.getElementById('cancel-cancel').addEventListener('click', closeCancelModal);
            document.getElementById('confirm-cancel').addEventListener('click', confirmCancel);

            // إغلاق بالنقر خارج النافذة
            document.querySelectorAll('.modal-overlay').forEach(modal => {
                modal.addEventListener('click', function(e) {
                    if (e.target === this) {
                        this.classList.remove('active');
                    }
                });
            });

            // إغلاق بمفتاح ESC
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape') {
                    document.querySelectorAll('.modal-overlay').forEach(modal => {
                        modal.classList.remove('active');
                    });
                }
            });
        }

        // تحديث الإحصائيات
        function updateStats() {
            document.getElementById('total-companies').textContent = Object.keys(companies).length;
            document.getElementById('total-transactions').textContent = transactions.length;
            
            let totalBalance = 0;
            Object.values(companies).forEach(company => {
                totalBalance += (company.LYD || 0);
            });
            
            document.getElementById('total-balance').textContent = totalBalance.toFixed(3) + ' د';
        }

        // تحديث حقول النموذج
        function updateFormFields(type) {
            const ticketFineFields = document.getElementById('ticket-fine-fields');
            const fineOnlyFields = document.getElementById('fine-only-fields');
            const paymentFields = document.getElementById('payment-fields');
            const notesGroup = document.getElementById('notes-group');
            
            ticketFineFields.style.display = type === 'payment' ? 'none' : 'block';
            fineOnlyFields.style.display = type === 'fine' ? 'block' : 'none';
            paymentFields.style.display = type === 'payment' ? 'block' : 'none';
            notesGroup.style.display = type === 'ticket' ? 'block' : 'none';
        }

        // تحديث رمز العملة
        function updateCurrencySymbol() {
            const currency = document.getElementById('currency').value;
            const symbols = {
                'LYD': 'دينار ليبي',
                'EUR': 'يورو',
                'USD': 'دولار أمريكي'
            };
            document.getElementById('currency-symbol').textContent = `المبلغ بالـ ${symbols[currency]}`;
        }

        // تحديث قائمة الشركات
        function updateCompanySelect() {
            const select = document.getElementById('company');
            const currentValue = select.value;
            
            select.innerHTML = '<option value="">-- اختر الشركة --</option>';
            Object.keys(companies).sort().forEach(company => {
                const option = document.createElement('option');
                option.value = company;
                option.textContent = company;
                select.appendChild(option);
            });
            
            if (currentValue && companies[currentValue]) {
                select.value = currentValue;
            }
        }

        // تحديث معلومات الشركة
        function updateCompanyInfo(company) {
            const companyInfo = document.getElementById('company-info');
            const companyName = document.getElementById('current-company');
            const companyBalance = document.getElementById('company-balance');
            
            if (company && companies[company]) {
                const balance = companies[company].LYD || 0;
                companyName.textContent = company;
                companyBalance.textContent = formatCurrency(Math.abs(balance), 'LYD') + 
                    (balance > 0 ? ' (دائن)' : balance < 0 ? ' (مدين)' : '');
                companyBalance.className = balance > 0 ? 'company-balance positive' : 
                    balance < 0 ? 'company-balance negative' : 'company-balance';
                companyInfo.style.display = 'block';
            } else {
                companyInfo.style.display = 'none';
            }
        }

        // تحديث قائمة الشركات في الواجهة
        function updateCompanyList() {
            const container = document.getElementById('company-list');
            const noCompanies = document.getElementById('no-companies');
            
            if (Object.keys(companies).length === 0) {
                noCompanies.style.display = 'block';
                container.innerHTML = '';
                return;
            }
            
            noCompanies.style.display = 'none';
            container.innerHTML = '';
            
            Object.keys(companies).sort().forEach(company => {
                const balance = companies[company].LYD || 0;
                const card = document.createElement('div');
                card.className = 'company-card';
                card.innerHTML = `
                    <div class="company-header">
                        <div class="company-name">${company}</div>
                        <div class="company-balance ${balance > 0 ? 'positive' : balance < 0 ? 'negative' : ''}">
                            ${formatCurrency(Math.abs(balance), 'LYD')} ${balance > 0 ? '(دائن)' : balance < 0 ? '(مدين)' : ''}
                        </div>
                    </div>
                    <div style="margin-top: 1rem;">
                        <button class="btn btn-danger btn-sm delete-company" data-company="${company}" style="width: 100%;">
                            <i class="fas fa-trash"></i> حذف الشركة
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
            
            // إضافة مستمعي الأحداث لحذف الشركات
            document.querySelectorAll('.delete-company').forEach(btn => {
                btn.addEventListener('click', function() {
                    const company = this.dataset.company;
                    if (confirm(`هل أنت متأكد من حذف شركة "${company}"؟ سيتم حذف جميع عملياتها أيضاً.`)) {
                        deleteCompany(company);
                    }
                });
            });
        }

        // حذف شركة
        function deleteCompany(companyName) {
            delete companies[companyName];
            transactions = transactions.filter(t => t.company !== companyName);
            
            saveData();
            updateCompanySelect();
            updateReportCompanySelect();
            updateFilterCompanySelect();
            updateCompanyList();
            updateReport();
            updateManageTable();
            updateStats();
            
            showNotification('تم حذف الشركة وعملياتها بنجاح', 'success');
        }

        // فتح نافذة إضافة شركة
        function openAddCompanyModal() {
            document.getElementById('add-company-modal').classList.add('active');
            document.getElementById('new-company-name').value = '';
            document.getElementById('initial-balance').value = '';
            
            // إعادة تعيين نوع الرصيد
            document.querySelectorAll('.type-btn[data-balance-type]').forEach(b => b.classList.remove('active'));
            document.querySelector('.type-btn[data-balance-type="credit"]').classList.add('active');
            balanceType = 'credit';
            document.getElementById('balance-type').value = 'credit';
            
            setTimeout(() => document.getElementById('new-company-name').focus(), 100);
        }

        // إغلاق نافذة إضافة شركة
        function closeAddCompanyModal() {
            document.getElementById('add-company-modal').classList.remove('active');
        }

        // حفظ شركة جديدة
        function saveNewCompany() {
            const companyName = document.getElementById('new-company-name').value.trim();
            const balance = parseFloat(document.getElementById('initial-balance').value) || 0;
            
            if (!companyName) {
                showNotification('يرجى إدخال اسم الشركة', 'error');
                return;
            }
            
            if (companies[companyName]) {
                showNotification('هذه الشركة موجودة مسبقاً', 'error');
                return;
            }
            
            let openingBalance = balance;
            if (balanceType === 'debit') {
                openingBalance = -balance;
            }
            
            companies[companyName] = {
                LYD: openingBalance,
                EUR: 0,
                USD: 0,
                openingBalance: openingBalance
            };
            
            if (balance > 0) {
                const transaction = {
                    id: generateId(),
                    date: new Date().toISOString().split('T')[0],
                    type: 'initial',
                    company: companyName,
                    amount: balance,
                    currency: 'LYD',
                    description: `رصيد افتتاحي ${balanceType === 'credit' ? 'دائن (الشركة تحتاج مني)' : 'مدين (أحتاج من الشركة)'}`
                };
                
                transactions.push(transaction);
            }
            
            saveData();
            updateCompanySelect();
            updateReportCompanySelect();
            updateFilterCompanySelect();
            updateCompanyList();
            updateReport();
            updateManageTable();
            updateStats();
            
            document.getElementById('company').value = companyName;
            updateCompanyInfo(companyName);
            
            closeAddCompanyModal();
            showNotification('تم إضافة الشركة بنجاح', 'success');
        }

        // إضافة عملية جديدة
        function addTransaction() {
            const company = document.getElementById('company').value;
            const type = document.getElementById('transaction-type').value;
            const currency = document.getElementById('currency').value;
            const amount = parseFloat(document.getElementById('amount').value);
            const date = document.getElementById('date').value;
            
            // التحقق من البيانات
            if (!company) {
                showNotification('يرجى اختيار شركة', 'error');
                return;
            }
            
            if (!amount || amount <= 0) {
                showNotification('يرجى إدخال مبلغ صحيح أكبر من صفر', 'error');
                return;
            }
            
            if (!date) {
                showNotification('يرجى اختيار تاريخ', 'error');
                return;
            }
            
            // إنشاء العملية
            const transaction = {
                id: generateId(),
                date: date,
                type: type,
                company: company,
                amount: amount,
                currency: currency
            };
            
            // إضافة البيانات الخاصة بالنوع
            if (type === 'ticket') {
                const passengerName = document.getElementById('passenger-name').value.trim();
                const documentNumber = document.getElementById('document-number').value.trim();
                let destination = document.getElementById('destination').value;
                
                if (destination === 'other') {
                    destination = document.getElementById('other-destination').value.trim();
                    if (!destination) {
                        showNotification('يرجى إدخال الوجهة', 'error');
                        return;
                    }
                }
                
                if (!passengerName || !documentNumber) {
                    showNotification('يرجى إكمال بيانات التذكرة', 'error');
                    return;
                }
                
                transaction.passengerName = passengerName;
                transaction.documentNumber = documentNumber;
                transaction.destination = destination;
                transaction.tripType = document.getElementById('trip-type').value;
                transaction.notes = document.getElementById('notes').value.trim();
                
            } else if (type === 'fine') {
                const passengerName = document.getElementById('passenger-name').value.trim();
                const documentNumber = document.getElementById('document-number').value.trim();
                const reason = document.getElementById('fine-reason').value.trim();
                
                if (!reason) {
                    showNotification('يرجى إدخال سبب الغرامة', 'error');
                    return;
                }
                
                transaction.passengerName = passengerName;
                transaction.documentNumber = documentNumber;
                transaction.destination = document.getElementById('destination').value;
                transaction.tripType = document.getElementById('trip-type').value;
                transaction.reason = reason;
                
            } else if (type === 'payment') {
                const description = document.getElementById('payment-description').value.trim();
                
                if (!description) {
                    showNotification('يرجى إدخال وصف الدفعة', 'error');
                    return;
                }
                
                transaction.description = description;
            }
            
            // تحديث رصيد الشركة
            updateCompanyBalance(company, type, amount, currency);
            
            // إضافة العملية
            transactions.push(transaction);
            saveData();
            
            // تحديث الواجهة
            updateReport();
            updateManageTable();
            updateStats();
            updateCompanyInfo(company);
            
            // إعادة تعيين النموذج
            resetForm();
            
            showNotification('تم إضافة العملية بنجاح', 'success');
        }

        // تحديث رصيد الشركة
        function updateCompanyBalance(company, type, amount, currency) {
            if (!companies[company]) {
                companies[company] = {
                    LYD: 0,
                    EUR: 0,
                    USD: 0,
                    openingBalance: 0
                };
            }
            
            if (type === 'ticket' || type === 'fine') {
                companies[company][currency] += amount;
            } else if (type === 'payment') {
                companies[company][currency] -= amount;
            }
        }

        // إعادة تعيين النموذج
        function resetForm() {
            document.getElementById('passenger-name').value = '';
            document.getElementById('document-number').value = '';
            document.getElementById('destination').value = 'TIP - IST';
            document.getElementById('other-destination').value = '';
            document.getElementById('other-destination').style.display = 'none';
            document.getElementById('trip-type').value = 'ذهاب';
            document.getElementById('fine-reason').value = '';
            document.getElementById('payment-description').value = '';
            document.getElementById('amount').value = '';
            document.getElementById('date').value = new Date().toISOString().split('T')[0];
            document.getElementById('notes').value = '';
            
            // إعادة تعيين نوع العملية
            document.querySelectorAll('.type-btn[data-type]').forEach(b => b.classList.remove('active'));
            document.querySelector('.type-btn[data-type="ticket"]').classList.add('active');
            document.getElementById('transaction-type').value = 'ticket';
            updateFormFields('ticket');
            
            // إعادة تعيين العملة
            document.getElementById('currency').value = 'LYD';
            updateCurrencySymbol();
        }

        // تحديث كشف الحساب
        function updateReport() {
            const company = document.getElementById('report-company').value;
            const tbody = document.getElementById('transactions-body');
            const noData = document.getElementById('no-data');
            
            // تصفية العمليات
            let filteredTransactions = company ? 
                transactions.filter(t => t.company === company) : 
                [...transactions];
            
            // ترتيب حسب التاريخ
            filteredTransactions.sort((a, b) => new Date(b.date) - new Date(a.date));
            
            // تحديث الجدول
            if (filteredTransactions.length === 0) {
                tbody.innerHTML = '';
                noData.style.display = 'block';
                document.getElementById('currency-summaries').innerHTML = '';
                return;
            }
            
            noData.style.display = 'none';
            tbody.innerHTML = '';
            
            let runningBalances = { LYD: 0, EUR: 0, USD: 0 };
            let groupedByCurrency = { LYD: [], EUR: [], USD: [] };
            
            filteredTransactions.forEach((transaction, index) => {
                // تحديث الرصيد الجاري
                if (transaction.type === 'ticket' || transaction.type === 'fine' || transaction.type === 'initial') {
                    runningBalances[transaction.currency] += transaction.amount;
                } else if (transaction.type === 'payment' || transaction.type === 'cancel') {
                    runningBalances[transaction.currency] -= transaction.amount;
                }
                
                // تجميع حسب العملة
                if (!groupedByCurrency[transaction.currency]) {
                    groupedByCurrency[transaction.currency] = [];
                }
                groupedByCurrency[transaction.currency].push(transaction);
                
                // إضافة الصف
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${transaction.date}</td>
                    <td><span class="currency-badge ${transaction.currency.toLowerCase()}">${transaction.currency}</span></td>
                    <td><span class="badge badge-${transaction.type}">${getTypeName(transaction.type)}</span></td>
                    <td>${transaction.passengerName || transaction.description || '-'}</td>
                    <td>${transaction.documentNumber || '-'}</td>
                    <td>${transaction.destination || '-'}</td>
                    <td>${formatCurrency(transaction.amount, transaction.currency)}</td>
                    <td>${formatCurrency(runningBalances[transaction.currency], transaction.currency)}</td>
                `;
                tbody.appendChild(row);
            });
            
            // تحديث ملخص العملات
            updateCurrencySummaries(groupedByCurrency, runningBalances);
        }

        // تصفية التقرير حسب العملة
        function filterReportByCurrency(currency) {
            const rows = document.querySelectorAll('#transactions-body tr');
            const summaries = document.querySelectorAll('#currency-summaries .summary-card');
            
            if (currency === 'all') {
                rows.forEach(row => row.style.display = '');
                summaries.forEach(summary => summary.style.display = 'block');
                return;
            }
            
            rows.forEach(row => {
                const rowCurrency = row.querySelector('.currency-badge').textContent;
                row.style.display = rowCurrency === currency ? '' : 'none';
            });
            
            summaries.forEach(summary => {
                const summaryCurrency = summary.dataset.currency;
                summary.style.display = summaryCurrency === currency ? 'block' : 'none';
            });
        }

        // تحديث ملخص العملات
        function updateCurrencySummaries(groupedByCurrency, runningBalances) {
            const container = document.getElementById('currency-summaries');
            container.innerHTML = '';
            
            Object.keys(groupedByCurrency).forEach(currency => {
                if (groupedByCurrency[currency].length === 0) return;
                
                const transactions = groupedByCurrency[currency];
                let totalTickets = 0;
                let totalFines = 0;
                let totalPayments = 0;
                
                transactions.forEach(t => {
                    if (t.type === 'ticket') totalTickets++;
                    else if (t.type === 'fine') totalFines += t.amount;
                    else if (t.type === 'payment') totalPayments += t.amount;
                });
                
                const summary = document.createElement('div');
                summary.className = 'summary-card';
                summary.dataset.currency = currency;
                summary.innerHTML = `
                    <div class="summary-icon ${currency.toLowerCase()}">
                        <i class="fas ${getCurrencyIcon(currency)}"></i>
                    </div>
                    <div class="summary-title">${getCurrencyName(currency)}</div>
                    <div class="summary-value">${formatCurrency(runningBalances[currency], currency)}</div>
                    <div style="margin-top: 1rem; display: grid; grid-template-columns: repeat(3, 1fr); gap: 0.5rem;">
                        <div>
                            <div style="font-size: 0.75rem; color: var(--gray-500);">التذاكر</div>
                            <div style="font-weight: 600;">${totalTickets}</div>
                        </div>
                        <div>
                            <div style="font-size: 0.75rem; color: var(--gray-500);">الغرامات</div>
                            <div style="font-weight: 600;">${formatCurrency(totalFines, currency)}</div>
                        </div>
                        <div>
                            <div style="font-size: 0.75rem; color: var(--gray-500);">المدفوعات</div>
                            <div style="font-weight: 600;">${formatCurrency(totalPayments, currency)}</div>
                        </div>
                    </div>
                `;
                container.appendChild(summary);
            });
        }

        // تحديث جدول إدارة العمليات
        function updateManageTable() {
            const companyFilter = document.getElementById('filter-company').value;
            const typeFilter = document.getElementById('filter-type').value;
            const currencyFilter = document.getElementById('filter-currency').value;
            
            let filteredTransactions = [...transactions];
            
            if (companyFilter) {
                filteredTransactions = filteredTransactions.filter(t => t.company === companyFilter);
            }
            
            if (typeFilter) {
                filteredTransactions = filteredTransactions.filter(t => t.type === typeFilter);
            }
            
            if (currencyFilter) {
                filteredTransactions = filteredTransactions.filter(t => t.currency === currencyFilter);
            }
            
            const tbody = document.getElementById('manage-transactions-body');
            const noTransactions = document.getElementById('no-transactions');
            
            if (filteredTransactions.length === 0) {
                tbody.innerHTML = '';
                noTransactions.style.display = 'block';
                return;
            }
            
            noTransactions.style.display = 'none';
            tbody.innerHTML = '';
            
            filteredTransactions.sort((a, b) => new Date(b.date) - new Date(a.date)).forEach((transaction, index) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${transaction.date}</td>
                    <td>${transaction.company}</td>
                    <td><span class="currency-badge ${transaction.currency.toLowerCase()}">${transaction.currency}</span></td>
                    <td><span class="badge badge-${transaction.type}">${getTypeName(transaction.type)}</span></td>
                    <td>${transaction.passengerName || transaction.description || '-'}</td>
                    <td>${formatCurrency(transaction.amount, transaction.currency)}</td>
                    <td>
                        <div class="action-buttons">
                            <button class="action-btn edit" data-id="${transaction.id}" title="تعديل">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="action-btn cancel" data-id="${transaction.id}" title="إلغاء">
                                <i class="fas fa-exchange-alt"></i>
                            </button>
                            <button class="action-btn delete" data-id="${transaction.id}" title="حذف">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
            
            // إضافة مستمعي الأحداث للأزرار
            addActionButtonListeners();
        }

        // إعادة تعيين الفلاتر
        function resetFilters() {
            document.getElementById('filter-company').value = '';
            document.getElementById('filter-type').value = '';
            document.getElementById('filter-currency').value = '';
            updateManageTable();
        }

        // إضافة مستمعي الأحداث لأزرار الإجراءات
        function addActionButtonListeners() {
            document.querySelectorAll('.action-btn.edit').forEach(btn => {
                btn.addEventListener('click', () => {
                    const id = btn.dataset.id;
                    openEditForm(id);
                });
            });
            
            document.querySelectorAll('.action-btn.delete').forEach(btn => {
                btn.addEventListener('click', () => {
                    const id = btn.dataset.id;
                    openDeleteConfirm(id);
                });
            });
            
            document.querySelectorAll('.action-btn.cancel').forEach(btn => {
                btn.addEventListener('click', () => {
                    const id = btn.dataset.id;
                    openCancelConfirm(id);
                });
            });
        }

        // فتح نموذج التعديل
        function openEditForm(transactionId) {
            const transaction = transactions.find(t => t.id === transactionId);
            if (!transaction) return;
            
            currentEditTransactionId = transactionId;
            
            document.getElementById('edit-transaction-type').value = transaction.type;
            document.getElementById('edit-currency').value = transaction.currency;
            
            // تحديث الحقول حسب النوع
            updateEditFormFields(transaction.type);
            
            if (transaction.type === 'ticket' || transaction.type === 'fine') {
                document.getElementById('edit-passenger-name').value = transaction.passengerName || '';
                document.getElementById('edit-document-number').value = transaction.documentNumber || '';
                if (transaction.type === 'fine') {
                    document.getElementById('edit-fine-reason').value = transaction.reason || '';
                }
            } else if (transaction.type === 'payment') {
                document.getElementById('edit-payment-description').value = transaction.description || '';
            }
            
            document.getElementById('edit-amount').value = transaction.amount;
            document.getElementById('edit-date').value = transaction.date;
            document.getElementById('edit-notes').value = transaction.notes || '';
            
            document.getElementById('edit-form-container').style.display = 'block';
            document.getElementById('delete-confirm-container').style.display = 'none';
        }

        // تحديث حقول نموذج التعديل
        function updateEditFormFields(type) {
            document.getElementById('edit-ticket-fields').style.display = 
                (type === 'ticket' || type === 'fine') ? 'block' : 'none';
            document.getElementById('edit-fine-only-fields').style.display = 
                type === 'fine' ? 'block' : 'none';
            document.getElementById('edit-payment-fields').style.display = 
                type === 'payment' ? 'block' : 'none';
        }

        // إلغاء التعديل
        function cancelEdit() {
            document.getElementById('edit-form-container').style.display = 'none';
            currentEditTransactionId = null;
        }

        // حفظ التعديل
        function saveEdit() {
            if (!currentEditTransactionId) return;
            
            const transactionIndex = transactions.findIndex(t => t.id === currentEditTransactionId);
            if (transactionIndex === -1) return;
            
            const oldTransaction = transactions[transactionIndex];
            const oldAmount = oldTransaction.amount;
            const oldType = oldTransaction.type;
            const oldCurrency = oldTransaction.currency;
            
            // التراجع عن التأثير القديم
            if (oldType === 'ticket' || oldType === 'fine') {
                if (companies[oldTransaction.company]) {
                    companies[oldTransaction.company][oldCurrency] -= oldAmount;
                }
            } else if (oldType === 'payment') {
                if (companies[oldTransaction.company]) {
                    companies[oldTransaction.company][oldCurrency] += oldAmount;
                }
            }
            
            const newType = document.getElementById('edit-transaction-type').value;
            const newCurrency = document.getElementById('edit-currency').value;
            const newAmount = parseFloat(document.getElementById('edit-amount').value);
            
            if (!newAmount || newAmount <= 0) {
                showNotification('يرجى إدخال مبلغ صحيح أكبر من صفر', 'error');
                return;
            }
            
            // تحديث العملية
            const updatedTransaction = {
                ...oldTransaction,
                type: newType,
                currency: newCurrency,
                amount: newAmount,
                date: document.getElementById('edit-date').value
            };
            
            // تحديث البيانات الخاصة بالنوع
            if (newType === 'ticket' || newType === 'fine') {
                updatedTransaction.passengerName = document.getElementById('edit-passenger-name').value.trim();
                updatedTransaction.documentNumber = document.getElementById('edit-document-number').value.trim();
                if (newType === 'fine') {
                    updatedTransaction.reason = document.getElementById('edit-fine-reason').value.trim();
                }
                updatedTransaction.description = '';
            } else if (newType === 'payment') {
                updatedTransaction.description = document.getElementById('edit-payment-description').value.trim();
                updatedTransaction.passengerName = '';
                updatedTransaction.documentNumber = '';
                updatedTransaction.reason = '';
            }
            
            updatedTransaction.notes = document.getElementById('edit-notes').value.trim();
            
            // تطبيق التأثير الجديد
            if (newType === 'ticket' || newType === 'fine') {
                if (!companies[updatedTransaction.company]) {
                    companies[updatedTransaction.company] = {
                        LYD: 0,
                        EUR: 0,
                        USD: 0,
                        openingBalance: 0
                    };
                }
                companies[updatedTransaction.company][newCurrency] += newAmount;
            } else if (newType === 'payment') {
                if (!companies[updatedTransaction.company]) {
                    companies[updatedTransaction.company] = {
                        LYD: 0,
                        EUR: 0,
                        USD: 0,
                        openingBalance: 0
                    };
                }
                companies[updatedTransaction.company][newCurrency] -= newAmount;
            }
            
            transactions[transactionIndex] = updatedTransaction;
            saveData();
            
            updateReport();
            updateManageTable();
            updateStats();
            updateCompanyInfo(updatedTransaction.company);
            
            cancelEdit();
            showNotification('تم تحديث العملية بنجاح', 'success');
        }

        // فتح تأكيد الحذف
        function openDeleteConfirm(transactionId) {
            const transaction = transactions.find(t => t.id === transactionId);
            if (!transaction) return;
            
            currentDeleteTransactionId = transactionId;
            document.getElementById('delete-confirm-container').style.display = 'block';
            document.getElementById('edit-form-container').style.display = 'none';
        }

        // إلغاء الحذف
        function cancelDelete() {
            document.getElementById('delete-confirm-container').style.display = 'none';
            currentDeleteTransactionId = null;
        }

        // تأكيد الحذف
        function confirmDelete() {
            if (!currentDeleteTransactionId) return;
            
            const transactionIndex = transactions.findIndex(t => t.id === currentDeleteTransactionId);
            if (transactionIndex === -1) return;
            
            const transaction = transactions[transactionIndex];
            
            // تحديث رصيد الشركة
            if (transaction.type === 'ticket' || transaction.type === 'fine') {
                if (companies[transaction.company]) {
                    companies[transaction.company][transaction.currency] -= transaction.amount;
                }
            } else if (transaction.type === 'payment') {
                if (companies[transaction.company]) {
                    companies[transaction.company][transaction.currency] += transaction.amount;
                }
            }
            
            transactions.splice(transactionIndex, 1);
            saveData();
            
            updateReport();
            updateManageTable();
            updateStats();
            updateCompanyInfo(transaction.company);
            
            cancelDelete();
            showNotification('تم حذف العملية بنجاح', 'success');
        }

        // فتح تأكيد الإلغاء
        function openCancelConfirm(transactionId) {
            const transaction = transactions.find(t => t.id === transactionId);
            if (!transaction) return;
            
            currentCancelTransactionId = transactionId;
            
            if (transaction.type === 'cancel') {
                showNotification('لا يمكن إلغاء عملية إلغاء!', 'error');
                return;
            }
            
            document.getElementById('cancel-details').innerHTML = `
                <p><strong>تفاصيل العملية الأصلية:</strong></p>
                <div style="background: var(--gray-50); padding: 1rem; border-radius: var(--radius); margin: 1rem 0;">
                    <div><strong>الشركة:</strong> ${transaction.company}</div>
                    <div><strong>النوع:</strong> ${getTypeName(transaction.type)}</div>
                    <div><strong>العملة:</strong> ${getCurrencyName(transaction.currency)}</div>
                    <div><strong>المبلغ:</strong> ${formatCurrency(transaction.amount, transaction.currency)}</div>
                    <div><strong>التاريخ:</strong> ${transaction.date}</div>
                </div>
                <p>سيتم إضافة عملية جديدة معكوسة بنفس البيانات لتحييد المبلغ.</p>
            `;
            
            document.getElementById('cancel-transaction-modal').classList.add('active');
        }

        // إغلاق نافذة الإلغاء
        function closeCancelModal() {
            document.getElementById('cancel-transaction-modal').classList.remove('active');
            currentCancelTransactionId = null;
        }

        // تأكيد الإلغاء
        function confirmCancel() {
            if (!currentCancelTransactionId) return;
            
            const originalTransaction = transactions.find(t => t.id === currentCancelTransactionId);
            if (!originalTransaction) return;
            
            // إنشاء عملية إلغاء
            const cancelTransaction = {
                id: generateId(),
                date: new Date().toISOString().split('T')[0],
                type: 'cancel',
                company: originalTransaction.company,
                amount: originalTransaction.amount,
                currency: originalTransaction.currency,
                originalTransactionId: originalTransaction.id,
                description: `إلغاء عملية ${getTypeName(originalTransaction.type)} بتاريخ ${originalTransaction.date}`
            };
            
            // نسخ البيانات من العملية الأصلية
            if (originalTransaction.type === 'ticket' || originalTransaction.type === 'fine') {
                cancelTransaction.passengerName = originalTransaction.passengerName;
                cancelTransaction.documentNumber = originalTransaction.documentNumber;
            }
            
            // تحديث رصيد الشركة (عملية معاكسة)
            if (originalTransaction.type === 'ticket' || originalTransaction.type === 'fine') {
                if (companies[originalTransaction.company]) {
                    companies[originalTransaction.company][originalTransaction.currency] -= originalTransaction.amount;
                }
            } else if (originalTransaction.type === 'payment') {
                if (companies[originalTransaction.company]) {
                    companies[originalTransaction.company][originalTransaction.currency] += originalTransaction.amount;
                }
            }
            
            transactions.push(cancelTransaction);
            saveData();
            
            updateReport();
            updateManageTable();
            updateStats();
            updateCompanyInfo(originalTransaction.company);
            
            closeCancelModal();
            showNotification('تم إضافة عملية الإلغاء بنجاح', 'success');
        }

        // الطباعة
        function printReport() {
            window.print();
        }

        // دالات مساعدة
        function generateId() {
            return Date.now().toString(36) + Math.random().toString(36).substr(2);
        }

        function getTypeName(type) {
            const names = {
                'ticket': 'تذكرة',
                'fine': 'غرامة',
                'payment': 'تسليم',
                'cancel': 'إلغاء',
                'initial': 'افتتاحي'
            };
            return names[type] || type;
        }

        function getCurrencyName(currency) {
            const names = {
                'LYD': 'دينار ليبي',
                'EUR': 'يورو',
                'USD': 'دولار أمريكي'
            };
            return names[currency] || currency;
        }

        function getCurrencyIcon(currency) {
            const icons = {
                'LYD': 'fa-coins',
                'EUR': 'fa-euro-sign',
                'USD': 'fa-dollar-sign'
            };
            return icons[currency] || 'fa-money-bill';
        }

        function formatCurrency(amount, currency) {
            const absAmount = Math.abs(amount);
            let symbol = '';
            
            switch(currency) {
                case 'LYD':
                    symbol = 'دينار';
                    break;
                case 'EUR':
                    symbol = 'يورو';
                    break;
                case 'USD':
                    symbol = 'دولار';
                    break;
            }
            
            const formatted = absAmount.toLocaleString('ar-LY', {
                minimumFractionDigits: 3,
                maximumFractionDigits: 3
            }) + ' ' + symbol;
            
            return amount < 0 ? '-' + formatted : formatted;
        }

        function showNotification(message, type = 'info') {
            // إزالة الإشعارات القديمة
            const oldNotifications = document.querySelectorAll('.notification');
            oldNotifications.forEach(n => n.remove());
            
            // إنشاء إشعار جديد
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.innerHTML = `
                <i class="fas fa-${type === 'success' ? 'check-circle' : type === 'error' ? 'exclamation-circle' : type === 'warning' ? 'exclamation-triangle' : 'info-circle'}"></i>
                <span>${message}</span>
            `;
            
            document.body.appendChild(notification);
            
            // إزالة الإشعار بعد 5 ثواني
            setTimeout(() => {
                if (notification.parentNode) {
                    notification.style.opacity = '0';
                    notification.style.transform = 'translateX(-50%) translateY(-20px)';
                    setTimeout(() => {
                        if (notification.parentNode) {
                            notification.remove();
                        }
                    }, 300);
                }
            }, 5000);
        }

        // تحديث select الشركات للتقرير
        function updateReportCompanySelect() {
            const select = document.getElementById('report-company');
            const currentValue = select.value;
            
            select.innerHTML = '<option value="">-- اختر الشركة --</option>';
            Object.keys(companies).sort().forEach(company => {
                const option = document.createElement('option');
                option.value = company;
                option.textContent = company;
                select.appendChild(option);
            });
            
            if (currentValue && companies[currentValue]) {
                select.value = currentValue;
            }
        }

        // تحديث select فلاتر الشركات
        function updateFilterCompanySelect() {
            const select = document.getElementById('filter-company');
            const currentValue = select.value;
            
            select.innerHTML = '<option value="">جميع الشركات</option>';
            Object.keys(companies).sort().forEach(company => {
                const option = document.createElement('option');
                option.value = company;
                option.textContent = company;
                select.appendChild(option);
            });
            
            if (currentValue && companies[currentValue]) {
                select.value = currentValue;
            }
        }

        // إضافة فئات CSS للهامش
        const style = document.createElement('style');
        style.textContent = `
            .mt-2 { margin-top: 0.5rem; }
            .btn-sm { padding: 0.5rem 1rem; font-size: 0.875rem; }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
