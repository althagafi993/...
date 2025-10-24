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
        }
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        .card-hover {
            transition: all 0.3s ease;
        }
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }
        .pulse-animation {
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
        .question-card {
            background: linear-gradient(145deg, #ffffff, #f0f4f8);
            border: 2px solid #e2e8f0;
        }
        .correct-answer {
            background-color: #d4edda !important;
            border-color: #28a745 !important;
        }
        .wrong-answer {
            background-color: #f8d7da !important;
            border-color: #dc3545 !important;
        }
        .loading-spinner {
            border: 3px solid #f3f3f3;
            border-top: 3px solid #667eea;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="min-h-full bg-gray-50">
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
            <div class="bg-white rounded-xl shadow-lg p-8 card-hover">
                <div class="text-center mb-6">
                    <div class="text-6xl mb-4">📚</div>
                    <h2 class="text-2xl font-bold text-gray-800 mb-2">مرحباً بك</h2>
                    <p class="text-gray-600">ابدأ رحلتك في تطوير قدراتك</p>
                </div>
                <form id="registrationForm">
                    <div class="mb-6">
                        <label for="studentName" class="block text-sm font-medium text-gray-700 mb-2">اسم الطالب</label>
                        <input type="text" id="studentName" required 
                               class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                               placeholder="أدخل اسمك الكامل">
                    </div>
                    <button type="submit" 
                            class="w-full bg-gradient-to-r from-blue-600 to-purple-600 text-white py-3 px-6 rounded-lg font-medium hover:from-blue-700 hover:to-purple-700 transition-all duration-300">
                        ابدأ التدريب
                    </button>
                </form>
            </div>
        </div>

        <!-- Mode Selection Screen -->
        <div id="modeSelectionScreen" class="hidden max-w-4xl mx-auto">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">اختر نوع التدريب</h2>
                <p class="text-gray-600">حدد الطريقة التي تفضل التدرب بها</p>
            </div>
            
            <div class="grid md:grid-cols-2 gap-8">
                <!-- Individual Training -->
                <div class="bg-white rounded-xl shadow-lg p-8 card-hover cursor-pointer" onclick="selectMode('individual')">
                    <div class="text-center">
                        <div class="text-6xl mb-4">👤</div>
                        <h3 class="text-xl font-bold text-gray-800 mb-3">تدريب فردي</h3>
                        <p class="text-gray-600 mb-4">تدرب بمفردك وطور مهاراتك الشخصية</p>
                        <div class="bg-blue-50 rounded-lg p-3">
                            <p class="text-sm text-blue-700">✨ تركيز كامل على نقاط ضعفك</p>
                        </div>
                    </div>
                </div>

                <!-- Group Challenge -->
                <div class="bg-white rounded-xl shadow-lg p-8 card-hover cursor-pointer" onclick="selectMode('group')">
                    <div class="text-center">
                        <div class="text-6xl mb-4">👥</div>
                        <h3 class="text-xl font-bold text-gray-800 mb-3">تحدي جماعي</h3>
                        <p class="text-gray-600 mb-4">تنافس مع زملائك واكسب نقاط إضافية</p>
                        <div class="bg-green-50 rounded-lg p-3">
                            <p class="text-sm text-green-700">🏆 تنافس مع حتى 50 طالب</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Question Type Selection -->
        <div id="questionTypeScreen" class="hidden max-w-6xl mx-auto">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">اختر أنواع أسئلة القدرات</h2>
                <p class="text-gray-600">حدد الأنواع التي تريد التدرب عليها وعدد الأسئلة لكل نوع</p>
            </div>
            
            <!-- القسم اللفظي -->
            <div class="bg-white rounded-xl shadow-lg p-6 mb-6">
                <div class="flex items-center mb-6">
                    <div class="text-3xl ml-3">📝</div>
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
            <div class="bg-white rounded-xl shadow-lg p-6 mb-6">
                <div class="flex items-center mb-6">
                    <div class="text-3xl ml-3">🔢</div>
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
            <div class="bg-gray-50 rounded-xl p-6 mb-6">
                <h4 class="text-lg font-medium text-gray-800 mb-4">اختيارات سريعة:</h4>
                <div class="flex flex-wrap gap-3">
                    <button onclick="setQuickSelection('verbal')" 
                            class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                        لفظي فقط (20 سؤال)
                    </button>
                    <button onclick="setQuickSelection('quantitative')" 
                            class="bg-green-600 text-white px-4 py-2 rounded-lg hover:bg-green-700 transition-colors">
                        كمي فقط (20 سؤال)
                    </button>
                    <button onclick="setQuickSelection('balanced')" 
                            class="bg-purple-600 text-white px-4 py-2 rounded-lg hover:bg-purple-700 transition-colors">
                        متوازن (30 سؤال)
                    </button>
                    <button onclick="setQuickSelection('full')" 
                            class="bg-red-600 text-white px-4 py-2 rounded-lg hover:bg-red-700 transition-colors">
                        اختبار كامل (50 سؤال)
                    </button>
                    <button onclick="clearAllSelections()" 
                            class="bg-gray-600 text-white px-4 py-2 rounded-lg hover:bg-gray-700 transition-colors">
                        مسح الكل
                    </button>
                </div>
            </div>
            
            <div class="text-center">
                <div class="mb-4">
                    <span class="text-lg font-medium">إجمالي الأسئلة: </span>
                    <span id="totalSelectedQuestions" class="text-2xl font-bold text-blue-600">0</span>
                </div>
                
                <button onclick="proceedWithSelectedQuestions()" 
                        class="bg-gradient-to-r from-blue-600 to-purple-600 text-white py-3 px-8 rounded-lg font-medium hover:from-blue-700 hover:to-purple-700 transition-all duration-300 disabled:bg-gray-400 disabled:cursor-not-allowed"
                        id="proceedBtn" disabled>
                    المتابعة
                </button>
            </div>
        </div>



        <!-- Group Size Selection -->
        <div id="groupSizeScreen" class="hidden max-w-2xl mx-auto">
            <div class="bg-white rounded-xl shadow-lg p-8">
                <div class="text-center mb-6">
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">حدد عدد المشاركين</h2>
                    <p class="text-gray-600">كم طالب سيشارك في التحدي؟</p>
                </div>
                
                <div class="mb-6">
                    <label for="participantCount" class="block text-sm font-medium text-gray-700 mb-2">عدد المشاركين (2-50)</label>
                    <input type="number" id="participantCount" min="2" max="50" value="5"
                           class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent text-center text-xl">
                </div>
                
                <button onclick="createGroupChallenge()" 
                        class="w-full bg-gradient-to-r from-green-600 to-blue-600 text-white py-3 px-6 rounded-lg font-medium hover:from-green-700 hover:to-blue-700 transition-all duration-300">
                    إنشاء رابط التحدي
                </button>
            </div>
        </div>

        <!-- Challenge Link Screen -->
        <div id="challengeLinkScreen" class="hidden max-w-2xl mx-auto">
            <div class="bg-white rounded-xl shadow-lg p-8">
                <div class="text-center mb-6">
                    <div class="text-4xl mb-4">🔗</div>
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">رابط التحدي جاهز!</h2>
                    <p class="text-gray-600">شارك هذا الرابط مع زملائك</p>
                </div>
                
                <div class="bg-gray-50 rounded-lg p-4 mb-6">
                    <div class="flex items-center justify-between">
                        <span id="challengeLink" class="text-sm text-gray-700 flex-1 mr-3"></span>
                        <button onclick="copyLink()" class="bg-blue-600 text-white px-4 py-2 rounded-lg text-sm hover:bg-blue-700 transition-colors">
                            نسخ
                        </button>
                    </div>
                </div>
                
                <div class="text-center">
                    <div class="mb-4">
                        <span class="text-lg font-medium">المشاركون: </span>
                        <span id="currentParticipants" class="text-2xl font-bold text-blue-600">1</span>
                        <span class="text-lg"> من </span>
                        <span id="totalParticipants" class="text-2xl font-bold text-gray-800">5</span>
                    </div>
                    
                    <div id="participantsList" class="mb-6">
                        <div class="bg-green-50 rounded-lg p-3 mb-2">
                            <span class="text-green-700">✓ <span id="creatorName"></span> (أنت)</span>
                        </div>
                    </div>
                    
                    <button id="startChallengeBtn" onclick="startQuiz()" disabled
                            class="w-full bg-gray-400 text-white py-3 px-6 rounded-lg font-medium cursor-not-allowed">
                        انتظار المشاركين...
                    </button>
                </div>
            </div>
        </div>

        <!-- Quiz Screen -->
        <div id="quizScreen" class="hidden max-w-4xl mx-auto">
            <!-- Quiz Header -->
            <div class="bg-white rounded-xl shadow-lg p-6 mb-6">
                <div class="flex justify-between items-center">
                    <div class="flex items-center space-x-4 space-x-reverse">
                        <div class="text-2xl">⏱️</div>
                        <div>
                            <div class="text-sm text-gray-600">الوقت المتبقي</div>
                            <div id="timer" class="text-xl font-bold text-red-600">15:00</div>
                        </div>
                    </div>
                    
                    <div class="text-center">
                        <div class="text-sm text-gray-600">السؤال</div>
                        <div class="text-xl font-bold">
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
                        class="bg-gray-300 text-gray-500 px-6 py-3 rounded-lg font-medium cursor-not-allowed">
                    السؤال السابق
                </button>
                <button id="nextBtn" onclick="nextQuestion()" disabled
                        class="bg-gray-400 text-white px-6 py-3 rounded-lg font-medium cursor-not-allowed">
                    السؤال التالي
                </button>
            </div>
        </div>

        <!-- Results Screen -->
        <div id="resultsScreen" class="hidden max-w-4xl mx-auto">
            <div class="bg-white rounded-xl shadow-lg p-8">
                <div class="text-center mb-8">
                    <div id="resultIcon" class="text-6xl mb-4">🎉</div>
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">انتهى الاختبار!</h2>
                    <p class="text-gray-600">إليك نتائجك التفصيلية</p>
                </div>

                <!-- Score Summary -->
                <div class="grid md:grid-cols-3 gap-6 mb-8">
                    <div class="bg-green-50 rounded-lg p-6 text-center">
                        <div class="text-3xl font-bold text-green-600" id="correctAnswers">8</div>
                        <div class="text-sm text-green-700">إجابات صحيحة</div>
                    </div>
                    <div class="bg-red-50 rounded-lg p-6 text-center">
                        <div class="text-3xl font-bold text-red-600" id="wrongAnswers">2</div>
                        <div class="text-sm text-red-700">إجابات خاطئة</div>
                    </div>
                    <div class="bg-blue-50 rounded-lg p-6 text-center">
                        <div class="text-3xl font-bold text-blue-600" id="earnedPoints">40</div>
                        <div class="text-sm text-blue-700">النقاط المكتسبة</div>
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
                            class="bg-blue-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-blue-700 transition-colors">
                        طباعة النتيجة
                    </button>
                    <button onclick="startNewQuiz()" 
                            class="bg-green-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-green-700 transition-colors">
                        اختبار جديد
                    </button>
                    <button onclick="goHome()" 
                            class="bg-gray-600 text-white px-6 py-3 rounded-lg font-medium hover:bg-gray-700 transition-colors">
                        الصفحة الرئيسية
                    </button>
                </div>
            </div>
        </div>
    </main>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-8 mt-16">
        <div class="container mx-auto px-4">
            <div class="text-center">
                <div class="mb-4">
                    <p class="text-lg font-medium">تصميم أ.عبدالرحمن الثقفي</p>
                </div>
                <div class="flex justify-center space-x-6 space-x-reverse">
                    <a href="https://x.com/a_a_althagafi?t=SKoq7PoEIK_sP9WabZ7QYA&s=09" target="_blank" rel="noopener noreferrer" 
                       class="flex items-center space-x-2 space-x-reverse hover:text-blue-400 transition-colors">
                        <span>𝕏</span>
                        <span>تويتر</span>
                    </a>
                    <a href="https://t.me/althagafi993" target="_blank" rel="noopener noreferrer" 
                       class="flex items-center space-x-2 space-x-reverse hover:text-blue-400 transition-colors">
                        <span>📱</span>
                        <span>تليجرام</span>
                    </a>
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
                    question: "اقرأ النص التالي ثم أجب: 'التعليم هو أساس تقدم الأمم، فبه ترتقي الشعوب وتزدهر الحضارات. والمعلم هو حجر الزاوية في العملية التعليمية.' ما الفكرة الرئيسية للنص؟",
                    options: ["أهمية المعلم في التعليم", "التعليم أساس تقدم الأمم", "ازدهار الحضارات", "العملية التعليمية"],
                    correct: 1,
                    explanation: "الفكرة الرئيسية هي أن التعليم أساس تقدم الأمم، وباقي الجمل تدعم هذه الفكرة",
                    videoLink: "https://www.youtube.com/watch?v=reading1",
                    points: 4,
                    type: "reading"
                },
                {
                    question: "من النص السابق، ما دور المعلم حسب الكاتب؟",
                    options: ["هو الأساس في التعليم", "هو حجر الزاوية في العملية التعليمية", "هو سبب تقدم الأمم", "هو مطور الحضارات"],
                    correct: 1,
                    explanation: "النص يذكر صراحة أن المعلم هو حجر الزاوية في العملية التعليمية",
                    videoLink: "https://www.youtube.com/watch?v=reading2",
                    points: 3,
                    type: "reading"
                }
            ],
            relation: [ // الارتباط والاختلاف
                {
                    question: "أي من الكلمات التالية لا تنتمي للمجموعة؟",
                    options: ["قلم", "كتاب", "مسطرة", "تفاحة"],
                    correct: 3,
                    explanation: "تفاحة هي الوحيدة التي ليست أداة مدرسية",
                    videoLink: "https://www.youtube.com/watch?v=relation1",
                    points: 3,
                    type: "relation"
                },
                {
                    question: "ما العلاقة بين (طبيب - مستشفى)؟",
                    options: ["معلم - مدرسة", "طالب - جامعة", "مريض - دواء", "ممرض - عيادة"],
                    correct: 0,
                    explanation: "العلاقة هي مهنة ومكان العمل، فالطبيب يعمل في المستشفى والمعلم يعمل في المدرسة",
                    videoLink: "https://www.youtube.com/watch?v=relation2",
                    points: 4,
                    type: "relation"
                }
            ],
            context: [ // الخطأ السياقي
                {
                    question: "أي من الجمل التالية تحتوي على خطأ سياقي؟",
                    options: ["شربت الماء البارد في الصيف", "لبست المعطف الثقيل في الشتاء", "أكلت الآيس كريم في القطب الشمالي", "فتحت المظلة عند المطر"],
                    correct: 2,
                    explanation: "أكل الآيس كريم في القطب الشمالي غير منطقي بسبب البرد الشديد",
                    videoLink: "https://www.youtube.com/watch?v=context1",
                    points: 3,
                    type: "context"
                },
                {
                    question: "ما الجملة التي تحتوي على تناقض؟",
                    options: ["السيارة سريعة جداً", "الطائرة تطير في السماء", "السمك يسبح في الصحراء", "الطيور تغرد في الصباح"],
                    correct: 2,
                    explanation: "السمك لا يمكن أن يسبح في الصحراء لأنه يحتاج للماء",
                    videoLink: "https://www.youtube.com/watch?v=context2",
                    points: 3,
                    type: "context"
                }
            ],
            analogy: [ // التناظر اللفظي
                {
                    question: "قلم : كتابة = ؟",
                    options: ["سيارة : قيادة", "مفتاح : باب", "طعام : جوع", "نوم : تعب"],
                    correct: 0,
                    explanation: "القلم أداة للكتابة، والسيارة أداة للقيادة (وسيلة لتحقيق الغرض)",
                    videoLink: "https://www.youtube.com/watch?v=analogy1",
                    points: 4,
                    type: "analogy"
                },
                {
                    question: "شمس : نهار = قمر : ؟",
                    options: ["ليل", "نجوم", "ظلام", "سماء"],
                    correct: 0,
                    explanation: "الشمس ترتبط بالنهار، والقمر يرتبط بالليل",
                    videoLink: "https://www.youtube.com/watch?v=analogy2",
                    points: 3,
                    type: "analogy"
                }
            ],
            completion: [ // إكمال الجمل
                {
                    question: "المطالعة غذاء _____ كما أن الطعام غذاء _____",
                    options: ["العقل - الجسم", "الروح - النفس", "الفكر - الذهن", "الذاكرة - العضلات"],
                    correct: 0,
                    explanation: "المطالعة تغذي العقل والطعام يغذي الجسم",
                    videoLink: "https://www.youtube.com/watch?v=completion1",
                    points: 4,
                    type: "completion"
                },
                {
                    question: "لا يمكن للإنسان أن _____ دون أن _____",
                    options: ["ينجح - يجتهد", "يأكل - يشرب", "يسافر - يعود", "يحلم - ينام"],
                    correct: 0,
                    explanation: "النجاح يتطلب الاجتهاد، وهذا مبدأ منطقي",
                    videoLink: "https://www.youtube.com/watch?v=completion2",
                    points: 3,
                    type: "completion"
                }
            ],
            
            // القسم الكمي
            statistics: [ // تحليل وإحصاء
                {
                    question: "إذا كانت درجات 5 طلاب في اختبار هي: 80، 85، 90، 75، 95. ما المتوسط الحسابي؟",
                    options: ["85", "87", "83", "90"],
                    correct: 0,
                    explanation: "المتوسط = (80+85+90+75+95)÷5 = 425÷5 = 85",
                    videoLink: "https://www.youtube.com/watch?v=statistics1",
                    points: 4,
                    type: "statistics"
                },
                {
                    question: "في مجموعة البيانات: 10، 15، 20، 25، 30. ما الوسيط؟",
                    options: ["20", "15", "25", "18"],
                    correct: 0,
                    explanation: "الوسيط هو القيمة الوسطى عند ترتيب البيانات، وهو 20",
                    videoLink: "https://www.youtube.com/watch?v=statistics2",
                    points: 3,
                    type: "statistics"
                }
            ],
            geometry: [ // هندسة
                {
                    question: "إذا كان محيط المربع 24 سم، فما مساحته؟",
                    options: ["36 سم²", "24 سم²", "144 سم²", "48 سم²"],
                    correct: 0,
                    explanation: "طول الضلع = 24÷4 = 6 سم، المساحة = 6² = 36 سم²",
                    videoLink: "https://www.youtube.com/watch?v=geometry1",
                    points: 4,
                    type: "geometry"
                },
                {
                    question: "مثلث قائم الزاوية، طولا ضلعيه القائمين 3 سم و 4 سم. ما طول الوتر؟",
                    options: ["5 سم", "7 سم", "6 سم", "8 سم"],
                    correct: 0,
                    explanation: "باستخدام نظرية فيثاغورس: √(3²+4²) = √(9+16) = √25 = 5 سم",
                    videoLink: "https://www.youtube.com/watch?v=geometry2",
                    points: 5,
                    type: "geometry"
                }
            ],
            algebra: [ // جبر
                {
                    question: "إذا كان 2س + 5 = 13، فما قيمة س؟",
                    options: ["4", "3", "5", "6"],
                    correct: 0,
                    explanation: "2س = 13 - 5 = 8، إذن س = 8÷2 = 4",
                    videoLink: "https://www.youtube.com/watch?v=algebra1",
                    points: 3,
                    type: "algebra"
                },
                {
                    question: "إذا كان س² = 49، فما قيمة س؟",
                    options: ["±7", "7", "-7", "49"],
                    correct: 0,
                    explanation: "الجذر التربيعي لـ 49 هو ±7",
                    videoLink: "https://www.youtube.com/watch?v=algebra2",
                    points: 4,
                    type: "algebra"
                }
            ],
            arithmetic: [ // حساب
                {
                    question: "ما ناتج 15% من 200؟",
                    options: ["30", "25", "35", "20"],
                    correct: 0,
                    explanation: "15% من 200 = (15÷100) × 200 = 0.15 × 200 = 30",
                    videoLink: "https://www.youtube.com/watch?v=arithmetic1",
                    points: 3,
                    type: "arithmetic"
                },
                {
                    question: "إذا اشترى أحمد 3 كتب بـ 45 ريال، فكم سعر الكتاب الواحد؟",
                    options: ["15 ريال", "12 ريال", "18 ريال", "20 ريال"],
                    correct: 0,
                    explanation: "سعر الكتاب الواحد = 45÷3 = 15 ريال",
                    videoLink: "https://www.youtube.com/watch?v=arithmetic2",
                    points: 2,
                    type: "arithmetic"
                }
            ],
            comparison: [ // مقارنة
                {
                    question: "قارن بين: العمود أ: 3² + 4²، العمود ب: 5²",
                    options: ["العمود أ = العمود ب", "العمود أ > العمود ب", "العمود أ < العمود ب", "لا يمكن المقارنة"],
                    correct: 0,
                    explanation: "العمود أ: 3² + 4² = 9 + 16 = 25، العمود ب: 5² = 25، إذن هما متساويان",
                    videoLink: "https://www.youtube.com/watch?v=comparison1",
                    points: 4,
                    type: "comparison"
                },
                {
                    question: "قارن بين: العمود أ: 2/3، العمود ب: 0.67",
                    options: ["العمود أ > العمود ب", "العمود أ < العمود ب", "العمود أ = العمود ب", "لا يمكن المقارنة"],
                    correct: 0,
                    explanation: "2/3 = 0.666... وهو أكبر من 0.67 (خطأ في الحساب، الصحيح أن 2/3 ≈ 0.667 وهو أصغر من 0.67)",
                    videoLink: "https://www.youtube.com/watch?v=comparison2",
                    points: 3,
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
                proceedBtn.className = 'bg-gradient-to-r from-blue-600 to-purple-600 text-white py-3 px-8 rounded-lg font-medium hover:from-blue-700 hover:to-purple-700 transition-all duration-300';
            } else {
                proceedBtn.disabled = true;
                proceedBtn.className = 'bg-gradient-to-r from-blue-600 to-purple-600 text-white py-3 px-8 rounded-lg font-medium hover:from-blue-700 hover:to-purple-700 transition-all duration-300 disabled:bg-gray-400 disabled:cursor-not-allowed';
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
                    
                    // If we need more questions than available, repeat some
                    while (typeQuestions.length < count) {
                        typeQuestions = [...typeQuestions, ...questionsDatabase[type]];
                    }
                    
                    // Shuffle and select the required number
                    typeQuestions = typeQuestions.sort(() => Math.random() - 0.5).slice(0, count);
                    quizQuestions.push(...typeQuestions);
                }
            });
            
            // Shuffle all questions
            quizQuestions = quizQuestions.sort(() => Math.random() - 0.5);
            
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
                        <a href="${question.videoLink}" target="_blank" rel="noopener noreferrer" 
                           class="bg-red-600 text-white px-3 py-1 rounded text-sm hover:bg-red-700 transition-colors">
                            📹 شرح بالفيديو
                        </a>
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
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'993c9a7066ddf7ba',t:'MTc2MTM0MTcxOS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
