<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>לוח מודעות מעוצב</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            direction: rtl;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 30px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.37);
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .ticker-container {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            overflow: hidden;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .ticker-header {
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 15px;
            font-weight: bold;
            font-size: 1.2rem;
        }

        .ticker {
            height: 60px;
            overflow: hidden;
            position: relative;
            background: #fff;
        }

        .ticker-content {
            position: absolute;
            white-space: nowrap;
            animation: scroll 30s linear infinite;
            line-height: 60px;
            font-size: 1.1rem;
            color: #333;
            padding: 0 20px;
        }

        @keyframes scroll {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }

        .main-content {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        .bulletin-board {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
        }

        .board-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            border-bottom: 3px solid #667eea;
            padding-bottom: 15px;
        }

        .board-title {
            font-size: 1.8rem;
            color: #333;
            font-weight: bold;
        }

        .add-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .add-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
        }

        .posts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .post {
            background: white;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            border-left: 5px solid #667eea;
        }

        .post:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .post-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .post-title {
            font-size: 1.3rem;
            font-weight: bold;
            color: #333;
        }

        .post-date {
            font-size: 0.9rem;
            color: #666;
        }

        .post-content {
            color: #555;
            line-height: 1.6;
            margin-bottom: 15px;
        }

        .post-actions {
            display: flex;
            gap: 10px;
        }

        .action-btn {
            padding: 6px 12px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }

        .edit-btn {
            background: #54a0ff;
            color: white;
        }

        .delete-btn {
            background: #ff6b6b;
            color: white;
        }

        .action-btn:hover {
            transform: scale(1.05);
        }

        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .video-section {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
        }

        .section-title {
            font-size: 1.5rem;
            color: #333;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
        }

        .video-container {
            position: relative;
            width: 100%;
            height: 200px;
            background: #000;
            border-radius: 15px;
            overflow: hidden;
            margin-bottom: 15px;
        }

        .video-placeholder {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.1rem;
            background: linear-gradient(45deg, #667eea, #764ba2);
        }

        .video-controls {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 10px;
        }

        .control-btn {
            background: #333;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .control-btn:hover {
            background: #555;
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            backdrop-filter: blur(5px);
        }

        .modal-content {
            background: white;
            margin: 5% auto;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.3);
        }

        .close {
            color: #aaa;
            float: left;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }

        .close:hover {
            color: #333;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #333;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #667eea;
        }

        .form-group textarea {
            height: 100px;
            resize: vertical;
        }

        .submit-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            width: 100%;
            transition: all 0.3s ease;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .posts-grid {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🏆 לוח מודעות מעוצב</h1>
            <p>מקום לשיתוף מידע, הודעות ועדכונים חשובים</p>
        </div>

        <div class="ticker-container">
            <div class="ticker-header">
                📢 מודעות רצות
            </div>
            <div class="ticker">
                <div class="ticker-content" id="tickerContent">
                    🔥 ברוכים הבאים ללוח המודעות החדש! • 📅 אירוע מיוחד השבוע • 💡 הזדמנויות עבודה חדשות • 🎉 חדשות מרגשות בדרך
                </div>
            </div>
        </div>

        <div class="main-content">
            <div class="bulletin-board">
                <div class="board-header">
                    <h2 class="board-title">📋 לוח מודעות</h2>
                    <button class="add-btn" onclick="openModal()">+ הוסף מודעה</button>
                </div>
                <div class="posts-grid" id="postsGrid">
                    <!-- Posts will be added here dynamically -->
                </div>
            </div>

            <div class="sidebar">
                <div class="video-section">
                    <h3 class="section-title">📹 שודר עכשיו</h3>
                    <div class="video-container">
                        <div class="video-placeholder" id="videoPlaceholder">
                            🎥 וידאו חי - לחץ על הפעל כדי להתחיל
                        </div>
                    </div>
                    <div class="video-controls">
                        <button class="control-btn" onclick="playVideo()">▶️ הפעל</button>
                        <button class="control-btn" onclick="pauseVideo()">⏸️ השהה</button>
                        <button class="control-btn" onclick="stopVideo()">⏹️ עצור</button>
                    </div>
                </div>

                <div class="video-section">
                    <h3 class="section-title">📊 סטטיסטיקות</h3>
                    <div style="text-align: center; color: #333;">
                        <p style="margin: 10px 0;"><strong>מודעות פעילות:</strong> <span id="activeCount">0</span></p>
                        <p style="margin: 10px 0;"><strong>צפיות היום:</strong> <span id="viewsCount">247</span></p>
                        <p style="margin: 10px 0;"><strong>משתמשים מחוברים:</strong> <span id="usersCount">12</span></p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal for adding new posts -->
    <div id="postModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal()">&times;</span>
            <h2 style="margin-bottom: 20px; color: #333;">➕ הוסף מודעה חדשה</h2>
            <form id="postForm">
                <div class="form-group">
                    <label for="postTitle">כותרת המודעה:</label>
                    <input type="text" id="postTitle" required>
                </div>
                <div class="form-group">
                    <label for="postContent">תוכן המודעה:</label>
                    <textarea id="postContent" required></textarea>
                </div>
                <button type="submit" class="submit-btn">פרסם מודעה</button>
            </form>
        </div>
    </div>

    <script>
        let posts = [];
        let postCounter = 0;
        let videoPlaying = false;

        // Initialize with sample posts
        function initializePosts() {
            const samplePosts = [
                {
                    title: "ברוכים הבאים ללוח המודעות!",
                    content: "זהו לוח מודעות מעוצב ומתקדם עם אפשרויות רבות לניהול תוכן ושיתוף מידע.",
                    date: new Date().toLocaleDateString('he-IL')
                },
                {
                    title: "אירוע מיוחד השבוע",
                    content: "הזמנה לכל הקהילה להשתתף באירוע המיוחד שלנו ביום רביעי הקרוב.",
                    date: new Date().toLocaleDateString('he-IL')
                },
                {
                    title: "עדכון חשוב",
                    content: "שימו לב לשינויים החדשים בתקנון ובהנחיות הקהילה.",
                    date: new Date().toLocaleDateString('he-IL')
                }
            ];

            samplePosts.forEach(post => {
                addPost(post.title, post.content, post.date);
            });
        }

        function openModal() {
            document.getElementById('postModal').style.display = 'block';
        }

        function closeModal() {
            document.getElementById('postModal').style.display = 'none';
            document.getElementById('postForm').reset();
        }

        function addPost(title, content, date = null) {
            const post = {
                id: ++postCounter,
                title: title,
                content: content,
                date: date || new Date().toLocaleDateString('he-IL')
            };
            
            posts.unshift(post);
            renderPosts();
            updateActiveCount();
        }

        function deletePost(id) {
            posts = posts.filter(post => post.id !== id);
            renderPosts();
            updateActiveCount();
        }

        function editPost(id) {
            const post = posts.find(p => p.id === id);
            if (post) {
                const newTitle = prompt('כותרת חדשה:', post.title);
                const newContent = prompt('תוכן חדש:', post.content);
                
                if (newTitle && newContent) {
                    post.title = newTitle;
                    post.content = newContent;
                    renderPosts();
                }
            }
        }

        function renderPosts() {
            const grid = document.getElementById('postsGrid');
            grid.innerHTML = '';

            posts.forEach(post => {
                const postElement = document.createElement('div');
                postElement.className = 'post';
                postElement.innerHTML = `
                    <div class="post-header">
                        <h3 class="post-title">${post.title}</h3>
                        <span class="post-date">${post.date}</span>
                    </div>
                    <p class="post-content">${post.content}</p>
                    <div class="post-actions">
                        <button class="action-btn edit-btn" onclick="editPost(${post.id})">✏️ ערוך</button>
                        <button class="action-btn delete-btn" onclick="deletePost(${post.id})">🗑️ מחק</button>
                    </div>
                `;
                grid.appendChild(postElement);
            });
        }

        function updateActiveCount() {
            document.getElementById('activeCount').textContent = posts.length;
        }

        // Video controls
        function playVideo() {
            const placeholder = document.getElementById('videoPlaceholder');
            if (!videoPlaying) {
                placeholder.innerHTML = '🔴 שידור חי פעיל - מתחבר לסטרים...';
                placeholder.style.background = 'linear-gradient(45deg, #ff6b6b, #ee5a24)';
                videoPlaying = true;
                
                // Simulate video loading
                setTimeout(() => {
                    placeholder.innerHTML = '📹 שידור חי - מוצג כעת';
                }, 2000);
            }
        }

        function pauseVideo() {
            const placeholder = document.getElementById('videoPlaceholder');
            if (videoPlaying) {
                placeholder.innerHTML = '⏸️ שידור מושהה - לחץ הפעל להמשך';
                placeholder.style.background = 'linear-gradient(45deg, #ffa500, #ff8c00)';
            }
        }

        function stopVideo() {
            const placeholder = document.getElementById('videoPlaceholder');
            placeholder.innerHTML = '🎥 וידאו חי - לחץ על הפעל כדי להתחיל';
            placeholder.style.background = 'linear-gradient(45deg, #667eea, #764ba2)';
            videoPlaying = false;
        }

        // Form submission
        document.getElementById('postForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const title = document.getElementById('postTitle').value;
            const content = document.getElementById('postContent').value;
            
            if (title && content) {
                addPost(title, content);
                closeModal();
            }
        });

        // Close modal when clicking outside
        window.onclick = function(event) {
            const modal = document.getElementById('postModal');
            if (event.target === modal) {
                closeModal();
            }
        }

        // Update statistics periodically
        setInterval(() => {
            const views = document.getElementById('viewsCount');
            const users = document.getElementById('usersCount');
            
            views.textContent = parseInt(views.textContent) + Math.floor(Math.random() * 3);
            users.textContent = 10 + Math.floor(Math.random() * 15);
        }, 5000);

        // Initialize the app
        initializePosts();
    </script>
</body>
</html># modaoot
