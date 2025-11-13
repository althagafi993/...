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
            flex-direction: column; /* لترتيب الترقيم والنص */
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }
        
        /* تنسيق الترقيم */
        .drop-zone .drop-label { 
            font-size: 0.9rem;
            color: #666;
            margin-bottom: 5px;
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
   </header><div id="name-registration" class="name-registration">
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
    </div><div id="level-1" class="level-content">
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
    </div><div id="level-2" class="level-content hidden">
     <div class="word-display">
      <div class="current-word" id="target-word">
       قرأ
      </div>
      <div class="word-meaning">
       رتب الأحرف لتكوين الكلمة بالترقيم
      </div>
     </div>
     <div class="drag-drop-area" id="letters-container"></div>
     <div class="drag-drop-area" id="word-builder"></div>
     <div class="controls"><button class="control-btn" id="check-word">✅ تحقق من الكلمة</button> <button class="control-btn" id="reset-letters">🔄 إعادة ترتيب</button>
     </div>
    </div><div id="level-3" class="level-content hidden">
     <div class="word-display">
      <div class="current-word">
       كون جملة مفيدة
      </div>
      <div class="word-meaning">
       اسحب الكلمات لتكوين جملة صحيحة بالترقيم
      </div>
     </div>
     <div class="drag-drop-area" id="words-container"></div>
     <div class="drag-drop-area" id="sentence-builder"></div>
     <div class="controls"><button class="control-btn" id="check-sentence">✅ تحقق من الجملة</button> <button class="control-btn" id="reset-words">🔄 إعادة ترتيب</button>
     </div>
    </div><div id="level-4" class="level-content hidden">
     <div class="word-display">
      <div class="current-word" id="incomplete-word">
       مدر_ة
      </div>
      <div class="word-meaning">
       اختر الحرف المناسب لإكمال الكلمة
      </div>
     </div>
     <div class="multiple-choice" id="choices-container"></div>
    </div>
    <div class="feedback" id="feedback"></div>
   </main><div id="certificate" class="certificate hidden">
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
   <div class="celebration" id="celebration"></div><div class="signature">
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
        // دالة مساعدة لخلط المصفوفة (لضمان عدم ترتيب الإجابات)
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }

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
