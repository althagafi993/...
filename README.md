<!DOCTYPE html>
<html lang="ar" dir="rtl" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة تدريب القدرات بالذكاء الاصطناعي</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            background-attachment: fixed;
            min-height: 100%;
        }
        
        /* Modern Gradient Backgrounds */
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
            pointer-events: none;
        }
        
        /* Enhanced Card Animations */
        .card-hover {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            backdrop-filter: blur(10px);
            background: rgba(255, 255, 255, 0.95);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .card-hover:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            background: rgba(255, 255, 255, 1);
        }
        
        /* Floating Animation */
        .float-animation {
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        /* Pulse Animation */
        .pulse-animation {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.8; transform: scale(1.05); }
        }
        
        /* Modern Question Card */
        .question-card {
            background: linear-gradient(145deg, rgba(255, 255, 255, 0.95), rgba(240, 244, 248, 0.95));
            border: 2px solid rgba(226, 232, 240, 0.3);
            backdrop-filter: blur(20px);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        /* Enhanced Button Styles */
        .modern-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border: none;
            color: white;
            padding: 12px 24px;
            border-radius: 12px;
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
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
        }
        
        /* Option Button Enhancements */
        .option-btn {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }
        
        .option-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(102, 126, 234, 0.1), transparent);
            transition: left 0.6s;
        }
        
        .option-btn:hover::before {
            left: 100%;
        }
        
        .option-btn:hover {
            transform: translateX(5px);
            border-color: #667eea;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.2);
        }
        
        /* Correct/Wrong Answer Animations */
        .correct-answer {
            background: linear-gradient(135deg, #d4edda, #c3e6cb) !important;
            border-color: #28a745 !important;
            animation: correctPulse 0.6s ease-in-out;
        }
        
        .wrong-answer {
            background: linear-gradient(135deg, #f8d7da, #f1b0b7) !important;
            border-color: #dc3545 !important;
            animation: wrongShake 0.6s ease-in-out;
        }
        
        @keyframes correctPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        @keyframes wrongShake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }
        
        /* Loading Spinner Enhancement */
        .loading-spinner {
            border: 4px solid rgba(102, 126, 234, 0.1);
            border-top: 4px solid #667eea;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Glass Morphism Effect */
        .glass-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        /* Progress Bar */
        .progress-bar {
            background: linear-gradient(90deg, #667eea, #764ba2);
            height: 4px;
            border-radius: 2px;
            transition: width 0.3s ease;
        }
        
        /* Notification Toast */
        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            padding: 16px 24px;
            border-radius: 12px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            transform: translateX(400px);
            transition: transform 0.3s ease;
            z-index: 1000;
        }
        
        .toast.show {
            transform: translateX(0);
        }
        
        /* Enhanced Typography */
        .title-gradient {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        /* Responsive Enhancements */
        @media (max-width: 768px) {
            .card-hover:hover {
                transform: translateY(-5px) scale(1.01);
            }
        }
        
        /* Social Icons */
        .social-icon {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
            font-size: 16px;
        }
        
        .social-icon:hover {
            transform: translateY(-2px);
            background: rgba(255, 255, 255, 0.2);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
        }
        
        .social-icon img {
            width: 24px;
            height: 24px;
            border-radius: 4px;
        }
    </style>
</head>
<body class="min-h-full">
    <!-- Header -->
    <header class="gradient-bg text-white shadow-lg">
        <div class="container mx-auto px-4 py-6">
            <div class="flex justify-between items-center">
                <div class="flex items-center space-x-4 space-x-reverse">
                    <div class="text-3xl">🧠</div>
                    <div>
                        <h1 class="text-2xl font-bold">منصة تدريب القدرات</h1>
                        <p class="text-blue-100">بالذكاء الاصطناعي</p>
                    </div>
                </div>
                <div id="userPoints" class="hidden bg-white/20 rounded-lg p-3">
                    <div class="flex items-center space-x-4 space-x-reverse text-sm">
                        <div class="flex items-center space-x-2 space-x-reverse">
                            <span>👤</span>
                            <span id="individualPoints">0</span>
                        </div>
                        <div class="flex items-center space-x-2 space-x-reverse">
                            <span>👥</span>
                            <span id="groupPoints">0</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <main class="container mx-auto px-4 py-8">
        <!-- Registration Screen -->
        <div id="registrationScreen" class="max-w-md mx-auto">
            <div class="card-hover rounded-xl shadow-lg p-8 float-animation">
                <div class="text-center mb-6">
                    <div class="text-6xl mb-4 pulse-animation">📚</div>
                    <h2 class="text-2xl font-bold title-gradient mb-2">مرحباً بك</h2>
                    <p class="text-gray-600">ابدأ رحلتك في تطوير قدراتك</p>
                </div>
                <form id="registrationForm">
                    <div class="mb-6">
                        <label for="studentName" class="block text-sm font-medium text-gray-700 mb-2">اسم الطالب</label>
                        <input type="text" id="studentName" required 
                               class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent backdrop-filter backdrop-blur-sm"
                               placeholder="أدخل اسمك الكامل">
                    </div>
                    <button type="submit" 
                            class="w-full modern-btn">
                        ابدأ التدريب
                    </button>
                </form>
            </div>
        </div>

        <!-- Mode Selection Screen -->
        <div id="modeSelectionScreen" class="hidden max-w-4xl mx-auto">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold title-gradient mb-4">اختر نوع التدريب</h2>
                <p class="text-white/80">حدد الطريقة التي تفضل التدرب بها</p>
            </div>
            
            <div class="grid md:grid-cols-2 gap-8">
                <!-- Individual Training -->
                <div class="card-hover rounded-xl shadow-lg p-8 cursor-pointer float-animation" onclick="selectMode('individual')" style="animation-delay: 0.2s;">
                    <div class="text-center">
                        <div class="text-6xl mb-4 pulse-animation">👤</div>
                        <h3 class="text-xl font-bold text-gray-800 mb-3">تدريب فردي</h3>
                        <p class="text-gray-600 mb-4">تدرب بمفردك وطور مهاراتك الشخصية</p>
                        <div class="glass-card rounded-lg p-3">
                            <p class="text-sm text-blue-700">✨ تركيز كامل على نقاط ضعفك</p>
                        </div>
                    </div>
                </div>

                <!-- Group Challenge -->
                <div class="card-hover rounded-xl shadow-lg p-8 cursor-pointer float-animation" onclick="selectMode('group')" style="animation-delay: 0.4s;">
                    <div class="text-center">
                        <div class="text-6xl mb-4 pulse-animation">👥</div>
                        <h3 class="text-xl font-bold text-gray-800 mb-3">تحدي جماعي</h3>
                        <p class="text-gray-600 mb-4">تنافس مع زملائك واكسب نقاط إضافية</p>
                        <div class="glass-card rounded-lg p-3">
                            <p class="text-sm text-green-700">🏆 تنافس مع حتى 50 طالب</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Question Type Selection -->
        <div id="questionTypeScreen" class="hidden max-w-6xl mx-auto">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold title-gradient mb-4">اختر أنواع أسئلة القدرات</h2>
                <p class="text-white/80">حدد الأنواع التي تريد التدرب عليها وعدد الأسئلة لكل نوع</p>
            </div>
            
            <!-- القسم اللفظي -->
            <div class="card-hover rounded-xl shadow-lg p-6 mb-6 float-animation" style="animation-delay: 0.1s;">
                <div class="flex items-center mb-6">
                    <div class="text-3xl ml-3 pulse-animation">📝</div>
                    <h3 class="text-xl font-bold text-gray-800">القسم اللفظي</h3>
                </div>
                
                <div class="grid md:grid-cols-5 gap-4">
                    <div class="bg-blue-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">📖</div>
                        <h4 class="font-medium text-gray-800 mb-2">استيعاب المقروء</h4>
                        <input type="number" id="reading-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-green-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">🔗</div>
                        <h4 class="font-medium text-gray-800 mb-2">الارتباط والاختلاف</h4>
                        <input type="number" id="relation-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-yellow-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">❌</div>
                        <h4 class="font-medium text-gray-800 mb-2">الخطأ السياقي</h4>
                        <input type="number" id="context-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-purple-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">⚖️</div>
                        <h4 class="font-medium text-gray-800 mb-2">التناظر اللفظي</h4>
                        <input type="number" id="analogy-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-red-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">✏️</div>
                        <h4 class="font-medium text-gray-800 mb-2">إكمال الجمل</h4>
                        <input type="number" id="completion-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                </div>
            </div>
            
            <!-- القسم الكمي -->
            <div class="card-hover rounded-xl shadow-lg p-6 mb-6 float-animation" style="animation-delay: 0.2s;">
                <div class="flex items-center mb-6">
                    <div class="text-3xl ml-3 pulse-animation">🔢</div>
                    <h3 class="text-xl font-bold text-gray-800">القسم الكمي</h3>
                </div>
                
                <div class="grid md:grid-cols-5 gap-4">
                    <div class="bg-indigo-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">📊</div>
                        <h4 class="font-medium text-gray-800 mb-2">تحليل وإحصاء</h4>
                        <input type="number" id="statistics-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-teal-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">📐</div>
                        <h4 class="font-medium text-gray-800 mb-2">هندسة</h4>
                        <input type="number" id="geometry-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-orange-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">🧮</div>
                        <h4 class="font-medium text-gray-800 mb-2">جبر</h4>
                        <input type="number" id="algebra-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-pink-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">🔢</div>
                        <h4 class="font-medium text-gray-800 mb-2">حساب</h4>
                        <input type="number" id="arithmetic-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                    
                    <div class="bg-cyan-50 rounded-lg p-4 text-center">
                        <div class="text-2xl mb-2">⚖️</div>
                        <h4 class="font-medium text-gray-800 mb-2">مقارنة</h4>
                        <input type="number" id="comparison-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center">
                    </div>
                </div>
            </div>
            
            <!-- أزرار سريعة -->
            <div class="glass-card rounded-xl p-6 mb-6 float-animation" style="animation-delay: 0.3s;">
                <h4 class="text-lg font-medium text-white mb-4">اختيارات سريعة:</h4>
                <div class="flex flex-wrap gap-3">
                    <button onclick="setQuickSelection('verbal')" 
                            class="modern-btn bg-blue-600 hover:bg-blue-700">
                        لفظي فقط (20 سؤال)
                    </button>
                    <button onclick="setQuickSelection('quantitative')" 
                            class="modern-btn bg-green-600 hover:bg-green-700">
                        كمي فقط (20 سؤال)
                    </button>
                    <button onclick="setQuickSelection('balanced')" 
                            class="modern-btn bg-purple-600 hover:bg-purple-700">
                        متوازن (30 سؤال)
                    </button>
                    <button onclick="setQuickSelection('full')" 
                            class="modern-btn bg-red-600 hover:bg-red-700">
                        اختبار كامل (50 سؤال)
                    </button>
                    <button onclick="clearAllSelections()" 
                            class="modern-btn bg-gray-600 hover:bg-gray-700">
                        مسح الكل
                    </button>
                </div>
            </div>
            
            <div class="text-center">
                <div class="mb-4 glass-card rounded-lg p-4 inline-block">
                    <span class="text-lg font-medium text-white">إجمالي الأسئلة: </span>
                    <span id="totalSelectedQuestions" class="text-2xl font-bold text-yellow-300 pulse-animation">0</span>
                </div>
                
                <div class="mt-6">
                    <button onclick="proceedWithSelectedQuestions()" 
                            class="modern-btn py-4 px-12 text-lg disabled:bg-gray-400 disabled:cursor-not-allowed"
                            id="proceedBtn" disabled>
                        المتابعة
                    </button>
                </div>
            </div>
        </div>



        <!-- Group Size Selection -->
        <div id="groupSizeScreen" class="hidden max-w-2xl mx-auto">
            <div class="card-hover rounded-xl shadow-lg p-8 float-animation">
                <div class="text-center mb-6">
                    <div class="text-4xl mb-4 pulse-animation">👥</div>
                    <h2 class="text-2xl font-bold title-gradient mb-4">حدد عدد المشاركين</h2>
                    <p class="text-gray-600">كم طالب سيشارك في التحدي؟</p>
                </div>
                
                <div class="mb-6">
                    <label for="participantCount" class="block text-sm font-medium text-gray-700 mb-2">عدد المشاركين (2-50)</label>
                    <input type="number" id="participantCount" min="2" max="50" value="5"
                           class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-center text-xl backdrop-filter backdrop-blur-sm">
                </div>
                
                <button onclick="createGroupChallenge()" 
                        class="w-full modern-btn py-4">
                    إنشاء رابط التحدي
                </button>
            </div>
        </div>

        <!-- Challenge Link Screen -->
        <div id="challengeLinkScreen" class="hidden max-w-2xl mx-auto">
            <div class="card-hover rounded-xl shadow-lg p-8 float-animation">
                <div class="text-center mb-6">
                    <div class="text-4xl mb-4 pulse-animation">🔗</div>
                    <h2 class="text-2xl font-bold title-gradient mb-4">رابط التحدي جاهز!</h2>
                    <p class="text-gray-600">شارك هذا الرابط مع زملائك</p>
                </div>
                
                <div class="glass-card rounded-lg p-4 mb-6">
                    <div class="flex items-center justify-between">
                        <span id="challengeLink" class="text-sm text-white flex-1 mr-3"></span>
                        <button onclick="copyLink()" class="modern-btn px-4 py-2 text-sm">
                            نسخ
                        </button>
                    </div>
                </div>
                
                <div class="text-center">
                    <div class="mb-4 glass-card rounded-lg p-4 inline-block">
                        <span class="text-lg font-medium text-white">المشاركون: </span>
                        <span id="currentParticipants" class="text-2xl font-bold text-yellow-300 pulse-animation">1</span>
                        <span class="text-lg text-white"> من </span>
                        <span id="totalParticipants" class="text-2xl font-bold text-white">5</span>
                    </div>
                    
                    <div id="participantsList" class="mb-6">
                        <div class="glass-card rounded-lg p-3 mb-2">
                            <span class="text-green-300">✓ <span id="creatorName"></span> (أنت)</span>
                        </div>
                    </div>
                    
                    <button id="startChallengeBtn" onclick="startQuiz()" disabled
                            class="w-full modern-btn py-4 disabled:bg-gray-400 disabled:cursor-not-allowed">
                        انتظار المشاركين...
                    </button>
                </div>
            </div>
        </div>

        <!-- Quiz Screen -->
        <div id="quizScreen" class="hidden max-w-4xl mx-auto">
            <!-- Quiz Header -->
            <div class="card-hover rounded-xl shadow-lg p-6 mb-6">
                <div class="flex justify-between items-center">
                    <div class="flex items-center space-x-4 space-x-reverse">
                        <div class="text-2xl pulse-animation">⏱️</div>
                        <div>
                            <div class="text-sm text-gray-600">الوقت المتبقي</div>
                            <div id="timer" class="text-xl font-bold text-red-600">15:00</div>
                        </div>
                    </div>
                    
                    <div class="text-center">
                        <div class="text-sm text-gray-600">السؤال</div>
                        <div class="text-xl font-bold title-gradient">
                            <span id="currentQuestion">1</span> من <span id="totalQuestions">10</span>
                        </div>
                    </div>
                    
                    <div id="groupInfo" class="hidden text-center">
                        <div class="text-sm text-gray-600">المشاركون</div>
                        <div class="text-xl font-bold text-blue-600">
                            <span id="quizParticipants">5</span> من <span id="quizTotal">5</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Question Card -->
            <div class="question-card rounded-xl shadow-lg p-8 mb-6">
                <div class="mb-6">
                    <div class="flex items-center mb-4">
                        <span id="questionType" class="bg-blue-100 text-blue-800 px-3 py-1 rounded-full text-sm font-medium">كمي</span>
                        <span id="questionPoints" class="bg-green-100 text-green-800 px-3 py-1 rounded-full text-sm font-medium mr-2">5 نقاط</span>
                    </div>
                    <h3 id="questionText" class="text-xl font-medium text-gray-800 leading-relaxed">
                        إذا كان س + ص = 12 و س - ص = 4، فما قيمة س؟
                    </h3>
                </div>
                
                <div id="questionOptions" class="space-y-3">
                    <button class="option-btn w-full text-right p-4 border-2 border-gray-200 rounded-lg hover:border-blue-500 hover:bg-blue-50 transition-all duration-200" onclick="selectAnswer(0)">
                        أ) 8
                    </button>
                    <button class="option-btn w-full text-right p-4 border-2 border-gray-200 rounded-lg hover:border-blue-500 hover:bg-blue-50 transition-all duration-200" onclick="selectAnswer(1)">
                        ب) 6
                    </button>
                    <button class="option-btn w-full text-right p-4 border-2 border-gray-200 rounded-lg hover:border-blue-500 hover:bg-blue-50 transition-all duration-200" onclick="selectAnswer(2)">
                        ج) 4
                    </button>
                    <button class="option-btn w-full text-right p-4 border-2 border-gray-200 rounded-lg hover:border-blue-500 hover:bg-blue-50 transition-all duration-200" onclick="selectAnswer(3)">
                        د) 2
                    </button>
                </div>
            </div>

            <div class="flex justify-between">
                <button id="prevBtn" onclick="previousQuestion()" disabled
                        class="modern-btn disabled:bg-gray-300 disabled:text-gray-500 disabled:cursor-not-allowed px-6 py-3">
                    السؤال السابق
                </button>
                <button id="nextBtn" onclick="nextQuestion()" disabled
                        class="modern-btn disabled:bg-gray-400 disabled:cursor-not-allowed px-6 py-3">
                    السؤال التالي
                </button>
            </div>
        </div>

        <!-- Results Screen -->
        <div id="resultsScreen" class="hidden max-w-4xl mx-auto">
            <div class="card-hover rounded-xl shadow-lg p-8 float-animation">
                <div class="text-center mb-8">
                    <div id="resultIcon" class="text-6xl mb-4 pulse-animation">🎉</div>
                    <h2 class="text-3xl font-bold title-gradient mb-2">انتهى الاختبار!</h2>
                    <p class="text-gray-600">إليك نتائجك التفصيلية</p>
                </div>

                <!-- Score Summary -->
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="glass-card rounded-lg p-6 text-center float-animation" style="animation-delay: 0.1s;">
                        <div class="text-3xl font-bold text-green-400 pulse-animation" id="correctAnswers">8</div>
                        <div class="text-sm text-green-300">إجابات صحيحة</div>
                    </div>
                    <div class="glass-card rounded-lg p-6 text-center float-animation" style="animation-delay: 0.2s;">
                        <div class="text-3xl font-bold text-red-400 pulse-animation" id="wrongAnswers">2</div>
                        <div class="text-sm text-red-300">إجابات خاطئة</div>
                    </div>
                    <div class="glass-card rounded-lg p-6 text-center float-animation" style="animation-delay: 0.3s;">
                        <div class="text-3xl font-bold text-blue-400 pulse-animation" id="earnedPoints">40</div>
                        <div class="text-sm text-blue-300">النقاط المكتسبة</div>
                    </div>
                </div>

                <!-- Detailed Review -->
                <div class="mb-8">
                    <h3 class="text-xl font-bold text-gray-800 mb-4">مراجعة الأسئلة</h3>
                    <div id="questionReview" class="space-y-4">
                        <!-- Questions will be populated here -->
                    </div>
                </div>

                <!-- Action Buttons -->
                <div class="flex flex-wrap gap-4 justify-center">
                    <button onclick="printResults()" 
                            class="modern-btn px-6 py-3 bg-blue-600 hover:bg-blue-700">
                        طباعة النتيجة
                    </button>
                    <button onclick="startNewQuiz()" 
                            class="modern-btn px-6 py-3 bg-green-600 hover:bg-green-700">
                        اختبار جديد
                    </button>
                    <button onclick="goHome()" 
                            class="modern-btn px-6 py-3 bg-gray-600 hover:bg-gray-700">
                        الصفحة الرئيسية
                    </button>
                </div>
            </div>
        </div>
    </main>

    <!-- Footer -->
    <footer class="bg-gray-900/90 backdrop-filter backdrop-blur-lg text-white py-12 mt-16 border-t border-white/10">
        <div class="container mx-auto px-4">
            <div class="text-center">
                <div class="mb-8">
                    <h3 class="text-2xl font-bold title-gradient mb-2">منصة تدريب القدرات</h3>
                    <p class="text-lg font-medium text-white/80">تصميم أ.عبدالرحمن الثقفي</p>
                </div>
                <div class="flex justify-center items-center space-x-6 space-x-reverse">
                    <a href="https://x.com/a_a_althagafi?t=SKoq7PoEIK_sP9WabZ7QYA&s=09" target="_blank" rel="noopener noreferrer" 
                       class="social-icon" title="تويتر">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
                        </svg>
                    </a>
                    <a href="https://t.me/althagafi993" target="_blank" rel="noopener noreferrer" 
                       class="social-icon" title="تليجرام شخصي">
                        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/>
                        </svg>
                    </a>
                    <a href="https://t.me/Interact2030" target="_blank" rel="noopener noreferrer" 
                       class="social-icon" title="قناة التفاعل">
                        <img src="https://drive.google.com/uc?export=view&id=1_BVPZQkiTb-18UhvJrF4Z1Sy0u3O7iOv" alt="قناة التفاعل" />
                    </a>
                </div>
                <div class="mt-8 pt-6 border-t border-white/10">
                    <p class="text-sm text-white/60">
                        © 2024 منصة تدريب القدرات بالذكاء الاصطناعي - جميع الحقوق محفوظة
                    </p>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Global variables
        let currentUser = '';
        let currentMode = '';
        let currentQuestionType = '';
        let selectedQuestionCount = 10; // Default question count
        let currentQuestionIndex = 0;
        let userAnswers = [];
        let quizQuestions = [];
        let timerInterval;
        let timeLeft = 900; // 15 minutes
        let userPoints = {
            individual: parseInt(localStorage.getItem('individualPoints') || '0'),
            group: parseInt(localStorage.getItem('groupPoints') || '0')
        };
        let challengeData = {};

        // Questions database for Saudi Qudurat test
        const questionsDatabase = {
            // القسم اللفظي
            reading: [ // استيعاب المقروء
                {
                    question: "اقرأ النص التالي ثم أجب: 'التعليم هو أساس تقدم الأمم، فبه ترتقي الشعوب وتزدهر الحضارات. والمعلم هو حجر الزاوية في العملية التعليمية، فهو الذي يصنع الأجيال ويبني العقول.' ما الفكرة الرئيسية للنص؟",
                    options: ["أهمية المعلم في التعليم", "التعليم أساس تقدم الأمم", "ازدهار الحضارات", "العملية التعليمية"],
                    correct: 1,
                    explanation: "الفكرة الرئيسية تظهر في الجملة الأولى 'التعليم هو أساس تقدم الأمم'، وباقي الجمل تأتي كتفصيل وشرح لهذه الفكرة المحورية. الكاتب يبدأ بالفكرة العامة ثم يوضح دور المعلم كجزء من منظومة التعليم.",
                    points: 4,
                    type: "reading"
                },
                {
                    question: "اقرأ النص: 'الصبر مفتاح الفرج، وهو من أعظم الصفات التي يجب أن يتحلى بها الإنسان في مواجهة تحديات الحياة. فالصابر ينال مراده في النهاية.' ما المعنى المقصود بـ 'مفتاح الفرج'؟",
                    options: ["الصبر يفتح الأبواب المغلقة", "الصبر وسيلة لتحقيق الأهداف والخروج من الضيق", "الصبر يجلب السعادة", "الصبر صفة حميدة"],
                    correct: 1,
                    explanation: "التعبير المجازي 'مفتاح الفرج' يعني أن الصبر هو الوسيلة التي تؤدي إلى الخروج من الضيق وتحقيق المراد. الفرج هنا يعني الخلاص من المشاكل والوصول للهدف المنشود.",
                    points: 3,
                    type: "reading"
                },
                {
                    question: "من النص التالي: 'الكتاب خير جليس في الزمان، يحدثك بأخبار الماضي ويعلمك دروس الحاضر ويهيئك لمستقبل أفضل.' ما الغرض من هذا النص؟",
                    options: ["وصف الكتاب", "الحث على القراءة", "شرح فوائد الكتاب", "مقارنة الكتاب بالأصدقاء"],
                    correct: 1,
                    explanation: "الغرض الأساسي هو الحث على القراءة من خلال إبراز فوائد الكتاب وأهميته. الكاتب يستخدم التشبيه والوصف كوسائل إقناعية لتشجيع القارئ على المطالعة.",
                    points: 4,
                    type: "reading"
                }
            ],
            relation: [ // الارتباط والاختلاف
                {
                    question: "أي من الكلمات التالية لا تنتمي للمجموعة؟ (ذهب - فضة - نحاس - خشب)",
                    options: ["ذهب", "فضة", "نحاس", "خشب"],
                    correct: 3,
                    explanation: "الخشب هو المختلف لأنه مادة عضوية من أصل نباتي، بينما الذهب والفضة والنحاس معادن غير عضوية. جميع المعادن تتشارك في خصائص فيزيائية وكيميائية مشتركة كالتوصيل الكهربائي واللمعان المعدني.",
                    points: 3,
                    type: "relation"
                },
                {
                    question: "ما العلاقة بين (طبيب : مستشفى)؟",
                    options: ["معلم : مدرسة", "طالب : جامعة", "مريض : دواء", "سائق : طريق"],
                    correct: 0,
                    explanation: "العلاقة هي (مهنة : مكان العمل الأساسي). الطبيب يعمل في المستشفى كمكان عمله الرئيسي، والمعلم يعمل في المدرسة. باقي الخيارات لا تحمل نفس العلاقة: الطالب يدرس وليس يعمل، المريض يستخدم الدواء، والسائق يستخدم الطريق.",
                    points: 4,
                    type: "relation"
                },
                {
                    question: "أي من المجموعات التالية متجانسة؟",
                    options: ["قلم - كتاب - مسطرة - تفاحة", "أسد - نمر - فهد - ذئب", "سيارة - طائرة - قطار - دراجة", "شمس - قمر - نجم - غيمة"],
                    correct: 1,
                    explanation: "المجموعة الثانية (أسد - نمر - فهد - ذئب) هي الأكثر تجانساً لأنها جميعاً حيوانات مفترسة آكلة لحوم. المجموعات الأخرى تحتوي على عناصر مختلفة: الأولى تخلط أدوات مدرسية مع طعام، والثالثة تخلط وسائل نقل مختلفة، والرابعة تخلط أجرام سماوية مع ظاهرة جوية.",
                    points: 4,
                    type: "relation"
                },
                {
                    question: "ما الكلمة التي لا تنتمي للمجموعة؟ (سعيد - مسرور - فرح - حزين)",
                    options: ["سعيد", "مسرور", "فرح", "حزين"],
                    correct: 3,
                    explanation: "حزين هو المختلف لأنه يعبر عن مشاعر سلبية، بينما سعيد ومسرور وفرح جميعها تعبر عن مشاعر إيجابية وحالة من السرور والبهجة. هذا السؤال يقيس قدرة الطالب على تصنيف المفردات حسب المعنى والدلالة العاطفية.",
                    points: 3,
                    type: "relation"
                }
            ],
            context: [ // الخطأ السياقي
                {
                    question: "أي من الجمل التالية تحتوي على خطأ سياقي؟",
                    options: ["شربت الماء البارد في الصيف", "لبست المعطف الثقيل في الشتاء", "أشعلت النار لأطفئ العطش", "فتحت المظلة عند المطر"],
                    correct: 2,
                    explanation: "الجملة الثالثة تحتوي على خطأ سياقي واضح، فالنار لا تُطفئ العطش بل تزيده. العطش يُطفأ بالماء أو السوائل، وليس بالنار التي تسبب الجفاف والحرارة. هذا تناقض منطقي في السبب والنتيجة.",
                    points: 3,
                    type: "context"
                },
                {
                    question: "ما الجملة التي تحتوي على تناقض منطقي؟",
                    options: ["السيارة سريعة جداً", "الطائرة تطير في السماء", "السمك يسبح في الصحراء", "الطيور تغرد في الصباح"],
                    correct: 2,
                    explanation: "السمك لا يمكن أن يسبح في الصحراء لأنه يحتاج للماء للعيش والحركة. الصحراء بيئة جافة تفتقر للماء، مما يجعل وجود السمك فيها مستحيلاً بيولوجياً. هذا تناقض بين طبيعة الكائن الحي والبيئة المذكورة.",
                    points: 3,
                    type: "context"
                },
                {
                    question: "أي من العبارات التالية غير منطقية؟",
                    options: ["استخدم المصباح لإضاءة الغرفة المظلمة", "فتح النافذة ليدخل الهواء النقي", "أغلق عينيه ليرى بوضوح أكبر", "شرب الدواء ليتحسن من المرض"],
                    correct: 2,
                    explanation: "إغلاق العينين لا يساعد على الرؤية بوضوح، بل يمنع الرؤية تماماً. الرؤية الواضحة تتطلب فتح العينين والإضاءة المناسبة. هذا تناقض واضح بين الفعل والهدف المرجو منه.",
                    points: 4,
                    type: "context"
                },
                {
                    question: "أي من الجمل التالية تحتوي على خطأ في التسلسل المنطقي؟",
                    options: ["زرع البذور ثم سقاها بالماء", "أشعل الفرن ثم وضع الطعام فيه", "ركب السيارة ثم أدار المحرك", "أكل الطعام ثم طبخه"],
                    correct: 3,
                    explanation: "الجملة الأخيرة تحتوي على خطأ في التسلسل الزمني المنطقي. الطبخ يجب أن يسبق الأكل وليس العكس. التسلسل الصحيح هو: طبخ الطعام ثم أكله. هذا خطأ في ترتيب الأحداث حسب السببية الطبيعية.",
                    points: 4,
                    type: "context"
                }
            ],
            analogy: [ // التناظر اللفظي
                {
                    question: "قلم : كتابة = ؟",
                    options: ["سيارة : قيادة", "مفتاح : باب", "طعام : جوع", "نوم : تعب"],
                    correct: 0,
                    explanation: "العلاقة هي (أداة : وظيفة). القلم أداة تُستخدم للكتابة، والسيارة أداة تُستخدم للقيادة. كلاهما يمثل وسيلة لتحقيق غرض معين. باقي الخيارات لا تحمل نفس العلاقة المنطقية.",
                    points: 4,
                    type: "analogy"
                },
                {
                    question: "شمس : نهار = قمر : ؟",
                    options: ["ليل", "نجوم", "ظلام", "سماء"],
                    correct: 0,
                    explanation: "العلاقة هي (جرم سماوي : الوقت المرتبط به). الشمس تظهر وتضيء في النهار، والقمر يظهر ويضيء في الليل. هذا تناظر زمني طبيعي بين الأجرام السماوية وأوقات ظهورها.",
                    points: 3,
                    type: "analogy"
                },
                {
                    question: "طبيب : مرض = ؟",
                    options: ["معلم : جهل", "مهندس : بناء", "طباخ : جوع", "سائق : سيارة"],
                    correct: 0,
                    explanation: "العلاقة هي (مهنة : ما تحاربه أو تعالجه). الطبيب يحارب المرض ويعالجه، والمعلم يحارب الجهل ويعالجه بالتعليم. كلاهما يسعى للقضاء على مشكلة معينة من خلال تخصصه.",
                    points: 4,
                    type: "analogy"
                },
                {
                    question: "كتاب : مكتبة = ؟",
                    options: ["سيارة : مرآب", "طائر : قفص", "سمك : بحر", "زهرة : حديقة"],
                    correct: 3,
                    explanation: "العلاقة هي (جزء : مكان تجمعه الطبيعي). الكتاب يُحفظ في المكتبة كمكان مخصص لتجميع الكتب، والزهرة تنمو في الحديقة كمكان طبيعي لتجمع الزهور. العلاقة تدل على الانتماء والتجمع المنظم.",
                    points: 4,
                    type: "analogy"
                },
                {
                    question: "ماء : عطش = ؟",
                    options: ["طعام : جوع", "دواء : صحة", "نوم : أحلام", "نار : دخان"],
                    correct: 0,
                    explanation: "العلاقة هي (حاجة : ما يشبعها). الماء يشبع العطش ويزيله، والطعام يشبع الجوع ويزيله. كلاهما يمثل إشباع حاجة أساسية للإنسان وإزالة الشعور بالنقص.",
                    points: 3,
                    type: "analogy"
                }
            ],
            completion: [ // إكمال الجمل
                {
                    question: "المطالعة غذاء _____ كما أن الطعام غذاء _____",
                    options: ["العقل - الجسم", "الروح - النفس", "الفكر - الذهن", "الذاكرة - العضلات"],
                    correct: 0,
                    explanation: "هذا تشبيه بليغ يوضح أن المطالعة تغذي العقل وتنميه بالمعرفة والثقافة، تماماً كما يغذي الطعام الجسم ويقويه. العلاقة متوازية ومنطقية بين التغذية الفكرية والتغذية الجسدية.",
                    points: 4,
                    type: "completion"
                },
                {
                    question: "لا يمكن للإنسان أن _____ دون أن _____",
                    options: ["ينجح - يجتهد", "يأكل - يشرب", "يسافر - يعود", "يحلم - ينام"],
                    correct: 0,
                    explanation: "هذا مبدأ السببية في النجاح. النجاح نتيجة طبيعية للاجتهاد والعمل الجاد، فلا يمكن تحقيق النجاح دون بذل الجهد المطلوب. العلاقة سببية منطقية بين الوسيلة والنتيجة.",
                    points: 3,
                    type: "completion"
                },
                {
                    question: "الصبر _____ والعجلة _____ ",
                    options: ["مفتاح الفرج - مفتاح الندم", "صفة حميدة - صفة ذميمة", "من الإيمان - من الشيطان", "يؤدي للنجاح - تؤدي للفشل"],
                    correct: 0,
                    explanation: "هذا تضاد بلاغي يوضح الفرق بين نتائج الصبر والعجلة. الصبر يؤدي إلى الفرج والخير، بينما العجلة تؤدي إلى الندم والأخطاء. التعبير يستخدم الاستعارة (مفتاح) ليوضح أن كلاً منهما وسيلة لنتيجة مختلفة.",
                    points: 4,
                    type: "completion"
                },
                {
                    question: "كلما ازداد _____ الإنسان، قل _____ ",
                    options: ["علم - جهله", "غرور - تواضعه", "مال - سعادته", "عمر - حكمته"],
                    correct: 0,
                    explanation: "هذه علاقة عكسية طبيعية بين العلم والجهل. كلما تعلم الإنسان أكثر وازدادت معرفته، قل جهله وانحسرت مناطق عدم المعرفة لديه. العلم والجهل متضادان لا يجتمعان في نفس المجال.",
                    points: 3,
                    type: "completion"
                },
                {
                    question: "من _____ زرع ومن _____ حصد",
                    options: ["جد - صبر", "اجتهد - ثابر", "سعى - عمل", "زرع - حصد"],
                    correct: 0,
                    explanation: "هذا مثل يوضح مبدأ الجهد والمثابرة. من جدّ واجتهد في عمله فإنه يزرع بذور النجاح، ومن صبر وثابر على جهده فإنه يحصد ثمار عمله. العلاقة تدل على التدرج الطبيعي من الجهد إلى النتيجة.",
                    points: 4,
                    type: "completion"
                }
            ],
            
            // القسم الكمي
            statistics: [ // تحليل وإحصاء
                {
                    question: "إذا كانت درجات 5 طلاب في اختبار هي: 80، 85، 90، 75، 95. ما المتوسط الحسابي؟",
                    options: ["85", "87", "83", "90"],
                    correct: 0,
                    explanation: "المتوسط الحسابي = مجموع القيم ÷ عددها\nالمتوسط = (80+85+90+75+95)÷5 = 425÷5 = 85\nالمتوسط الحسابي يعطي فكرة عن القيمة المركزية للبيانات.",
                    points: 4,
                    type: "statistics"
                },
                {
                    question: "في مجموعة البيانات: 10، 15، 20، 25، 30. ما الوسيط؟",
                    options: ["20", "15", "25", "18"],
                    correct: 0,
                    explanation: "الوسيط هو القيمة الوسطى عند ترتيب البيانات تصاعدياً أو تنازلياً. البيانات مرتبة: 10، 15، 20، 25، 30. القيمة الوسطى (الثالثة من أصل 5) هي 20.",
                    points: 3,
                    type: "statistics"
                },
                {
                    question: "إذا كان المتوسط الحسابي لـ 4 أعداد هو 15، فما مجموع هذه الأعداد؟",
                    options: ["60", "45", "75", "30"],
                    correct: 0,
                    explanation: "المتوسط الحسابي = مجموع القيم ÷ عددها\n15 = مجموع القيم ÷ 4\nمجموع القيم = 15 × 4 = 60",
                    points: 3,
                    type: "statistics"
                },
                {
                    question: "في الجدول التالي يوضح عدد الكتب المقروءة:\n5 طلاب قرأوا كتاباً واحداً\n3 طلاب قرأوا كتابين\n2 طلاب قرأوا 3 كتب\nما المنوال؟",
                    options: ["كتاب واحد", "كتابان", "3 كتب", "لا يوجد منوال"],
                    correct: 0,
                    explanation: "المنوال هو القيمة الأكثر تكراراً في البيانات. كتاب واحد تكرر 5 مرات، كتابان تكرر 3 مرات، و3 كتب تكرر مرتين. إذن المنوال هو كتاب واحد.",
                    points: 4,
                    type: "statistics"
                },
                {
                    question: "إذا كانت النسبة المئوية للنجاح في مدرسة 80%، وعدد الطلاب الناجحين 240 طالباً، فما العدد الكلي للطلاب؟",
                    options: ["300", "320", "280", "360"],
                    correct: 0,
                    explanation: "النسبة المئوية = (عدد الناجحين ÷ العدد الكلي) × 100\n80% = (240 ÷ العدد الكلي) × 100\n0.8 = 240 ÷ العدد الكلي\nالعدد الكلي = 240 ÷ 0.8 = 300 طالب",
                    points: 4,
                    type: "statistics"
                }
            ],
            geometry: [ // هندسة
                {
                    question: "إذا كان محيط المربع 24 سم، فما مساحته؟",
                    options: ["36 سم²", "24 سم²", "144 سم²", "48 سم²"],
                    correct: 0,
                    explanation: "محيط المربع = 4 × طول الضلع\n24 = 4 × طول الضلع\nطول الضلع = 24÷4 = 6 سم\nمساحة المربع = (طول الضلع)² = 6² = 36 سم²",
                    points: 4,
                    type: "geometry"
                },
                {
                    question: "مثلث قائم الزاوية، طولا ضلعيه القائمين 3 سم و 4 سم. ما طول الوتر؟",
                    options: ["5 سم", "7 سم", "6 سم", "8 سم"],
                    correct: 0,
                    explanation: "باستخدام نظرية فيثاغورس: (الوتر)² = (الضلع الأول)² + (الضلع الثاني)²\n(الوتر)² = 3² + 4² = 9 + 16 = 25\nالوتر = √25 = 5 سم",
                    points: 5,
                    type: "geometry"
                },
                {
                    question: "دائرة نصف قطرها 7 سم، ما محيطها؟ (استخدم π = 22/7)",
                    options: ["44 سم", "154 سم", "22 سم", "49 سم"],
                    correct: 0,
                    explanation: "محيط الدائرة = 2πr\nمحيط الدائرة = 2 × (22/7) × 7 = 2 × 22 = 44 سم",
                    points: 4,
                    type: "geometry"
                },
                {
                    question: "مستطيل طوله 12 سم وعرضه 8 سم، ما مساحته؟",
                    options: ["96 سم²", "40 سم²", "20 سم²", "48 سم²"],
                    correct: 0,
                    explanation: "مساحة المستطيل = الطول × العرض\nالمساحة = 12 × 8 = 96 سم²",
                    points: 3,
                    type: "geometry"
                }
            ],
            algebra: [ // جبر
                {
                    question: "إذا كان 2س + 5 = 13، فما قيمة س؟",
                    options: ["4", "3", "5", "6"],
                    correct: 0,
                    explanation: "2س + 5 = 13\n2س = 13 - 5\n2س = 8\nس = 8÷2 = 4",
                    points: 3,
                    type: "algebra"
                },
                {
                    question: "إذا كان س² = 49، فما قيمة س؟",
                    options: ["±7", "7", "-7", "49"],
                    correct: 0,
                    explanation: "س² = 49\nس = ±√49 = ±7\nالجذر التربيعي لأي عدد موجب له قيمتان: موجبة وسالبة",
                    points: 4,
                    type: "algebra"
                },
                {
                    question: "إذا كان 3س - 7 = 2س + 5، فما قيمة س؟",
                    options: ["12", "8", "10", "6"],
                    correct: 0,
                    explanation: "3س - 7 = 2س + 5\n3س - 2س = 5 + 7\nس = 12",
                    points: 4,
                    type: "algebra"
                },
                {
                    question: "إذا كان س + ص = 10 و س - ص = 4، فما قيمة س؟",
                    options: ["7", "6", "8", "3"],
                    correct: 0,
                    explanation: "س + ص = 10 ... (1)\nس - ص = 4 ... (2)\nبجمع المعادلتين: 2س = 14\nس = 7",
                    points: 5,
                    type: "algebra"
                }
            ],
            arithmetic: [ // حساب
                {
                    question: "ما ناتج 15% من 200؟",
                    options: ["30", "25", "35", "20"],
                    correct: 0,
                    explanation: "15% من 200 = (15÷100) × 200 = 0.15 × 200 = 30\nأو يمكن حسابها: (15 × 200) ÷ 100 = 3000 ÷ 100 = 30",
                    points: 3,
                    type: "arithmetic"
                },
                {
                    question: "إذا اشترى أحمد 3 كتب بـ 45 ريال، فكم سعر الكتاب الواحد؟",
                    options: ["15 ريال", "12 ريال", "18 ريال", "20 ريال"],
                    correct: 0,
                    explanation: "سعر الكتاب الواحد = إجمالي السعر ÷ عدد الكتب\nسعر الكتاب الواحد = 45 ÷ 3 = 15 ريال",
                    points: 2,
                    type: "arithmetic"
                },
                {
                    question: "ما ناتج: 2.5 × 4 + 3 × 2؟",
                    options: ["16", "14", "18", "12"],
                    correct: 0,
                    explanation: "نطبق ترتيب العمليات (الضرب قبل الجمع):\n2.5 × 4 = 10\n3 × 2 = 6\n10 + 6 = 16",
                    points: 3,
                    type: "arithmetic"
                },
                {
                    question: "إذا كان سعر السلعة 80 ريال وعليها خصم 25%، فما السعر بعد الخصم؟",
                    options: ["60 ريال", "55 ريال", "65 ريال", "70 ريال"],
                    correct: 0,
                    explanation: "قيمة الخصم = 25% من 80 = 0.25 × 80 = 20 ريال\nالسعر بعد الخصم = 80 - 20 = 60 ريال",
                    points: 4,
                    type: "arithmetic"
                }
            ],
            comparison: [ // مقارنة
                {
                    question: "قارن بين القيمتين:\nالقيمة الأولى: 3² + 4²\nالقيمة الثانية: 5²",
                    options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                    correct: 2,
                    explanation: "القيمة الأولى: 3² + 4² = 9 + 16 = 25\nالقيمة الثانية: 5² = 25\nإذن القيمتان متساويتان (25 = 25). هذا مثال على نظرية فيثاغورس حيث مربع الوتر يساوي مجموع مربعي الضلعين الآخرين.",
                    points: 4,
                    type: "comparison"
                },
                {
                    question: "قارن بين القيمتين:\nالقيمة الأولى: 2/3\nالقيمة الثانية: 0.65",
                    options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                    correct: 0,
                    explanation: "القيمة الأولى: 2/3 = 0.666...\nالقيمة الثانية: 0.65\nبما أن 0.666... > 0.65، فإن القيمة الأولى أكبر من الثانية.",
                    points: 3,
                    type: "comparison"
                },
                {
                    question: "قارن بين القيمتين:\nالقيمة الأولى: √16 + √9\nالقيمة الثانية: √25",
                    options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                    correct: 0,
                    explanation: "القيمة الأولى: √16 + √9 = 4 + 3 = 7\nالقيمة الثانية: √25 = 5\nبما أن 7 > 5، فإن القيمة الأولى أكبر من الثانية.",
                    points: 4,
                    type: "comparison"
                },
                {
                    question: "قارن بين القيمتين:\nالقيمة الأولى: 15% من 200\nالقيمة الثانية: 25% من 120",
                    options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                    correct: 2,
                    explanation: "القيمة الأولى: 15% من 200 = 0.15 × 200 = 30\nالقيمة الثانية: 25% من 120 = 0.25 × 120 = 30\nإذن القيمتان متساويتان (30 = 30).",
                    points: 3,
                    type: "comparison"
                },
                {
                    question: "قارن بين القيمتين:\nالقيمة الأولى: س + 3 (حيث س > 5)\nالقيمة الثانية: 8",
                    options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                    correct: 0,
                    explanation: "بما أن س > 5، فإن س + 3 > 5 + 3 = 8\nإذن القيمة الأولى (س + 3) أكبر من القيمة الثانية (8) في جميع الحالات الممكنة.",
                    points: 4,
                    type: "comparison"
                }
            ]
        };

        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            updatePointsDisplay();
        });

        // Registration form handler
        document.getElementById('registrationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('studentName').value.trim();
            if (name) {
                currentUser = name;
                document.getElementById('registrationScreen').classList.add('hidden');
                document.getElementById('modeSelectionScreen').classList.remove('hidden');
                document.getElementById('userPoints').classList.remove('hidden');
            }
        });

        // Mode selection
        function selectMode(mode) {
            currentMode = mode;
            document.getElementById('modeSelectionScreen').classList.add('hidden');
            document.getElementById('questionTypeScreen').classList.remove('hidden');
            
            // Add event listeners for question count inputs
            addQuestionCountListeners();
        }

        // Add event listeners for question count inputs
        function addQuestionCountListeners() {
            const inputs = [
                'reading-count', 'relation-count', 'context-count', 'analogy-count', 'completion-count',
                'statistics-count', 'geometry-count', 'algebra-count', 'arithmetic-count', 'comparison-count'
            ];
            
            inputs.forEach(inputId => {
                const input = document.getElementById(inputId);
                if (input) {
                    input.addEventListener('input', updateTotalQuestions);
                }
            });
        }

        // Update total questions count
        function updateTotalQuestions() {
            const inputs = [
                'reading-count', 'relation-count', 'context-count', 'analogy-count', 'completion-count',
                'statistics-count', 'geometry-count', 'algebra-count', 'arithmetic-count', 'comparison-count'
            ];
            
            let total = 0;
            inputs.forEach(inputId => {
                const input = document.getElementById(inputId);
                if (input) {
                    total += parseInt(input.value) || 0;
                }
            });
            
            document.getElementById('totalSelectedQuestions').textContent = total;
            
            // Enable/disable proceed button
            const proceedBtn = document.getElementById('proceedBtn');
            if (total > 0) {
                proceedBtn.disabled = false;
                proceedBtn.className = 'modern-btn py-4 px-12 text-lg';
            } else {
                proceedBtn.disabled = true;
                proceedBtn.className = 'modern-btn py-4 px-12 text-lg disabled:bg-gray-400 disabled:cursor-not-allowed';
            }
        }

        // Quick selection functions
        function setQuickSelection(type) {
            // Clear all inputs first
            clearAllSelections();
            
            if (type === 'verbal') {
                document.getElementById('reading-count').value = 4;
                document.getElementById('relation-count').value = 4;
                document.getElementById('context-count').value = 4;
                document.getElementById('analogy-count').value = 4;
                document.getElementById('completion-count').value = 4;
            } else if (type === 'quantitative') {
                document.getElementById('statistics-count').value = 4;
                document.getElementById('geometry-count').value = 4;
                document.getElementById('algebra-count').value = 4;
                document.getElementById('arithmetic-count').value = 4;
                document.getElementById('comparison-count').value = 4;
            } else if (type === 'balanced') {
                document.getElementById('reading-count').value = 3;
                document.getElementById('relation-count').value = 3;
                document.getElementById('context-count').value = 3;
                document.getElementById('analogy-count').value = 3;
                document.getElementById('completion-count').value = 3;
                document.getElementById('statistics-count').value = 3;
                document.getElementById('geometry-count').value = 3;
                document.getElementById('algebra-count').value = 3;
                document.getElementById('arithmetic-count').value = 3;
                document.getElementById('comparison-count').value = 3;
            } else if (type === 'full') {
                document.getElementById('reading-count').value = 5;
                document.getElementById('relation-count').value = 5;
                document.getElementById('context-count').value = 5;
                document.getElementById('analogy-count').value = 5;
                document.getElementById('completion-count').value = 5;
                document.getElementById('statistics-count').value = 5;
                document.getElementById('geometry-count').value = 5;
                document.getElementById('algebra-count').value = 5;
                document.getElementById('arithmetic-count').value = 5;
                document.getElementById('comparison-count').value = 5;
            }
            
            updateTotalQuestions();
        }

        function clearAllSelections() {
            const inputs = [
                'reading-count', 'relation-count', 'context-count', 'analogy-count', 'completion-count',
                'statistics-count', 'geometry-count', 'algebra-count', 'arithmetic-count', 'comparison-count'
            ];
            
            inputs.forEach(inputId => {
                const input = document.getElementById(inputId);
                if (input) {
                    input.value = 0;
                }
            });
            
            updateTotalQuestions();
        }

        // Proceed with selected questions
        function proceedWithSelectedQuestions() {
            const questionCounts = {
                reading: parseInt(document.getElementById('reading-count').value) || 0,
                relation: parseInt(document.getElementById('relation-count').value) || 0,
                context: parseInt(document.getElementById('context-count').value) || 0,
                analogy: parseInt(document.getElementById('analogy-count').value) || 0,
                completion: parseInt(document.getElementById('completion-count').value) || 0,
                statistics: parseInt(document.getElementById('statistics-count').value) || 0,
                geometry: parseInt(document.getElementById('geometry-count').value) || 0,
                algebra: parseInt(document.getElementById('algebra-count').value) || 0,
                arithmetic: parseInt(document.getElementById('arithmetic-count').value) || 0,
                comparison: parseInt(document.getElementById('comparison-count').value) || 0
            };
            
            // Store question counts globally
            window.selectedQuestionCounts = questionCounts;
            
            // Calculate total
            selectedQuestionCount = Object.values(questionCounts).reduce((sum, count) => sum + count, 0);
            
            if (selectedQuestionCount === 0) {
                alert('يرجى اختيار عدد أسئلة أكبر من صفر');
                return;
            }
            
            document.getElementById('questionTypeScreen').classList.add('hidden');
            
            if (currentMode === 'group') {
                document.getElementById('groupSizeScreen').classList.remove('hidden');
            } else {
                startQuiz();
            }
        }



        // Create group challenge
        function createGroupChallenge() {
            const participantCount = parseInt(document.getElementById('participantCount').value);
            if (participantCount < 2 || participantCount > 50) {
                alert('عدد المشاركين يجب أن يكون بين 2 و 50');
                return;
            }

            // Generate unique challenge ID
            const challengeId = 'challenge_' + Date.now();
            challengeData = {
                id: challengeId,
                creator: currentUser,
                maxParticipants: participantCount,
                currentParticipants: 1,
                participants: [currentUser],
                questionType: currentQuestionType
            };

            // Store challenge data
            localStorage.setItem(challengeId, JSON.stringify(challengeData));

            // Show challenge link screen
            document.getElementById('groupSizeScreen').classList.add('hidden');
            document.getElementById('challengeLinkScreen').classList.remove('hidden');
            
            // Update UI
            document.getElementById('challengeLink').textContent = `${window.location.origin}${window.location.pathname}?challenge=${challengeId}`;
            document.getElementById('totalParticipants').textContent = participantCount;
            document.getElementById('creatorName').textContent = currentUser;
            
            // Simulate participants joining (for demo)
            simulateParticipants();
        }

        // Simulate participants joining (for demo purposes)
        function simulateParticipants() {
            const names = ['أحمد محمد', 'فاطمة علي', 'خالد سعد', 'نورا حسن', 'عبدالله يوسف'];
            let joinedCount = 1;
            
            const joinInterval = setInterval(() => {
                if (joinedCount < challengeData.maxParticipants && joinedCount < 5) {
                    const newParticipant = names[joinedCount - 1];
                    challengeData.participants.push(newParticipant);
                    challengeData.currentParticipants++;
                    
                    // Add participant to list
                    const participantsList = document.getElementById('participantsList');
                    const participantDiv = document.createElement('div');
                    participantDiv.className = 'bg-green-50 rounded-lg p-3 mb-2';
                    participantDiv.innerHTML = `<span class="text-green-700">✓ ${newParticipant}</span>`;
                    participantsList.appendChild(participantDiv);
                    
                    // Update counter
                    document.getElementById('currentParticipants').textContent = challengeData.currentParticipants;
                    
                    joinedCount++;
                    
                    // Enable start button when enough participants
                    if (challengeData.currentParticipants >= 2) {
                        const startBtn = document.getElementById('startChallengeBtn');
                        startBtn.disabled = false;
                        startBtn.className = 'w-full bg-gradient-to-r from-green-600 to-blue-600 text-white py-3 px-6 rounded-lg font-medium hover:from-green-700 hover:to-blue-700 transition-all duration-300';
                        startBtn.textContent = 'بدء التحدي';
                    }
                } else {
                    clearInterval(joinInterval);
                }
            }, 2000);
        }

        // Copy challenge link
        function copyLink() {
            const link = document.getElementById('challengeLink').textContent;
            navigator.clipboard.writeText(link).then(() => {
                // Show success message
                const button = event.target;
                const originalText = button.textContent;
                button.textContent = 'تم النسخ!';
                button.className = 'bg-green-600 text-white px-4 py-2 rounded-lg text-sm';
                setTimeout(() => {
                    button.textContent = originalText;
                    button.className = 'bg-blue-600 text-white px-4 py-2 rounded-lg text-sm hover:bg-blue-700 transition-colors';
                }, 2000);
            });
        }

        // Start quiz
        function startQuiz() {
            // Hide all screens
            document.querySelectorAll('[id$="Screen"]').forEach(screen => {
                screen.classList.add('hidden');
            });
            
            // Show quiz screen
            document.getElementById('quizScreen').classList.remove('hidden');
            
            // Show group info if group mode
            if (currentMode === 'group') {
                document.getElementById('groupInfo').classList.remove('hidden');
                document.getElementById('quizParticipants').textContent = challengeData.currentParticipants;
                document.getElementById('quizTotal').textContent = challengeData.maxParticipants;
            }
            
            // Generate questions
            generateQuestions();
            
            // Start timer
            startTimer();
            
            // Show first question
            showQuestion(0);
        }

        // Generate questions based on selected types and counts
        function generateQuestions() {
            quizQuestions = [];
            const questionCounts = window.selectedQuestionCounts || {};
            
            // Generate questions for each type
            Object.keys(questionCounts).forEach(type => {
                const count = questionCounts[type];
                if (count > 0 && questionsDatabase[type]) {
                    let typeQuestions = [...questionsDatabase[type]];
                    
                    // Shuffle questions first to ensure randomness
                    typeQuestions = typeQuestions.sort(() => Math.random() - 0.5);
                    
                    // If we need more questions than available, we'll cycle through them
                    // but ensure no immediate repetition in the same quiz
                    let selectedQuestions = [];
                    for (let i = 0; i < count; i++) {
                        selectedQuestions.push(typeQuestions[i % typeQuestions.length]);
                    }
                    
                    // Add unique identifier to prevent exact duplicates in same quiz
                    selectedQuestions = selectedQuestions.map((q, index) => ({
                        ...q,
                        uniqueId: `${type}_${index}_${Date.now()}`
                    }));
                    
                    quizQuestions.push(...selectedQuestions);
                }
            });
            
            // Shuffle all questions to mix different types
            quizQuestions = quizQuestions.sort(() => Math.random() - 0.5);
            
            // Remove any potential duplicates based on question text
            const uniqueQuestions = [];
            const seenQuestions = new Set();
            
            quizQuestions.forEach(question => {
                if (!seenQuestions.has(question.question)) {
                    seenQuestions.add(question.question);
                    uniqueQuestions.push(question);
                }
            });
            
            quizQuestions = uniqueQuestions;
            
            // Initialize user answers
            userAnswers = new Array(quizQuestions.length).fill(-1);
            
            // Update total questions display
            document.getElementById('totalQuestions').textContent = quizQuestions.length;
            
            // Adjust timer based on question count (1.5 minutes per question)
            timeLeft = quizQuestions.length * 90;
        }

        // Show question
        function showQuestion(index) {
            const question = quizQuestions[index];
            
            // Update question info
            document.getElementById('currentQuestion').textContent = index + 1;
            document.getElementById('questionText').textContent = question.question;
            document.getElementById('questionPoints').textContent = `${question.points} نقاط`;
            
            // Set question type badge based on question type
            const typeMap = {
                'reading': '📖 استيعاب المقروء',
                'relation': '🔗 ارتباط واختلاف',
                'context': '❌ خطأ سياقي',
                'analogy': '⚖️ تناظر لفظي',
                'completion': '✏️ إكمال جمل',
                'statistics': '📊 تحليل وإحصاء',
                'geometry': '📐 هندسة',
                'algebra': '🧮 جبر',
                'arithmetic': '🔢 حساب',
                'comparison': '⚖️ مقارنة'
            };
            
            const questionTypeText = typeMap[question.type] || 'سؤال عام';
            document.getElementById('questionType').textContent = questionTypeText;
            
            // Update options
            const optionsContainer = document.getElementById('questionOptions');
            optionsContainer.innerHTML = '';
            
            question.options.forEach((option, i) => {
                const button = document.createElement('button');
                button.className = 'option-btn w-full text-right p-4 border-2 border-gray-200 rounded-lg hover:border-blue-500 hover:bg-blue-50 transition-all duration-200';
                button.textContent = `${String.fromCharCode(65 + i)}) ${option}`;
                button.onclick = () => selectAnswer(i);
                
                // Highlight if already selected
                if (userAnswers[index] === i) {
                    button.className += ' border-blue-500 bg-blue-50';
                }
                
                optionsContainer.appendChild(button);
            });
            
            // Update navigation buttons
            document.getElementById('prevBtn').disabled = index === 0;
            document.getElementById('prevBtn').className = index === 0 ? 
                'bg-gray-300 text-gray-500 px-6 py-3 rounded-lg font-medium cursor-not-allowed' :
                'bg-blue-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-blue-700 transition-colors';
            
            const isLastQuestion = index === quizQuestions.length - 1;
            const nextBtn = document.getElementById('nextBtn');
            nextBtn.textContent = isLastQuestion ? 'إنهاء الاختبار' : 'السؤال التالي';
            nextBtn.disabled = userAnswers[index] === -1;
            nextBtn.className = userAnswers[index] === -1 ?
                'bg-gray-400 text-white px-6 py-3 rounded-lg font-medium cursor-not-allowed' :
                (isLastQuestion ? 'bg-red-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-red-700 transition-colors' :
                'bg-blue-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-blue-700 transition-colors');
        }

        // Select answer
        function selectAnswer(answerIndex) {
            userAnswers[currentQuestionIndex] = answerIndex;
            
            // Update option buttons
            const optionBtns = document.querySelectorAll('.option-btn');
            optionBtns.forEach((btn, i) => {
                if (i === answerIndex) {
                    btn.className = 'option-btn w-full text-right p-4 border-2 border-blue-500 bg-blue-50 rounded-lg transition-all duration-200';
                } else {
                    btn.className = 'option-btn w-full text-right p-4 border-2 border-gray-200 rounded-lg hover:border-blue-500 hover:bg-blue-50 transition-all duration-200';
                }
            });
            
            // Enable next button
            const nextBtn = document.getElementById('nextBtn');
            const isLastQuestion = currentQuestionIndex === quizQuestions.length - 1;
            nextBtn.disabled = false;
            nextBtn.className = isLastQuestion ? 
                'bg-red-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-red-700 transition-colors' :
                'bg-blue-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-blue-700 transition-colors';
        }

        // Navigation functions
        function previousQuestion() {
            if (currentQuestionIndex > 0) {
                currentQuestionIndex--;
                showQuestion(currentQuestionIndex);
            }
        }

        function nextQuestion() {
            if (currentQuestionIndex < quizQuestions.length - 1) {
                currentQuestionIndex++;
                showQuestion(currentQuestionIndex);
            } else {
                finishQuiz();
            }
        }

        // Timer functions
        function startTimer() {
            timerInterval = setInterval(() => {
                timeLeft--;
                updateTimerDisplay();
                
                if (timeLeft <= 0) {
                    finishQuiz();
                }
            }, 1000);
        }

        function updateTimerDisplay() {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            document.getElementById('timer').textContent = 
                `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }

        // Finish quiz
        function finishQuiz() {
            clearInterval(timerInterval);
            
            // Calculate results
            let correctCount = 0;
            let totalPoints = 0;
            
            quizQuestions.forEach((question, index) => {
                if (userAnswers[index] === question.correct) {
                    correctCount++;
                    totalPoints += question.points;
                }
            });
            
            // Update points
            if (currentMode === 'individual') {
                userPoints.individual += totalPoints;
                localStorage.setItem('individualPoints', userPoints.individual.toString());
            } else {
                userPoints.group += totalPoints;
                localStorage.setItem('groupPoints', userPoints.group.toString());
            }
            
            updatePointsDisplay();
            
            // Show results
            showResults(correctCount, quizQuestions.length - correctCount, totalPoints);
        }

        // Show results
        function showResults(correct, wrong, points) {
            document.getElementById('quizScreen').classList.add('hidden');
            document.getElementById('resultsScreen').classList.remove('hidden');
            
            // Update result summary
            document.getElementById('correctAnswers').textContent = correct;
            document.getElementById('wrongAnswers').textContent = wrong;
            document.getElementById('earnedPoints').textContent = points;
            
            // Set result icon based on performance
            const percentage = (correct / quizQuestions.length) * 100;
            const resultIcon = document.getElementById('resultIcon');
            if (percentage >= 80) {
                resultIcon.textContent = '🏆';
            } else if (percentage >= 60) {
                resultIcon.textContent = '🎉';
            } else {
                resultIcon.textContent = '📚';
            }
            
            // Generate detailed review
            generateQuestionReview();
        }

        // Generate question review
        function generateQuestionReview() {
            const reviewContainer = document.getElementById('questionReview');
            reviewContainer.innerHTML = '';
            
            quizQuestions.forEach((question, index) => {
                const isCorrect = userAnswers[index] === question.correct;
                const userAnswer = userAnswers[index];
                
                const reviewDiv = document.createElement('div');
                reviewDiv.className = `border rounded-lg p-4 ${isCorrect ? 'border-green-300 bg-green-50' : 'border-red-300 bg-red-50'}`;
                
                reviewDiv.innerHTML = `
                    <div class="flex items-start justify-between mb-3">
                        <div class="flex-1">
                            <h4 class="font-medium text-gray-800 mb-2">السؤال ${index + 1}: ${question.question}</h4>
                            <div class="text-sm space-y-1">
                                <div class="flex items-center">
                                    <span class="font-medium ml-2">إجابتك:</span>
                                    <span class="${isCorrect ? 'text-green-700' : 'text-red-700'}">
                                        ${userAnswer >= 0 ? question.options[userAnswer] : 'لم تجب'}
                                    </span>
                                    <span class="mr-2">${isCorrect ? '✓' : '✗'}</span>
                                </div>
                                ${!isCorrect ? `
                                <div class="flex items-center">
                                    <span class="font-medium ml-2">الإجابة الصحيحة:</span>
                                    <span class="text-green-700">${question.options[question.correct]}</span>
                                </div>
                                ` : ''}
                            </div>
                        </div>
                        <div class="text-2xl">${isCorrect ? '✅' : '❌'}</div>
                    </div>
                    
                    <div class="bg-white rounded-lg p-3 mb-3">
                        <div class="font-medium text-gray-700 mb-1">الشرح:</div>
                        <div class="text-gray-600 text-sm">${question.explanation}</div>
                    </div>
                    
                    <div class="flex items-center justify-between">
                        <div class="text-sm text-gray-600">
                            النقاط: ${isCorrect ? question.points : 0} من ${question.points}
                        </div>
                        <div class="text-sm font-medium ${isCorrect ? 'text-green-600' : 'text-red-600'}">
                            ${isCorrect ? '✅ إجابة صحيحة' : '❌ إجابة خاطئة'}
                        </div>
                    </div>
                `;
                
                reviewContainer.appendChild(reviewDiv);
            });
        }

        // Update points display
        function updatePointsDisplay() {
            document.getElementById('individualPoints').textContent = userPoints.individual;
            document.getElementById('groupPoints').textContent = userPoints.group;
        }

        // Print results
        function printResults() {
            const printWindow = window.open('', '_blank');
            const correct = parseInt(document.getElementById('correctAnswers').textContent);
            const wrong = parseInt(document.getElementById('wrongAnswers').textContent);
            const points = parseInt(document.getElementById('earnedPoints').textContent);
            
            printWindow.document.write(`
                <!DOCTYPE html>
                <html lang="ar" dir="rtl">
                <head>
                    <meta charset="UTF-8">
                    <title>نتيجة اختبار القدرات</title>
                    <style>
                        body { font-family: Arial, sans-serif; padding: 20px; }
                        .header { text-align: center; margin-bottom: 30px; }
                        .result-box { border: 2px solid #333; padding: 20px; margin: 20px 0; }
                        .points-summary { display: flex; justify-content: space-around; margin: 20px 0; }
                        .footer { text-align: center; margin-top: 30px; font-size: 12px; }
                    </style>
                </head>
                <body>
                    <div class="header">
                        <h1>🧠 منصة تدريب القدرات بالذكاء الاصطناعي</h1>
                        <h2>نتيجة الاختبار</h2>
                    </div>
                    
                    <div class="result-box">
                        <h3>اسم الطالب: ${currentUser}</h3>
                        <p>نوع التدريب: ${currentMode === 'individual' ? 'فردي' : 'جماعي'}</p>
                        <p>نوع الأسئلة: ${currentQuestionType === 'quantitative' ? 'كمي' : currentQuestionType === 'verbal' ? 'لفظي' : 'كمي ولفظي'}</p>
                        <p>تاريخ الاختبار: ${new Date().toLocaleDateString('ar-SA')}</p>
                    </div>
                    
                    <div class="points-summary">
                        <div>
                            <h4>الإجابات الصحيحة</h4>
                            <p style="font-size: 24px; color: green;">${correct}</p>
                        </div>
                        <div>
                            <h4>الإجابات الخاطئة</h4>
                            <p style="font-size: 24px; color: red;">${wrong}</p>
                        </div>
                        <div>
                            <h4>النقاط المكتسبة</h4>
                            <p style="font-size: 24px; color: blue;">${points}</p>
                        </div>
                    </div>
                    
                    <div class="result-box">
                        <h4>إجمالي النقاط:</h4>
                        <p>نقاط التعلم الفردي: ${userPoints.individual}</p>
                        <p>نقاط التعلم الجماعي: ${userPoints.group}</p>
                        <p><strong>المجموع الكلي: ${userPoints.individual + userPoints.group}</strong></p>
                    </div>
                    
                    <div class="footer">
                        <p>تصميم أ.عبدالرحمن الثقفي</p>
                        <p>منصة تدريب القدرات بالذكاء الاصطناعي</p>
                    </div>
                </body>
                </html>
            `);
            
            printWindow.document.close();
            printWindow.print();
        }

        // Start new quiz
        function startNewQuiz() {
            // Reset variables
            currentQuestionIndex = 0;
            userAnswers = [];
            selectedQuestionCount = 10;
            timeLeft = 900;
            
            // Hide results and show mode selection
            document.getElementById('resultsScreen').classList.add('hidden');
            document.getElementById('modeSelectionScreen').classList.remove('hidden');
        }

        // Go to home
        function goHome() {
            // Reset all variables
            currentUser = '';
            currentMode = '';
            currentQuestionType = '';
            selectedQuestionCount = 10;
            currentQuestionIndex = 0;
            userAnswers = [];
            timeLeft = 900;
            challengeData = {};
            
            // Hide all screens except registration
            document.querySelectorAll('[id$="Screen"]').forEach(screen => {
                screen.classList.add('hidden');
            });
            document.getElementById('registrationScreen').classList.remove('hidden');
            document.getElementById('userPoints').classList.add('hidden');
            
            // Clear form
            document.getElementById('studentName').value = '';
        }
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'993ce62ff03af919',t:'MTc2MTM0NDgyMi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
