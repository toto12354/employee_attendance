<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="style.css">
    <title>لوحة التحكم</title>
    <style>
        /* تنسيق الحاوية الأساسية */
        .dashboard-container {
            text-align: center;
            margin-top: 50px;
            padding: 20px;
        }
        
        /* تنسيق حاوية الأزرار */
        .button-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px; /* مسافة بين الأزرار */
        }

        /* تنسيق الأزرار */
        .action-button {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            font-size: 16px;
            cursor: pointer;
            border: 2px solid #2980b9;
            border-radius: 8px;
            background-color: #34495e;
            color: white;
            text-decoration: none;
            width: 100px;
            transition: background-color 0.3s;
        }

        /* تغيير لون الخلفية عند التمرير */
        .action-button:hover {
            background-color: #2980b9;
        }

        /* تنسيق الرمز التعبيري */
        .icon {
            font-size: 40px;
            margin-bottom: 5px;
        }

        /* تنسيق رسالة التفاعل */
        .message {
            margin-top: 20px;
            font-size: 18px;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="dashboard-container">
        <h1>مرحبًا، <span id="username">[اسم الموظف]</span></h1>
        <div class="button-container">
            <button class="action-button" onclick="recordAction('صلاة')">
                <span class="icon">🕌</span> صلاة
            </button>
            <button class="action-button" onclick="recordAction('اجتماع')">
                <span class="icon">🤝</span> اجتماع
            </button>
            <button class="action-button" onclick="recordAction('تدريب')">
                <span class="icon">📚</span> تدريب
            </button>
            <button class="action-button" onclick="recordAction('استراحة')">
                <span class="icon">☕</span> استراحة
            </button>
            <button class="action-button" onclick="logout()">
                <span class="icon">🚪</span> خروج
            </button>
        </div>
        <div class="message" id="actionMessage"></div>
    </div>

    <script src="script.js"></script>
    <script>
        function setUsername() {
            const username = sessionStorage.getItem("username") || "بكم";
            document.getElementById('username').innerText = username;
        }

        function recordAction(action) {
            document.getElementById('actionMessage').innerText = `الزر '${action}' فعال الآن.`;
        }

        function logout() {
            history.back(); // يرجع المستخدم إلى الصفحة السابقة
        }

        // استدعاء دالة تعيين اسم المستخدم عند تحميل الصفحة
        setUsername();
    </script>
</body>
</html>
