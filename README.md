<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق اللغة العربية المتكامل</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
    
    <style>
        /* === التنسيقات العامة === */
        body { margin: 0; padding: 0; background-color: #f4f7f9; font-family: 'Cairo', sans-serif; direction: rtl; }
        .screen { display: none; padding: 40px; min-height: 100vh; }
        .screen.active { 
            display: flex; 
            flex-direction: column; 
            align-items: center; 
            /* لا تضع justify-content: center إلا في شاشة الدخول */
        }
        .card { background-color: white; padding: 30px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1); width: 100%; max-width: 800px; margin-top: 20px; }
        .back-button { align-self: flex-start; margin-bottom: 20px; background: #607D8B; color: white; padding: 10px 15px; border: none; border-radius: 5px; cursor: pointer; font-weight: bold; }
        
        /* === شاشة تسجيل الدخول === */
        #login-screen { justify-content: center; }
        #login-screen h1 { color: #1565C0; margin-bottom: 30px; }
        #login-screen input[type="text"] { width: 100%; padding: 15px; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 8px; font-size: 1.1em; }
        #login-screen button { background-color: #4CAF50; color: white; padding: 15px 30px; border: none; border-radius: 8px; cursor: pointer; font-size: 1.2em; }

        /* === الشاشة الرئيسية (القائمة) === */
        #main-menu .card { max-width: 900px; }
        #main-menu h1 { color: #1565C0; margin-bottom: 30px; text-align: center; }
        .section-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; width: 100%; margin-top: 20px; }
        .section-card { padding: 30px; border-radius: 15px; text-align: center; font-size: 1.3em; font-weight: bold; cursor: pointer; transition: transform 0.2s, box-shadow 0.2s; color: white; }
        .section-card:hover { transform: translateY(-5px); box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2); }
        .section-card[data-section="sorter"] { background-color: #1565C0; } /* ترتيب الكلمة والجملة */
        .section-card[data-section="mcq"] { background-color: #FF9800; } /* الاختيار من متعدد */
        .section-card[data-section="fill"] { background-color: #E91E63; } /* أكمل الفراغ */
        .section-card[data-section="grammar"] { background-color: #4CAF50; } /* قواعد وتصحيح */

        /* === قسم الترتيب (الآلية التي طورناها) === */
        .word-bank { display: flex; flex-wrap: wrap; gap: 15px; padding: 20px; border: 1px solid #ddd; background-color: #fcfcfc; border-radius: 8px; min-height: 80px; margin-bottom: 20px; }
        .word-card { cursor: pointer; padding: 12px 18px; border: 1px solid #CCCCCC; border-radius: 30px; background-color: #F5F5F5; transition: all 0.2s ease; font-size: 18px; font-weight: 600; position: relative; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05); }
        .word-card.selected { background-color: #B3E5FC; color: #000; border-color: #B3E5FC; transform: translateY(-2px); box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15); }
        .word-card .order-badge { position: absolute; top: -10px; right: -10px; background-color: #1565C0; color: white; border-radius: 50%; width: 28px; height: 28px; display: flex; justify-content: center; align-items: center; font-size: 16px; font-weight: bold; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2); z-index: 10; }
        .sentence-area { margin: 20px 0; padding: 20px; border: 2px dashed #B0BEC5; min-height: 70px; display: flex; gap: 10px; flex-wrap: wrap; border-radius: 8px; background-color: #f9f9f9; }
        .sentence-area .placeholder { color: #90A4AE; font-style: italic; font-size: 18px; align-self: center; }
        .controls { display: flex; gap: 15px; justify-content: center; margin-top: 20px; }
        .check-button, .reset-button { padding: 12px 25px; border: none; border-radius: 8px; cursor: pointer; font-size: 16px; font-weight: bold; transition: all 0.3s; }
        .check-button { background-color: #4CAF50; color: white; }
        .reset-button { background-color: #FF9800; color: white; }
        .feedback { font-weight: bold; margin-top: 25px; padding: 15px; border-radius: 8px; text-align: center; font-size: 18px; }
        .feedback.correct { background-color: #C8E6C9; color: #2E7D32; }
        .feedback.incorrect { background-color: #FFCDD2; color: #C62828; }
        
        /* زر النطق (جديد) */
        .speak-btn { background: none; border: none; cursor: pointer; margin-right: 5px; color: #1565C0; font-size: 1.5em; vertical-align: middle; }
    </style>
</head>
<body>

    <div id="login-screen" class="screen active">
        <div class="card">
            <h1>مرحباً بك في تطبيق اللغة العربية</h1>
            <p>الرجاء إدخال اسم الطالبة للبدء:</p>
            <input type="text" id="student-name" placeholder="اسم الطالبة">
            <button onclick="goToMenu()">ابدأ</button>
        </div>
    </div>

    <div id="main-menu" class="screen">
        <div class="card">
            <h1 id="welcome-message"></h1>
            <h2>الرجاء اختيار القسم المطلوب:</h2>
            <div class="section-grid">
                <div class="section-card" data-section="sorter" onclick="goToSection('sorter')">
                    ترتيب الكلمة والجملة 🔢
                </div>
                <div class="section-card" data-section="mcq" onclick="goToSection('mcq')">
                    الاختيار من متعدد ✔️
                </div>
                <div class="section-card" data-section="fill" onclick="goToSection('fill')">
                    أكمل الفراغ ✍️
                </div>
                <div class="section-card" data-section="grammar" onclick="goToSection('grammar')">
                    قواعد وتصحيح 📚
                </div>
            </div>
        </div>
    </div>

    <div id="sorter-screen" class="screen">
        <button class="back-button" onclick="goToMenu()">عودة للقائمة</button>
        <div class="card">
            <h2 id="sorter-title">عنوان التمرين سيظهر هنا</h2>
            
            <div id="sorter-word-bank" class="word-bank"></div>
            
            <div id="sorter-sentence-area" class="sentence-area">
                <span class="placeholder">انقر على الكلمات بالترتيب الصحيح...</span>
            </div>
            
            <div class="controls">
                <button id="sorter-check-button" class="check-button">تحقق</button>
                <button id="sorter-reset-button" class="reset-button">إعادة الترتيب</button>
                <button id="sorter-next-button" class="check-button" style="background-color:#007bff; display:none;">التمرين التالي</button>
            </div>
            <p id="sorter-feedback" class="feedback"></p>
        </div>
    </div>

    <div id="mcq-screen" class="screen">
        <button class="back-button" onclick="goToMenu()">عودة للقائمة</button>
        <div class="card">
            <h2>قسم الاختيار من متعدد</h2>
            <p>هذا القسم جاهز لاستقبال أسئلة الاختيار من متعدد (MCQ). يمكنك إضافة منطق الأسئلة هنا.</p>
        </div>
    </div>

    <div id="fill-screen" class="screen">
        <button class="back-button" onclick="goToMenu()">عودة للقائمة</button>
        <div class="card">
            <h2>قسم أكمل الفراغ (يشمل إكمال الكلمة والجملة)</h2>
            <p>هذا القسم جاهز لاستقبال أسئلة إكمال الكلمات أو الفراغات في الجمل. يمكنك إضافة خانات الإدخال ومنطق المقارنة هنا.</p>
        </div>
    </div>
    
    <div id="grammar-screen" class="screen">
        <button class="back-button" onclick="goToMenu()">عودة للقائمة</button>
        <div class="card">
            <h2>قسم قواعد وتصحيح</h2>
            <p>هذا القسم جاهز لاستقبال أسئلة تصحيح الأخطاء النحوية أو الصرفية. يمكنك إضافة محتوى هذا النوع من الأسئلة هنا.</p>
        </div>
    </div>


    <script>
        /* === منطق JavaScript: التنقل وإدارة الأقسام === */
        
        let currentScreenId = 'login-screen';
        let studentName = '';

        // دوال التنقل
        const navigate = (targetId) => {
            document.getElementById(currentScreenId).classList.remove('active');
            document.getElementById(targetId).classList.add('active');
            currentScreenId = targetId;
        };

        const goToMenu = () => {
            navigate('main-menu');
        };

        const goToSection = (sectionName) => {
            navigate(sectionName + '-screen');
            if (sectionName === 'sorter') {
                 // عند الدخول لقسم الترتيب، يتم تحميل التمرين الأول
                 loadSorterExercise('1'); 
            }
        };
        
        // دالة البدء وتسجيل الاسم
        const goToMenu = () => {
            const nameInput = document.getElementById('student-name');
            studentName = nameInput.value.trim();

            if (studentName) {
                document.getElementById('welcome-message').textContent = `أهلاً بك، ${studentName}!`;
                navigate('main-menu');
            } else {
                alert('الرجاء إدخال الاسم للبدء.');
            }
        };

        // **********************************************
        // منطق قسم ترتيب الكلمة والجملة (Sorter Logic)
        // **********************************************

        // دالة النطق (Text-to-Speech)
        const speakWord = (word) => {
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(word);
                utterance.lang = 'ar-SA'; 
                speechSynthesis.speak(utterance);
            } else {
                console.warn("المتصفح لا يدعم ميزة نطق النص.");
            }
        };

        const SORTER_EXERCISES = {
            '1': { title: "ترتيب الجملة: السفر", correctOrder: ["سافر", "محمد", "إلى", "جدة"], type: 'sentence' },
            '2': { title: "ترتيب الكلمة: فعل الأمر", correctOrder: ["ن", "ط", "ق"], type: 'word' },
            '3': { title: "ترتيب الجملة: الرياضة", correctOrder: ["الرياضة", "تقوي", "الجسم"], type: 'sentence' }
        };
        
        let currentSorterExerciseId = '1';
        let sorterUserOrder = [];

        const sorterWordBank = document.getElementById('sorter-word-bank');
        const sorterSentenceArea = document.getElementById('sorter-sentence-area');
        const sorterCheckButton = document.getElementById('sorter-check-button');
        const sorterResetButton = document.getElementById('sorter-reset-button');
        const sorterNextButton = document.getElementById('sorter-next-button');
        const sorterFeedbackElement = document.getElementById('sorter-feedback');
        const sorterTitle = document.getElementById('sorter-title');
        const sorterPlaceholder = sorterSentenceArea.querySelector('.placeholder');

        const resetSorterGame = () => {
            sorterUserOrder = [];
            sorterSentenceArea.innerHTML = '';
            if (sorterPlaceholder) {
                sorterSentenceArea.appendChild(sorterPlaceholder);
                sorterPlaceholder.style.display = 'block';
            }
            // إعادة تعيين الكلمات البصرية
            const wordCards = Array.from(sorterWordBank.children);
            wordCards.forEach(card => {
                card.classList.remove('selected');
                card.style.backgroundColor = '';
                const badge = card.querySelector('.order-badge');
                if (badge) { card.removeChild(badge); }
            });
            sorterFeedbackElement.textContent = '';
            sorterFeedbackElement.className = 'feedback';
            sorterNextButton.style.display = 'none';
            sorterCheckButton.style.display = 'inline-block';
            sorterResetButton.style.display = 'inline-block';
        };

        const loadSorterExercise = (exerciseId) => {
            const exercise = SORTER_EXERCISES[exerciseId];
            if (!exercise) return;

            currentSorterExerciseId = exerciseId;
            resetSorterGame(); 
            
            // 1. تحديث العنوان
            sorterTitle.textContent = exercise.title;
            
            // 2. مسح وتوليد الكلمات/الأحرف الجديدة
            sorterWordBank.innerHTML = '';
            const itemsToShuffle = [...exercise.correctOrder]; 
            
            itemsToShuffle.sort(() => Math.random() - 0.5).forEach(item => {
                const card = document.createElement('div');
                card.classList.add('word-card');
                card.setAttribute('data-word', item);
                card.textContent = item;
                card.addEventListener('click', handleSorterClick); // ربط النقر
                sorterWordBank.appendChild(card);
            });
        };

        const handleSorterClick = (event) => {
            const card = event.currentTarget;
            const item = card.getAttribute('data-word');

            if (card.classList.contains('selected')) {
                // نطق الكلمة/الحرف عند النقر مجدداً (أو النطق التلقائي عند أول نقرة)
                speakWord(item); 
                return;
            }

            sorterUserOrder.push(item);
            
            // التحديث البصري والترقيم
            card.classList.add('selected');
            
            const badge = document.createElement('span');
            badge.classList.add('order-badge');
            badge.textContent = sorterUserOrder.length; 
            card.appendChild(badge);

            if (sorterPlaceholder) { sorterPlaceholder.style.display = 'none'; }

            // إنشاء نسخة للـ sentenceArea وجعلها غير قابلة للنقر
            const orderedCard = card.cloneNode(true);
            orderedCard.style.cursor = 'default';
            orderedCard.removeEventListener('click', handleSorterClick); 
            sorterSentenceArea.appendChild(orderedCard);
            
            sorterFeedbackElement.textContent = '';
            sorterFeedbackElement.className = 'feedback';

            // النطق عند إضافة الكلمة
            speakWord(item); 
        };

        sorterCheckButton.addEventListener('click', () => {
            const CORRECT_ORDER = SORTER_EXERCISES[currentSorterExerciseId].correctOrder;

            if (sorterUserOrder.length !== CORRECT_ORDER.length) {
                sorterFeedbackElement.textContent = 'الرجاء إكمال الترتيب أولاً.';
                sorterFeedbackElement.className = 'feedback incorrect';
                return;
            }

            const isCorrect = sorterUserOrder.every((item, index) => item === CORRECT_ORDER[index]);

            if (isCorrect) {
                sorterFeedbackElement.textContent = '🏆 أحسنتِ! الترتيب صحيح وممتاز.';
                sorterFeedbackElement.className = 'feedback correct';
                
                Array.from(sorterSentenceArea.children).forEach(card => {
                    card.style.backgroundColor = '#C8E6C9';
                });
                
                // إظهار زر التمرين التالي
                sorterNextButton.style.display = 'inline-block';
                sorterCheckButton.style.display = 'none';
                
            } else {
                sorterFeedbackElement.textContent = '❌ هناك خطأ في الترتيب. حاولي مرة أخرى!';
                sorterFeedbackElement.className = 'feedback incorrect';
            }
        });
        
        sorterResetButton.addEventListener('click', resetSorterGame);

        sorterNextButton.addEventListener('click', () => {
            const nextId = (parseInt(currentSorterExerciseId) + 1).toString();
            if (SORTER_EXERCISES[nextId]) {
                loadSorterExercise(nextId);
            } else {
                sorterFeedbackElement.textContent = '🎉 انتهت جميع التمارين في هذا القسم!';
                sorterNextButton.style.display = 'none';
            }
        });

        // **********************************************
        // بدء التطبيق
        // **********************************************
        
        document.addEventListener('DOMContentLoaded', () => {
            // يتم تحميل شاشة الدخول أولاً بشكل افتراضي
            document.getElementById('login-screen').classList.add('active');
        });
    </script>
</body>
</html>
