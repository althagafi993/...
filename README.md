<!doctype html>
<html lang="ar" dir="rtl">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>تعليم القراءة للأطفال</title>
  <script src="/_sdk/data_sdk.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <style>
        body {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ffeef8 0%, #f8d7da 50%, #ffc1cc 100%);
            min-height: 100%;
            overflow-x: hidden;
        }

        html {
            height: 100%;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            min-height: 100%;
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
            background: linear-gradient(45deg, #ff69b4, #ff1493);
            color: white;
            padding: 20px;
            border-radius: 20px;
            box-shadow: 0 8px 25px rgba(255, 20, 147, 0.3);
        }

        .header h1 {
            margin: 0;
            font-size: 2.5rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .welcome-text {
            font-size: 1.2rem;
            margin-top: 10px;
            opacity: 0.9;
        }

        /* نموذج تسجيل الاسم */
        .name-registration {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(255, 105, 180, 0.2);
            text-align: center;
            margin-bottom: 20px;
        }

        .name-input {
            font-size: 1.5rem;
            padding: 15px 25px;
            border: 3px solid #ff69b4;
            border-radius: 25px;
            text-align: center;
            margin: 20px 0;
            width: 300px;
            max-width: 90%;
        }

        .name-input:focus {
            outline: none;
            border-color: #ff1493;
            box-shadow: 0 0 15px rgba(255, 20, 147, 0.3);
        }

        .start-btn {
            background: linear-gradient(45deg, #ff69b4, #ff1493);
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 25px;
            font-size: 1.3rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 20, 147, 0.3);
        }

        .start-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 20, 147, 0.4);
        }

        .game-area {
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(255, 105, 180, 0.2);
            margin-bottom: 20px;
        }

        .level-selector {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .level-btn {
            background: linear-gradient(45deg, #ff69b4, #ff1493);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 20, 147, 0.3);
        }

        .level-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 20, 147, 0.4);
        }

        .level-btn.active {
            background: linear-gradient(45deg, #ff1493, #dc143c);
            transform: scale(1.05);
        }

        .word-display {
            text-align: center;
            margin-bottom: 30px;
        }

        .current-word {
            font-size: 3rem;
            color: #ff1493;
            font-weight: bold;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(255, 20, 147, 0.3);
        }

        .word-meaning {
            font-size: 1.3rem;
            color: #666;
            margin-bottom: 20px;
        }

        .controls {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .control-btn {
            background: linear-gradient(45deg, #ff69b4, #ff1493);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 20, 147, 0.3);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .control-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 20, 147, 0.4);
        }

        .control-btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }

        .mic-btn {
            background: linear-gradient(45deg, #ff6b6b, #ee5a52);
            font-size: 1.2rem;
            animation: pulse 2s infinite;
        }

        .mic-btn.recording {
            background: linear-gradient(45deg, #ff4757, #ff3838);
            animation: recording 1s infinite;
        }

        .mic-btn.processing {
            background: linear-gradient(45deg, #ffa502, #ff6348);
            animation: processing 1s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        @keyframes recording {
            0% { box-shadow: 0 0 0 0 rgba(255, 71, 87, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(255, 71, 87, 0); }
            100% { box-shadow: 0 0 0 0 rgba(255, 71, 87, 0); }
        }

        @keyframes processing {
            0% { transform: scale(1) rotate(0deg); }
            50% { transform: scale(1.1) rotate(180deg); }
            100% { transform: scale(1) rotate(360deg); }
        }

        .drag-drop-area {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .letter-box, .word-box {
            background: linear-gradient(45deg, #ffc1cc, #ffb3ba);
            border: 3px dashed #ff69b4;
            border-radius: 15px;
            padding: 15px 20px;
            font-size: 1.5rem;
            font-weight: bold;
            color: #ff1493;
            cursor: pointer;
            transition: all 0.3s ease;
            min-width: 60px;
            text-align: center;
            user-select: none;
        }

        .letter-box:hover, .word-box:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255, 105, 180, 0.4);
        }

        .letter-box.dragging, .word-box.dragging {
            opacity: 0.5;
            transform: rotate(5deg);
        }

        .drop-zone {
            background: white;
            border: 3px dashed #ff69b4;
            border-radius: 15px;
            padding: 20px;
            margin: 10px;
            min-height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }

        .drop-zone.drag-over {
            background: linear-gradient(45deg, #ffeef8, #f8d7da);
            border-color: #ff1493;
            transform: scale(1.05);
        }

        .multiple-choice {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .choice-btn {
            background: linear-gradient(45deg, #ffc1cc, #ffb3ba);
            border: 3px solid #ff69b4;
            border-radius: 15px;
            padding: 20px;
            font-size: 1.3rem;
            font-weight: bold;
            color: #ff1493;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .choice-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255, 105, 180, 0.4);
            background: linear-gradient(45deg, #ff69b4, #ff1493);
            color: white;
        }

        .feedback {
            text-align: center;
            margin: 20px 0;
            font-size: 1.5rem;
            font-weight: bold;
            min-height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .success {
            color: #28a745;
            animation: bounce 0.6s ease-in-out;
        }

        .error {
            color: #dc3545;
            animation: shake 0.6s ease-in-out;
        }

        @keyframes bounce {
            0%, 20%, 53%, 80%, 100% { transform: translate3d(0,0,0); }
            40%, 43% { transform: translate3d(0,-30px,0); }
            70% { transform: translate3d(0,-15px,0); }
            90% { transform: translate3d(0,-4px,0); }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            10%, 30%, 50%, 70%, 90% { transform: translateX(-10px); }
            20%, 40%, 60%, 80% { transform: translateX(10px); }
        }

        .celebration {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1000;
        }

        .bubble {
            position: absolute;
            background: radial-gradient(circle, #ff69b4, #ff1493);
            border-radius: 50%;
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0% { transform: translateY(100vh) scale(0); opacity: 1; }
            50% { opacity: 1; }
            100% { transform: translateY(-100px) scale(1); opacity: 0; }
        }

        .progress-bar {
            background: #f0f0f0;
            border-radius: 25px;
            padding: 3px;
            margin: 20px 0;
        }

        .progress-fill {
            background: linear-gradient(45deg, #ff69b4, #ff1493);
            height: 20px;
            border-radius: 25px;
            transition: width 0.5s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        .school-illustration {
            text-align: center;
            margin: 20px 0;
            font-size: 4rem;
        }

        .student-avatar {
            display: inline-block;
            font-size: 3rem;
            margin: 0 10px;
            animation: wave 2s ease-in-out infinite;
        }

        @keyframes wave {
            0%, 100% { transform: rotate(0deg); }
            25% { transform: rotate(-10deg); }
            75% { transform: rotate(10deg); }
        }

        .score-display {
            background: linear-gradient(45deg, #28a745, #20c997);
            color: white;
            padding: 15px;
            border-radius: 15px;
            text-align: center;
            margin: 20px 0;
            font-size: 1.2rem;
            font-weight: bold;
        }

        /* شهادة التفوق */
        .certificate {
            background: linear-gradient(135deg, #fff 0%, #f8f9fa 100%);
            border: 5px solid #ffd700;
            border-radius: 20px;
            padding: 40px;
            text-align: center;
            margin: 30px 0;
            box-shadow: 0 15px 35px rgba(255, 215, 0, 0.3);
            position: relative;
            overflow: hidden;
        }

        .certificate::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 215, 0, 0.1), transparent);
            animation: shine 3s infinite;
        }

        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .certificate-title {
            font-size: 2.5rem;
            color: #ffd700;
            font-weight: bold;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .certificate-content {
            font-size: 1.3rem;
            color: #333;
            line-height: 1.8;
            margin: 20px 0;
        }

        .student-name-cert {
            font-size: 2rem;
            color: #ff1493;
            font-weight: bold;
            margin: 20px 0;
            text-decoration: underline;
            text-decoration-color: #ffd700;
        }

        .certificate-footer {
            margin-top: 30px;
            font-size: 1.1rem;
            color: #666;
        }

        .certificate-stars {
            font-size: 3rem;
            color: #ffd700;
            margin: 20px 0;
            animation: twinkle 2s infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.7; transform: scale(1.1); }
        }

        /* توقيع لمى */
        .signature {
            text-align: center;
            margin: 40px 0 20px 0;
            padding: 20px;
            background: linear-gradient(45deg, #1a1a2e, #16213e);
            border-radius: 15px;
            position: relative;
            overflow: hidden;
        }

        .signature::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4, #ffeaa7, #dda0dd);
            border-radius: 15px;
            z-index: -1;
            animation: rainbow 3s linear infinite;
        }

        @keyframes rainbow {
            0% { filter: hue-rotate(0deg); }
            100% { filter: hue-rotate(360deg); }
        }

        .signature-content {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }

        .gem {
            font-size: 2rem;
            animation: sparkle 2s ease-in-out infinite;
        }

        .gem:nth-child(1) {
            animation-delay: 0s;
        }

        .gem:nth-child(3) {
            animation-delay: 1s;
        }

        @keyframes sparkle {
            0%, 100% { transform: scale(1) rotate(0deg); opacity: 0.8; }
            50% { transform: scale(1.2) rotate(180deg); opacity: 1; }
        }

        .signature-name {
            font-size: 2.5rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradient-flow 3s ease infinite, glow 2s ease-in-out infinite alternate;
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.5);
        }

        @keyframes gradient-flow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes glow {
            from { filter: drop-shadow(0 0 10px rgba(255, 107, 107, 0.7)); }
            to { filter: drop-shadow(0 0 20px rgba(78, 205, 196, 0.7)); }
        }

        .hidden {
            display: none;
        }

        /* تحسين الاستجابة */
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            .header h1 {
                font-size: 2rem;
            }
            
            .current-word {
                font-size: 2rem;
            }
            
            .controls {
                flex-direction: column;
                align-items: center;
            }
            
            .drag-drop-area {
                flex-direction: column;
                align-items: center;
            }

            .name-input {
                width: 250px;
            }

            .certificate-title {
                font-size: 2rem;
            }

            .signature-name {
                font-size: 2rem;
            }
        }

        /* تحسين التعرف على الصوت */
        .voice-feedback {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 15px;
            margin: 15px 0;
            text-align: center;
            font-size: 1.1rem;
            border: 2px solid #ff69b4;
        }

        .voice-confidence {
            background: linear-gradient(45deg, #28a745, #20c997);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            margin-top: 10px;
            display: inline-block;
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <div class="container">
   <header class="header">
    <h1 id="app-title">تعليم القراءة للأطفال</h1>
    <p class="welcome-text" id="welcome-message">مرحباً بك في رحلة تعلم القراءة!</p>
    <div class="school-illustration">
     🏫 <span class="student-avatar">👧</span> <span class="student-avatar">👦</span> 📚
    </div>
   </header><!-- نموذج تسجيل الاسم -->
   <div id="name-registration" class="name-registration">
    <h2>مرحباً بك! ما اسمك؟</h2>
    <p>سجلي اسمك لتحصلي على شهادة تفوق عند إنجاز 70% من الأسئلة</p><input type="text" id="student-name-input" class="name-input" placeholder="اكتبي اسمك هنا..." maxlength="20"> <br><button id="start-learning" class="start-btn">ابدأ التعلم 🌟</button>
   </div>
   <main id="main-game" class="game-area hidden">
    <div class="level-selector"><button class="level-btn active" data-level="1">المستوى الأول - نطق الكلمات</button> <button class="level-btn" data-level="2">المستوى الثاني - ترتيب الأحرف</button> <button class="level-btn" data-level="3">المستوى الثالث - ترتيب الكلمات</button> <button class="level-btn" data-level="4">المستوى الرابع - إكمال الكلمات</button>
    </div>
    <div class="progress-bar">
     <div class="progress-fill" id="progress-fill" style="width: 0%">
      0%
     </div>
    </div>
    <div class="score-display">
     الطالبة: <span id="student-name-display">غير محدد</span> | النقاط: <span id="score">0</span> | الإجابات الصحيحة: <span id="correct-answers">0</span>/<span id="total-questions">0</span> (<span id="success-percentage">0</span>%)
    </div><!-- المستوى الأول: نطق الكلمات -->
    <div id="level-1" class="level-content">
     <div class="word-display">
      <div class="current-word" id="current-word">
       قرأ
      </div>
      <div class="word-meaning" id="word-meaning">
       فعل يعني النظر في الكتاب وفهم معناه
      </div>
     </div>
     <div class="controls"><button class="control-btn" id="play-word"> 🔊 استمع للكلمة </button> <button class="control-btn mic-btn" id="record-btn"> 🎤 انطق الكلمة </button> <button class="control-btn" id="next-word"> ➡️ الكلمة التالية </button>
     </div>
     <div id="voice-feedback" class="voice-feedback hidden">
      <div id="recognized-text"></div>
      <div id="confidence-score" class="voice-confidence"></div>
     </div>
    </div><!-- المستوى الثاني: ترتيب الأحرف -->
    <div id="level-2" class="level-content hidden">
     <div class="word-display">
      <div class="current-word" id="target-word">
       قرأ
      </div>
      <div class="word-meaning">
       رتب الأحرف لتكوين الكلمة
      </div>
     </div>
     <div class="drag-drop-area" id="letters-container"><!-- سيتم إضافة الأحرف هنا -->
     </div>
     <div class="drag-drop-area" id="word-builder"><!-- منطقة بناء الكلمة -->
     </div>
     <div class="controls"><button class="control-btn" id="check-word">✅ تحقق من الكلمة</button> <button class="control-btn" id="reset-letters">🔄 إعادة ترتيب</button>
     </div>
    </div><!-- المستوى الثالث: ترتيب الكلمات -->
    <div id="level-3" class="level-content hidden">
     <div class="word-display">
      <div class="current-word">
       كون جملة مفيدة
      </div>
      <div class="word-meaning">
       اسحب الكلمات لتكوين جملة صحيحة
      </div>
     </div>
     <div class="drag-drop-area" id="words-container"><!-- سيتم إضافة الكلمات هنا -->
     </div>
     <div class="drag-drop-area" id="sentence-builder"><!-- منطقة بناء الجملة -->
     </div>
     <div class="controls"><button class="control-btn" id="check-sentence">✅ تحقق من الجملة</button> <button class="control-btn" id="reset-words">🔄 إعادة ترتيب</button>
     </div>
    </div><!-- المستوى الرابع: إكمال الكلمات -->
    <div id="level-4" class="level-content hidden">
     <div class="word-display">
      <div class="current-word" id="incomplete-word">
       مدر_ة
      </div>
      <div class="word-meaning">
       اختر الحرف المناسب لإكمال الكلمة
      </div>
     </div>
     <div class="multiple-choice" id="choices-container"><!-- سيتم إضافة الخيارات هنا -->
     </div>
    </div>
    <div class="feedback" id="feedback"></div>
   </main><!-- شهادة التفوق -->
   <div id="certificate" class="certificate hidden">
    <div class="certificate-stars">
     ⭐ 🌟 ⭐
    </div>
    <h2 class="certificate-title" id="certificate-title">شهادة تفوق في القراءة</h2>
    <div class="certificate-content">
     نشهد بأن الطالبة المتميزة 
     <div class="student-name-cert" id="student-name-cert"></div> قد أتمت بنجاح برنامج تعليم القراءة والإملاء <br>
      وحصلت على نسبة نجاح <span id="final-percentage">0</span>% <br>
      في <span id="certificate-date"></span>
    </div>
    <div class="certificate-stars">
     🏆 👑 🏆
    </div>
    <div class="certificate-footer">
     تهانينا على هذا الإنجاز الرائع!
    </div>
   </div>
   <div class="celebration" id="celebration"></div><!-- توقيع لمى -->
   <div class="signature">
    <div class="signature-content">
     <div class="gem">
      💎
     </div>
     <div class="signature-name">
      لمى
     </div>
     <div class="gem">
      💎
     </div>
    </div>
   </div>
  </div>
  <script>
        // إعداد البيانات والمتغيرات
        const defaultConfig = {
            app_title: "تعليم القراءة للأطفال",
            welcome_message: "مرحباً بك في رحلة تعلم القراءة!",
            success_message: "أحسنت! إجابة صحيحة",
            retry_message: "حاولي مرة أخرى",
            certificate_title: "شهادة تفوق في القراءة",
            background_color: "#ffeef8",
            surface_color: "#ffffff",
            text_color: "#ff1493",
            primary_action_color: "#ff69b4",
            secondary_action_color: "#ffc1cc"
        };

        let currentLevel = 1;
        let currentWordIndex = 0;
        let score = 0;
        let correctAnswers = 0;
        let totalQuestions = 0;
        let isRecording = false;
        let recognition = null;
        let currentData = [];
        let studentName = "";
        let certificateEarned = false;

        // بيانات موسعة للكلمات والجمل
        const wordsData = {
            level1: [
                { word: "قرأ", meaning: "فعل يعني النظر في الكتاب وفهم معناه" },
                { word: "كتب", meaning: "فعل يعني الكتابة بالقلم" },
                { word: "زرع", meaning: "فعل يعني وضع البذور في الأرض" },
                { word: "حصد", meaning: "فعل يعني قطف الثمار" },
                { word: "مدرسة", meaning: "مكان التعلم والدراسة" },
                { word: "طالب", meaning: "الشخص الذي يتعلم" },
                { word: "معلم", meaning: "الشخص الذي يعلم الآخرين" },
                { word: "كتاب", meaning: "مجموعة من الصفحات للقراءة" },
                { word: "قلم", meaning: "أداة للكتابة" },
                { word: "دفتر", meaning: "مجموعة أوراق للكتابة" },
                { word: "حقيبة", meaning: "وعاء لحمل الأشياء" },
                { word: "نافذة", meaning: "فتحة في الجدار للنظر خارجاً" },
                { word: "باب", meaning: "مدخل للغرفة أو المنزل" },
                { word: "شمس", meaning: "النجم الذي ينير الأرض" },
                { word: "قمر", meaning: "القمر الذي ينير الليل" },
                { word: "نجم", meaning: "جسم مضيء في السماء" },
                { word: "بحر", meaning: "مساحة كبيرة من الماء المالح" },
                { word: "جبل", meaning: "ارتفاع كبير من الأرض" },
                { word: "شجرة", meaning: "نبات كبير له جذع وأوراق" },
                { word: "زهرة", meaning: "جزء جميل وملون من النبات" },
                { word: "طائر", meaning: "حيوان يطير في السماء" },
                { word: "سمك", meaning: "حيوان يعيش في الماء" },
                { word: "قطة", meaning: "حيوان أليف صغير" },
                { word: "كلب", meaning: "حيوان أليف وفي" },
                { word: "حصان", meaning: "حيوان كبير للركوب" }
            ],
            level2: [
                { word: "قرأ", letters: ["ق", "ر", "أ"] },
                { word: "كتب", letters: ["ك", "ت", "ب"] },
                { word: "زرع", letters: ["ز", "ر", "ع"] },
                { word: "حصد", letters: ["ح", "ص", "د"] },
                { word: "مدرسة", letters: ["م", "د", "ر", "س", "ة"] },
                { word: "طالب", letters: ["ط", "ا", "ل", "ب"] },
                { word: "معلم", letters: ["م", "ع", "ل", "م"] },
                { word: "كتاب", letters: ["ك", "ت", "ا", "ب"] },
                { word: "قلم", letters: ["ق", "ل", "م"] },
                { word: "دفتر", letters: ["د", "ف", "ت", "ر"] },
                { word: "حقيبة", letters: ["ح", "ق", "ي", "ب", "ة"] },
                { word: "نافذة", letters: ["ن", "ا", "ف", "ذ", "ة"] },
                { word: "باب", letters: ["ب", "ا", "ب"] },
                { word: "شمس", letters: ["ش", "م", "س"] },
                { word: "قمر", letters: ["ق", "م", "ر"] },
                { word: "بحر", letters: ["ب", "ح", "ر"] },
                { word: "جبل", letters: ["ج", "ب", "ل"] },
                { word: "شجرة", letters: ["ش", "ج", "ر", "ة"] },
                { word: "زهرة", letters: ["ز", "ه", "ر", "ة"] },
                { word: "طائر", letters: ["ط", "ا", "ئ", "ر"] }
            ],
            level3: [
                { sentence: "الطالب يقرأ الكتاب", words: ["الطالب", "يقرأ", "الكتاب"] },
                { sentence: "المعلم يكتب على السبورة", words: ["المعلم", "يكتب", "على", "السبورة"] },
                { sentence: "الفلاح يزرع القمح", words: ["الفلاح", "يزرع", "القمح"] },
                { sentence: "الطفل يذهب إلى المدرسة", words: ["الطفل", "يذهب", "إلى", "المدرسة"] },
                { sentence: "الشمس تشرق في الصباح", words: ["الشمس", "تشرق", "في", "الصباح"] },
                { sentence: "القمر ينير في الليل", words: ["القمر", "ينير", "في", "الليل"] },
                { sentence: "الطائر يطير في السماء", words: ["الطائر", "يطير", "في", "السماء"] },
                { sentence: "السمك يسبح في البحر", words: ["السمك", "يسبح", "في", "البحر"] },
                { sentence: "الزهرة تنمو في الحديقة", words: ["الزهرة", "تنمو", "في", "الحديقة"] },
                { sentence: "الطالبة تحل الواجب", words: ["الطالبة", "تحل", "الواجب"] },
                { sentence: "الأم تطبخ الطعام", words: ["الأم", "تطبخ", "الطعام"] },
                { sentence: "الأب يقود السيارة", words: ["الأب", "يقود", "السيارة"] },
                { sentence: "الطفلة تلعب بالكرة", words: ["الطفلة", "تلعب", "بالكرة"] },
                { sentence: "الكتاب موجود على الطاولة", words: ["الكتاب", "موجود", "على", "الطاولة"] },
                { sentence: "القطة تنام تحت الشجرة", words: ["القطة", "تنام", "تحت", "الشجرة"] }
            ],
            level4: [
                { word: "مدرسة", incomplete: "مدر_ة", choices: ["س", "ص", "ض", "ط"], correct: "س" },
                { word: "كتاب", incomplete: "كت_ب", choices: ["ا", "و", "ي", "ة"], correct: "ا" },
                { word: "طالب", incomplete: "طا_ب", choices: ["ل", "ر", "ن", "م"], correct: "ل" },
                { word: "معلم", incomplete: "مع_م", choices: ["ل", "ر", "ن", "د"], correct: "ل" },
                { word: "حديقة", incomplete: "حد_قة", choices: ["ي", "و", "ا", "ة"], correct: "ي" },
                { word: "نافذة", incomplete: "نا_ذة", choices: ["ف", "ق", "ك", "ت"], correct: "ف" },
                { word: "طائر", incomplete: "طا_ر", choices: ["ئ", "ي", "و", "ا"], correct: "ئ" },
                { word: "شجرة", incomplete: "ش_رة", choices: ["ج", "ح", "خ", "غ"], correct: "ج" },
                { word: "زهرة", incomplete: "ز_رة", choices: ["ه", "ح", "خ", "غ"], correct: "ه" },
                { word: "حقيبة", incomplete: "حق_بة", choices: ["ي", "و", "ا", "ة"], correct: "ي" },
                { word: "سيارة", incomplete: "س_ارة", choices: ["ي", "و", "ا", "ة"], correct: "ي" },
                { word: "طاولة", incomplete: "طا_لة", choices: ["و", "ي", "ا", "ة"], correct: "و" },
                { word: "مكتبة", incomplete: "مكت_ة", choices: ["ب", "ت", "ث", "ن"], correct: "ب" },
                { word: "حاسوب", incomplete: "حا_وب", choices: ["س", "ص", "ض", "ط"], correct: "س" },
                { word: "تلفاز", incomplete: "تل_از", choices: ["ف", "ق", "ك", "ت"], correct: "ف" }
            ]
        };

        // إعداد SDK للبيانات
        const dataHandler = {
            onDataChanged(data) {
                currentData = data;
                updateProgressDisplay();
            }
        };

        // إعداد SDK للعناصر
        async function onConfigChange(config) {
            const appTitle = config.app_title || defaultConfig.app_title;
            const welcomeMessage = config.welcome_message || defaultConfig.welcome_message;
            const certificateTitle = config.certificate_title || defaultConfig.certificate_title;
            
            document.getElementById('app-title').textContent = appTitle;
            document.getElementById('welcome-message').textContent = welcomeMessage;
            document.getElementById('certificate-title').textContent = certificateTitle;
            
            // تطبيق الألوان
            const backgroundColor = config.background_color || defaultConfig.background_color;
            const surfaceColor = config.surface_color || defaultConfig.surface_color;
            const textColor = config.text_color || defaultConfig.text_color;
            const primaryActionColor = config.primary_action_color || defaultConfig.primary_action_color;
            const secondaryActionColor = config.secondary_action_color || defaultConfig.secondary_action_color;
            
            document.body.style.background = `linear-gradient(135deg, ${backgroundColor} 0%, ${secondaryActionColor} 50%, ${primaryActionColor} 100%)`;
            document.querySelector('.game-area').style.backgroundColor = surfaceColor;
            document.querySelector('.name-registration').style.backgroundColor = surfaceColor;
            document.querySelector('.current-word').style.color = textColor;
        }

        function mapToCapabilities(config) {
            return {
                recolorables: [
                    {
                        get: () => config.background_color || defaultConfig.background_color,
                        set: (value) => {
                            if (window.elementSdk) {
                                window.elementSdk.setConfig({ background_color: value });
                            }
                        }
                    },
                    {
                        get: () => config.surface_color || defaultConfig.surface_color,
                        set: (value) => {
                            if (window.elementSdk) {
                                window.elementSdk.setConfig({ surface_color: value });
                            }
                        }
                    },
                    {
                        get: () => config.text_color || defaultConfig.text_color,
                        set: (value) => {
                            if (window.elementSdk) {
                                window.elementSdk.setConfig({ text_color: value });
                            }
                        }
                    },
                    {
                        get: () => config.primary_action_color || defaultConfig.primary_action_color,
                        set: (value) => {
                            if (window.elementSdk) {
                                window.elementSdk.setConfig({ primary_action_color: value });
                            }
                        }
                    },
                    {
                        get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
                        set: (value) => {
                            if (window.elementSdk) {
                                window.elementSdk.setConfig({ secondary_action_color: value });
                            }
                        }
                    }
                ],
                borderables: [],
                fontEditable: undefined,
                fontSizeable: undefined
            };
        }

        function mapToEditPanelValues(config) {
            return new Map([
                ["app_title", config.app_title || defaultConfig.app_title],
                ["welcome_message", config.welcome_message || defaultConfig.welcome_message],
                ["success_message", config.success_message || defaultConfig.success_message],
                ["retry_message", config.retry_message || defaultConfig.retry_message],
                ["certificate_title", config.certificate_title || defaultConfig.certificate_title]
            ]);
        }

        // تهيئة التطبيق
        async function initApp() {
            try {
                // تهيئة SDK البيانات
                if (window.dataSdk) {
                    const initResult = await window.dataSdk.init(dataHandler);
                    if (!initResult.isOk) {
                        console.error("فشل في تهيئة SDK البيانات");
                    }
                }

                // تهيئة SDK العناصر
                if (window.elementSdk) {
                    await window.elementSdk.init({
                        defaultConfig,
                        onConfigChange,
                        mapToCapabilities,
                        mapToEditPanelValues
                    });
                }

                initSpeechRecognition();
                setupEventListeners();
            } catch (error) {
                console.error("خطأ في تهيئة التطبيق:", error);
            }
        }

        // إعداد التعرف على الصوت المحسن
        function initSpeechRecognition() {
            if ('webkitSpeechRecognition' in window || 'SpeechRecognition' in window) {
                const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
                recognition = new SpeechRecognition();
                
                // إعدادات محسنة للتعرف على الصوت
                recognition.lang = 'ar-SA';
                recognition.continuous = false;
                recognition.interimResults = true;
                recognition.maxAlternatives = 5;
                
                recognition.onstart = function() {
                    showVoiceFeedback("جاري الاستماع...", 0);
                };

                recognition.onresult = function(event) {
                    let finalTranscript = '';
                    let interimTranscript = '';
                    
                    for (let i = event.resultIndex; i < event.results.length; i++) {
                        const transcript = event.results[i][0].transcript;
                        const confidence = event.results[i][0].confidence;
                        
                        if (event.results[i].isFinal) {
                            finalTranscript += transcript;
                            showVoiceFeedback(`سمعت: "${transcript}"`, confidence);
                            checkPronunciation(transcript, confidence);
                        } else {
                            interimTranscript += transcript;
                            showVoiceFeedback(`أستمع: "${interimTranscript}"`, 0);
                        }
                    }
                };

                recognition.onerror = function(event) {
                    let errorMessage = "حدث خطأ في التسجيل";
                    switch(event.error) {
                        case 'no-speech':
                            errorMessage = "لم أسمع صوتك، حاولي مرة أخرى";
                            break;
                        case 'audio-capture':
                            errorMessage = "تأكدي من تشغيل المايك";
                            break;
                        case 'not-allowed':
                            errorMessage = "يرجى السماح باستخدام المايك";
                            break;
                        case 'network':
                            errorMessage = "تحققي من الاتصال بالإنترنت";
                            break;
                    }
                    showFeedback(errorMessage, false);
                    hideVoiceFeedback();
                    stopRecording();
                };

                recognition.onend = function() {
                    stopRecording();
                    setTimeout(hideVoiceFeedback, 3000);
                };
            }
        }

        // إعداد مستمعي الأحداث
        function setupEventListeners() {
            // تسجيل الاسم
            document.getElementById('start-learning').addEventListener('click', startLearning);
            document.getElementById('student-name-input').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    startLearning();
                }
            });

            // أزرار المستويات
            document.querySelectorAll('.level-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const level = parseInt(e.target.dataset.level);
                    loadLevel(level);
                });
            });

            // أزرار التحكم
            document.getElementById('play-word').addEventListener('click', playCurrentWord);
            document.getElementById('record-btn').addEventListener('click', toggleRecording);
            document.getElementById('next-word').addEventListener('click', nextWord);
            document.getElementById('check-word').addEventListener('click', checkWordBuilding);
            document.getElementById('reset-letters').addEventListener('click', resetLetters);
            document.getElementById('check-sentence').addEventListener('click', checkSentenceBuilding);
            document.getElementById('reset-words').addEventListener('click', resetWords);
        }

        // بدء التعلم
        function startLearning() {
            const nameInput = document.getElementById('student-name-input');
            studentName = nameInput.value.trim();
            
            if (!studentName) {
                nameInput.style.borderColor = '#dc3545';
                nameInput.placeholder = 'يرجى كتابة اسمك أولاً';
                return;
            }

            document.getElementById('student-name-display').textContent = studentName;
            document.getElementById('name-registration').classList.add('hidden');
            document.getElementById('main-game').classList.remove('hidden');
            
            loadLevel(1);
        }

        // عرض تغذية راجعة للصوت
        function showVoiceFeedback(text, confidence) {
            const feedback = document.getElementById('voice-feedback');
            const recognizedText = document.getElementById('recognized-text');
            const confidenceScore = document.getElementById('confidence-score');
            
            recognizedText.textContent = text;
            
            if (confidence > 0) {
                const percentage = Math.round(confidence * 100);
                confidenceScore.textContent = `دقة التعرف: ${percentage}%`;
                confidenceScore.style.background = percentage > 70 ? 
                    'linear-gradient(45deg, #28a745, #20c997)' : 
                    'linear-gradient(45deg, #ffc107, #fd7e14)';
            } else {
                confidenceScore.textContent = '';
            }
            
            feedback.classList.remove('hidden');
        }

        function hideVoiceFeedback() {
            document.getElementById('voice-feedback').classList.add('hidden');
        }

        // تحميل المستوى
        function loadLevel(level) {
            currentLevel = level;
            currentWordIndex = 0;
            
            // إخفاء جميع المستويات
            document.querySelectorAll('.level-content').forEach(content => {
                content.classList.add('hidden');
            });
            
            // إظهار المستوى المحدد
            document.getElementById(`level-${level}`).classList.remove('hidden');
            
            // تحديث أزرار المستويات
            document.querySelectorAll('.level-btn').forEach(btn => {
                btn.classList.remove('active');
                if (parseInt(btn.dataset.level) === level) {
                    btn.classList.add('active');
                }
            });

            // تحميل محتوى المستوى
            switch(level) {
                case 1:
                    loadWordPronunciation();
                    break;
                case 2:
                    loadLetterArrangement();
                    break;
                case 3:
                    loadWordArrangement();
                    break;
                case 4:
                    loadWordCompletion();
                    break;
            }
        }

        // المستوى الأول: نطق الكلمات
        function loadWordPronunciation() {
            const currentWord = wordsData.level1[currentWordIndex];
            document.getElementById('current-word').textContent = currentWord.word;
            document.getElementById('word-meaning').textContent = currentWord.meaning;
            hideVoiceFeedback();
        }

        function playCurrentWord() {
            const currentWord = wordsData.level1[currentWordIndex].word;
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(currentWord);
                utterance.lang = 'ar-SA';
                utterance.rate = 0.7;
                utterance.pitch = 1.2;
                speechSynthesis.speak(utterance);
            }
        }

        function toggleRecording() {
            if (!recognition) {
                showFeedback("التعرف على الصوت غير مدعوم في هذا المتصفح", false);
                return;
            }

            if (isRecording) {
                stopRecording();
            } else {
                startRecording();
            }
        }

        function startRecording() {
            isRecording = true;
            const recordBtn = document.getElementById('record-btn');
            recordBtn.classList.add('recording');
            recordBtn.innerHTML = '🛑 توقف عن التسجيل';
            
            try {
                recognition.start();
            } catch (error) {
                showFeedback("خطأ في بدء التسجيل", false);
                stopRecording();
            }
        }

        function stopRecording() {
            isRecording = false;
            const recordBtn = document.getElementById('record-btn');
            recordBtn.classList.remove('recording', 'processing');
            recordBtn.innerHTML = '🎤 انطق الكلمة';
            
            if (recognition) {
                recognition.stop();
            }
        }

        function checkPronunciation(spokenText, confidence) {
            const recordBtn = document.getElementById('record-btn');
            recordBtn.classList.add('processing');
            recordBtn.innerHTML = '⚙️ جاري التحليل...';
            
            setTimeout(() => {
                const currentWord = wordsData.level1[currentWordIndex].word;
                const config = window.elementSdk ? window.elementSdk.config : defaultConfig;
                
                // تنظيف النص المنطوق
                const cleanSpoken = spokenText.replace(/[^\u0600-\u06FF]/g, '').trim();
                const cleanTarget = currentWord.replace(/[^\u0600-\u06FF]/g, '').trim();
                
                // تحسين دقة المقارنة
                const similarity = calculateSimilarity(cleanSpoken, cleanTarget);
                const isCorrect = similarity > 0.7 || cleanSpoken === cleanTarget || 
                                spokenText.includes(currentWord) || confidence > 0.8;
                
                totalQuestions++;
                
                if (isCorrect) {
                    correctAnswers++;
                    showFeedback(config.success_message || defaultConfig.success_message, true);
                    updateScore(10);
                    createCelebration();
                    setTimeout(() => {
                        nextWord();
                    }, 2000);
                } else {
                    showFeedback(config.retry_message || defaultConfig.retry_message, false);
                }
                
                updateStats();
                checkForCertificate();
                stopRecording();
            }, 1000);
        }

        // حساب التشابه بين النصوص
        function calculateSimilarity(str1, str2) {
            const longer = str1.length > str2.length ? str1 : str2;
            const shorter = str1.length > str2.length ? str2 : str1;
            
            if (longer.length === 0) return 1.0;
            
            const editDistance = levenshteinDistance(longer, shorter);
            return (longer.length - editDistance) / longer.length;
        }

        function levenshteinDistance(str1, str2) {
            const matrix = [];
            
            for (let i = 0; i <= str2.length; i++) {
                matrix[i] = [i];
            }
            
            for (let j = 0; j <= str1.length; j++) {
                matrix[0][j] = j;
            }
            
            for (let i = 1; i <= str2.length; i++) {
                for (let j = 1; j <= str1.length; j++) {
                    if (str2.charAt(i - 1) === str1.charAt(j - 1)) {
                        matrix[i][j] = matrix[i - 1][j - 1];
                    } else {
                        matrix[i][j] = Math.min(
                            matrix[i - 1][j - 1] + 1,
                            matrix[i][j - 1] + 1,
                            matrix[i - 1][j] + 1
                        );
                    }
                }
            }
            
            return matrix[str2.length][str1.length];
        }

        function nextWord() {
            currentWordIndex++;
            if (currentWordIndex >= wordsData.level1.length) {
                currentWordIndex = 0;
            }
            loadWordPronunciation();
            clearFeedback();
        }

        // المستوى الثاني: ترتيب الأحرف
        function loadLetterArrangement() {
            const currentWord = wordsData.level2[currentWordIndex];
            document.getElementById('target-word').textContent = currentWord.word;
            
            const lettersContainer = document.getElementById('letters-container');
            const wordBuilder = document.getElementById('word-builder');
            
            lettersContainer.innerHTML = '';
            wordBuilder.innerHTML = '';
            
            // خلط الأحرف
            const shuffledLetters = [...currentWord.letters].sort(() => Math.random() - 0.5);
            
            // إضافة الأحرف
            shuffledLetters.forEach((letter, index) => {
                const letterBox = document.createElement('div');
                letterBox.className = 'letter-box';
                letterBox.textContent = letter;
                letterBox.draggable = true;
                letterBox.dataset.letter = letter;
                letterBox.dataset.index = index;
                
                letterBox.addEventListener('dragstart', handleDragStart);
                letterBox.addEventListener('dragend', handleDragEnd);
                
                lettersContainer.appendChild(letterBox);
            });
            
            // إضافة مناطق الإسقاط
            for (let i = 0; i < currentWord.letters.length; i++) {
                const dropZone = document.createElement('div');
                dropZone.className = 'drop-zone';
                dropZone.dataset.position = i;
                
                dropZone.addEventListener('dragover', handleDragOver);
                dropZone.addEventListener('drop', handleDrop);
                
                wordBuilder.appendChild(dropZone);
            }
        }

        function handleDragStart(e) {
            e.target.classList.add('dragging');
            e.dataTransfer.setData('text/plain', e.target.dataset.letter);
            e.dataTransfer.setData('source', 'letter');
        }

        function handleDragEnd(e) {
            e.target.classList.remove('dragging');
        }

        function handleDragOver(e) {
            e.preventDefault();
            e.target.classList.add('drag-over');
        }

        function handleDrop(e) {
            e.preventDefault();
            e.target.classList.remove('drag-over');
            
            const letter = e.dataTransfer.getData('text/plain');
            const source = e.dataTransfer.getData('source');
            
            if (source === 'letter' && !e.target.textContent.trim()) {
                e.target.textContent = letter;
                e.target.style.background = 'linear-gradient(45deg, #ff69b4, #ff1493)';
                e.target.style.color = 'white';
                
                // إخفاء الحرف من المصدر
                const letterBoxes = document.querySelectorAll('.letter-box');
                letterBoxes.forEach(box => {
                    if (box.dataset.letter === letter && box.classList.contains('dragging')) {
                        box.style.display = 'none';
                    }
                });
            }
        }

        function checkWordBuilding() {
            const dropZones = document.querySelectorAll('#word-builder .drop-zone');
            const builtWord = Array.from(dropZones).map(zone => zone.textContent.trim()).join('');
            const targetWord = wordsData.level2[currentWordIndex].word;
            
            const config = window.elementSdk ? window.elementSdk.config : defaultConfig;
            totalQuestions++;
            
            if (builtWord === targetWord) {
                correctAnswers++;
                showFeedback(config.success_message || defaultConfig.success_message, true);
                updateScore(15);
                createCelebration();
                setTimeout(() => {
                    nextLetterWord();
                }, 2000);
            } else {
                showFeedback(config.retry_message || defaultConfig.retry_message, false);
            }
            
            updateStats();
            checkForCertificate();
        }

        function resetLetters() {
            loadLetterArrangement();
            clearFeedback();
        }

        function nextLetterWord() {
            currentWordIndex++;
            if (currentWordIndex >= wordsData.level2.length) {
                currentWordIndex = 0;
            }
            loadLetterArrangement();
            clearFeedback();
        }

        // المستوى الثالث: ترتيب الكلمات
        function loadWordArrangement() {
            const currentSentence = wordsData.level3[currentWordIndex];
            
            const wordsContainer = document.getElementById('words-container');
            const sentenceBuilder = document.getElementById('sentence-builder');
            
            wordsContainer.innerHTML = '';
            sentenceBuilder.innerHTML = '';
            
            // خلط الكلمات
            const shuffledWords = [...currentSentence.words].sort(() => Math.random() - 0.5);
            
            // إضافة الكلمات
            shuffledWords.forEach((word, index) => {
                const wordBox = document.createElement('div');
                wordBox.className = 'word-box';
                wordBox.textContent = word;
                wordBox.draggable = true;
                wordBox.dataset.word = word;
                wordBox.dataset.index = index;
                
                wordBox.addEventListener('dragstart', handleWordDragStart);
                wordBox.addEventListener('dragend', handleDragEnd);
                
                wordsContainer.appendChild(wordBox);
            });
            
            // إضافة مناطق الإسقاط
            for (let i = 0; i < currentSentence.words.length; i++) {
                const dropZone = document.createElement('div');
                dropZone.className = 'drop-zone';
                dropZone.dataset.position = i;
                
                dropZone.addEventListener('dragover', handleDragOver);
                dropZone.addEventListener('drop', handleWordDrop);
                
                sentenceBuilder.appendChild(dropZone);
            }
        }

        function handleWordDragStart(e) {
            e.target.classList.add('dragging');
            e.dataTransfer.setData('text/plain', e.target.dataset.word);
            e.dataTransfer.setData('source', 'word');
        }

        function handleWordDrop(e) {
            e.preventDefault();
            e.target.classList.remove('drag-over');
            
            const word = e.dataTransfer.getData('text/plain');
            const source = e.dataTransfer.getData('source');
            
            if (source === 'word' && !e.target.textContent.trim()) {
                e.target.textContent = word;
                e.target.style.background = 'linear-gradient(45deg, #ff69b4, #ff1493)';
                e.target.style.color = 'white';
                
                // إخفاء الكلمة من المصدر
                const wordBoxes = document.querySelectorAll('.word-box');
                wordBoxes.forEach(box => {
                    if (box.dataset.word === word && box.classList.contains('dragging')) {
                        box.style.display = 'none';
                    }
                });
            }
        }

        function checkSentenceBuilding() {
            const dropZones = document.querySelectorAll('#sentence-builder .drop-zone');
            const builtSentence = Array.from(dropZones).map(zone => zone.textContent.trim()).join(' ');
            const targetSentence = wordsData.level3[currentWordIndex].sentence;
            
            const config = window.elementSdk ? window.elementSdk.config : defaultConfig;
            totalQuestions++;
            
            if (builtSentence === targetSentence) {
                correctAnswers++;
                showFeedback(config.success_message || defaultConfig.success_message, true);
                updateScore(20);
                createCelebration();
                setTimeout(() => {
                    nextSentence();
                }, 2000);
            } else {
                showFeedback(config.retry_message || defaultConfig.retry_message, false);
            }
            
            updateStats();
            checkForCertificate();
        }

        function resetWords() {
            loadWordArrangement();
            clearFeedback();
        }

        function nextSentence() {
            currentWordIndex++;
            if (currentWordIndex >= wordsData.level3.length) {
                currentWordIndex = 0;
            }
            loadWordArrangement();
            clearFeedback();
        }

        // المستوى الرابع: إكمال الكلمات
        function loadWordCompletion() {
            const currentWord = wordsData.level4[currentWordIndex];
            document.getElementById('incomplete-word').textContent = currentWord.incomplete;
            
            const choicesContainer = document.getElementById('choices-container');
            choicesContainer.innerHTML = '';
            
            currentWord.choices.forEach(choice => {
                const choiceBtn = document.createElement('button');
                choiceBtn.className = 'choice-btn';
                choiceBtn.textContent = choice;
                choiceBtn.addEventListener('click', () => checkWordCompletion(choice));
                choicesContainer.appendChild(choiceBtn);
            });
        }

        function checkWordCompletion(selectedChoice) {
            const currentWord = wordsData.level4[currentWordIndex];
            const config = window.elementSdk ? window.elementSdk.config : defaultConfig;
            totalQuestions++;
            
            if (selectedChoice === currentWord.correct) {
                correctAnswers++;
                document.getElementById('incomplete-word').textContent = currentWord.word;
                showFeedback(config.success_message || defaultConfig.success_message, true);
                updateScore(10);
                createCelebration();
                setTimeout(() => {
                    nextCompletionWord();
                }, 2000);
            } else {
                showFeedback(config.retry_message || defaultConfig.retry_message, false);
            }
            
            updateStats();
            checkForCertificate();
        }

        function nextCompletionWord() {
            currentWordIndex++;
            if (currentWordIndex >= wordsData.level4.length) {
                currentWordIndex = 0;
            }
            loadWordCompletion();
            clearFeedback();
        }

        // تحديث الإحصائيات
        function updateStats() {
            document.getElementById('correct-answers').textContent = correctAnswers;
            document.getElementById('total-questions').textContent = totalQuestions;
            
            const percentage = totalQuestions > 0 ? Math.round((correctAnswers / totalQuestions) * 100) : 0;
            document.getElementById('success-percentage').textContent = percentage;
        }

        // فحص استحقاق الشهادة
        function checkForCertificate() {
            if (totalQuestions >= 10 && !certificateEarned) {
                const percentage = Math.round((correctAnswers / totalQuestions) * 100);
                if (percentage >= 70) {
                    showCertificate(percentage);
                    certificateEarned = true;
                }
            }
        }

        // عرض شهادة التفوق
        function showCertificate(percentage) {
            document.getElementById('student-name-cert').textContent = studentName;
            document.getElementById('final-percentage').textContent = percentage;
            document.getElementById('certificate-date').textContent = new Date().toLocaleDateString('ar-SA');
            document.getElementById('certificate').classList.remove('hidden');
            
            // تأثير احتفالي خاص
            createMegaCelebration();
            
            // حفظ إنجاز الشهادة
            saveCertificateAchievement(percentage);
        }

        async function saveCertificateAchievement(percentage) {
            if (window.dataSdk && currentData.length < 999) {
                const certificateData = {
                    student_name: studentName,
                    level: currentLevel,
                    score: score,
                    total_questions: totalQuestions,
                    correct_answers: correctAnswers,
                    completed_words: `${correctAnswers}/${totalQuestions}`,
                    certificate_earned: true,
                    timestamp: new Date().toISOString()
                };
                
                const result = await window.dataSdk.create(certificateData);
                if (!result.isOk) {
                    console.error("فشل في حفظ بيانات الشهادة");
                }
            }
        }

        // وظائف مساعدة
        function showFeedback(message, isSuccess) {
            const feedback = document.getElementById('feedback');
            feedback.textContent = isSuccess ? `✅ ${message}` : `❌ ${message}`;
            feedback.className = `feedback ${isSuccess ? 'success' : 'error'}`;
        }

        function clearFeedback() {
            const feedback = document.getElementById('feedback');
            feedback.textContent = '';
            feedback.className = 'feedback';
        }

        function updateScore(points) {
            score += points;
            document.getElementById('score').textContent = score;
            
            // حفظ التقدم
            saveProgress();
            updateProgressDisplay();
        }

        async function saveProgress() {
            if (window.dataSdk && currentData.length < 999) {
                const progressData = {
                    student_name: studentName,
                    level: currentLevel,
                    score: score,
                    total_questions: totalQuestions,
                    correct_answers: correctAnswers,
                    completed_words: `${correctAnswers}/${totalQuestions}`,
                    certificate_earned: certificateEarned,
                    timestamp: new Date().toISOString()
                };
                
                const result = await window.dataSdk.create(progressData);
                if (!result.isOk) {
                    console.error("فشل في حفظ التقدم");
                }
            }
        }

        function updateProgressDisplay() {
            const totalWords = Object.values(wordsData).reduce((sum, level) => sum + level.length, 0);
            const progress = Math.min((correctAnswers / totalWords) * 100, 100);
            const progressFill = document.getElementById('progress-fill');
            progressFill.style.width = `${progress}%`;
            progressFill.textContent = `${Math.round(progress)}%`;
        }

        function createCelebration() {
            const celebration = document.getElementById('celebration');
            
            // إنشاء فقاعات الاحتفال
            for (let i = 0; i < 20; i++) {
                const bubble = document.createElement('div');
                bubble.className = 'bubble';
                bubble.style.left = Math.random() * 100 + '%';
                bubble.style.width = bubble.style.height = Math.random() * 20 + 10 + 'px';
                bubble.style.animationDelay = Math.random() * 2 + 's';
                celebration.appendChild(bubble);
                
                setTimeout(() => {
                    bubble.remove();
                }, 3000);
            }
            
            // تشغيل صوت التصفيق
            playApplauseSound();
        }

        function createMegaCelebration() {
            const celebration = document.getElementById('celebration');
            
            // احتفال كبير للشهادة
            for (let i = 0; i < 50; i++) {
                const bubble = document.createElement('div');
                bubble.className = 'bubble';
                bubble.style.left = Math.random() * 100 + '%';
                bubble.style.width = bubble.style.height = Math.random() * 30 + 15 + 'px';
                bubble.style.animationDelay = Math.random() * 3 + 's';
                bubble.style.background = `radial-gradient(circle, #ffd700, #ff69b4)`;
                celebration.appendChild(bubble);
                
                setTimeout(() => {
                    bubble.remove();
                }, 5000);
            }
            
            // صوت احتفالي مميز
            playVictorySound();
        }

        function playApplauseSound() {
            // محاكاة صوت التصفيق باستخدام Web Audio API
            if ('AudioContext' in window || 'webkitAudioContext' in window) {
                const AudioContext = window.AudioContext || window.webkitAudioContext;
                const audioContext = new AudioContext();
                
                // إنشاء نغمة احتفالية
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                oscillator.frequency.setValueAtTime(800, audioContext.currentTime);
                oscillator.frequency.exponentialRampToValueAtTime(400, audioContext.currentTime + 0.5);
                
                gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
                gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.5);
                
                oscillator.start(audioContext.currentTime);
                oscillator.stop(audioContext.currentTime + 0.5);
            }
        }

        function playVictorySound() {
            // صوت انتصار للشهادة
            if ('AudioContext' in window || 'webkitAudioContext' in window) {
                const AudioContext = window.AudioContext || window.webkitAudioContext;
                const audioContext = new AudioContext();
                
                // نغمة انتصار متقدمة
                const notes = [523.25, 659.25, 783.99, 1046.50]; // C5, E5, G5, C6
                
                notes.forEach((freq, index) => {
                    const oscillator = audioContext.createOscillator();
                    const gainNode = audioContext.createGain();
                    
                    oscillator.connect(gainNode);
                    gainNode.connect(audioContext.destination);
                    
                    oscillator.frequency.setValueAtTime(freq, audioContext.currentTime + index * 0.3);
                    gainNode.gain.setValueAtTime(0.2, audioContext.currentTime + index * 0.3);
                    gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + index * 0.3 + 0.5);
                    
                    oscillator.start(audioContext.currentTime + index * 0.3);
                    oscillator.stop(audioContext.currentTime + index * 0.3 + 0.5);
                });
            }
        }

        // تهيئة التطبيق عند تحميل الصفحة
        document.addEventListener('DOMContentLoaded', initApp);
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'99e0c18bf4199350',t:'MTc2MzA2Mjk4NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>