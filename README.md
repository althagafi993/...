<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>السجل المهاري التطوعي – الإصدار السحابي</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
<style>
  body { font-family: 'Cairo', system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial; }
  /* Modal backdrop */
  .modal-backdrop { background: rgba(0,0,0,0.45); }

  /* New styles for floating label and button consistency */
  .floating-label {
      position: relative;
      margin-bottom: 20px;
  }
  .floating-label input {
      width: 100%;
      padding: 16px 12px 8px 12px;
      border: 1px solid #e5e7eb;
      border-radius: 0.5rem;
      background: white;
      font-size: 16px;
      transition: all 0.3s ease;
  }
  .floating-label label {
      position: absolute;
      top: 16px;
      right: 12px;
      font-size: 16px;
      color: #6b7280;
      transition: all 0.3s ease;
      pointer-events: none;
      padding: 0 4px;
  }
  .floating-label input:focus + label,
  .floating-label input:not(:placeholder-shown) + label {
      top: -8px;
      font-size: 12px;
      color: #4f46e5;
      background: #f9fafb;
      font-weight: 600;
  }
</style>
<script src="https://apis.google.com/js/api.js" defer></script>
</head>
<body class="bg-gray-50 min-h-screen text-gray-800">

<header class="bg-gradient-to-r from-blue-600 to-indigo-700 text-white py-6 shadow relative">
  <div class="container mx-auto flex items-center justify-between px-4">
    <div class="flex items-center gap-4">
      <div id="logoContainer" class="w-16 h-16 bg-white rounded-full flex items-center justify-center p-1 shadow-lg">
        <i class="fas fa-school text-indigo-700 text-3xl"></i>
      </div>
      <h1 class="text-2xl font-bold">السجل المهاري التطوعي</h1>
    </div>
    
    <div class="flex flex-col md:flex-row items-center gap-4 text-sm">
        <button id="driveConnectBtn" 
                class="px-3 py-1 bg-white/20 hover:bg-white/30 rounded-md transition duration-200 font-medium">
            ربط بـ Google Drive
        </button>
        <div id="cloudStatus" class="bg-white/10 px-3 py-2 rounded-md">
            <i class="fa fa-cloud ml-2"></i> السحابة: <span id="cloudLabel" class="text-red-300">محلية (LocalStorage)</span>
        </div>
    </div>
  </div>
</header>

<div class="container mx-auto px-4 mt-6">
  <div class="flex justify-center gap-4">
    <button id="studentTab" onclick="showSection('student')" class="px-6 py-3 bg-indigo-600 text-white rounded-2xl shadow">قسم الطالب</button>
    <button id="supervisorTab" onclick="showSection('supervisor')" class="px-6 py-3 bg-gray-200 text-gray-700 rounded-2xl shadow">قسم المشرف</button>
  </div>
</div>

<main class="container mx-auto px-4 mt-8">

  <section id="studentSection" class="">
    <div id="studentLogin" class="max-w-lg mx-auto bg-white rounded-3xl shadow p-8">
      <div class="text-center mb-6">
        <i class="fa fa-user-graduate text-4xl text-indigo-600 mb-4"></i>
        <h2 class="text-2xl font-bold">تسجيل دخول الطالب</h2>
        <p class="text-gray-600">أدخل بياناتك للوصول إلى سجلك</p>
      </div>
      <form onsubmit="studentLoginSubmit(event)">
        <div class="floating-label">
            <input type="tel" id="studentPhone" placeholder=" " required>
            <label>رقم الجوال</label>
        </div>
        <div class="floating-label">
            <input type="text" id="studentId" placeholder=" " required>
            <label>السجل المدني</label>
        </div>
        <button type="submit" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-3 px-4 rounded-xl transition duration-200">
          دخول إلى السجل
        </button>
      </form>
    </div>
    
    <div id="studentProfile" class="hidden">
        <h3 class="text-xl font-bold mb-4">سجل الطالب المهاري</h3>
        </div>
  </section>

  <section id="supervisorSection" class="hidden">
    <div id="supervisorLogin" class="max-w-lg mx-auto bg-white rounded-3xl shadow p-8">
      <div class="text-center mb-6">
        <i class="fa fa-user-tie text-4xl text-purple-600 mb-4"></i>
        <h2 class="text-2xl font-bold">تسجيل دخول المشرف</h2>
        <p class="text-gray-600">أدخل بياناتك للتحكم والمزامنة السحابية</p>
      </div>
      <form onsubmit="supervisorLoginSubmit(event)">
        <div class="floating-label">
            <input type="text" id="supervisorCode" placeholder=" " required>
            <label>رمز المشرف</label>
        </div>
        <button type="submit" class="w-full bg-purple-600 hover:bg-purple-700 text-white font-bold py-3 px-4 rounded-xl transition duration-200">
          دخول وربط السحابة
        </button>
      </form>
    </div>

    <div id="supervisorDashboard" class="hidden">
        <h3 class="text-xl font-bold mb-4">لوحة تحكم المشرف</h3>
        </div>
  </section>
</main>


<script>
    // =======================================================
    // إعدادات Google Drive API (يجب استبدالها بقيمك الحقيقية)
    // =======================================================
    const CLIENT_ID = 'YOUR_CLIENT_ID.apps.googleusercontent.com'; // 💡 استبدل هنا
    const API_KEY = 'YOUR_API_KEY'; // 💡 استبدل هنا (إذا لزم الأمر)
    const DISCOVERY_DOCS = ["https://www.googleapis.com/discovery/v1/apis/drive/v3/rest"];
    const SCOPES = 'https://www.googleapis.com/auth/drive.file profile'; 

    // حالة التطبيق
    let authInstance;
    let driveFileId = null;
    const DRIVE_FILENAME = 'volunteer_log_data.json';
    const STORAGE_MODE_DRIVE = 'drive';
    const STORAGE_MODE_LOCAL = 'local';
    let currentStorageMode = STORAGE_MODE_LOCAL; 

    // =======================================================
    // 1. وظائف التنقل (تمت إضافتها لحل مشكلة اختفاء الصفحة)
    // =======================================================
    
    /**
     * تبديل عرض الأقسام الرئيسية (الطالب/المشرف)
     */
    function showSection(sectionId) {
        // إخفاء جميع الأقسام
        document.getElementById('studentSection').classList.add('hidden');
        document.getElementById('supervisorSection').classList.add('hidden');
        
        // إزالة حالة النشاط من جميع أزرار التبويبات
        document.getElementById('studentTab').classList.remove('bg-indigo-600', 'text-white');
        document.getElementById('studentTab').classList.add('bg-gray-200', 'text-gray-700');
        document.getElementById('supervisorTab').classList.remove('bg-purple-600', 'text-white');
        document.getElementById('supervisorTab').classList.add('bg-gray-200', 'text-gray-700');

        // إظهار القسم المطلوب
        const targetSection = document.getElementById(sectionId + 'Section');
        if (targetSection) {
            targetSection.classList.remove('hidden');
            // تفعيل زر التبويب
            const targetTab = document.getElementById(sectionId + 'Tab');
            if (targetTab) {
                targetTab.classList.remove('bg-gray-200', 'text-gray-700');
                targetTab.classList.add(sectionId === 'student' ? 'bg-indigo-600' : 'bg-purple-600', 'text-white');
            }
        }
    }


    // =======================================================
    // 2. وظائف Google Drive API والتهيئة
    // =======================================================

    function updateCloudStatus() {
        // ... (منطق تحديث حالة السحابة كما ورد سابقًا) ...
        const cloudLabel = document.getElementById('cloudLabel');
        const connectButton = document.getElementById('driveConnectBtn');

        if (!cloudLabel || !connectButton) return;

        if (!authInstance || !authInstance.isSignedIn.get()) {
            currentStorageMode = STORAGE_MODE_LOCAL;
        }

        if (currentStorageMode === STORAGE_MODE_DRIVE) {
            cloudLabel.textContent = 'سحابية (Google Drive)';
            cloudLabel.className = 'text-green-300';
            connectButton.textContent = 'قطع الاتصال بـ Drive';
            connectButton.onclick = handleSignoutClick;
            connectButton.classList.remove('bg-white/20');
            connectButton.classList.add('bg-red-500/50');
        } else {
            cloudLabel.textContent = 'محلية (LocalStorage)';
            cloudLabel.className = 'text-red-300';
            connectButton.textContent = 'ربط بـ Google Drive';
            connectButton.onclick = handleAuthClick;
            connectButton.classList.remove('bg-red-500/50');
            connectButton.classList.add('bg-white/20');
        }
    }

    function initClient() {
        if (CLIENT_ID.includes('YOUR_CLIENT_ID')) {
             console.error("Please replace YOUR_CLIENT_ID with your actual Google Client ID.");
             document.getElementById('cloudLabel').textContent = 'خطأ: لم يتم تعيين Client ID';
             return;
        }

        gapi.client.init({
            apiKey: API_KEY,
            clientId: CLIENT_ID,
            discoveryDocs: DISCOVERY_DOCS,
            scope: SCOPES
        }).then(() => {
            authInstance = gapi.auth2.getAuthInstance();
            authInstance.isSignedIn.listen(updateCloudStatus);
            
            if (authInstance.isSignedIn.get()) {
                currentStorageMode = STORAGE_MODE_DRIVE;
                connectDriveAndLoad();
            }
            updateCloudStatus();
        }, error => {
            console.error("Error initializing GAPI client:", error);
            document.getElementById('cloudLabel').textContent = 'خطأ في تهيئة API';
        });
    }

    function handleAuthClick() {
        authInstance.signIn().then(() => {
            currentStorageMode = STORAGE_MODE_DRIVE;
            connectDriveAndLoad();
        });
    }

    function handleSignoutClick() {
        authInstance.signOut();
        currentStorageMode = STORAGE_MODE_LOCAL;
        driveFileId = null;
        updateCloudStatus();
    }
    
    function connectDriveAndLoad() {
        findOrCreateDriveFile().then(id => {
            driveFileId = id;
            updateCloudStatus();
            // يتم تحميل البيانات تلقائياً بعد الربط
            loadData().then(data => console.log('Loaded data from Drive:', data));
        }).catch(err => {
            console.error("Failed to connect or find file on Drive:", err);
            currentStorageMode = STORAGE_MODE_LOCAL;
            updateCloudStatus();
        });
    }
    
    // (دوال findOrCreateDriveFile, saveData, loadData تظل كما هي في الكود السابق)

    /**
     * تبحث عن ملف البيانات أو تنشئ ملفًا جديدًا إذا لم يكن موجودًا
     */
    function findOrCreateDriveFile() {
        return new Promise((resolve, reject) => {
            gapi.client.drive.files.list({
                q: `name='${DRIVE_FILENAME}' and trashed=false`,
                fields: 'files(id, name)',
                spaces: 'drive',
            }).then(response => {
                const files = response.result.files;
                if (files.length > 0) { resolve(files[0].id); } 
                else {
                    const fileMetadata = { 'name': DRIVE_FILENAME, 'mimeType': 'application/json' };
                    const initialContent = JSON.stringify({ students: [], opportunities: [], settings: {} });
                    
                    const boundary = 'foo_bar_baz';
                    const delimiter = "\r\n--" + boundary + "\r\n";
                    const close_delimiter = "\r\n--" + boundary + "--";

                    const multipartRequestBody =
                        delimiter + 'Content-Type: application/json\r\n\r\n' + JSON.stringify(fileMetadata) +
                        delimiter + 'Content-Type: application/json\r\n\r\n' + initialContent +
                        close_delimiter;

                    gapi.client.request({
                        'path': '/upload/drive/v3/files',
                        'method': 'POST',
                        'params': {'uploadType': 'multipart'},
                        'headers': { 'Content-Type': 'multipart/mixed; boundary="' + boundary + '"' },
                        'body': multipartRequestBody
                    }).then(res => resolve(res.result.id), err => reject(err));
                }
            }, err => reject(err));
        });
    }

    window.saveData = function(data) {
        if (currentStorageMode === STORAGE_MODE_DRIVE && driveFileId) {
            const content = JSON.stringify(data);
            const boundary = 'foo_bar_baz';
            const delimiter = "\r\n--" + boundary + "\r\n";
            const close_delimiter = "\r\n--" + boundary + "--";
            const contentType = 'application/json';
            const metadata = { 'mimeType': contentType };

            const multipartRequestBody =
                delimiter + 'Content-Type: application/json\r\n\r\n' + JSON.stringify(metadata) +
                delimiter + 'Content-Type: ' + contentType + '\r\n\r\n' + content +
                close_delimiter;

            gapi.client.request({
                'path': '/upload/drive/v3/files/' + driveFileId,
                'method': 'PATCH',
                'params': {'uploadType': 'multipart'},
                'headers': { 'Content-Type': 'multipart/mixed; boundary="' + boundary + '"' },
                'body': multipartRequestBody
            }).then(() => console.log('Data saved to Google Drive.'), err => console.error('Error saving to Drive:', err));

        } else {
            localStorage.setItem('appData', JSON.stringify(data));
            console.log('Data saved to LocalStorage.');
        }
    }

    window.loadData = function() {
        if (currentStorageMode === STORAGE_MODE_DRIVE && driveFileId) {
            return gapi.client.drive.files.get({
                fileId: driveFileId,
                alt: 'media'
            }).then(response => {
                console.log('Data loaded from Google Drive.');
                return response.result; 
            }, err => {
                console.error('Error loading data from Drive. Reverting to local data.', err);
                return JSON.parse(localStorage.getItem('appData') || '{}');
            });
        } else {
            const data = localStorage.getItem('appData');
            console.log('Data loaded from LocalStorage.');
            return Promise.resolve(JSON.parse(data || '{}'));
        }
    }


    // =======================================================
    // 3. وظائف تسجيل الدخول
    // =======================================================

    window.studentLoginSubmit = function(event) {
        event.preventDefault();
        alert('تم محاكاة دخول الطالب. هنا يجب أن يظهر سجل الطالب بعد التحقق.');
        // هنا يمكنك إظهار قسم الملف الشخصي للطالب وإخفاء شاشة الدخول
        document.getElementById('studentLogin').classList.add('hidden');
        document.getElementById('studentProfile').classList.remove('hidden');
        
        loadData().then(data => console.log('Student data loaded:', data));
    };
    
    /**
     * وظيفة تسجيل دخول المشرف (مربوطة بالربط السحابي)
     */
    window.supervisorLoginSubmit = function(event) {
        event.preventDefault();
        const supervisorCode = document.getElementById('supervisorCode').value;
        
        if (supervisorCode === '12345') { // 💡 يجب استبدال هذا بمنطق تحقق حقيقي
             alert('تم تسجيل دخول المشرف بنجاح.');
             
             // إخفاء شاشة الدخول وإظهار لوحة التحكم
             document.getElementById('supervisorLogin').classList.add('hidden');
             document.getElementById('supervisorDashboard').classList.remove('hidden');

            // 💡 عند نجاح تسجيل الدخول، ابدأ عملية ربط Google Drive إذا لم يكن متصلاً
            if (!authInstance.isSignedIn.get()) {
                handleAuthClick(); 
            } else {
                currentStorageMode = STORAGE_MODE_DRIVE;
                updateCloudStatus();
                loadData().then(data => console.log('Supervisor logged in, data loaded from Drive.'));
            }
        } else {
             alert('رمز المشرف غير صحيح.');
        }
    };


    // عند تحميل الصفحة، ابدأ بتهيئة API وعرض قسم الطالب الافتراضي
    window.addEventListener('load', () => {
         if (typeof gapi !== 'undefined') {
            gapi.load('client:auth2', initClient);
        }
        showSection('student');
    });
</script>
</body>
</html>
