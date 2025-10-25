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
                    options: ["التعامل مع المادة على مقياس الذرات", "التكلفة المرتفعة والمخاطر البي
