<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق الترتيب الذكي للجمل</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
    
    <style>
        /* === 1. تنسيقات CSS (التصميم والألوان) === */
        
        /* إعادة تعيين الأنماط الأساسية والخط */
        body {
            margin: 0;
            padding: 0;
            background-color: #f4f7f9;
            font-family: 'Cairo', sans-serif; 
        }

        /* حاوية الصفحة الكاملة (تقسيم جانبي ورئيسي) */
        .full-page-wrapper {
            display: flex; 
            width: 100%;
            min-height: 100vh;
            direction: rtl; /* اتجاه الكتابة من اليمين لليسار */
        }

        /* تنسيق القائمة الجانبية (Sidebar) */
        .sidebar {
            width: 250px;
            background-color: #ffffff;
            padding: 20px;
            border-left: 1px solid #eee;
            box-shadow: 2px 0 5px rgba(0, 0, 0, 0.05);
            padding-top: 50px; /* مسافة من الأعلى */
        }

        .sidebar h3 {
            color: #1565C0;
            margin-bottom: 15px;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
        }

        .sidebar ul {
            list-style: none;
            padding: 0;
        }

        .sidebar li {
            padding: 10px;
            margin-bottom: 5px;
            cursor: pointer;
            border-radius: 5px;
            transition: background-color 0.2s;
            font-weight: 500;
        }

        .sidebar li:hover:not(.active) {
            background-color: #e3f2fd;
        }

        .sidebar li.active {
            background-color: #1565C0;
            color: white;
            font-weight: bold;
        }

        /* تنسيق المحتوى الرئيسي (Main Content) */
        .content-area {
            flex-grow: 1; 
            padding: 30px;
        }

        .content-area h1 {
            text-align: center;
            color: #333;
            margin-bottom: 40px;
            font-size: 2.2em;
        }

        /* تنسيق حاوية التمرين */
        .exercise-container {
            background-color: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .exercise-container h2 {
            text-align: center;
            color: #555;
            margin-bottom: 25px;
            font-size: 1.6em;
        }

        /* منطقة الكلمات العشوائية */
        .word-bank {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            padding: 20px;
            border: 1px solid #ddd;
            background-color: #fcfcfc;
            border-radius: 8px;
            min-height: 80px;
            margin-bottom: 20px;
        }

        /* بطاقة الكلمة (الوضع الافتراضي) */
        .word-card {
            cursor: pointer;
            padding: 12px 18px;
            border: 1px solid #CCCCCC; 
            border-radius: 30px; 
            background-color: #F5F5F5; 
            transition: all 0.2s ease;
            font-size: 18px;
            font-weight: 600;
            position: relative; 
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
        }

        /* حالة اختيار الكلمة (التظليل الأزرق) */
        .word-card.selected {
            background-color: #B3E5FC; /* أزرق فاتح مريح */
            color: #000;
            border-color: #B3E5FC;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
        }

        /* أيقونة الترقيم (الشارة الزرقاء الداكنة) */
        .word-card .order-badge {
            position: absolute;
            top: -10px;
            right: -10px;
            background-color: #1565C0; /* أزرق غامق للتباين */
            color: white;
            border-radius: 50%;
            width: 28px;
            height: 28px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 16px;
            font-weight: bold;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
            z-index: 10;
        }

        /* منطقة الجملة المرتبة */
        .sentence-area {
            margin: 20px 0;
            padding: 20px;
            border: 2px dashed #B0BEC5; 
            min-height: 70px;
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            border-radius: 8px;
            background-color: #f9f9f9;
        }

        .sentence-area .placeholder {
            color: #90A4AE;
            font-style: italic;
            font-size: 18px;
            align-self: center; 
        }
        
        .sentence-area .word-card {
            cursor: default; 
            box-shadow: none; 
        }

        /* أزرار التحكم */
        .controls {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-top: 20px;
        }

        .check-button, .reset-button {
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s;
        }

        .check-button {
            background-color: #4CAF50; /* أخضر للتحقق */
            color: white;
        }

        .check-button:hover {
            background-color: #388E3C;
        }

        .reset-button {
            background-color: #FF9800; /* برتقالي للإعادة */
            color: white;
        }

        .reset-button:hover {
            background-color: #FB8C00;
        }

        /* رسائل التغذية الراجعة */
        .feedback {
            font-weight: bold;
            margin-top: 25px;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            font-size: 18px;
        }
        .feedback.correct {
            background-color: #C8E6C9; 
            color: #2E7D32; 
        }
        .feedback.incorrect {
            background-color: #FFCDD2; 
            color: #C62828; 
        }
    </style>
</head>
<body>
    
    <div class="full-page-wrapper">

        <aside class="sidebar">
            <h3>📖 التمارين المتاحة</h3>
            <ul>
                <li class="active" data-exercise="1">تمرين 1: السفر إلى جدة</li>
                <li data-exercise="2">تمرين 2: شروق الشمس</li>
                <li data-exercise="3">تمرين 3: الألوان الجميلة</li>
            </ul>
        </aside>

        <main class="content-area">
            <h1>تطبيق الترتيب الذكي للجمل</h1>
            
            <div class="exercise-container">
                <h2>عنوان التمرين سيظهر هنا</h2>
                
                <div id="word-bank" class="word-bank">
                    </div>

                <div id="sentence-area" class="sentence-area">
                    <span class="placeholder">انقر على الكلمات بالترتيب الصحيح...</span>
                </div>

                <div class="controls">
                    <button id="check-button" class="check-button">تحقق</button>
                    <button id="reset-button" class="reset-button">إعادة الترتيب</button>
                </div>

                <p id="feedback" class="feedback"></p>
            </div>
        </main>
    </div>

    <script>
        /* === 2. منطق JavaScript (الآلية التفاعلية وإدارة التمارين) === */
        document.addEventListener('DOMContentLoaded', () => {
            
            // ** 1. هيكل بيانات التمارين - يمكنك إضافة المزيد هنا **
            const EXERCISES = {
                '1': {
                    title: "تمرين 1: السفر إلى جدة",
                    correctOrder: ["سافر", "محمد", "إلى", "جدة"]
                },
                '2': {
                    title: "تمرين 2: شروق الشمس",
                    correctOrder: ["الشمس", "تشرق", "من", "الشرق"]
                },
                '3': {
                    title: "تمرين 3: الألوان الجميلة",
                    correctOrder: ["أحب", "الزهور", "ذات", "الألوان", "الجميلة"]
                }
            };
            
            let currentExerciseId = '1';
            let userOrder = [];

            // العناصر البرمجية الأساسية
            const wordBank = document.getElementById('word-bank');
            const sentenceArea = document.getElementById('sentence-area');
            const checkButton = document.getElementById('check-button');
            const resetButton = document.getElementById('reset-button');
            const feedbackElement = document.getElementById('feedback');
            const placeholder = sentenceArea.querySelector('.placeholder');
            
            // **********************************************
            // دوال التحكم
            // **********************************************

            // دالة لإعادة تعيين حالة التمرين
            const resetGame = () => {
                userOrder = [];
                sentenceArea.innerHTML = '';
                if (placeholder) {
                    sentenceArea.appendChild(placeholder);
                    placeholder.style.display = 'block';
                }
                
                // إعادة الكلمات في بنك الكلمات لحالتها الافتراضية
                const wordCards = Array.from(wordBank.children);
                wordCards.forEach(card => {
                    card.classList.remove('selected');
                    card.style.backgroundColor = '';
                    const badge = card.querySelector('.order-badge');
                    if (badge) {
                        card.removeChild(badge);
                    }
                });
                
                feedbackElement.textContent = '';
                feedbackElement.className = 'feedback';
            };


            // دالة لتحميل تمرين جديد
            const loadExercise = (exerciseId) => {
                const exercise = EXERCISES[exerciseId];
                if (!exercise) return;

                currentExerciseId = exerciseId;
                resetGame(); // إعادة تعيين اللعبة قبل التحميل
                
                // 1. تحديث العنوان
                document.querySelector('.exercise-container h2').textContent = exercise.title;
                
                // 2. مسح وتوليد الكلمات الجديدة
                wordBank.innerHTML = '';
                const wordsToShuffle = [...exercise.correctOrder]; 
                
                // توليد العناصر عشوائياً وربطها بـ Event Listener
                wordsToShuffle.sort(() => Math.random() - 0.5).forEach(word => {
                    const card = document.createElement('div');
                    card.classList.add('word-card');
                    card.setAttribute('data-word', word);
                    card.textContent = word;
                    card.addEventListener('click', handleWordClick); // ربط النقر
                    wordBank.appendChild(card);
                });
            };

            // دالة معالجة النقر (لبناء الجملة)
            const handleWordClick = (event) => {
                const card = event.currentTarget;
                const word = card.getAttribute('data-word');

                // منع النقر على الكلمة المختارة مسبقاً
                if (card.classList.contains('selected')) {
                    return;
                }

                userOrder.push(word);
                
                // التحديث البصري والترقيم
                card.classList.add('selected');
                
                const badge = document.createElement('span');
                badge.classList.add('order-badge');
                badge.textContent = userOrder.length; 
                card.appendChild(badge);

                // إخفاء النص التمهيدي
                if (placeholder) {
                    placeholder.style.display = 'none';
                }

                // إنشاء نسخة للـ sentenceArea وجعلها غير قابلة للنقر
                const orderedCard = card.cloneNode(true);
                orderedCard.style.cursor = 'default';
                orderedCard.removeEventListener('click', handleWordClick); 
                sentenceArea.appendChild(orderedCard);
                
                feedbackElement.textContent = '';
                feedbackElement.className = 'feedback';
            };

            // **********************************************
            // ربط الأزرار والأحداث
            // **********************************************
            
            // دالة التصحيح (عند النقر على "تحقق")
            checkButton.addEventListener('click', () => {
                const CORRECT_ORDER = EXERCISES[currentExerciseId].correctOrder;

                if (userOrder.length !== CORRECT_ORDER.length) {
                    feedbackElement.textContent = 'الرجاء إكمال الجملة أولاً.';
                    feedbackElement.className = 'feedback incorrect';
                    return;
                }

                const isCorrect = userOrder.every((word, index) => word === CORRECT_ORDER[index]);

                if (isCorrect) {
                    feedbackElement.textContent = '🏆 أحسنتِ! الترتيب صحيح وممتاز.';
                    feedbackElement.className = 'feedback correct';
                    
                    // تظليل كل الكلمات في منطقة الترتيب بالأخضر
                    Array.from(sentenceArea.children).forEach(card => {
                        card.style.backgroundColor = '#C8E6C9';
                    });
                    
                } else {
                    feedbackElement.textContent = '❌ هناك خطأ في الترتيب. حاولي مرة أخرى!';
                    feedbackElement.className = 'feedback incorrect';
                }
            });
            
            // ربط زر إعادة الترتيب
            resetButton.addEventListener('click', resetGame);

            // ** منطق التبديل بين التمارين (Sidebar Click) **
            document.querySelectorAll('.sidebar li').forEach(item => {
                item.addEventListener('click', (e) => {
                    const newId = e.target.getAttribute('data-exercise');
                    if (newId !== currentExerciseId) {
                        // تحديث الفئة النشطة
                        document.querySelector('.sidebar li.active').classList.remove('active');
                        e.target.classList.add('active');
                        
                        loadExercise(newId); // تحميل التمرين الجديد
                    }
                });
            });

            // تحميل التمرين الأول عند بدء التشغيل
            loadExercise(currentExerciseId);
        });
    </script>
</body>
</html>
