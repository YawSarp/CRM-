<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vidaluma CRM — Medical Tourism Platform</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Noto+Sans+SC:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --vida-primary: #0d9488;
            --vida-primary-dark: #0f766e;
            --vida-primary-light: #ccfbf1;
            --vida-secondary: #14b8a6;
            --vida-accent: #f59e0b;
            --vida-success: #10b981;
            --vida-warning: #f59e0b;
            --vida-danger: #ef4444;
            --vida-purple: #8b5cf6;
            --vida-rose: #f43f5e;
            --vida-dark: #0f172a;
            --vida-gray-900: #111827;
            --vida-gray-800: #1f2937;
            --vida-gray-700: #374151;
            --vida-gray-600: #4b5563;
            --vida-gray-500: #6b7280;
            --vida-gray-400: #9ca3af;
            --vida-gray-300: #d1d5db;
            --vida-gray-200: #e5e7eb;
            --vida-gray-100: #f3f4f6;
            --vida-gray-50: #f9fafb;
            --vida-white: #ffffff;
            --sidebar-width: 280px;
            --sidebar-collapsed: 72px;
            --header-height: 68px;
            --radius-sm: 6px;
            --radius-md: 10px;
            --radius-lg: 14px;
            --radius-xl: 20px;
            --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
            --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
            --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
            --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        html { scroll-behavior: smooth; }

        body {
            font-family: 'Inter', 'Noto Sans SC', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--vida-gray-50);
            color: var(--vida-gray-900);
            font-size: 14px;
            line-height: 1.5;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
        }

        /* ===== SIDEBAR ===== */
        .sidebar {
            position: fixed;
            left: 0; top: 0;
            width: var(--sidebar-width);
            height: 100vh;
            background: var(--vida-dark);
            color: var(--vida-white);
            z-index: 1000;
            display: flex;
            flex-direction: column;
            transition: width 0.3s ease;
            overflow: hidden;
        }

        .sidebar-header {
            height: var(--header-height);
            display: flex;
            align-items: center;
            padding: 0 20px;
            border-bottom: 1px solid rgba(255,255,255,0.06);
            gap: 12px;
            flex-shrink: 0;
        }

        .sidebar-logo {
            width: 38px; height: 38px;
            background: linear-gradient(135deg, var(--vida-primary), var(--vida-secondary));
            border-radius: var(--radius-md);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            flex-shrink: 0;
        }

        .sidebar-brand {
            font-weight: 700;
            font-size: 18px;
            letter-spacing: -0.3px;
        }

        .sidebar-brand span {
            font-weight: 400;
            opacity: 0.6;
            font-size: 13px;
            display: block;
            margin-top: -2px;
        }

        .sidebar-nav {
            flex: 1;
            overflow-y: auto;
            padding: 12px 0;
        }

        .sidebar-nav::-webkit-scrollbar { width: 4px; }
        .sidebar-nav::-webkit-scrollbar-track { background: transparent; }
        .sidebar-nav::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.15); border-radius: 4px; }

        .nav-section {
            padding: 16px 20px 6px;
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 0.8px;
            color: var(--vida-gray-500);
            font-weight: 600;
        }

        .nav-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 16px;
            margin: 2px 12px;
            border-radius: var(--radius-md);
            cursor: pointer;
            transition: all 0.2s;
            color: var(--vida-gray-400);
            font-size: 14px;
            font-weight: 500;
            position: relative;
            text-decoration: none;
        }

        .nav-item:hover {
            background: rgba(255,255,255,0.04);
            color: var(--vida-white);
        }

        .nav-item.active {
            background: rgba(13,148,136,0.15);
            color: var(--vida-primary);
        }

        .nav-item.active::before {
            content: '';
            position: absolute;
            left: -12px; top: 50%;
            transform: translateY(-50%);
            width: 3px; height: 20px;
            background: var(--vida-primary);
            border-radius: 0 3px 3px 0;
        }

        .nav-item i {
            width: 22px;
            text-align: center;
            font-size: 17px;
            flex-shrink: 0;
        }

        .nav-badge {
            margin-left: auto;
            background: var(--vida-danger);
            color: white;
            font-size: 11px;
            font-weight: 600;
            padding: 2px 7px;
            border-radius: 10px;
            min-width: 20px;
            text-align: center;
        }

        .sidebar-footer {
            padding: 14px 20px;
            border-top: 1px solid rgba(255,255,255,0.06);
            flex-shrink: 0;
        }

        .sidebar-user {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            padding: 6px;
            border-radius: var(--radius-md);
            transition: background 0.2s;
        }

        .sidebar-user:hover { background: rgba(255,255,255,0.04); }

        .sidebar-user-avatar {
            width: 34px; height: 34px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--vida-primary), var(--vida-secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            font-size: 13px;
            flex-shrink: 0;
        }

        .sidebar-user-info { line-height: 1.3; }
        .sidebar-user-name { font-weight: 600; font-size: 13px; }
        .sidebar-user-role { font-size: 11px; color: var(--vida-gray-500); }

        /* ===== MAIN CONTENT ===== */
        .main-content {
            margin-left: var(--sidebar-width);
            min-height: 100vh;
            transition: margin-left 0.3s ease;
        }

        /* ===== HEADER ===== */
        .header {
            height: var(--header-height);
            background: var(--vida-white);
            border-bottom: 1px solid var(--vida-gray-200);
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 28px;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .header-search {
            position: relative;
        }

        .header-search input {
            width: 380px;
            padding: 9px 14px 9px 38px;
            border: 1px solid var(--vida-gray-200);
            border-radius: var(--radius-lg);
            font-size: 13px;
            outline: none;
            transition: all 0.2s;
            background: var(--vida-gray-50);
            font-family: inherit;
        }

        .header-search input:focus {
            border-color: var(--vida-primary);
            background: var(--vida-white);
            box-shadow: 0 0 0 3px rgba(13,148,136,0.1);
        }

        .header-search input::placeholder { color: var(--vida-gray-400); }

        .header-search i {
            position: absolute;
            left: 13px; top: 50%;
            transform: translateY(-50%);
            color: var(--vida-gray-400);
            font-size: 14px;
        }

        .header-right {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .header-btn {
            position: relative;
            width: 40px; height: 40px;
            border-radius: var(--radius-md);
            border: 1px solid var(--vida-gray-200);
            background: var(--vida-white);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--vida-gray-600);
            transition: all 0.2s;
            font-size: 15px;
        }

        .header-btn:hover {
            background: var(--vida-gray-100);
            border-color: var(--vida-gray-300);
        }

        .header-btn .dot {
            position: absolute;
            top: -2px; right: -2px;
            width: 18px; height: 18px;
            background: var(--vida-danger);
            color: white;
            font-size: 10px;
            font-weight: 700;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 2px solid var(--vida-white);
        }

        .header-lang {
            display: flex;
            align-items: center;
            gap: 6px;
            padding: 7px 12px;
            border-radius: var(--radius-md);
            border: 1px solid var(--vida-gray-200);
            background: var(--vida-white);
            cursor: pointer;
            font-size: 13px;
            font-weight: 500;
            color: var(--vida-gray-700);
            transition: all 0.2s;
        }

        .header-lang:hover { background: var(--vida-gray-100); }
        .header-lang i { font-size: 12px; color: var(--vida-gray-400); }

        /* ===== CONTENT AREA ===== */
        .content {
            padding: 24px 28px 32px;
            max-width: 1600px;
        }

        .page-header {
            margin-bottom: 24px;
        }

        .page-title {
            font-size: 26px;
            font-weight: 700;
            letter-spacing: -0.5px;
            color: var(--vida-gray-900);
            margin-bottom: 4px;
        }

        .page-subtitle {
            color: var(--vida-gray-500);
            font-size: 14px;
        }

        .page-actions {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        /* ===== BUTTONS ===== */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 9px 18px;
            border-radius: var(--radius-md);
            border: 1px solid transparent;
            font-size: 13px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            font-family: inherit;
            white-space: nowrap;
        }

        .btn-primary {
            background: var(--vida-primary);
            color: white;
            border-color: var(--vida-primary);
        }

        .btn-primary:hover {
            background: var(--vida-primary-dark);
            border-color: var(--vida-primary-dark);
            transform: translateY(-1px);
            box-shadow: var(--shadow-md);
        }

        .btn-secondary {
            background: var(--vida-white);
            color: var(--vida-gray-700);
            border-color: var(--vida-gray-300);
        }

        .btn-secondary:hover {
            background: var(--vida-gray-50);
            border-color: var(--vida-gray-400);
        }

        .btn-success {
            background: var(--vida-success);
            color: white;
            border-color: var(--vida-success);
        }

        .btn-success:hover { background: #059669; }

        .btn-ghost {
            background: transparent;
            color: var(--vida-gray-600);
            border-color: transparent;
        }

        .btn-ghost:hover { background: var(--vida-gray-100); color: var(--vida-gray-900); }

        .btn-sm { padding: 6px 12px; font-size: 12px; }
        .btn-lg { padding: 12px 24px; font-size: 14px; }
        .btn-icon { padding: 8px; gap: 0; }

        /* ===== CARDS ===== */
        .card {
            background: var(--vida-white);
            border-radius: var(--radius-xl);
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--vida-gray-100);
            overflow: hidden;
        }

        .card-header {
            padding: 20px 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid var(--vida-gray-100);
        }

        .card-header h3 {
            font-size: 16px;
            font-weight: 700;
            color: var(--vida-gray-900);
        }

        .card-body { padding: 20px 24px; }
        .card-body-no-pad { padding: 0; }

        /* ===== STATS ===== */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-bottom: 24px;
        }

        .stat-card {
            background: var(--vida-white);
            border-radius: var(--radius-xl);
            padding: 22px;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--vida-gray-100);
            transition: all 0.2s;
        }

        .stat-card:hover {
            box-shadow: var(--shadow-md);
            transform: translateY(-2px);
        }

        .stat-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 16px;
        }

        .stat-icon {
            width: 44px; height: 44px;
            border-radius: var(--radius-lg);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
        }

        .stat-icon.teal { background: rgba(13,148,136,0.1); color: var(--vida-primary); }
        .stat-icon.green { background: rgba(16,185,129,0.1); color: var(--vida-success); }
        .stat-icon.amber { background: rgba(245,158,11,0.1); color: var(--vida-warning); }
        .stat-icon.rose { background: rgba(244,63,94,0.1); color: var(--vida-rose); }
        .stat-icon.purple { background: rgba(139,92,246,0.1); color: var(--vida-purple); }
        .stat-icon.blue { background: rgba(59,130,246,0.1); color: #3b82f6; }

        .stat-trend {
            font-size: 12px;
            font-weight: 600;
            padding: 4px 8px;
            border-radius: var(--radius-sm);
            display: flex;
            align-items: center;
            gap: 3px;
        }

        .stat-trend.up { background: rgba(16,185,129,0.1); color: var(--vida-success); }
        .stat-trend.down { background: rgba(239,68,68,0.1); color: var(--vida-danger); }

        .stat-value {
            font-size: 30px;
            font-weight: 800;
            letter-spacing: -1px;
            color: var(--vida-gray-900);
            margin-bottom: 4px;
        }

        .stat-label {
            font-size: 13px;
            color: var(--vida-gray-500);
            font-weight: 500;
        }

        /* ===== TABLES ===== */
        .table-wrap { overflow-x: auto; }

        .data-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 13px;
        }

        .data-table thead th {
            text-align: left;
            padding: 12px 20px;
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: var(--vida-gray-500);
            font-weight: 600;
            background: var(--vida-gray-50);
            border-bottom: 1px solid var(--vida-gray-200);
            white-space: nowrap;
        }

        .data-table tbody td {
            padding: 14px 20px;
            border-bottom: 1px solid var(--vida-gray-100);
            color: var(--vida-gray-700);
            vertical-align: middle;
        }

        .data-table tbody tr:hover { background: var(--vida-gray-50); }
        .data-table tbody tr:last-child td { border-bottom: none; }

        /* ===== AVATARS & BADGES ===== */
        .avatar {
            width: 36px; height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            font-size: 13px;
            color: white;
            flex-shrink: 0;
            background: linear-gradient(135deg, var(--vida-primary), var(--vida-secondary));
        }

        .avatar-sm { width: 28px; height: 28px; font-size: 11px; }
        .avatar-lg { width: 48px; height: 48px; font-size: 16px; }
        .avatar-xl { width: 72px; height: 72px; font-size: 24px; }

        .badge {
            display: inline-flex;
            align-items: center;
            gap: 4px;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            white-space: nowrap;
        }

        .badge-teal { background: rgba(13,148,136,0.1); color: var(--vida-primary); }
        .badge-green { background: rgba(16,185,129,0.1); color: var(--vida-success); }
        .badge-amber { background: rgba(245,158,11,0.1); color: #b45309; }
        .badge-rose { background: rgba(244,63,94,0.1); color: var(--vida-rose); }
        .badge-purple { background: rgba(139,92,246,0.1); color: var(--vida-purple); }
        .badge-gray { background: var(--vida-gray-100); color: var(--vida-gray-600); }
        .badge-blue { background: rgba(59,130,246,0.1); color: #2563eb; }

        .badge-dot {
            width: 6px; height: 6px;
            border-radius: 50%;
            display: inline-block;
        }

        .badge-dot.teal { background: var(--vida-primary); }
        .badge-dot.green { background: var(--vida-success); }
        .badge-dot.amber { background: var(--vida-warning); }
        .badge-dot.rose { background: var(--vida-rose); }
        .badge-dot.gray { background: var(--vida-gray-400); }

        /* ===== PRIORITY ===== */
        .priority { font-size: 11px; font-weight: 700; padding: 3px 8px; border-radius: 4px; }
        .priority-high { background: rgba(239,68,68,0.1); color: var(--vida-danger); }
        .priority-medium { background: rgba(245,158,11,0.1); color: #b45309; }
        .priority-low { background: rgba(16,185,129,0.1); color: var(--vida-success); }

        /* ===== TABS ===== */
        .tabs {
            display: flex;
            gap: 2px;
            padding: 0 20px;
            border-bottom: 1px solid var(--vida-gray-200);
            background: var(--vida-white);
        }

        .tab {
            padding: 14px 18px;
            cursor: pointer;
            font-weight: 600;
            font-size: 13px;
            color: var(--vida-gray-500);
            border-bottom: 2px solid transparent;
            transition: all 0.2s;
            white-space: nowrap;
            background: none;
            border-top: none;
            border-left: none;
            border-right: none;
            font-family: inherit;
        }

        .tab:hover { color: var(--vida-gray-700); }
        .tab.active {
            color: var(--vida-primary);
            border-bottom-color: var(--vida-primary);
        }

        .tab-pane { display: none; }
        .tab-pane.active { display: block; animation: fadeIn 0.3s ease; }

        /* ===== QUICK ACTIONS ===== */
        .quick-actions {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 16px;
            margin-bottom: 24px;
        }

        .quick-action {
            background: var(--vida-white);
            border: 1px solid var(--vida-gray-200);
            border-radius: var(--radius-xl);
            padding: 18px 20px;
            display: flex;
            align-items: center;
            gap: 14px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .quick-action:hover {
            border-color: var(--vida-primary);
            box-shadow: var(--shadow-md);
            transform: translateY(-2px);
        }

        .quick-action-icon {
            width: 44px; height: 44px;
            border-radius: var(--radius-lg);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            flex-shrink: 0;
        }

        .quick-action-text h4 {
            font-weight: 600;
            font-size: 14px;
            color: var(--vida-gray-900);
            margin-bottom: 2px;
        }

        .quick-action-text span {
            font-size: 12px;
            color: var(--vida-gray-500);
        }

        /* ===== GRID LAYOUTS ===== */
        .grid-2 { display: grid; grid-template-columns: 2fr 1fr; gap: 20px; }
        .grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
        .grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; }
        .grid-1 { display: grid; grid-template-columns: 1fr; gap: 20px; }

        /* ===== TIMELINE ===== */
        .timeline { padding: 8px 0; }

        .timeline-item {
            display: flex;
            gap: 14px;
            padding-bottom: 24px;
            position: relative;
        }

        .timeline-item:not(:last-child)::before {
            content: '';
            position: absolute;
            left: 17px; top: 36px; bottom: 0;
            width: 2px;
            background: var(--vida-gray-200);
        }

        .timeline-dot {
            width: 36px; height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
            font-size: 13px;
            z-index: 1;
        }

        .timeline-dot.teal { background: rgba(13,148,136,0.1); color: var(--vida-primary); }
        .timeline-dot.green { background: rgba(16,185,129,0.1); color: var(--vida-success); }
        .timeline-dot.amber { background: rgba(245,158,11,0.1); color: var(--vida-warning); }
        .timeline-dot.purple { background: rgba(139,92,246,0.1); color: var(--vida-purple); }
        .timeline-dot.blue { background: rgba(59,130,246,0.1); color: #3b82f6; }
        .timeline-dot.rose { background: rgba(244,63,94,0.1); color: var(--vida-rose); }

        .timeline-content h4 {
            font-weight: 600;
            font-size: 14px;
            color: var(--vida-gray-900);
            margin-bottom: 3px;
        }

        .timeline-content p {
            color: var(--vida-gray-500);
            font-size: 13px;
            margin-bottom: 3px;
        }

        .timeline-time {
            font-size: 12px;
            color: var(--vida-gray-400);
        }

        /* ===== KANBAN / PIPELINE ===== */
        .pipeline-wrap {
            overflow-x: auto;
            padding-bottom: 8px;
        }

        .pipeline-wrap::-webkit-scrollbar { height: 6px; }
        .pipeline-wrap::-webkit-scrollbar-track { background: var(--vida-gray-100); border-radius: 3px; }
        .pipeline-wrap::-webkit-scrollbar-thumb { background: var(--vida-gray-300); border-radius: 3px; }

        .pipeline {
            display: flex;
            gap: 16px;
            min-width: 1100px;
        }

        .pipeline-col {
            flex: 1;
            min-width: 260px;
            max-width: 300px;
        }

        .pipeline-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 14px;
            padding: 0 2px;
        }

        .pipeline-title {
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 700;
            font-size: 13px;
            color: var(--vida-gray-700);
        }

        .pipeline-count {
            background: var(--vida-gray-100);
            padding: 3px 9px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: 700;
            color: var(--vida-gray-600);
        }

        .pipeline-cards {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .pipeline-card {
            background: var(--vida-white);
            border: 1px solid var(--vida-gray-200);
            border-radius: var(--radius-lg);
            padding: 14px;
            cursor: grab;
            transition: all 0.2s;
        }

        .pipeline-card:hover {
            box-shadow: var(--shadow-md);
            border-color: var(--vida-gray-300);
            transform: translateY(-2px);
        }

        .pipeline-card-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 8px;
        }

        .pipeline-card-title {
            font-weight: 600;
            font-size: 13px;
            color: var(--vida-gray-900);
        }

        .pipeline-card-desc {
            font-size: 12px;
            color: var(--vida-gray-500);
            margin-bottom: 10px;
        }

        .pipeline-card-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 10px;
            border-top: 1px solid var(--vida-gray-100);
        }

        .pipeline-avatars {
            display: flex;
        }

        .pipeline-avatars .avatar {
            width: 26px; height: 26px;
            font-size: 10px;
            margin-left: -7px;
            border: 2px solid var(--vida-white);
        }

        .pipeline-avatars .avatar:first-child { margin-left: 0; }

        .pipeline-value {
            font-weight: 700;
            font-size: 13px;
            color: var(--vida-primary);
        }

        /* ===== MODAL ===== */
        .modal-overlay {
            position: fixed;
            inset: 0;
            background: rgba(15,23,42,0.5);
            backdrop-filter: blur(4px);
            z-index: 2000;
            display: none;
            align-items: center;
            justify-content: center;
            padding: 20px;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .modal-overlay.active {
            display: flex;
            opacity: 1;
        }

        .modal {
            background: var(--vida-white);
            border-radius: var(--radius-xl);
            width: 100%;
            max-width: 720px;
            max-height: 90vh;
            overflow-y: auto;
            transform: translateY(20px);
            transition: transform 0.3s;
            box-shadow: var(--shadow-xl);
        }

        .modal-overlay.active .modal { transform: translateY(0); }

        .modal-header {
            padding: 22px 26px;
            border-bottom: 1px solid var(--vida-gray-100);
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            background: var(--vida-white);
            z-index: 1;
        }

        .modal-title {
            font-size: 18px;
            font-weight: 700;
            color: var(--vida-gray-900);
        }

        .modal-close {
            width: 34px; height: 34px;
            border-radius: var(--radius-md);
            border: none;
            background: var(--vida-gray-100);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--vida-gray-500);
            transition: all 0.2s;
        }

        .modal-close:hover { background: var(--vida-gray-200); color: var(--vida-gray-700); }

        .modal-body { padding: 24px 26px; }
        .modal-footer {
            padding: 18px 26px;
            border-top: 1px solid var(--vida-gray-100);
            display: flex;
            justify-content: flex-end;
            gap: 10px;
            position: sticky;
            bottom: 0;
            background: var(--vida-white);
        }

        /* ===== FORMS ===== */
        .form-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 18px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }

        .form-group.full { grid-column: 1 / -1; }

        .form-label {
            font-size: 13px;
            font-weight: 600;
            color: var(--vida-gray-700);
        }

        .form-label .required { color: var(--vida-danger); margin-left: 2px; }

        .form-input, .form-select, .form-textarea {
            padding: 10px 14px;
            border: 1px solid var(--vida-gray-300);
            border-radius: var(--radius-md);
            font-size: 13px;
            outline: none;
            transition: all 0.2s;
            font-family: inherit;
            color: var(--vida-gray-900);
            background: var(--vida-white);
        }

        .form-input:focus, .form-select:focus, .form-textarea:focus {
            border-color: var(--vida-primary);
            box-shadow: 0 0 0 3px rgba(13,148,136,0.1);
        }

        .form-input::placeholder, .form-textarea::placeholder { color: var(--vida-gray-400); }

        .form-textarea { resize: vertical; min-height: 90px; }

        .form-select {
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%236b7280' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 12px center;
            padding-right: 32px;
        }

        .form-hint {
            font-size: 12px;
            color: var(--vida-gray-400);
        }

        .form-row { display: flex; gap: 10px; }
        .form-row .form-group { flex: 1; }

        /* ===== CHAT ===== */
        .chat-layout {
            display: flex;
            height: 620px;
        }

        .chat-sidebar {
            width: 300px;
            border-right: 1px solid var(--vida-gray-200);
            display: flex;
            flex-direction: column;
            background: var(--vida-gray-50);
        }

        .chat-search {
            padding: 14px;
            border-bottom: 1px solid var(--vida-gray-200);
        }

        .chat-search input {
            width: 100%;
            padding: 9px 12px 9px 34px;
            border: 1px solid var(--vida-gray-200);
            border-radius: var(--radius-lg);
            font-size: 13px;
            outline: none;
            font-family: inherit;
            background: var(--vida-white);
        }

        .chat-search input:focus { border-color: var(--vida-primary); }

        .chat-contacts { flex: 1; overflow-y: auto; }

        .chat-contact {
            display: flex;
            align-items: center;
            gap: 11px;
            padding: 12px 14px;
            cursor: pointer;
            transition: background 0.15s;
            border-bottom: 1px solid var(--vida-gray-100);
        }

        .chat-contact:hover { background: var(--vida-gray-100); }
        .chat-contact.active { background: var(--vida-primary-light); }

        .chat-contact-info { flex: 1; min-width: 0; }

        .chat-contact-name {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2px;
        }

        .chat-contact-name strong {
            font-weight: 600;
            font-size: 13px;
            color: var(--vida-gray-900);
        }

        .chat-contact-name span {
            font-size: 11px;
            color: var(--vida-gray-400);
        }

        .chat-contact-preview {
            font-size: 12px;
            color: var(--vida-gray-500);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .chat-contact-badge {
            background: var(--vida-primary);
            color: white;
            font-size: 10px;
            font-weight: 700;
            padding: 2px 6px;
            border-radius: 10px;
            min-width: 18px;
            text-align: center;
        }

        .chat-main {
            flex: 1;
            display: flex;
            flex-direction: column;
            background: var(--vida-white);
        }

        .chat-header-bar {
            padding: 14px 20px;
            border-bottom: 1px solid var(--vida-gray-100);
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .chat-messages-area {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 14px;
            background: var(--vida-gray-50);
        }

        .msg {
            max-width: 70%;
            padding: 12px 16px;
            border-radius: 16px;
            font-size: 13px;
            line-height: 1.5;
            animation: msgSlide 0.3s ease;
        }

        @keyframes msgSlide {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .msg-in {
            align-self: flex-start;
            background: var(--vida-white);
            border-bottom-left-radius: 4px;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--vida-gray-200);
        }

        .msg-out {
            align-self: flex-end;
            background: var(--vida-primary);
            color: white;
            border-bottom-right-radius: 4px;
        }

        .msg-time {
            font-size: 11px;
            margin-top: 5px;
            opacity: 0.65;
        }

        .msg-out .msg-time { opacity: 0.8; }

        .chat-input-bar {
            padding: 14px 20px;
            border-top: 1px solid var(--vida-gray-200);
            display: flex;
            gap: 10px;
            background: var(--vida-white);
        }

        .chat-input-bar input {
            flex: 1;
            padding: 10px 16px;
            border: 1px solid var(--vida-gray-200);
            border-radius: var(--radius-lg);
            font-size: 13px;
            outline: none;
            font-family: inherit;
        }

        .chat-input-bar input:focus { border-color: var(--vida-primary); }

        .chat-send-btn {
            width: 40px; height: 40px;
            border-radius: var(--radius-lg);
            border: none;
            background: var(--vida-primary);
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 0.2s;
            flex-shrink: 0;
        }

        .chat-send-btn:hover { background: var(--vida-primary-dark); }

        /* ===== CALENDAR ===== */
        .cal-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 1px;
            background: var(--vida-gray-200);
            border-radius: var(--radius-lg);
            overflow: hidden;
        }

        .cal-header-cell {
            background: var(--vida-gray-50);
            padding: 10px;
            text-align: center;
            font-size: 11px;
            font-weight: 700;
            color: var(--vida-gray-500);
            text-transform: uppercase;
        }

        .cal-cell {
            background: var(--vida-white);
            min-height: 90px;
            padding: 6px;
            position: relative;
        }

        .cal-cell.other { background: var(--vida-gray-50); color: var(--vida-gray-400); }
        .cal-cell.today { background: rgba(13,148,136,0.04); }

        .cal-date {
            font-size: 13px;
            font-weight: 600;
            margin-bottom: 4px;
        }

        .cal-cell.today .cal-date { color: var(--vida-primary); }

        .cal-event {
            font-size: 10px;
            padding: 3px 5px;
            border-radius: 3px;
            margin-bottom: 2px;
            cursor: pointer;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            font-weight: 500;
        }

        .cal-event.surgery { background: rgba(239,68,68,0.1); color: var(--vida-danger); }
        .cal-event.consult { background: rgba(13,148,136,0.1); color: var(--vida-primary); }
        .cal-event.travel { background: rgba(245,158,11,0.1); color: #b45309; }
        .cal-event.follow { background: rgba(16,185,129,0.1); color: var(--vida-success); }

        /* ===== PACKAGES ===== */
        .pkg-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .pkg-card {
            background: var(--vida-white);
            border-radius: var(--radius-xl);
            overflow: hidden;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--vida-gray-100);
            transition: all 0.2s;
        }

        .pkg-card:hover {
            box-shadow: var(--shadow-lg);
            transform: translateY(-4px);
        }

        .pkg-image {
            height: 150px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 42px;
            position: relative;
        }

        .pkg-image::after {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(0,0,0,0.3), transparent 60%);
        }

        .pkg-content { padding: 18px; }

        .pkg-hospital {
            font-size: 11px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 6px;
        }

        .pkg-title {
            font-size: 16px;
            font-weight: 700;
            color: var(--vida-gray-900);
            margin-bottom: 6px;
        }

        .pkg-loc {
            display: flex;
            align-items: center;
            gap: 5px;
            font-size: 12px;
            color: var(--vida-gray-500);
            margin-bottom: 12px;
        }

        .pkg-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
            margin-bottom: 14px;
        }

        .pkg-tag {
            background: var(--vida-gray-100);
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 600;
            color: var(--vida-gray-600);
        }

        .pkg-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 14px;
            border-top: 1px solid var(--vida-gray-100);
        }

        .pkg-price {
            font-size: 22px;
            font-weight: 800;
            color: var(--vida-primary);
            letter-spacing: -0.5px;
        }

        .pkg-price span {
            font-size: 12px;
            color: var(--vida-gray-400);
            font-weight: 500;
        }

        /* ===== DOCUMENTS ===== */
        .doc-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 16px;
        }

        .doc-card {
            background: var(--vida-white);
            border: 1px solid var(--vida-gray-200);
            border-radius: var(--radius-lg);
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.2s;
        }

        .doc-card:hover {
            border-color: var(--vida-primary);
            box-shadow: var(--shadow-md);
        }

        .doc-icon {
            width: 50px; height: 50px;
            border-radius: var(--radius-lg);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            margin: 0 auto 12px;
        }

        .doc-name {
            font-weight: 600;
            font-size: 13px;
            color: var(--vida-gray-900);
            margin-bottom: 4px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .doc-meta {
            font-size: 11px;
            color: var(--vida-gray-400);
        }

        /* ===== PROFILE / DETAIL ===== */
        .profile-layout {
            display: flex;
            gap: 24px;
        }

        .profile-sidebar {
            width: 300px;
            flex-shrink: 0;
        }

        .profile-main { flex: 1; }

        .profile-card-box {
            background: var(--vida-white);
            border-radius: var(--radius-xl);
            padding: 28px;
            text-align: center;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--vida-gray-100);
        }

        .profile-avatar-xl {
            width: 90px; height: 90px;
            border-radius: 50%;
            margin: 0 auto 16px;
            font-size: 32px;
        }

        .profile-name-xl {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 3px;
        }

        .profile-id-xl {
            font-size: 12px;
            color: var(--vida-gray-400);
            margin-bottom: 14px;
        }

        .detail-list {
            text-align: left;
            margin-top: 18px;
        }

        .detail-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid var(--vida-gray-100);
            font-size: 13px;
        }

        .detail-item:last-child { border-bottom: none; }
        .detail-item-label { color: var(--vida-gray-500); }
        .detail-item-value { font-weight: 600; color: var(--vida-gray-900); }

        /* ===== SECTIONS ===== */
        .section { display: none; }
        .section.active { display: block; animation: fadeIn 0.35s ease; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* ===== UTILITIES ===== */
        .flex { display: flex; }
        .flex-between { display: flex; justify-content: space-between; align-items: center; }
        .flex-center { display: flex; align-items: center; gap: 8px; }
        .gap-2 { gap: 8px; }
        .gap-3 { gap: 12px; }
        .gap-4 { gap: 16px; }
        .mb-0 { margin-bottom: 0; }
        .mb-2 { margin-bottom: 8px; }
        .mb-3 { margin-bottom: 12px; }
        .mb-4 { margin-bottom: 16px; }
        .mb-5 { margin-bottom: 20px; }
        .mt-2 { margin-top: 8px; }
        .mt-3 { margin-top: 12px; }
        .text-sm { font-size: 12px; }
        .text-xs { font-size: 11px; }
        .text-gray { color: var(--vida-gray-500); }
        .text-muted { color: var(--vida-gray-400); }
        .font-semibold { font-weight: 600; }
        .font-bold { font-weight: 700; }
        .w-full { width: 100%; }
        .truncate { white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
        .empty-state {
            padding: 60px 20px;
            text-align: center;
            color: var(--vida-gray-400);
        }
        .empty-state i {
            font-size: 48px;
            margin-bottom: 16px;
            opacity: 0.4;
        }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 1280px) {
            .stats-grid { grid-template-columns: repeat(2, 1fr); }
            .quick-actions { grid-template-columns: repeat(2, 1fr); }
            .grid-2, .grid-3 { grid-template-columns: 1fr; }
            .pkg-grid { grid-template-columns: repeat(2, 1fr); }
            .doc-grid { grid-template-columns: repeat(2, 1fr); }
        }

        @media (max-width: 768px) {
            .sidebar { transform: translateX(-100%); }
            .main-content { margin-left: 0; }
            .stats-grid { grid-template-columns: 1fr; }
            .quick-actions { grid-template-columns: 1fr; }
            .grid-4 { grid-template-columns: 1fr; }
            .pkg-grid { grid-template-columns: 1fr; }
            .doc-grid { grid-template-columns: 1fr; }
            .form-grid { grid-template-columns: 1fr; }
            .profile-layout { flex-direction: column; }
            .profile-sidebar { width: 100%; }
            .chat-layout { flex-direction: column; height: auto; }
            .chat-sidebar { width: 100%; border-right: none; border-bottom: 1px solid var(--vida-gray-200); }
            .header-search input { width: 200px; }
        }
    </style>
<base target="_blank">
</head>
<body>

    <!-- ===== SIDEBAR ===== -->
    <aside class="sidebar" id="sidebar">
        <div class="sidebar-header">
            <div class="sidebar-logo"><i class="fas fa-leaf"></i></div>
            <div class="sidebar-brand">
                Vidaluma
                <span>Medical Tourism CRM</span>
            </div>
        </div>

        <nav class="sidebar-nav">
            <div class="nav-section">Main</div>
            <a class="nav-item active" onclick="showSection('dashboard')">
                <i class="fas fa-chart-line"></i>
                <span>Dashboard</span>
            </a>
            <a class="nav-item" onclick="showSection('patients')">
                <i class="fas fa-users"></i>
                <span>Patients</span>
                <span class="nav-badge">24</span>
            </a>
            <a class="nav-item" onclick="showSection('pipeline')">
                <i class="fas fa-sitemap"></i>
                <span>Pipeline</span>
            </a>
            <a class="nav-item" onclick="showSection('packages')">
                <i class="fas fa-briefcase-medical"></i>
                <span>Treatment Packages</span>
            </a>

            <div class="nav-section">Operations</div>
            <a class="nav-item" onclick="showSection('calendar')">
                <i class="fas fa-calendar-alt"></i>
                <span>Calendar</span>
            </a>
            <a class="nav-item" onclick="showSection('communications')">
                <i class="fas fa-comments"></i>
                <span>Communications</span>
                <span class="nav-badge">5</span>
            </a>
            <a class="nav-item" onclick="showSection('documents')">
                <i class="fas fa-file-medical"></i>
                <span>Documents</span>
            </a>
            <a class="nav-item" onclick="showSection('finance')">
                <i class="fas fa-coins"></i>
                <span>Finance</span>
            </a>

            <div class="nav-section">Management</div>
            <a class="nav-item" onclick="showSection('hospitals')">
                <i class="fas fa-hospital"></i>
                <span>Partner Hospitals</span>
            </a>
            <a class="nav-item" onclick="showSection('reports')">
                <i class="fas fa-chart-bar"></i>
                <span>Reports & Analytics</span>
            </a>
            <a class="nav-item" onclick="showSection('settings')">
                <i class="fas fa-cog"></i>
                <span>Settings</span>
            </a>
        </nav>

        <div class="sidebar-footer">
            <div class="sidebar-user">
                <div class="sidebar-user-avatar">EW</div>
                <div class="sidebar-user-info">
                    <div class="sidebar-user-name">Elena Wang</div>
                    <div class="sidebar-user-role">Senior Coordinator</div>
                </div>
            </div>
        </div>
    </aside>

    <!-- ===== MAIN CONTENT ===== -->
    <main class="main-content">
        <!-- ===== HEADER ===== -->
        <header class="header">
            <div class="header-left">
                <div class="header-search">
                    <i class="fas fa-search"></i>
                    <input type="text" placeholder="Search patients, hospitals, treatments, documents...">
                </div>
            </div>
            <div class="header-right">
                <div class="header-lang">
                    <i class="fas fa-globe"></i>
                    <span>EN</span>
                    <i class="fas fa-chevron-down" style="font-size:10px"></i>
                </div>
                <button class="header-btn">
                    <i class="fas fa-bell"></i>
                    <span class="dot">3</span>
                </button>
                <button class="header-btn">
                    <i class="fas fa-envelope"></i>
                    <span class="dot">5</span>
                </button>
                <div class="header-btn" style="width:auto;padding:0 10px;gap:8px">
                    <div class="avatar avatar-sm" style="width:30px;height:30px;font-size:11px">EW</div>
                    <span style="font-size:13px;font-weight:600;color:var(--vida-gray-700)">Elena</span>
                    <i class="fas fa-chevron-down" style="font-size:10px;color:var(--vida-gray-400)"></i>
                </div>
            </div>
        </header>

        <!-- ===== CONTENT AREA ===== -->
        <div class="content">

            <!-- ===== DASHBOARD ===== -->
            <section id="dashboard" class="section active">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Dashboard</h1>
                        <p class="page-subtitle">Welcome back, Elena. Here is what is happening across your medical tourism operations in Sanya.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-download"></i> Export Report</button>
                    </div>
                </div>

                <!-- Quick Actions -->
                <div class="quick-actions">
                    <div class="quick-action" onclick="openModal('modalAddPatient')">
                        <div class="quick-action-icon" style="background:rgba(13,148,136,0.1);color:var(--vida-primary)">
                            <i class="fas fa-user-plus"></i>
                        </div>
                        <div class="quick-action-text">
                            <h4>New Patient</h4>
                            <span>Register international inquiry</span>
                        </div>
                    </div>
                    <div class="quick-action" onclick="openModal('modalAddPackage')">
                        <div class="quick-action-icon" style="background:rgba(16,185,129,0.1);color:var(--vida-success)">
                            <i class="fas fa-plus-circle"></i>
                        </div>
                        <div class="quick-action-text">
                            <h4>New Package</h4>
                            <span>Create treatment bundle</span>
                        </div>
                    </div>
                    <div class="quick-action" onclick="showSection('communications')">
                        <div class="quick-action-icon" style="background:rgba(245,158,11,0.1);color:#b45309">
                            <i class="fas fa-paper-plane"></i>
                        </div>
                        <div class="quick-action-text">
                            <h4>Send Message</h4>
                            <span>Quick patient communication</span>
                        </div>
                    </div>
                    <div class="quick-action" onclick="showSection('calendar')">
                        <div class="quick-action-icon" style="background:rgba(139,92,246,0.1);color:var(--vida-purple)">
                            <i class="fas fa-calendar-plus"></i>
                        </div>
                        <div class="quick-action-text">
                            <h4>Schedule</h4>
                            <span>Book appointment or travel</span>
                        </div>
                    </div>
                </div>

                <!-- Stats -->
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-header">
                            <div class="stat-icon teal"><i class="fas fa-users"></i></div>
                            <span class="stat-trend up"><i class="fas fa-arrow-up" style="font-size:10px"></i> 12%</span>
                        </div>
                        <div class="stat-value">156</div>
                        <div class="stat-label">Active Patients</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-header">
                            <div class="stat-icon green"><i class="fas fa-check-circle"></i></div>
                            <span class="stat-trend up"><i class="fas fa-arrow-up" style="font-size:10px"></i> 8%</span>
                        </div>
                        <div class="stat-value">42</div>
                        <div class="stat-label">Completed This Month</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-header">
                            <div class="stat-icon amber"><i class="fas fa-coins"></i></div>
                            <span class="stat-trend up"><i class="fas fa-arrow-up" style="font-size:10px"></i> 23%</span>
                        </div>
                        <div class="stat-value">$1.24M</div>
                        <div class="stat-label">Revenue This Month</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-header">
                            <div class="stat-icon purple"><i class="fas fa-hospital"></i></div>
                            <span class="stat-trend down"><i class="fas fa-arrow-down" style="font-size:10px"></i> 2%</span>
                        </div>
                        <div class="stat-value">18</div>
                        <div class="stat-label">Partner Hospitals</div>
                    </div>
                </div>

                <!-- Dashboard Grid -->
                <div class="grid-2">
                    <!-- Recent Patients -->
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-users" style="color:var(--vida-primary);margin-right:8px"></i>Recent Patients</h3>
                            <div class="page-actions">
                                <button class="btn btn-ghost btn-sm" onclick="showSection('patients')">View All <i class="fas fa-arrow-right" style="margin-left:4px;font-size:10px"></i></button>
                            </div>
                        </div>
                        <div class="table-wrap">
                            <table class="data-table">
                                <thead>
                                    <tr>
                                        <th>Patient</th>
                                        <th>Treatment</th>
                                        <th>Hospital</th>
                                        <th>Status</th>
                                        <th>Priority</th>
                                        <th style="text-align:right">Action</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar">AK</div>
                                                <div>
                                                    <div style="font-weight:600;font-size:13px">Anna Kovaleva</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">anna.k@mail.ru · Russia</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td>TCM Chronic Rehab</td>
                                        <td>Sanya TCM Hospital</td>
                                        <td><span class="badge badge-teal"><span class="badge-dot teal"></span> Travel Phase</span></td>
                                        <td><span class="priority priority-high">HIGH</span></td>
                                        <td style="text-align:right"><button class="btn btn-primary btn-sm" onclick="showPatientDetail('anna')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#f59e0b,#d97706)">DS</div>
                                                <div>
                                                    <div style="font-weight:600;font-size:13px">Dmitry Sokolov</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">d.sokolov@gmail.com · Russia</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td>Integrative Cardiac</td>
                                        <td>Hainan Boao Lecheng</td>
                                        <td><span class="badge badge-green"><span class="badge-dot green"></span> In Treatment</span></td>
                                        <td><span class="priority priority-medium">MED</span></td>
                                        <td style="text-align:right"><button class="btn btn-primary btn-sm" onclick="showPatientDetail('dmitry')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#8b5cf6,#7c3aed)">OI</div>
                                                <div>
                                                    <div style="font-weight:600;font-size:13px">Olga Ivanova</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">o.ivanova@yandex.ru · Kazakhstan</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td>IVF Treatment</td>
                                        <td>Sanya Women & Children</td>
                                        <td><span class="badge badge-purple"><span class="badge-dot purple"></span> Consultation</span></td>
                                        <td><span class="priority priority-high">HIGH</span></td>
                                        <td style="text-align:right"><button class="btn btn-primary btn-sm" onclick="showPatientDetail('olga')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#3b82f6,#2563eb)">MP</div>
                                                <div>
                                                    <div style="font-weight:600;font-size:13px">Mohammed Al-Rashid</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">m.alrashid@emirates.ae · UAE</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td>Anti-Aging Package</td>
                                        <td>Sanya TCM Hospital</td>
                                        <td><span class="badge badge-amber"><span class="badge-dot amber"></span> Scheduled</span></td>
                                        <td><span class="priority priority-low">LOW</span></td>
                                        <td style="text-align:right"><button class="btn btn-primary btn-sm" onclick="showPatientDetail('mohammed')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#ec4899,#db2777)">LP</div>
                                                <div>
                                                    <div style="font-weight:600;font-size:13px">Liudmila Petrova</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">l.petrova@bk.ru · Russia</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td>TCM Wellness Retreat</td>
                                        <td>Sanya TCM Hospital</td>
                                        <td><span class="badge badge-blue"><span class="badge-dot" style="background:#3b82f6"></span> New Inquiry</span></td>
                                        <td><span class="priority priority-medium">MED</span></td>
                                        <td style="text-align:right"><button class="btn btn-primary btn-sm" onclick="showPatientDetail('liudmila')">View</button></td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <!-- Activity Timeline -->
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-clock" style="color:var(--vida-primary);margin-right:8px"></i>Activity Timeline</h3>
                        </div>
                        <div class="card-body">
                            <div class="timeline">
                                <div class="timeline-item">
                                    <div class="timeline-dot teal"><i class="fas fa-plane"></i></div>
                                    <div class="timeline-content">
                                        <h4>Travel Arranged — Anna Kovaleva</h4>
                                        <p>Flight SU501 Moscow→Sanya confirmed. Arrival Jun 8, 14:30 CST. Airport pickup assigned.</p>
                                        <span class="timeline-time">2 hours ago · Elena Wang</span>
                                    </div>
                                </div>
                                <div class="timeline-item">
                                    <div class="timeline-dot green"><i class="fas fa-check"></i></div>
                                    <div class="timeline-content">
                                        <h4>Treatment Completed — Dmitry Sokolov</h4>
                                        <p>Cardiac rehabilitation program completed at Hainan Boao. Discharge summary issued.</p>
                                        <span class="timeline-time">5 hours ago · Dr. Chen Wei</span>
                                    </div>
                                </div>
                                <div class="timeline-item">
                                    <div class="timeline-dot amber"><i class="fas fa-file-medical"></i></div>
                                    <div class="timeline-content">
                                        <h4>Medical Records Received — Olga Ivanova</h4>
                                        <p>Pre-treatment fertility assessment uploaded. Dr. Li reviewing for IVF protocol.</p>
                                        <span class="timeline-time">Yesterday · Automated</span>
                                    </div>
                                </div>
                                <div class="timeline-item">
                                    <div class="timeline-dot purple"><i class="fas fa-handshake"></i></div>
                                    <div class="timeline-content">
                                        <h4>New Hospital Partnership</h4>
                                        <p>Added Hainan Boao Lecheng International Medical Tourism Pilot Zone as strategic partner.</p>
                                        <span class="timeline-time">2 days ago · Management</span>
                                    </div>
                                </div>
                                <div class="timeline-item">
                                    <div class="timeline-dot blue"><i class="fas fa-coins"></i></div>
                                    <div class="timeline-content">
                                        <h4>Payment Received — Mohammed Al-Rashid</h4>
                                        <p>Deposit $4,100 (50%) received via wire transfer. Booking confirmed.</p>
                                        <span class="timeline-time">3 days ago · Finance Team</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bottom Row -->
                <div class="grid-3" style="margin-top:20px">
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-globe-europe" style="color:var(--vida-primary);margin-right:8px"></i>Patient Sources</h3>
                        </div>
                        <div class="card-body">
                            <div style="display:flex;flex-direction:column;gap:12px">
                                <div>
                                    <div class="flex-between" style="margin-bottom:4px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇷🇺</span>Russia</span>
                                        <span style="font-size:13px;font-weight:700">78%</span>
                                    </div>
                                    <div style="height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                        <div style="width:78%;height:100%;background:var(--vida-primary);border-radius:3px"></div>
                                    </div>
                                    <span style="font-size:11px;color:var(--vida-gray-400)">122 patients · Primary market</span>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:4px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇰🇿</span>Kazakhstan</span>
                                        <span style="font-size:13px;font-weight:700">8%</span>
                                    </div>
                                    <div style="height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                        <div style="width:8%;height:100%;background:var(--vida-secondary);border-radius:3px"></div>
                                    </div>
                                    <span style="font-size:11px;color:var(--vida-gray-400)">12 patients</span>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:4px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇦🇪</span>UAE</span>
                                        <span style="font-size:13px;font-weight:700">5%</span>
                                    </div>
                                    <div style="height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                        <div style="width:5%;height:100%;background:var(--vida-warning);border-radius:3px"></div>
                                    </div>
                                    <span style="font-size:11px;color:var(--vida-gray-400)">8 patients</span>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:4px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇩🇪</span>Germany</span>
                                        <span style="font-size:13px;font-weight:700">4%</span>
                                    </div>
                                    <div style="height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                        <div style="width:4%;height:100%;background:var(--vida-purple);border-radius:3px"></div>
                                    </div>
                                    <span style="font-size:11px;color:var(--vida-gray-400)">6 patients</span>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:4px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🌍</span>Other</span>
                                        <span style="font-size:13px;font-weight:700">5%</span>
                                    </div>
                                    <div style="height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                        <div style="width:5%;height:100%;background:var(--vida-gray-400);border-radius:3px"></div>
                                    </div>
                                    <span style="font-size:11px;color:var(--vida-gray-400)">8 patients · 6 countries</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-chart-pie" style="color:var(--vida-primary);margin-right:8px"></i>Revenue by Category</h3>
                        </div>
                        <div class="card-body">
                            <div style="display:flex;flex-direction:column;gap:12px">
                                <div class="flex-between">
                                    <div class="flex-center">
                                        <div style="width:10px;height:10px;border-radius:50%;background:var(--vida-primary);margin-right:8px"></div>
                                        <span style="font-size:13px">TCM Chronic Rehab</span>
                                    </div>
                                    <span style="font-size:13px;font-weight:700">$482K</span>
                                </div>
                                <div class="flex-between">
                                    <div class="flex-center">
                                        <div style="width:10px;height:10px;border-radius:50%;background:var(--vida-success);margin-right:8px"></div>
                                        <span style="font-size:13px">Integrative Cardiac</span>
                                    </div>
                                    <span style="font-size:13px;font-weight:700">$310K</span>
                                </div>
                                <div class="flex-between">
                                    <div class="flex-center">
                                        <div style="width:10px;height:10px;border-radius:50%;background:var(--vida-warning);margin-right:8px"></div>
                                        <span style="font-size:13px">Anti-Aging & Wellness</span>
                                    </div>
                                    <span style="font-size:13px;font-weight:700">$248K</span>
                                </div>
                                <div class="flex-between">
                                    <div class="flex-center">
                                        <div style="width:10px;height:10px;border-radius:50%;background:var(--vida-purple);margin-right:8px"></div>
                                        <span style="font-size:13px">IVF & Fertility</span>
                                    </div>
                                    <span style="font-size:13px;font-weight:700">$124K</span>
                                </div>
                                <div class="flex-between">
                                    <div class="flex-center">
                                        <div style="width:10px;height:10px;border-radius:50%;background:var(--vida-rose);margin-right:8px"></div>
                                        <span style="font-size:13px">Dental & Cosmetic</span>
                                    </div>
                                    <span style="font-size:13px;font-weight:700">$76K</span>
                                </div>
                            </div>
                            <div style="margin-top:16px;padding-top:14px;border-top:1px solid var(--vida-gray-100)">
                                <div class="flex-between">
                                    <span style="font-size:13px;font-weight:600">Total</span>
                                    <span style="font-size:15px;font-weight:800;color:var(--vida-primary)">$1.24M</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-bolt" style="color:var(--vida-primary);margin-right:8px"></i>Tasks & Alerts</h3>
                        </div>
                        <div class="card-body" style="padding:12px 0">
                            <div style="padding:12px 20px;border-bottom:1px solid var(--vida-gray-100);display:flex;align-items:flex-start;gap:10px">
                                <div style="width:8px;height:8px;border-radius:50%;background:var(--vida-danger);margin-top:5px;flex-shrink:0"></div>
                                <div>
                                    <div style="font-weight:600;font-size:13px">Visa support letter pending</div>
                                    <div style="font-size:12px;color:var(--vida-gray-500)">Olga Ivanova (KZ) — needs medical visa for 14-day IVF program</div>
                                    <div style="font-size:11px;color:var(--vida-danger);margin-top:2px">Due in 4 hours</div>
                                </div>
                            </div>
                            <div style="padding:12px 20px;border-bottom:1px solid var(--vida-gray-100);display:flex;align-items:flex-start;gap:10px">
                                <div style="width:8px;height:8px;border-radius:50%;background:var(--vida-warning);margin-top:5px;flex-shrink:0"></div>
                                <div>
                                    <div style="font-weight:600;font-size:13px">Payment follow-up required</div>
                                    <div style="font-size:12px;color:var(--vida-gray-500)">Mohammed Al-Rashid (UAE) — balance $4,100 due before arrival</div>
                                    <div style="font-size:11px;color:var(--vida-warning);margin-top:2px">Due in 2 days</div>
                                </div>
                            </div>
                            <div style="padding:12px 20px;border-bottom:1px solid var(--vida-gray-100);display:flex;align-items:flex-start;gap:10px">
                                <div style="width:8px;height:8px;border-radius:50%;background:var(--vida-primary);margin-top:5px;flex-shrink:0"></div>
                                <div>
                                    <div style="font-weight:600;font-size:13px">Interpreter assignment needed</div>
                                    <div style="font-size:12px;color:var(--vida-gray-500)">Liudmila Petrova (RU) — Russian→Chinese medical interpreter for Jun 12</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-top:2px">Due in 5 days</div>
                                </div>
                            </div>
                            <div style="padding:12px 20px;display:flex;align-items:flex-start;gap:10px">
                                <div style="width:8px;height:8px;border-radius:50%;background:var(--vida-success);margin-top:5px;flex-shrink:0"></div>
                                <div>
                                    <div style="font-weight:600;font-size:13px">Post-care survey pending</div>
                                    <div style="font-size:12px;color:var(--vida-gray-500)">Sergey Volkov (RU) — 30-day follow-up survey not yet completed</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-top:2px">Overdue by 2 days</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== PATIENTS ===== -->
            <section id="patients" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Patients</h1>
                        <p class="page-subtitle">Manage all international patient inquiries, treatments, and post-care journeys.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-filter"></i> Filter</button>
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-download"></i> Export</button>
                        <button class="btn btn-primary" onclick="openModal('modalAddPatient')"><i class="fas fa-user-plus"></i> Add New Patient</button>
                    </div>
                </div>

                <div class="card">
                    <div class="tabs">
                        <button class="tab active" onclick="switchTab(this,'tabAllPatients')">All Patients <span style="color:var(--vida-gray-400);margin-left:4px">(156)</span></button>
                        <button class="tab" onclick="switchTab(this,'tabActivePatients')">Active <span style="color:var(--vida-gray-400);margin-left:4px">(24)</span></button>
                        <button class="tab" onclick="switchTab(this,'tabCompletedPatients')">Completed <span style="color:var(--vida-gray-400);margin-left:4px">(89)</span></button>
                        <button class="tab" onclick="switchTab(this,'tabArchivedPatients')">Archived <span style="color:var(--vida-gray-400);margin-left:4px">(43)</span></button>
                    </div>

                    <div id="tabAllPatients" class="tab-pane active">
                        <div class="table-wrap">
                            <table class="data-table">
                                <thead>
                                    <tr>
                                        <th>Patient ID</th>
                                        <th>Name / Contact</th>
                                        <th>Nationality</th>
                                        <th>Treatment</th>
                                        <th>Hospital</th>
                                        <th>Coordinator</th>
                                        <th>Status</th>
                                        <th>Priority</th>
                                        <th style="text-align:right">Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td><strong style="color:var(--vida-primary)">#VD-2026-0142</strong></td>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar">AK</div>
                                                <div>
                                                    <div style="font-weight:600">Anna Kovaleva</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">anna.k@mail.ru · +7-916-555-0142</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td><span style="margin-right:4px">🇷🇺</span>Russia</td>
                                        <td>TCM Chronic Rehab (14-day)</td>
                                        <td>Sanya TCM Hospital</td>
                                        <td>Elena Wang</td>
                                        <td><span class="badge badge-teal"><span class="badge-dot teal"></span> Travel Phase</span></td>
                                        <td><span class="priority priority-high">HIGH</span></td>
                                        <td style="text-align:right"><button class="btn btn-ghost btn-sm" onclick="showPatientDetail('anna')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td><strong style="color:var(--vida-primary)">#VD-2026-0139</strong></td>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#f59e0b,#d97706)">DS</div>
                                                <div>
                                                    <div style="font-weight:600">Dmitry Sokolov</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">d.sokolov@gmail.com · +7-903-555-0139</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td><span style="margin-right:4px">🇷🇺</span>Russia</td>
                                        <td>Integrative Cardiac (21-day)</td>
                                        <td>Hainan Boao Lecheng</td>
                                        <td>Elena Wang</td>
                                        <td><span class="badge badge-green"><span class="badge-dot green"></span> In Treatment</span></td>
                                        <td><span class="priority priority-medium">MED</span></td>
                                        <td style="text-align:right"><button class="btn btn-ghost btn-sm" onclick="showPatientDetail('dmitry')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td><strong style="color:var(--vida-primary)">#VD-2026-0135</strong></td>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#8b5cf6,#7c3aed)">OI</div>
                                                <div>
                                                    <div style="font-weight:600">Olga Ivanova</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">o.ivanova@yandex.kz · +7-777-555-0135</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td><span style="margin-right:4px">🇰🇿</span>Kazakhstan</td>
                                        <td>IVF Treatment (3 cycles)</td>
                                        <td>Sanya Women & Children</td>
                                        <td>Li Wei</td>
                                        <td><span class="badge badge-purple"><span class="badge-dot purple"></span> Consultation</span></td>
                                        <td><span class="priority priority-high">HIGH</span></td>
                                        <td style="text-align:right"><button class="btn btn-ghost btn-sm" onclick="showPatientDetail('olga')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td><strong style="color:var(--vida-primary)">#VD-2026-0128</strong></td>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#3b82f6,#2563eb)">MA</div>
                                                <div>
                                                    <div style="font-weight:600">Mohammed Al-Rashid</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">m.alrashid@emirates.ae · +971-50-555-0128</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td><span style="margin-right:4px">🇦🇪</span>UAE</td>
                                        <td>Anti-Aging & Regeneration (10-day)</td>
                                        <td>Sanya TCM Hospital</td>
                                        <td>Zhang Min</td>
                                        <td><span class="badge badge-amber"><span class="badge-dot amber"></span> Scheduled</span></td>
                                        <td><span class="priority priority-low">LOW</span></td>
                                        <td style="text-align:right"><button class="btn btn-ghost btn-sm" onclick="showPatientDetail('mohammed')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td><strong style="color:var(--vida-primary)">#VD-2026-0121</strong></td>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#ec4899,#db2777)">LP</div>
                                                <div>
                                                    <div style="font-weight:600">Liudmila Petrova</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">l.petrova@bk.ru · +7-925-555-0121</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td><span style="margin-right:4px">🇷🇺</span>Russia</td>
                                        <td>TCM Wellness Retreat (7-day)</td>
                                        <td>Sanya TCM Hospital</td>
                                        <td>Unassigned</td>
                                        <td><span class="badge badge-blue"><span class="badge-dot" style="background:#3b82f6"></span> New Inquiry</span></td>
                                        <td><span class="priority priority-medium">MED</span></td>
                                        <td style="text-align:right"><button class="btn btn-ghost btn-sm" onclick="showPatientDetail('liudmila')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td><strong style="color:var(--vida-primary)">#VD-2026-0115</strong></td>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#10b981,#059669)">SV</div>
                                                <div>
                                                    <div style="font-weight:600">Sergey Volkov</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">s.volkov@mail.ru · +7-915-555-0115</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td><span style="margin-right:4px">🇷🇺</span>Russia</td>
                                        <td>TCM Chronic Rehab (21-day)</td>
                                        <td>Sanya TCM Hospital</td>
                                        <td>Elena Wang</td>
                                        <td><span class="badge badge-green"><span class="badge-dot green"></span> Post-Care</span></td>
                                        <td><span class="priority priority-medium">MED</span></td>
                                        <td style="text-align:right"><button class="btn btn-ghost btn-sm" onclick="showPatientDetail('sergey')">View</button></td>
                                    </tr>
                                    <tr>
                                        <td><strong style="color:var(--vida-primary)">#VD-2026-0108</strong></td>
                                        <td>
                                            <div style="display:flex;align-items:center;gap:10px">
                                                <div class="avatar" style="background:linear-gradient(135deg,#f43f5e,#e11d48)">NK</div>
                                                <div>
                                                    <div style="font-weight:600">Natalia Kuznetsova</div>
                                                    <div style="font-size:11px;color:var(--vida-gray-400)">n.kuznetsova@gmail.com · +7-926-555-0108</div>
                                                </div>
                                            </div>
                                        </td>
                                        <td><span style="margin-right:4px">🇷🇺</span>Russia</td>
                                        <td>Dental Implants (Full Set)</td>
                                        <td>Sanya Stomatology Center</td>
                                        <td>Li Wei</td>
                                        <td><span class="badge badge-amber"><span class="badge-dot amber"></span> Scheduled</span></td>
                                        <td><span class="priority priority-low">LOW</span></td>
                                        <td style="text-align:right"><button class="btn btn-ghost btn-sm" onclick="showPatientDetail('natalia')">View</button></td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <div id="tabActivePatients" class="tab-pane">
                        <div class="empty-state">
                            <i class="fas fa-user-check"></i>
                            <p style="font-weight:600;color:var(--vida-gray-600)">24 active patients</p>
                            <p style="font-size:13px">Patients currently in treatment pipeline (Inquiry through Post-Care)</p>
                        </div>
                    </div>
                    <div id="tabCompletedPatients" class="tab-pane">
                        <div class="empty-state">
                            <i class="fas fa-check-circle"></i>
                            <p style="font-weight:600;color:var(--vida-gray-600)">89 completed treatments</p>
                            <p style="font-size:13px">Patients who have finished their full treatment and post-care cycle</p>
                        </div>
                    </div>
                    <div id="tabArchivedPatients" class="tab-pane">
                        <div class="empty-state">
                            <i class="fas fa-archive"></i>
                            <p style="font-weight:600;color:var(--vida-gray-600)">43 archived records</p>
                            <p style="font-size:13px">Inactive or cancelled patient records retained per PIPL requirements</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== PIPELINE ===== -->
            <section id="pipeline" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Patient Pipeline</h1>
                        <p class="page-subtitle">Track international patient journey from initial inquiry through post-care follow-up.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-filter"></i> Filter</button>
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-columns"></i> Customize</button>
                    </div>
                </div>

                <div class="pipeline-wrap">
                    <div class="pipeline">
                        <!-- New Inquiry -->
                        <div class="pipeline-col">
                            <div class="pipeline-header">
                                <div class="pipeline-title">
                                    <span style="width:8px;height:8px;border-radius:50%;background:var(--vida-primary);display:inline-block;margin-right:6px"></span>
                                    New Inquiry
                                </div>
                                <span class="pipeline-count">12</span>
                            </div>
                            <div class="pipeline-cards">
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Liudmila Petrova</span>
                                        <span class="priority priority-medium" style="font-size:10px">MED</span>
                                    </div>
                                    <div class="pipeline-card-desc">TCM Wellness Retreat · 7-day · Sanya TCM Hospital</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-globe" style="margin-right:4px"></i> Russia · WhatsApp inquiry</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-gray-400)">—</div>
                                        </div>
                                        <span class="pipeline-value">$1,800</span>
                                    </div>
                                </div>
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Ivan Smirnov</span>
                                        <span class="priority priority-high" style="font-size:10px">HIGH</span>
                                    </div>
                                    <div class="pipeline-card-desc">Integrative Cardiac · 21-day · Hainan Boao</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-globe" style="margin-right:4px"></i> Russia · Website form</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-primary)">EW</div>
                                        </div>
                                        <span class="pipeline-value">$8,500</span>
                                    </div>
                                </div>
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Fatima Al-Hassan</span>
                                        <span class="priority priority-medium" style="font-size:10px">MED</span>
                                    </div>
                                    <div class="pipeline-card-desc">TCM Chronic Rehab · 14-day · Sanya TCM</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-globe" style="margin-right:4px"></i> UAE · Email</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-primary)">EW</div>
                                        </div>
                                        <span class="pipeline-value">$3,200</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Consultation -->
                        <div class="pipeline-col">
                            <div class="pipeline-header">
                                <div class="pipeline-title">
                                    <span style="width:8px;height:8px;border-radius:50%;background:var(--vida-purple);display:inline-block;margin-right:6px"></span>
                                    Consultation
                                </div>
                                <span class="pipeline-count">8</span>
                            </div>
                            <div class="pipeline-cards">
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Olga Ivanova</span>
                                        <span class="priority priority-high" style="font-size:10px">HIGH</span>
                                    </div>
                                    <div class="pipeline-card-desc">IVF Treatment · 3 cycles · Sanya Women & Children</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-video" style="margin-right:4px"></i> Tele-consult Jun 5 · Dr. Li</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-purple)">LW</div>
                                        </div>
                                        <span class="pipeline-value">$12,800</span>
                                    </div>
                                </div>
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Klaus Mueller</span>
                                        <span class="priority priority-medium" style="font-size:10px">MED</span>
                                    </div>
                                    <div class="pipeline-card-desc">Spine Rehabilitation · 14-day · Sanya TCM</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-video" style="margin-right:4px"></i> Tele-consult Jun 6 · Dr. Zhang</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-purple)">ZM</div>
                                        </div>
                                        <span class="pipeline-value">$4,500</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Quoted -->
                        <div class="pipeline-col">
                            <div class="pipeline-header">
                                <div class="pipeline-title">
                                    <span style="width:8px;height:8px;border-radius:50%;background:#3b82f6;display:inline-block;margin-right:6px"></span>
                                    Quoted
                                </div>
                                <span class="pipeline-count">5</span>
                            </div>
                            <div class="pipeline-cards">
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Elena Voronova</span>
                                        <span class="priority priority-high" style="font-size:10px">HIGH</span>
                                    </div>
                                    <div class="pipeline-card-desc">TCM Chronic Rehab · 21-day · Sanya TCM</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-file-invoice" style="margin-right:4px"></i> Quote sent Jun 1 · Awaiting response</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-primary)">EW</div>
                                        </div>
                                        <span class="pipeline-value">$4,800</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Booked -->
                        <div class="pipeline-col">
                            <div class="pipeline-header">
                                <div class="pipeline-title">
                                    <span style="width:8px;height:8px;border-radius:50%;background:var(--vida-warning);display:inline-block;margin-right:6px"></span>
                                    Booked
                                </div>
                                <span class="pipeline-count">4</span>
                            </div>
                            <div class="pipeline-cards">
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Mohammed Al-Rashid</span>
                                        <span class="priority priority-low" style="font-size:10px">LOW</span>
                                    </div>
                                    <div class="pipeline-card-desc">Anti-Aging · 10-day · Sanya TCM</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-coins" style="margin-right:4px"></i> Deposit $4,100 received · Balance due</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-warning)">ZM</div>
                                        </div>
                                        <span class="pipeline-value">$8,200</span>
                                    </div>
                                </div>
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Natalia Kuznetsova</span>
                                        <span class="priority priority-low" style="font-size:10px">LOW</span>
                                    </div>
                                    <div class="pipeline-card-desc">Dental Implants · Full Set · Sanya Stomatology</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-coins" style="margin-right:4px"></i> Full payment received</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-warning)">LW</div>
                                        </div>
                                        <span class="pipeline-value">$6,500</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Travel -->
                        <div class="pipeline-col">
                            <div class="pipeline-header">
                                <div class="pipeline-title">
                                    <span style="width:8px;height:8px;border-radius:50%;background:var(--vida-secondary);display:inline-block;margin-right:6px"></span>
                                    Travel
                                </div>
                                <span class="pipeline-count">3</span>
                            </div>
                            <div class="pipeline-cards">
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Anna Kovaleva</span>
                                        <span class="priority priority-high" style="font-size:10px">HIGH</span>
                                    </div>
                                    <div class="pipeline-card-desc">TCM Chronic Rehab · 14-day · Sanya TCM</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-plane" style="margin-right:4px"></i> Arrival Jun 8 · SU501 Moscow→Sanya</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-primary)">EW</div>
                                            <div class="avatar avatar-sm" style="background:var(--vida-purple)">LW</div>
                                        </div>
                                        <span class="pipeline-value">$3,200</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- In Treatment -->
                        <div class="pipeline-col">
                            <div class="pipeline-header">
                                <div class="pipeline-title">
                                    <span style="width:8px;height:8px;border-radius:50%;background:var(--vida-success);display:inline-block;margin-right:6px"></span>
                                    In Treatment
                                </div>
                                <span class="pipeline-count">5</span>
                            </div>
                            <div class="pipeline-cards">
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Dmitry Sokolov</span>
                                        <span class="priority priority-medium" style="font-size:10px">MED</span>
                                    </div>
                                    <div class="pipeline-card-desc">Integrative Cardiac · Day 12/21 · Boao Lecheng</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-heartbeat" style="margin-right:4px"></i> BP stable · Acupuncture daily · Herbal Rx</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-success)">EW</div>
                                        </div>
                                        <span class="pipeline-value">$8,500</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Post-Care -->
                        <div class="pipeline-col">
                            <div class="pipeline-header">
                                <div class="pipeline-title">
                                    <span style="width:8px;height:8px;border-radius:50%;background:var(--vida-gray-400);display:inline-block;margin-right:6px"></span>
                                    Post-Care
                                </div>
                                <span class="pipeline-count">6</span>
                            </div>
                            <div class="pipeline-cards">
                                <div class="pipeline-card">
                                    <div class="pipeline-card-header">
                                        <span class="pipeline-card-title">Sergey Volkov</span>
                                        <span class="priority priority-medium" style="font-size:10px">MED</span>
                                    </div>
                                    <div class="pipeline-card-desc">TCM Chronic Rehab · Completed May 10</div>
                                    <div style="font-size:11px;color:var(--vida-gray-400);margin-bottom:8px"><i class="fas fa-clipboard-check" style="margin-right:4px"></i> 30-day follow-up survey pending</div>
                                    <div class="pipeline-card-meta">
                                        <div class="pipeline-avatars">
                                            <div class="avatar avatar-sm" style="background:var(--vida-gray-400)">EW</div>
                                        </div>
                                        <span class="pipeline-value">$4,800</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== PACKAGES ===== -->
            <section id="packages" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Treatment Packages</h1>
                        <p class="page-subtitle">Curated medical tourism bundles aligned with Sanya's TCM and integrative medicine offerings.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-filter"></i> Filter</button>
                        <button class="btn btn-primary" onclick="openModal('modalAddPackage')"><i class="fas fa-plus"></i> New Package</button>
                    </div>
                </div>

                <div class="pkg-grid">
                    <div class="pkg-card">
                        <div class="pkg-image" style="background:linear-gradient(135deg,#0d9488,#14b8a6)">
                            <i class="fas fa-spa"></i>
                        </div>
                        <div class="pkg-content">
                            <div class="pkg-hospital" style="color:var(--vida-primary)">Sanya TCM Hospital</div>
                            <div class="pkg-title">7-Day Health Relaxation</div>
                            <div class="pkg-loc"><i class="fas fa-map-marker-alt"></i> Sanya, Hainan, China</div>
                            <div class="pkg-tags">
                                <span class="pkg-tag">Acupuncture</span>
                                <span class="pkg-tag">Tuina</span>
                                <span class="pkg-tag">Herbal Bath</span>
                                <span class="pkg-tag">Tai Chi</span>
                            </div>
                            <div class="pkg-footer">
                                <div class="pkg-price">$1,800 <span>starting</span></div>
                                <button class="btn btn-primary btn-sm">Details</button>
                            </div>
                        </div>
                    </div>

                    <div class="pkg-card">
                        <div class="pkg-image" style="background:linear-gradient(135deg,#059669,#10b981)">
                            <i class="fas fa-heartbeat"></i>
                        </div>
                        <div class="pkg-content">
                            <div class="pkg-hospital" style="color:var(--vida-success)">Sanya TCM Hospital</div>
                            <div class="pkg-title">14-Day Chronic Disease Rehab</div>
                            <div class="pkg-loc"><i class="fas fa-map-marker-alt"></i> Sanya, Hainan, China</div>
                            <div class="pkg-tags">
                                <span class="pkg-tag">TCM Diagnosis</span>
                                <span class="pkg-tag">Herbal Medicine</span>
                                <span class="pkg-tag">Moxibustion</span>
                                <span class="pkg-tag">Dietary Therapy</span>
                                <span class="pkg-tag">Solar Therapy</span>
                            </div>
                            <div class="pkg-footer">
                                <div class="pkg-price">$3,200 <span>starting</span></div>
                                <button class="btn btn-primary btn-sm">Details</button>
                            </div>
                        </div>
                    </div>

                    <div class="pkg-card">
                        <div class="pkg-image" style="background:linear-gradient(135deg,#7c3aed,#8b5cf6)">
                            <i class="fas fa-baby"></i>
                        </div>
                        <div class="pkg-content">
                            <div class="pkg-hospital" style="color:var(--vida-purple)">Sanya Women & Children</div>
                            <div class="pkg-title">IVF & Fertility Package</div>
                            <div class="pkg-loc"><i class="fas fa-map-marker-alt"></i> Sanya, Hainan, China</div>
                            <div class="pkg-tags">
                                <span class="pkg-tag">3 Cycles</span>
                                <span class="pkg-tag">14-Day Stay</span>
                                <span class="pkg-tag">Counseling</span>
                                <span class="pkg-tag">Accommodation</span>
                            </div>
                            <div class="pkg-footer">
                                <div class="pkg-price">$12,800 <span>starting</span></div>
                                <button class="btn btn-primary btn-sm">Details</button>
                            </div>
                        </div>
                    </div>

                    <div class="pkg-card">
                        <div class="pkg-image" style="background:linear-gradient(135deg,#d97706,#f59e0b)">
                            <i class="fas fa-tooth"></i>
                        </div>
                        <div class="pkg-content">
                            <div class="pkg-hospital" style="color:#b45309">Sanya Stomatology Center</div>
                            <div class="pkg-title">Dental Implants (Full Set)</div>
                            <div class="pkg-loc"><i class="fas fa-map-marker-alt"></i> Sanya, Hainan, China</div>
                            <div class="pkg-tags">
                                <span class="pkg-tag">Full Arch</span>
                                <span class="pkg-tag">5-Day Stay</span>
                                <span class="pkg-tag">Follow-up</span>
                                <span class="pkg-tag">City Tour</span>
                            </div>
                            <div class="pkg-footer">
                                <div class="pkg-price">$6,500 <span>starting</span></div>
                                <button class="btn btn-primary btn-sm">Details</button>
                            </div>
                        </div>
                    </div>

                    <div class="pkg-card">
                        <div class="pkg-image" style="background:linear-gradient(135deg,#dc2626,#ef4444)">
                            <i class="fas fa-heart-pulse"></i>
                        </div>
                        <div class="pkg-content">
                            <div class="pkg-hospital" style="color:var(--vida-danger)">Hainan Boao Lecheng</div>
                            <div class="pkg-title">Integrative Cardiac Recovery</div>
                            <div class="pkg-loc"><i class="fas fa-map-marker-alt"></i> Boao, Hainan, China</div>
                            <div class="pkg-tags">
                                <span class="pkg-tag">21-Day Program</span>
                                <span class="pkg-tag">TCM + Western</span>
                                <span class="pkg-tag">ECG Monitoring</span>
                                <span class="pkg-tag">VIP Suite</span>
                            </div>
                            <div class="pkg-footer">
                                <div class="pkg-price">$8,500 <span>starting</span></div>
                                <button class="btn btn-primary btn-sm">Details</button>
                            </div>
                        </div>
                    </div>

                    <div class="pkg-card">
                        <div class="pkg-image" style="background:linear-gradient(135deg,#ec4899,#db2777)">
                            <i class="fas fa-magic"></i>
                        </div>
                        <div class="pkg-content">
                            <div class="pkg-hospital" style="color:#db2777">Sanya TCM Hospital</div>
                            <div class="pkg-title">Anti-Aging & Regeneration</div>
                            <div class="pkg-loc"><i class="fas fa-map-marker-alt"></i> Sanya, Hainan, China</div>
                            <div class="pkg-tags">
                                <span class="pkg-tag">10-Day Program</span>
                                <span class="pkg-tag">Stem Cell Consult</span>
                                <span class="pkg-tag">Cosmetic TCM</span>
                                <span class="pkg-tag">Luxury Hotel</span>
                            </div>
                            <div class="pkg-footer">
                                <div class="pkg-price">$6,200 <span>starting</span></div>
                                <button class="btn btn-primary btn-sm">Details</button>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== CALENDAR ===== -->
            <section id="calendar" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Calendar</h1>
                        <p class="page-subtitle">Schedule consultations, treatments, travel arrangements, and follow-ups. All times in CST (UTC+8).</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-chevron-left"></i></button>
                        <button class="btn btn-secondary btn-sm">Today</button>
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-chevron-right"></i></button>
                        <button class="btn btn-primary btn-sm" style="margin-left:8px"><i class="fas fa-plus"></i> New Event</button>
                    </div>
                </div>

                <div class="card">
                    <div style="padding:16px 24px;border-bottom:1px solid var(--vida-gray-100);display:flex;justify-content:space-between;align-items:center">
                        <h3 style="font-size:16px;font-weight:700">June 2026</h3>
                        <div style="display:flex;gap:12px;font-size:12px">
                            <div class="flex-center"><span style="width:8px;height:8px;border-radius:50%;background:var(--vida-danger);margin-right:6px"></span>Surgery</div>
                            <div class="flex-center"><span style="width:8px;height:8px;border-radius:50%;background:var(--vida-primary);margin-right:6px"></span>Consultation</div>
                            <div class="flex-center"><span style="width:8px;height:8px;border-radius:50%;background:var(--vida-warning);margin-right:6px"></span>Travel</div>
                            <div class="flex-center"><span style="width:8px;height:8px;border-radius:50%;background:var(--vida-success);margin-right:6px"></span>Follow-up</div>
                        </div>
                    </div>
                    <div style="padding:20px">
                        <div class="cal-grid">
                            <div class="cal-header-cell">Sun</div>
                            <div class="cal-header-cell">Mon</div>
                            <div class="cal-header-cell">Tue</div>
                            <div class="cal-header-cell">Wed</div>
                            <div class="cal-header-cell">Thu</div>
                            <div class="cal-header-cell">Fri</div>
                            <div class="cal-header-cell">Sat</div>

                            <div class="cal-cell other"><div class="cal-date">31</div></div>
                            <div class="cal-cell"><div class="cal-date">1</div></div>
                            <div class="cal-cell"><div class="cal-date">2</div><div class="cal-event consult">Olga Ivanova — Tele-consult 14:00 CST</div></div>
                            <div class="cal-cell"><div class="cal-date">3</div></div>
                            <div class="cal-cell"><div class="cal-date">4</div><div class="cal-event travel">Anna Kovaleva — Arrival SU501 14:30</div></div>
                            <div class="cal-cell"><div class="cal-date">5</div></div>
                            <div class="cal-cell"><div class="cal-date">6</div></div>
                            <div class="cal-cell"><div class="cal-date">7</div></div>
                            <div class="cal-cell"><div class="cal-date">8</div><div class="cal-event surgery">Dmitry Sokolov — Cardiac Procedure</div></div>
                            <div class="cal-cell today"><div class="cal-date" style="color:var(--vida-primary)">9</div><div class="cal-event follow">Sergey Volkov — 30-day Checkup</div></div>
                            <div class="cal-cell"><div class="cal-date">10</div></div>
                            <div class="cal-cell"><div class="cal-date">11</div><div class="cal-event consult">Ivan Smirnov — Tele-consult 10:00 CST</div></div>
                            <div class="cal-cell"><div class="cal-date">12</div></div>
                            <div class="cal-cell"><div class="cal-date">13</div></div>
                            <div class="cal-cell"><div class="cal-date">14</div></div>
                            <div class="cal-cell"><div class="cal-date">15</div><div class="cal-event surgery">Anna Kovaleva — TCM Assessment Start</div></div>
                            <div class="cal-cell"><div class="cal-date">16</div></div>
                            <div class="cal-cell"><div class="cal-date">17</div><div class="cal-event travel">Mohammed Al-Rashid — Arrival EK386 09:15</div></div>
                            <div class="cal-cell"><div class="cal-date">18</div></div>
                            <div class="cal-cell"><div class="cal-date">19</div><div class="cal-event follow">Dmitry Sokolov — Post-surgery Review</div></div>
                            <div class="cal-cell"><div class="cal-date">20</div></div>
                            <div class="cal-cell"><div class="cal-date">21</div></div>
                            <div class="cal-cell"><div class="cal-date">22</div></div>
                            <div class="cal-cell"><div class="cal-date">23</div><div class="cal-event surgery">Klaus Mueller — Spine Procedure</div></div>
                            <div class="cal-cell"><div class="cal-date">24</div></div>
                            <div class="cal-cell"><div class="cal-date">25</div></div>
                            <div class="cal-cell"><div class="cal-date">26</div><div class="cal-event travel">Elena Voronova — Arrival CZ679 16:20</div></div>
                            <div class="cal-cell"><div class="cal-date">27</div></div>
                            <div class="cal-cell"><div class="cal-date">28</div></div>
                            <div class="cal-cell"><div class="cal-date">29</div></div>
                            <div class="cal-cell"><div class="cal-date">30</div><div class="cal-event consult">Liudmila Petrova — Final Consult 11:00</div></div>
                            <div class="cal-cell other"><div class="cal-date">1</div></div>
                            <div class="cal-cell other"><div class="cal-date">2</div></div>
                            <div class="cal-cell other"><div class="cal-date">3</div></div>
                            <div class="cal-cell other"><div class="cal-date">4</div></div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== COMMUNICATIONS ===== -->
            <section id="communications" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Communications</h1>
                        <p class="page-subtitle">Unified messaging hub for patient coordination across WhatsApp, WeChat, email, and phone.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-cog"></i> Settings</button>
                    </div>
                </div>

                <div class="card" style="overflow:hidden">
                    <div class="chat-layout">
                        <div class="chat-sidebar">
                            <div class="chat-search">
                                <input type="text" placeholder="Search conversations...">
                            </div>
                            <div class="chat-contacts">
                                <div class="chat-contact active">
                                    <div class="avatar" style="width:40px;height:40px;font-size:13px">AK</div>
                                    <div class="chat-contact-info">
                                        <div class="chat-contact-name"><strong>Anna Kovaleva</strong><span>2m ago</span></div>
                                        <div class="chat-contact-preview">Flight confirmed for tomorrow. Thank you!</div>
                                    </div>
                                    <span class="chat-contact-badge">2</span>
                                </div>
                                <div class="chat-contact">
                                    <div class="avatar" style="width:40px;height:40px;font-size:13px;background:linear-gradient(135deg,#f59e0b,#d97706)">DS</div>
                                    <div class="chat-contact-info">
                                        <div class="chat-contact-name"><strong>Dmitry Sokolov</strong><span>1h ago</span></div>
                                        <div class="chat-contact-preview">The acupuncture session was excellent today</div>
                                    </div>
                                </div>
                                <div class="chat-contact">
                                    <div class="avatar" style="width:40px;height:40px;font-size:13px;background:linear-gradient(135deg,#8b5cf6,#7c3aed)">OI</div>
                                    <div class="chat-contact-info">
                                        <div class="chat-contact-name"><strong>Olga Ivanova</strong><span>3h ago</span></div>
                                        <div class="chat-contact-preview">Can we reschedule the tele-consult to 15:00?</div>
                                    </div>
                                    <span class="chat-contact-badge">1</span>
                                </div>
                                <div class="chat-contact">
                                    <div class="avatar" style="width:40px;height:40px;font-size:13px;background:linear-gradient(135deg,#3b82f6,#2563eb)">MA</div>
                                    <div class="chat-contact-info">
                                        <div class="chat-contact-name"><strong>Mohammed Al-Rashid</strong><span>5h ago</span></div>
                                        <div class="chat-contact-preview">Package details look excellent. Proceeding with deposit.</div>
                                    </div>
                                </div>
                                <div class="chat-contact">
                                    <div class="avatar" style="width:40px;height:40px;font-size:13px;background:linear-gradient(135deg,#ec4899,#db2777)">LP</div>
                                    <div class="chat-contact-info">
                                        <div class="chat-contact-name"><strong>Liudmila Petrova</strong><span>1d ago</span></div>
                                        <div class="chat-contact-preview">Visa application submitted. Waiting for approval.</div>
                                    </div>
                                </div>
                                <div class="chat-contact">
                                    <div class="avatar" style="width:40px;height:40px;font-size:13px;background:linear-gradient(135deg,#10b981,#059669)">SV</div>
                                    <div class="chat-contact-info">
                                        <div class="chat-contact-name"><strong>Sergey Volkov</strong><span>2d ago</span></div>
                                        <div class="chat-contact-preview">Can you send me the herbal medicine prescription?</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="chat-main">
                            <div class="chat-header-bar">
                                <div class="avatar" style="width:40px;height:40px;font-size:13px">AK</div>
                                <div style="flex:1">
                                    <div style="font-weight:600;font-size:14px">Anna Kovaleva</div>
                                    <div style="font-size:12px;color:var(--vida-gray-500)">TCM Chronic Rehab Patient · Travel Phase · Russia</div>
                                </div>
                                <div style="display:flex;gap:6px">
                                    <button class="header-btn" style="width:36px;height:36px"><i class="fas fa-phone"></i></button>
                                    <button class="header-btn" style="width:36px;height:36px"><i class="fas fa-video"></i></button>
                                    <button class="header-btn" style="width:36px;height:36px"><i class="fas fa-ellipsis-v"></i></button>
                                </div>
                            </div>
                            <div class="chat-messages-area">
                                <div class="msg msg-in">
                                    <div>Hello Elena! I wanted to confirm my flight details for tomorrow. My reference is SU501 Moscow to Sanya. Is everything still on schedule?</div>
                                    <div class="msg-time">10:30 AM CST · WhatsApp</div>
                                </div>
                                <div class="msg msg-out">
                                    <div>Hello Anna! Yes, everything is confirmed. SU501 departs Moscow (SVO) at 08:45 local time, arriving Sanya (SYX) at 14:30 CST. Your airport transfer is arranged — driver Li Wei will meet you at Gate 3 with a Vidaluma sign.</div>
                                    <div class="msg-time">10:35 AM CST · You</div>
                                </div>
                                <div class="msg msg-in">
                                    <div>Perfect! And the hotel booking near Sanya TCM Hospital?</div>
                                    <div class="msg-time">10:38 AM CST · WhatsApp</div>
                                </div>
                                <div class="msg msg-out">
                                    <div>Confirmed at the Sanya Marriott Yalong Bay, 15 minutes from the hospital. Check-in is ready. Your medical coordinator Dr. Chen will visit you at the hotel on June 10 at 09:00 for your initial TCM constitution assessment.</div>
                                    <div class="msg-time">10:40 AM CST · You</div>
                                </div>
                                <div class="msg msg-in">
                                    <div>Wonderful, thank you so much! I am very excited but also a little nervous. See you tomorrow in Sanya!</div>
                                    <div class="msg-time">10:42 AM CST · WhatsApp</div>
                                </div>
                                <div class="msg msg-out">
                                    <div>No need to be nervous, Anna. We will take excellent care of you. Safe travels! 🌴</div>
                                    <div class="msg-time">10:43 AM CST · You</div>
                                </div>
                            </div>
                            <div class="chat-input-bar">
                                <button class="header-btn" style="width:36px;height:36px"><i class="fas fa-paperclip"></i></button>
                                <input type="text" placeholder="Type a message... (Auto-translate: RU ↔ EN)">
                                <button class="chat-send-btn"><i class="fas fa-paper-plane"></i></button>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== DOCUMENTS ===== -->
            <section id="documents" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Documents</h1>
                        <p class="page-subtitle">Medical records, visa documents, consent forms, and travel itineraries. PIPL-compliant storage on AliCloud OSS.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-filter"></i> Filter</button>
                        <button class="btn btn-primary"><i class="fas fa-upload"></i> Upload Document</button>
                    </div>
                </div>

                <div class="card">
                    <div class="tabs">
                        <button class="tab active" onclick="switchTab(this,'tabAllDocs')">All Documents <span style="color:var(--vida-gray-400);margin-left:4px">(234)</span></button>
                        <button class="tab" onclick="switchTab(this,'tabMedicalDocs')">Medical Records <span style="color:var(--vida-gray-400);margin-left:4px">(89)</span></button>
                        <button class="tab" onclick="switchTab(this,'tabTravelDocs')">Travel Documents <span style="color:var(--vida-gray-400);margin-left:4px">(67)</span></button>
                        <button class="tab" onclick="switchTab(this,'tabLegalDocs')">Legal & Insurance <span style="color:var(--vida-gray-400);margin-left:4px">(45)</span></button>
                        <button class="tab" onclick="switchTab(this,'tabConsentDocs')">Consent Forms <span style="color:var(--vida-gray-400);margin-left:4px">(33)</span></button>
                    </div>

                    <div id="tabAllDocs" class="tab-pane active">
                        <div style="padding:24px">
                            <div class="doc-grid">
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(239,68,68,0.1);color:var(--vida-danger)"><i class="fas fa-file-pdf"></i></div>
                                    <div class="doc-name">Anna Kovaleva — Medical History</div>
                                    <div class="doc-meta">PDF · 2.4 MB · Updated 2 days ago</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(37,99,235,0.1);color:#2563eb"><i class="fas fa-file-medical-alt"></i></div>
                                    <div class="doc-name">Dmitry Sokolov — ECG Report</div>
                                    <div class="doc-meta">PDF · 15.8 MB · Updated 1 week ago</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(16,185,129,0.1);color:var(--vida-success)"><i class="fas fa-passport"></i></div>
                                    <div class="doc-name">Olga Ivanova — Passport Copy</div>
                                    <div class="doc-meta">JPG · 1.2 MB · Updated 3 days ago</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(245,158,11,0.1);color:#b45309"><i class="fas fa-file-contract"></i></div>
                                    <div class="doc-name">Mohammed Al-Rashid — Visa Application</div>
                                    <div class="doc-meta">PDF · 856 KB · Updated 5 days ago</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(139,92,246,0.1);color:var(--vida-purple)"><i class="fas fa-file-medical"></i></div>
                                    <div class="doc-name">Anna Kovaleva — Insurance Policy</div>
                                    <div class="doc-meta">PDF · 3.1 MB · Updated 1 day ago</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(100,116,139,0.1);color:var(--vida-gray-500)"><i class="fas fa-x-ray"></i></div>
                                    <div class="doc-name">Dmitry Sokolov — Chest X-Ray</div>
                                    <div class="doc-meta">DICOM · 45.2 MB · Updated yesterday</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(59,130,246,0.1);color:#3b82f6"><i class="fas fa-file-prescription"></i></div>
                                    <div class="doc-name">Sergey Volkov — Herbal Prescription</div>
                                    <div class="doc-meta">PDF · 520 KB · Updated 2 days ago</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                                <div class="doc-card">
                                    <div class="doc-icon" style="background:rgba(16,185,129,0.1);color:var(--vida-success)"><i class="fas fa-plane"></i></div>
                                    <div class="doc-name">Anna Kovaleva — Flight Itinerary</div>
                                    <div class="doc-meta">PDF · 1.8 MB · Updated 4 days ago</div>
                                    <div style="margin-top:10px;font-size:11px;color:var(--vida-gray-400)"><i class="fas fa-shield-alt" style="margin-right:4px"></i> AES-256 · AliCloud CN</div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div id="tabMedicalDocs" class="tab-pane">
                        <div class="empty-state">
                            <i class="fas fa-file-medical"></i>
                            <p style="font-weight:600;color:var(--vida-gray-600)">89 medical records</p>
                            <p style="font-size:13px">Diagnostic reports, lab results, imaging, prescriptions, and TCM assessment forms</p>
                        </div>
                    </div>
                    <div id="tabTravelDocs" class="tab-pane">
                        <div class="empty-state">
                            <i class="fas fa-passport"></i>
                            <p style="font-weight:600;color:var(--vida-gray-600)">67 travel documents</p>
                            <p style="font-size:13px">Passport copies, visa applications, flight itineraries, hotel confirmations, and airport pickup schedules</p>
                        </div>
                    </div>
                    <div id="tabLegalDocs" class="tab-pane">
                        <div class="empty-state">
                            <i class="fas fa-file-contract"></i>
                            <p style="font-weight:600;color:var(--vida-gray-600)">45 legal & insurance documents</p>
                            <p style="font-size:13px">Insurance policies, consent forms, liability waivers, and PIPL compliance records</p>
                        </div>
                    </div>
                    <div id="tabConsentDocs" class="tab-pane">
                        <div class="empty-state">
                            <i class="fas fa-user-shield"></i>
                            <p style="font-weight:600;color:var(--vida-gray-600)">33 consent forms</p>
                            <p style="font-size:13px">PIPL data processing consent, medical treatment consent, photo/video release, and testimonial consent</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== FINANCE ===== -->
            <section id="finance" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Finance</h1>
                        <p class="page-subtitle">Revenue tracking, payments, commissions, and multi-currency reconciliation.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-filter"></i> Period</button>
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-download"></i> Export</button>
                    </div>
                </div>

                <div class="stats-grid" style="grid-template-columns:repeat(3,1fr);margin-bottom:24px">
                    <div class="stat-card">
                        <div class="stat-header">
                            <div class="stat-icon green"><i class="fas fa-wallet"></i></div>
                            <span class="stat-trend up"><i class="fas fa-arrow-up" style="font-size:10px"></i> 23%</span>
                        </div>
                        <div class="stat-value">$1.24M</div>
                        <div class="stat-label">Total Revenue (Jun 2026)</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-header">
                            <div class="stat-icon blue"><i class="fas fa-clock"></i></div>
                            <span class="stat-trend down"><i class="fas fa-arrow-down" style="font-size:10px"></i> 5%</span>
                        </div>
                        <div class="stat-value">$340K</div>
                        <div class="stat-label">Pending Payments</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-header">
                            <div class="stat-icon amber"><i class="fas fa-hand-holding-usd"></i></div>
                            <span class="stat-trend up"><i class="fas fa-arrow-up" style="font-size:10px"></i> 2%</span>
                        </div>
                        <div class="stat-value">$85K</div>
                        <div class="stat-label">Refunds & Cancellations</div>
                    </div>
                </div>

                <div class="card">
                    <div class="card-header">
                        <h3><i class="fas fa-list" style="color:var(--vida-primary);margin-right:8px"></i>Recent Transactions</h3>
                        <div class="page-actions">
                            <button class="btn btn-secondary btn-sm"><i class="fas fa-file-csv"></i> Export CSV</button>
                        </div>
                    </div>
                    <div class="table-wrap">
                        <table class="data-table">
                            <thead>
                                <tr>
                                    <th>Transaction ID</th>
                                    <th>Patient</th>
                                    <th>Description</th>
                                    <th>Date</th>
                                    <th>Currency</th>
                                    <th>Amount</th>
                                    <th>Method</th>
                                    <th>Status</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td><strong style="color:var(--vida-primary)">#TRX-2026-0891</strong></td>
                                    <td>Anna Kovaleva</td>
                                    <td>TCM Chronic Rehab — 50% Deposit</td>
                                    <td>Jun 1, 2026</td>
                                    <td><span style="font-weight:600">USD</span></td>
                                    <td style="color:var(--vida-success);font-weight:700">+$1,600.00</td>
                                    <td><span class="badge badge-gray"><i class="fab fa-cc-visa" style="margin-right:4px"></i>Stripe</span></td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Completed</span></td>
                                </tr>
                                <tr>
                                    <td><strong style="color:var(--vida-primary)">#TRX-2026-0890</strong></td>
                                    <td>Dmitry Sokolov</td>
                                    <td>Integrative Cardiac — Final Payment</td>
                                    <td>May 30, 2026</td>
                                    <td><span style="font-weight:600">USDT</span></td>
                                    <td style="color:var(--vida-success);font-weight:700">+$8,500.00</td>
                                    <td><span class="badge badge-gray"><i class="fab fa-bitcoin" style="margin-right:4px"></i>Crypto</span></td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Completed</span></td>
                                </tr>
                                <tr>
                                    <td><strong style="color:var(--vida-primary)">#TRX-2026-0889</strong></td>
                                    <td>Olga Ivanova</td>
                                    <td>IVF Treatment — Consultation Fee</td>
                                    <td>May 28, 2026</td>
                                    <td><span style="font-weight:600">USD</span></td>
                                    <td style="color:var(--vida-success);font-weight:700">+$500.00</td>
                                    <td><span class="badge badge-gray"><i class="fab fa-cc-visa" style="margin-right:4px"></i>Stripe</span></td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Completed</span></td>
                                </tr>
                                <tr>
                                    <td><strong style="color:var(--vida-primary)">#TRX-2026-0888</strong></td>
                                    <td>Mohammed Al-Rashid</td>
                                    <td>Anti-Aging — 50% Deposit</td>
                                    <td>May 25, 2026</td>
                                    <td><span style="font-weight:600">USD</span></td>
                                    <td style="color:var(--vida-success);font-weight:700">+$4,100.00</td>
                                    <td><span class="badge badge-gray"><i class="fas fa-university" style="margin-right:4px"></i>Wire</span></td>
                                    <td><span class="badge badge-amber"><span class="badge-dot amber"></span> Pending</span></td>
                                </tr>
                                <tr>
                                    <td><strong style="color:var(--vida-primary)">#TRX-2026-0887</strong></td>
                                    <td>Ivan Smirnov</td>
                                    <td>Integrative Cardiac — Refund (Cancelled)</td>
                                    <td>May 22, 2026</td>
                                    <td><span style="font-weight:600">USDT</span></td>
                                    <td style="color:var(--vida-danger);font-weight:700">-$2,500.00</td>
                                    <td><span class="badge badge-gray"><i class="fab fa-bitcoin" style="margin-right:4px"></i>Crypto</span></td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Processed</span></td>
                                </tr>
                                <tr>
                                    <td><strong style="color:var(--vida-primary)">#TRX-2026-0886</strong></td>
                                    <td>Liudmila Petrova</td>
                                    <td>TCM Wellness — 50% Deposit</td>
                                    <td>May 20, 2026</td>
                                    <td><span style="font-weight:600">CNY</span></td>
                                    <td style="color:var(--vida-success);font-weight:700">+¥6,480.00</td>
                                    <td><span class="badge badge-gray"><i class="fab fa-weixin" style="margin-right:4px"></i>WeChat</span></td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Completed</span></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- ===== HOSPITALS ===== -->
            <section id="hospitals" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Partner Hospitals</h1>
                        <p class="page-subtitle">Manage relationships with medical facilities across Sanya and Hainan.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-filter"></i> Filter</button>
                        <button class="btn btn-primary"><i class="fas fa-plus"></i> Add Hospital</button>
                    </div>
                </div>

                <div class="card">
                    <div class="table-wrap">
                        <table class="data-table">
                            <thead>
                                <tr>
                                    <th>Hospital</th>
                                    <th>Location</th>
                                    <th>Specialties</th>
                                    <th>Accreditation</th>
                                    <th>Rating</th>
                                    <th>Active Patients</th>
                                    <th>Status</th>
                                    <th style="text-align:right">Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>
                                        <div style="display:flex;align-items:center;gap:10px">
                                            <div class="avatar" style="background:linear-gradient(135deg,#dc2626,#ef4444)">ST</div>
                                            <div>
                                                <div style="font-weight:600">Sanya TCM Hospital</div>
                                                <div style="font-size:11px;color:var(--vida-gray-400)">三亚市中医院 · Multi-Specialty TCM</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>Sanya, Hainan</td>
                                    <td>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">TCM Internal</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Acupuncture</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Rehab</span>
                                    </td>
                                    <td><span class="badge badge-green" style="font-size:10px">三级甲等</span> <span class="badge badge-gray" style="font-size:10px">JCI</span></td>
                                    <td><i class="fas fa-star" style="color:var(--vida-warning);font-size:11px"></i> 4.8</td>
                                    <td>42</td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Active</span></td>
                                    <td style="text-align:right"><button class="btn btn-ghost btn-sm">View</button></td>
                                </tr>
                                <tr>
                                    <td>
                                        <div style="display:flex;align-items:center;gap:10px">
                                            <div class="avatar" style="background:linear-gradient(135deg,#059669,#10b981)">BL</div>
                                            <div>
                                                <div style="font-weight:600">Hainan Boao Lecheng</div>
                                                <div style="font-size:11px;color:var(--vida-gray-400)">海南博鳌乐城 · International Medical Tourism Pilot Zone</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>Boao, Hainan</td>
                                    <td>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Cardiac</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Oncology</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Stem Cell</span>
                                    </td>
                                    <td><span class="badge badge-green" style="font-size:10px">State-Level</span> <span class="badge badge-gray" style="font-size:10px">FTZ Approved</span></td>
                                    <td><i class="fas fa-star" style="color:var(--vida-warning);font-size:11px"></i> 4.9</td>
                                    <td>18</td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Active</span></td>
                                    <td style="text-align:right"><button class="btn btn-ghost btn-sm">View</button></td>
                                </tr>
                                <tr>
                                    <td>
                                        <div style="display:flex;align-items:center;gap:10px">
                                            <div class="avatar" style="background:linear-gradient(135deg,#7c3aed,#8b5cf6)">WC</div>
                                            <div>
                                                <div style="font-weight:600">Sanya Women & Children</div>
                                                <div style="font-size:11px;color:var(--vida-gray-400)">三亚市妇幼保健院 · Reproductive Health</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>Sanya, Hainan</td>
                                    <td>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">IVF</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Obstetrics</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Pediatrics</span>
                                    </td>
                                    <td><span class="badge badge-green" style="font-size:10px">三级乙等</span></td>
                                    <td><i class="fas fa-star" style="color:var(--vida-warning);font-size:11px"></i> 4.6</td>
                                    <td>12</td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Active</span></td>
                                    <td style="text-align:right"><button class="btn btn-ghost btn-sm">View</button></td>
                                </tr>
                                <tr>
                                    <td>
                                        <div style="display:flex;align-items:center;gap:10px">
                                            <div class="avatar" style="background:linear-gradient(135deg,#d97706,#f59e0b)">SC</div>
                                            <div>
                                                <div style="font-weight:600">Sanya Stomatology Center</div>
                                                <div style="font-size:11px;color:var(--vida-gray-400)">三亚市口腔医院 · Dental & Maxillofacial</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>Sanya, Hainan</td>
                                    <td>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Implants</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Cosmetic</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Orthodontics</span>
                                    </td>
                                    <td><span class="badge badge-green" style="font-size:10px">二级甲等</span></td>
                                    <td><i class="fas fa-star" style="color:var(--vida-warning);font-size:11px"></i> 4.5</td>
                                    <td>8</td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Active</span></td>
                                    <td style="text-align:right"><button class="btn btn-ghost btn-sm">View</button></td>
                                </tr>
                                <tr>
                                    <td>
                                        <div style="display:flex;align-items:center;gap:10px">
                                            <div class="avatar" style="background:linear-gradient(135deg,#2563eb,#3b82f6)">HI</div>
                                            <div>
                                                <div style="font-weight:600">Hainan International Health Center</div>
                                                <div style="font-size:11px;color:var(--vida-gray-400)">海南国际健康中心 · Integrative Medicine</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td>Haikou, Hainan</td>
                                    <td>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Anti-Aging</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Regeneration</span>
                                        <span class="badge badge-gray" style="font-size:10px;padding:2px 8px">Wellness</span>
                                    </td>
                                    <td><span class="badge badge-green" style="font-size:10px">ISO 9001</span></td>
                                    <td><i class="fas fa-star" style="color:var(--vida-warning);font-size:11px"></i> 4.7</td>
                                    <td>6</td>
                                    <td><span class="badge badge-green"><span class="badge-dot green"></span> Active</span></td>
                                    <td style="text-align:right"><button class="btn btn-ghost btn-sm">View</button></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- ===== REPORTS ===== -->
            <section id="reports" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Reports & Analytics</h1>
                        <p class="page-subtitle">Data-driven insights for patient acquisition, revenue, and operational efficiency.</p>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-calendar"></i> Jun 2026</button>
                        <button class="btn btn-secondary btn-sm"><i class="fas fa-download"></i> Export</button>
                    </div>
                </div>

                <div class="grid-2" style="margin-bottom:20px">
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-chart-line" style="color:var(--vida-primary);margin-right:8px"></i>Revenue Overview</h3>
                        </div>
                        <div style="padding:40px">
                            <div style="display:flex;align-items:flex-end;justify-content:space-around;height:200px;gap:12px">
                                <div style="text-align:center;flex:1">
                                    <div style="height:60px;background:linear-gradient(to top,var(--vida-primary),rgba(13,148,136,0.3));border-radius:6px 6px 0 0"></div>
                                    <div style="font-size:11px;color:var(--vida-gray-500);margin-top:8px">Jan</div>
                                    <div style="font-size:12px;font-weight:700">$680K</div>
                                </div>
                                <div style="text-align:center;flex:1">
                                    <div style="height:90px;background:linear-gradient(to top,var(--vida-primary),rgba(13,148,136,0.3));border-radius:6px 6px 0 0"></div>
                                    <div style="font-size:11px;color:var(--vida-gray-500);margin-top:8px">Feb</div>
                                    <div style="font-size:12px;font-weight:700">$920K</div>
                                </div>
                                <div style="text-align:center;flex:1">
                                    <div style="height:120px;background:linear-gradient(to top,var(--vida-primary),rgba(13,148,136,0.3));border-radius:6px 6px 0 0"></div>
                                    <div style="font-size:11px;color:var(--vida-gray-500);margin-top:8px">Mar</div>
                                    <div style="font-size:12px;font-weight:700">$1.1M</div>
                                </div>
                                <div style="text-align:center;flex:1">
                                    <div style="height:100px;background:linear-gradient(to top,var(--vida-primary),rgba(13,148,136,0.3));border-radius:6px 6px 0 0"></div>
                                    <div style="font-size:11px;color:var(--vida-gray-500);margin-top:8px">Apr</div>
                                    <div style="font-size:12px;font-weight:700">$980K</div>
                                </div>
                                <div style="text-align:center;flex:1">
                                    <div style="height:80px;background:linear-gradient(to top,var(--vida-primary),rgba(13,148,136,0.3));border-radius:6px 6px 0 0"></div>
                                    <div style="font-size:11px;color:var(--vida-gray-500);margin-top:8px">May</div>
                                    <div style="font-size:12px;font-weight:700">$840K</div>
                                </div>
                                <div style="text-align:center;flex:1">
                                    <div style="height:140px;background:linear-gradient(to top,var(--vida-primary),rgba(13,148,136,0.3));border-radius:6px 6px 0 0;position:relative">
                                        <div style="position:absolute;top:-24px;left:50%;transform:translateX(-50%);background:var(--vida-primary);color:white;font-size:11px;font-weight:700;padding:3px 10px;border-radius:12px;white-space:nowrap">$1.24M</div>
                                    </div>
                                    <div style="font-size:11px;color:var(--vida-primary);font-weight:700;margin-top:8px">Jun</div>
                                    <div style="font-size:12px;font-weight:700;color:var(--vida-primary)">$1.24M</div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-chart-pie" style="color:var(--vida-primary);margin-right:8px"></i>Patient Sources</h3>
                        </div>
                        <div style="padding:30px">
                            <div style="display:flex;flex-direction:column;gap:16px">
                                <div>
                                    <div class="flex-between" style="margin-bottom:6px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇷🇺</span>Russia</span>
                                        <span style="font-size:13px;font-weight:700">78% · 122 patients</span>
                                    </div>
                                    <div style="height:8px;background:var(--vida-gray-100);border-radius:4px;overflow:hidden">
                                        <div style="width:78%;height:100%;background:var(--vida-primary);border-radius:4px"></div>
                                    </div>
                                    <span style="font-size:11px;color:var(--vida-gray-400)">Primary: Website, WhatsApp, Partner Agencies</span>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:6px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇰🇿</span>Kazakhstan</span>
                                        <span style="font-size:13px;font-weight:700">8% · 12 patients</span>
                                    </div>
                                    <div style="height:8px;background:var(--vida-gray-100);border-radius:4px;overflow:hidden">
                                        <div style="width:8%;height:100%;background:var(--vida-secondary);border-radius:4px"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:6px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇦🇪</span>UAE</span>
                                        <span style="font-size:13px;font-weight:700">5% · 8 patients</span>
                                    </div>
                                    <div style="height:8px;background:var(--vida-gray-100);border-radius:4px;overflow:hidden">
                                        <div style="width:5%;height:100%;background:var(--vida-warning);border-radius:4px"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:6px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🇩🇪</span>Germany</span>
                                        <span style="font-size:13px;font-weight:700">4% · 6 patients</span>
                                    </div>
                                    <div style="height:8px;background:var(--vida-gray-100);border-radius:4px;overflow:hidden">
                                        <div style="width:4%;height:100%;background:var(--vida-purple);border-radius:4px"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex-between" style="margin-bottom:6px">
                                        <span style="font-size:13px;font-weight:600"><span style="margin-right:6px">🌍</span>Other (8 countries)</span>
                                        <span style="font-size:13px;font-weight:700">5% · 8 patients</span>
                                    </div>
                                    <div style="height:8px;background:var(--vida-gray-100);border-radius:4px;overflow:hidden">
                                        <div style="width:5%;height:100%;background:var(--vida-gray-400);border-radius:4px"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-funnel-dollar" style="color:var(--vida-primary);margin-right:8px"></i>Conversion Funnel</h3>
                        </div>
                        <div style="padding:24px">
                            <div style="display:flex;flex-direction:column;gap:10px">
                                <div class="flex-between" style="padding:10px 14px;background:var(--vida-gray-50);border-radius:var(--radius-md)">
                                    <span style="font-size:13px;font-weight:600">Inquiry</span>
                                    <span style="font-size:13px;font-weight:700;color:var(--vida-primary)">1,200 · 100%</span>
                                </div>
                                <div style="text-align:center"><i class="fas fa-arrow-down" style="color:var(--vida-gray-400);font-size:12px"></i> <span style="font-size:11px;color:var(--vida-gray-500)">35% conversion</span></div>
                                <div class="flex-between" style="padding:10px 14px;background:var(--vida-gray-50);border-radius:var(--radius-md)">
                                    <span style="font-size:13px;font-weight:600">Consultation</span>
                                    <span style="font-size:13px;font-weight:700;color:var(--vida-primary)">420 · 35%</span>
                                </div>
                                <div style="text-align:center"><i class="fas fa-arrow-down" style="color:var(--vida-gray-400);font-size:12px"></i> <span style="font-size:11px;color:var(--vida-gray-500)">80% conversion</span></div>
                                <div class="flex-between" style="padding:10px 14px;background:var(--vida-gray-50);border-radius:var(--radius-md)">
                                    <span style="font-size:13px;font-weight:600">Quote Sent</span>
                                    <span style="font-size:13px;font-weight:700;color:var(--vida-primary)">336 · 28%</span>
                                </div>
                                <div style="text-align:center"><i class="fas fa-arrow-down" style="color:var(--vida-gray-400);font-size:12px"></i> <span style="font-size:11px;color:var(--vida-gray-500)">60% conversion</span></div>
                                <div class="flex-between" style="padding:10px 14px;background:var(--vida-primary-light);border-radius:var(--radius-md)">
                                    <span style="font-size:13px;font-weight:600;color:var(--vida-primary-dark)">Treatment Completed</span>
                                    <span style="font-size:13px;font-weight:700;color:var(--vida-primary-dark)">202 · 17%</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-smile" style="color:var(--vida-primary);margin-right:8px"></i>Satisfaction Metrics</h3>
                        </div>
                        <div style="padding:24px">
                            <div style="text-align:center;margin-bottom:20px">
                                <div style="font-size:48px;font-weight:800;color:var(--vida-primary);letter-spacing:-2px">94.2%</div>
                                <div style="font-size:13px;color:var(--vida-gray-500)">Overall Satisfaction Rate</div>
                            </div>
                            <div style="display:flex;flex-direction:column;gap:12px">
                                <div class="flex-between">
                                    <span style="font-size:13px">Treatment Quality</span>
                                    <div style="display:flex;align-items:center;gap:8px">
                                        <div style="width:100px;height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                            <div style="width:96%;height:100%;background:var(--vida-success);border-radius:3px"></div>
                                        </div>
                                        <span style="font-size:12px;font-weight:700">4.8/5</span>
                                    </div>
                                </div>
                                <div class="flex-between">
                                    <span style="font-size:13px">Coordinator Service</span>
                                    <div style="display:flex;align-items:center;gap:8px">
                                        <div style="width:100px;height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                            <div style="width:94%;height:100%;background:var(--vida-success);border-radius:3px"></div>
                                        </div>
                                        <span style="font-size:12px;font-weight:700">4.7/5</span>
                                    </div>
                                </div>
                                <div class="flex-between">
                                    <span style="font-size:13px">Accommodation</span>
                                    <div style="display:flex;align-items:center;gap:8px">
                                        <div style="width:100px;height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                            <div style="width:90%;height:100%;background:var(--vida-success);border-radius:3px"></div>
                                        </div>
                                        <span style="font-size:12px;font-weight:700">4.5/5</span>
                                    </div>
                                </div>
                                <div class="flex-between">
                                    <span style="font-size:13px">Value for Money</span>
                                    <div style="display:flex;align-items:center;gap:8px">
                                        <div style="width:100px;height:6px;background:var(--vida-gray-100);border-radius:3px;overflow:hidden">
                                            <div style="width:92%;height:100%;background:var(--vida-success);border-radius:3px"></div>
                                        </div>
                                        <span style="font-size:12px;font-weight:700">4.6/5</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-user-tie" style="color:var(--vida-primary);margin-right:8px"></i>Staff Performance</h3>
                        </div>
                        <div style="padding:20px">
                            <div style="display:flex;flex-direction:column;gap:14px">
                                <div style="display:flex;align-items:center;gap:12px">
                                    <div class="avatar" style="width:36px;height:36px;font-size:12px">EW</div>
                                    <div style="flex:1">
                                        <div class="flex-between">
                                            <span style="font-weight:600;font-size:13px">Elena Wang</span>
                                            <span style="font-size:12px;font-weight:700;color:var(--vida-primary)">$482K</span>
                                        </div>
                                        <div style="font-size:11px;color:var(--vida-gray-400)">42 patients · Avg response 1.2h</span>
                                    </div>
                                </div>
                                <div style="display:flex;align-items:center;gap:12px">
                                    <div class="avatar" style="width:36px;height:36px;font-size:12px;background:linear-gradient(135deg,#f59e0b,#d97706)">LW</div>
                                    <div style="flex:1">
                                        <div class="flex-between">
                                            <span style="font-weight:600;font-size:13px">Li Wei</span>
                                            <span style="font-size:12px;font-weight:700;color:var(--vida-primary)">$310K</span>
                                        </div>
                                        <div style="font-size:11px;color:var(--vida-gray-400)">28 patients · Avg response 2.1h</span>
                                    </div>
                                </div>
                                <div style="display:flex;align-items:center;gap:12px">
                                    <div class="avatar" style="width:36px;height:36px;font-size:12px;background:linear-gradient(135deg,#8b5cf6,#7c3aed)">ZM</div>
                                    <div style="flex:1">
                                        <div class="flex-between">
                                            <span style="font-weight:600;font-size:13px">Zhang Min</span>
                                            <span style="font-size:12px;font-weight:700;color:var(--vida-primary)">$248K</span>
                                        </div>
                                        <div style="font-size:11px;color:var(--vida-gray-400)">22 patients · Avg response 1.8h</span>
                                    </div>
                                </div>
                                <div style="display:flex;align-items:center;gap:12px">
                                    <div class="avatar" style="width:36px;height:36px;font-size:12px;background:linear-gradient(135deg,#3b82f6,#2563eb)">CW</div>
                                    <div style="flex:1">
                                        <div class="flex-between">
                                            <span style="font-weight:600;font-size:13px">Chen Wei</span>
                                            <span style="font-size:12px;font-weight:700;color:var(--vida-primary)">$198K</span>
                                        </div>
                                        <div style="font-size:11px;color:var(--vida-gray-400)">18 patients · Avg response 3.2h</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== SETTINGS ===== -->
            <section id="settings" class="section">
                <div class="page-header flex-between">
                    <div>
                        <h1 class="page-title">Settings</h1>
                        <p class="page-subtitle">Configure system preferences, compliance, and integrations.</p>
                    </div>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-building" style="color:var(--vida-primary);margin-right:8px"></i>Company Profile</h3>
                        </div>
                        <div style="padding:24px">
                            <div class="form-group full" style="margin-bottom:18px">
                                <label class="form-label">Company Name</label>
                                <input type="text" class="form-input" value="Vidaluma Medical Tourism Co., Ltd.">
                            </div>
                            <div class="form-group full" style="margin-bottom:18px">
                                <label class="form-label">Business Registration (统一社会信用代码)</label>
                                <input type="text" class="form-input" value="91460000MA5T4XXXXX" readonly style="background:var(--vida-gray-50)">
                            </div>
                            <div class="form-grid" style="margin-bottom:18px">
                                <div class="form-group">
                                    <label class="form-label">Default Currency</label>
                                    <select class="form-select">
                                        <option>USD ($) — Primary</option>
                                        <option>CNY (¥)</option>
                                        <option>EUR (€)</option>
                                        <option>RUB (₽)</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Timezone</label>
                                    <select class="form-select">
                                        <option>Asia/Shanghai (CST, UTC+8) — Primary</option>
                                        <option>Europe/Moscow (MSK, UTC+3)</option>
                                        <option>Europe/Berlin (CET, UTC+1)</option>
                                        <option>Asia/Dubai (GST, UTC+4)</option>
                                    </select>
                                </div>
                            </div>
                            <div class="form-group full" style="margin-bottom:18px">
                                <label class="form-label">Primary Languages</label>
                                <div style="display:flex;gap:10px;flex-wrap:wrap;margin-top:6px">
                                    <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-primary-light);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox" checked style="accent-color:var(--vida-primary)"> Russian (Primary)</label>
                                    <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-primary-light);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox" checked style="accent-color:var(--vida-primary)"> English</label>
                                    <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-primary-light);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox" checked style="accent-color:var(--vida-primary)"> Chinese (中文)</label>
                                    <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> German</label>
                                    <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Arabic</label>
                                </div>
                            </div>
                            <div style="display:flex;justify-content:flex-end;gap:10px">
                                <button class="btn btn-secondary">Cancel</button>
                                <button class="btn btn-primary">Save Changes</button>
                            </div>
                        </div>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-shield-alt" style="color:var(--vida-primary);margin-right:8px"></i>PIPL Compliance & Security</h3>
                        </div>
                        <div style="padding:24px">
                            <div class="form-group full" style="margin-bottom:18px">
                                <label class="form-label">Data Residency</label>
                                <select class="form-select">
                                    <option>AliCloud China (Hangzhou) — Primary</option>
                                    <option>AliCloud Hong Kong — Backup</option>
                                    <option>Tencent Cloud Beijing — Secondary</option>
                                </select>
                                <div class="form-hint">Patient health data must be stored in mainland China per PIPL Article 38</div>
                            </div>
                            <div class="form-group full" style="margin-bottom:18px">
                                <label class="form-label">Encryption Standard</label>
                                <select class="form-select">
                                    <option>AES-256-GCM (At Rest + In Transit)</option>
                                    <option>SM4 (国密算法) — PIPL Recommended</option>
                                </select>
                            </div>
                            <div class="form-group full" style="margin-bottom:18px">
                                <label class="form-label">Data Retention (Health Records)</label>
                                <select class="form-select">
                                    <option>7 years post-treatment (Medical standard)</option>
                                    <option>10 years post-treatment</option>
                                    <option>Patient lifetime + 5 years</option>
                                </select>
                            </div>
                            <div class="form-group full" style="margin-bottom:18px">
                                <label class="form-label">Cross-Border Transfer Consent</label>
                                <div style="display:flex;flex-direction:column;gap:8px;margin-top:6px">
                                    <label style="display:flex;align-items:center;gap:8px;cursor:pointer;font-size:13px"><input type="checkbox" checked> Require explicit patient consent for any data leaving China</label>
                                    <label style="display:flex;align-items:center;gap:8px;cursor:pointer;font-size:13px"><input type="checkbox" checked> Auto-generate security assessment report for each transfer</label>
                                    <label style="display:flex;align-items:center;gap:8px;cursor:pointer;font-size:13px"><input type="checkbox" checked> Notify DPO within 24h of any cross-border data request</label>
                                </div>
                            </div>
                            <div style="display:flex;justify-content:flex-end;gap:10px">
                                <button class="btn btn-secondary">Cancel</button>
                                <button class="btn btn-primary">Save Compliance Settings</button>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="grid-2" style="margin-top:20px">
                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-plug" style="color:var(--vida-primary);margin-right:8px"></i>Integrations</h3>
                        </div>
                        <div style="padding:24px">
                            <div style="display:flex;flex-direction:column;gap:16px">
                                <div class="flex-between" style="padding:14px;background:var(--vida-gray-50);border-radius:var(--radius-lg)">
                                    <div style="display:flex;align-items:center;gap:12px">
                                        <div style="width:40px;height:40px;background:#07c160;border-radius:var(--radius-md);display:flex;align-items:center;justify-content:center;color:white;font-size:18px"><i class="fab fa-weixin"></i></div>
                                        <div>
                                            <div style="font-weight:600;font-size:14px">WeChat Official Account</div>
                                            <div style="font-size:12px;color:var(--vida-gray-400)">Service Account · 12,450 followers</div>
                                        </div>
                                    </div>
                                    <span class="badge badge-green"><span class="badge-dot green"></span> Connected</span>
                                </div>
                                <div class="flex-between" style="padding:14px;background:var(--vida-gray-50);border-radius:var(--radius-lg)">
                                    <div style="display:flex;align-items:center;gap:12px">
                                        <div style="width:40px;height:40px;background:#25d366;border-radius:var(--radius-md);display:flex;align-items:center;justify-content:center;color:white;font-size:18px"><i class="fab fa-whatsapp"></i></div>
                                        <div>
                                            <div style="font-weight:600;font-size:14px">WhatsApp Business API</div>
                                            <div style="font-size:12px;color:var(--vida-gray-400)">Meta Business · 89 active chats</div>
                                        </div>
                                    </div>
                                    <span class="badge badge-green"><span class="badge-dot green"></span> Connected</span>
                                </div>
                                <div class="flex-between" style="padding:14px;background:var(--vida-gray-50);border-radius:var(--radius-lg)">
                                    <div style="display:flex;align-items:center;gap:12px">
                                        <div style="width:40px;height:40px;background:#635bff;border-radius:var(--radius-md);display:flex;align-items:center;justify-content:center;color:white;font-size:18px"><i class="fab fa-stripe"></i></div>
                                        <div>
                                            <div style="font-weight:600;font-size:14px">Stripe</div>
                                            <div style="font-size:12px;color:var(--vida-gray-400)">USD/EUR payments · Test mode</div>
                                        </div>
                                    </div>
                                    <span class="badge badge-amber"><span class="badge-dot amber"></span> Test Mode</span>
                                </div>
                                <div class="flex-between" style="padding:14px;background:var(--vida-gray-50);border-radius:var(--radius-lg)">
                                    <div style="display:flex;align-items:center;gap:12px">
                                        <div style="width:40px;height:40px;background:#1677ff;border-radius:var(--radius-md);display:flex;align-items:center;justify-content:center;color:white;font-size:18px"><i class="fab fa-alipay"></i></div>
                                        <div>
                                            <div style="font-weight:600;font-size:14px">Alipay / WeChat Pay</div>
                                            <div style="font-size:12px;color:var(--vida-gray-400)">CNY payments · Live</div>
                                        </div>
                                    </div>
                                    <span class="badge badge-green"><span class="badge-dot green"></span> Live</span>
                                </div>
                                <div class="flex-between" style="padding:14px;background:var(--vida-gray-50);border-radius:var(--radius-lg)">
                                    <div style="display:flex;align-items:center;gap:12px">
                                        <div style="width:40px;height:40px;background:#f7931a;border-radius:var(--radius-md);display:flex;align-items:center;justify-content:center;color:white;font-size:18px"><i class="fab fa-bitcoin"></i></div>
                                        <div>
                                            <div style="font-weight:600;font-size:14px">USDT (TRC-20)</div>
                                            <div style="font-size:12px;color:var(--vida-gray-400)">Crypto payments for Russian market</div>
                                        </div>
                                    </div>
                                    <span class="badge badge-green"><span class="badge-dot green"></span> Live</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <h3><i class="fas fa-bell" style="color:var(--vida-primary);margin-right:8px"></i>Notifications</h3>
                        </div>
                        <div style="padding:24px">
                            <div style="display:flex;flex-direction:column;gap:14px">
                                <div class="flex-between">
                                    <div>
                                        <div style="font-weight:600;font-size:14px">New patient inquiry</div>
                                        <div style="font-size:12px;color:var(--vida-gray-400)">Alert when lead score >= 70</div>
                                    </div>
                                    <label style="position:relative;display:inline-block;width:44px;height:24px">
                                        <input type="checkbox" checked style="opacity:0;width:0;height:0">
                                        <span style="position:absolute;cursor:pointer;top:0;left:0;right:0;bottom:0;background:var(--vida-primary);border-radius:24px;transition:0.3s"></span>
                                    </label>
                                </div>
                                <div class="flex-between">
                                    <div>
                                        <div style="font-weight:600;font-size:14px">Payment received</div>
                                        <div style="font-size:12px;color:var(--vida-gray-400)">Alert on deposit or full payment</div>
                                    </div>
                                    <label style="position:relative;display:inline-block;width:44px;height:24px">
                                        <input type="checkbox" checked style="opacity:0;width:0;height:0">
                                        <span style="position:absolute;cursor:pointer;top:0;left:0;right:0;bottom:0;background:var(--vida-primary);border-radius:24px;transition:0.3s"></span>
                                    </label>
                                </div>
                                <div class="flex-between">
                                    <div>
                                        <div style="font-weight:600;font-size:14px">SLA breach warning</div>
                                        <div style="font-size:12px;color:var(--vida-gray-400)">Alert when response time > 2 hours</div>
                                    </div>
                                    <label style="position:relative;display:inline-block;width:44px;height:24px">
                                        <input type="checkbox" checked style="opacity:0;width:0;height:0">
                                        <span style="position:absolute;cursor:pointer;top:0;left:0;right:0;bottom:0;background:var(--vida-primary);border-radius:24px;transition:0.3s"></span>
                                    </label>
                                </div>
                                <div class="flex-between">
                                    <div>
                                        <div style="font-weight:600;font-size:14px">Visa expiry alert</div>
                                        <div style="font-size:12px;color:var(--vida-gray-400)">14, 7, 3 days before expiry</div>
                                    </div>
                                    <label style="position:relative;display:inline-block;width:44px;height:24px">
                                        <input type="checkbox" checked style="opacity:0;width:0;height:0">
                                        <span style="position:absolute;cursor:pointer;top:0;left:0;right:0;bottom:0;background:var(--vida-primary);border-radius:24px;transition:0.3s"></span>
                                    </label>
                                </div>
                                <div class="flex-between">
                                    <div>
                                        <div style="font-weight:600;font-size:14px">Marketing emails</div>
                                        <div style="font-size:12px;color:var(--vida-gray-400)">Weekly newsletter, seasonal offers</div>
                                    </div>
                                    <label style="position:relative;display:inline-block;width:44px;height:24px">
                                        <input type="checkbox" style="opacity:0;width:0;height:0">
                                        <span style="position:absolute;cursor:pointer;top:0;left:0;right:0;bottom:0;background:var(--vida-gray-300);border-radius:24px;transition:0.3s"></span>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ===== PATIENT DETAIL ===== -->
            <section id="patient-detail" class="section">
                <div class="page-header flex-between">
                    <div style="display:flex;align-items:center;gap:16px">
                        <button class="btn btn-secondary" onclick="showSection('patients')" style="padding:8px 14px"><i class="fas fa-arrow-left"></i> Back</button>
                        <div>
                            <h1 class="page-title" id="detailName">Patient Profile</h1>
                            <p class="page-subtitle" id="detailId">View complete patient dossier</p>
                        </div>
                    </div>
                    <div class="page-actions">
                        <button class="btn btn-secondary"><i class="fas fa-edit"></i> Edit</button>
                        <button class="btn btn-primary" onclick="showSection('communications')"><i class="fas fa-envelope"></i> Message</button>
                    </div>
                </div>

                <div class="profile-layout">
                    <div class="profile-sidebar">
                        <div class="profile-card-box">
                            <div class="avatar profile-avatar-xl" id="detailAvatar">AK</div>
                            <div class="profile-name-xl" id="detailPatientName">Anna Kovaleva</div>
                            <div class="profile-id-xl" id="detailPatientId">ID: VD-2026-0142</div>
                            <div id="detailStatusBadge"><span class="badge badge-teal"><span class="badge-dot teal"></span> Travel Phase</span></div>
                            <div class="detail-list">
                                <div class="detail-item">
                                    <span class="detail-item-label">Nationality</span>
                                    <span class="detail-item-value" id="detailNationality"><span style="margin-right:4px">🇷🇺</span> Russia</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Age</span>
                                    <span class="detail-item-value" id="detailAge">54 years</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Blood Type</span>
                                    <span class="detail-item-value">O+</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Phone</span>
                                    <span class="detail-item-value">+7-916-555-0142</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Email</span>
                                    <span class="detail-item-value" style="font-size:12px">anna.k@mail.ru</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Passport</span>
                                    <span class="detail-item-value">75 12 345678</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Coordinator</span>
                                    <span class="detail-item-value">Elena Wang</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Preferred Language</span>
                                    <span class="detail-item-value">Russian</span>
                                </div>
                                <div class="detail-item">
                                    <span class="detail-item-label">Timezone</span>
                                    <span class="detail-item-value">Europe/Moscow (UTC+3)</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="profile-main">
                        <div class="card" style="margin-bottom:20px">
                            <div class="tabs">
                                <button class="tab active" onclick="switchTab(this,'tabOverview')">Overview</button>
                                <button class="tab" onclick="switchTab(this,'tabMedical')">Medical History</button>
                                <button class="tab" onclick="switchTab(this,'tabTravel')">Travel Details</button>
                                <button class="tab" onclick="switchTab(this,'tabFinancial')">Financial</button>
                                <button class="tab" onclick="switchTab(this,'tabTimeline')">Timeline</button>
                            </div>

                            <div id="tabOverview" class="tab-pane active" style="padding:24px">
                                <div class="grid-2" style="gap:24px">
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:14px;color:var(--vida-gray-900)"><i class="fas fa-stethoscope" style="color:var(--vida-primary);margin-right:8px"></i>Treatment Information</h4>
                                        <div style="display:flex;flex-direction:column;gap:0">
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Treatment Type</span><span class="detail-item-value" id="detailTreatment">TCM Chronic Rehab (14-day)</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Hospital</span><span class="detail-item-value">Sanya TCM Hospital</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Doctor</span><span class="detail-item-value">Dr. Zhang Wei (张伟)</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Admission Date</span><span class="detail-item-value">June 10, 2026</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Estimated Discharge</span><span class="detail-item-value">June 24, 2026</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">TCM Constitution</span><span class="detail-item-value">Qi Deficiency (气虚质)</span></div>
                                        </div>
                                    </div>
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:14px;color:var(--vida-gray-900)"><i class="fas fa-file-invoice-dollar" style="color:var(--vida-primary);margin-right:8px"></i>Package & Payment</h4>
                                        <div style="display:flex;flex-direction:column;gap:0">
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Package</span><span class="detail-item-value">14-Day Chronic Disease Rehab</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Package Code</span><span class="detail-item-value">TCM-14D-REHAB</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Total Cost</span><span class="detail-item-value">$3,200 USD</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Paid Amount</span><span class="detail-item-value" style="color:var(--vida-success)">$1,600 (50%)</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Balance Due</span><span class="detail-item-value" style="color:var(--vida-danger);font-weight:700">$1,600</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Insurance</span><span class="detail-item-value">Ingosstrakh (Russia) — Policy #7849201</span></div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div id="tabMedical" class="tab-pane" style="padding:24px">
                                <div style="display:flex;flex-direction:column;gap:16px">
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:12px"><i class="fas fa-notes-medical" style="color:var(--vida-primary);margin-right:8px"></i>Medical Conditions</h4>
                                        <div style="display:flex;flex-wrap:wrap;gap:8px">
                                            <span class="badge badge-gray">Hypertension (Stage 2)</span>
                                            <span class="badge badge-gray">Type 2 Diabetes</span>
                                            <span class="badge badge-gray">Chronic Lower Back Pain</span>
                                            <span class="badge badge-gray">Insomnia</span>
                                        </div>
                                    </div>
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:12px"><i class="fas fa-pills" style="color:var(--vida-primary);margin-right:8px"></i>Current Medications</h4>
                                        <p style="font-size:13px;color:var(--vida-gray-600);line-height:1.6">Amlodipine 5mg daily, Metformin 500mg BID, Meloxicam 7.5mg PRN. Patient reports herbal supplement use (Valerian root, Motherwort). No known drug allergies.</p>
                                    </div>
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:12px"><i class="fas fa-allergies" style="color:var(--vida-primary);margin-right:8px"></i>Allergies & Contraindications</h4>
                                        <p style="font-size:13px;color:var(--vida-gray-600);line-height:1.6">No known allergies. Contraindicated for moxibustion on lower back (skin sensitivity). Avoid strong purgative herbal formulas.</p>
                                    </div>
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:12px"><i class="fas fa-file-medical" style="color:var(--vida-primary);margin-right:8px"></i>Prior Surgeries</h4>
                                        <p style="font-size:13px;color:var(--vida-gray-600);line-height:1.6">Appendectomy (2015, Moscow). Cholecystectomy (2019, St. Petersburg). No complications.</p>
                                    </div>
                                </div>
                            </div>

                            <div id="tabTravel" class="tab-pane" style="padding:24px">
                                <div class="grid-2" style="gap:24px">
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:14px"><i class="fas fa-plane" style="color:var(--vida-primary);margin-right:8px"></i>Flight Details</h4>
                                        <div style="display:flex;flex-direction:column;gap:0">
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Airline</span><span class="detail-item-value">Aeroflot (SU)</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Flight Number</span><span class="detail-item-value">SU501</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Departure</span><span class="detail-item-value">SVO (Moscow) — Jun 8, 08:45 MSK</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Arrival</span><span class="detail-item-value">SYX (Sanya) — Jun 8, 14:30 CST</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Booking Ref</span><span class="detail-item-value">SU-7849201A</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Class</span><span class="detail-item-value">Business (requested by patient)</span></div>
                                        </div>
                                    </div>
                                    <div>
                                        <h4 style="font-size:15px;font-weight:700;margin-bottom:14px"><i class="fas fa-hotel" style="color:var(--vida-primary);margin-right:8px"></i>Accommodation</h4>
                                        <div style="display:flex;flex-direction:column;gap:0">
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Property</span><span class="detail-item-value">Sanya Marriott Yalong Bay Resort</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Room Type</span><span class="detail-item-value">Deluxe Ocean View, King</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Check-in</span><span class="detail-item-value">June 8, 2026</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Check-out</span><span class="detail-item-value">June 25, 2026 (17 nights)</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Booking Ref</span><span class="detail-item-value">MR-2026-SY-8892</span></div>
                                            <div class="detail-item" style="padding:10px 0"><span class="detail-item-label">Special Requests</span><span class="detail-item-value">Ground floor, near elevator, non-smoking</span></div>
                                        </div>
                                    </div>
                                </div>
                                <div style="margin-top:20px;padding:16px;background:var(--vida-primary-light);border-radius:var(--radius-lg)">
                                    <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
                                        <i class="fas fa-car" style="color:var(--vida-primary)"></i>
                                        <span style="font-weight:600;font-size:14px">Airport Transfer</span>
                                    </div>
                                    <p style="font-size:13px;color:var(--vida-gray-600)">Driver: Li Wei (李伟) · Vehicle: Mercedes V-Class · Pickup: SYX Gate 3, 15:00 CST · Contact: +86-138-0013-8000</p>
                                </div>
                            </div>

                            <div id="tabFinancial" class="tab-pane" style="padding:24px">
                                <div class="table-wrap">
                                    <table class="data-table">
                                        <thead>
                                            <tr>
                                                <th>Date</th>
                                                <th>Description</th>
                                                <th>Currency</th>
                                                <th>Amount</th>
                                                <th>Method</th>
                                                <th>Status</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            <tr>
                                                <td>Jun 1, 2026</td>
                                                <td>TCM Chronic Rehab — 50% Deposit</td>
                                                <td>USD</td>
                                                <td style="color:var(--vida-success);font-weight:700">+$1,600.00</td>
                                                <td><span class="badge badge-gray" style="font-size:10px"><i class="fab fa-cc-visa" style="margin-right:4px"></i>Stripe</span></td>
                                                <td><span class="badge badge-green"><span class="badge-dot green"></span> Completed</span></td>
                                            </tr>
                                            <tr>
                                                <td>May 28, 2026</td>
                                                <td>Consultation Fee (Telemedicine)</td>
                                                <td>USD</td>
                                                <td style="color:var(--vida-success);font-weight:700">+$150.00</td>
                                                <td><span class="badge badge-gray" style="font-size:10px"><i class="fab fa-cc-visa" style="margin-right:4px"></i>Stripe</span></td>
                                                <td><span class="badge badge-green"><span class="badge-dot green"></span> Completed</span></td>
                                            </tr>
                                            <tr>
                                                <td>May 20, 2026</td>
                                                <td>Medical Records Translation (RU→ZH)</td>
                                                <td>USD</td>
                                                <td style="color:var(--vida-success);font-weight:700">+$85.00</td>
                                                <td><span class="badge badge-gray" style="font-size:10px"><i class="fab fa-cc-visa" style="margin-right:4px"></i>Stripe</span></td>
                                                <td><span class="badge badge-green"><span class="badge-dot green"></span> Completed</span></td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                                <div style="margin-top:20px;padding:16px;background:var(--vida-gray-50);border-radius:var(--radius-lg)">
                                    <div class="flex-between">
                                        <div>
                                            <div style="font-size:13px;font-weight:600;color:var(--vida-gray-700)">Outstanding Balance</div>
                                            <div style="font-size:12px;color:var(--vida-gray-500)">Due before admission: June 10, 2026</div>
                                        </div>
                                        <div style="font-size:22px;font-weight:800;color:var(--vida-danger)">$1,600.00</div>
                                    </div>
                                </div>
                            </div>

                            <div id="tabTimeline" class="tab-pane" style="padding:24px">
                                <div class="timeline">
                                    <div class="timeline-item">
                                        <div class="timeline-dot teal"><i class="fas fa-clipboard-list"></i></div>
                                        <div class="timeline-content">
                                            <h4>Inquiry Received</h4>
                                            <p>Website inquiry form submitted from Moscow. Treatment interest: TCM chronic disease rehabilitation. Self-assessed urgency: medium.</p>
                                            <span class="timeline-time">May 10, 2026 · Automated</span>
                                        </div>
                                    </div>
                                    <div class="timeline-item">
                                        <div class="timeline-dot purple"><i class="fas fa-user-md"></i></div>
                                        <div class="timeline-content">
                                            <h4>Medical Review Completed</h4>
                                            <p>Dr. Zhang Wei reviewed medical records (translated RU→ZH). Approved for 14-day TCM chronic rehab program. TCM constitution: Qi Deficiency.</p>
                                            <span class="timeline-time">May 15, 2026 · Dr. Zhang Wei</span>
                                        </div>
                                    </div>
                                    <div class="timeline-item">
                                        <div class="timeline-dot amber"><i class="fas fa-file-signature"></i></div>
                                        <div class="timeline-content">
                                            <h4>Package Confirmed & Deposit Paid</h4>
                                            <p>Patient accepted TCM-14D-REHAB package ($3,200). 50% deposit ($1,600) received via Stripe. Visa-free entry confirmed (Russian passport, 30 days).</p>
                                            <span class="timeline-time">May 20, 2026 · Elena Wang</span>
                                        </div>
                                    </div>
                                    <div class="timeline-item">
                                        <div class="timeline-dot blue"><i class="fas fa-plane"></i></div>
                                        <div class="timeline-content">
                                            <h4>Travel Arranged</h4>
                                            <p>Flight SU501 Moscow→Sanya booked. Hotel: Sanya Marriott Yalong Bay (17 nights). Airport transfer assigned to Li Wei. Interpreter: Wang Fang (RU/ZH).</p>
                                            <span class="timeline-time">Jun 1, 2026 · Operations Team</span>
                                        </div>
                                    </div>
                                    <div class="timeline-item">
                                        <div class="timeline-dot green"><i class="fas fa-hospital"></i></div>
                                        <div class="timeline-content">
                                            <h4>Pre-Arrival Briefing Sent</h4>
                                            <p>Patient received: arrival guide (RU), hospital orientation video, emergency contacts, WeChat group invitation (patient + coordinator + interpreter + doctor).</p>
                                            <span class="timeline-time">Jun 5, 2026 · Automated</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

        </div>
    </main>

    <!-- ===== MODALS ===== -->
    <!-- Add Patient Modal -->
    <div class="modal-overlay" id="modalAddPatient">
        <div class="modal">
            <div class="modal-header">
                <h3 class="modal-title"><i class="fas fa-user-plus" style="color:var(--vida-primary);margin-right:10px"></i>Add New Patient</h3>
                <button class="modal-close" onclick="closeModal('modalAddPatient')"><i class="fas fa-times"></i></button>
            </div>
            <div class="modal-body">
                <div class="form-grid">
                    <div class="form-group">
                        <label class="form-label">First Name <span class="required">*</span></label>
                        <input type="text" class="form-input" placeholder="e.g. Anna">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Last Name <span class="required">*</span></label>
                        <input type="text" class="form-input" placeholder="e.g. Kovaleva">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Email <span class="required">*</span></label>
                        <input type="email" class="form-input" placeholder="patient@email.com">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Phone (E.164 format) <span class="required">*</span></label>
                        <input type="tel" class="form-input" placeholder="+7-916-555-0000">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Nationality <span class="required">*</span></label>
                        <select class="form-select">
                            <option>Select country</option>
                            <option selected>Russia</option>
                            <option>Kazakhstan</option>
                            <option>UAE</option>
                            <option>Germany</option>
                            <option>United Kingdom</option>
                            <option>United States</option>
                            <option>Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Date of Birth <span class="required">*</span></label>
                        <input type="date" class="form-input">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Treatment Interest <span class="required">*</span></label>
                        <select class="form-select">
                            <option>Select treatment</option>
                            <option>TCM Chronic Rehab (14-day)</option>
                            <option>TCM Wellness Retreat (7-day)</option>
                            <option>Integrative Cardiac Recovery (21-day)</option>
                            <option>IVF & Fertility (3 cycles)</option>
                            <option>Anti-Aging & Regeneration (10-day)</option>
                            <option>Dental Implants (Full Set)</option>
                            <option>Other — specify in notes</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Priority</label>
                        <select class="form-select">
                            <option>Low</option>
                            <option selected>Medium</option>
                            <option>High</option>
                            <option>Urgent</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Preferred Language</label>
                        <select class="form-select">
                            <option selected>Russian</option>
                            <option>English</option>
                            <option>Chinese (中文)</option>
                            <option>German</option>
                            <option>Arabic</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Preferred Contact</label>
                        <select class="form-select">
                            <option selected>WhatsApp</option>
                            <option>WeChat</option>
                            <option>Email</option>
                            <option>Phone</option>
                        </select>
                    </div>
                    <div class="form-group full">
                        <label class="form-label">Medical Condition / Inquiry Notes</label>
                        <textarea class="form-textarea" placeholder="Describe the patient's medical condition, symptoms, prior treatments, and specific interests..."></textarea>
                    </div>
                    <div class="form-group full">
                        <label class="form-label">Source Channel</label>
                        <select class="form-select">
                            <option>Website Inquiry Form</option>
                            <option>WhatsApp Direct</option>
                            <option>WeChat Official Account</option>
                            <option>Email</option>
                            <option>Phone Call</option>
                            <option>Partner Referral</option>
                            <option>Trade Show / Expo</option>
                            <option>Walk-in</option>
                        </select>
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" onclick="closeModal('modalAddPatient')">Cancel</button>
                <button class="btn btn-primary"><i class="fas fa-user-plus"></i> Add Patient</button>
            </div>
        </div>
    </div>

    <!-- Add Package Modal -->
    <div class="modal-overlay" id="modalAddPackage">
        <div class="modal">
            <div class="modal-header">
                <h3 class="modal-title"><i class="fas fa-plus-circle" style="color:var(--vida-primary);margin-right:10px"></i>Create Treatment Package</h3>
                <button class="modal-close" onclick="closeModal('modalAddPackage')"><i class="fas fa-times"></i></button>
            </div>
            <div class="modal-body">
                <div class="form-grid">
                    <div class="form-group full">
                        <label class="form-label">Package Name (English) <span class="required">*</span></label>
                        <input type="text" class="form-input" placeholder="e.g. 14-Day Chronic Disease Rehabilitation">
                    </div>
                    <div class="form-group full">
                        <label class="form-label">Package Name (Russian)</label>
                        <input type="text" class="form-input" placeholder="e.g. 14-дневная реабилитация хронических заболеваний">
                    </div>
                    <div class="form-group full">
                        <label class="form-label">Package Name (Chinese)</label>
                        <input type="text" class="form-input" placeholder="e.g. 14天慢性病康复套餐">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Hospital <span class="required">*</span></label>
                        <select class="form-select">
                            <option>Select hospital</option>
                            <option>Sanya TCM Hospital (三亚市中医院)</option>
                            <option>Hainan Boao Lecheng (海南博鳌乐城)</option>
                            <option>Sanya Women & Children (三亚市妇幼保健院)</option>
                            <option>Sanya Stomatology Center (三亚市口腔医院)</option>
                            <option>Hainan International Health Center (海南国际健康中心)</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Category <span class="required">*</span></label>
                        <select class="form-select">
                            <option>Select category</option>
                            <option>TCM Wellness</option>
                            <option>TCM Chronic Rehab</option>
                            <option>Integrative Cardiac</option>
                            <option>IVF & Fertility</option>
                            <option>Anti-Aging & Regeneration</option>
                            <option>Dental & Cosmetic</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Duration (Days) <span class="required">*</span></label>
                        <input type="number" class="form-input" placeholder="14">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Base Price (USD) <span class="required">*</span></label>
                        <input type="number" class="form-input" placeholder="3200.00">
                    </div>
                    <div class="form-group full">
                        <label class="form-label">Included Treatments & Services</label>
                        <div style="display:flex;flex-wrap:wrap;gap:8px;margin-top:6px">
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Acupuncture</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Tuina Massage</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Herbal Medicine</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Moxibustion</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Cupping Therapy</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Tai Chi Class</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Dietary Therapy</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Solar Therapy</label>
                        </div>
                    </div>
                    <div class="form-group full">
                        <label class="form-label">Included Logistics</label>
                        <div style="display:flex;flex-wrap:wrap;gap:8px;margin-top:6px">
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox" checked> Airport Transfer</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox" checked> Accommodation (4-star)</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox" checked> Interpreter (Medical)</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> City Tour</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> Travel Insurance</label>
                            <label style="display:flex;align-items:center;gap:6px;padding:6px 12px;background:var(--vida-gray-100);border-radius:var(--radius-md);font-size:13px;cursor:pointer"><input type="checkbox"> VIP Suite Upgrade</label>
                        </div>
                    </div>
                    <div class="form-group full">
                        <label class="form-label">Description</label>
                        <textarea class="form-textarea" placeholder="Describe the treatment package, target conditions, expected outcomes, and unique selling points..."></textarea>
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" onclick="closeModal('modalAddPackage')">Cancel</button>
                <button class="btn btn-primary"><i class="fas fa-plus-circle"></i> Create Package</button>
            </div>
        </div>
    </div>

    <script>
        // ===== SECTION NAVIGATION =====
        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
            // Show target section
            const target = document.getElementById(sectionId);
            if (target) target.classList.add('active');

            // Update sidebar nav
            document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
            const navMap = {
                'dashboard': 0, 'patients': 1, 'pipeline': 2, 'packages': 3,
                'calendar': 4, 'communications': 5, 'documents': 6, 'finance': 7,
                'hospitals': 8, 'reports': 9, 'settings': 10
            };
            const navItems = document.querySelectorAll('.nav-item');
            if (navMap[sectionId] !== undefined && navItems[navMap[sectionId]]) {
                navItems[navMap[sectionId]].classList.add('active');
            }

            window.scrollTo(0, 0);
        }

        // ===== TAB SWITCHING =====
        function switchTab(tabEl, paneId) {
            const parent = tabEl.closest('.card') || tabEl.parentElement;
            parent.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            tabEl.classList.add('active');

            parent.querySelectorAll('.tab-pane').forEach(p => p.classList.remove('active'));
            const pane = document.getElementById(paneId);
            if (pane) pane.classList.add('active');
        }

        // ===== MODALS =====
        function openModal(modalId) {
            const modal = document.getElementById(modalId);
            if (modal) {
                modal.classList.add('active');
                document.body.style.overflow = 'hidden';
            }
        }

        function closeModal(modalId) {
            const modal = document.getElementById(modalId);
            if (modal) {
                modal.classList.remove('active');
                document.body.style.overflow = '';
            }
        }

        // Close modal on overlay click
        document.querySelectorAll('.modal-overlay').forEach(overlay => {
            overlay.addEventListener('click', function(e) {
                if (e.target === this) {
                    this.classList.remove('active');
                    document.body.style.overflow = '';
                }
            });
        });

        // ===== PATIENT DETAIL =====
        const patientData = {
            anna: {
                name: 'Anna Kovaleva',
                id: 'VD-2026-0142',
                avatar: 'AK',
                nationality: 'Russia',
                flag: '🇷🇺',
                age: '54 years',
                treatment: 'TCM Chronic Rehab (14-day)',
                status: 'Travel Phase',
                statusClass: 'badge-teal',
                statusDot: 'teal',
                phone: '+7-916-555-0142',
                email: 'anna.k@mail.ru',
                passport: '75 12 345678',
                coordinator: 'Elena Wang',
                doctor: 'Dr. Zhang Wei (张伟)',
                hospital: 'Sanya TCM Hospital',
                package: '14-Day Chronic Disease Rehab',
                packageCode: 'TCM-14D-REHAB',
                totalCost: '$3,200 USD',
                paid: '$1,600 (50%)',
                balance: '$1,600',
                insurance: 'Ingosstrakh (Russia)',
                admission: 'June 10, 2026',
                discharge: 'June 24, 2026',
                tcmType: 'Qi Deficiency (气虚质)'
            },
            dmitry: {
                name: 'Dmitry Sokolov',
                id: 'VD-2026-0139',
                avatar: 'DS',
                nationality: 'Russia',
                flag: '🇷🇺',
                age: '62 years',
                treatment: 'Integrative Cardiac Recovery (21-day)',
                status: 'In Treatment',
                statusClass: 'badge-green',
                statusDot: 'green',
                phone: '+7-903-555-0139',
                email: 'd.sokolov@gmail.com',
                passport: '75 09 876543',
                coordinator: 'Elena Wang',
                doctor: 'Dr. Li Ming (李明)',
                hospital: 'Hainan Boao Lecheng',
                package: 'Integrative Cardiac Recovery',
                packageCode: 'INT-CARD-21D',
                totalCost: '$8,500 USD',
                paid: '$8,500 (100%)',
                balance: '$0',
                insurance: 'Sogaz (Russia)',
                admission: 'May 20, 2026',
                discharge: 'June 10, 2026',
                tcmType: 'Yang Deficiency (阳虚质)'
            },
            olga: {
                name: 'Olga Ivanova',
                id: 'VD-2026-0135',
                avatar: 'OI',
                nationality: 'Kazakhstan',
                flag: '🇰🇿',
                age: '38 years',
                treatment: 'IVF Treatment (3 cycles)',
                status: 'Consultation',
                statusClass: 'badge-purple',
                statusDot: 'purple',
                phone: '+7-777-555-0135',
                email: 'o.ivanova@yandex.kz',
                passport: 'N12345678',
                coordinator: 'Li Wei',
                doctor: 'Dr. Liu Fang (刘芳)',
                hospital: 'Sanya Women & Children',
                package: 'IVF & Fertility Package',
                packageCode: 'IVF-3C-14D',
                totalCost: '$12,800 USD',
                paid: '$500 (Consultation)',
                balance: '$12,300',
                insurance: 'None declared',
                admission: 'TBD',
                discharge: 'TBD',
                tcmType: 'Blood Deficiency (血虚质)'
            },
            mohammed: {
                name: 'Mohammed Al-Rashid',
                id: 'VD-2026-0128',
                avatar: 'MA',
                nationality: 'UAE',
                flag: '🇦🇪',
                age: '45 years',
                treatment: 'Anti-Aging & Regeneration (10-day)',
                status: 'Scheduled',
                statusClass: 'badge-amber',
                statusDot: 'amber',
                phone: '+971-50-555-0128',
                email: 'm.alrashid@emirates.ae',
                passport: 'P1234567',
                coordinator: 'Zhang Min',
                doctor: 'Dr. Wang Hua (王华)',
                hospital: 'Sanya TCM Hospital',
                package: 'Anti-Aging & Regeneration',
                packageCode: 'ANTI-AGE-10D',
                totalCost: '$6,200 USD',
                paid: '$4,100 (Deposit)',
                balance: '$2,100',
                insurance: 'Daman (UAE)',
                admission: 'June 17, 2026',
                discharge: 'June 27, 2026',
                tcmType: 'Yin Deficiency (阴虚质)'
            },
            liudmila: {
                name: 'Liudmila Petrova',
                id: 'VD-2026-0121',
                avatar: 'LP',
                nationality: 'Russia',
                flag: '🇷🇺',
                age: '29 years',
                treatment: 'TCM Wellness Retreat (7-day)',
                status: 'New Inquiry',
                statusClass: 'badge-blue',
                statusDot: 'blue',
                phone: '+7-925-555-0121',
                email: 'l.petrova@bk.ru',
                passport: '75 15 112233',
                coordinator: 'Unassigned',
                doctor: 'TBD',
                hospital: 'Sanya TCM Hospital',
                package: '7-Day Health Relaxation',
                packageCode: 'TCM-7D-RELAX',
                totalCost: '$1,800 USD',
                paid: '$0',
                balance: '$1,800',
                insurance: 'None declared',
                admission: 'TBD',
                discharge: 'TBD',
                tcmType: 'Balanced (平和质)'
            },
            sergey: {
                name: 'Sergey Volkov',
                id: 'VD-2026-0115',
                avatar: 'SV',
                nationality: 'Russia',
                flag: '🇷🇺',
                age: '58 years',
                treatment: 'TCM Chronic Rehab (21-day)',
                status: 'Post-Care',
                statusClass: 'badge-green',
                statusDot: 'green',
                phone: '+7-915-555-0115',
                email: 's.volkov@mail.ru',
                passport: '75 08 445566',
                coordinator: 'Elena Wang',
                doctor: 'Dr. Zhang Wei (张伟)',
                hospital: 'Sanya TCM Hospital',
                package: '21-Day Chronic Disease Rehab',
                packageCode: 'TCM-21D-REHAB',
                totalCost: '$4,800 USD',
                paid: '$4,800 (100%)',
                balance: '$0',
                insurance: 'Renaissance (Russia)',
                admission: 'April 20, 2026',
                discharge: 'May 10, 2026',
                tcmType: 'Phlegm-Dampness (痰湿质)'
            },
            natalia: {
                name: 'Natalia Kuznetsova',
                id: 'VD-2026-0108',
                avatar: 'NK',
                nationality: 'Russia',
                flag: '🇷🇺',
                age: '41 years',
                treatment: 'Dental Implants (Full Set)',
                status: 'Scheduled',
                statusClass: 'badge-amber',
                statusDot: 'amber',
                phone: '+7-926-555-0108',
                email: 'n.kuznetsova@gmail.com',
                passport: '75 07 778899',
                coordinator: 'Li Wei',
                doctor: 'Dr. Chen Jing (陈静)',
                hospital: 'Sanya Stomatology Center',
                package: 'Dental Implants Full Set',
                packageCode: 'DENT-FULL-SET',
                totalCost: '$6,500 USD',
                paid: '$6,500 (100%)',
                balance: '$0',
                insurance: 'Ingosstrakh Dental',
                admission: 'June 15, 2026',
                discharge: 'June 20, 2026',
                tcmType: 'N/A'
            }
        };

        function showPatientDetail(patientKey) {
            const d = patientData[patientKey];
            if (!d) return;

            document.getElementById('detailName').textContent = d.name;
            document.getElementById('detailId').textContent = 'ID: ' + d.id;
            document.getElementById('detailAvatar').textContent = d.avatar;
            document.getElementById('detailPatientName').textContent = d.name;
            document.getElementById('detailPatientId').textContent = 'ID: ' + d.id;
            document.getElementById('detailStatusBadge').innerHTML = '<span class="badge ' + d.statusClass + '"><span class="badge-dot ' + d.statusDot + '"></span> ' + d.status + '</span>';
            document.getElementById('detailNationality').innerHTML = '<span style="margin-right:4px">' + d.flag + '</span> ' + d.nationality;
            document.getElementById('detailAge').textContent = d.age;
            document.getElementById('detailTreatment').textContent = d.treatment;

            showSection('patient-detail');
        }

        // ===== KEYBOARD SHORTCUTS =====
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                document.querySelectorAll('.modal-overlay.active').forEach(m => {
                    m.classList.remove('active');
                    document.body.style.overflow = '';
                });
            }
        });
    </script>
</body>
</html>
