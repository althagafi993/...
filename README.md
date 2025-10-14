<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>السجل المهاري التطوعي</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap');
        
        body {
            box-sizing: border-box;
            font-family: 'Cairo', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            position: relative;
            overflow: hidden;
        }
        
        .gradient-bg::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="25" cy="25" r="1" fill="white" opacity="0.1"/><circle cx="75" cy="75" r="1" fill="white" opacity="0.1"/><circle cx="50" cy="10" r="0.5" fill="white" opacity="0.1"/><circle cx="10" cy="60" r="0.5" fill="white" opacity="0.1"/><circle cx="90" cy="40" r="0.5" fill="white" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
            animation: float 20s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-10px) rotate(1deg); }
        }
        
        .card-shadow {
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.2);
        }
        
        .glass-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        .modern-input {
            background: rgba(255, 255, 255, 0.9);
            border: 2px solid transparent;
            border-radius: 12px;
            padding: 12px 16px;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }
        
        .modern-input:focus {
            outline: none;
            border-color: #667eea;
            background: rgba(255, 255, 255, 1);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.15);
        }
        
        .modern-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border: none;
            border-radius: 12px;
            padding: 12px 24px;
            color: white;
            font-weight: 600;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .modern-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        
        .modern-btn:hover::before {
            left: 100%;
        }
        
        .modern-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
        }
        
        .modern-btn:active {
            transform: translateY(-1px);
        }
        
        .nav-btn {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 12px;
            padding: 12px 24px;
            color: white;
            font-weight: 600;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .nav-btn.active {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
        }
        
        .nav-btn:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: translateY(-2px);
        }
        
        .opportunity-card {
            background: linear-gradient(135deg, rgba(255,255,255,0.9) 0%, rgba(255,255,255,0.7) 100%);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 20px;
            padding: 24px;
            margin-bottom: 24px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .opportunity-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 4px;
            height: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 0 4px 4px 0;
        }
        
        .opportunity-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
        }
        
        .skill-input {
            background: rgba(255, 255, 255, 0.8);
            border: 1px solid rgba(102, 126, 234, 0.2);
            border-radius: 8px;
            padding: 8px 12px;
            margin: 4px 0;
            transition: all 0.3s ease;
        }
        
        .skill-input:focus {
            outline: none;
            border-color: #667eea;
            background: rgba(255, 255, 255, 1);
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.1);
        }
        
        .floating-label {
            position: relative;
            margin-bottom: 20px;
        }
        
        .floating-label input,
        .floating-label select,
        .floating-label textarea {
            width: 100%;
            padding: 16px 12px 8px 12px;
            border: 2px solid rgba(102, 126, 234, 0.2);
            border-radius: 12px;
            background: rgba(255, 255, 255, 0.9);
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .floating-label label {
            position: absolute;
            top: 16px;
            right: 12px;
            font-size: 16px;
            color: #666;
            transition: all 0.3s ease;
            pointer-events: none;
            background: transparent;
            padding: 0 4px;
        }
        
        .floating-label input:focus + label,
        .floating-label input:not(:placeholder-shown) + label,
        .floating-label select:focus + label,
        .floating-label select:not([value=""]) + label,
        .floating-label textarea:focus + label,
        .floating-label textarea:not(:placeholder-shown) + label {
            top: -8px;
            font-size: 12px;
            color: #667eea;
            background: rgba(255, 255, 255, 0.9);
            font-weight: 600;
        }
        
        .floating-label input:focus,
        .floating-label select:focus,
        .floating-label textarea:focus {
            outline: none;
            border-color: #667eea;
            background: rgba(255, 255, 255, 1);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.15);
        }
        
        .section-header {
            background: linear-gradient(135deg, rgba(255,255,255,0.9) 0%, rgba(255,255,255,0.7) 100%);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 24px;
            position: relative;
            overflow: hidden;
        }
        
        .section-header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
        }
        
        .stats-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border-radius: 16px;
            padding: 20px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .stats-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            animation: pulse 4s ease-in-out infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1) rotate(0deg); opacity: 0.5; }
            50% { transform: scale(1.1) rotate(180deg); opacity: 0.8; }
        }
        
        .print-section {
            display: none;
        }
        
        @media print {
            .no-print { display: none !important; }
            .print-section { display: block !important; }
            body { background: white !important; }
        }
        
        .animate-fade-in {
            animation: fadeIn 0.6s ease-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .animate-slide-in {
            animation: slideIn 0.8s ease-out;
        }
        
        @keyframes slideIn {
            from { opacity: 0; transform: translateX(-30px); }
            to { opacity: 1; transform: translateX(0); }
        }
        
        /* Hero Section Styles */
        .floating-shapes {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
        }
        
        .shape {
            position: absolute;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: floatShapes 20s infinite linear;
        }
        
        .shape-1 {
            width: 80px;
            height: 80px;
            top: 20%;
            left: 10%;
            animation-delay: 0s;
        }
        
        .shape-2 {
            width: 120px;
            height: 120px;
            top: 60%;
            right: 15%;
            animation-delay: -5s;
        }
        
        .shape-3 {
            width: 60px;
            height: 60px;
            top: 80%;
            left: 20%;
            animation-delay: -10s;
        }
        
        .shape-4 {
            width: 100px;
            height: 100px;
            top: 30%;
            right: 30%;
            animation-delay: -15s;
        }
        
        .shape-5 {
            width: 40px;
            height: 40px;
            top: 10%;
            right: 10%;
            animation-delay: -7s;
        }
        
        @keyframes floatShapes {
            0% { transform: translateY(0px) rotate(0deg); opacity: 0.3; }
            50% { transform: translateY(-20px) rotate(180deg); opacity: 0.8; }
            100% { transform: translateY(0px) rotate(360deg); opacity: 0.3; }
        }
        
        .school-logo {
            width: 120px;
            height: 120px;
        }
        
        .logo-circle {
            width: 120px;
            height: 120px;
            background: linear-gradient(135deg, rgba(255,255,255,0.2) 0%, rgba(255,255,255,0.1) 100%);
            border: 3px solid rgba(255,255,255,0.3);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(10px);
            animation: logoGlow 3s ease-in-out infinite;
        }
        
        @keyframes logoGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(255,255,255,0.3); }
            50% { box-shadow: 0 0 40px rgba(255,255,255,0.6); }
        }
        
        .text-shadow-lg {
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }
        
        .divider {
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, transparent, #fbbf24, transparent);
            border-radius: 2px;
        }
        
        /* Feature Cards */
        .feature-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 16px;
            padding: 24px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            transition: left 0.5s;
        }
        
        .feature-card:hover::before {
            left: 100%;
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
        }
        
        .feature-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #fbbf24 0%, #f59e0b 100%);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 16px;
            color: white;
        }
        
        /* Main Navigation Buttons */
        .main-nav-btn {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 24px;
            padding: 32px;
            width: 100%;
            max-width: 500px;
            display: flex;
            align-items: center;
            gap: 24px;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            color: #1f2937;
            text-align: right;
        }
        
        .main-nav-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(102, 126, 234, 0.1), transparent);
            transition: left 0.6s;
        }
        
        .main-nav-btn:hover::before {
            left: 100%;
        }
        
        .main-nav-btn:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
            border-color: #667eea;
        }
        
        .main-nav-btn.active {
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
            border-color: #667eea;
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(102, 126, 234, 0.2);
        }
        
        .btn-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            flex-shrink: 0;
        }
        
        .supervisor-btn .btn-icon {
            background: linear-gradient(135deg, #a855f7 0%, #ec4899 100%);
        }
        
        .btn-content {
            flex: 1;
        }
        
        .btn-features {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 12px;
        }
        
        .feature-tag {
            background: rgba(102, 126, 234, 0.1);
            color: #667eea;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            border: 1px solid rgba(102, 126, 234, 0.2);
        }
        
        .supervisor-btn .feature-tag {
            background: rgba(168, 85, 247, 0.1);
            color: #a855f7;
            border-color: rgba(168, 85, 247, 0.2);
        }
        
        .btn-arrow {
            color: #667eea;
            opacity: 0.7;
            transition: all 0.3s ease;
        }
        
        .main-nav-btn:hover .btn-arrow {
            opacity: 1;
            transform: translateX(-5px);
        }
        
        /* Statistics Cards */
        .stat-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 16px;
            padding: 24px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 16px;
            color: white;
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: 900;
            color: #1f2937;
            margin-bottom: 8px;
        }
        
        .stat-label {
            font-size: 0.875rem;
            color: #6b7280;
            font-weight: 600;
        }
        
        /* Quick Action Buttons */
        .quick-action-btn {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 12px;
            padding: 12px 24px;
            color: white;
            font-weight: 600;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
        }
        
        .quick-action-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
        }
        
        /* Scroll Indicator */
        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            color: rgba(255, 255, 255, 0.7);
        }
        
        .scroll-arrow {
            animation: bounce 2s infinite;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .main-nav-btn {
                flex-direction: column;
                text-align: center;
                gap: 16px;
            }
            
            .btn-content {
                text-align: center;
            }
            
            .btn-arrow {
                transform: rotate(90deg);
            }
            
            .main-nav-btn:hover .btn-arrow {
                transform: rotate(90deg) translateY(-5px);
            }
        }
        
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: linear-gradient(135deg, #5a6fd8 0%, #6a4190 100%);
        }
    </style>
</head>
<body class="min-h-full bg-gray-50">
    <section class="gradient-bg text-white relative overflow-hidden min-h-screen flex items-center">
        <div class="absolute inset-0">
            <div class="floating-shapes">
                <div class="shape shape-1"></div>
                <div class="shape shape-2"></div>
                <div class="shape shape-3"></div>
                <div class="shape shape-4"></div>
                <div class="shape shape-5"></div>
            </div>
        </div>
        
        <div class="container mx-auto px-4 relative z-10">
            <div class="text-center mb-12 animate-fade-in">
                <div class="school-logo mx-auto mb-8">
                    <div class="logo-circle">
                        <i class="fas fa-graduation-cap text-6xl text-white"></i>
                    </div>
                </div>
                <h1 class="text-5xl md:text-7xl font-black mb-4 text-shadow-lg">
                    <span class="block">متوسطة وثانوية</span>
                    <span class="block text-yellow-300">ترعة ثقيف</span>
                </h1>
                <div class="divider mx-auto mb-6"></div>
                <h2 class="text-3xl md:text-4xl font-bold mb-4 text-blue-100">السجل المهاري التطوعي</h2>
                <p class="text-xl md:text-2xl opacity-90 max-w-3xl mx-auto leading-relaxed">
                    منصة متطورة لتسجيل وإدارة الأعمال التطوعية والمهارات المكتسبة للطلاب
                </p>
            </div>
            
            <div class="flex flex-col md:flex-row justify-center items-center gap-8 mb-12">
                <button onclick="showSection('student')" id="studentBtn" class="main-nav-btn student-btn active group">
                    <div class="btn-icon">
                        <i class="fas fa-user-graduate text-4xl group-hover:scale-110 transition-transform duration-300"></i>
                    </div>
                    <div class="btn-content">
                        <h3 class="text-2xl font-bold mb-2">قسم الطالب</h3>
                        <p class="text-sm opacity-90">سجل أعمالك التطوعية ومهاراتك</p>
                        <div class="btn-features">
                            <span class="feature-tag">
                                <i class="fas fa-plus-circle ml-1"></i>إضافة فرص
                            </span>
                            <span class="feature-tag">
                                <i class="fas fa-brain ml-1"></i>تسجيل مهارات
                            </span>
                            <span class="feature-tag">
                                <i class="fas fa-print ml-1"></i>طباعة السجل
                            </span>
                        </div>
                    </div>
                    <div class="btn-arrow">
                        <i class="fas fa-arrow-left text-2xl"></i>
                    </div>
                </button>

                <button onclick="showSection('supervisor')" id="supervisorBtn" class="main-nav-btn supervisor-btn group">
                    <div class="btn-icon">
                        <i class="fas fa-user-tie text-4xl group-hover:scale-110 transition-transform duration-300"></i>
                    </div>
                    <div class="btn-content">
                        <h3 class="text-2xl font-bold mb-2">قسم المشرف</h3>
                        <p class="text-sm opacity-90">إدارة ومراجعة سجلات الطلاب</p>
                        <div class="btn-features">
                            <span class="feature-tag">
                                <i class="fas fa-eye ml-1"></i>مراجعة السجلات
                            </span>
                            <span class="feature-tag">
                                <i class="fas fa-stamp ml-1"></i>اعتماد الأعمال
                            </span>
                            <span class="feature-tag">
                                <i class="fas fa-cloud ml-1"></i>إدارة البيانات
                            </span>
                        </div>
                    </div>
                    <div class="btn-arrow">
                        <i class="fas fa-arrow-left text-2xl"></i>
                    </div>
                </button>
            </div>

            <div class="grid grid-cols-2 md:grid-cols-4 gap-6 mb-12">
                <div class="stat-card animate-fade-in" style="animation-delay: 0.8s">
                    <div class="stat-icon">
                        <i class="fas fa-users text-2xl"></i>
                    </div>
                    <div class="stat-number" id="studentsCount">0</div>
                    <div class="stat-label">طالب مسجل</div>
                </div>
                <div class="stat-card animate-fade-in" style="animation-delay: 1s">
                    <div class="stat-icon">
                        <i class="fas fa-hands-helping text-2xl"></i>
                    </div>
                    <div class="stat-number" id="opportunitiesCount">0</div>
                    <div class="stat-label">فرصة تطوعية</div>
                </div>
                <div class="stat-card animate-fade-in" style="animation-delay: 1.2s">
                    <div class="stat-icon">
                        <i class="fas fa-clock text-2xl"></i>
                    </div>
                    <div class="stat-number" id="totalHours">0</div>
                    <div class="stat-label">ساعة تطوعية</div>
                </div>
                <div class="stat-card animate-fade-in" style="animation-delay: 1.4s">
                    <div class="stat-icon">
                        <i class="fas fa-brain text-2xl"></i>
                    </div>
                    <div class="stat-number" id="skillsCount">0</div>
                    <div class="stat-label">مهارة مكتسبة</div>
                </div>
            </div>

            <div class="text-center">
                <h3 class="text-2xl font-bold mb-6">إجراءات سريعة</h3>
                <div class="flex flex-wrap justify-center gap-4">
                    <button onclick="showQuickGuide()" class="quick-action-btn">
                        <i class="fas fa-question-circle text-xl ml-2"></i>
                        دليل الاستخدام
                    </button>
                    <button onclick="showAboutSchool()" class="quick-action-btn">
                        <i class="fas fa-school text-xl ml-2"></i>
                        عن المدرسة
                    </button>
                    <button onclick="showContactInfo()" class="quick-action-btn">
                        <i class="fas fa-phone text-xl ml-2"></i>
                        تواصل معنا
                    </button>
                </div>
            </div>
        </div>

        <div class="scroll-indicator">
            <div class="scroll-arrow">
                <i class="fas fa-chevron-down text-2xl animate-bounce"></i>
            </div>
        </div>
    </section>

    <div id="studentSection" class="container mx-auto px-4 py-8">
        <div id="studentLogin" class="max-w-md mx-auto glass-card rounded-2xl p-8 mb-8 animate-fade-in">
            <div class="text-center mb-8">
                <div class="w-20 h-20 mx-auto mb-4 bg-gradient-to-br from-blue-500 to-purple-600 rounded-full flex items-center justify-center">
                    <i class="fas fa-user-graduate text-white text-2xl"></i>
                </div>
                <h2 class="text-3xl font-bold text-gray-800 mb-2">مرحباً بك</h2>
                <p class="text-gray-600">سجل دخولك للوصول إلى سجلك المهاري</p>
            </div>
            <form onsubmit="studentLoginSubmit(event)" class="space-y-6">
                <div class="floating-label">
                    <input type="tel" id="studentPhone" placeholder=" " required>
                    <label>رقم الجوال</label>
                </div>
                <div class="floating-label">
                    <input type="text" id="studentId" placeholder=" " required>
                    <label>السجل المدني</label>
                </div>
                <button type="submit" class="w-full modern-btn py-4 text-lg font-bold">
                    <i class="fas fa-sign-in-alt ml-2"></i>
                    دخول إلى السجل المهاري
                </button>
            </form>
        </div>

        <div id="studentProfile" class="hidden">
            <div class="section-header animate-slide-in">
                <div class="flex items-center mb-6">
                    <div class="w-12 h-12 bg-gradient-to-br from-blue-500 to-purple-600 rounded-xl flex items-center justify-center ml-4">
                        <i class="fas fa-user text-white text-lg"></i>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold text-gray-800">معلومات الطالب</h2>
                        <p class="text-gray-600">أكمل بياناتك الشخصية والأكاديمية</p>
                    </div>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="floating-label">
                        <input type="text" id="fullNameTerah1" placeholder=" ">
                        <label>الاسم الكامل (T3r4h1)</label>
                    </div>
                    <div class="floating-label">
                        <input type="text" id="identificationNumber" placeholder=" ">
                        <label>الرقم التعريفي</label>
                    </div>
                    <div class="floating-label">
                        <input type="text" id="school" placeholder=" ">
                        <label>المدرسة</label>
                    </div>
                    <div class="floating-label">
                        <input type="text" id="grade" placeholder=" ">
                        <label>المرحلة الدراسية</label>
                    </div>
                    <div class="floating-label">
                        <input type="text" id="nationalId" placeholder=" ">
                        <label>رقم الهوية الوطنية</label>
                    </div>
                    <div class="floating-label">
                        <input type="tel" id="phoneNumber" placeholder=" ">
                        <label>رقم الهاتف</label>
                    </div>
                    <div class="floating-label">
                        <input type="email" id="email" placeholder=" ">
                        <label>البريد الإلكتروني</label>
                    </div>
                    <div class="floating-label">
                        <input type="text" id="currentSemester" placeholder=" ">
                        <label>الفصل الدراسي الحالي</label>
                    </div>
                    <div class="md:col-span-2 floating-label">
                        <textarea id="personalGoals" rows="3" placeholder=" "></textarea>
                        <label>الأهداف الشخصية والتعليمية والمهنية</label>
                    </div>
                    <div class="floating-label">
                        <textarea id="
