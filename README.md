<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق ترتيب الجملة (طريقة النقر)</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
    
    <style>
        /* === 1. تنسيقات CSS (التصميم والألوان) === */
        
        /* تطبيق اتجاه الكتابة والخط */
        .container, .word-bank, .sentence-area {
            direction: rtl;
            font-family: 'Cairo', sans-serif; 
        }

        body {
            background-color: #f4f7f9;
            display: flex;
            justify-content: center;
            padding: 20px;
        }

        .container {
            width: 90%;
            max-width: 800px;
            background-color: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            color: #333;
            margin-bottom: 25px;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
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
            border: 1px solid #CCCCCC; /* حد رمادي ناعم */
            border-radius: 30px; /* جعلها مستديرة أكثر */
            background-color: #F5F5F5; /* خلفية رمادية فاتحة */
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
        }

        /* منطقة الجملة المرتبة (حيث تظهر الكلمات بعد النقر) */
        .sentence-area {
            margin: 20px 0;
            padding: 20px;
            border: 2px dashed #B0BEC5; /* حد متقطع فاتح */
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
            align-self: center; /* توسيط النص التمهيدي */
        }
        
        .sentence-area .word-card {
            cursor: default; /* منع النقر عليها مرة أخرى */
            box-shadow: none; /* إزالة الظل في منطقة العرض */
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
    
    <div class="container">
        <h2>رتب الكلمات لتكوين جملة مفيدة</h2>

        <div id="word-bank" class="word-bank">
            <div class="word-card" data-word="سافر">سافر</div>
            <div class="word-card" data-word="جدة">جدة</div>
            <div class="word-card" data-word="محمد">محمد</div>
            <div class="word-card" data-word="إلى">إلى</div>
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

    <script>
        /* === 2. منطق JavaScript (الآلية التفاعلية) === */
        document.addEventListener('DOMContentLoaded', () => {
            // ** 1. الترتيب الصحيح للجملة - يمكنك تغيير هذا لكل تمرين جديد **
            const CORRECT_ORDER = ["سافر", "محمد", "إلى", "جدة"];
            
            // العناصر البرمجية الأساسية
            const wordBank = document.getElementById('word-bank');
            const sentenceArea = document.getElementById('sentence-area');
            const checkButton = document.getElementById('check-button');
            const resetButton = document.getElementById('reset-button');
            const feedbackElement = document.getElementById('feedback');
            const wordCards = Array.from(document.querySelectorAll('.word-card'));

            let userOrder = []; // الترتيب الذي اختارته الطالبة (سيخزن الكلمات كـ strings)

            // توزيع الكلمات عشوائيًا عند تحميل الصفحة
            wordCards.sort(() => Math.random() - 0.5).forEach(card => wordBank.appendChild(card));
            
            // عنصر النص التمهيدي
            const placeholder = sentenceArea.querySelector('.placeholder');
            
            // دالة معالجة النقر
            const handleWordClick = (event) => {
                const card = event.currentTarget;
                const word = card.getAttribute('data-word');

                // منع النقر على الكلمة المختارة مسبقاً
                if (card.classList.contains('selected')) {
                    return;
                }

                // 2. الإضافة والتحديث الداخلي
                userOrder.push(word);
                
                // 3. التحديث البصري والترقيم
                card.classList.add('selected');
                
                // إضافة أيقونة الترقيم
                const badge = document.createElement('span');
                badge.classList.add('order-badge');
                badge.textContent = userOrder.length; 
                card.appendChild(badge);

                // إخفاء النص التمهيدي
                if (placeholder) {
                    placeholder.style.display = 'none';
                }

                // إنشاء نسخة من البطاقة لإضافتها لمنطقة الترتيب
                const orderedCard = card.cloneNode(true);
                orderedCard.removeEventListener('click', handleWordClick); 
                sentenceArea.appendChild(orderedCard);
                
                // مسح رسالة التغذية الراجعة القديمة
                feedbackElement.textContent = '';
                feedbackElement.className = 'feedback';
            };

            // ربط دالة النقر بكل كلمة
            wordCards.forEach(card => {
                card.addEventListener('click', handleWordClick);
            });
            
            // دالة التصحيح (عند النقر على "تحقق")
            checkButton.addEventListener('click', () => {
                // التحقق من اكتمال الجملة
                if (userOrder.length !== CORRECT_ORDER.length) {
                    feedbackElement.textContent = 'الرجاء إكمال الجملة أولاً.';
                    feedbackElement.className = 'feedback incorrect';
                    return;
                }

                // مقارنة الترتيب
                const isCorrect = userOrder.every((word, index) => word === CORRECT_ORDER[index]);

                if (isCorrect) {
                    // حالة النجاح
                    feedbackElement.textContent = '🏆 أحسنتِ! الترتيب صحيح وممتاز.';
                    feedbackElement.className = 'feedback correct';
                    
                    // تظليل الكلمات في منطقة الترتيب بالأخضر كإشارة نهائية
                    Array.from(sentenceArea.children).forEach(card => {
                        card.style.backgroundColor = '#C8E6C9';
                    });
                    
                } else {
                    // حالة الخطأ
                    feedbackElement.textContent = '❌ هناك خطأ في الترتيب. حاولي مرة أخرى!';
                    feedbackElement.className = 'feedback incorrect';
                }
            });
            
            // دالة إعادة الترتيب
            resetButton.addEventListener('click', () => {
                // إعادة تهيئة المتغيرات
                userOrder = [];
                
                // إعادة الواجهة البصرية لحالتها الافتراضية
                sentenceArea.innerHTML = '';
                if (placeholder) {
                    sentenceArea.appendChild(placeholder);
                    placeholder.style.display = 'block';
                }
                
                wordCards.forEach(card => {
                    card.classList.remove('selected');
                    // إزالة شارات الترقيم
                    const badge = card.querySelector('.order-badge');
                    if (badge) {
                        card.removeChild(badge);
                    }
                    card.style.backgroundColor = ''; // إزالة تظليل النجاح إن وجد
                });
                
                feedbackElement.textContent = '';
                feedbackElement.className = 'feedback';
            });
        });
    </script>
</body>
</html>
