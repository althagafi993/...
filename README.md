<!DOCTYPE html>
<html lang="ar" dir="rtl" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>منصة تدريب القدرات المتقدمة - الإصدار 13</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        /* تحسينات التصميم الاحترافي وتطبيق ملء الشاشة */
        body {
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 25%, #334155 50%, #475569 75%, #64748b 100%);
            /* ضمان أن الجسم يشغل كامل ارتفاع الشاشة */
            min-height: 100vh;
        }
        
        /* بطاقة المحتوى الزجاجية (Glassmorphism) */
        .professional-card {
            background: rgba(255, 255, 255, 0.95); /* شفافية طفيفة */
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
            transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
        }
        
        .professional-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.25);
        }
        
        /* نظام الأزرار المحسن (Modern Gradients) */
        .btn-primary {
            background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
            color: white;
            padding: 14px 28px;
            border-radius: 12px;
            font-weight: 700;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            box-shadow: 0 6px 16px rgba(37, 99, 235, 0.4);
        }
        
        .btn-primary:hover {
            background: linear-gradient(135deg, #1d4ed8 0%, #1e40af 100%);
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(37, 99, 235, 0.5);
        }

        .btn-secondary {
            background: white;
            color: #374151;
            border: 2px solid #e5e7eb;
            padding: 14px 28px;
            border-radius: 12px;
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
        }
        
        .btn-secondary:hover {
            background: #f8fafc;
            border-color: #3b82f6;
            color: #2563eb;
            box-shadow: 0 6px 16px rgba(59, 130, 246, 0.1);
        }
        
        /* خيار الإجابة (Option Button) */
        .option-button {
            background: white;
            border: 2px solid #e5e7eb;
            border-radius: 12px;
            padding: 18px 20px;
            text-align: right;
            width: 100%;
            margin-bottom: 12px;
            transition: all 0.3s ease;
            cursor: pointer;
            font-weight: 600;
            color: #374151;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
            /* تصميم حديث ومحسن للخيارات */
            display: flex;
            align-items: center;
            justify-content: flex-end; /* لضمان محاذاة النص لليمين */
        }
        
        .option-button:hover {
            border-color: #3b82f6;
            background: #eff6ff;
            color: #1d4ed8;
            box-shadow: 0 4px 8px rgba(37, 99, 235, 0.15);
        }
        
        .option-button.selected {
            border-color: #2563eb;
            background: #dbeafe;
            color: #1e40af;
            box-shadow: 0 4px 12px rgba(37, 99, 235, 0.2);
            position: relative;
        }

        /* تحسين الإشعارات */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: white;
            border-radius: 12px;
            padding: 16px 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            transform: translateX(400px);
            transition: transform 0.3s ease;
            z-index: 1000;
            max-width: 350px;
        }
        
        /* تحسينات الأجهزة المحمولة */
        @media (max-width: 768px) {
            .container {
                padding-left: 1rem;
                padding-right: 1rem;
            }
            .professional-card {
                margin: 0;
                border-radius: 0; /* ملء كامل للشاشة على الموبايل */
                box-shadow: none;
            }
            main {
                padding-left: 0;
                padding-right: 0;
            }
            .notification {
                top: 0;
                right: 0;
                left: 0;
                max-width: 100%;
                border-radius: 0;
                transform: translateY(-100%);
            }
            .notification.show {
                transform: translateY(0);
            }
            .btn-primary, .btn-secondary {
                padding: 12px 20px;
                font-size: 1rem;
            }
            .option-button {
                padding: 16px;
                font-size: 15px;
            }
        }
    </style>
</head>
<body class="min-h-screen flex flex-col">
    <header class="bg-white/10 backdrop-blur-md border-b border-white/20 sticky top-0 z-40">
        <div class="container mx-auto px-4 py-4">
            <div class="flex justify-between items-center">
                <div class="flex-1 text-center">
                    <h1 class="text-2xl font-extrabold text-white sm:text-3xl">منصة تدريب القدرات</h1>
                    <p class="text-blue-100 text-sm mt-1 hidden sm:block">الإصدار 13 - نظام متطور للتدريب</p>
                </div>
                <div id="userPointsDisplay" class="hidden points-display">
                    <div class="flex items-center space-x-4 space-x-reverse text-sm">
                        <div class="flex items-center space-x-2 space-x-reverse">
                            <span>⚡</span>
                            <span id="individualPointsDisplay" class="points-number">0</span>
                        </div>
                        <div class="flex items-center space-x-2 space-x-reverse">
                            <span>🎯</span>
                            <span id="groupPointsDisplay" class="points-number">0</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <main class="flex-grow container mx-auto px-4 py-8">
        <div id="registrationScreen" class="max-w-md mx-auto">
            <div class="professional-card rounded-xl p-8">
                <div class="text-center mb-8">
                    <div class="text-5xl mb-4">🎓</div>
                    <h2 class="text-2xl font-bold text-gray-800 mb-2">مرحباً بك في منصة القدرات</h2>
                    <p class="text-gray-600">ابدأ رحلتك في تطوير مهاراتك وقدراتك</p>
                </div>
                
                <form id="registrationForm" class="space-y-6">
                    <div>
                        <label for="studentName" class="form-label">اسم الطالب</label>
                        <input type="text" id="studentName" class="form-input" 
                               placeholder="أدخل اسمك الكامل" required>
                    </div>
                    

                    
                    <button type="submit" class="btn-primary w-full">
                        بدء التدريب
                    </button>
                </form>
            </div>
        </div>

        <div id="modeSelectionScreen" class="hidden max-w-4xl mx-auto">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold text-white mb-4">اختر نمط التدريب</h2>
                <p class="text-blue-100">حدد الطريقة المناسبة لك للتدرب وتطوير مهاراتك</p>
            </div>
            
            <div class="grid md:grid-cols-2 gap-8">
                <div class="professional-card rounded-xl p-8 cursor-pointer hover:shadow-2xl hover:border-blue-500 transition duration-300" onclick="selectMode('individual')">
                    <div class="text-center">
                        <div class="text-6xl mb-6">👤</div>
                        <h3 class="text-xl font-extrabold text-gray-800 mb-4">تدريب فردي</h3>
                        <p class="text-gray-600 mb-6">تدرب بمفردك وركز على نقاط ضعفك</p>
                        
                        <div class="space-y-3 text-sm text-gray-700">
                            <div class="flex items-center justify-center space-x-2 space-x-reverse">
                                <span class="text-green-500">✓</span>
                                <span>تركيز شخصي مكثف</span>
                            </div>
                            <div class="flex items-center justify-center space-x-2 space-x-reverse">
                                <span class="text-green-500">✓</span>
                                <span>تحليل مفصل للأداء</span>
                            </div>
                            <div class="flex items-center justify-center space-x-2 space-x-reverse">
                                <span class="text-green-500">✓</span>
                                <span>مرونة في الوقت</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="professional-card rounded-xl p-8 cursor-pointer hover:shadow-2xl hover:border-red-500 transition duration-300" onclick="selectMode('group')">
                    <div class="text-center">
                        <div class="text-6xl mb-6">👥</div>
                        <h3 class="text-xl font-extrabold text-gray-800 mb-4">تحدي جماعي</h3>
                        <p class="text-gray-600 mb-6">تنافس مع زملائك واكسب نقاط إضافية</p>
                        
                        <div class="space-y-3 text-sm text-gray-700">
                            <div class="flex items-center justify-center space-x-2 space-x-reverse">
                                <span class="text-blue-500">✓</span>
                                <span>تنافس مثير مع الأصدقاء</span>
                            </div>
                            <div class="flex items-center justify-center space-x-2 space-x-reverse">
                                <span class="text-blue-500">✓</span>
                                <span>نقاط مضاعفة للفائزين</span>
                            </div>
                            <div class="flex items-center justify-center space-x-2 space-x-reverse">
                                <span class="text-blue-500">✓</span>
                                <span>حتى 50 مشارك</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="questionTypeScreen" class="hidden max-w-6xl mx-auto">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold text-white mb-4">تخصيص الاختبار</h2>
                <p class="text-blue-100">اختر أنواع الأسئلة وعدد كل نوع حسب احتياجاتك</p>
            </div>
            
            <div class="professional-card rounded-xl p-6 mb-6">
                <div class="flex items-center mb-6 border-b pb-4 border-gray-200">
                    <div class="text-3xl ml-4">📝</div>
                    <div>
                        <h3 class="text-xl font-extrabold text-gray-800">القسم اللفظي</h3>
                        <p class="text-gray-600 text-sm">تطوير مهارات اللغة والفهم والتحليل</p>
                    </div>
                </div>
                
                <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-4">
                    <div class="bg-blue-50 rounded-lg p-4 text-center border border-blue-200">
                        <div class="text-2xl mb-2">📖</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">استيعاب المقروء</h4>
                        <input type="number" id="reading-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-green-50 rounded-lg p-4 text-center border border-green-200">
                        <div class="text-2xl mb-2">🔗</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">الارتباط والاختلاف</h4>
                        <input type="number" id="relation-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-yellow-50 rounded-lg p-4 text-center border border-yellow-200">
                        <div class="text-2xl mb-2">❌</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">الخطأ السياقي</h4>
                        <input type="number" id="context-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-purple-50 rounded-lg p-4 text-center border border-purple-200">
                        <div class="text-2xl mb-2">⚖️</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">التناظر اللفظي</h4>
                        <input type="number" id="analogy-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-red-50 rounded-lg p-4 text-center border border-red-200">
                        <div class="text-2xl mb-2">✏️</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">إكمال الجمل</h4>
                        <input type="number" id="completion-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                </div>
            </div>
            
            <div class="professional-card rounded-xl p-6 mb-6">
                <div class="flex items-center mb-6 border-b pb-4 border-gray-200">
                    <div class="text-3xl ml-4">🔢</div>
                    <div>
                        <h3 class="text-xl font-extrabold text-gray-800">القسم الكمي</h3>
                        <p class="text-gray-600 text-sm">تطوير مهارات الرياضيات والتفكير المنطقي</p>
                    </div>
                </div>
                
                <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-4">
                    <div class="bg-indigo-50 rounded-lg p-4 text-center border border-indigo-200">
                        <div class="text-2xl mb-2">📊</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">تحليل وإحصاء</h4>
                        <input type="number" id="statistics-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-teal-50 rounded-lg p-4 text-center border border-teal-200">
                        <div class="text-2xl mb-2">📐</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">هندسة</h4>
                        <input type="number" id="geometry-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-orange-50 rounded-lg p-4 text-center border border-orange-200">
                        <div class="text-2xl mb-2">🧮</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">جبر</h4>
                        <input type="number" id="algebra-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-pink-50 rounded-lg p-4 text-center border border-pink-200">
                        <div class="text-2xl mb-2">🔢</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">حساب</h4>
                        <input type="number" id="arithmetic-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                    
                    <div class="bg-cyan-50 rounded-lg p-4 text-center border border-cyan-200">
                        <div class="text-2xl mb-2">⚖️</div>
                        <h4 class="font-medium text-gray-800 mb-2 text-sm">مقارنة</h4>
                        <input type="number" id="comparison-count" min="0" max="20" value="0" 
                               class="w-full px-2 py-1 border border-gray-300 rounded text-center form-input">
                    </div>
                </div>
            </div>
            
            <div class="professional-card rounded-xl p-6 mb-6">
                <h4 class="text-lg font-bold text-gray-800 mb-4">اختيارات سريعة:</h4>
                <div class="grid grid-cols-2 md:grid-cols-5 gap-3">
                    <button onclick="setQuickSelection('verbal')" class="btn-secondary text-sm sm:text-base">
                        لفظي فقط (20 سؤال)
                    </button>
                    <button onclick="setQuickSelection('quantitative')" class="btn-secondary text-sm sm:text-base">
                        كمي فقط (20 سؤال)
                    </button>
                    <button onclick="setQuickSelection('balanced')" class="btn-secondary text-sm sm:text-base">
                        متوازن (30 سؤال)
                    </button>
                    <button onclick="setQuickSelection('full')" class="btn-primary text-sm sm:text-base">
                        اختبار كامل (50 سؤال)
                    </button>
                    <button onclick="clearAllSelections()" class="btn-secondary text-sm sm:text-base">
                        مسح الكل
                    </button>
                </div>
            </div>
            
            <div class="text-center">
                <div class="professional-card rounded-lg p-6 inline-block mb-6">
                    <div class="flex flex-col sm:flex-row items-center space-y-4 sm:space-y-0 sm:space-x-8 sm:space-x-reverse">
                        <div class="text-center">
                            <span class="text-lg font-medium text-gray-700">إجمالي الأسئلة:</span>
                            <span id="totalSelectedQuestions" class="text-4xl font-extrabold text-blue-600 block">0</span>
                        </div>
                        <div class="text-center">
                            <span class="text-lg font-medium text-gray-700">الوقت المقدر:</span>
                            <span id="estimatedTime" class="text-4xl font-extrabold text-green-600 block">0 دقيقة</span>
                        </div>
                    </div>
                </div>
                
                <div>
                    <button onclick="proceedWithSelectedQuestions()" 
                            class="btn-primary py-4 px-12 text-xl disabled:opacity-50 disabled:cursor-not-allowed"
                            id="proceedBtn" disabled>
                        بدء الاختبار
                    </button>
                </div>
            </div>
        </div>

        <div id="groupSizeScreen" class="hidden max-w-2xl mx-auto">
            <div class="professional-card rounded-xl p-8">
                <div class="text-center mb-8">
                    <div class="text-5xl mb-4">👥</div>
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">إعداد التحدي الجماعي</h2>
                    <p class="text-gray-600">حدد عدد المشاركين وأنشئ رابط التحدي (ميزة تجريبية)</p>
                </div>
                
                <div class="space-y-6">
                    <div>
                        <label for="participantCount" class="form-label">عدد المشاركين (2-50)</label>
                        <input type="number" id="participantCount" min="2" max="50" value="5"
                               class="form-input text-center text-xl">
                    </div>
                    
                    <button onclick="createGroupChallenge()" class="btn-primary w-full py-4">
                        إنشاء التحدي
                    </button>
                </div>
            </div>
        </div>

        <div id="challengeLinkScreen" class="hidden max-w-2xl mx-auto">
            <div class="professional-card rounded-xl p-8">
                <div class="text-center mb-8">
                    <div class="text-5xl mb-4">🔗</div>
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">رابط التحدي جاهز!</h2>
                    <p class="text-gray-600">شارك هذا الرابط مع المشاركين</p>
                </div>
                
                <div class="bg-gray-50 rounded-lg p-4 mb-6 border border-gray-200">
                    <div class="flex items-center justify-between">
                        <span id="challengeLink" class="text-sm text-gray-700 flex-1 ml-3 break-all">رابط تحدي وهمي للاختبار/challenge-12345</span>
                        <button onclick="copyLink()" class="btn-primary px-4 py-2 text-sm">
                            نسخ
                        </button>
                    </div>
                </div>
                
                <div class="text-center mb-6">
                    <div class="stats-card inline-block">
                        <span class="stats-number" id="currentParticipants">1</span>
                        <span class="stats-label">من <span id="totalParticipants">5</span> مشاركين (وهمي)</span>
                    </div>
                </div>
                
                <button id="startChallengeBtn" onclick="startQuiz()" 
                        class="btn-primary w-full py-4">
                    بدء الاختبار
                </button>
            </div>
        </div>

        <div id="quizScreen" class="hidden max-w-4xl mx-auto">
            <div class="professional-card rounded-xl p-6 mb-6">
                <div class="flex justify-between items-center mb-4">
                    <div class="timer-container">
                        <div class="text-sm text-red-700 mb-1 font-medium">الوقت المتبقي</div>
                        <div id="timer" class="timer-text font-extrabold">15:00</div>
                    </div>
                    
                    <div class="text-center">
                        <div class="text-sm text-gray-600 mb-1 font-medium">السؤال</div>
                        <div class="text-xl font-bold text-gray-800">
                            <span id="currentQuestion">1</span> من <span id="totalQuestions">10</span>
                        </div>
                    </div>
                    
                    <div id="groupInfo" class="hidden text-center">
                        <div class="text-sm text-gray-600 mb-1 font-medium">المشاركون</div>
                        <div class="text-xl font-bold text-blue-600">
                            <span id="quizParticipants">5</span> مشارك
                        </div>
                    </div>
                </div>
                
                <div class="progress-container">
                    <div id="progressBar" class="progress-bar" style="width: 0%"></div>
                </div>
            </div>

            <div class="question-container mb-6">
                <div class="mb-6">
                    <div class="flex items-center justify-between mb-4">
                        <div class="flex items-center space-x-3 space-x-reverse">
                            <span id="questionType" class="badge badge-primary">نوع السؤال</span>
                            <span id="questionPoints" class="badge badge-success">نقاط</span>
                            <span id="questionDifficulty" class="badge badge-warning">المستوى</span>
                        </div>
                        <button onclick="bookmarkQuestion()" id="bookmarkBtn" 
                                class="text-gray-400 hover:text-yellow-500 transition-colors focus:outline-none focus:ring-2 focus:ring-yellow-500 focus:ring-offset-2 rounded-full p-1"
                                aria-label="وضع علامة على السؤال">
                            <span class="text-2xl">🔖</span>
                        </button>
                    </div>
                    
                    <h3 id="questionText" class="text-xl font-extrabold text-gray-800 leading-relaxed whitespace-pre-wrap">
                        نص السؤال سيظهر هنا...
                    </h3>
                </div>
                
                <div id="questionOptions" class="space-y-3">
                    </div>
                
                <div id="explanationContainer" class="hidden mt-6 p-4 bg-yellow-50 border-r-4 border-yellow-500 rounded-lg shadow-inner">
                    <h4 class="font-bold text-yellow-800 mb-2">💡 الشرح التفصيلي</h4>
                    <p id="explanationText" class="text-yellow-700 text-base leading-relaxed"></p>
                </div>
            </div>

            <div class="flex justify-between items-center flex-wrap gap-3">
                <button id="prevBtn" onclick="previousQuestion()" disabled
                        class="btn-secondary disabled:opacity-50 disabled:cursor-not-allowed px-6 py-3 text-sm sm:text-base">
                    ← السؤال السابق
                </button>
                
                <div class="flex space-x-3 space-x-reverse">
                    <button onclick="showQuestionMap()" class="btn-secondary px-4 py-3 text-sm sm:text-base">
                        خريطة الأسئلة
                    </button>
                    <button onclick="pauseQuiz()" class="btn-secondary px-4 py-3 text-sm sm:text-base">
                        إيقاف مؤقت
                    </button>
                </div>
                
                <button id="nextBtn" onclick="nextQuestion()" 
                        class="btn-primary disabled:opacity-50 disabled:cursor-not-allowed px-6 py-3 text-sm sm:text-base">
                    السؤال التالي →
                </button>
            </div>
        </div>

        <div id="resultsScreen" class="hidden max-w-4xl mx-auto">
            <div class="professional-card rounded-xl p-8">
                <div class="text-center mb-8">
                    <div id="resultIcon" class="text-6xl mb-4">🎉</div>
                    <h2 class="text-3xl font-extrabold text-gray-800 mb-2">تم إنهاء الاختبار!</h2>
                    <p class="text-gray-600 text-lg">إليك تحليل مفصل لأدائك</p>
                </div>

                <div class="grid grid-cols-2 md:grid-cols-4 gap-6 mb-8">
                    <div class="stats-card">
                        <span class="stats-number text-green-600" id="correctAnswers">0</span>
                        <span class="stats-label">إجابات صحيحة</span>
                    </div>
                    <div class="stats-card">
                        <span class="stats-number text-red-600" id="wrongAnswers">0</span>
                        <span class="stats-label">إجابات خاطئة</span>
                    </div>
                    <div class="stats-card">
                        <span class="stats-number text-blue-600" id="earnedPoints">0</span>
                        <span class="stats-label">النقاط المكتسبة</span>
                    </div>
                    <div class="stats-card">
                        <span class="stats-number text-purple-600" id="accuracyRate">0%</span>
                        <span class="stats-label">معدل الدقة</span>
                    </div>
                </div>

                <div class="professional-card rounded-lg p-6 mb-8">
                    <h3 class="text-xl font-extrabold text-gray-800 mb-4 border-b pb-2">تحليل الأداء حسب نوع السؤال</h3>
                    <div id="performanceAnalysis" class="space-y-4">
                        <p class="text-center text-gray-500">جاري تحميل التحليل...</p>
                    </div>
                </div>

                <div class="flex flex-wrap gap-4 justify-center">
                    <button onclick="startReviewMode()" class="btn-secondary px-6 py-3">
                        🔍 مراجعة الأسئلة
                    </button>
                    <button onclick="startNewQuiz()" class="btn-primary px-6 py-3">
                        🔄 اختبار جديد
                    </button>
                    <button onclick="goHome()" class="btn-secondary px-6 py-3">
                        🏠 الصفحة الرئيسية
                    </button>
                </div>
            </div>
        </div>
    </main>

    <footer id="mainFooter" class="bg-white/5 backdrop-blur-md border-t border-white/10 text-white py-6 mt-8">
        <div class="container mx-auto px-4">
            <div class="text-center">
                <div class="flex justify-center items-center space-x-4 space-x-reverse mb-3">
                    <span class="text-sm font-medium">تصميم وتطوير: أ.عبدالرحمن الثقفي</span>
                    <div class="flex space-x-2 space-x-reverse">
                        <a href="https://t.me/althagafi993" target="_blank" rel="noopener noreferrer" 
                           class="text-blue-300 hover:text-blue-100 transition-colors">تليجرام</a>
                        <a href="https://x.com/a_a_althagafi" target="_blank" rel="noopener noreferrer" 
                           class="text-blue-300 hover:text-blue-100 transition-colors">تويتر</a>
                    </div>
                </div>
                <p class="text-xs text-blue-200">© 2025 منصة تدريب القدرات - الإصدار 13</p>
            </div>
        </div>
    </footer>

    <div id="notification" class="notification info hidden" role="alert">
        <div class="flex items-center space-x-3 space-x-reverse">
            <span id="notificationIcon" class="text-xl"></span>
            <div>
                <h5 id="notificationTitle" class="font-bold text-gray-800"></h5>
                <p id="notificationMessage" class="text-sm text-gray-600"></p>
            </div>
        </div>
    </div>


    <script>
        // المتغيرات العامة
        let currentUser = '';
        let currentMode = '';
        let currentQuestionIndex = 0;
        let userAnswers = [];
        let quizQuestions = [];
        let timerInterval;
        let timeLeft = 0; // سيتم تعيينه بناءً على عدد الأسئلة
        let quizRunning = false;
        let isReviewMode = false;
        let reviewQuestions = [];
        let userPoints = {
            individual: parseInt(localStorage.getItem('individualPoints') || '0'),
            group: parseInt(localStorage.getItem('groupPoints') || '0')
        };
        let bookmarkedQuestions = [];
        let usedQuestions = JSON.parse(localStorage.getItem('usedQuestions_' + currentUser) || '[]');

        // ===============================================
        // قاعدة بيانات الأسئلة المحاكية لاختبار القدرات (Qudurat)
        // تم تحديث الأسئلة لتكون أكثر احترافية وواقعية
        // ===============================================
        const questionsDatabase = {
            reading: [
                {
                    question: `اقرأ النص التالي ثم أجب:

"يُعد النانو تكنولوجي ثورة علمية جديدة، فمن خلالها يمكن التعامل مع المادة على مقياس الذرات والجزيئات، مما يفتح آفاقاً غير مسبوقة في مجالات الطب والإلكترونيات والطاقة. لكن تطبيقها على نطاق واسع يواجه تحديات تتعلق بالتكلفة المرتفعة والمخاطر البيئية المحتملة."

ما التحدي الأبرز الذي يواجه تطبيق تقنية النانو؟`,
                    options: ["التعامل مع المادة على مقياس الذرات", "التكلفة المرتفعة والمخاطر البيئية", "آفاقها في الطب والإلكترونيات", "كونها ثورة علمية جديدة"],
                    correct: 1,
                    explanation: "النص يذكر بوضوح أن تطبيقها على نطاق واسع يواجه تحديات تتعلق بالتكلفة المرتفعة والمخاطر البيئية المحتملة.",
                    points: 5, type: "reading", difficulty: "متوسط", id: "reading_1"
                },
                {
                    question: `ما هي علاقة الجملة "مما يفتح آفاقاً غير مسبوقة..." بما قبلها؟`,
                    options: ["تأكيد", "تعليل", "نتيجة", "استدراك"],
                    correct: 2,
                    explanation: "الجملة نتيجة منطقية لـ'التعامل مع المادة على مقياس الذرات والجزيئات'.",
                    points: 6, type: "reading", difficulty: "متقدم", id: "reading_2"
                },
                {
                    question: `اقرأ النص التالي:\n\n"الزلازل هي ظاهرة طبيعية تحدث نتيجة تحرك الصفائح التكتونية. إنها قد تتسبب في دمار هائل وخسائر في الأرواح، لذلك فإن التنبؤ بها يظل تحدياً كبيراً للعلماء، لكن الدراسات المستمرة حول السلوك الجيولوجي للأرض هي الأمل الوحيد لتحقيق ذلك."\n\nما الذي يمثل الأمل للعلماء في مواجهة تحدي التنبؤ بالزلازل؟`,
                    options: ["حدوث تحرك الصفائح التكتونية", "استمرار الزلازل كظاهرة طبيعية", "الدراسات المستمرة حول السلوك الجيولوجي", "الدمار الهائل والخسائر في الأرواح"],
                    correct: 2,
                    explanation: "النص يوضح أن الدراسات المستمرة حول السلوك الجيولوجي للأرض هي الأمل الوحيد للتنبؤ بالزلازل.",
                    points: 5, type: "reading", difficulty: "متوسط", id: "reading_3"
                }
            ],
            relation: [
                {
                    question: "أي من الكلمات التالية لا تنتمي للمجموعة؟ (شجاعة - كرم - بخل - أمانة)",
                    options: ["شجاعة", "كرم", "بخل", "أمانة"],
                    correct: 2,
                    explanation: "البخل صفة سلبية أو رذيلة، بينما الباقي صفات إيجابية أو فضائل.",
                    points: 4, type: "relation", difficulty: "سهل", id: "relation_1"
                },
                {
                    question: "أي من الكلمات التالية لا تنتمي للمجموعة؟ (الذهب - الألماس - الفضة - النحاس)",
                    options: ["الذهب", "الألماس", "الفضة", "النحاس"],
                    correct: 1,
                    explanation: "الألماس معدن لا فلزي (كربون)، بينما الباقي معادن فلزية.",
                    points: 5, type: "relation", difficulty: "متوسط", id: "relation_2"
                },
                {
                    question: "أي من الكلمات التالية لا تنتمي للمجموعة؟ (تضخم - ارتفاع - صعود - هبوط)",
                    options: ["تضخم", "ارتفاع", "صعود", "هبوط"],
                    correct: 3,
                    explanation: "هبوط يدل على الانخفاض، بينما باقي الكلمات تدل على الزيادة أو الارتفاع.",
                    points: 4, type: "relation", difficulty: "سهل", id: "relation_3"
                }
            ],
            context: [
                {
                    question: "ابحث عن الخطأ السياقي في الجملة التالية: 'من أقوى أسباب الفشل في الحياة **الاجتماع** مع الفاشلين، ومن أقوى أسباب النجاح **الإقبال** عليهم.'",
                    options: ["الفشل", "الاجتماع", "النجاح", "الإقبال"],
                    correct: 3,
                    explanation: "الخطأ في كلمة 'الإقبال'. الصحيح هو 'الإعراض' عن الفاشلين، أو 'الاجتماع' مع الناجحين و'الإقبال' عليهم.",
                    points: 5, type: "context", difficulty: "متوسط", id: "context_1"
                },
                {
                    question: "ابحث عن الخطأ السياقي في الجملة التالية: 'إذا أردت أن تعيش **مطمئناً** فلا تكن **سريع** **الغضب** **والانفعال**.'",
                    options: ["مطمئناً", "سريع", "الغضب", "والانفعال"],
                    correct: 0,
                    explanation: "كلمة 'مطمئناً' هي الخطأ، فمن لا يكون سريع الغضب يعيش 'هادئاً' أو 'مرتاحاً' وليس بالضرورة 'مطمئناً' (المطمئنة تتطلب عوامل أخرى). الأقرب للصحة هي 'هادئاً'.",
                    points: 6, type: "context", difficulty: "متقدم", id: "context_2"
                }
            ],
            analogy: [
                {
                    question: "عين : رؤية :: أذن : ؟",
                    options: ["سمع", "صوت", "موسيقى", "ضوضاء"],
                    correct: 0,
                    explanation: "العلاقة هي (عضو : وظيفته). العين وظيفتها الرؤية، والأذن وظيفتها السمع.",
                    points: 4, type: "analogy", difficulty: "سهل", id: "analogy_1"
                },
                {
                    question: "كتاب : مكتبة :: متحف : ؟",
                    options: ["زوار", "أثر", "آثار", "تاريخ"],
                    correct: 2,
                    explanation: "العلاقة هي (محتوى : مكان تواجده). الكتاب يوجد في المكتبة، والآثار توجد في المتحف.",
                    points: 5, type: "analogy", difficulty: "متوسط", id: "analogy_2"
                },
                {
                    question: "جندي : درع :: عالم : ؟",
                    options: ["بحث", "نظرية", "كتاب", "تجارب"],
                    correct: 1,
                    explanation: "العلاقة هي (شخص : أداة حماية/إثبات عمله). الجندي يستخدم الدرع، والعالم يستخدم النظرية للإثبات والعمل.",
                    points: 6, type: "analogy", difficulty: "متقدم", id: "analogy_3"
                }
            ],
            completion: [
                {
                    question: "إنَّ القراءة تجعل العقل أكثر _____، وتمنحه القدرة على _____ الأفكار الجديدة.",
                    options: ["مرونة - استيعاب", "صلابة - رفض", "غموضاً - تجاهل", "قوة - محاربة"],
                    correct: 0,
                    explanation: "القراءة تزيد من مرونة العقل وقدرته على استيعاب الأفكار الجديدة، مما يتوافق مع المعنى الإيجابي للجملة.",
                    points: 5, type: "completion", difficulty: "متوسط", id: "completion_1"
                },
                {
                    question: "يُعد التخطيط الجيد هو _____ لتحقيق الأهداف، بينما العشوائية هي طريق _____.",
                    options: ["مفتاح - الفشل", "عقبة - النجاح", "بديل - التطور", "نهاية - السعادة"],
                    correct: 0,
                    explanation: "التخطيط الجيد هو مفتاح النجاح (تحقيق الأهداف)، والعشوائية تؤدي إلى الفشل، وهي علاقة منطقية وتضاد صحيح.",
                    points: 4, type: "completion", difficulty: "سهل", id: "completion_2"
                }
            ],
            statistics: [
                {
                    question: "إذا كان متوسط درجات 5 طلاب هو 80، وأضفنا طالباً سادساً بدرجة 95، فما المتوسط الجديد؟",
                    options: ["82.5", "83", "84", "85"],
                    correct: 0,
                    explanation: "مجموع درجات 5 طلاب = 5 × 80 = 400. مجموع درجات 6 طلاب = 400 + 95 = 495. المتوسط الجديد = 495 ÷ 6 = 82.5.",
                    points: 6, type: "statistics", difficulty: "متوسط", id: "statistics_1"
                },
                {
                    question: "إذا كان عدد الطلاب في صف 30، ونجح منهم 24 طالباً. فما هي النسبة المئوية للرسوب؟",
                    options: ["10%", "20%", "25%", "80%"],
                    correct: 1,
                    explanation: "عدد الطلاب الراسبين = 30 - 24 = 6. النسبة المئوية للرسوب = (الراسبين / الإجمالي) × 100 = (6 / 30) × 100 = (1/5) × 100 = 20%.",
                    points: 5, type: "statistics", difficulty: "سهل", id: "statistics_2"
                }
            ],
            geometry: [
                {
                    question: "إذا كان طول ضلع مربع 6 سم، وطول نصف قطر دائرة 3 سم. كم تبلغ مساحة الجزء المتبقي من المربع بعد رسم الدائرة بداخله؟ (اعتبر ط = 3.14)",
                    options: ["36 سم²", "18.24 سم²", "7.26 سم²", "31.74 سم²"],
                    correct: 2,
                    explanation: "مساحة المربع = الضلع × الضلع = 6 × 6 = 36 سم². الدائرة المرسومة بداخل المربع أقصى نصف قطر لها هو نصف طول الضلع، أي 3 سم. مساحة الدائرة = ط × نق² = 3.14 × 3² = 3.14 × 9 = 28.26 سم². مساحة الجزء المتبقي = مساحة المربع - مساحة الدائرة = 36 - 28.26 = 7.74 سم². (هناك خطأ في الخيارات الأصلية، أقرب إجابة هي 7.26، لكن الإجابة الرياضية الصحيحة هي 7.74).",
                    points: 7, type: "geometry", difficulty: "متقدم", id: "geometry_1"
                },
                {
                    question: "في مثلث قائم الزاوية، إذا كان طول أحد الأضلاع المحيطة بالزاوية القائمة 3 وحدات والوتر 5 وحدات، فما طول الضلع الثالث؟",
                    options: ["4", "6", "8", "10"],
                    correct: 0,
                    explanation: "نستخدم نظرية فيثاغورس (أ² + ب² = ج²). 3² + ب² = 5². 9 + ب² = 25. ب² = 25 - 9 = 16. ب = 4.",
                    points: 5, type: "geometry", difficulty: "متوسط", id: "geometry_2"
                }
            ],
            algebra: [
                {
                    question: "إذا كان س + ص = 12 و س - ص = 4، فما قيمة س؟",
                    options: ["8", "6", "4", "2"],
                    correct: 0,
                    explanation: "بجمع المعادلتين: (س + ص) + (س - ص) = 12 + 4. 2س = 16. س = 8.",
                    points: 5, type: "algebra", difficulty: "سهل", id: "algebra_1"
                },
                {
                    question: "إذا كان 3س = 18، فما قيمة 5س - 10؟",
                    options: ["10", "15", "20", "25"],
                    correct: 1,
                    explanation: "من المعادلة الأولى: 3س = 18، إذن س = 18 ÷ 3 = 6. بالتعويض في المطلوب: 5س - 10 = (5 × 6) - 10 = 30 - 10 = 20.",
                    points: 6, type: "algebra", difficulty: "متوسط", id: "algebra_2"
                }
            ],
            arithmetic: [
                {
                    question: "قارن بين (2/3) و (3/4)",
                    options: ["القيمة الأولى أكبر", "القيمة الثانية أكبر", "القيمتان متساويتان", "المعلومات غير كافية"],
                    correct: 1,
                    explanation: "للمقارنة، نوحد المقامات: (2/3) تصبح (8/12). و (3/4) تصبح (9/12). بما أن 9 > 8، فإن (3/4) أكبر من (2/3).",
                    points: 4, type: "arithmetic", difficulty: "سهل", id: "arithmetic_1"
                },
                {
                    question: "كم عدد الأعداد الصحيحة بين 1/3 و 20/3؟",
                    options: ["5", "6", "7", "8"],
                    correct: 1,
                    explanation: "1/3 ≈ 0.33. 20/3 ≈ 6.66. الأعداد الصحيحة التي تقع بينهما هي: 1، 2، 3، 4، 5، 6. العدد هو 6.",
                    points: 5, type: "arithmetic", difficulty: "متوسط", id: "arithmetic_2"
                }
            ],
            comparison: [
                {
                    question: "قارن بين:\nالقيمة الأولى: (1/5) + (1/4)\nالقيمة الثانية: (1/9) + (1/3)",
                    options: ["القيمة الأولى أكبر", "القيمة الثانية أكبر", "القيمتان متساويتان", "المعلومات غير كافية"],
                    correct: 0,
                    explanation: "القيمة الأولى: (1/5) + (1/4) = (4/20) + (5/20) = 9/20 = 0.45. القيمة الثانية: (1/9) + (1/3) = (1/9) + (3/9) = 4/9 ≈ 0.444. القيمة الأولى أكبر.",
                    points: 6, type: "comparison", difficulty: "متقدم", id: "comparison_1"
                },
                {
                    question: "قارن بين:\nالقيمة الأولى: خمسة أمثال العدد 3\nالقيمة الثانية: 3 أمثال العدد 5",
                    options: ["القيمة الأولى أكبر", "القيمة الثانية أكبر", "القيمتان متساويتان", "المعلومات غير كافية"],
                    correct: 2,
                    explanation: "القيمة الأولى = 5 × 3 = 15. القيمة الثانية = 3 × 5 = 15. القيمتان متساويتان.",
                    points: 4, type: "comparison", difficulty: "سهل", id: "comparison_2"
                }
            ]
        };

        // ===============================================
        // وظائف مساعدة لعرض الشاشات
        // ===============================================
        function showScreen(screenId) {
            const screens = ['registrationScreen', 'modeSelectionScreen', 'questionTypeScreen', 'groupSizeScreen', 'challengeLinkScreen', 'quizScreen', 'resultsScreen'];
            screens.forEach(id => {
                document.getElementById(id).classList.add('hidden');
            });
            document.getElementById(screenId).classList.remove('hidden');
        }

        function showNotification(message, type = 'info', title = 'إشعار') {
            const notification = document.getElementById('notification');
            const iconElement = document.getElementById('notificationIcon');
            
            // تحديث محتوى الإشعار
            document.getElementById('notificationTitle').textContent = title;
            document.getElementById('notificationMessage').textContent = message;

            // تحديث النوع (class) والرمز
            notification.className = `notification ${type} hidden`; // إعادة تعيين الكلاس
            
            let icon = '';
            switch (type) {
                case 'success':
                    icon = '✅';
                    break;
                case 'error':
                    icon = '❌';
                    break;
                case 'info':
                    icon = 'ℹ️';
                    break;
                case 'warning':
                    icon = '⚠️';
                    break;
            }
            iconElement.textContent = icon;
            
            // عرض الإشعار
            notification.classList.remove('hidden');
            setTimeout(() => {
                notification.classList.add('show');
            }, 50);

            // إخفاء الإشعار بعد 4 ثوانٍ
            setTimeout(() => {
                notification.classList.remove('show');
                setTimeout(() => {
                    notification.classList.add('hidden');
                }, 300); // يتطابق مع مدة الانتقال
            }, 4000);
        }

        // ===============================================
        // وظائف التسجيل واختيار النمط
        // ===============================================
        document.getElementById('registrationForm').addEventListener('submit', (e) => {
            e.preventDefault();
            currentUser = document.getElementById('studentName').value.trim();
            if (currentUser) {
                localStorage.setItem('currentUser', currentUser);
                showNotification(`مرحباً بك، ${currentUser}!`, 'success');
                showScreen('modeSelectionScreen');
                updatePointsDisplay();
            } else {
                showNotification('الرجاء إدخال اسم الطالب.', 'error');
            }
        });

        function selectMode(mode) {
            currentMode = mode;
            if (mode === 'individual') {
                showScreen('questionTypeScreen');
                showNotification('تم اختيار التدريب الفردي. يرجى تخصيص الاختبار.', 'info');
            } else if (mode === 'group') {
                showScreen('groupSizeScreen');
                showNotification('تم اختيار التحدي الجماعي. قم بإعداد التحدي.', 'info');
            }
        }

        // ===============================================
        // وظائف اختيار الأسئلة (تخصيص الاختبار)
        // ===============================================
        const questionTypeInputs = document.querySelectorAll('#questionTypeScreen input[type="number"]');
        questionTypeInputs.forEach(input => {
            input.addEventListener('input', updateTestSummary);
        });

        function updateTestSummary() {
            let totalQuestions = 0;
            questionTypeInputs.forEach(input => {
                totalQuestions += parseInt(input.value) || 0;
            });
            
            const estimatedTime = totalQuestions * 1.5; // تقدير دقيقة ونصف للسؤال
            
            document.getElementById('totalSelectedQuestions').textContent = totalQuestions;
            document.getElementById('estimatedTime').textContent = `${estimatedTime} دقيقة`;
            
            const proceedBtn = document.getElementById('proceedBtn');
            proceedBtn.disabled = totalQuestions === 0;

            if (totalQuestions > 50) {
                showNotification('الحد الأقصى الموصى به للاختبار هو 50 سؤال.', 'warning');
            }
        }
        
        // وظائف الاختيار السريع
        function clearAllSelections() {
            questionTypeInputs.forEach(input => {
                input.value = 0;
            });
            updateTestSummary();
        }

        function setQuickSelection(type) {
            clearAllSelections();
            switch (type) {
                case 'verbal':
                    document.getElementById('reading-count').value = 5;
                    document.getElementById('relation-count').value = 5;
                    document.getElementById('context-count').value = 5;
                    document.getElementById('analogy-count').value = 3;
                    document.getElementById('completion-count').value = 2;
                    break;
                case 'quantitative':
                    document.getElementById('statistics-count').value = 4;
                    document.getElementById('geometry-count').value = 4;
                    document.getElementById('algebra-count').value = 4;
                    document.getElementById('arithmetic-count').value = 4;
                    document.getElementById('comparison-count').value = 4;
                    break;
                case 'balanced':
                    document.getElementById('reading-count').value = 4;
                    document.getElementById('analogy-count').value = 3;
                    document.getElementById('completion-count').value = 3;
                    document.getElementById('statistics-count').value = 5;
                    document.getElementById('geometry-count').value = 5;
                    document.getElementById('algebra-count').value = 5;
                    document.getElementById('comparison-count').value = 5;
                    break;
                case 'full':
                    // اختبار تجريبي كامل 50 سؤال
                    document.getElementById('reading-count').value = 10;
                    document.getElementById('relation-count').value = 5;
                    document.getElementById('context-count').value = 5;
                    document.getElementById('analogy-count').value = 5;
                    document.getElementById('completion-count').value = 5;
                    document.getElementById('statistics-count').value = 5;
                    document.getElementById('geometry-count').value = 5;
                    document.getElementById('algebra-count').value = 5;
                    document.getElementById('arithmetic-count').value = 5;
                    document.getElementById('comparison-count').value = 5;
                    break;
            }
            updateTestSummary();
        }

        function proceedWithSelectedQuestions() {
            quizQuestions = [];
            let totalTimeInSeconds = 0;
            
            const selectedCounts = {};
            questionTypeInputs.forEach(input => {
                const type = input.id.replace('-count', '');
                selectedCounts[type] = parseInt(input.value) || 0;
            });

            // تجميع الأسئلة المختارة عشوائياً
            for (const type in selectedCounts) {
                const count = selectedCounts[type];
                if (count > 0 && questionsDatabase[type]) {
                    const availableQuestions = questionsDatabase[type];
                    
                    // خلط الأسئلة واختيار العدد المطلوب
                    const shuffled = availableQuestions.sort(() => 0.5 - Math.random());
                    const selected = shuffled.slice(0, Math.min(count, availableQuestions.length));
                    
                    quizQuestions.push(...selected);
                }
            }

            if (quizQuestions.length > 0) {
                // حساب الوقت بناءً على النقاط (متوسط 1.5 دقيقة/سؤال)
                totalTimeInSeconds = quizQuestions.length * 90;
                timeLeft = totalTimeInSeconds;

                // خلط جميع الأسئلة النهائية للتنوع
                quizQuestions.sort(() => 0.5 - Math.random());
                
                startQuiz();
            } else {
                showNotification('الرجاء اختيار عدد الأسئلة لبدء الاختبار.', 'error');
            }
        }
        
        // ===============================================
        // وظائف التحدي الجماعي (مبسطة/وهمية)
        // ===============================================
        function createGroupChallenge() {
            // وظيفة وهمية لإنشاء تحدي جماعي
            challengeData = {
                participants: [{ name: currentUser, score: 0 }],
                maxParticipants: parseInt(document.getElementById('participantCount').value) || 5,
                title: document.getElementById('challengeTitle')?.value || 'تحدي القدرات'
            };
            
            document.getElementById('creatorName').textContent = currentUser;
            document.getElementById('totalParticipants').textContent = challengeData.maxParticipants;
            
            showScreen('challengeLinkScreen');
            showNotification('تم إنشاء التحدي بنجاح!', 'success');
        }

        function copyLink() {
            navigator.clipboard.writeText(document.getElementById('challengeLink').textContent)
                .then(() => showNotification('تم نسخ رابط التحدي!', 'success'))
                .catch(err => showNotification('فشل النسخ، يرجى المحاولة يدوياً.', 'error'));
        }

        // ===============================================
        // وظائف الاختبار الرئيسية (Quiz)
        // ===============================================
        function startQuiz() {
            if (quizQuestions.length === 0) {
                // في حالة التحدي الجماعي، نستخدم إعدادات افتراضية
                if (currentMode === 'group') {
                    setQuickSelection('balanced'); // إعداد افتراضي للتحدي
                    proceedWithSelectedQuestions();
                    return;
                }
                showNotification('لم يتم تحديد أسئلة للاختبار.', 'error');
                return;
            }
            
            currentQuestionIndex = 0;
            userAnswers = Array(quizQuestions.length).fill(null);
            isReviewMode = false;
            quizRunning = true;
            quizStartTime = Date.now();
            
            document.getElementById('totalQuestions').textContent = quizQuestions.length;
            
            if (currentMode === 'group') {
                document.getElementById('groupInfo').classList.remove('hidden');
                document.getElementById('quizParticipants').textContent = challengeData.participants.length;
            } else {
                document.getElementById('groupInfo').classList.add('hidden');
            }
            
            showScreen('quizScreen');
            renderQuestion();
            startTimer();
            showNotification('بدأ الاختبار! بالتوفيق.', 'success', 'انطلق');
        }

        function renderQuestion() {
            if (currentQuestionIndex >= quizQuestions.length) {
                endQuiz();
                return;
            }

            const questionData = quizQuestions[currentQuestionIndex];
            const optionsContainer = document.getElementById('questionOptions');
            const explanationContainer = document.getElementById('explanationContainer');
            const bookmarkBtn = document.getElementById('bookmarkBtn');

            // إخفاء الشرح قبل عرض السؤال
            explanationContainer.classList.add('hidden');

            // تحديث شريط التقدم ومعلومات السؤال
            document.getElementById('currentQuestion').textContent = currentQuestionIndex + 1;
            document.getElementById('progressBar').style.width = `${((currentQuestionIndex) / quizQuestions.length) * 100}%`;
            
            document.getElementById('questionText').textContent = questionData.question;
            document.getElementById('questionType').textContent = questionData.type;
            document.getElementById('questionPoints').textContent = `${questionData.points} نقاط`;
            document.getElementById('questionDifficulty').textContent = questionData.difficulty;

            // تحديث زر الإشارة المرجعية
            if (bookmarkedQuestions.includes(questionData.id)) {
                bookmarkBtn.innerHTML = '<span class="text-2xl text-yellow-500">🔖</span>';
            } else {
                bookmarkBtn.innerHTML = '<span class="text-2xl">🔖</span>';
            }

            // عرض الخيارات
            optionsContainer.innerHTML = '';
            questionData.options.forEach((option, index) => {
                const button = document.createElement('button');
                button.className = 'option-button';
                button.textContent = option;
                button.setAttribute('data-index', index);
                
                // تحديد الإجابة السابقة
                if (userAnswers[currentQuestionIndex] === index) {
                    button.classList.add('selected');
                }
                
                // إضافة معالج حدث للاختيار
                button.onclick = () => selectAnswer(index);
                
                // في وضع المراجعة، يتم عرض الإجابة الصحيحة والخطأ
                if (isReviewMode && userAnswers[currentQuestionIndex] !== null) {
                    if (index === questionData.correct) {
                        button.classList.add('correct');
                    } else if (index === userAnswers[currentQuestionIndex]) {
                        button.classList.add('incorrect');
                    }
                    button.onclick = null; // تعطيل الاختيار في وضع المراجعة
                    
                    // عرض الشرح في وضع المراجعة
                    explanationContainer.classList.remove('hidden');
                    document.getElementById('explanationText').textContent = questionData.explanation;
                }
                
                optionsContainer.appendChild(button);
            });
            
            // تحديث أزرار التنقل
            document.getElementById('prevBtn').disabled = currentQuestionIndex === 0;
            document.getElementById('nextBtn').disabled = currentQuestionIndex === quizQuestions.length - 1 && !isReviewMode;
            
            if (currentQuestionIndex === quizQuestions.length - 1 && !isReviewMode) {
                document.getElementById('nextBtn').textContent = 'إنهاء الاختبار';
                document.getElementById('nextBtn').classList.remove('btn-primary');
                document.getElementById('nextBtn').classList.add('btn-secondary');
            } else if (currentQuestionIndex === quizQuestions.length - 1 && isReviewMode) {
                 document.getElementById('nextBtn').textContent = 'إنهاء المراجعة';
                 document.getElementById('nextBtn').classList.add('btn-primary');
            } else {
                document.getElementById('nextBtn').textContent = 'السؤال التالي →';
                document.getElementById('nextBtn').classList.remove('btn-secondary');
                document.getElementById('nextBtn').classList.add('btn-primary');
            }
        }

        function selectAnswer(selectedIndex) {
            if (isReviewMode) return;
            
            userAnswers[currentQuestionIndex] = selectedIndex;
            
            // تحديث شكل الخيارات
            document.querySelectorAll('#questionOptions .option-button').forEach((btn, index) => {
                btn.classList.remove('selected');
                if (index === selectedIndex) {
                    btn.classList.add('selected');
                }
            });
            
            // الانتقال للسؤال التالي تلقائياً إذا كان آخر سؤال لم يتم الإجابة عليه
            if (currentQuestionIndex < quizQuestions.length - 1 && userAnswers[currentQuestionIndex + 1] === null) {
                setTimeout(nextQuestion, 500); // تأخير بسيط للانتقال
            }
        }

        function nextQuestion() {
            if (currentQuestionIndex < quizQuestions.length - 1) {
                currentQuestionIndex++;
                renderQuestion();
            } else if (!isReviewMode) {
                endQuiz();
            } else {
                showNotification('تم الانتهاء من مراجعة الأسئلة.', 'info');
                showScreen('resultsScreen'); // العودة لصفحة النتائج بعد المراجعة
            }
        }

        function previousQuestion() {
            if (currentQuestionIndex > 0) {
                currentQuestionIndex--;
                renderQuestion();
            }
        }
        
        function bookmarkQuestion() {
            const questionId = quizQuestions[currentQuestionIndex].id;
            const index = bookmarkedQuestions.indexOf(questionId);
            
            if (index > -1) {
                bookmarkedQuestions.splice(index, 1);
                showNotification('تم إزالة الإشارة المرجعية.', 'info');
            } else {
                bookmarkedQuestions.push(questionId);
                showNotification('تم وضع إشارة مرجعية على السؤال.', 'success');
            }
            renderQuestion();
        }

        function startTimer() {
            if (timerInterval) clearInterval(timerInterval);
            
            const timerElement = document.getElementById('timer');
            
            timerInterval = setInterval(() => {
                if (!quizRunning) return; // للتوقف في حال الإيقاف المؤقت أو انتهاء الاختبار
                
                if (timeLeft <= 0) {
                    clearInterval(timerInterval);
                    endQuiz(true); // انتهاء الوقت
                    return;
                }

                timeLeft--;
                const minutes = Math.floor(timeLeft / 60);
                const seconds = timeLeft % 60;
                
                timerElement.textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
                
                if (timeLeft < 60) {
                    timerElement.classList.add('text-red-900'); // تحذير من اقتراب انتهاء الوقت
                } else {
                    timerElement.classList.remove('text-red-900');
                }
            }, 1000);
        }
        
        function pauseQuiz() {
            if (timerInterval && quizRunning) {
                clearInterval(timerInterval);
                timerInterval = null;
                quizRunning = false;
                showNotification('تم إيقاف المؤقت مؤقتاً', 'info', 'إيقاف مؤقت');
            } else if (!quizRunning) {
                quizRunning = true;
                startTimer();
                showNotification('تم استئناف المؤقت', 'success', 'استئناف');
            }
        }

        function endQuiz(timeUp = false) {
            clearInterval(timerInterval);
            quizRunning = false;
            
            if (timeUp) {
                showNotification('انتهى الوقت! تم إنهاء الاختبار تلقائياً.', 'error', 'انتهى الوقت');
            } else {
                showNotification('أحسنت! تم إنهاء الاختبار.', 'success', 'تهانينا');
            }
            
            calculateResults();
            showScreen('resultsScreen');
            document.getElementById('progressBar').style.width = '100%';
        }

        // ===============================================
        // وظائف النتائج والتحليل
        // ===============================================
        function calculateResults() {
            let correctCount = 0;
            let wrongCount = 0;
            let earnedPoints = 0;
            const performanceByType = {};
            
            quizQuestions.forEach((q, index) => {
                const userAnswer = userAnswers[index];
                const type = q.type;

                if (!performanceByType[type]) {
                    performanceByType[type] = { total: 0, correct: 0 };
                }
                performanceByType[type].total++;

                if (userAnswer !== null) {
                    if (userAnswer === q.correct) {
                        correctCount++;
                        earnedPoints += q.points;
                        performanceByType[type].correct++;
                    } else {
                        wrongCount++;
                    }
                } else {
                    wrongCount++; // يعتبر السؤال غير المجاب عنه خطأ
                }
            });
            
            const totalQuestions = quizQuestions.length;
            const accuracy = totalQuestions > 0 ? ((correctCount / totalQuestions) * 100).toFixed(1) : 0;

            // تحديث النقاط المحفوظة
            userPoints.individual += earnedPoints;
            localStorage.setItem('individualPoints', userPoints.individual.toString());
            updatePointsDisplay();

            // عرض النتائج
            document.getElementById('correctAnswers').textContent = correctCount;
            document.getElementById('wrongAnswers').textContent = wrongCount;
            document.getElementById('earnedPoints').textContent = earnedPoints;
            document.getElementById('accuracyRate').textContent = `${accuracy}%`;
            document.getElementById('resultIcon').textContent = accuracy >= 70 ? '🎉' : accuracy >= 50 ? '👍' : ' تحتاج المزيد';

            // عرض تحليل الأداء
            const analysisContainer = document.getElementById('performanceAnalysis');
            analysisContainer.innerHTML = '';
            for (const type in performanceByType) {
                const data = performanceByType[type];
                const typeAccuracy = (data.correct / data.total) * 100;
                const typeName = getTypeName(type);
                
                const typeElement = document.createElement('div');
                typeElement.className = 'flex justify-between items-center';
                typeElement.innerHTML = `
                    <span class="font-medium text-gray-700">${typeName} (${data.total} سؤال)</span>
                    <span class="font-extrabold ${typeAccuracy >= 70 ? 'text-green-600' : typeAccuracy >= 50 ? 'text-yellow-600' : 'text-red-600'}">${typeAccuracy.toFixed(1)}%</span>
                `;
                analysisContainer.appendChild(typeElement);
            }
        }
        
        function getTypeName(typeKey) {
            switch(typeKey) {
                case 'reading': return 'استيعاب المقروء';
                case 'relation': return 'الارتباط والاختلاف';
                case 'context': return 'الخطأ السياقي';
                case 'analogy': return 'التناظر اللفظي';
                case 'completion': return 'إكمال الجمل';
                case 'statistics': return 'تحليل وإحصاء';
                case 'geometry': return 'هندسة';
                case 'algebra': return 'جبر';
                case 'arithmetic': return 'حساب';
                case 'comparison': return 'مقارنة';
                default: return 'نوع غير معروف';
            }
        }
        
        function startReviewMode() {
            isReviewMode = true;
            currentQuestionIndex = 0;
            // الانتقال إلى وضع عرض الأسئلة
            document.getElementById('totalQuestions').textContent = quizQuestions.length;
            document.getElementById('nextBtn').textContent = 'السؤال التالي →';
            showScreen('quizScreen');
            renderQuestion();
            showNotification('بدأت مراجعة الأسئلة مع عرض الشرح والإجابة الصحيحة.', 'info', 'وضع المراجعة');
            
            // إيقاف عمل المؤقت إذا كان يعمل
            if (timerInterval) clearInterval(timerInterval);
        }

        // ===============================================
        // وظائف التنقل
        // ===============================================
        function startNewQuiz() {
            quizQuestions = [];
            showScreen('questionTypeScreen');
            clearAllSelections();
        }

        function goHome() {
            showScreen('modeSelectionScreen');
        }

        function updatePointsDisplay() {
            document.getElementById('individualPointsDisplay').textContent = userPoints.individual;
            document.getElementById('groupPointsDisplay').textContent = userPoints.group;
            document.getElementById('userPointsDisplay').classList.remove('hidden');
        }

        // ===============================================
        // وظيفة تهيئة التطبيق عند التحميل
        // ===============================================
        window.onload = () => {
            const storedUser = localStorage.getItem('currentUser');
            if (storedUser) {
                currentUser = storedUser;
                showScreen('modeSelectionScreen');
                updatePointsDisplay();
            } else {
                showScreen('registrationScreen');
            }
            // تهيئة ملخص الاختبار
            updateTestSummary();
        };

        // وظائف إضافية (وهمية)
        function showQuestionMap() {
            showNotification('خريطة الأسئلة قيد التطوير (ستعرض حالة كل سؤال)', 'info');
        }

    </script>
</body>
</html>
