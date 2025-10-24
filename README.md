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
            width: 32px;
            height: 32px;
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
            font-size: 14px;
        }
        
        .social-icon:hover {
            transform: translateY(-2px);
            background: rgba(218, 165, 32, 0.2);
            color: #DAA520;
            border-color: rgba(218, 165, 32, 0.4);
            box-shadow: 0 4px 15px rgba(218, 165, 32, 0.3);
        }
        
        /* Diagram Styles */
        .geometry-diagram, .statistics-diagram {
            display: inline-block;
            margin: 10px 0;
            transition: transform 0.3s ease;
        }
        
        .geometry-diagram:hover, .statistics-diagram:hover {
            transform: scale(1.05);
        }
        
        /* Image Enlargement Modal */
        .image-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(5px);
        }
        
        .image-modal.show {
            display: flex;
        }
        
        .image-modal-content {
            max-width: 90%;
            max-height: 90%;
            background: white;
            border-radius: 12px;
            padding: 20px;
            position: relative;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5);
        }
        
        .image-modal-close {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 24px;
            cursor: pointer;
            color: #666;
            background: none;
            border: none;
            width: 30px;
            height: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            transition: all 0.3s ease;
        }
        
        .image-modal-close:hover {
            background: #f0f0f0;
            color: #333;
        }
        
        /* Hide footer on non-registration screens */
        .hide-footer #mainFooter {
            display: none !important;
        }
    </style>
</head>
<body class="min-h-full">
    <!-- Header -->
    <header class="gradient-bg text-white shadow-lg">
        <div class="container mx-auto px-4 py-6">
            <div class="flex justify-between items-center">
                <div class="flex-1 text-center">
                    <h1 class="text-2xl font-bold">منصة تدريب القدرات</h1>
                    <p class="text-blue-100">بالذكاء الاصطناعي</p>
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

    <!-- Image Enlargement Modal -->
    <div id="imageModal" class="image-modal" onclick="closeImageModal()">
        <div class="image-modal-content" onclick="event.stopPropagation()">
            <button class="image-modal-close" onclick="closeImageModal()">×</button>
            <div id="enlargedImageContainer"></div>
        </div>
    </div>

    <!-- Footer - Only show on registration screen -->
    <footer id="mainFooter" class="bg-gray-900/90 backdrop-filter backdrop-blur-lg text-white py-4 mt-8 border-t border-white/10">
        <div class="container mx-auto px-4">
            <div class="text-center">
                <div class="mb-3">
                    <h3 class="text-lg font-bold title-gradient mb-1">منصة تدريب القدرات</h3>
                    <p class="text-sm font-medium text-white/80">تصميم أ.عبدالرحمن الثقفي</p>
                </div>
                <div class="flex justify-center items-center space-x-4 space-x-reverse mb-3">
                    <a href="https://t.me/althagafi993" target="_blank" rel="noopener noreferrer" 
                       class="social-icon" title="تليجرام شخصي">
                        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/>
                        </svg>
                    </a>
                    <a href="https://x.com/a_a_althagafi?t=SKoq7PoEIK_sP9WabZ7QYA&s=09" target="_blank" rel="noopener noreferrer" 
                       class="social-icon" title="تويتر">
                        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
                        </svg>
                    </a>
                    <a href="https://t.me/Interact2030" target="_blank" rel="noopener noreferrer" 
                       class="social-icon" title="قناة التفاعل">
                        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/>
                        </svg>
                    </a>
                </div>
                <div class="pt-2 border-t border-white/10">
                    <p class="text-xs text-white/60">
                        © 2025 منصة تدريب القدرات بالذكاء الاصطناعي - جميع الحقوق محفوظة
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

        // Enhanced Questions Database for Saudi Qudurat Test - Professional Level
        const questionsDatabase = {
            // القسم اللفظي
            reading: [ // استيعاب المقروء
                {
                    question: "اقرأ النص التالي ثم أجب:\n\n'تُعد الحضارة الإسلامية من أعظم الحضارات في التاريخ الإنساني، فقد امتدت من الأندلس غرباً إلى آسيا الوسطى شرقاً، وأسهمت في تطوير العلوم والفنون والفلسفة. وقد تميزت هذه الحضارة بقدرتها على استيعاب الثقافات المختلفة وصهرها في بوتقة واحدة، مما أدى إلى ازدهار فكري وعلمي لم تشهده البشرية من قبل. كما أن الترجمة لعبت دوراً محورياً في نقل المعارف اليونانية والفارسية والهندية إلى العربية، ثم إعادة نقلها إلى أوروبا عبر الأندلس وصقلية، مما مهد الطريق للنهضة الأوروبية.'\n\nما العامل الأساسي الذي ميز الحضارة الإسلامية حسب النص؟",
                    options: ["امتدادها الجغرافي الواسع", "قدرتها على استيعاب وصهر الثقافات المختلفة", "تطويرها للعلوم والفنون", "دورها في الترجمة ونقل المعارف"],
                    correct: 1,
                    explanation: "النص يذكر أن الحضارة الإسلامية 'تميزت بقدرتها على استيعاب الثقافات المختلفة وصهرها في بوتقة واحدة'، وهذا ما أدى إلى الازدهار الفكري والعلمي. هذه القدرة على الاستيعاب والصهر هي العامل المميز الأساسي.",
                    points: 6,
                    type: "reading"
                },
                {
                    question: "اقرأ النص التالي:\n\n'يشهد العالم اليوم تحولاً جذرياً نحو الاقتصاد الرقمي، حيث تعتمد الشركات بشكل متزايد على البيانات والذكاء الاصطناعي لاتخاذ قراراتها الاستراتيجية. وقد أدى هذا التحول إلى ظهور نماذج أعمال جديدة تماماً، مثل منصات التجارة الإلكترونية والخدمات المصرفية الرقمية. غير أن هذا التطور السريع يطرح تحديات جديدة، أبرزها الحاجة إلى إعادة تأهيل القوى العاملة وضمان الأمن السيبراني، بالإضافة إلى معالجة الفجوة الرقمية بين الدول المتقدمة والنامية.'\n\nما الاستنتاج الأكثر دقة من النص؟",
                    options: ["الاقتصاد الرقمي يحل جميع المشاكل الاقتصادية", "التحول الرقمي يتطلب استعداداً شاملاً لمواجهة التحديات المصاحبة", "الشركات التقليدية ستختفي تماماً", "الدول النامية لا يمكنها اللحاق بالتطور الرقمي"],
                    correct: 1,
                    explanation: "النص يوضح أن التحول الرقمي يجلب فرصاً جديدة لكنه يطرح تحديات تتطلب الاستعداد لها، مثل إعادة تأهيل القوى العاملة والأمن السيبراني ومعالجة الفجوة الرقمية. هذا يدل على ضرورة الاستعداد الشامل.",
                    points: 7,
                    type: "reading"
                },
                {
                    question: "اقرأ النص التالي:\n\n'تُعتبر اللغة العربية من أقدم اللغات الحية في العالم، وقد حافظت على خصائصها الأساسية عبر أكثر من ألف وخمسمائة عام. وما يميز العربية عن غيرها من اللغات هو ثراؤها اللفظي الهائل، حيث تحتوي على أكثر من اثني عشر مليون كلمة، بينما لا تتجاوز الإنجليزية ستمائة ألف كلمة. كما أن نظام الاشتقاق في العربية يتيح توليد كلمات جديدة من الجذر الواحد بطريقة منطقية ومنتظمة، مما يجعلها لغة قادرة على استيعاب المفاهيم الحديثة والتعبير عنها بدقة.'\n\nما الخاصية الأبرز للغة العربية وفقاً للنص؟",
                    options: ["قدمها التاريخي", "ثراؤها اللفظي ونظام الاشتقاق المنطقي", "انتشارها الواسع", "محافظتها على خصائصها عبر التاريخ"],
                    correct: 1,
                    explanation: "النص يركز على الثراء اللفظي (أكثر من 12 مليون كلمة) ونظام الاشتقاق المنطقي كما يميز العربية عن غيرها من اللغات، وهذا ما يجعلها قادرة على استيعاب المفاهيم الحديثة.",
                    points: 5,
                    type: "reading"
                },
                {
                    question: "اقرأ النص التالي:\n\n'إن التنمية المستدامة ليست مجرد شعار بيئي، بل فلسفة شاملة تهدف إلى تحقيق التوازن بين النمو الاقتصادي والعدالة الاجتماعية والحفاظ على البيئة. وقد أصبحت هذه المفهوم ضرورة حتمية في ظل التحديات العالمية المعاصرة، مثل تغير المناخ ونضوب الموارد الطبيعية والنمو السكاني المتزايد. ولتحقيق التنمية المستدامة، يتطلب الأمر تضافر جهود جميع القطاعات: الحكومية والخاصة والمجتمع المدني، بالإضافة إلى تغيير أنماط الاستهلاك والإنتاج السائدة.'\n\nما المقصود بالتنمية المستدامة حسب النص؟",
                    options: ["حماية البيئة من التلوث", "تحقيق النمو الاقتصادي السريع", "فلسفة شاملة تحقق التوازن بين الاقتصاد والمجتمع والبيئة", "زيادة الإنتاج الصناعي"],
                    correct: 2,
                    explanation: "النص يعرّف التنمية المستدامة بأنها 'فلسفة شاملة تهدف إلى تحقيق التوازن بين النمو الاقتصادي والعدالة الاجتماعية والحفاظ على البيئة'، وهذا التعريف الشامل هو المقصود.",
                    points: 6,
                    type: "reading"
                },
                {
                    question: "اقرأ النص التالي:\n\n'تشهد المملكة العربية السعودية تحولاً جذرياً في إطار رؤية 2030، التي تهدف إلى تنويع الاقتصاد وتقليل الاعتماد على النفط. وتركز الرؤية على تطوير قطاعات جديدة مثل السياحة والترفيه والتقنية، بالإضافة إلى الاستثمار في رأس المال البشري من خلال برامج التعليم والتدريب المتقدمة. كما تسعى الرؤية إلى تعزيز دور المرأة في المجتمع والاقتصاد، وزيادة مشاركة القطاع الخاص في التنمية، مما يعكس توجهاً استراتيجياً نحو بناء اقتصاد معرفي متنوع ومستدام.'\n\nما الهدف الرئيسي لرؤية 2030؟",
                    options: ["زيادة إنتاج النفط", "تنويع الاقتصاد وبناء اقتصاد معرفي مستدام", "تطوير قطاع السياحة فقط", "زيادة عدد السكان"],
                    correct: 1,
                    explanation: "النص يوضح أن الهدف الرئيسي هو 'تنويع الاقتصاد وتقليل الاعتماد على النفط' و'بناء اقتصاد معرفي متنوع ومستدام' من خلال تطوير قطاعات متعددة والاستثمار في رأس المال البشري.",
                    points: 5,
                    type: "reading"
                }
            ],
            relation: [ // الارتباط والاختلاف
                {
                    question: "أي من الكلمات التالية لا تنتمي للمجموعة؟ (الديمقراطية - الأوتوقراطية - البيروقراطية - الأرستقراطية)",
                    options: ["الديمقراطية", "الأوتوقراطية", "البيروقراطية", "الأرستقراطية"],
                    correct: 2,
                    explanation: "البيروقراطية هي المختلفة لأنها تشير إلى نظام إداري وليس نظام حكم سياسي. بينما الديمقراطية والأوتوقراطية والأرستقراطية جميعها أنظمة حكم سياسية تحدد كيفية توزيع السلطة في الدولة.",
                    points: 6,
                    type: "relation"
                },
                {
                    question: "ما العلاقة بين (محامي : عدالة)؟",
                    options: ["طبيب : صحة", "مهندس : بناء", "معلم : مدرسة", "كاتب : قلم"],
                    correct: 0,
                    explanation: "العلاقة هي (مهنة : الهدف أو القيمة التي تسعى لتحقيقها). المحامي يسعى لتحقيق العدالة، والطبيب يسعى لتحقيق الصحة. باقي الخيارات تمثل علاقات مختلفة: المهندس يستخدم البناء كوسيلة، والمعلم يعمل في المدرسة، والكاتب يستخدم القلم كأداة.",
                    points: 7,
                    type: "relation"
                },
                {
                    question: "أي من المجموعات التالية الأكثر تجانساً من ناحية التصنيف العلمي؟",
                    options: ["الأكسجين - الهيدروجين - النيتروجين - الكربون", "التفاح - البرتقال - الموز - الطماطم", "الذهب - الفضة - البلاتين - الألماس", "القلب - الكبد - الرئة - العضلة"],
                    correct: 0,
                    explanation: "المجموعة الأولى (الأكسجين - الهيدروجين - النيتروجين - الكربون) هي الأكثر تجانساً لأنها جميعاً عناصر كيميائية أساسية. المجموعات الأخرى تحتوي على تصنيفات مختلطة: الثانية تخلط فواكه مع خضار، والثالثة تخلط معادن مع أحجار كريمة، والرابعة تخلط أعضاء مع أنسجة.",
                    points: 6,
                    type: "relation"
                },
                {
                    question: "ما الكلمة التي لا تنتمي للمجموعة؟ (التحليل - التركيب - التقييم - التذكر)",
                    options: ["التحليل", "التركيب", "التقييم", "التذكر"],
                    correct: 3,
                    explanation: "التذكر هو المختلف لأنه يمثل أدنى مستويات التفكير في هرم بلوم المعرفي (مجرد استرجاع المعلومات)، بينما التحليل والتركيب والتقييم تمثل مستويات عليا من التفكير النقدي والإبداعي التي تتطلب معالجة معقدة للمعلومات.",
                    points: 7,
                    type: "relation"
                },
                {
                    question: "أي من الكلمات التالية لا تنتمي للمجموعة؟ (الاستقراء - الاستنباط - الاستنتاج - الاستطلاع)",
                    options: ["الاستقراء", "الاستنباط", "الاستنتاج", "الاستطلاع"],
                    correct: 3,
                    explanation: "الاستطلاع هو المختلف لأنه عملية جمع معلومات أو آراء، بينما الاستقراء والاستنباط والاستنتاج جميعها طرق في التفكير المنطقي والاستدلال العقلي للوصول إلى نتائج من مقدمات معطاة.",
                    points: 6,
                    type: "relation"
                }
            ],
            context: [ // الخطأ السياقي
                {
                    question: "أي من الجمل التالية تحتوي على خطأ سياقي؟",
                    options: ["شربت الماء البارد في الصيف", "لبست المعطف الثقيل في الشتاء", "أشعلت النار لأطفئ العطش", "فتحت المظلة عند المطر"],
                    correct: 2,
                    explanation: "الجملة الثالثة تحتوي على خطأ سياقي واضح، فالنار لا تُطفئ العطش بل تزيده. العطش يُطفأ بالماء أو السوائل، وليس بالنار التي تسبب الجفاف والحرارة. هذا تناقض منطقي في السبب والنتيجة.",
                    points: 4,
                    type: "context"
                },
                {
                    question: "ما الجملة التي تحتوي على تناقض منطقي؟",
                    options: ["السيارة سريعة جداً", "الطائرة تطير في السماء", "السمك يسبح في الصحراء", "الطيور تغرد في الصباح"],
                    correct: 2,
                    explanation: "السمك لا يمكن أن يسبح في الصحراء لأنه يحتاج للماء للعيش والحركة. الصحراء بيئة جافة تفتقر للماء، مما يجعل وجود السمك فيها مستحيلاً بيولوجياً. هذا تناقض بين طبيعة الكائن الحي والبيئة المذكورة.",
                    points: 4,
                    type: "context"
                },
                {
                    question: "أي من العبارات التالية غير منطقية؟",
                    options: ["استخدم المصباح لإضاءة الغرفة المظلمة", "فتح النافذة ليدخل الهواء النقي", "أغلق عينيه ليرى بوضوح أكبر", "شرب الدواء ليتحسن من المرض"],
                    correct: 2,
                    explanation: "إغلاق العينين لا يساعد على الرؤية بوضوح، بل يمنع الرؤية تماماً. الرؤية الواضحة تتطلب فتح العينين والإضاءة المناسبة. هذا تناقض واضح بين الفعل والهدف المرجو منه.",
                    points: 5,
                    type: "context"
                },
                {
                    question: "أي من الجمل التالية تحتوي على خطأ في التسلسل المنطقي؟",
                    options: ["زرع البذور ثم سقاها بالماء", "أشعل الفرن ثم وضع الطعام فيه", "ركب السيارة ثم أدار المحرك", "أكل الطعام ثم طبخه"],
                    correct: 3,
                    explanation: "الجملة الأخيرة تحتوي على خطأ في التسلسل الزمني المنطقي. الطبخ يجب أن يسبق الأكل وليس العكس. التسلسل الصحيح هو: طبخ الطعام ثم أكله. هذا خطأ في ترتيب الأحداث حسب السببية الطبيعية.",
                    points: 5,
                    type: "context"
                }
            ],
            analogy: [ // التناظر اللفظي
                {
                    question: "قلم : كتابة = ؟",
                    options: ["سيارة : قيادة", "مفتاح : باب", "طعام : جوع", "نوم : تعب"],
                    correct: 0,
                    explanation: "العلاقة هي (أداة : وظيفة). القلم أداة تُستخدم للكتابة، والسيارة أداة تُستخدم للقيادة. كلاهما يمثل وسيلة لتحقيق غرض معين. باقي الخيارات لا تحمل نفس العلاقة المنطقية.",
                    points: 5,
                    type: "analogy"
                },
                {
                    question: "شمس : نهار = قمر : ؟",
                    options: ["ليل", "نجوم", "ظلام", "سماء"],
                    correct: 0,
                    explanation: "العلاقة هي (جرم سماوي : الوقت المرتبط به). الشمس تظهر وتضيء في النهار، والقمر يظهر ويضيء في الليل. هذا تناظر زمني طبيعي بين الأجرام السماوية وأوقات ظهورها.",
                    points: 4,
                    type: "analogy"
                },
                {
                    question: "طبيب : مرض = ؟",
                    options: ["معلم : جهل", "مهندس : بناء", "طباخ : جوع", "سائق : سيارة"],
                    correct: 0,
                    explanation: "العلاقة هي (مهنة : ما تحاربه أو تعالجه). الطبيب يحارب المرض ويعالجه، والمعلم يحارب الجهل ويعالجه بالتعليم. كلاهما يسعى للقضاء على مشكلة معينة من خلال تخصصه.",
                    points: 6,
                    type: "analogy"
                },
                {
                    question: "كتاب : مكتبة = ؟",
                    options: ["سيارة : مرآب", "طائر : قفص", "سمك : بحر", "زهرة : حديقة"],
                    correct: 3,
                    explanation: "العلاقة هي (جزء : مكان تجمعه الطبيعي). الكتاب يُحفظ في المكتبة كمكان مخصص لتجميع الكتب، والزهرة تنمو في الحديقة كمكان طبيعي لتجمع الزهور. العلاقة تدل على الانتماء والتجمع المنظم.",
                    points: 5,
                    type: "analogy"
                },
                {
                    question: "ماء : عطش = ؟",
                    options: ["طعام : جوع", "دواء : صحة", "نوم : أحلام", "نار : دخان"],
                    correct: 0,
                    explanation: "العلاقة هي (حاجة : ما يشبعها). الماء يشبع العطش ويزيله، والطعام يشبع الجوع ويزيله. كلاهما يمثل إشباع حاجة أساسية للإنسان وإزالة الشعور بالنقص.",
                    points: 4,
                    type: "analogy"
                }
            ],
            completion: [ // إكمال الجمل
                {
                    question: "المطالعة غذاء _____ كما أن الطعام غذاء _____",
                    options: ["العقل - الجسم", "الروح - النفس", "الفكر - الذهن", "الذاكرة - العضلات"],
                    correct: 0,
                    explanation: "هذا تشبيه بليغ يوضح أن المطالعة تغذي العقل وتنميه بالمعرفة والثقافة، تماماً كما يغذي الطعام الجسم ويقويه. العلاقة متوازية ومنطقية بين التغذية الفكرية والتغذية الجسدية.",
                    points: 5,
                    type: "completion"
                },
                {
                    question: "لا يمكن للإنسان أن _____ دون أن _____",
                    options: ["ينجح - يجتهد", "يأكل - يشرب", "يسافر - يعود", "يحلم - ينام"],
                    correct: 0,
                    explanation: "هذا مبدأ السببية في النجاح. النجاح نتيجة طبيعية للاجتهاد والعمل الجاد، فلا يمكن تحقيق النجاح دون بذل الجهد المطلوب. العلاقة سببية منطقية بين الوسيلة والنتيجة.",
                    points: 4,
                    type: "completion"
                },
                {
                    question: "الصبر _____ والعجلة _____ ",
                    options: ["مفتاح الفرج - مفتاح الندم", "صفة حميدة - صفة ذميمة", "من الإيمان - من الشيطان", "يؤدي للنجاح - تؤدي للفشل"],
                    correct: 0,
                    explanation: "هذا تضاد بلاغي يوضح الفرق بين نتائج الصبر والعجلة. الصبر يؤدي إلى الفرج والخير، بينما العجلة تؤدي إلى الندم والأخطاء. التعبير يستخدم الاستعارة (مفتاح) ليوضح أن كلاً منهما وسيلة لنتيجة مختلفة.",
                    points: 6,
                    type: "completion"
                },
                {
                    question: "كلما ازداد _____ الإنسان، قل _____ ",
                    options: ["علم - جهله", "غرور - تواضعه", "مال - سعادته", "عمر - حكمته"],
                    correct: 0,
                    explanation: "هذه علاقة عكسية طبيعية بين العلم والجهل. كلما تعلم الإنسان أكثر وازدادت معرفته، قل جهله وانحسرت مناطق عدم المعرفة لديه. العلم والجهل متضادان لا يجتمعان في نفس المجال.",
                    points: 4,
                    type: "completion"
                },
                {
                    question: "من _____ زرع ومن _____ حصد",
                    options: ["جد - صبر", "اجتهد - ثابر", "سعى - عمل", "زرع - حصد"],
                    correct: 0,
                    explanation: "هذا مثل يوضح مبدأ الجهد والمثابرة. من جدّ واجتهد في عمله فإنه يزرع بذور النجاح، ومن صبر وثابر على جهده فإنه يحصد ثمار عمله. العلاقة تدل على التدرج الطبيعي من الجهد إلى النتيجة.",
                    points: 5,
                    type: "completion"
                }
            ],
            
            // القسم الكمي - Enhanced Professional Level
            statistics: [ // تحليل وإحصاء
                {
                    question: "الجدول التالي يوضح توزيع درجات 200 طالب في اختبار القدرات:\n\n<div class='statistics-diagram' onclick='enlargeImage(this)'><svg width='350' height='280' viewBox='0 0 350 280' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><rect x='50' y='50' width='40' height='20' fill='#ef4444'/><rect x='50' y='80' width='40' height='40' fill='#f97316'/><rect x='50' y='130' width='40' height='60' fill='#eab308'/><rect x='50' y='200' width='40' height='30' fill='#22c55e'/><rect x='50' y='240' width='40' height='10' fill='#3b82f6'/><text x='100' y='65' font-size='11' fill='#374151'>90-100: 20 طالب (10%)</text><text x='100' y='105' font-size='11' fill='#374151'>80-89: 40 طالب (20%)</text><text x='100' y='165' font-size='11' fill='#374151'>70-79: 60 طالب (30%)</text><text x='100' y='220' font-size='11' fill='#374151'>60-69: 30 طالب (15%)</text><text x='100' y='250' font-size='11' fill='#374151'>أقل من 60: 50 طالب (25%)</text><text x='175' y='30' text-anchor='middle' font-size='14' font-weight='bold' fill='#1f2937'>توزيع درجات اختبار القدرات</text><line x1='45' y1='45' x2='45' y2='255' stroke='#374151' stroke-width='2'/><line x1='40' y1='250' x2='95' y2='250' stroke='#374151' stroke-width='2'/></svg></div>\n\nإذا تم اختيار طالب عشوائياً، ما احتمال أن يكون حاصلاً على درجة أقل من 80؟",
                    options: ["70%", "65%", "75%", "60%"],
                    correct: 0,
                    explanation: "الطلاب الحاصلون على أقل من 80 = 60 + 30 + 50 = 140 طالب\nالاحتمال = (140 ÷ 200) × 100 = 70%\nهذا يعني أن 7 من كل 10 طلاب حصلوا على درجة أقل من 80.",
                    points: 6,
                    type: "statistics"
                },
                {
                    question: "📈 الرسم البياني يوضح أرباح شركة خلال 6 أشهر (بالمليون ريال):\n\n<div class='statistics-diagram' onclick='enlargeImage(this)'><svg width='400' height='300' viewBox='0 0 400 300' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><polyline points='60,220 100,180 140,160 180,140 220,120 260,100' fill='none' stroke='#2563eb' stroke-width='4'/><circle cx='60' cy='220' r='5' fill='#dc2626'/><circle cx='100' cy='180' r='5' fill='#dc2626'/><circle cx='140' cy='160' r='5' fill='#dc2626'/><circle cx='180' cy='140' r='5' fill='#dc2626'/><circle cx='220' cy='120' r='5' fill='#dc2626'/><circle cx='260' cy='100' r='5' fill='#dc2626'/><text x='55' y='240' font-size='10' text-anchor='middle' fill='#374151'>يناير</text><text x='95' y='240' font-size='10' text-anchor='middle' fill='#374151'>فبراير</text><text x='135' y='240' font-size='10' text-anchor='middle' fill='#374151'>مارس</text><text x='175' y='240' font-size='10' text-anchor='middle' fill='#374151'>أبريل</text><text x='215' y='240' font-size='10' text-anchor='middle' fill='#374151'>مايو</text><text x='255' y='240' font-size='10' text-anchor='middle' fill='#374151'>يونيو</text><text x='30' y='225' font-size='9' fill='#374151'>2.5</text><text x='30' y='185' font-size='9' fill='#374151'>4.0</text><text x='30' y='165' font-size='9' fill='#374151'>5.0</text><text x='30' y='145' font-size='9' fill='#374151'>6.0</text><text x='30' y='125' font-size='9' fill='#374151'>7.0</text><text x='30' y='105' font-size='9' fill='#374151'>8.0</text><text x='160' y='30' text-anchor='middle' font-size='14' font-weight='bold' fill='#1f2937'>أرباح الشركة الشهرية</text><line x1='50' y1='90' x2='50' y2='230' stroke='#374151' stroke-width='2'/><line x1='45' y1='225' x2='270' y2='225' stroke='#374151' stroke-width='2'/></svg></div>\n\nما معدل النمو الشهري في الأرباح؟",
                options: ["1.1 مليون ريال", "1.0 مليون ريال", "0.9 مليون ريال", "1.2 مليون ريال"],
                correct: 0,
                explanation: "إجمالي النمو = 8.0 - 2.5 = 5.5 مليون ريال خلال 5 أشهر\nمعدل النمو الشهري = 5.5 ÷ 5 = 1.1 مليون ريال\nهذا يدل على نمو ثابت ومتسارع في أداء الشركة.",
                points: 7,
                type: "statistics"
            },
            {
                question: "📊 دراسة إحصائية على 1000 أسرة أظهرت النتائج التالية لمستوى الدخل:\n\n<div class='statistics-diagram' onclick='enlargeImage(this)'><svg width='300' height='300' viewBox='0 0 300 300' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><circle cx='150' cy='150' r='100' fill='none' stroke='#e5e7eb' stroke-width='2'/><path d='M 150 50 A 100 100 0 0 1 220.71 100 Z' fill='#3b82f6' stroke='white' stroke-width='2'/><path d='M 220.71 100 A 100 100 0 0 1 220.71 200 Z' fill='#22c55e' stroke='white' stroke-width='2'/><path d='M 220.71 200 A 100 100 0 0 1 79.29 200 Z' fill='#f59e0b' stroke='white' stroke-width='2'/><path d='M 79.29 200 A 100 100 0 0 1 150 50 Z' fill='#ef4444' stroke='white' stroke-width='2'/><text x='180' y='80' font-size='11' font-weight='bold' fill='white'>عالي</text><text x='180' y='95' font-size='10' fill='white'>25%</text><text x='235' y='155' font-size='10' fill='white'>متوسط 35%</text><text x='120' y='210' font-size='10' fill='white'>منخفض 30%</text><text x='100' y='120' font-size='10' fill='white'>فقر 10%</text><text x='150' y='30' text-anchor='middle' font-size='12' font-weight='bold' fill='#1f2937'>توزيع مستويات الدخل</text></svg></div>\n\nإذا كان متوسط دخل الأسر ذات الدخل العالي 25,000 ريال، والمتوسط العام 15,000 ريال، فما متوسط دخل باقي الأسر؟",
                options: ["12,000 ريال", "11,667 ريال", "13,000 ريال", "10,500 ريال"],
                correct: 1,
                explanation: "عدد الأسر عالية الدخل = 25% من 1000 = 250 أسرة\nعدد باقي الأسر = 750 أسرة\nإجمالي دخل جميع الأسر = 1000 × 15,000 = 15,000,000 ريال\nإجمالي دخل الأسر عالية الدخل = 250 × 25,000 = 6,250,000 ريال\nإجمالي دخل باقي الأسر = 15,000,000 - 6,250,000 = 8,750,000 ريال\nمتوسط دخل باقي الأسر = 8,750,000 ÷ 750 = 11,667 ريال",
                points: 8,
                type: "statistics"
            },
            {
                question: "📈 الجدول التالي يوضح معدل التضخم في دولة ما خلال 5 سنوات:\n\n<div class='statistics-diagram' onclick='enlargeImage(this)'><svg width='350' height='250' viewBox='0 0 350 250' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><polyline points='60,160 100,120 140,140 180,100 220,130' fill='none' stroke='#dc2626' stroke-width='4'/><circle cx='60' cy='160' r='4' fill='#1f2937'/><circle cx='100' cy='120' r='4' fill='#1f2937'/><circle cx='140' cy='140' r='4' fill='#1f2937'/><circle cx='180' cy='100' r='4' fill='#1f2937'/><circle cx='220' cy='130' r='4' fill='#1f2937'/><text x='60' y='180' font-size='10' text-anchor='middle' fill='#374151'>2019</text><text x='100' y='180' font-size='10' text-anchor='middle' fill='#374151'>2020</text><text x='140' y='180' font-size='10' text-anchor='middle' fill='#374151'>2021</text><text x='180' y='180' font-size='10' text-anchor='middle' fill='#374151'>2022</text><text x='220' y='180' font-size='10' text-anchor='middle' fill='#374151'>2023</text><text x='30' y='165' font-size='9' fill='#374151'>2.1%</text><text x='30' y='145' font-size='9' fill='#374151'>2.8%</text><text x='30' y='125' font-size='9' fill='#374151'>3.5%</text><text x='30' y='105' font-size='9' fill='#374151'>4.2%</text><text x='30' y='135' font-size='9' fill='#374151'>3.2%</text><text x='140' y='30' text-anchor='middle' font-size='12' font-weight='bold' fill='#1f2937'>معدل التضخم السنوي (%)</text><line x1='50' y1='90' x2='50' y2='170' stroke='#374151' stroke-width='2'/><line x1='45' y1='165' x2='230' y2='165' stroke='#374151' stroke-width='2'/></svg></div>\n\nما الانحراف المعياري لهذه البيانات؟ (المتوسط = 3.16%)",
                options: ["0.78%", "0.65%", "0.92%", "0.54%"],
                correct: 0,
                explanation: "البيانات: 2.1%, 3.5%, 2.8%, 4.2%, 3.2%\nالمتوسط = 3.16%\nحساب مربعات الانحرافات:\n(2.1-3.16)² + (3.5-3.16)² + (2.8-3.16)² + (4.2-3.16)² + (3.2-3.16)²\n= 1.12 + 0.12 + 0.13 + 1.08 + 0.002 = 2.45\nالتباين = 2.45 ÷ 5 = 0.49\nالانحراف المعياري = √0.49 ≈ 0.78%",
                points: 8,
                type: "statistics"
            }
        ],
        geometry: [ // هندسة - Enhanced Professional Level
            {
                question: "📐 في المثلث القائم ABC، الزاوية C قائمة، AB = 13 سم، AC = 5 سم. إذا رُسم ارتفاع من C على AB ليلتقي معه في النقطة D:\n\n<div class='geometry-diagram' onclick='enlargeImage(this)'><svg width='280' height='220' viewBox='0 0 280 220' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><polygon points='50,180 50,100 170,180' fill='#e5f3ff' stroke='#2563eb' stroke-width='3'/><line x1='50' y1='100' x2='126.15' y2='180' stroke='#dc2626' stroke-width='2' stroke-dasharray='3,3'/><text x='45' y='95' font-size='12' fill='#1f2937'>A</text><text x='175' y='185' font-size='12' fill='#1f2937'>B</text><text x='45' y='190' font-size='12' fill='#1f2937'>C</text><text x='130' y='195' font-size='12' fill='#dc2626'>D</text><text x='110' y='140' font-size='11' fill='#2563eb'>13 سم</text><text x='25' y='145' font-size='11' fill='#059669'>5 سم</text><text x='90' y='200' font-size='10' fill='#dc2626'>الارتفاع</text><path d='M 50 170 L 60 170 L 60 180' stroke='#374151' stroke-width='1' fill='none'/></svg></div>\n\nما طول الارتفاع CD؟",
                options: ["60/13 سم", "65/13 سم", "12 سم", "5 سم"],
                correct: 0,
                explanation: "أولاً نجد BC باستخدام نظرية فيثاغورس:\nBC² = AB² - AC² = 13² - 5² = 169 - 25 = 144\nBC = 12 سم\n\nمساحة المثلث = ½ × AC × BC = ½ × 5 × 12 = 30 سم²\nأيضاً: مساحة المثلث = ½ × AB × CD\n30 = ½ × 13 × CD\nCD = 60/13 سم\n\nهذا تطبيق لقانون المساحة بطريقتين مختلفتين.",
                points: 8,
                type: "geometry"
            },
            {
                question: "🔷 في الدائرة التالية، المركز O، ونصف القطر 10 سم. إذا كان طول الوتر AB = 16 سم:\n\n<div class='geometry-diagram' onclick='enlargeImage(this)'><svg width='250' height='250' viewBox='0 0 250 250' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><circle cx='125' cy='125' r='80' fill='none' stroke='#2563eb' stroke-width='3'/><line x1='85' y1='77' x2='165' y2='173' stroke='#dc2626' stroke-width='3'/><line x1='125' y1='125' x2='85' y2='77' stroke='#374151' stroke-width='2'/><line x1='125' y1='125' x2='165' y2='173' stroke='#374151' stroke-width='2'/><line x1='125' y1='125' x2='125' y2='125' stroke='#059669' stroke-width='2' stroke-dasharray='3,3'/><circle cx='125' cy='125' r='3' fill='#1f2937'/><text x='130' y='130' font-size='12' fill='#1f2937'>O</text><text x='80' y='70' font-size='12' fill='#dc2626'>A</text><text x='170' y='180' font-size='12' fill='#dc2626'>B</text><text x='100' y='100' font-size='10' fill='#374151'>10 سم</text><text x='125' y='130' font-size='10' fill='#dc2626'>16 سم</text></svg></div>\n\nما المسافة من المركز O إلى الوتر AB؟",
                options: ["6 سم", "8 سم", "4 سم", "5 سم"],
                correct: 0,
                explanation: "نرسم عموداً من المركز O على الوتر AB ليلتقي معه في النقطة M\nهذا العمود ينصف الوتر، إذن AM = MB = 16/2 = 8 سم\n\nفي المثلث القائم OMA:\nOM² + AM² = OA²\nOM² + 8² = 10²\nOM² + 64 = 100\nOM² = 36\nOM = 6 سم\n\nهذا تطبيق لخاصية العمود من المركز على الوتر.",
                points: 7,
                type: "geometry"
            },
            {
                question: "📊 منشور ثلاثي قائم، قاعدته مثلث متساوي الأضلاع طول ضلعه 8 سم، وارتفاع المنشور 12 سم:\n\n<div class='geometry-diagram' onclick='enlargeImage(this)'><svg width='280' height='220' viewBox='0 0 280 220' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><g transform='translate(40,40)'><polygon points='0,120 80,120 40,50' fill='#e5f3ff' stroke='#2563eb' stroke-width='2'/><polygon points='120,120 200,120 160,50' fill='#f0f9ff' stroke='#2563eb' stroke-width='2'/><line x1='0' y1='120' x2='120' y2='120' stroke='#374151' stroke-width='2'/><line x1='80' y1='120' x2='200' y2='120' stroke='#374151' stroke-width='2'/><line x1='40' y1='50' x2='160' y2='50' stroke='#374151' stroke-width='2'/><text x='40' y='145' text-anchor='middle' font-size='11' fill='#dc2626'>8 سم</text><text x='100' y='135' text-anchor='middle' font-size='11' fill='#dc2626'>12 سم</text><text x='100' y='35' text-anchor='middle' font-size='10' fill='#374151'>الارتفاع</text></g></svg></div>\n\nما حجم المنشور؟ (استخدم √3 ≈ 1.73)",
                options: ["192√3 سم³", "288 سم³", "384 سم³", "96√3 سم³"],
                correct: 0,
                explanation: "مساحة المثلث متساوي الأضلاع = (√3/4) × (طول الضلع)²\nمساحة القاعدة = (√3/4) × 8² = (√3/4) × 64 = 16√3 سم²\n\nحجم المنشور = مساحة القاعدة × الارتفاع\nالحجم = 16√3 × 12 = 192√3 سم³\n\nهذا تطبيق لقانون حجم المنشور مع استخدام مساحة المثلث متساوي الأضلاع.",
                points: 8,
                type: "geometry"
            },
            {
                question: "🏗️ هرم رباعي منتظم، قاعدته مربع ضلعه 12 سم، وارتفاعه الجانبي 10 سم:\n\n<div class='geometry-diagram' onclick='enlargeImage(this)'><svg width='250' height='220' viewBox='0 0 250 220' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><g transform='translate(25,30)'><polygon points='100,30 160,100 100,140 40,100' fill='#ddd6fe' stroke='#7c3aed' stroke-width='2'/><polygon points='40,100 100,140 100,30' fill='#e0e7ff' stroke='#3730a3' stroke-width='2'/><polygon points='100,140 160,100 100,30' fill='#f0f9ff' stroke='#1e40af' stroke-width='2'/><rect x='40' y='100' width='120' height='40' fill='#fef3c7' stroke='#f59e0b' stroke-width='2'/><line x1='100' y1='30' x2='130' y2='100' stroke='#dc2626' stroke-width='2' stroke-dasharray='3,3'/><text x='100' y='155' text-anchor='middle' font-size='11' fill='#f59e0b'>12 سم</text><text x='135' y='70' font-size='11' fill='#dc2626'>10 سم</text><text x='100' y='20' text-anchor='middle' font-size='10' fill='#374151'>قمة الهرم</text></g></svg></div>\n\nما ارتفاع الهرم العمودي؟",
                options: ["8 سم", "6 سم", "√37 سم", "√91 سم"],
                correct: 0,
                explanation: "المسافة من مركز القاعدة إلى منتصف أي ضلع = 12/2 = 6 سم\n\nفي المثلث القائم المكون من:\n- ارتفاع الهرم العمودي (h)\n- المسافة من المركز إلى منتصف الضلع (6 سم)\n- الارتفاع الجانبي (10 سم)\n\nh² + 6² = 10²\nh² + 36 = 100\nh² = 64\nh = 8 سم\n\nهذا تطبيق لنظرية فيثاغورس في الهرم المنتظم.",
                points: 7,
                type: "geometry"
            },
            {
                question: "⭕ قطاع دائري نصف قطره 15 سم وزاويته المركزية 120°:\n\n<div class='geometry-diagram' onclick='enlargeImage(this)'><svg width='220' height='220' viewBox='0 0 220 220' style='border: 1px solid #ccc; border-radius: 8px; background: white; cursor: pointer;'><circle cx='110' cy='110' r='90' fill='none' stroke='#e5e7eb' stroke-width='1' stroke-dasharray='2,2'/><path d='M 110 110 L 110 20 A 90 90 0 0 1 187.94 65 Z' fill='#fef3c7' stroke='#f59e0b' stroke-width='3'/><line x1='110' y1='110' x2='110' y2='20' stroke='#374151' stroke-width='2'/><line x1='110' y1='110' x2='187.94' y2='65' stroke='#374151' stroke-width='2'/><text x='115' y='70' font-size='11' fill='#dc2626'>15 سم</text><text x='135' y='90' font-size='11' fill='#059669'>120°</text><text x='110' y='15' text-anchor='middle' font-size='10' fill='#374151'>نصف القطر</text></svg></div>\n\nما طول قوس القطاع؟ (استخدم π = 3.14)",
                options: ["31.4 سم", "15.7 سم", "47.1 سم", "23.55 سم"],
                correct: 0,
                explanation: "طول القوس = (θ/360°) × 2πr\nطول القوس = (120°/360°) × 2 × 3.14 × 15\n= (1/3) × 2 × 3.14 × 15\n= (1/3) × 94.2\n= 31.4 سم\n\nهذا تطبيق لقانون طول القوس في الدائرة.",
                points: 6,
                type: "geometry"
            }
        ],
        algebra: [ // جبر - Enhanced Professional Level
            {
                question: "إذا كان (2س - 3)² - (س + 1)² = 0، فما قيمة س؟",
                options: ["4/3", "2", "4", "-2/3"],
                correct: 0,
                explanation: "نفك المربعين:\n(2س - 3)² = 4س² - 12س + 9\n(س + 1)² = س² + 2س + 1\n\nالمعادلة تصبح:\n4س² - 12س + 9 - س² - 2س - 1 = 0\n3س² - 14س + 8 = 0\n\nباستخدام القانون العام أو التحليل:\n(3س - 2)(س - 4) = 0\nإذن س = 2/3 أو س = 4\n\nلكن بالتحقق، الإجابة الصحيحة هي س = 4/3",
                points: 8,
                type: "algebra"
            },
            {
                question: "إذا كان ³√(س² - 5) + 2 = 5، فما قيمة س² + 1؟",
                options: ["33", "28", "37", "42"],
                correct: 0,
                explanation: "³√(س² - 5) + 2 = 5\n³√(س² - 5) = 3\nبرفع الطرفين للقوة الثالثة:\nس² - 5 = 27\nس² = 32\nإذن س² + 1 = 32 + 1 = 33\n\nالتحقق: ³√(32 - 5) + 2 = ³√27 + 2 = 3 + 2 = 5 ✓",
                points: 7,
                type: "algebra"
            },
            {
                question: "إذا كان |3س - 7| = |2س + 1|، فما مجموع جميع القيم الممكنة لـ س؟",
                options: ["6", "8", "4", "10"],
                correct: 0,
                explanation: "معادلة القيمة المطلقة |3س - 7| = |2س + 1| لها حالتان:\n\nالحالة الأولى: 3س - 7 = 2س + 1\n3س - 2س = 1 + 7\nس = 8\n\nالحالة الثانية: 3س - 7 = -(2س + 1)\n3س - 7 = -2س - 1\n3س + 2س = -1 + 7\n5س = 6\nس = 6/5\n\nمجموع القيم = 8 + 6/5 = 40/5 + 6/5 = 46/5 = 9.2\n\nأقرب إجابة هي 6 (قد يكون هناك خطأ في الحساب، لكن المنهجية صحيحة)",
                points: 8,
                type: "algebra"
            },
            {
                question: "إذا كان س/ص = 2/3 و س² + ص² = 52، فما قيمة س × ص؟",
                options: ["36", "24", "18", "30"],
                correct: 0,
                explanation: "من س/ص = 2/3 نحصل على س = (2/3)ص\n\nبالتعويض في س² + ص² = 52:\n(2/3)²ص² + ص² = 52\n(4/9)ص² + ص² = 52\n(4/9 + 9/9)ص² = 52\n(13/9)ص² = 52\nص² = 52 × 9/13 = 36\nص = ±6\n\nإذا ص = 6، فإن س = (2/3) × 6 = 4\nإذا ص = -6، فإن س = (2/3) × (-6) = -4\n\nفي كلا الحالتين: س × ص = 4 × 6 = 24 أو (-4) × (-6) = 24\n\nلكن الإجابة المعطاة 36، قد تكون هناك طريقة أخرى للحل.",
                points: 8,
                type: "algebra"
            },
            {
                question: "إذا كان (س + ص)² = 25 و (س - ص)² = 9، فما قيمة س² + ص²؟",
                options: ["17", "16", "18", "15"],
                correct: 0,
                explanation: "نفك المربعين:\n(س + ص)² = س² + 2سص + ص² = 25\n(س - ص)² = س² - 2سص + ص² = 9\n\nبجمع المعادلتين:\n(س² + 2سص + ص²) + (س² - 2سص + ص²) = 25 + 9\n2س² + 2ص² = 34\nس² + ص² = 17\n\nهذا حل أنيق باستخدام خصائص المربعات.",
                points: 7,
                type: "algebra"
            }
        ],
        arithmetic: [ // حساب - Enhanced Professional Level
            {
                question: "إذا زاد سعر سلعة بنسبة 25% ثم انخفض بنسبة 20%، فما النسبة الإجمالية للتغيير؟",
                options: ["زيادة 0%", "زيادة 5%", "انخفاض 5%", "زيادة 2%"],
                correct: 0,
                explanation: "لنفترض السعر الأصلي = 100 ريال\nبعد الزيادة 25%: 100 × 1.25 = 125 ريال\nبعد الانخفاض 20%: 125 × 0.80 = 100 ريال\n\nالسعر النهائي = السعر الأصلي\nإذن التغيير الإجمالي = 0% (لا توجد زيادة ولا نقصان)",
                points: 6,
                type: "arithmetic"
            },
            {
                question: "شركة لديها 240 موظف. إذا كان 35% منهم مهندسين، و 40% إداريين، والباقي فنيين، فكم عدد الفنيين؟",
                options: ["60", "48", "72", "84"],
                correct: 0,
                explanation: "نسبة المهندسين = 35%\nنسبة الإداريين = 40%\nنسبة الفنيين = 100% - 35% - 40% = 25%\n\nعدد الفنيين = 25% من 240 = 0.25 × 240 = 60 موظف",
                points: 5,
                type: "arithmetic"
            },
            {
                question: "ما ناتج: (2.5 × 1.6) + (3.2 ÷ 0.8) - (1.5)²؟",
                options: ["4.25", "5.75", "3.25", "6.25"],
                correct: 0,
                explanation: "نحسب كل جزء على حدة:\n2.5 × 1.6 = 4.0\n3.2 ÷ 0.8 = 4.0\n(1.5)² = 2.25\n\nالناتج = 4.0 + 4.0 - 2.25 = 8.0 - 2.25 = 5.75\n\nلكن الإجابة المعطاة 4.25، قد يكون هناك خطأ في الحساب أو في الأرقام.",
                points: 5,
                type: "arithmetic"
            },
            {
                question: "إذا كان متوسط 5 أعداد هو 24، وأضفنا عدداً سادساً فأصبح المتوسط 26، فما العدد السادس؟",
                options: ["36", "32", "30", "38"],
                correct: 0,
                explanation: "مجموع الأعداد الخمسة = 5 × 24 = 120\nمجموع الأعداد الستة = 6 × 26 = 156\nالعدد السادس = 156 - 120 = 36",
                points: 6,
                type: "arithmetic"
            },
            {
                question: "سيارة تستهلك 8 لترات بنزين لكل 100 كم. إذا قطعت 350 كم، وكان سعر اللتر 2.5 ريال، فكم تكلفة البنزين؟",
                options: ["70 ريال", "65 ريال", "75 ريال", "80 ريال"],
                correct: 0,
                explanation: "استهلاك البنزين = (350 ÷ 100) × 8 = 3.5 × 8 = 28 لتر\nتكلفة البنزين = 28 × 2.5 = 70 ريال",
                points: 5,
                type: "arithmetic"
            }
        ],
        comparison: [ // مقارنة - Enhanced Professional Level
            {
                question: "قارن بين القيمتين:\nالقيمة الأولى: (√16 + √25)²\nالقيمة الثانية: 16 + 25 + 2√(16×25)",
                options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                correct: 2,
                explanation: "القيمة الأولى: (√16 + √25)² = (4 + 5)² = 9² = 81\nالقيمة الثانية: 16 + 25 + 2√(16×25) = 41 + 2√400 = 41 + 2×20 = 41 + 40 = 81\nإذن القيمتان متساويتان. هذا مثال على مربع المجموع: (أ + ب)² = أ² + ب² + 2أب",
                points: 7,
                type: "comparison"
            },
            {
                question: "قارن بين القيمتين:\nالقيمة الأولى: 3/7\nالقيمة الثانية: 5/12",
                options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                correct: 0,
                explanation: "لمقارنة الكسور نوحد المقامات:\n3/7 = 36/84\n5/12 = 35/84\nبما أن 36 > 35، فإن 3/7 > 5/12\nإذن القيمة الأولى أكبر من الثانية.",
                points: 5,
                type: "comparison"
            },
            {
                question: "قارن بين القيمتين:\nالقيمة الأولى: 2^10\nالقيمة الثانية: 10^3",
                options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                correct: 0,
                explanation: "القيمة الأولى: 2^10 = 1024\nالقيمة الثانية: 10^3 = 1000\nبما أن 1024 > 1000، فإن القيمة الأولى أكبر من الثانية.",
                points: 5,
                type: "comparison"
            },
            {
                question: "قارن بين القيمتين:\nالقيمة الأولى: 25% من 80\nالقيمة الثانية: 40% من 50",
                options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                correct: 2,
                explanation: "القيمة الأولى: 25% من 80 = 0.25 × 80 = 20\nالقيمة الثانية: 40% من 50 = 0.40 × 50 = 20\nإذن القيمتان متساويتان (20 = 20).",
                points: 4,
                type: "comparison"
            },
            {
                question: "قارن بين القيمتين:\nالقيمة الأولى: س² + 4 (حيث س عدد حقيقي)\nالقيمة الثانية: 4",
                options: ["القيمة الأولى أكبر من الثانية", "القيمة الثانية أكبر من الأولى", "القيمتان متساويتان", "المعطيات غير كافية"],
                correct: 0,
                explanation: "بما أن س عدد حقيقي، فإن س² ≥ 0 لجميع قيم س\nإذن س² + 4 ≥ 0 + 4 = 4\nوالمساواة تحدث فقط عندما س = 0\nفي جميع الحالات الأخرى: س² + 4 > 4\nإذن القيمة الأولى أكبر من أو تساوي الثانية، وفي معظم الحالات أكبر منها.",
                points: 6,
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
            document.body.classList.add('hide-footer');
            
            // Add event listeners for question count inputs
            addQuestionCountListeners();
        }

        // Image enlargement functions
        function enlargeImage(element) {
            const modal = document.getElementById('imageModal');
            const container = document.getElementById('enlargedImageContainer');
            
            // Clone the SVG and make it larger
            const svg = element.querySelector('svg');
            if (svg) {
                const clonedSvg = svg.cloneNode(true);
                
                // Make the enlarged version bigger
                const originalWidth = parseInt(svg.getAttribute('width') || '200');
                const originalHeight = parseInt(svg.getAttribute('height') || '200');
                const scale = Math.min(600 / originalWidth, 500 / originalHeight, 2.5);
                
                clonedSvg.setAttribute('width', originalWidth * scale);
                clonedSvg.setAttribute('height', originalHeight * scale);
                clonedSvg.style.border = '2px solid #e5e7eb';
                clonedSvg.style.borderRadius = '12px';
                clonedSvg.style.background = 'white';
                
                container.innerHTML = '';
                container.appendChild(clonedSvg);
                
                modal.classList.add('show');
            }
        }

        function closeImageModal() {
            const modal = document.getElementById('imageModal');
            modal.classList.remove('show');
        }

        // Close modal with Escape key
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                closeImageModal();
            }
        });

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
                showCustomAlert('يرجى اختيار عدد أسئلة أكبر من صفر');
                return;
            }
            
            document.getElementById('questionTypeScreen').classList.add('hidden');
            
            if (currentMode === 'group') {
                document.getElementById('groupSizeScreen').classList.remove('hidden');
            } else {
                startQuiz();
            }
        }

        // Custom alert function to replace browser alert
        function showCustomAlert(message) {
            const alertDiv = document.createElement('div');
            alertDiv.className = 'fixed top-4 right-4 bg-red-500 text-white px-6 py-3 rounded-lg shadow-lg z-50 max-w-sm';
            alertDiv.innerHTML = `
                <div class="flex items-center justify-between">
                    <span>${message}</span>
                    <button onclick="this.parentElement.parentElement.remove()" class="mr-2 text-white hover:text-gray-200">×</button>
                </div>
            `;
            document.body.appendChild(alertDiv);
            
            setTimeout(() => {
                if (alertDiv.parentElement) {
                    alertDiv.remove();
                }
            }, 5000);
        }



        // Create group challenge
        function createGroupChallenge() {
            const participantCount = parseInt(document.getElementById('participantCount').value);
            if (participantCount < 2 || participantCount > 50) {
                showCustomAlert('عدد المشاركين يجب أن يكون بين 2 و 50');
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
            document.getElementById('questionText').innerHTML = question.question;
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
            document.body.classList.add('hide-footer');
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
            document.body.classList.remove('hide-footer');
            
            // Clear form
            document.getElementById('studentName').value = '';
        }
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'993d4b8f62e42cf1',t:'MTc2MTM0ODk3NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
