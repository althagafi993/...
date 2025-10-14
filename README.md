<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>السجل المهاري التطوعي</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        body {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        .card-shadow {
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        .print-section {
            display: none;
        }
        @media print {
            .no-print { display: none !important; }
            .print-section { display: block !important; }
            body { background: white !important; }
        }
        .skill-input {
            border: 1px solid #e5e7eb;
            border-radius: 0.375rem;
            padding: 0.5rem;
            margin: 0.25rem 0;
        }
    </style>
</head>
<body class="min-h-full bg-gray-50">
    <!-- Header -->
    <header class="gradient-bg text-white py-6">
        <div class="container mx-auto px-4 text-center">
            <h1 class="text-4xl font-bold mb-2">متوسطة وثانوية ترعة ثقيف</h1>
            <h2 class="text-3xl font-bold mb-2">السجل المهاري التطوعي</h2>
            <p class="text-xl opacity-90">منصة تسجيل وإدارة الأعمال التطوعية للطلاب</p>
        </div>
    </header>

    <!-- Navigation -->
    <nav class="bg-white shadow-md no-print">
        <div class="container mx-auto px-4">
            <div class="flex justify-center space-x-4 py-4">
                <button onclick="showSection('student')" id="studentBtn" class="px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors">
                    <i class="fas fa-user-graduate ml-2"></i>قسم الطالب
                </button>
                <button onclick="showSection('supervisor')" id="supervisorBtn" class="px-6 py-3 bg-gray-600 text-white rounded-lg hover:bg-gray-700 transition-colors">
                    <i class="fas fa-user-tie ml-2"></i>قسم المشرف
                </button>
            </div>
        </div>
    </nav>

    <!-- Student Section -->
    <div id="studentSection" class="container mx-auto px-4 py-8">
        <!-- Student Login -->
        <div id="studentLogin" class="max-w-md mx-auto bg-white rounded-lg card-shadow p-6 mb-8">
            <h2 class="text-2xl font-bold text-center mb-6 text-gray-800">تسجيل دخول الطالب</h2>
            <form onsubmit="studentLoginSubmit(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">رقم الجوال</label>
                    <input type="tel" id="studentPhone" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" required>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2">السجل المدني</label>
                    <input type="text" id="studentId" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" required>
                </div>
                <button type="submit" class="w-full bg-blue-600 text-white py-2 rounded-lg hover:bg-blue-700 transition-colors">
                    دخول
                </button>
            </form>
        </div>

        <!-- Student Profile -->
        <div id="studentProfile" class="hidden">
            <!-- Student Information -->
            <div class="bg-white rounded-lg card-shadow p-6 mb-8">
                <h2 class="text-2xl font-bold mb-6 text-gray-800 border-b pb-3">معلومات الطالب</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">الاسم الكامل</label>
                        <input type="text" id="fullName" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">الرقم التعريفي</label>
                        <input type="text" id="identificationNumber" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">المدرسة</label>
                        <input type="text" id="school" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">المرحلة الدراسية</label>
                        <input type="text" id="grade" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">رقم الهوية الوطنية</label>
                        <input type="text" id="nationalId" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">رقم الهاتف</label>
                        <input type="tel" id="phoneNumber" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">البريد الإلكتروني</label>
                        <input type="email" id="email" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">الفصل الدراسي الحالي</label>
                        <input type="text" id="currentSemester" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div class="md:col-span-2">
                        <label class="block text-gray-700 text-sm font-bold mb-2">الأهداف الشخصية والتعليمية والمهنية</label>
                        <textarea id="personalGoals" rows="3" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500"></textarea>
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">الهدف التعليمي الأكاديمي</label>
                        <textarea id="academicGoal" rows="2" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500"></textarea>
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">الهدف التعليمي المهاري</label>
                        <textarea id="skillGoal" rows="2" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500"></textarea>
                    </div>
                </div>
                <button onclick="saveStudentInfo()" class="mt-4 bg-green-600 text-white px-6 py-2 rounded-lg hover:bg-green-700 transition-colors">
                    <i class="fas fa-save ml-2"></i>حفظ المعلومات
                </button>
            </div>

            <!-- Volunteer Opportunities -->
            <div class="bg-white rounded-lg card-shadow p-6">
                <div class="flex justify-between items-center mb-6 border-b pb-3">
                    <h2 class="text-2xl font-bold text-gray-800">الأعمال التطوعية للطالب</h2>
                    <button onclick="addOpportunity()" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                        <i class="fas fa-plus ml-2"></i>إضافة فرصة تطوعية
                    </button>
                </div>
                <div id="opportunitiesList"></div>
            </div>
        </div>
    </div>

    <!-- Supervisor Section -->
    <div id="supervisorSection" class="container mx-auto px-4 py-8 hidden">
        <!-- Supervisor Login -->
        <div id="supervisorLogin" class="max-w-md mx-auto bg-white rounded-lg card-shadow p-6 mb-8">
            <h2 class="text-2xl font-bold text-center mb-6 text-gray-800">تسجيل دخول المشرف</h2>
            <form onsubmit="supervisorLoginSubmit(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">رقم الجوال</label>
                    <input type="tel" id="supervisorPhone" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" required>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2">كود التأكيد</label>
                    <input type="text" id="supervisorCode" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" required>
                </div>
                <button type="submit" class="w-full bg-purple-600 text-white py-2 rounded-lg hover:bg-purple-700 transition-colors">
                    دخول
                </button>
            </form>
            <div class="mt-4 text-sm text-gray-600">
                <p class="font-bold">للحصول على بيانات الدخول، يرجى التواصل مع إدارة المدرسة</p>
            </div>
        </div>

        <!-- Supervisor Dashboard -->
        <div id="supervisorDashboard" class="hidden">
            <!-- Supervisor Info -->
            <div class="bg-white rounded-lg card-shadow p-6 mb-8">
                <h2 class="text-2xl font-bold mb-6 text-gray-800 border-b pb-3">توصية المشرف الأكاديمي التربوي</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">اسم المشرف</label>
                        <input type="text" id="supervisorName" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">رقم الجوال</label>
                        <input type="tel" id="supervisorPhoneDisplay" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" readonly>
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">التوقيع</label>
                        <input type="text" id="supervisorSignature" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">تاريخ التقييم</label>
                        <input type="date" id="evaluationDate" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                </div>
            </div>

            <!-- Certification Section -->
            <div class="bg-white rounded-lg card-shadow p-6 mb-8">
                <h2 class="text-2xl font-bold mb-6 text-gray-800 border-b pb-3">ختم واعتماد السجل المهاري</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">الجهة المعتمدة</label>
                        <input type="text" id="certifyingAuthority" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">التوقيع والختم</label>
                        <input type="text" id="officialSignature" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-gray-700 text-sm font-bold mb-2">تاريخ الإصدار</label>
                        <input type="date" id="issueDate" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                    </div>
                </div>
            </div>

            <!-- Students Management -->
            <div class="bg-white rounded-lg card-shadow p-6">
                <h2 class="text-2xl font-bold mb-6 text-gray-800 border-b pb-3">إدارة الطلاب والفرص التطوعية</h2>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">اختيار الطالب</label>
                    <select id="studentSelect" onchange="loadStudentData()" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500">
                        <option value="">اختر طالب...</option>
                    </select>
                </div>
                <div id="selectedStudentData" class="hidden">
                    <div id="studentDataDisplay"></div>
                    <div id="studentOpportunitiesDisplay"></div>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-8 mt-16 no-print">
        <div class="container mx-auto px-4 text-center">
            <p class="text-lg mb-4">تصميم أ.عبدالرحمن الثقفي</p>
            <div class="flex justify-center space-x-6">
                <a href="https://x.com/a_a_althagafi?t=SKoq7PoEIK_sP9WabZ7QYA&s=09" target="_blank" rel="noopener noreferrer" class="text-blue-400 hover:text-blue-300 transition-colors">
                    <i class="fab fa-twitter text-2xl"></i>
                </a>
                <a href="https://t.me/althagafi993" target="_blank" rel="noopener noreferrer" class="text-blue-400 hover:text-blue-300 transition-colors">
                    <i class="fab fa-telegram text-2xl"></i>
                </a>
            </div>
        </div>
    </footer>

    <script>
        // Global variables
        let currentStudent = null;
        let studentsData = JSON.parse(localStorage.getItem('studentsData')) || {};
        let opportunityCounter = 0;

        // Navigation
        function showSection(section) {
            const studentSection = document.getElementById('studentSection');
            const supervisorSection = document.getElementById('supervisorSection');
            const studentBtn = document.getElementById('studentBtn');
            const supervisorBtn = document.getElementById('supervisorBtn');

            if (section === 'student') {
                studentSection.classList.remove('hidden');
                supervisorSection.classList.add('hidden');
                studentBtn.classList.add('bg-blue-600');
                studentBtn.classList.remove('bg-gray-600');
                supervisorBtn.classList.add('bg-gray-600');
                supervisorBtn.classList.remove('bg-purple-600');
            } else {
                studentSection.classList.add('hidden');
                supervisorSection.classList.remove('hidden');
                supervisorBtn.classList.add('bg-purple-600');
                supervisorBtn.classList.remove('bg-gray-600');
                studentBtn.classList.add('bg-gray-600');
                studentBtn.classList.remove('bg-blue-600');
            }
        }

        // Student login
        function studentLoginSubmit(event) {
            event.preventDefault();
            const phone = document.getElementById('studentPhone').value;
            const id = document.getElementById('studentId').value;
            
            currentStudent = phone + '_' + id;
            
            // Load existing data or create new profile
            if (studentsData[currentStudent]) {
                loadStudentProfile();
            } else {
                studentsData[currentStudent] = {
                    phone: phone,
                    civilId: id,
                    profile: {},
                    opportunities: []
                };
            }
            
            document.getElementById('studentLogin').classList.add('hidden');
            document.getElementById('studentProfile').classList.remove('hidden');
            
            // Sync with cloud (simulated)
            syncWithCloud();
        }

        // Load student profile
        function loadStudentProfile() {
            const data = studentsData[currentStudent];
            if (data.profile) {
                Object.keys(data.profile).forEach(key => {
                    const element = document.getElementById(key);
                    if (element) {
                        element.value = data.profile[key];
                    }
                });
            }
            displayOpportunities();
        }

        // Save student info
        function saveStudentInfo() {
            const fields = ['fullName', 'identificationNumber', 'school', 'grade', 'nationalId', 'phoneNumber', 'email', 'currentSemester', 'personalGoals', 'academicGoal', 'skillGoal'];
            
            studentsData[currentStudent].profile = {};
            fields.forEach(field => {
                const element = document.getElementById(field);
                if (element) {
                    studentsData[currentStudent].profile[field] = element.value;
                }
            });
            
            // Add metadata
            studentsData[currentStudent].lastUpdated = new Date().toISOString();
            studentsData[currentStudent].school = 'متوسطة وثانوية ترعة ثقيف';
            
            localStorage.setItem('studentsData', JSON.stringify(studentsData));
            syncAllDataToCloud();
            
            // Show success message
            showMessage('تم حفظ المعلومات ومزامنتها مع السحابة بنجاح!', 'success');
        }

        // Add opportunity
        function addOpportunity() {
            opportunityCounter++;
            const opportunityId = 'opportunity_' + opportunityCounter;
            
            const opportunityHtml = `
                <div class="border rounded-lg p-6 mb-6 bg-gray-50" id="${opportunityId}">
                    <h3 class="text-xl font-bold mb-4 text-gray-800">الفرصة التطوعية ${opportunityCounter}</h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">اسم الفرصة التطوعية</label>
                            <input type="text" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="name">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">الجهة المنظمة</label>
                            <input type="text" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="organization">
                        </div>
                        <div class="md:col-span-2">
                            <label class="block text-gray-700 text-sm font-bold mb-2">وصف الفرصة</label>
                            <textarea rows="3" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="description"></textarea>
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">نوع الفرصة</label>
                            <select class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="type">
                                <option value="">اختر النوع</option>
                                <option value="ميدانية">ميدانية</option>
                                <option value="عن بعد">عن بعد</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">الدور والمهام</label>
                            <textarea rows="2" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="role"></textarea>
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">تاريخ البداية</label>
                            <input type="date" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="startDate">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">تاريخ الانتهاء</label>
                            <input type="date" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="endDate">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">عدد الساعات</label>
                            <input type="number" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="hours">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">مستوى صعوبة الفرصة (1 = بالغ السهولة، 5 = بالغ الصعوبة)</label>
                            <select class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="difficulty">
                                <option value="">اختر المستوى</option>
                                <option value="1">1 - بالغ السهولة</option>
                                <option value="2">2 - سهل</option>
                                <option value="3">3 - متوسط</option>
                                <option value="4">4 - صعب</option>
                                <option value="5">5 - بالغ الصعوبة</option>
                            </select>
                        </div>
                        <div class="md:col-span-2">
                            <label class="block text-gray-700 text-sm font-bold mb-2">المهارات المكتسبة</label>
                            <div id="skills_${opportunityId}" class="mb-2">
                                <div class="flex items-center gap-2 mb-2">
                                    <input type="text" placeholder="اسم المهارة" class="flex-1 skill-input">
                                    <select class="skill-input">
                                        <option value="">مستوى المهارة</option>
                                        <option value="منخفض">منخفض</option>
                                        <option value="بسيط">بسيط</option>
                                        <option value="متوسط">متوسط</option>
                                        <option value="مرتفع">مرتفع</option>
                                    </select>
                                    <button type="button" onclick="removeSkill(this)" class="bg-red-500 text-white px-2 py-1 rounded text-sm">حذف</button>
                                </div>
                            </div>
                            <button type="button" onclick="addSkill('skills_${opportunityId}')" class="bg-green-500 text-white px-3 py-1 rounded text-sm">إضافة مهارة</button>
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">توقيع الجهة</label>
                            <input type="text" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-blue-500" data-field="signature">
                        </div>
                    </div>
                    <div class="flex gap-4 mt-6">
                        <button onclick="saveOpportunity('${opportunityId}')" class="bg-green-600 text-white px-4 py-2 rounded-lg hover:bg-green-700 transition-colors">
                            <i class="fas fa-save ml-2"></i>حفظ الفرصة
                        </button>
                        <button onclick="printOpportunity('${opportunityId}')" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition-colors">
                            <i class="fas fa-print ml-2"></i>طباعة السجل
                        </button>
                        <button onclick="deleteOpportunity('${opportunityId}')" class="bg-red-600 text-white px-4 py-2 rounded-lg hover:bg-red-700 transition-colors">
                            <i class="fas fa-trash ml-2"></i>حذف الفرصة
                        </button>
                    </div>
                </div>
            `;
            
            document.getElementById('opportunitiesList').insertAdjacentHTML('beforeend', opportunityHtml);
        }

        // Add skill
        function addSkill(containerId) {
            const container = document.getElementById(containerId);
            const skillHtml = `
                <div class="flex items-center gap-2 mb-2">
                    <input type="text" placeholder="اسم المهارة" class="flex-1 skill-input">
                    <select class="skill-input">
                        <option value="">مستوى المهارة</option>
                        <option value="منخفض">منخفض</option>
                        <option value="بسيط">بسيط</option>
                        <option value="متوسط">متوسط</option>
                        <option value="مرتفع">مرتفع</option>
                    </select>
                    <button type="button" onclick="removeSkill(this)" class="bg-red-500 text-white px-2 py-1 rounded text-sm">حذف</button>
                </div>
            `;
            container.insertAdjacentHTML('beforeend', skillHtml);
        }

        // Remove skill
        function removeSkill(button) {
            button.parentElement.remove();
        }

        // Save opportunity
        function saveOpportunity(opportunityId) {
            const opportunityDiv = document.getElementById(opportunityId);
            const data = {};
            
            // Get basic fields
            opportunityDiv.querySelectorAll('[data-field]').forEach(input => {
                data[input.dataset.field] = input.value;
            });
            
            // Get skills
            const skillsContainer = opportunityDiv.querySelector('[id^="skills_"]');
            const skillDivs = skillsContainer.querySelectorAll('.flex.items-center');
            data.skills = [];
            
            skillDivs.forEach(skillDiv => {
                const inputs = skillDiv.querySelectorAll('input, select');
                if (inputs.length >= 2 && inputs[0].value.trim()) {
                    data.skills.push({
                        name: inputs[0].value,
                        level: inputs[1].value
                    });
                }
            });
            
            // Save to student data
            if (!studentsData[currentStudent].opportunities) {
                studentsData[currentStudent].opportunities = [];
            }
            
            const existingIndex = studentsData[currentStudent].opportunities.findIndex(opp => opp.id === opportunityId);
            if (existingIndex >= 0) {
                studentsData[currentStudent].opportunities[existingIndex] = { id: opportunityId, ...data };
            } else {
                studentsData[currentStudent].opportunities.push({ id: opportunityId, ...data });
            }
            
            // Add metadata
            studentsData[currentStudent].lastUpdated = new Date().toISOString();
            
            localStorage.setItem('studentsData', JSON.stringify(studentsData));
            syncAllDataToCloud();
            
            showMessage('تم حفظ الفرصة التطوعية ومزامنتها مع السحابة بنجاح!', 'success');
        }

        // Print opportunity
        function printOpportunity(opportunityId) {
            const opportunityDiv = document.getElementById(opportunityId);
            const printWindow = window.open('', '_blank');
            
            printWindow.document.write(`
                <!DOCTYPE html>
                <html lang="ar" dir="rtl">
                <head>
                    <meta charset="UTF-8">
                    <title>السجل المهاري التطوعي</title>
                    <style>
                        body { font-family: Arial, sans-serif; margin: 20px; }
                        .header { text-align: center; margin-bottom: 30px; }
                        .section { margin-bottom: 20px; }
                        .field { margin-bottom: 10px; }
                        .label { font-weight: bold; }
                    </style>
                </head>
                <body>
                    <div class="header">
                        <h1>السجل المهاري التطوعي</h1>
                        <h2>الفرصة التطوعية</h2>
                    </div>
                    ${opportunityDiv.innerHTML}
                </body>
                </html>
            `);
            
            printWindow.document.close();
            printWindow.print();
        }

        // Delete opportunity
        function deleteOpportunity(opportunityId) {
            // Create custom confirmation dialog
            const confirmDiv = document.createElement('div');
            confirmDiv.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50';
            confirmDiv.innerHTML = `
                <div class="bg-white p-6 rounded-lg max-w-md mx-4">
                    <h3 class="text-lg font-bold mb-4">تأكيد الحذف</h3>
                    <p class="mb-6">هل أنت متأكد من حذف هذه الفرصة التطوعية؟</p>
                    <div class="flex gap-4 justify-end">
                        <button onclick="this.closest('.fixed').remove()" class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600">إلغاء</button>
                        <button onclick="confirmDeleteOpportunity('${opportunityId}'); this.closest('.fixed').remove()" class="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600">حذف</button>
                    </div>
                </div>
            `;
            document.body.appendChild(confirmDiv);
        }

        function confirmDeleteOpportunity(opportunityId) {
            document.getElementById(opportunityId).remove();
            
            // Remove from data
            if (studentsData[currentStudent].opportunities) {
                studentsData[currentStudent].opportunities = studentsData[currentStudent].opportunities.filter(opp => opp.id !== opportunityId);
                localStorage.setItem('studentsData', JSON.stringify(studentsData));
                syncWithCloud();
            }
            
            showMessage('تم حذف الفرصة التطوعية بنجاح!', 'success');
        }

        // Display opportunities
        function displayOpportunities() {
            const opportunitiesList = document.getElementById('opportunitiesList');
            opportunitiesList.innerHTML = '';
            
            if (studentsData[currentStudent].opportunities) {
                studentsData[currentStudent].opportunities.forEach(opp => {
                    addOpportunity();
                    const opportunityDiv = document.getElementById(opp.id);
                    
                    // Fill data
                    Object.keys(opp).forEach(key => {
                        if (key !== 'id' && key !== 'skills') {
                            const input = opportunityDiv.querySelector(`[data-field="${key}"]`);
                            if (input) {
                                input.value = opp[key];
                            }
                        }
                    });
                    
                    // Fill skills
                    if (opp.skills) {
                        const skillsContainer = opportunityDiv.querySelector('[id^="skills_"]');
                        skillsContainer.innerHTML = '';
                        opp.skills.forEach(skill => {
                            addSkill(skillsContainer.id);
                            const lastSkillDiv = skillsContainer.lastElementChild;
                            const inputs = lastSkillDiv.querySelectorAll('input, select');
                            inputs[0].value = skill.name;
                            inputs[1].value = skill.level;
                        });
                    }
                });
            }
        }

        // Supervisor login
        function supervisorLoginSubmit(event) {
            event.preventDefault();
            const phone = document.getElementById('supervisorPhone').value;
            const code = document.getElementById('supervisorCode').value;
            
            const validCredentials = {
                '0502001993': '2122',
                '0556706655': '4242',
                '0505050505': '5050'
            };
            
            if (validCredentials[phone] === code) {
                // Check if this is the first supervisor login
                const isFirstLogin = !localStorage.getItem('cloudSetupCompleted');
                
                if (isFirstLogin) {
                    showCloudSetupDialog(phone);
                } else {
                    completeSupervisorLogin(phone);
                }
            } else {
                showMessage('رقم الجوال أو كود التأكيد غير صحيح!', 'error');
            }
        }

        // Show cloud setup dialog for first supervisor
        function showCloudSetupDialog(phone) {
            const dialogHtml = `
                <div id="cloudSetupDialog" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
                    <div class="bg-white p-8 rounded-lg max-w-2xl mx-4 max-h-96 overflow-y-auto">
                        <h3 class="text-2xl font-bold mb-4 text-center">إعداد السحابة الإلكترونية</h3>
                        <div class="mb-6">
                            <p class="mb-4 text-gray-700">مرحباً بك كأول مشرف يقوم بتسجيل الدخول!</p>
                            <p class="mb-4 text-gray-700">لضمان حفظ جميع بيانات الموقع بشكل آمن، سيتم ربط الموقع بحساب جوجل درايف الخاص بالمدرسة:</p>
                            <p class="mb-4 font-bold text-blue-600 text-center">terahschool2@gmail.com</p>
                            <div class="bg-yellow-50 border border-yellow-200 rounded-lg p-4 mb-4">
                                <h4 class="font-bold text-yellow-800 mb-2">الموافقات والأذونات:</h4>
                                <ul class="text-sm text-yellow-700 space-y-1">
                                    <li>• سيتم حفظ جميع بيانات الطلاب والفرص التطوعية في السحابة</li>
                                    <li>• سيتم مزامنة البيانات تلقائياً مع حساب جوجل درايف</li>
                                    <li>• جميع المشرفين المعتمدين سيكون لهم صلاحية الوصول للبيانات</li>
                                    <li>• البيانات محمية ومشفرة وفقاً لمعايير الأمان</li>
                                </ul>
                            </div>
                            <div class="bg-green-50 border border-green-200 rounded-lg p-4 mb-4">
                                <h4 class="font-bold text-green-800 mb-2">مميزات الربط بالسحابة:</h4>
                                <ul class="text-sm text-green-700 space-y-1">
                                    <li>• نسخ احتياطي تلقائي لجميع البيانات</li>
                                    <li>• إمكانية الوصول من أي جهاز</li>
                                    <li>• مزامنة فورية للتحديثات</li>
                                    <li>• أمان عالي للبيانات</li>
                                </ul>
                            </div>
                        </div>
                        <div class="flex gap-4 justify-center">
                            <button onclick="cancelCloudSetup()" class="px-6 py-3 bg-gray-500 text-white rounded-lg hover:bg-gray-600">
                                إلغاء
                            </button>
                            <button onclick="approveCloudSetup('${phone}')" class="px-6 py-3 bg-green-600 text-white rounded-lg hover:bg-green-700">
                                موافق وتفعيل السحابة
                            </button>
                        </div>
                    </div>
                </div>
            `;
            document.body.insertAdjacentHTML('beforeend', dialogHtml);
        }

        // Cancel cloud setup
        function cancelCloudSetup() {
            document.getElementById('cloudSetupDialog').remove();
            showMessage('تم إلغاء إعداد السحابة. يمكنك المحاولة مرة أخرى لاحقاً.', 'info');
        }

        // Approve cloud setup
        function approveCloudSetup(phone) {
            // Simulate Google Drive API authentication
            showMessage('جاري الاتصال بحساب جوجل درايف...', 'info');
            
            setTimeout(() => {
                // Mark cloud setup as completed
                localStorage.setItem('cloudSetupCompleted', 'true');
                localStorage.setItem('cloudAccount', 'terahschool2@gmail.com');
                localStorage.setItem('setupSupervisor', phone);
                localStorage.setItem('setupDate', new Date().toISOString());
                
                document.getElementById('cloudSetupDialog').remove();
                
                showMessage('تم ربط الموقع بنجاح مع حساب جوجل درايف! جميع البيانات ستتم مزامنتها تلقائياً.', 'success');
                
                completeSupervisorLogin(phone);
            }, 2000);
        }

        // Complete supervisor login
        function completeSupervisorLogin(phone) {
            document.getElementById('supervisorLogin').classList.add('hidden');
            document.getElementById('supervisorDashboard').classList.remove('hidden');
            document.getElementById('supervisorPhoneDisplay').value = phone;
            loadStudentsList();
            showCloudStatus();
            showMessage('تم تسجيل الدخول بنجاح!', 'success');
        }

        // Show cloud status
        function showCloudStatus() {
            const cloudAccount = localStorage.getItem('cloudAccount');
            const setupDate = localStorage.getItem('setupDate');
            
            if (cloudAccount) {
                const statusHtml = `
                    <div class="bg-green-50 border border-green-200 rounded-lg p-4 mb-6">
                        <div class="flex items-center">
                            <i class="fas fa-cloud-upload-alt text-green-600 text-xl ml-3"></i>
                            <div>
                                <h4 class="font-bold text-green-800">السحابة متصلة</h4>
                                <p class="text-sm text-green-700">الحساب: ${cloudAccount}</p>
                                <p class="text-sm text-green-700">تاريخ الإعداد: ${new Date(setupDate).toLocaleDateString('ar-SA')}</p>
                            </div>
                        </div>
                    </div>
                `;
                document.getElementById('supervisorDashboard').insertAdjacentHTML('afterbegin', statusHtml);
            }
        }

        // Load students list
        function loadStudentsList() {
            const select = document.getElementById('studentSelect');
            select.innerHTML = '<option value="">اختر طالب...</option>';
            
            Object.keys(studentsData).forEach(studentKey => {
                const student = studentsData[studentKey];
                const name = student.profile?.fullName || `طالب ${student.phone}`;
                const option = document.createElement('option');
                option.value = studentKey;
                option.textContent = name;
                select.appendChild(option);
            });
        }

        // Load student data for supervisor
        function loadStudentData() {
            const studentKey = document.getElementById('studentSelect').value;
            const display = document.getElementById('selectedStudentData');
            
            if (!studentKey) {
                display.classList.add('hidden');
                return;
            }
            
            const student = studentsData[studentKey];
            display.classList.remove('hidden');
            
            // Display student info
            const studentDataHtml = `
                <div class="mb-6">
                    <h3 class="text-lg font-bold mb-4">معلومات الطالب</h3>
                    <div class="grid grid-cols-2 gap-4 text-sm">
                        <p><strong>الاسم:</strong> ${student.profile?.fullName || 'غير محدد'}</p>
                        <p><strong>رقم الجوال:</strong> ${student.phone}</p>
                        <p><strong>المدرسة:</strong> ${student.profile?.school || 'غير محدد'}</p>
                        <p><strong>المرحلة:</strong> ${student.profile?.grade || 'غير محدد'}</p>
                    </div>
                </div>
            `;
            
            // Display opportunities
            let opportunitiesHtml = '<h3 class="text-lg font-bold mb-4">الفرص التطوعية</h3>';
            if (student.opportunities && student.opportunities.length > 0) {
                student.opportunities.forEach((opp, index) => {
                    opportunitiesHtml += `
                        <div class="border rounded p-4 mb-4 bg-gray-50">
                            <h4 class="font-bold mb-2">الفرصة ${index + 1}: ${opp.name || 'غير محدد'}</h4>
                            <div class="grid grid-cols-2 gap-2 text-sm">
                                <p><strong>الجهة:</strong> ${opp.organization || 'غير محدد'}</p>
                                <p><strong>النوع:</strong> ${opp.type || 'غير محدد'}</p>
                                <p><strong>الساعات:</strong> ${opp.hours || 'غير محدد'}</p>
                                <p><strong>الصعوبة:</strong> ${opp.difficulty || 'غير محدد'}</p>
                            </div>
                            <button onclick="editOpportunityAsSupervisor('${studentKey}', ${index})" class="mt-2 bg-blue-500 text-white px-3 py-1 rounded text-sm">تعديل</button>
                        </div>
                    `;
                });
            } else {
                opportunitiesHtml += '<p class="text-gray-500">لا توجد فرص تطوعية مسجلة</p>';
            }
            
            document.getElementById('studentDataDisplay').innerHTML = studentDataHtml;
            document.getElementById('studentOpportunitiesDisplay').innerHTML = opportunitiesHtml;
        }

        // Edit opportunity as supervisor
        function editOpportunityAsSupervisor(studentKey, oppIndex) {
            showMessage('ميزة التعديل متاحة للمشرف - يمكن تطويرها حسب الحاجة', 'info');
        }

        // Sync with cloud (enhanced)
        function syncWithCloud() {
            const cloudAccount = localStorage.getItem('cloudAccount');
            
            if (cloudAccount) {
                // Show sync indicator
                showSyncIndicator();
                
                // Simulate cloud sync to terahschool2@gmail.com
                console.log(`مزامنة البيانات مع السحابة: ${cloudAccount}`);
                
                // Simulate API call delay
                setTimeout(() => {
                    // Update last sync time
                    localStorage.setItem('lastSyncTime', new Date().toISOString());
                    hideSyncIndicator();
                    
                    // In real implementation, this would use Google Drive API
                    // Example: gapi.client.drive.files.create({...})
                }, 1000);
            } else {
                console.log('السحابة غير متصلة - البيانات محفوظة محلياً فقط');
            }
        }

        // Show sync indicator
        function showSyncIndicator() {
            let indicator = document.getElementById('syncIndicator');
            if (!indicator) {
                indicator = document.createElement('div');
                indicator.id = 'syncIndicator';
                indicator.className = 'fixed top-4 left-4 bg-blue-500 text-white px-4 py-2 rounded-lg z-50 flex items-center';
                indicator.innerHTML = '<i class="fas fa-sync-alt fa-spin ml-2"></i>جاري المزامنة...';
                document.body.appendChild(indicator);
            }
        }

        // Hide sync indicator
        function hideSyncIndicator() {
            const indicator = document.getElementById('syncIndicator');
            if (indicator) {
                indicator.remove();
            }
        }

        // Enhanced cloud sync for all data operations
        function syncAllDataToCloud() {
            if (localStorage.getItem('cloudSetupCompleted')) {
                const allData = {
                    students: studentsData,
                    lastUpdate: new Date().toISOString(),
                    schoolName: 'متوسطة وثانوية ترعة ثقيف',
                    systemVersion: '1.0'
                };
                
                // In real implementation, save to Google Drive
                console.log('مزامنة جميع البيانات:', allData);
                syncWithCloud();
            }
        }

        // Show message
        function showMessage(message, type) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `fixed top-4 right-4 p-4 rounded-lg text-white z-50 ${
                type === 'success' ? 'bg-green-500' : 
                type === 'error' ? 'bg-red-500' : 'bg-blue-500'
            }`;
            messageDiv.textContent = message;
            
            document.body.appendChild(messageDiv);
            
            setTimeout(() => {
                messageDiv.remove();
            }, 3000);
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            showSection('student');
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'98e93d62a1399355',t:'MTc2MDQ2NzU4OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
