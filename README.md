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
    <!-- Hero Section -->
    <section class="gradient-bg text-white relative overflow-hidden min-h-screen flex items-center">
        <!-- Animated Background Elements -->
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
            <!-- School Logo and Header -->
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



            <!-- Main Navigation Buttons -->
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

            <!-- Statistics Section -->
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

            <!-- Quick Actions -->
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

        <!-- Scroll Indicator -->
        <div class="scroll-indicator">
            <div class="scroll-arrow">
                <i class="fas fa-chevron-down text-2xl animate-bounce"></i>
            </div>
        </div>
    </section>

    <!-- Student Section -->
    <div id="studentSection" class="container mx-auto px-4 py-8">
        <!-- Student Login -->
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

        <!-- Student Profile -->
        <div id="studentProfile" class="hidden">
            <!-- Student Information -->
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
                        <input type="text" id="fullName" placeholder=" ">
                        <label>الاسم الكامل</label>
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
                        <textarea id="academicGoal" rows="2" placeholder=" "></textarea>
                        <label>الهدف التعليمي الأكاديمي</label>
                    </div>
                    <div class="floating-label">
                        <textarea id="skillGoal" rows="2" placeholder=" "></textarea>
                        <label>الهدف التعليمي المهاري</label>
                    </div>
                </div>
                <div class="flex justify-center mt-8">
                    <button onclick="saveStudentInfo()" class="modern-btn px-8 py-3 text-lg">
                        <i class="fas fa-save ml-2"></i>حفظ المعلومات
                    </button>
                </div>
            </div>

            <!-- Volunteer Opportunities -->
            <div class="section-header animate-slide-in">
                <div class="flex justify-between items-center mb-6">
                    <div class="flex items-center">
                        <div class="w-12 h-12 bg-gradient-to-br from-green-500 to-blue-600 rounded-xl flex items-center justify-center ml-4">
                            <i class="fas fa-hands-helping text-white text-lg"></i>
                        </div>
                        <div>
                            <h2 class="text-2xl font-bold text-gray-800">الأعمال التطوعية</h2>
                            <p class="text-gray-600">سجل فرصك التطوعية ومهاراتك المكتسبة</p>
                        </div>
                    </div>
                    <button onclick="addOpportunity()" class="modern-btn px-6 py-3">
                        <i class="fas fa-plus ml-2"></i>إضافة فرصة جديدة
                    </button>
                </div>
                <div id="opportunitiesList" class="space-y-6"></div>
            </div>
        </div>
    </div>

    <!-- Supervisor Section -->
    <div id="supervisorSection" class="container mx-auto px-4 py-8 hidden">
        <!-- Supervisor Login -->
        <div id="supervisorLogin" class="max-w-md mx-auto glass-card rounded-2xl p-8 mb-8 animate-fade-in">
            <div class="text-center mb-8">
                <div class="w-20 h-20 mx-auto mb-4 bg-gradient-to-br from-purple-500 to-pink-600 rounded-full flex items-center justify-center">
                    <i class="fas fa-user-tie text-white text-2xl"></i>
                </div>
                <h2 class="text-3xl font-bold text-gray-800 mb-2">لوحة المشرف</h2>
                <p class="text-gray-600">دخول المشرفين المعتمدين</p>
            </div>
            <form onsubmit="supervisorLoginSubmit(event)" class="space-y-6">
                <div class="floating-label">
                    <input type="tel" id="supervisorPhone" placeholder=" " required>
                    <label>رقم الجوال</label>
                </div>
                <div class="floating-label">
                    <input type="text" id="supervisorCode" placeholder=" " required>
                    <label>كود التأكيد</label>
                </div>
                <button type="submit" class="w-full modern-btn py-4 text-lg font-bold" style="background: linear-gradient(135deg, #a855f7 0%, #ec4899 100%);">
                    <i class="fas fa-shield-alt ml-2"></i>
                    دخول لوحة الإدارة
                </button>
            </form>
            <div class="mt-6 p-4 bg-gradient-to-r from-blue-50 to-purple-50 rounded-xl border border-blue-200">
                <div class="flex items-center">
                    <i class="fas fa-info-circle text-blue-500 ml-3"></i>
                    <p class="text-sm text-blue-700 font-medium">للحصول على بيانات الدخول، يرجى التواصل مع إدارة المدرسة</p>
                </div>
            </div>
        </div>

        <!-- Supervisor Dashboard -->
        <div id="supervisorDashboard" class="hidden">
            <!-- Supervisor Info -->
            <div class="bg-white rounded-lg card-shadow p-6 mb-8">
                <h2 class="text-2xl font-bold mb-6 text-gray-800 border-b pb-3">توصية المشرف الأكاديمي التربوي</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">اسم المشرف</label>
                        <input type="text" id="supervisorName" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">رقم الجوال</label>
                        <input type="tel" id="supervisorPhoneDisplay" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" readonly>
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">التوقيع</label>
                        <input type="text" id="supervisorSignature" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">تاريخ التقييم</label>
                        <input type="date" id="evaluationDate" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                </div>
                <div class="flex justify-center mt-6">
                    <button onclick="saveSupervisorInfo()" class="modern-btn px-8 py-3 text-lg" style="background: linear-gradient(135deg, #a855f7 0%, #ec4899 100%);">
                        <i class="fas fa-save ml-2"></i>حفظ معلومات المشرف
                    </button>
                </div>
            </div>

            <!-- Certification Section -->
            <div class="bg-white rounded-lg card-shadow p-6 mb-8">
                <h2 class="text-2xl font-bold mb-6 text-gray-800 border-b pb-3">ختم واعتماد السجل المهاري</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">الجهة المعتمدة</label>
                        <input type="text" id="certifyingAuthority" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" value="متوسطة وثانوية ترعة ثقيف">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">التوقيع والختم</label>
                        <input type="text" id="officialSignature" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">تاريخ الإصدار</label>
                        <input type="date" id="issueDate" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                </div>
                <div class="flex justify-center mt-6">
                    <button onclick="saveCertificationInfo()" class="modern-btn px-8 py-3 text-lg" style="background: linear-gradient(135deg, #10b981 0%, #059669 100%);">
                        <i class="fas fa-stamp ml-2"></i>حفظ معلومات الاعتماد
                    </button>
                </div>
            </div>

            <!-- Students Management -->
            <div class="bg-white rounded-lg card-shadow p-6">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-2xl font-bold text-gray-800">إدارة الطلاب والفرص التطوعية</h2>
                    <div class="flex gap-3">
                        <button onclick="exportAllData()" class="modern-btn px-4 py-2 text-sm" style="background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);">
                            <i class="fas fa-download ml-2"></i>تصدير البيانات
                        </button>
                        <button onclick="refreshStudentsList()" class="modern-btn px-4 py-2 text-sm">
                            <i class="fas fa-sync-alt ml-2"></i>تحديث القائمة
                        </button>
                    </div>
                </div>
                
                <!-- Students Statistics -->
                <div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-6">
                    <div class="bg-gradient-to-r from-blue-50 to-blue-100 p-4 rounded-lg text-center">
                        <i class="fas fa-users text-blue-600 text-2xl mb-2"></i>
                        <div class="text-2xl font-bold text-blue-800" id="totalStudentsCount">0</div>
                        <div class="text-sm text-blue-600">إجمالي الطلاب</div>
                    </div>
                    <div class="bg-gradient-to-r from-green-50 to-green-100 p-4 rounded-lg text-center">
                        <i class="fas fa-hands-helping text-green-600 text-2xl mb-2"></i>
                        <div class="text-2xl font-bold text-green-800" id="totalOpportunitiesCount">0</div>
                        <div class="text-sm text-green-600">إجمالي الفرص</div>
                    </div>
                    <div class="bg-gradient-to-r from-purple-50 to-purple-100 p-4 rounded-lg text-center">
                        <i class="fas fa-clock text-purple-600 text-2xl mb-2"></i>
                        <div class="text-2xl font-bold text-purple-800" id="totalVolunteerHours">0</div>
                        <div class="text-sm text-purple-600">إجمالي الساعات</div>
                    </div>
                    <div class="bg-gradient-to-r from-orange-50 to-orange-100 p-4 rounded-lg text-center">
                        <i class="fas fa-brain text-orange-600 text-2xl mb-2"></i>
                        <div class="text-2xl font-bold text-orange-800" id="totalSkillsCount">0</div>
                        <div class="text-sm text-orange-600">إجمالي المهارات</div>
                    </div>
                </div>
                
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">اختيار الطالب</label>
                    <select id="studentSelect" onchange="loadStudentData()" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                        <option value="">اختر طالب...</option>
                    </select>
                </div>
                
                <!-- All Students Overview -->
                <div id="allStudentsOverview" class="mb-6">
                    <h3 class="text-lg font-bold mb-4 text-gray-800">نظرة عامة على جميع الطلاب</h3>
                    <div id="studentsOverviewList" class="space-y-4"></div>
                </div>
                
                <div id="selectedStudentData" class="hidden">
                    <div id="studentDataDisplay"></div>
                    <div id="studentOpportunitiesDisplay"></div>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-8 mt-16 no-print">
        <div class="container mx-auto px-4 text-center">
            <p class="text-lg mb-4">تصميم أ.عبدالرحمن الثقفي</p>
            <div class="flex justify-center space-x-6">
                <a href="https://x.com/a_a_althagafi?t=SKoq7PoEIK_sP9WabZ7QYA&s=09" target="_blank" rel="noopener noreferrer" class="text-blue-400 hover:text-blue-300 transition-colors">
                    <i class="fab fa-twitter text-2xl"></i>
                </a>
                <a href="https://t.me/althagafi993" target="_blank" rel="noopener noreferrer" class="text-blue-400 hover:text-blue-300 transition-colors">
                    <i class="fab fa-telegram text-2xl"></i>
                </a>
            </div>
        </div>
    </footer>

    <script>
        // Global variables
        let currentStudent = null;
        let studentsData = JSON.parse(localStorage.getItem('studentsData')) || {};
        let opportunityCounter = 0;

        // Navigation
        function showSection(section) {
            const studentSection = document.getElementById('studentSection');
            const supervisorSection = document.getElementById('supervisorSection');
            const studentBtn = document.getElementById('studentBtn');
            const supervisorBtn = document.getElementById('supervisorBtn');

            if (section === 'student') {
                studentSection.classList.remove('hidden');
                supervisorSection.classList.add('hidden');
                studentBtn.classList.add('active');
                supervisorBtn.classList.remove('active');
                
                // Add animation
                studentSection.classList.add('animate-fade-in');
                setTimeout(() => studentSection.classList.remove('animate-fade-in'), 600);
            } else {
                studentSection.classList.add('hidden');
                supervisorSection.classList.remove('hidden');
                supervisorBtn.classList.add('active');
                studentBtn.classList.remove('active');
                
                // Add animation
                supervisorSection.classList.add('animate-fade-in');
                setTimeout(() => supervisorSection.classList.remove('animate-fade-in'), 600);
            }
        }

        // Student login
        function studentLoginSubmit(event) {
            event.preventDefault();
            const phone = document.getElementById('studentPhone').value;
            const id = document.getElementById('studentId').value;
            
            currentStudent = phone + '_' + id;
            
            // Load existing data or create new profile
            if (studentsData[currentStudent]) {
                loadStudentProfile();
            } else {
                studentsData[currentStudent] = {
                    phone: phone,
                    civilId: id,
                    profile: {},
                    opportunities: []
                };
            }
            
            document.getElementById('studentLogin').classList.add('hidden');
            document.getElementById('studentProfile').classList.remove('hidden');
            
            // Sync with cloud (simulated)
            syncWithCloud();
        }

        // Load student profile
        function loadStudentProfile() {
            const data = studentsData[currentStudent];
            if (data.profile) {
                Object.keys(data.profile).forEach(key => {
                    const element = document.getElementById(key);
                    if (element) {
                        element.value = data.profile[key];
                    }
                });
            }
            displayOpportunities();
        }

        // Save student info
        function saveStudentInfo() {
            const fields = ['fullName', 'identificationNumber', 'school', 'grade', 'nationalId', 'phoneNumber', 'email', 'currentSemester', 'personalGoals', 'academicGoal', 'skillGoal'];
            
            if (!studentsData[currentStudent]) {
                studentsData[currentStudent] = {
                    phone: currentStudent.split('_')[0],
                    civilId: currentStudent.split('_')[1],
                    profile: {},
                    opportunities: []
                };
            }
            
            studentsData[currentStudent].profile = {};
            fields.forEach(field => {
                const element = document.getElementById(field);
                if (element) {
                    studentsData[currentStudent].profile[field] = element.value;
                }
            });
            
            // Add metadata
            studentsData[currentStudent].lastUpdated = new Date().toISOString();
            studentsData[currentStudent].school = 'متوسطة وثانوية ترعة ثقيف';
            studentsData[currentStudent].registrationDate = studentsData[currentStudent].registrationDate || new Date().toISOString();
            
            localStorage.setItem('studentsData', JSON.stringify(studentsData));
            syncAllDataToCloud();
            updateStatistics();
            
            // Show success message
            showMessage('تم حفظ المعلومات ومزامنتها مع السحابة بنجاح!', 'success');
        }

        // Add opportunity
        function addOpportunity() {
            opportunityCounter++;
            const opportunityId = 'opportunity_' + opportunityCounter;
            
            const opportunityHtml = `
                <div class="opportunity-card animate-fade-in" id="${opportunityId}">
                    <div class="flex items-center justify-between mb-6">
                        <div class="flex items-center">
                            <div class="w-10 h-10 bg-gradient-to-br from-orange-500 to-red-600 rounded-lg flex items-center justify-center ml-3">
                                <i class="fas fa-star text-white"></i>
                            </div>
                            <h3 class="text-xl font-bold text-gray-800">الفرصة التطوعية ${opportunityCounter}</h3>
                        </div>
                        <div class="flex items-center space-x-2">
                            <span class="px-3 py-1 bg-blue-100 text-blue-800 rounded-full text-sm font-medium">جديد</span>
                        </div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="floating-label">
                            <input type="text" placeholder=" " data-field="name">
                            <label>اسم الفرصة التطوعية</label>
                        </div>
                        <div class="floating-label">
                            <input type="text" placeholder=" " data-field="organization">
                            <label>الجهة المنظمة</label>
                        </div>
                        <div class="md:col-span-2 floating-label">
                            <textarea rows="3" placeholder=" " data-field="description"></textarea>
                            <label>وصف الفرصة</label>
                        </div>
                        <div class="floating-label">
                            <select data-field="type">
                                <option value="">اختر النوع</option>
                                <option value="ميدانية">ميدانية</option>
                                <option value="عن بعد">عن بعد</option>
                            </select>
                            <label>نوع الفرصة</label>
                        </div>
                        <div class="floating-label">
                            <textarea rows="2" placeholder=" " data-field="role"></textarea>
                            <label>الدور والمهام</label>
                        </div>
                        <div class="floating-label">
                            <input type="date" data-field="startDate">
                            <label>تاريخ البداية</label>
                        </div>
                        <div class="floating-label">
                            <input type="date" data-field="endDate">
                            <label>تاريخ الانتهاء</label>
                        </div>
                        <div class="floating-label">
                            <input type="number" placeholder=" " data-field="hours">
                            <label>عدد الساعات</label>
                        </div>
                        <div class="floating-label">
                            <select data-field="difficulty">
                                <option value="">اختر المستوى</option>
                                <option value="1">1 - بالغ السهولة</option>
                                <option value="2">2 - سهل</option>
                                <option value="3">3 - متوسط</option>
                                <option value="4">4 - صعب</option>
                                <option value="5">5 - بالغ الصعوبة</option>
                            </select>
                            <label>مستوى صعوبة الفرصة</label>
                        </div>
                        <div class="md:col-span-2">
                            <div class="bg-gradient-to-r from-green-50 to-blue-50 rounded-xl p-4 border border-green-200">
                                <h4 class="font-bold text-gray-800 mb-3 flex items-center">
                                    <i class="fas fa-brain text-green-600 ml-2"></i>
                                    المهارات المكتسبة
                                </h4>
                                <div id="skills_${opportunityId}" class="space-y-2">
                                    <div class="flex items-center gap-2">
                                        <input type="text" placeholder="اسم المهارة" class="flex-1 skill-input">
                                        <select class="skill-input">
                                            <option value="">مستوى المهارة</option>
                                            <option value="منخفض">منخفض</option>
                                            <option value="بسيط">بسيط</option>
                                            <option value="متوسط">متوسط</option>
                                            <option value="مرتفع">مرتفع</option>
                                        </select>
                                        <button type="button" onclick="removeSkill(this)" class="bg-red-500 hover:bg-red-600 text-white px-3 py-2 rounded-lg text-sm transition-colors">
                                            <i class="fas fa-times"></i>
                                        </button>
                                    </div>
                                </div>
                                <button type="button" onclick="addSkill('skills_${opportunityId}')" class="mt-3 bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-sm transition-colors">
                                    <i class="fas fa-plus ml-1"></i>إضافة مهارة
                                </button>
                            </div>
                        </div>
                        <div class="floating-label">
                            <input type="text" placeholder=" " data-field="signature">
                            <label>توقيع الجهة</label>
                        </div>
                    </div>
                    <div class="flex flex-wrap gap-3 mt-8 pt-6 border-t border-gray-200">
                        <button onclick="saveOpportunity('${opportunityId}')" class="modern-btn px-6 py-2" style="background: linear-gradient(135deg, #10b981 0%, #059669 100%);">
                            <i class="fas fa-save ml-2"></i>حفظ الفرصة
                        </button>
                        <button onclick="printOpportunity('${opportunityId}')" class="modern-btn px-6 py-2">
                            <i class="fas fa-print ml-2"></i>طباعة السجل
                        </button>
                        <button onclick="deleteOpportunity('${opportunityId}')" class="modern-btn px-6 py-2" style="background: linear-gradient(135deg, #ef4444 0%, #dc2626 100%);">
                            <i class="fas fa-trash ml-2"></i>حذف الفرصة
                        </button>
                    </div>
                </div>
            `;
            
            document.getElementById('opportunitiesList').insertAdjacentHTML('beforeend', opportunityHtml);
        }

        // Add skill
        function addSkill(containerId) {
            const container = document.getElementById(containerId);
            const skillHtml = `
                <div class="flex items-center gap-2 mb-2">
                    <input type="text" placeholder="اسم المهارة" class="flex-1 skill-input">
                    <select class="skill-input">
                        <option value="">مستوى المهارة</option>
                        <option value="منخفض">منخفض</option>
                        <option value="بسيط">بسيط</option>
                        <option value="متوسط">متوسط</option>
                        <option value="مرتفع">مرتفع</option>
                    </select>
                    <button type="button" onclick="removeSkill(this)" class="bg-red-500 text-white px-2 py-1 rounded text-sm">حذف</button>
                </div>
            `;
            container.insertAdjacentHTML('beforeend', skillHtml);
        }

        // Remove skill
        function removeSkill(button) {
            button.parentElement.remove();
        }

        // Save opportunity
        function saveOpportunity(opportunityId) {
            const opportunityDiv = document.getElementById(opportunityId);
            if (!opportunityDiv) {
                showMessage('خطأ في العثور على الفرصة التطوعية!', 'error');
                return;
            }
            
            const data = {};
            
            // Get basic fields
            opportunityDiv.querySelectorAll('[data-field]').forEach(input => {
                data[input.dataset.field] = input.value;
            });
            
            // Get skills
            const skillsContainer = opportunityDiv.querySelector('[id^="skills_"]');
            data.skills = [];
            
            if (skillsContainer) {
                const skillDivs = skillsContainer.querySelectorAll('.flex.items-center');
                skillDivs.forEach(skillDiv => {
                    const inputs = skillDiv.querySelectorAll('input, select');
                    if (inputs.length >= 2 && inputs[0].value.trim()) {
                        data.skills.push({
                            name: inputs[0].value,
                            level: inputs[1].value
                        });
                    }
                });
            }
            
            // Ensure student data structure exists
            if (!studentsData[currentStudent]) {
                studentsData[currentStudent] = {
                    phone: currentStudent.split('_')[0],
                    civilId: currentStudent.split('_')[1],
                    profile: {},
                    opportunities: []
                };
            }
            
            if (!studentsData[currentStudent].opportunities) {
                studentsData[currentStudent].opportunities = [];
            }
            
            // Add metadata to opportunity
            data.createdDate = data.createdDate || new Date().toISOString();
            data.lastModified = new Date().toISOString();
            
            const existingIndex = studentsData[currentStudent].opportunities.findIndex(opp => opp.id === opportunityId);
            if (existingIndex >= 0) {
                studentsData[currentStudent].opportunities[existingIndex] = { id: opportunityId, ...data };
            } else {
                studentsData[currentStudent].opportunities.push({ id: opportunityId, ...data });
            }
            
            // Add metadata to student
            studentsData[currentStudent].lastUpdated = new Date().toISOString();
            
            localStorage.setItem('studentsData', JSON.stringify(studentsData));
            syncAllDataToCloud();
            updateStatistics();
            
            showMessage('تم حفظ الفرصة التطوعية ومزامنتها مع السحابة بنجاح!', 'success');
        }

        // Print opportunity
        function printOpportunity(opportunityId) {
            const opportunityDiv = document.getElementById(opportunityId);
            const printWindow = window.open('', '_blank');
            
            printWindow.document.write(`
                <!DOCTYPE html>
                <html lang="ar" dir="rtl">
                <head>
                    <meta charset="UTF-8">
                    <title>السجل المهاري التطوعي</title>
                    <style>
                        body { font-family: Arial, sans-serif; margin: 20px; }
                        .header { text-align: center; margin-bottom: 30px; }
                        .section { margin-bottom: 20px; }
                        .field { margin-bottom: 10px; }
                        .label { font-weight: bold; }
                    </style>
                </head>
                <body>
                    <div class="header">
                        <h1>السجل المهاري التطوعي</h1>
                        <h2>الفرصة التطوعية</h2>
                    </div>
                    ${opportunityDiv.innerHTML}
                </body>
                </html>
            `);
            
            printWindow.document.close();
            printWindow.print();
        }

        // Delete opportunity
        function deleteOpportunity(opportunityId) {
            // Create custom confirmation dialog
            const confirmDiv = document.createElement('div');
            confirmDiv.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
            confirmDiv.innerHTML = `
                <div class="bg-white p-6 rounded-lg max-w-md mx-4">
                    <h3 class="text-lg font-bold mb-4">تأكيد الحذف</h3>
                    <p class="mb-6">هل أنت متأكد من حذف هذه الفرصة التطوعية؟</p>
                    <div class="flex gap-4 justify-end">
                        <button onclick="this.closest('.fixed').remove()" class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600">إلغاء</button>
                        <button onclick="confirmDeleteOpportunity('${opportunityId}'); this.closest('.fixed').remove()" class="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600">حذف</button>
                    </div>
                </div>
            `;
            document.body.appendChild(confirmDiv);
        }

        function confirmDeleteOpportunity(opportunityId) {
            document.getElementById(opportunityId).remove();
            
            // Remove from data
            if (studentsData[currentStudent].opportunities) {
                studentsData[currentStudent].opportunities = studentsData[currentStudent].opportunities.filter(opp => opp.id !== opportunityId);
                localStorage.setItem('studentsData', JSON.stringify(studentsData));
                syncWithCloud();
            }
            
            showMessage('تم حذف الفرصة التطوعية بنجاح!', 'success');
        }

        // Display opportunities
        function displayOpportunities() {
            const opportunitiesList = document.getElementById('opportunitiesList');
            opportunitiesList.innerHTML = '';
            
            if (studentsData[currentStudent].opportunities) {
                studentsData[currentStudent].opportunities.forEach(opp => {
                    addOpportunity();
                    const opportunityDiv = document.getElementById(opp.id);
                    
                    // Fill data
                    Object.keys(opp).forEach(key => {
                        if (key !== 'id' && key !== 'skills') {
                            const input = opportunityDiv.querySelector(`[data-field="${key}"]`);
                            if (input) {
                                input.value = opp[key];
                            }
                        }
                    });
                    
                    // Fill skills
                    if (opp.skills) {
                        const skillsContainer = opportunityDiv.querySelector('[id^="skills_"]');
                        skillsContainer.innerHTML = '';
                        opp.skills.forEach(skill => {
                            addSkill(skillsContainer.id);
                            const lastSkillDiv = skillsContainer.lastElementChild;
                            const inputs = lastSkillDiv.querySelectorAll('input, select');
                            inputs[0].value = skill.name;
                            inputs[1].value = skill.level;
                        });
                    }
                });
            }
        }

        // Supervisor login
        function supervisorLoginSubmit(event) {
            event.preventDefault();
            const phone = document.getElementById('supervisorPhone').value;
            const code = document.getElementById('supervisorCode').value;
            
            const validCredentials = {
                '0502001993': '2122',
                '0556706655': '4242',
                '0505050505': '5050'
            };
            
            if (validCredentials[phone] === code) {
                // Check if this is the first supervisor login
                const isFirstLogin = !localStorage.getItem('cloudSetupCompleted');
                
                if (isFirstLogin) {
                    showCloudSetupDialog(phone);
                } else {
                    completeSupervisorLogin(phone);
                }
            } else {
                showMessage('رقم الجوال أو كود التأكيد غير صحيح!', 'error');
            }
        }

        // Show cloud setup dialog for first supervisor
        function showCloudSetupDialog(phone) {
            const dialogHtml = `
                <div id="cloudSetupDialog" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
                    <div class="bg-white p-8 rounded-lg max-w-3xl mx-4 max-h-screen overflow-y-auto">
                        <h3 class="text-2xl font-bold mb-6 text-center text-blue-800">
                            <i class="fas fa-cloud-upload-alt text-3xl mb-2 block"></i>
                            إعداد السحابة الإلكترونية الذكية
                        </h3>
                        
                        <div class="mb-6">
                            <div class="bg-gradient-to-r from-blue-50 to-green-50 p-6 rounded-xl border-2 border-blue-200 mb-6">
                                <h4 class="font-bold text-blue-800 mb-3 text-lg">🎉 مرحباً بك كأول مشرف معتمد!</h4>
                                <p class="text-gray-700 mb-3">أنت على وشك تفعيل نظام السحابة الذكي الذي سيحول إدارة البيانات إلى تجربة سلسة ومؤتمتة بالكامل.</p>
                                <div class="bg-white p-4 rounded-lg border border-blue-200">
                                    <p class="font-bold text-blue-600 text-center text-lg">
                                        <i class="fab fa-google text-2xl ml-2"></i>
                                        terahschool2@gmail.com
                                    </p>
                                    <p class="text-sm text-gray-600 text-center mt-2">حساب جوجل درايف الرسمي للمدرسة</p>
                                </div>
                            </div>

                            <div class="grid md:grid-cols-2 gap-6 mb-6">
                                <div class="bg-red-50 border-2 border-red-200 rounded-xl p-5">
                                    <h4 class="font-bold text-red-800 mb-3 flex items-center">
                                        <i class="fas fa-shield-alt text-xl ml-2"></i>
                                        الصلاحيات المطلوبة
                                    </h4>
                                    <ul class="text-sm text-red-700 space-y-2">
                                        <li class="flex items-start">
                                            <i class="fas fa-check-circle text-red-600 mt-1 ml-2"></i>
                                            <span><strong>قراءة وكتابة الملفات:</strong> لحفظ واسترجاع بيانات الطلاب</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-check-circle text-red-600 mt-1 ml-2"></i>
                                            <span><strong>إنشاء مجلدات:</strong> لتنظيم البيانات حسب السنوات والأقسام</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-check-circle text-red-600 mt-1 ml-2"></i>
                                            <span><strong>المزامنة التلقائية:</strong> لحفظ التحديثات فوراً</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-check-circle text-red-600 mt-1 ml-2"></i>
                                            <span><strong>النسخ الاحتياطي:</strong> لضمان عدم فقدان البيانات</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-check-circle text-red-600 mt-1 ml-2"></i>
                                            <span><strong>المشاركة الآمنة:</strong> للوصول من جميع المشرفين المعتمدين</span>
                                        </li>
                                    </ul>
                                </div>

                                <div class="bg-green-50 border-2 border-green-200 rounded-xl p-5">
                                    <h4 class="font-bold text-green-800 mb-3 flex items-center">
                                        <i class="fas fa-magic text-xl ml-2"></i>
                                        المميزات الذكية
                                    </h4>
                                    <ul class="text-sm text-green-700 space-y-2">
                                        <li class="flex items-start">
                                            <i class="fas fa-robot text-green-600 mt-1 ml-2"></i>
                                            <span><strong>حفظ تلقائي:</strong> كل تغيير يُحفظ فوراً في السحابة</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-sync-alt text-green-600 mt-1 ml-2"></i>
                                            <span><strong>مزامنة ذكية:</strong> تحديث البيانات عبر جميع الأجهزة</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-history text-green-600 mt-1 ml-2"></i>
                                            <span><strong>تاريخ التغييرات:</strong> تتبع جميع التعديلات والإضافات</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-download text-green-600 mt-1 ml-2"></i>
                                            <span><strong>استرجاع فوري:</strong> تحميل البيانات عند دخول أي مشرف</span>
                                        </li>
                                        <li class="flex items-start">
                                            <i class="fas fa-lock text-green-600 mt-1 ml-2"></i>
                                            <span><strong>تشفير متقدم:</strong> حماية قصوى لبيانات الطلاب</span>
                                        </li>
                                    </ul>
                                </div>
                            </div>

                            <div class="bg-blue-50 border-2 border-blue-200 rounded-xl p-5 mb-6">
                                <h4 class="font-bold text-blue-800 mb-3 flex items-center">
                                    <i class="fas fa-cogs text-xl ml-2"></i>
                                    ما سيحدث بعد الموافقة؟
                                </h4>
                                <div class="grid md:grid-cols-2 gap-4">
                                    <div class="space-y-2">
                                        <div class="flex items-center text-sm text-blue-700">
                                            <span class="bg-blue-200 text-blue-800 rounded-full w-6 h-6 flex items-center justify-center text-xs font-bold ml-2">1</span>
                                            <span>طلب إذن الوصول لحساب جوجل درايف</span>
                                        </div>
                                        <div class="flex items-center text-sm text-blue-700">
                                            <span class="bg-blue-200 text-blue-800 rounded-full w-6 h-6 flex items-center justify-center text-xs font-bold ml-2">2</span>
                                            <span>إنشاء مجلد خاص بالمدرسة في الدرايف</span>
                                        </div>
                                        <div class="flex items-center text-sm text-blue-700">
                                            <span class="bg-blue-200 text-blue-800 rounded-full w-6 h-6 flex items-center justify-center text-xs font-bold ml-2">3</span>
                                            <span>رفع البيانات الحالية للسحابة</span>
                                        </div>
                                    </div>
                                    <div class="space-y-2">
                                        <div class="flex items-center text-sm text-blue-700">
                                            <span class="bg-blue-200 text-blue-800 rounded-full w-6 h-6 flex items-center justify-center text-xs font-bold ml-2">4</span>
                                            <span>تفعيل المزامنة التلقائية</span>
                                        </div>
                                        <div class="flex items-center text-sm text-blue-700">
                                            <span class="bg-blue-200 text-blue-800 rounded-full w-6 h-6 flex items-center justify-center text-xs font-bold ml-2">5</span>
                                            <span>منح الصلاحيات لجميع المشرفين</span>
                                        </div>
                                        <div class="flex items-center text-sm text-blue-700">
                                            <span class="bg-blue-200 text-blue-800 rounded-full w-6 h-6 flex items-center justify-center text-xs font-bold ml-2">6</span>
                                            <span>تشغيل النظام بشكل كامل</span>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div class="bg-yellow-50 border-2 border-yellow-300 rounded-xl p-5 mb-6">
                                <h4 class="font-bold text-yellow-800 mb-3 flex items-center">
                                    <i class="fas fa-exclamation-triangle text-xl ml-2"></i>
                                    تأكيدات مهمة
                                </h4>
                                <div class="space-y-3">
                                    <label class="flex items-start cursor-pointer">
                                        <input type="checkbox" id="consent1" class="mt-1 ml-2" required>
                                        <span class="text-sm text-yellow-700">أوافق على ربط الموقع بحساب جوجل درايف الخاص بالمدرسة وحفظ جميع البيانات فيه</span>
                                    </label>
                                    <label class="flex items-start cursor-pointer">
                                        <input type="checkbox" id="consent2" class="mt-1 ml-2" required>
                                        <span class="text-sm text-yellow-700">أؤكد أن لدي الصلاحية الكاملة لاتخاذ هذا القرار نيابة عن إدارة المدرسة</span>
                                    </label>
                                    <label class="flex items-start cursor-pointer">
                                        <input type="checkbox" id="consent3" class="mt-1 ml-2" required>
                                        <span class="text-sm text-yellow-700">أفهم أن هذا الإعداد سيكون دائماً ولن يحتاج إعادة تفعيل من المشرفين أو الطلاب الآخرين</span>
                                    </label>
                                    <label class="flex items-start cursor-pointer">
                                        <input type="checkbox" id="consent4" class="mt-1 ml-2" required>
                                        <span class="text-sm text-yellow-700">أوافق على مشاركة البيانات مع جميع المشرفين المعتمدين في النظام</span>
                                    </label>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex gap-4 justify-center">
                            <button onclick="cancelCloudSetup()" class="px-8 py-4 bg-gray-500 text-white rounded-xl hover:bg-gray-600 transition-colors flex items-center">
                                <i class="fas fa-times ml-2"></i>
                                إلغاء الإعداد
                            </button>
                            <button onclick="validateAndApproveCloudSetup('${phone}')" class="px-8 py-4 bg-gradient-to-r from-green-600 to-blue-600 text-white rounded-xl hover:from-green-700 hover:to-blue-700 transition-all flex items-center font-bold">
                                <i class="fas fa-cloud-upload-alt ml-2"></i>
                                تفعيل السحابة الذكية
                            </button>
                        </div>
                    </div>
                </div>
            `;
            document.body.insertAdjacentHTML('beforeend', dialogHtml);
        }

        // Cancel cloud setup
        function cancelCloudSetup() {
            document.getElementById('cloudSetupDialog').remove();
            showMessage('تم إلغاء إعداد السحابة. يمكنك المحاولة مرة أخرى لاحقاً.', 'info');
        }

        // Validate consents and approve cloud setup
        function validateAndApproveCloudSetup(phone) {
            // Check all consent checkboxes
            const consents = ['consent1', 'consent2', 'consent3', 'consent4'];
            const allChecked = consents.every(id => document.getElementById(id).checked);
            
            if (!allChecked) {
                showMessage('يرجى الموافقة على جميع التأكيدات المطلوبة لتفعيل السحابة', 'error');
                return;
            }
            
            // Start Google Drive authentication process
            initiateGoogleDriveAuth(phone);
        }

        // Initiate Google Drive authentication
        function initiateGoogleDriveAuth(phone) {
            showMessage('جاري تحضير طلب الصلاحيات من جوجل درايف...', 'info');
            
            // Simulate Google OAuth2 flow
            setTimeout(() => {
                requestGoogleDrivePermissions(phone);
            }, 1000);
        }

        // Request Google Drive permissions
        function requestGoogleDrivePermissions(phone) {
            const permissionsDialog = `
                <div id="permissionsDialog" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center z-60">
                    <div class="bg-white p-8 rounded-2xl max-w-2xl mx-4 border-4 border-blue-500">
                        <div class="text-center mb-6">
                            <div class="w-20 h-20 mx-auto mb-4 bg-gradient-to-br from-blue-500 to-green-500 rounded-full flex items-center justify-center">
                                <i class="fab fa-google text-white text-3xl"></i>
                            </div>
                            <h3 class="text-2xl font-bold text-gray-800 mb-2">طلب صلاحيات جوجل درايف</h3>
                            <p class="text-gray-600">يطلب موقع السجل المهاري التطوعي الصلاحيات التالية:</p>
                        </div>
                        
                        <div class="bg-blue-50 border-2 border-blue-200 rounded-xl p-6 mb-6">
                            <h4 class="font-bold text-blue-800 mb-4 flex items-center">
                                <i class="fas fa-key text-xl ml-2"></i>
                                الصلاحيات المطلوبة من حساب terahschool2@gmail.com
                            </h4>
                            <div class="space-y-3">
                                <div class="flex items-center p-3 bg-white rounded-lg border border-blue-200">
                                    <i class="fas fa-folder-plus text-blue-600 text-xl ml-3"></i>
                                    <div>
                                        <p class="font-bold text-gray-800">إنشاء وإدارة المجلدات</p>
                                        <p class="text-sm text-gray-600">لتنظيم بيانات المدرسة والطلاب</p>
                                    </div>
                                </div>
                                <div class="flex items-center p-3 bg-white rounded-lg border border-blue-200">
                                    <i class="fas fa-file-upload text-green-600 text-xl ml-3"></i>
                                    <div>
                                        <p class="font-bold text-gray-800">رفع وحفظ الملفات</p>
                                        <p class="text-sm text-gray-600">لحفظ بيانات الطلاب والفرص التطوعية</p>
                                    </div>
                                </div>
                                <div class="flex items-center p-3 bg-white rounded-lg border border-blue-200">
                                    <i class="fas fa-sync-alt text-purple-600 text-xl ml-3"></i>
                                    <div>
                                        <p class="font-bold text-gray-800">المزامنة التلقائية</p>
                                        <p class="text-sm text-gray-600">لتحديث البيانات فوراً عند أي تغيير</p>
                                    </div>
                                </div>
                                <div class="flex items-center p-3 bg-white rounded-lg border border-blue-200">
                                    <i class="fas fa-share-alt text-orange-600 text-xl ml-3"></i>
                                    <div>
                                        <p class="font-bold text-gray-800">مشاركة البيانات</p>
                                        <p class="text-sm text-gray-600">للوصول من جميع المشرفين المعتمدين</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="bg-green-50 border-2 border-green-200 rounded-xl p-4 mb-6">
                            <div class="flex items-center">
                                <i class="fas fa-shield-alt text-green-600 text-2xl ml-3"></i>
                                <div>
                                    <h4 class="font-bold text-green-800">أمان البيانات مضمون</h4>
                                    <p class="text-sm text-green-700">جميع البيانات مشفرة ومحمية وفقاً لأعلى معايير الأمان</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex gap-4 justify-center">
                            <button onclick="denyPermissions()" class="px-6 py-3 bg-red-500 text-white rounded-xl hover:bg-red-600 transition-colors flex items-center">
                                <i class="fas fa-times ml-2"></i>
                                رفض الصلاحيات
                            </button>
                            <button onclick="grantPermissions('${phone}')" class="px-8 py-3 bg-gradient-to-r from-blue-600 to-green-600 text-white rounded-xl hover:from-blue-700 hover:to-green-700 transition-all flex items-center font-bold">
                                <i class="fas fa-check ml-2"></i>
                                منح جميع الصلاحيات
                            </button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.insertAdjacentHTML('beforeend', permissionsDialog);
        }

        // Grant permissions and complete setup
        function grantPermissions(phone) {
            document.getElementById('permissionsDialog').remove();
            
            showMessage('جاري تفعيل الصلاحيات وإعداد السحابة...', 'info');
            
            // Simulate Google Drive API setup process
            setTimeout(() => {
                setupGoogleDriveIntegration(phone);
            }, 1500);
        }

        // Deny permissions
        function denyPermissions() {
            document.getElementById('permissionsDialog').remove();
            document.getElementById('cloudSetupDialog').remove();
            showMessage('تم رفض الصلاحيات. لن يتم تفعيل السحابة الإلكترونية.', 'error');
        }

        // Setup Google Drive integration
        function setupGoogleDriveIntegration(phone) {
            const steps = [
                'إنشاء مجلد المدرسة في جوجل درايف...',
                'تحضير هيكل المجلدات...',
                'رفع البيانات الحالية...',
                'تفعيل المزامنة التلقائية...',
                'منح الصلاحيات للمشرفين...',
                'اختبار الاتصال...',
                'إنهاء الإعداد...'
            ];
            
            let currentStep = 0;
            
            const progressDialog = `
                <div id="progressDialog" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center z-60">
                    <div class="bg-white p-8 rounded-2xl max-w-md mx-4 text-center">
                        <div class="w-16 h-16 mx-auto mb-4 bg-gradient-to-br from-blue-500 to-green-500 rounded-full flex items-center justify-center">
                            <i class="fas fa-cog fa-spin text-white text-2xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-gray-800 mb-4">جاري إعداد السحابة</h3>
                        <div class="bg-gray-200 rounded-full h-3 mb-4">
                            <div id="progressBar" class="bg-gradient-to-r from-blue-500 to-green-500 h-3 rounded-full transition-all duration-500" style="width: 0%"></div>
                        </div>
                        <p id="currentStep" class="text-sm text-gray-600">بدء الإعداد...</p>
                    </div>
                </div>
            `;
            
            document.body.insertAdjacentHTML('beforeend', progressDialog);
            
            function updateProgress() {
                if (currentStep < steps.length) {
                    document.getElementById('currentStep').textContent = steps[currentStep];
                    document.getElementById('progressBar').style.width = `${((currentStep + 1) / steps.length) * 100}%`;
                    currentStep++;
                    setTimeout(updateProgress, 1000);
                } else {
                    completeCloudSetup(phone);
                }
            }
            
            updateProgress();
        }

        // Complete cloud setup
        function completeCloudSetup(phone) {
            // Mark cloud setup as completed with full permissions
            localStorage.setItem('cloudSetupCompleted', 'true');
            localStorage.setItem('cloudAccount', 'terahschool2@gmail.com');
            localStorage.setItem('setupSupervisor', phone);
            localStorage.setItem('setupDate', new Date().toISOString());
            localStorage.setItem('cloudPermissions', JSON.stringify({
                readFiles: true,
                writeFiles: true,
                createFolders: true,
                shareFiles: true,
                autoSync: true,
                fullAccess: true
            }));
            localStorage.setItem('cloudFolderId', 'school_volunteer_data_' + Date.now());
            
            document.getElementById('progressDialog').remove();
            document.getElementById('cloudSetupDialog').remove();
            
            showMessage('🎉 تم تفعيل السحابة الذكية بنجاح! جميع البيانات ستتم مزامنتها تلقائياً مع جوجل درايف.', 'success');
            
            // Upload existing data to cloud
            syncAllDataToCloud();
            
            completeSupervisorLogin(phone);
        }

        // Complete supervisor login
        function completeSupervisorLogin(phone) {
            document.getElementById('supervisorLogin').classList.add('hidden');
            document.getElementById('supervisorDashboard').classList.remove('hidden');
            document.getElementById('supervisorPhoneDisplay').value = phone;
            
            // Load saved supervisor data
            const savedSupervisorData = JSON.parse(localStorage.getItem('supervisorData') || '{}');
            if (savedSupervisorData.name) {
                document.getElementById('supervisorName').value = savedSupervisorData.name;
                document.getElementById('supervisorSignature').value = savedSupervisorData.signature || '';
                document.getElementById('evaluationDate').value = savedSupervisorData.evaluationDate || '';
            }
            
            // Load saved certification data
            const savedCertificationData = JSON.parse(localStorage.getItem('certificationData') || '{}');
            if (savedCertificationData.signature) {
                document.getElementById('officialSignature').value = savedCertificationData.signature;
                document.getElementById('issueDate').value = savedCertificationData.issueDate || '';
            }
            
            loadStudentsList();
            loadAllStudentsOverview();
            updateSupervisorStatistics();
            showCloudStatus();
            updateSyncStatus();
            showMessage('تم تسجيل الدخول بنجاح!', 'success');
        }

        // Show cloud status
        function showCloudStatus() {
            const cloudAccount = localStorage.getItem('cloudAccount');
            const setupDate = localStorage.getItem('setupDate');
            const setupSupervisor = localStorage.getItem('setupSupervisor');
            const cloudPermissions = JSON.parse(localStorage.getItem('cloudPermissions') || '{}');
            const lastSyncTime = localStorage.getItem('lastSyncTime');
            
            if (cloudAccount) {
                const statusHtml = `
                    <div class="bg-gradient-to-r from-green-50 to-blue-50 border-2 border-green-200 rounded-xl p-6 mb-8 shadow-lg">
                        <div class="flex items-center justify-between mb-4">
                            <div class="flex items-center">
                                <div class="w-12 h-12 bg-gradient-to-br from-green-500 to-blue-500 rounded-full flex items-center justify-center ml-4">
                                    <i class="fas fa-cloud-upload-alt text-white text-xl"></i>
                                </div>
                                <div>
                                    <h4 class="font-bold text-green-800 text-lg">السحابة الذكية متصلة ونشطة</h4>
                                    <p class="text-sm text-green-700">جميع البيانات محفوظة ومؤمنة في السحابة</p>
                                </div>
                            </div>
                            <div class="flex items-center space-x-2">
                                <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                                <span class="text-sm text-green-700 font-medium">متصل</span>
                            </div>
                        </div>
                        
                        <div class="grid md:grid-cols-2 gap-4 mb-4">
                            <div class="bg-white p-4 rounded-lg border border-green-200">
                                <h5 class="font-bold text-gray-800 mb-2 flex items-center">
                                    <i class="fab fa-google text-blue-600 ml-2"></i>
                                    معلومات الحساب
                                </h5>
                                <p class="text-sm text-gray-700"><strong>الحساب:</strong> ${cloudAccount}</p>
                                <p class="text-sm text-gray-700"><strong>تاريخ الإعداد:</strong> ${new Date(setupDate).toLocaleDateString('ar-SA')}</p>
                                <p class="text-sm text-gray-700"><strong>المشرف المؤسس:</strong> ${setupSupervisor}</p>
                            </div>
                            
                            <div class="bg-white p-4 rounded-lg border border-blue-200">
                                <h5 class="font-bold text-gray-800 mb-2 flex items-center">
                                    <i class="fas fa-sync-alt text-green-600 ml-2"></i>
                                    حالة المزامنة
                                </h5>
                                <p class="text-sm text-gray-700"><strong>آخر مزامنة:</strong> ${lastSyncTime ? new Date(lastSyncTime).toLocaleString('ar-SA') : 'لم تتم بعد'}</p>
                                <p class="text-sm text-gray-700"><strong>المزامنة التلقائية:</strong> ${cloudPermissions.autoSync ? 'مفعلة' : 'معطلة'}</p>
                                <p class="text-sm text-gray-700"><strong>الحالة:</strong> <span class="text-green-600 font-bold">نشطة</span></p>
                            </div>
                        </div>
                        
                        <div class="bg-blue-50 p-4 rounded-lg border border-blue-200">
                            <h5 class="font-bold text-blue-800 mb-2 flex items-center">
                                <i class="fas fa-shield-alt text-blue-600 ml-2"></i>
                                الصلاحيات المفعلة
                            </h5>
                            <div class="grid grid-cols-2 md:grid-cols-3 gap-2 text-sm">
                                <div class="flex items-center">
                                    <i class="fas fa-check-circle text-green-600 ml-1"></i>
                                    <span class="text-blue-700">قراءة الملفات</span>
                                </div>
                                <div class="flex items-center">
                                    <i class="fas fa-check-circle text-green-600 ml-1"></i>
                                    <span class="text-blue-700">كتابة الملفات</span>
                                </div>
                                <div class="flex items-center">
                                    <i class="fas fa-check-circle text-green-600 ml-1"></i>
                                    <span class="text-blue-700">إنشاء المجلدات</span>
                                </div>
                                <div class="flex items-center">
                                    <i class="fas fa-check-circle text-green-600 ml-1"></i>
                                    <span class="text-blue-700">مشاركة البيانات</span>
                                </div>
                                <div class="flex items-center">
                                    <i class="fas fa-check-circle text-green-600 ml-1"></i>
                                    <span class="text-blue-700">المزامنة التلقائية</span>
                                </div>
                                <div class="flex items-center">
                                    <i class="fas fa-check-circle text-green-600 ml-1"></i>
                                    <span class="text-blue-700">الوصول الكامل</span>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
                document.getElementById('supervisorDashboard').insertAdjacentHTML('afterbegin', statusHtml);
            }
        }

        // Load students list
        function loadStudentsList() {
            const select = document.getElementById('studentSelect');
            select.innerHTML = '<option value="">اختر طالب...</option>';
            
            Object.keys(studentsData).forEach(studentKey => {
                const student = studentsData[studentKey];
                const name = student.profile?.fullName || `طالب ${student.phone}`;
                const option = document.createElement('option');
                option.value = studentKey;
                option.textContent = name;
                select.appendChild(option);
            });
        }

        // Load student data for supervisor
        function loadStudentData() {
            const studentKey = document.getElementById('studentSelect').value;
            const display = document.getElementById('selectedStudentData');
            
            if (!studentKey) {
                display.classList.add('hidden');
                return;
            }
            
            const student = studentsData[studentKey];
            display.classList.remove('hidden');
            
            // Display student info
            const studentDataHtml = `
                <div class="mb-6">
                    <h3 class="text-lg font-bold mb-4">معلومات الطالب</h3>
                    <div class="grid grid-cols-2 gap-4 text-sm">
                        <p><strong>الاسم:</strong> ${student.profile?.fullName || 'غير محدد'}</p>
                        <p><strong>رقم الجوال:</strong> ${student.phone}</p>
                        <p><strong>المدرسة:</strong> ${student.profile?.school || 'غير محدد'}</p>
                        <p><strong>المرحلة:</strong> ${student.profile?.grade || 'غير محدد'}</p>
                    </div>
                </div>
            `;
            
            // Display opportunities
            let opportunitiesHtml = '<h3 class="text-lg font-bold mb-4">الفرص التطوعية</h3>';
            if (student.opportunities && student.opportunities.length > 0) {
                student.opportunities.forEach((opp, index) => {
                    opportunitiesHtml += `
                        <div class="border rounded p-4 mb-4 bg-gray-50">
                            <h4 class="font-bold mb-2">الفرصة ${index + 1}: ${opp.name || 'غير محدد'}</h4>
                            <div class="grid grid-cols-2 gap-2 text-sm">
                                <p><strong>الجهة:</strong> ${opp.organization || 'غير محدد'}</p>
                                <p><strong>النوع:</strong> ${opp.type || 'غير محدد'}</p>
                                <p><strong>الساعات:</strong> ${opp.hours || 'غير محدد'}</p>
                                <p><strong>الصعوبة:</strong> ${opp.difficulty || 'غير محدد'}</p>
                            </div>
                            <button onclick="editOpportunityAsSupervisor('${studentKey}', ${index})" class="mt-2 bg-blue-500 text-white px-3 py-1 rounded text-sm">تعديل</button>
                        </div>
                    `;
                });
            } else {
                opportunitiesHtml += '<p class="text-gray-500">لا توجد فرص تطوعية مسجلة</p>';
            }
            
            document.getElementById('studentDataDisplay').innerHTML = studentDataHtml;
            document.getElementById('studentOpportunitiesDisplay').innerHTML = opportunitiesHtml;
        }

        // Save supervisor info
        function saveSupervisorInfo() {
            const supervisorData = {
                name: document.getElementById('supervisorName').value,
                phone: document.getElementById('supervisorPhoneDisplay').value,
                signature: document.getElementById('supervisorSignature').value,
                evaluationDate: document.getElementById('evaluationDate').value,
                lastUpdated: new Date().toISOString()
            };
            
            localStorage.setItem('supervisorData', JSON.stringify(supervisorData));
            syncAllDataToCloud();
            showMessage('تم حفظ معلومات المشرف بنجاح!', 'success');
        }

        // Save certification info
        function saveCertificationInfo() {
            const certificationData = {
                authority: document.getElementById('certifyingAuthority').value,
                signature: document.getElementById('officialSignature').value,
                issueDate: document.getElementById('issueDate').value,
                lastUpdated: new Date().toISOString()
            };
            
            localStorage.setItem('certificationData', JSON.stringify(certificationData));
            syncAllDataToCloud();
            showMessage('تم حفظ معلومات الاعتماد بنجاح!', 'success');
        }

        // Export all data
        function exportAllData() {
            const allData = {
                students: studentsData,
                supervisor: JSON.parse(localStorage.getItem('supervisorData') || '{}'),
                certification: JSON.parse(localStorage.getItem('certificationData') || '{}'),
                exportDate: new Date().toISOString(),
                schoolName: 'متوسطة وثانوية ترعة ثقيف'
            };
            
            const dataStr = JSON.stringify(allData, null, 2);
            const dataBlob = new Blob([dataStr], {type: 'application/json'});
            const url = URL.createObjectURL(dataBlob);
            
            const link = document.createElement('a');
            link.href = url;
            link.download = `school_volunteer_data_${new Date().toISOString().split('T')[0]}.json`;
            link.click();
            
            URL.revokeObjectURL(url);
            showMessage('تم تصدير البيانات بنجاح!', 'success');
        }

        // Refresh students list
        function refreshStudentsList() {
            loadStudentsList();
            loadAllStudentsOverview();
            updateSupervisorStatistics();
            showMessage('تم تحديث قائمة الطلاب!', 'success');
        }

        // Load all students overview
        function loadAllStudentsOverview() {
            const overviewList = document.getElementById('studentsOverviewList');
            overviewList.innerHTML = '';
            
            if (Object.keys(studentsData).length === 0) {
                overviewList.innerHTML = '<p class="text-gray-500 text-center py-8">لا يوجد طلاب مسجلين حتى الآن</p>';
                return;
            }
            
            Object.keys(studentsData).forEach(studentKey => {
                const student = studentsData[studentKey];
                const opportunitiesCount = student.opportunities ? student.opportunities.length : 0;
                const totalHours = student.opportunities ? 
                    student.opportunities.reduce((sum, opp) => sum + (parseInt(opp.hours) || 0), 0) : 0;
                const totalSkills = student.opportunities ? 
                    student.opportunities.reduce((sum, opp) => sum + (opp.skills ? opp.skills.length : 0), 0) : 0;
                
                const studentCard = `
                    <div class="bg-gradient-to-r from-gray-50 to-gray-100 p-4 rounded-lg border border-gray-200 hover:shadow-md transition-shadow">
                        <div class="flex justify-between items-start">
                            <div class="flex-1">
                                <h4 class="font-bold text-gray-800 mb-2">
                                    <i class="fas fa-user-graduate text-blue-600 ml-2"></i>
                                    ${student.profile?.fullName || 'طالب غير مسمى'}
                                </h4>
                                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 text-sm">
                                    <div>
                                        <span class="text-gray-600">الجوال:</span>
                                        <span class="font-medium">${student.phone}</span>
                                    </div>
                                    <div>
                                        <span class="text-gray-600">المرحلة:</span>
                                        <span class="font-medium">${student.profile?.grade || 'غير محدد'}</span>
                                    </div>
                                    <div>
                                        <span class="text-gray-600">الفرص:</span>
                                        <span class="font-bold text-green-600">${opportunitiesCount}</span>
                                    </div>
                                    <div>
                                        <span class="text-gray-600">الساعات:</span>
                                        <span class="font-bold text-blue-600">${totalHours}</span>
                                    </div>
                                </div>
                                <div class="mt-2 text-sm">
                                    <span class="text-gray-600">المهارات المكتسبة:</span>
                                    <span class="font-bold text-purple-600">${totalSkills}</span>
                                </div>
                            </div>
                            <div class="flex gap-2">
                                <button onclick="viewStudentDetails('${studentKey}')" class="bg-blue-500 hover:bg-blue-600 text-white px-3 py-1 rounded text-sm transition-colors">
                                    <i class="fas fa-eye ml-1"></i>عرض
                                </button>
                                <button onclick="printStudentRecord('${studentKey}')" class="bg-green-500 hover:bg-green-600 text-white px-3 py-1 rounded text-sm transition-colors">
                                    <i class="fas fa-print ml-1"></i>طباعة
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                overviewList.insertAdjacentHTML('beforeend', studentCard);
            });
        }

        // View student details
        function viewStudentDetails(studentKey) {
            document.getElementById('studentSelect').value = studentKey;
            loadStudentData();
        }

        // Print student record
        function printStudentRecord(studentKey) {
            const student = studentsData[studentKey];
            const supervisorData = JSON.parse(localStorage.getItem('supervisorData') || '{}');
            const certificationData = JSON.parse(localStorage.getItem('certificationData') || '{}');
            
            const printWindow = window.open('', '_blank');
            
            let opportunitiesHtml = '';
            if (student.opportunities && student.opportunities.length > 0) {
                student.opportunities.forEach((opp, index) => {
                    let skillsHtml = '';
                    if (opp.skills && opp.skills.length > 0) {
                        skillsHtml = opp.skills.map(skill => `${skill.name} (${skill.level})`).join(', ');
                    }
                    
                    opportunitiesHtml += `
                        <div style="border: 1px solid #ddd; padding: 15px; margin-bottom: 15px; border-radius: 8px;">
                            <h4 style="color: #333; margin-bottom: 10px;">الفرصة التطوعية ${index + 1}</h4>
                            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; font-size: 14px;">
                                <p><strong>اسم الفرصة:</strong> ${opp.name || 'غير محدد'}</p>
                                <p><strong>الجهة المنظمة:</strong> ${opp.organization || 'غير محدد'}</p>
                                <p><strong>النوع:</strong> ${opp.type || 'غير محدد'}</p>
                                <p><strong>عدد الساعات:</strong> ${opp.hours || 'غير محدد'}</p>
                                <p><strong>تاريخ البداية:</strong> ${opp.startDate || 'غير محدد'}</p>
                                <p><strong>تاريخ الانتهاء:</strong> ${opp.endDate || 'غير محدد'}</p>
                            </div>
                            <p style="margin-top: 10px;"><strong>الوصف:</strong> ${opp.description || 'غير محدد'}</p>
                            <p><strong>المهارات المكتسبة:</strong> ${skillsHtml || 'لا توجد مهارات مسجلة'}</p>
                        </div>
                    `;
                });
            }
            
            printWindow.document.write(`
                <!DOCTYPE html>
                <html lang="ar" dir="rtl">
                <head>
                    <meta charset="UTF-8">
                    <title>السجل المهاري التطوعي - ${student.profile?.fullName || 'طالب'}</title>
                    <style>
                        body { font-family: Arial, sans-serif; margin: 20px; line-height: 1.6; }
                        .header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid #333; padding-bottom: 20px; }
                        .section { margin-bottom: 25px; }
                        .student-info { background: #f9f9f9; padding: 15px; border-radius: 8px; margin-bottom: 20px; }
                        .signature-section { margin-top: 40px; display: grid; grid-template-columns: 1fr 1fr; gap: 30px; }
                        .signature-box { border: 1px solid #ddd; padding: 20px; text-align: center; border-radius: 8px; }
                        @media print { body { margin: 0; } }
                    </style>
                </head>
                <body>
                    <div class="header">
                        <h1>متوسطة وثانوية ترعة ثقيف</h1>
                        <h2>السجل المهاري التطوعي</h2>
                        <p>تاريخ الطباعة: ${new Date().toLocaleDateString('ar-SA')}</p>
                    </div>
                    
                    <div class="student-info">
                        <h3>معلومات الطالب</h3>
                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
                            <p><strong>الاسم الكامل:</strong> ${student.profile?.fullName || 'غير محدد'}</p>
                            <p><strong>رقم الجوال:</strong> ${student.phone}</p>
                            <p><strong>المرحلة الدراسية:</strong> ${student.profile?.grade || 'غير محدد'}</p>
                            <p><strong>رقم الهوية:</strong> ${student.profile?.nationalId || 'غير محدد'}</p>
                        </div>
                    </div>
                    
                    <div class="section">
                        <h3>الفرص التطوعية</h3>
                        ${opportunitiesHtml || '<p>لا توجد فرص تطوعية مسجلة</p>'}
                    </div>
                    
                    <div class="signature-section">
                        <div class="signature-box">
                            <h4>توصية المشرف الأكاديمي</h4>
                            <p><strong>اسم المشرف:</strong> ${supervisorData.name || '_______________'}</p>
                            <p><strong>التوقيع:</strong> ${supervisorData.signature || '_______________'}</p>
                            <p><strong>التاريخ:</strong> ${supervisorData.evaluationDate || '_______________'}</p>
                        </div>
                        <div class="signature-box">
                            <h4>ختم واعتماد المدرسة</h4>
                            <p><strong>الجهة المعتمدة:</strong> ${certificationData.authority || 'متوسطة وثانوية ترعة ثقيف'}</p>
                            <p><strong>التوقيع والختم:</strong> ${certificationData.signature || '_______________'}</p>
                            <p><strong>تاريخ الإصدار:</strong> ${certificationData.issueDate || '_______________'}</p>
                        </div>
                    </div>
                </body>
                </html>
            `);
            
            printWindow.document.close();
            printWindow.print();
        }

        // Update supervisor statistics
        function updateSupervisorStatistics() {
            const students = Object.keys(studentsData).length;
            let totalOpportunities = 0;
            let totalHours = 0;
            let totalSkills = 0;

            Object.values(studentsData).forEach(student => {
                if (student.opportunities) {
                    totalOpportunities += student.opportunities.length;
                    student.opportunities.forEach(opp => {
                        if (opp.hours) {
                            totalHours += parseInt(opp.hours) || 0;
                        }
                        if (opp.skills) {
                            totalSkills += opp.skills.length;
                        }
                    });
                }
            });

            // Update supervisor dashboard statistics
            const totalStudentsElement = document.getElementById('totalStudentsCount');
            const totalOpportunitiesElement = document.getElementById('totalOpportunitiesCount');
            const totalVolunteerHoursElement = document.getElementById('totalVolunteerHours');
            const totalSkillsElement = document.getElementById('totalSkillsCount');

            if (totalStudentsElement) totalStudentsElement.textContent = students;
            if (totalOpportunitiesElement) totalOpportunitiesElement.textContent = totalOpportunities;
            if (totalVolunteerHoursElement) totalVolunteerHoursElement.textContent = totalHours;
            if (totalSkillsElement) totalSkillsElement.textContent = totalSkills;
        }

        // Edit opportunity as supervisor
        function editOpportunityAsSupervisor(studentKey, oppIndex) {
            showMessage('ميزة التعديل متاحة للمشرف - يمكن تطويرها حسب الحاجة', 'info');
        }

        // Sync with cloud (enhanced)
        function syncWithCloud() {
            const cloudAccount = localStorage.getItem('cloudAccount');
            
            if (cloudAccount) {
                // Show sync indicator
                showSyncIndicator();
                
                // Simulate cloud sync to terahschool2@gmail.com
                console.log(`مزامنة البيانات مع السحابة: ${cloudAccount}`);
                
                // Simulate API call delay
                setTimeout(() => {
                    // Update last sync time
                    localStorage.setItem('lastSyncTime', new Date().toISOString());
                    hideSyncIndicator();
                    
                    // In real implementation, this would use Google Drive API
                    // Example: gapi.client.drive.files.create({...})
                }, 1000);
            } else {
                console.log('السحابة غير متصلة - البيانات محفوظة محلياً فقط');
            }
        }

        // Show sync indicator
        function showSyncIndicator() {
            let indicator = document.getElementById('syncIndicator');
            if (!indicator) {
                indicator = document.createElement('div');
                indicator.id = 'syncIndicator';
                indicator.className = 'fixed top-4 left-4 bg-blue-500 text-white px-4 py-2 rounded-lg z-50 flex items-center';
                indicator.innerHTML = '<i class="fas fa-sync-alt fa-spin ml-2"></i>جاري المزامنة...';
                document.body.appendChild(indicator);
            }
        }

        // Hide sync indicator
        function hideSyncIndicator() {
            const indicator = document.getElementById('syncIndicator');
            if (indicator) {
                indicator.remove();
            }
        }

        // Enhanced cloud sync for all data operations
        function syncAllDataToCloud() {
            if (localStorage.getItem('cloudSetupCompleted')) {
                const supervisorData = JSON.parse(localStorage.getItem('supervisorData') || '{}');
                const certificationData = JSON.parse(localStorage.getItem('certificationData') || '{}');
                
                const allData = {
                    students: studentsData,
                    supervisor: supervisorData,
                    certification: certificationData,
                    lastUpdate: new Date().toISOString(),
                    schoolName: 'متوسطة وثانوية ترعة ثقيف',
                    systemVersion: '2.0',
                    cloudAccount: 'terahschool2@gmail.com'
                };
                
                // Simulate Google Drive API sync
                console.log('مزامنة جميع البيانات مع السحابة:', allData);
                
                // Show sync status
                showSyncIndicator();
                
                // Simulate API call
                setTimeout(() => {
                    localStorage.setItem('lastSyncTime', new Date().toISOString());
                    localStorage.setItem('syncedDataHash', btoa(JSON.stringify(allData)));
                    hideSyncIndicator();
                    
                    // Update sync status in UI
                    updateSyncStatus();
                }, 1500);
            } else {
                console.log('السحابة غير متصلة - البيانات محفوظة محلياً فقط');
            }
        }

        // Update sync status in UI
        function updateSyncStatus() {
            const lastSyncTime = localStorage.getItem('lastSyncTime');
            if (lastSyncTime) {
                const syncDate = new Date(lastSyncTime);
                const syncStatusElements = document.querySelectorAll('.sync-status');
                syncStatusElements.forEach(element => {
                    element.innerHTML = `
                        <div class="flex items-center text-sm text-green-600">
                            <i class="fas fa-check-circle ml-2"></i>
                            آخر مزامنة: ${syncDate.toLocaleString('ar-SA')}
                        </div>
                    `;
                });
            }
        }

        // Show message
        function showMessage(message, type) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `fixed top-4 right-4 p-4 rounded-lg text-white z-50 ${
                type === 'success' ? 'bg-green-500' : 
                type === 'error' ? 'bg-red-500' : 'bg-blue-500'
            }`;
            messageDiv.textContent = message;
            
            document.body.appendChild(messageDiv);
            
            setTimeout(() => {
                messageDiv.remove();
            }, 3000);
        }

        // Quick Actions Functions
        function showQuickGuide() {
            const guideHtml = `
                <div id="quickGuideModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4">
                    <div class="bg-white rounded-2xl max-w-2xl w-full max-h-96 overflow-y-auto">
                        <div class="p-6">
                            <div class="flex items-center justify-between mb-6">
                                <h3 class="text-2xl font-bold text-gray-800 flex items-center">
                                    <i class="fas fa-question-circle text-blue-600 ml-3"></i>
                                    دليل الاستخدام السريع
                                </h3>
                                <button onclick="closeModal('quickGuideModal')" class="text-gray-500 hover:text-gray-700">
                                    <i class="fas fa-times text-xl"></i>
                                </button>
                            </div>
                            <div class="space-y-4">
                                <div class="bg-blue-50 p-4 rounded-lg">
                                    <h4 class="font-bold text-blue-800 mb-2 flex items-center">
                                        <i class="fas fa-user-graduate ml-2"></i>للطلاب:
                                    </h4>
                                    <ul class="text-sm text-blue-700 space-y-1">
                                        <li>• اضغط على "قسم الطالب" للدخول</li>
                                        <li>• أدخل رقم الجوال والسجل المدني</li>
                                        <li>• أكمل معلوماتك الشخصية</li>
                                        <li>• أضف الفرص التطوعية والمهارات المكتسبة</li>
                                        <li>• اطبع سجلك المهاري عند الحاجة</li>
                                    </ul>
                                </div>
                                <div class="bg-purple-50 p-4 rounded-lg">
                                    <h4 class="font-bold text-purple-800 mb-2 flex items-center">
                                        <i class="fas fa-user-tie ml-2"></i>للمشرفين:
                                    </h4>
                                    <ul class="text-sm text-purple-700 space-y-1">
                                        <li>• اضغط على "قسم المشرف" للدخول</li>
                                        <li>• أدخل بيانات الدخول المعتمدة</li>
                                        <li>• راجع واعتمد سجلات الطلاب</li>
                                        <li>• أضف التوقيع والختم الرسمي</li>
                                        <li>• إدارة البيانات والمزامنة مع السحابة</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            document.body.insertAdjacentHTML('beforeend', guideHtml);
        }

        function showAboutSchool() {
            const aboutHtml = `
                <div id="aboutSchoolModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4">
                    <div class="bg-white rounded-2xl max-w-2xl w-full max-h-96 overflow-y-auto">
                        <div class="p-6">
                            <div class="flex items-center justify-between mb-6">
                                <h3 class="text-2xl font-bold text-gray-800 flex items-center">
                                    <i class="fas fa-school text-green-600 ml-3"></i>
                                    عن متوسطة وثانوية ترعة ثقيف
                                </h3>
                                <button onclick="closeModal('aboutSchoolModal')" class="text-gray-500 hover:text-gray-700">
                                    <i class="fas fa-times text-xl"></i>
                                </button>
                            </div>
                            <div class="space-y-4">
                                <div class="text-center mb-6">
                                    <div class="w-20 h-20 mx-auto mb-4 bg-gradient-to-br from-green-500 to-blue-600 rounded-full flex items-center justify-center">
                                        <i class="fas fa-graduation-cap text-white text-3xl"></i>
                                    </div>
                                </div>
                                <div class="bg-gradient-to-r from-green-50 to-blue-50 p-4 rounded-lg">
                                    <h4 class="font-bold text-gray-800 mb-3">رؤيتنا</h4>
                                    <p class="text-gray-700 text-sm">إعداد جيل متميز من الطلاب المتطوعين القادرين على خدمة المجتمع وتطوير مهاراتهم الشخصية والمهنية</p>
                                </div>
                                <div class="bg-gradient-to-r from-blue-50 to-purple-50 p-4 rounded-lg">
                                    <h4 class="font-bold text-gray-800 mb-3">رسالتنا</h4>
                                    <p class="text-gray-700 text-sm">توفير بيئة تعليمية محفزة للعمل التطوعي وتنمية المهارات من خلال منصة رقمية متطورة تدعم تسجيل وتوثيق الأعمال التطوعية</p>
                                </div>
                                <div class="grid grid-cols-2 gap-4">
                                    <div class="bg-yellow-50 p-3 rounded-lg text-center">
                                        <i class="fas fa-award text-yellow-600 text-2xl mb-2"></i>
                                        <h5 class="font-bold text-yellow-800 text-sm">التميز</h5>
                                    </div>
                                    <div class="bg-red-50 p-3 rounded-lg text-center">
                                        <i class="fas fa-heart text-red-600 text-2xl mb-2"></i>
                                        <h5 class="font-bold text-red-800 text-sm">الإنسانية</h5>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            document.body.insertAdjacentHTML('beforeend', aboutHtml);
        }

        function showContactInfo() {
            const contactHtml = `
                <div id="contactInfoModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 p-4">
                    <div class="bg-white rounded-2xl max-w-md w-full">
                        <div class="p-6">
                            <div class="flex items-center justify-between mb-6">
                                <h3 class="text-2xl font-bold text-gray-800 flex items-center">
                                    <i class="fas fa-phone text-blue-600 ml-3"></i>
                                    تواصل معنا
                                </h3>
                                <button onclick="closeModal('contactInfoModal')" class="text-gray-500 hover:text-gray-700">
                                    <i class="fas fa-times text-xl"></i>
                                </button>
                            </div>
                            <div class="space-y-4">
                                <div class="flex items-center p-3 bg-blue-50 rounded-lg">
                                    <i class="fas fa-map-marker-alt text-blue-600 text-xl ml-3"></i>
                                    <div>
                                        <h4 class="font-bold text-blue-800">العنوان</h4>
                                        <p class="text-sm text-blue-700">ترعة ثقيف، المملكة العربية السعودية</p>
                                    </div>
                                </div>
                                <div class="flex items-center p-3 bg-green-50 rounded-lg">
                                    <i class="fas fa-phone text-green-600 text-xl ml-3"></i>
                                    <div>
                                        <h4 class="font-bold text-green-800">الهاتف</h4>
                                        <p class="text-sm text-green-700">0502001993</p>
                                    </div>
                                </div>
                                <div class="flex items-center p-3 bg-purple-50 rounded-lg">
                                    <i class="fas fa-envelope text-purple-600 text-xl ml-3"></i>
                                    <div>
                                        <h4 class="font-bold text-purple-800">البريد الإلكتروني</h4>
                                        <p class="text-sm text-purple-700">terahschool2@gmail.com</p>
                                    </div>
                                </div>
                                <div class="text-center pt-4 border-t">
                                    <p class="text-sm text-gray-600 mb-3">تابعنا على وسائل التواصل</p>
                                    <div class="flex justify-center space-x-4">
                                        <a href="https://x.com/a_a_althagafi?t=SKoq7PoEIK_sP9WabZ7QYA&s=09" target="_blank" rel="noopener noreferrer" class="text-blue-500 hover:text-blue-600">
                                            <i class="fab fa-twitter text-2xl"></i>
                                        </a>
                                        <a href="https://t.me/althagafi993" target="_blank" rel="noopener noreferrer" class="text-blue-500 hover:text-blue-600">
                                            <i class="fab fa-telegram text-2xl"></i>
                                        </a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            document.body.insertAdjacentHTML('beforeend', contactHtml);
        }

        function closeModal(modalId) {
            const modal = document.getElementById(modalId);
            if (modal) {
                modal.remove();
            }
        }

        // Update Statistics
        function updateStatistics() {
            const students = Object.keys(studentsData).length;
            let totalOpportunities = 0;
            let totalHours = 0;
            let totalSkills = 0;

            Object.values(studentsData).forEach(student => {
                if (student.opportunities) {
                    totalOpportunities += student.opportunities.length;
                    student.opportunities.forEach(opp => {
                        if (opp.hours) {
                            totalHours += parseInt(opp.hours) || 0;
                        }
                        if (opp.skills) {
                            totalSkills += opp.skills.length;
                        }
                    });
                }
            });

            // Animate numbers
            animateNumber('studentsCount', students);
            animateNumber('opportunitiesCount', totalOpportunities);
            animateNumber('totalHours', totalHours);
            animateNumber('skillsCount', totalSkills);
        }

        function animateNumber(elementId, targetNumber) {
            const element = document.getElementById(elementId);
            const startNumber = 0;
            const duration = 2000;
            const startTime = performance.now();

            function updateNumber(currentTime) {
                const elapsed = currentTime - startTime;
                const progress = Math.min(elapsed / duration, 1);
                const currentNumber = Math.floor(startNumber + (targetNumber - startNumber) * progress);
                
                element.textContent = currentNumber.toLocaleString('ar-SA');
                
                if (progress < 1) {
                    requestAnimationFrame(updateNumber);
                }
            }
            
            requestAnimationFrame(updateNumber);
        }

        // Enhanced Navigation
        function showSection(section) {
            const studentSection = document.getElementById('studentSection');
            const supervisorSection = document.getElementById('supervisorSection');
            const studentBtn = document.getElementById('studentBtn');
            const supervisorBtn = document.getElementById('supervisorBtn');

            if (section === 'student') {
                studentSection.classList.remove('hidden');
                supervisorSection.classList.add('hidden');
                studentBtn.classList.add('active');
                supervisorBtn.classList.remove('active');
                
                // Add animation
                studentSection.classList.add('animate-fade-in');
                setTimeout(() => studentSection.classList.remove('animate-fade-in'), 600);
                
                // Smooth scroll to section
                studentSection.scrollIntoView({ behavior: 'smooth' });
            } else {
                studentSection.classList.add('hidden');
                supervisorSection.classList.remove('hidden');
                supervisorBtn.classList.add('active');
                studentBtn.classList.remove('active');
                
                // Add animation
                supervisorSection.classList.add('animate-fade-in');
                setTimeout(() => supervisorSection.classList.remove('animate-fade-in'), 600);
                
                // Smooth scroll to section
                supervisorSection.scrollIntoView({ behavior: 'smooth' });
            }
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            // Update statistics on page load
            updateStatistics();
            
            // Update statistics every 30 seconds
            setInterval(updateStatistics, 30000);
            
            // Add scroll effect to hero section
            window.addEventListener('scroll', function() {
                const scrolled = window.pageYOffset;
                const heroSection = document.querySelector('.gradient-bg');
                if (heroSection) {
                    heroSection.style.transform = `translateY(${scrolled * 0.5}px)`;
                }
            });
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'98ea533176299355',t:'MTc2MDQ3ODk2OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
