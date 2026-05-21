<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>秦腔 - 大秦之音，华夏正声</title>
    <style>
        :root {
            --bg-deep: #1a0a0a;
            --bg-dark: #2d1414;
            --bg-medium: #3d1c1c;
            --red-primary: #b5343a;
            --red-bright: #d4443f;
            --red-dark: #7a1f23;
            --gold: #c9a96e;
            --gold-light: #e0c88a;
            --gold-dark: #8b6f3f;
            --cream: #f5f0e8;
            --text-light: #e8d5c8;
            --text-muted: #c4a992;
            --text-dark: #2c1810;
            --white: #fefaf5;
            --shadow-strong: 0 8px 32px rgba(0, 0, 0, 0.5);
            --shadow-gold: 0 4px 20px rgba(201, 169, 110, 0.3);
            --transition-smooth: cubic-bezier(0.4, 0, 0.2, 1);
            --font-display: 'STSong', 'Songti SC', 'Noto Serif SC', 'SimSun', 'KaiTi', 'STKaiti', '楷体', '华文楷体', serif;
            --font-body: 'PingFang SC', 'Microsoft YaHei', 'Hiragino Sans GB', 'STHeiti', '华文细黑', sans-serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
            font-size: 16px;
        }

        body {
            font-family: var(--font-body);
            background: var(--bg-deep);
            color: var(--text-light);
            overflow-x: hidden;
            line-height: 1.7;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* ============ 背景装饰 ============ */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            background:
                radial-gradient(ellipse at 20% 20%, rgba(180, 50, 45, 0.08) 0%, transparent 50%),
                radial-gradient(ellipse at 80% 60%, rgba(201, 169, 110, 0.06) 0%, transparent 50%),
                radial-gradient(ellipse at 50% 80%, rgba(180, 50, 45, 0.05) 0%, transparent 50%);
        }

        /* 背景纹理 */
        .bg-texture {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -2;
            opacity: 0.03;
            background-image: repeating-linear-gradient(0deg,
                    transparent,
                    transparent 2px,
                    rgba(201, 169, 110, 0.5) 2px,
                    rgba(201, 169, 110, 0.5) 2.5px),
                repeating-linear-gradient(90deg,
                    transparent,
                    transparent 2px,
                    rgba(201, 169, 110, 0.5) 2px,
                    rgba(201, 169, 110, 0.5) 2.5px);
        }

        /* ============ 顶部帷幕装饰 ============ */
        .stage-curtain-top {
            position: fixed;
            top: -5px;
            left: -5%;
            width: 110%;
            height: 70px;
            pointer-events: none;
            z-index: 999;
            background: linear-gradient(180deg,
                    #3d0c0c 0%, #5a1515 15%, #7a1f23 30%, #8b2025 45%,
                    #6b181c 60%, #4a1014 75%, #2d0a0c 90%, transparent 100%);
            box-shadow: 0 6px 30px rgba(0, 0, 0, 0.7);
            border-bottom: 3px solid #c9a96e;
            animation: curtainGlow 4s ease-in-out infinite;
        }
        @keyframes curtainGlow {
            0%,
            100% {
                border-bottom-color: #c9a96e;
                box-shadow: 0 6px 30px rgba(0, 0, 0, 0.7), 0 2px 15px rgba(201, 169, 110, 0.2);
            }
            50% {
                border-bottom-color: #e0c88a;
                box-shadow: 0 6px 30px rgba(0, 0, 0, 0.7), 0 2px 25px rgba(201, 169, 110, 0.45);
            }
        }
        .stage-curtain-top::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 100%;
            height: 16px;
            background: repeating-linear-gradient(90deg,
                    transparent,
                    transparent 18px,
                    #c9a96e 18px,
                    #c9a96e 22px,
                    transparent 22px,
                    transparent 40px);
            opacity: 0.7;
        }

        /* ============ 导航栏 ============ */
        .main-nav {
            position: fixed;
            top: 55px;
            left: 0;
            right: 0;
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 6px;
            padding: 10px 20px;
            flex-wrap: wrap;
            background: rgba(20, 8, 8, 0.85);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border-bottom: 1px solid rgba(201, 169, 110, 0.25);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
            transition: all 0.4s var(--transition-smooth);
        }
        .main-nav.scrolled {
            top: 0;
            background: rgba(20, 8, 8, 0.95);
            padding: 8px 20px;
            box-shadow: 0 4px 25px rgba(0, 0, 0, 0.7);
        }
        .nav-item {
            position: relative;
            padding: 9px 18px;
            font-family: var(--font-display);
            font-size: 0.95rem;
            color: var(--text-muted);
            cursor: pointer;
            border: none;
            background: transparent;
            letter-spacing: 0.05em;
            transition: all 0.35s var(--transition-smooth);
            white-space: nowrap;
            border-radius: 4px;
            text-decoration: none;
            outline: none;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }
        .nav-item:hover {
            color: var(--gold-light);
            background: rgba(201, 169, 110, 0.08);
            transform: translateY(-1px);
        }
        .nav-item.active {
            color: #fff;
            background: rgba(180, 50, 45, 0.35);
            font-weight: bold;
            box-shadow: 0 0 20px rgba(180, 50, 45, 0.3);
        }
        .nav-item.active::after {
            content: '';
            position: absolute;
            bottom: 2px;
            left: 50%;
            transform: translateX(-50%);
            width: 24px;
            height: 3px;
            background: var(--gold);
            border-radius: 2px;
            box-shadow: 0 0 10px rgba(201, 169, 110, 0.7);
        }
        .nav-item .nav-icon {
            display: block;
            font-size: 1.1rem;
            margin-bottom: 2px;
            text-align: center;
        }
        .nav-item .nav-label {
            display: block;
            font-size: 0.78rem;
            letter-spacing: 0.06em;
        }

        /* 移动端导航汉堡按钮 */
        .nav-toggle-btn {
            display: none;
            position: fixed;
            top: 60px;
            right: 15px;
            z-index: 1001;
            width: 42px;
            height: 42px;
            border-radius: 50%;
            background: rgba(180, 50, 45, 0.85);
            border: 2px solid var(--gold);
            cursor: pointer;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 5px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
        }
        .nav-toggle-btn span {
            display: block;
            width: 20px;
            height: 2px;
            background: var(--gold-light);
            border-radius: 1px;
            transition: all 0.3s ease;
        }
        .nav-toggle-btn.open span:nth-child(1) {
            transform: rotate(45deg) translate(5px, 5px);
        }
        .nav-toggle-btn.open span:nth-child(2) {
            opacity: 0;
        }
        .nav-toggle-btn.open span:nth-child(3) {
            transform: rotate(-45deg) translate(5px, -5px);
        }

        /* ============ 页面容器 ============ */
        .page-container {
            padding-top: 140px;
            min-height: 100vh;
        }
        .page {
            display: none;
            animation: pageFadeIn 0.55s var(--transition-smooth) forwards;
            padding: 20px 30px 60px;
            max-width: 1200px;
            margin: 0 auto;
            min-height: 70vh;
        }
        .page.active {
            display: block;
        }
        @keyframes pageFadeIn {
            from {
                opacity: 0;
                transform: translateY(25px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* ============ 首页样式 ============ */
        .home-hero {
            text-align: center;
            padding: 40px 20px;
            position: relative;
        }
        .home-hero .hero-emblem {
            display: inline-block;
            font-size: 5rem;
            animation: emblemFloat 3s ease-in-out infinite;
            filter: drop-shadow(0 8px 24px rgba(180, 50, 45, 0.5));
            line-height: 1;
        }
        @keyframes emblemFloat {
            0%,
            100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-14px);
            }
        }
        .home-hero .hero-title {
            font-family: var(--font-display);
            font-size: clamp(3rem, 7vw, 5.5rem);
            font-weight: bold;
            color: #fff;
            letter-spacing: 0.12em;
            margin: 10px 0;
            text-shadow: 0 0 40px rgba(201, 169, 110, 0.6), 0 4px 8px rgba(0, 0, 0, 0.6);
            line-height: 1.2;
        }
        .home-hero .hero-subtitle {
            font-family: var(--font-display);
            font-size: clamp(1.1rem, 2.2vw, 1.5rem);
            color: var(--gold-light);
            letter-spacing: 0.2em;
            margin-bottom: 8px;
        }
        .home-hero .hero-desc {
            font-size: 1.05rem;
            color: var(--text-muted);
            max-width: 650px;
            margin: 16px auto 30px;
            line-height: 1.8;
        }
        .home-hero .hero-divider {
            width: 120px;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--gold), transparent);
            margin: 0 auto 20px;
            border-radius: 1px;
        }

        /* 首页导航卡片 */
        .home-cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(170px, 1fr));
            gap: 18px;
            max-width: 1000px;
            margin: 0 auto;
        }
        .home-card {
            background: linear-gradient(160deg, rgba(45, 20, 20, 0.85), rgba(30, 10, 10, 0.9));
            border: 1px solid rgba(201, 169, 110, 0.2);
            border-radius: 12px;
            padding: 24px 16px;
            text-align: center;
            cursor: pointer;
            transition: all 0.4s var(--transition-smooth);
            position: relative;
            overflow: hidden;
            text-decoration: none;
            color: inherit;
            display: block;
            -webkit-tap-highlight-color: transparent;
        }
        .home-card:hover {
            transform: translateY(-6px);
            border-color: var(--gold);
            box-shadow: var(--shadow-gold), 0 12px 35px rgba(0, 0, 0, 0.5);
            background: linear-gradient(160deg, rgba(60, 25, 25, 0.9), rgba(40, 12, 12, 0.95));
        }
        .home-card:active {
            transform: scale(0.96);
            transition: all 0.15s ease;
        }
        .home-card .card-icon {
            font-size: 2.8rem;
            display: block;
            margin-bottom: 10px;
            transition: transform 0.4s var(--transition-smooth);
        }
        .home-card:hover .card-icon {
            transform: scale(1.15);
        }
        .home-card .card-title {
            font-family: var(--font-display);
            font-size: 1.1rem;
            color: #fff;
            letter-spacing: 0.05em;
            margin-bottom: 4px;
        }
        .home-card .card-hint {
            font-size: 0.75rem;
            color: var(--text-muted);
            letter-spacing: 0.04em;
        }
        .home-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(201, 169, 110, 0.06) 0%, transparent 70%);
            opacity: 0;
            transition: opacity 0.4s ease;
            pointer-events: none;
        }
        .home-card:hover::before {
            opacity: 1;
        }

        /* ============ 详情页通用样式 ============ */
        .page-header {
            text-align: center;
            margin-bottom: 40px;
        }
        .page-header .page-icon {
            font-size: 3.2rem;
            display: block;
            margin-bottom: 6px;
        }
        .page-header h2 {
            font-family: var(--font-display);
            font-size: clamp(2rem, 4vw, 2.8rem);
            color: #fff;
            letter-spacing: 0.08em;
            margin-bottom: 6px;
            text-shadow: 0 0 25px rgba(201, 169, 110, 0.4);
        }
        .page-header .page-subtitle {
            color: var(--gold-light);
            font-size: 1rem;
            letter-spacing: 0.1em;
            font-family: var(--font-display);
        }
        .page-header .divider-line {
            width: 80px;
            height: 2px;
            background: var(--gold);
            margin: 12px auto 0;
            border-radius: 1px;
            opacity: 0.7;
        }

        /* 内容区块 */
        .content-block {
            background: rgba(35, 15, 15, 0.6);
            border: 1px solid rgba(201, 169, 110, 0.15);
            border-radius: 14px;
            padding: 28px;
            margin-bottom: 24px;
            transition: all 0.35s ease;
            position: relative;
            overflow: hidden;
        }
        .content-block:hover {
            border-color: rgba(201, 169, 110, 0.35);
            box-shadow: 0 4px 25px rgba(0, 0, 0, 0.4);
        }
        .content-block h3 {
            font-family: var(--font-display);
            font-size: 1.35rem;
            color: var(--gold-light);
            margin-bottom: 10px;
            letter-spacing: 0.04em;
        }
        .content-block p {
            color: var(--text-muted);
            line-height: 1.85;
            font-size: 0.98rem;
        }
        .content-block .highlight {
            color: var(--gold-light);
            font-weight: bold;
        }

        /* 图文搭配 - 图片占位 */
        .image-placeholder {
            width: 100%;
            aspect-ratio: 16/9;
            max-height: 380px;
            border-radius: 10px;
            background: linear-gradient(135deg, #3d1c1c 0%, #5a2525 25%, #4a1a1a 50%, #3d1515 75%, #2d1010 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5rem;
            color: rgba(201, 169, 110, 0.4);
            border: 2px dashed rgba(201, 169, 110, 0.25);
            position: relative;
            overflow: hidden;
            transition: all 0.5s ease;
        }
        .image-placeholder::after {
            content: '';
            position: absolute;
            inset: 0;
            background: radial-gradient(ellipse at center, rgba(201, 169, 110, 0.08) 0%, transparent 70%);
            pointer-events: none;
        }
        .image-placeholder.small {
            aspect-ratio: 1/1;
            max-height: 200px;
            font-size: 3.5rem;
        }
        .image-placeholder.portrait {
            aspect-ratio: 3/4;
            max-height: 350px;
            font-size: 4rem;
        }

        /* 双栏布局 */
        .two-col {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
            align-items: center;
        }
        .three-col {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }
        .four-col {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 16px;
        }

        /* 时间线 */
        .timeline {
            position: relative;
            padding-left: 40px;
            border-left: 2px solid rgba(201, 169, 110, 0.3);
            margin-left: 20px;
        }
        .timeline-item {
            position: relative;
            margin-bottom: 28px;
            padding-left: 20px;
        }
        .timeline-item::before {
            content: '';
            position: absolute;
            left: -47px;
            top: 5px;
            width: 12px;
            height: 12px;
            background: var(--red-bright);
            border-radius: 50%;
            border: 2px solid var(--gold);
            box-shadow: 0 0 12px rgba(180, 50, 45, 0.6);
        }
        .timeline-item .timeline-year {
            font-family: var(--font-display);
            font-size: 1.1rem;
            color: var(--gold-light);
            font-weight: bold;
            letter-spacing: 0.05em;
        }
        .timeline-item p {
            color: var(--text-muted);
            margin-top: 4px;
            font-size: 0.93rem;
        }

        /* 卡片 */
        .info-card {
            background: rgba(40, 18, 18, 0.7);
            border: 1px solid rgba(201, 169, 110, 0.18);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            transition: all 0.35s var(--transition-smooth);
            cursor: default;
        }
        .info-card:hover {
            transform: translateY(-4px);
            border-color: var(--gold);
            box-shadow: var(--shadow-gold);
            background: rgba(50, 22, 22, 0.8);
        }
        .info-card .card-emoji {
            font-size: 2.5rem;
            display: block;
            margin-bottom: 8px;
        }
        .info-card h4 {
            font-family: var(--font-display);
            color: #fff;
            font-size: 1.05rem;
            margin-bottom: 4px;
            letter-spacing: 0.04em;
        }
        .info-card p {
            font-size: 0.85rem;
            color: var(--text-muted);
            line-height: 1.6;
        }

        /* 引用块 */
        .quote-block {
            background: rgba(180, 50, 45, 0.1);
            border-left: 4px solid var(--gold);
            padding: 20px 24px;
            border-radius: 0 10px 10px 0;
            margin: 20px 0;
            font-family: var(--font-display);
            font-style: italic;
            color: var(--gold-light);
            font-size: 1.05rem;
            letter-spacing: 0.03em;
            position: relative;
        }
        .quote-block::before {
            content: '"';
            position: absolute;
            top: -10px;
            left: 12px;
            font-size: 3rem;
            color: rgba(201, 169, 110, 0.25);
            font-family: serif;
            line-height: 1;
        }

        /* 标签 */
        .tag {
            display: inline-block;
            padding: 5px 14px;
            background: rgba(180, 50, 45, 0.25);
            color: var(--gold-light);
            border-radius: 20px;
            font-size: 0.82rem;
            letter-spacing: 0.04em;
            margin: 3px 4px;
            border: 1px solid rgba(201, 169, 110, 0.3);
            transition: all 0.3s ease;
        }
        .tag:hover {
            background: rgba(180, 50, 45, 0.45);
            border-color: var(--gold);
            cursor: pointer;
        }

        /* 返回顶部按钮 */
        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            z-index: 999;
            width: 46px;
            height: 46px;
            border-radius: 50%;
            background: rgba(180, 50, 45, 0.8);
            border: 2px solid var(--gold);
            color: var(--gold-light);
            font-size: 1.3rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.35s ease;
            opacity: 0;
            pointer-events: none;
            box-shadow: 0 4px 18px rgba(0, 0, 0, 0.5);
        }
        .back-to-top.visible {
            opacity: 1;
            pointer-events: auto;
        }
        .back-to-top:hover {
            background: rgba(200, 55, 50, 0.9);
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.6), 0 0 20px rgba(201, 169, 110, 0.4);
        }

        /* 页脚 */
        .site-footer {
            text-align: center;
            padding: 30px;
            color: var(--text-muted);
            font-size: 0.8rem;
            letter-spacing: 0.05em;
            border-top: 1px solid rgba(201, 169, 110, 0.15);
            margin-top: 40px;
        }

        /* ============ 响应式 ============ */
        @media (max-width: 900px) {
            .two-col,
            .three-col {
                grid-template-columns: 1fr;
            }
            .four-col {
                grid-template-columns: repeat(2, 1fr);
            }
            .main-nav {
                gap: 2px;
                padding: 8px 8px;
                top: 45px;
                flex-wrap: nowrap;
                overflow-x: auto;
                justify-content: flex-start;
                -webkit-overflow-scrolling: touch;
                scrollbar-width: none;
                mask-image: linear-gradient(90deg, transparent 0%, black 5%, black 95%, transparent 100%);
                -webkit-mask-image: linear-gradient(90deg, transparent 0%, black 5%, black 95%, transparent 100%);
            }
            .main-nav::-webkit-scrollbar {
                display: none;
            }
            .nav-item {
                padding: 8px 11px;
                font-size: 0.75rem;
                flex-shrink: 0;
            }
            .nav-item .nav-icon {
                font-size: 0.9rem;
            }
            .nav-item .nav-label {
                font-size: 0.68rem;
            }
            .nav-toggle-btn {
                display: flex;
            }
            .page-container {
                padding-top: 120px;
            }
            .page {
                padding: 15px 12px 40px;
            }
            .home-cards-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 10px;
            }
            .home-card {
                padding: 16px 10px;
            }
            .home-card .card-icon {
                font-size: 2rem;
            }
            .timeline {
                padding-left: 25px;
                margin-left: 10px;
            }
            .timeline-item::before {
                left: -32px;
                width: 10px;
                height: 10px;
            }
            .image-placeholder {
                aspect-ratio: 4/3;
                max-height: 220px;
                font-size: 3rem;
            }
            .image-placeholder.portrait {
                max-height: 240px;
                font-size: 2.8rem;
            }
        }
        @media (max-width: 480px) {
            .home-cards-grid {
                grid-template-columns: 1fr 1fr;
                gap: 8px;
            }
            .home-card {
                padding: 12px 6px;
                border-radius: 8px;
            }
            .home-card .card-icon {
                font-size: 1.6rem;
            }
            .home-card .card-title {
                font-size: 0.85rem;
            }
            .home-card .card-hint {
                font-size: 0.65rem;
            }
            .home-hero .hero-title {
                font-size: 2.2rem;
            }
            .four-col {
                grid-template-columns: 1fr 1fr;
            }
            .content-block {
                padding: 16px;
            }
            .back-to-top {
                bottom: 18px;
                right: 14px;
                width: 38px;
                height: 38px;
                font-size: 1rem;
            }
            .stage-curtain-top {
                height: 40px;
            }
            .main-nav {
                top: 30px;
            }
            .page-container {
                padding-top: 100px;
            }
        }
    </style>
</head>
<body>
    <div class="bg-texture"></div>
    <div class="stage-curtain-top"></div>

    <!-- 导航栏 -->
    <nav class="main-nav" id="mainNav" role="navigation" aria-label="主导航">
        <button class="nav-item active" data-page="home" aria-current="page">
            <span class="nav-icon">🏠</span>
            <span class="nav-label">首页</span>
        </button>
        <button class="nav-item" data-page="history">
            <span class="nav-icon">📜</span>
            <span class="nav-label">历史渊源</span>
        </button>
        <button class="nav-item" data-page="art">
            <span class="nav-icon">🎭</span>
            <span class="nav-label">艺术特色</span>
        </button>
        <button class="nav-item" data-page="repertoire">
            <span class="nav-icon">🎬</span>
            <span class="nav-label">经典剧目</span>
        </button>
        <button class="nav-item" data-page="masters">
            <span class="nav-icon">🌟</span>
            <span class="nav-label">名家风采</span>
        </button>
        <button class="nav-item" data-page="visual">
            <span class="nav-icon">🎨</span>
            <span class="nav-label">脸谱服饰</span>
        </button>
        <button class="nav-item" data-page="future">
            <span class="nav-icon">🔥</span>
            <span class="nav-label">传承发展</span>
        </button>
    </nav>

    <!-- 移动端导航按钮 -->
    <button class="nav-toggle-btn" id="navToggleBtn" aria-label="菜单" title="展开导航菜单">
        <span></span><span></span><span></span>
    </button>

    <!-- 页面容器 -->
    <div class="page-container" id="pageContainer">

        <!-- ==================== 首页 ==================== -->
        <section class="page active" id="page-home" data-page="home">
            <div class="home-hero">
                <span class="hero-emblem">🎭</span>
                <h1 class="hero-title">秦 腔</h1>
                <p class="hero-subtitle">大秦之音 · 华夏正声</p>
                <div class="hero-divider"></div>
                <p class="hero-desc">
                    秦腔，中国最古老的戏曲剧种之一，源于周秦、成于唐宋、盛于明清，被誉为<strong style="color:#e0c88a;">"梆子戏鼻祖"</strong>。
                    其声腔高昂激越、粗犷豪放，承载着西北大地千年的文化魂魄，是国家级非物质文化遗产，更是中华民族的艺术瑰宝。
                </p>
            </div>
            <div class="home-cards-grid">
                <div class="home-card" data-nav="history">
                    <span class="card-icon">📜</span>
                    <div class="card-title">历史渊源</div>
                    <div class="card-hint">追溯千年根脉</div>
                </div>
                <div class="home-card" data-nav="art">
                    <span class="card-icon">🎭</span>
                    <div class="card-title">艺术特色</div>
                    <div class="card-hint">唱念做打之美</div>
                </div>
                <div class="home-card" data-nav="repertoire">
                    <span class="card-icon">🎬</span>
                    <div class="card-title">经典剧目</div>
                    <div class="card-hint">传世名篇赏析</div>
                </div>
                <div class="home-card" data-nav="masters">
                    <span class="card-icon">🌟</span>
                    <div class="card-title">名家风采</div>
                    <div class="card-hint">一代宗师列传</div>
                </div>
                <div class="home-card" data-nav="visual">
                    <span class="card-icon">🎨</span>
                    <div class="card-title">脸谱服饰</div>
                    <div class="card-hint">视觉艺术盛宴</div>
                </div>
                <div class="home-card" data-nav="future">
                    <span class="card-icon">🔥</span>
                    <div class="card-title">传承发展</div>
                    <div class="card-hint">古今交融创新</div>
                </div>
            </div>
        </section>

        <!-- ==================== 第2页：历史渊源 ==================== -->
        <section class="page" id="page-history" data-page="history">
            <div class="page-header">
                <span class="page-icon">📜</span>
                <h2>历史渊源</h2>
                <p class="page-subtitle">从周秦礼乐到梆子鼻祖</p>
                <div class="divider-line"></div>
            </div>
            <div class="two-col">
                <div class="image-placeholder" style="aspect-ratio:4/3;" aria-label="秦腔历史图片占位">🏛️</div>
                <div class="content-block">
                    <h3>源起三秦大地</h3>
                    <p>秦腔起源于<strong class="highlight">周秦时期的礼乐文化</strong>，其音乐基因可追溯至《诗经》中的"秦风"。秦汉时期，关中地区的民间歌舞、角抵戏为秦腔的雏形奠定了基础。唐代长安作为国际大都会，各种艺术形式交融碰撞，秦腔的声腔体系逐渐成形。</p>
                    <p>至明清时期，秦腔已发展为成熟的戏曲剧种，并随着商路传播至全国各地，对<strong class="highlight">京剧、豫剧、晋剧等数十个剧种</strong>产生了深远影响，故有"梆子戏鼻祖"之美誉。</p>
                </div>
            </div>
            <div class="content-block" style="margin-top:24px;">
                <h3>📅 秦腔发展大事记</h3>
                <div class="timeline">
                    <div class="timeline-item">
                        <span class="timeline-year">周秦时期（约公元前11世纪）</span>
                        <p>关中民间歌舞与祭祀仪式中的音乐元素，成为秦腔音乐的原始基因。"秦风"诗篇记录了当时的民间歌唱传统。</p>
                    </div>
                    <div class="timeline-item">
                        <span class="timeline-year">汉唐时期（公元前206年—公元907年）</span>
                        <p>汉代角抵戏、唐代参军戏与歌舞戏繁荣，长安作为文化中心，各种表演艺术为秦腔的形成提供了丰富养分。</p>
                    </div>
                    <div class="timeline-item">
                        <span class="timeline-year">宋元时期（960年—1368年）</span>
                        <p>杂剧兴盛，秦腔的板腔体音乐结构初步确立，梆子腔开始形成独特的艺术风格。</p>
                    </div>
                    <div class="timeline-item">
                        <span class="timeline-year">明清时期（1368年—1911年）</span>
                        <p>秦腔进入全盛期，涌现大量经典剧目，传播至全国。乾隆年间秦腔艺人进京演出，轰动一时。</p>
                    </div>
                    <div class="timeline-item">
                        <span class="timeline-year">2006年</span>
                        <p>秦腔被列入<strong class="highlight">第一批国家级非物质文化遗产名录</strong>，得到国家层面的保护与重视。</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- ==================== 第3页：艺术特色 ==================== -->
        <section class="page" id="page-art" data-page="art">
            <div class="page-header">
                <span class="page-icon">🎭</span>
                <h2>艺术特色</h2>
                <p class="page-subtitle">高昂激越·大气磅礴</p>
                <div class="divider-line"></div>
            </div>
            <div class="three-col">
                <div class="info-card">
                    <span class="card-emoji">🎵</span>
                    <h4>声腔体系</h4>
                    <p>以梆子腔为主，分欢音与苦音两大系统。欢音明快高昂，苦音深沉悲壮，形成强烈的艺术感染力。</p>
                </div>
                <div class="info-card">
                    <span class="card-emoji">🥁</span>
                    <h4>伴奏乐器</h4>
                    <p>以板胡为主奏乐器，配以二胡、笛子、唢呐等。打击乐中使用梆子与暴鼓，节奏鲜明有力。</p>
                </div>
                <div class="info-card">
                    <span class="card-emoji">🗣️</span>
                    <h4>演唱风格</h4>
                    <p>讲究"吼"的艺术，真声与假声结合，高亢处如裂帛穿云，低回处似幽谷鸣泉，极具震撼力。</p>
                </div>
                <div class="info-card">
                    <span class="card-emoji">💃</span>
                    <h4>表演程式</h4>
                    <p>唱念做打并重，身段刚劲有力。生旦净丑各行当均有严格的表演规范，讲究精气神的高度统一。</p>
                </div>
                <div class="info-card">
                    <span class="card-emoji">📝</span>
                    <h4>语言特色</h4>
                    <p>使用关中方言演唱，保留了大量的古汉语词汇与发音，被称为古代汉语的"活化石"。</p>
                </div>
                <div class="info-card">
                    <span class="card-emoji">🎪</span>
                    <h4>舞台美学</h4>
                    <p>虚实结合的写意风格，一桌二椅即可营造万千场景。演员的表演是舞台的核心灵魂。</p>
                </div>
            </div>
            <div class="quote-block" style="margin-top:28px;">
                秦腔之美，在于其毫不掩饰的生命力。它不似江南丝竹那般婉约，却有着黄土高原般的厚重与辽阔，每一声吼唱都是对生命最直接的礼赞。
            </div>
        </section>

        <!-- ==================== 第4页：经典剧目 ==================== -->
        <section class="page" id="page-repertoire" data-page="repertoire">
            <div class="page-header">
                <span class="page-icon">🎬</span>
                <h2>经典剧目</h2>
                <p class="page-subtitle">传世名篇·千古流芳</p>
                <div class="divider-line"></div>
            </div>
            <div class="two-col">
                <div class="content-block">
                    <h3>🎭 《三滴血》</h3>
                    <p>秦腔经典名剧，由<strong class="highlight">范紫东</strong>创作于1918年。讲述了一桩因滴血认亲而引发的曲折公案，情节跌宕起伏，深刻讽刺了教条主义的荒谬。该剧被誉为"秦腔的莎士比亚戏剧"，文学价值极高。</p>
                    <span class="tag">公案戏</span><span class="tag">讽刺喜剧</span><span class="tag">范紫东代表作</span>
                </div>
                <div class="image-placeholder" aria-label="三滴血剧照占位">🩸</div>

                <div class="image-placeholder" aria-label="铡美案剧照占位">⚖️</div>
                <div class="content-block">
                    <h3>⚖️ 《铡美案》</h3>
                    <p>秦腔包公戏的代表作，讲述包拯不畏权贵、秉公执法，铡杀忘恩负义的驸马陈世美的故事。<strong class="highlight">"黑头"包公</strong>的形象深入人心，其唱腔雄浑有力，充分展现了秦腔慷慨激昂的艺术魅力。</p>
                    <span class="tag">包公戏</span><span class="tag">黑头唱功</span><span class="tag">惩恶扬善</span>
                </div>

                <div class="content-block">
                    <h3>🏯 《火焰驹》</h3>
                    <p>秦腔传统名剧，讲述宋时忠良之后的故事。该剧以<strong class="highlight">"义马"火焰驹</strong>为线索，贯穿全剧，情节感人至深。剧中武打场面精彩，唱腔设计精妙，是秦腔舞台上常演不衰的经典。</p>
                    <span class="tag">忠义传奇</span><span class="tag">武打精彩</span>
                </div>
                <div class="image-placeholder" aria-label="火焰驹剧照占位">🐎</div>
            </div>
            <div class="content-block" style="text-align:center;">
                <p style="font-size:1.05rem;">秦腔现存传统剧目超过<strong class="highlight">3000部</strong>，题材涵盖历史演义、民间故事、神话传说等，是中国戏曲文学的宝库。</p>
            </div>
        </section>

        <!-- ==================== 第5页：名家风采 ==================== -->
        <section class="page" id="page-masters" data-page="masters">
            <div class="page-header">
                <span class="page-icon">🌟</span>
                <h2>名家风采</h2>
                <p class="page-subtitle">一代宗师·薪火相传</p>
                <div class="divider-line"></div>
            </div>
            <div class="four-col">
                <div class="info-card">
                    <div class="image-placeholder small portrait" aria-label="魏长生像占位">👤</div>
                    <h4>魏长生</h4>
                    <p style="font-size:0.8rem;">清代乾隆年间秦腔名家，以旦角表演闻名，曾进京演出轰动京城，对京剧旦行艺术影响深远。</p>
                </div>
                <div class="info-card">
                    <div class="image-placeholder small portrait" aria-label="刘毓中像占位">👤</div>
                    <h4>刘毓中</h4>
                    <p style="font-size:0.8rem;">20世纪秦腔须生泰斗，嗓音洪亮醇厚，表演深沉大气，被誉为"秦腔须生第一人"。</p>
                </div>
                <div class="info-card">
                    <div class="image-placeholder small portrait" aria-label="苏育民像占位">👤</div>
                    <h4>苏育民</h4>
                    <p style="font-size:0.8rem;">秦腔小生表演艺术家，文武兼备，唱做俱佳，其表演风格潇洒俊逸，自成一家。</p>
                </div>
                <div class="info-card">
                    <div class="image-placeholder small portrait" aria-label="李瑞芳像占位">👤</div>
                    <h4>李瑞芳</h4>
                    <p style="font-size:0.8rem;">当代秦腔旦角名家，嗓音清脆婉转，表演细腻传神，为秦腔艺术的传承做出重要贡献。</p>
                </div>
            </div>
            <div class="quote-block" style="margin-top:24px;">
                舞台方丈地，一转万重山。秦腔艺术家们用一生坚守着这门古老的艺术，他们是华夏文化真正的守护者。
            </div>
        </section>

        <!-- ==================== 第6页：脸谱服饰 ==================== -->
        <section class="page" id="page-visual" data-page="visual">
            <div class="page-header">
                <span class="page-icon">🎨</span>
                <h2>脸谱服饰</h2>
                <p class="page-subtitle">色彩斑斓的视觉艺术</p>
                <div class="divider-line"></div>
            </div>
            <div class="two-col">
                <div class="content-block">
                    <h3>🎨 秦腔脸谱艺术</h3>
                    <p>秦腔脸谱是中国戏曲脸谱的重要流派，以<strong class="highlight">色彩浓烈、线条粗犷</strong>著称。红色代表忠勇（如关羽），黑色代表刚正（如包拯），白色代表奸诈，金色代表神怪。每一张脸谱都是一幅精美的艺术品。</p>
                    <p>脸谱的绘制遵循严格的程式规范，一笔一划皆有寓意，被誉为<strong class="highlight">"无声的语言，有形的性格"</strong>。</p>
                </div>
                <div class="image-placeholder" aria-label="秦腔脸谱展示占位" style="display:flex;gap:10px;flex-wrap:wrap;justify-content:center;align-items:center;padding:15px;">
                    <span style="font-size:3rem;">🔴</span><span style="font-size:3rem;">⚫</span><span style="font-size:3rem;">⚪</span><span style="font-size:3rem;">🟡</span>
                    <span style="font-size:2.5rem;">🟢</span><span style="font-size:2.5rem;">🟣</span>
                </div>
            </div>
            <div class="two-col" style="margin-top:20px;">
                <div class="image-placeholder portrait" aria-label="秦腔戏服占位" style="font-size:4rem;">👘</div>
                <div class="content-block">
                    <h3>👘 戏服与盔头</h3>
                    <p>秦腔戏服以<strong class="highlight">明代服饰为基础</strong>，融合了汉唐以来的传统元素。蟒袍、靠甲、褶子、官衣等各类服饰工艺精湛，刺绣华美。盔头（头饰）更是精雕细琢，珠翠满目，每一件都是手工艺的杰作。</p>
                    <p>戏服的色彩与纹样严格对应角色的身份地位，形成了独特的<strong class="highlight">视觉符号系统</strong>，使观众一眼便能辨识人物的性格与命运。</p>
                </div>
            </div>
        </section>

        <!-- ==================== 第7页：传承发展 ==================== -->
        <section class="page" id="page-future" data-page="future">
            <div class="page-header">
                <span class="page-icon">🔥</span>
                <h2>传承与发展</h2>
                <p class="page-subtitle">古今交融·守正创新</p>
                <div class="divider-line"></div>
            </div>
            <div class="content-block">
                <h3>🌱 当代传承现状</h3>
                <p>目前，秦腔面临着观众老龄化、传承人才短缺等挑战。但令人欣慰的是，越来越多的<strong class="highlight">年轻人</strong>开始关注并学习秦腔。陕西省戏曲研究院等机构积极开展"秦腔进校园"活动，培养新一代观众与传承人。</p>
                <p>数字化技术也为秦腔的保护与传播提供了新途径——经典剧目的高清录制、线上教学平台的搭建，让这门古老艺术得以<strong class="highlight">跨越时空限制</strong>，触达更广泛的受众。</p>
            </div>
            <div class="two-col" style="margin-top:20px;">
                <div class="content-block">
                    <h3>💡 创新探索</h3>
                    <p>新时代的秦腔艺术家们在坚守传统精髓的同时，大胆进行创新尝试：新编历史剧融入现代舞台技术，实景演出结合文旅项目，跨界合作吸引年轻观众……秦腔正以<strong class="highlight">更加开放的姿态</strong>拥抱未来。</p>
                    <span class="tag">新编剧目</span><span class="tag">文旅融合</span><span class="tag">数字传播</span><span class="tag">国际交流</span>
                </div>
                <div class="content-block">
                    <h3>🌍 走向世界</h3>
                    <p>秦腔作为中国文化的代表之一，多次走出国门，在世界各地的舞台上亮相。从巴黎到纽约，从东京到悉尼，秦腔以其独特的艺术魅力征服了海外观众，成为<strong class="highlight">讲好中国故事</strong>的重要载体。</p>
                </div>
            </div>
            <div class="quote-block" style="text-align:center;">
                传承不是守旧，创新不是忘本。<br>让秦腔这棵千年古树，在新时代的土壤中绽放出更加绚烂的花朵。
            </div>
        </section>

        <!-- 页脚 -->
        <footer class="site-footer">
            <p>🎭 秦腔 — 国家级非物质文化遗产 | 大秦之音 · 华夏正声 🎭</p>
            <p style="margin-top:4px;opacity:0.6;">弘扬中华优秀传统文化 · 让世界听见秦腔</p>
        </footer>
    </div>

    <!-- 返回顶部按钮 -->
    <button class="back-to-top" id="backToTop" title="返回顶部" aria-label="返回顶部">⬆</button>

    <script>
        (function() {
            // ============ 元素引用 ============
            const navItems = document.querySelectorAll('.nav-item');
            const pages = document.querySelectorAll('.page');
            const mainNav = document.getElementById('mainNav');
            const backToTopBtn = document.getElementById('backToTop');
            const pageContainer = document.getElementById('pageContainer');
            const navToggleBtn = document.getElementById('navToggleBtn');
            const homeCards = document.querySelectorAll('.home-card[data-nav]');

            // ============ 页面切换函数 ============
            function switchPage(pageName) {
                // 更新导航激活状态
                navItems.forEach(item => {
                    const isActive = item.getAttribute('data-page') === pageName;
                    item.classList.toggle('active', isActive);
                    if (isActive) {
                        item.setAttribute('aria-current', 'page');
                    } else {
                        item.removeAttribute('aria-current');
                    }
                });

                // 切换页面
                pages.forEach(page => {
                    const isTarget = page.getAttribute('data-page') === pageName;
                    if (isTarget) {
                        page.classList.add('active');
                        // 重新触发动画
                        page.style.animation = 'none';
                        page.offsetHeight; // 触发回流
                        page.style.animation = 'pageFadeIn 0.55s cubic-bezier(0.4, 0, 0.2, 1) forwards';
                    } else {
                        page.classList.remove('active');
                    }
                });

                // 滚动到页面顶部
                window.scrollTo({ top: 0, behavior: 'smooth' });

                // 在移动端关闭导航（如果展开的话）
                if (window.innerWidth <= 900 && navToggleBtn.classList.contains('open')) {
                    toggleMobileNav(false);
                }

                // 更新URL hash
                if (history.pushState) {
                    const newHash = pageName === 'home' ? '' : '#' + pageName;
                    const currentHash = window.location.hash.replace('#', '');
                    if (currentHash !== pageName && !(pageName === 'home' && currentHash === '')) {
                        history.pushState({ page: pageName }, '', newHash || window.location.pathname);
                    }
                }
            }

            // ============ 导航点击事件 ============
            navItems.forEach(item => {
                item.addEventListener('click', function() {
                    const pageName = this.getAttribute('data-page');
                    if (pageName) {
                        switchPage(pageName);
                    }
                });
            });

            // ============ 首页卡片点击跳转 ============
            homeCards.forEach(card => {
                card.addEventListener('click', function() {
                    const pageName = this.getAttribute('data-nav');
                    if (pageName) {
                        switchPage(pageName);
                    }
                });
                // 键盘可访问性
                card.setAttribute('tabindex', '0');
                card.setAttribute('role', 'button');
                card.addEventListener('keydown', function(e) {
                    if (e.key === 'Enter' || e.key === ' ') {
                        e.preventDefault();
                        const pageName = this.getAttribute('data-nav');
                        if (pageName) switchPage(pageName);
                    }
                });
            });

            // ============ 移动端导航切换 ============
            function toggleMobileNav(forceState) {
                const isOpen = forceState !== undefined ? forceState : !navToggleBtn.classList.contains(
                    'open');
                if (isOpen) {
                    navToggleBtn.classList.add('open');
                    mainNav.classList.add('mobile-expanded');
                    navToggleBtn.setAttribute('aria-label', '关闭菜单');
                } else {
                    navToggleBtn.classList.remove('open');
                    mainNav.classList.remove('mobile-expanded');
                    navToggleBtn.setAttribute('aria-label', '展开导航菜单');
                }
            }

            navToggleBtn.addEventListener('click', function() {
                toggleMobileNav();
            });

            // 点击页面区域关闭移动端导航
            pageContainer.addEventListener('click', function(e) {
                if (navToggleBtn.classList.contains('open') &&
                    !e.target.closest('.main-nav') &&
                    !e.target.closest('.nav-toggle-btn')) {
                    toggleMobileNav(false);
                }
            });

            // ============ 键盘导航 ============
            document.addEventListener('keydown', function(e) {
                // 数字键1-7快速切换页面
                const keyMap = {
                    '1': 'home',
                    '2': 'history',
                    '3': 'art',
                    '4': 'repertoire',
                    '5': 'masters',
                    '6': 'visual',
                    '7': 'future'
                };
                if (e.key >= '1' && e.key <= '7' && !e.target.closest('input, textarea, [contenteditable]')) {
                    e.preventDefault();
                    switchPage(keyMap[e.key]);
                }
                // Escape关闭移动端导航
                if (e.key === 'Escape' && navToggleBtn.classList.contains('open')) {
                    toggleMobileNav(false);
                }
            });

            // ============ 滚动监听 ============
            let scrollTimeout;
            window.addEventListener('scroll', function() {
                // 导航栏样式
                if (window.scrollY > 30) {
                    mainNav.classList.add('scrolled');
                } else {
                    mainNav.classList.remove('scrolled');
                }

                // 返回顶部按钮
                if (window.scrollY > 400) {
                    backToTopBtn.classList.add('visible');
                } else {
                    backToTopBtn.classList.remove('visible');
                }

                // 防抖处理
                clearTimeout(scrollTimeout);
                scrollTimeout = setTimeout(() => {
                    // 可以在这里添加滚动相关的逻辑
                }, 100);
            }, { passive: true });

            // ============ 返回顶部 ============
            backToTopBtn.addEventListener('click', function() {
                window.scrollTo({ top: 0, behavior: 'smooth' });
            });

            // ============ URL Hash 处理 ============
            function handleHashChange() {
                const hash = window.location.hash.replace('#', '');
                if (hash && document.getElementById('page-' + hash)) {
                    switchPage(hash);
                } else if (!hash) {
                    switchPage('home');
                }
            }

            window.addEventListener('hashchange', handleHashChange);
            window.addEventListener('popstate', function(e) {
                if (e.state && e.state.page) {
                    switchPage(e.state.page);
                } else {
                    handleHashChange();
                }
            });

            // 初始加载时检查hash
            const initialHash = window.location.hash.replace('#', '');
            if (initialHash && document.getElementById('page-' + initialHash)) {
                switchPage(initialHash);
            }

            // ============ 响应式调整 ============
            function handleResize() {
                if (window.innerWidth > 900 && navToggleBtn.classList.contains('open')) {
                    toggleMobileNav(false);
                }
            }
            window.addEventListener('resize', handleResize);

            // ============ 初始化 ============
            // 触发一次滚动检测
            window.dispatchEvent(new Event('scroll'));

            console.log('🎭 秦腔主题页面已就绪');
            console.log('  💡 提示：可使用键盘数字键 1-7 快速切换页面');
            console.log('  📱 移动端请使用右上角按钮展开导航菜单');
            console.log('  🏠 共7个页面：首页 + 6个详情页');
        })();
    </script>
</body>
</html>
