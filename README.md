<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Zentrix - Social Media</title>
  <!-- Funnel Display font for special titles -->
  <link href="https://fonts.googleapis.com/css2?family=Funnel+Display&display=swap" rel="stylesheet" />
  <!-- Material Icons -->
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet" />
  <!-- Firebase Initialization (using module) -->
  <script type="module">
    // Import the functions you need from the SDKs you need
    import { initializeApp } from "https://www.gstatic.com/firebasejs/11.2.0/firebase-app.js";
    import { getAnalytics } from "https://www.gstatic.com/firebasejs/11.2.0/firebase-analytics.js";
    // Your web app's Firebase configuration
    const firebaseConfig = {
      apiKey: "AIzaSyDjI46S2PGPbUsdvQfWXA0EQ6Pd9lpBRCE",
      authDomain: "toxicstudios-6de44.firebaseapp.com",
      projectId: "toxicstudios-6de44",
      storageBucket: "toxicstudios-6de44.firebasestorage.app",
      messagingSenderId: "22447277764",
      appId: "1:22447277764:web:78aa5cba1ce2b106b6ab91",
      measurementId: "G-E5JJV7VD5P"
    };
    // Initialize Firebase
    const app = initializeApp(firebaseConfig);
    const analytics = getAnalytics(app);
  </script>
  <style>
    /* === GENERAL & LAYOUT STYLES === */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      user-select: none;
      transition: background-color 0.3s, color 0.3s;
      background-color: white;
      color: black;
    }
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 20px;
      background-color: #2c3e50;
      color: white;
      position: relative;
    }
    .taskbar {
      display: flex;
      align-items: center;
    }
    .taskbar h1 {
      margin: 0;
      font-family: 'Funnel Display', sans-serif;
      font-size: 32px;
    }
    .search-bar {
      margin-left: 20px;
      flex-grow: 1;
    }
    .search-bar input {
      width: 100%;
      padding: 8px;
      border-radius: 4px;
      border: 1px solid #ccc;
    }
    .icons {
      display: flex;
      align-items: center;
      gap: 15px;
      position: relative;
    }
    .icons i {
      cursor: pointer;
      font-size: 24px;
    }
    .sign-in {
      background-color: #27ae60;
      color: white;
      font-family: 'Funnel Display', sans-serif;
      font-size: 16px;
      padding: 10px 20px;
      border-radius: 5px;
      border: none;
      cursor: pointer;
      position: relative;
    }
    .container {
      display: flex;
      padding: 20px;
    }
    .left-panel {
      width: 70%;
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 15px;
      overflow-y: auto;
      height: 80vh;
      background-color: #ecf0f1;
    }
    .right-panel {
      width: 30%;
      background-color: #ecf0f1;
      padding: 15px;
      border-radius: 5px;
      margin-left: 20px;
      overflow-y: auto;
      height: 80vh;
    }
    /* === POST & VIEW POST BOX === */
    .post {
      background-color: #ecf0f1;
      padding: 10px;
      border-radius: 5px;
      text-align: center;
      cursor: pointer;
      transition: transform 0.3s, border 0.3s;
      display: flex;
      flex-direction: column;
      align-items: center;
      border: 2px solid transparent;
      font-family: 'Funnel Display', sans-serif;
    }
    .post:hover {
      transform: scale(1.05);
    }
    .post img {
      max-width: 80%;
      height: auto;
      object-fit: cover;
      border-radius: 5px;
      margin-bottom: 10px;
    }
    .post .title,
    .post .info {
      text-align: left;
      margin: 5px 0;
    }
    .post .title { font-weight: bold; }
    .post .info { font-size: 14px; color: #7f8c8d; }
    .view-post-box {
      background-color: white;
      padding: 15px;
      border-radius: 5px;
      border: 2px solid #bdc3c7;
      margin-top: 15px;
    }
    .view-post-box h3 {
      font-weight: bold;
      font-family: 'Funnel Display', sans-serif;
    }
    .view-post-box .description { font-size: 14px; }
    .view-post-box .info { color: #7f8c8d; font-size: 14px; }
    .view-post-box .release-date { font-size: 12px; color: #95a5a6; }
    /* === COMMENTS SECTION === */
    .comments-box {
      margin-top: 20px;
      display: none;
      background-color: #ecf0f1;
      padding: 15px;
      border-radius: 5px;
      border: 2px solid #bdc3c7;
      font-family: 'Funnel Display', sans-serif;
      max-height: 300px;
      overflow-y: auto;
    }
    .comments-box h3 { font-family: 'Funnel Display', sans-serif; }
    #comment-list { max-height: 200px; overflow-y: auto; }
    .comment-item {
      display: flex;
      align-items: center;
      padding: 10px;
      border-bottom: 1px solid #bdc3c7;
    }
    .comment-item .icon {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      margin-right: 10px;
      overflow: hidden;
    }
    .comment-item .icon img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .comment-item .comment-info { flex-grow: 1; }
    .comment-item .date { font-size: 12px; color: #95a5a6; }
    .comment-item .username,
    .comment-item .comment-name { font-weight: bold; }
    .comments-count {
      font-size: 16px;
      font-family: 'Funnel Display', sans-serif;
      font-weight: bold;
      margin-top: 10px;
    }
    /* === MORE SECTION BUTTONS === */
    .more-section {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-top: 20px;
    }
    .more-section button {
      padding: 10px;
      font-size: 16px;
      border: none;
      cursor: pointer;
      border-radius: 5px;
      font-family: 'Funnel Display', sans-serif;
    }
    .more-section .comment-btn { background-color: lightblue; }
    .more-section .share-btn { background-color: #27ae60; color: white; }
    .more-section .report-btn { background-color: lightcoral; }
    .more-section .mark-btn { background-color: lightcoral; }
    /* === NEW COMMENT FORM === */
    .new-comment-form {
      margin-top: 10px;
      padding: 10px;
      border: 1px solid #bdc3c7;
      border-radius: 5px;
      background-color: #f9f9f9;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .new-comment-form label { font-weight: bold; }
    .new-comment-form textarea {
      width: 100%;
      height: 60px;
      resize: none;
      padding: 5px;
      font-family: Arial, sans-serif;
      font-size: 14px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    .new-comment-form .char-count {
      font-size: 12px;
      color: #555;
      text-align: right;
    }
    .new-comment-form .buttons {
      display: flex;
      gap: 10px;
      justify-content: flex-end;
    }
    .new-comment-form button.create-btn {
      padding: 5px 10px;
      background-color: #27ae60;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    .new-comment-form button.discard-btn {
      padding: 5px 10px;
      background-color: #e57373;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    /* === SHARE PANEL === */
    .share-panel {
      margin-top: 10px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .share-panel button {
      padding: 8px;
      background-color: #a5d6a7;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 5px;
    }
    /* === "SHOW MORE" TOGGLE TEXT === */
    #show-more {
      color: blue;
      cursor: pointer;
      margin-top: 10px;
    }
    /* === DROPDOWNS (for settings, sign in, info) === */
    .dropdown {
      position: absolute;
      background-color: white;
      border: 1px solid #ccc;
      border-radius: 4px;
      padding: 10px;
      box-shadow: 0px 2px 8px rgba(0,0,0,0.15);
      z-index: 1000;
      display: none;
    }
    .dropdown button {
      width: 100%;
      background: none;
      border: none;
      padding: 5px;
      text-align: left;
      cursor: pointer;
    }
    /* === MODAL STYLES (for Changelog, Login, Register, Access Prompt) === */
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 2000;
      display: none;
      flex-direction: column;
      background-color: white; /* Explicit background */
      color: black;
    }
    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 20px;
      border-bottom: 1px solid #ccc;
    }
    .modal-header .title {
      font-size: 20px;
      font-weight: bold;
      font-family: 'Funnel Display', sans-serif;
    }
    .modal-header .close-btn {
      background-color: #e57373;
      border: none;
      color: white;
      padding: 5px 10px;
      border-radius: 4px;
      cursor: pointer;
    }
    .modal-content {
      flex: 1;
      overflow-y: auto;
      padding: 20px;
    }
    .changelog-item {
      margin-bottom: 15px;
      padding-bottom: 10px;
      border-bottom: 1px solid #ddd;
      font-family: monospace;
    }
    /* === LOGIN & REGISTER MODAL STYLES === */
    .auth-form {
      max-width: 400px;
      margin: 40px auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 4px;
      background-color: white;
      color: black;
    }
    .auth-form h2 {
      text-align: center;
      font-family: 'Funnel Display', sans-serif;
    }
    .auth-form label {
      display: block;
      margin-top: 10px;
      font-weight: bold;
    }
    .auth-form input {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 14px;
    }
    .auth-form button {
      width: 100%;
      padding: 10px;
      margin-top: 20px;
      background-color: #27ae60;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
    }
    .auth-form .toggle-link {
      text-align: center;
      margin-top: 15px;
      cursor: pointer;
      color: blue;
    }
    /* === ACCESS PROMPT MODAL (for guests) === */
    .access-modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 2100;
      display: none;
      flex-direction: column;
      background-color: white;
      color: black;
    }
    .access-modal .modal-header {
      background-color: #27ae60;
      color: white;
    }
    .access-modal .modal-header .title {
      font-size: 20px;
      font-weight: bold;
    }
    .access-modal .modal-content {
      flex: 1;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      padding: 20px;
      text-align: center;
    }
    /* === DARK MODE STYLES === */
    .dark-mode {
      background-color: #222 !important;
      color: white !important;
    }
    .dark-mode header { background-color: #111; }
    .dark-mode .left-panel,
    .dark-mode .right-panel,
    .dark-mode .comments-box {
      background-color: #333;
      color: white;
    }
    .dark-mode .post {
      background-color: #444;
      color: white;
    }
    .dark-mode .view-post-box {
      background-color: #444;
      color: white;
    }
    .dark-mode .dropdown {
      background-color: #333;
      color: white;
      border: 1px solid #555;
    }
    .dark-mode .modal { background-color: #222; color: white; }
    .dark-mode .auth-form { background-color: #333; color: white; border: 1px solid #555; }
    .dark-mode .access-modal { background-color: #222; color: white; }
  </style>
</head>
<body>
  <header>
    <div class="taskbar">
      <h1>Zentrix</h1>
      <div class="search-bar">
        <input type="text" placeholder="Search..." />
      </div>
    </div>
    <div class="icons">
      <!-- Sign In Button with dropdown -->
      <button class="sign-in" id="sign-in-btn">Sign In</button>
      <!-- Settings Icon -->
      <i class="material-icons" id="settings-icon" style="cursor:pointer;">settings</i>
      <!-- Info Icon -->
      <i class="material-icons" id="info-icon" style="cursor:pointer;">info</i>
      <!-- Dropdown containers -->
      <div class="dropdown" id="settings-dropdown" style="top:50px; right:100px;"></div>
      <div class="dropdown" id="signin-dropdown" style="top:50px; right:250px;"></div>
      <div class="dropdown" id="info-dropdown" style="top:50px; right:10px;"></div>
    </div>
  </header>

  <div class="container">
    <div class="left-panel" id="posts">
      <!-- Posts generated dynamically -->
    </div>
    <div class="right-panel" id="post-details">
      <h2>View Post</h2>
      <p>Select a media item to display detailed info here.</p>
      <div id="post-title"></div>
      <div id="post-thumbnail"></div>
      <div class="view-post-box" id="view-post-box">
        <h3 id="view-post-title"></h3>
        <div class="info" id="view-post-info"></div>
        <div class="description" id="view-post-description"></div>
        <div class="release-date" id="view-post-date"></div>
      </div>
      <!-- Comments Section -->
      <div class="comments-box" id="comments-box">
        <h3>Comments (<span id="comments-count">0</span>)</h3>
        <div id="comment-list"></div>
        <!-- More Section Buttons -->
        <div class="more-section">
          <button class="comment-btn" id="add-comment-btn">+ Comment</button>
          <!-- New Comment Form inserted dynamically -->
          <button class="share-btn" id="share-btn">Share</button>
          <!-- Share Panel inserted dynamically -->
          <button class="report-btn" id="report-btn">Report</button>
          <button class="mark-btn" id="mark-btn">Mark it (18+)</button>
        </div>
      </div>
    </div>
  </div>

  <!-- === CHANGELOG MODAL (Full Screen UI) === -->
  <div class="modal" id="changelog-modal">
    <div class="modal-header">
      <div class="title">Changelog</div>
      <button class="close-btn" id="close-changelog">X</button>
    </div>
    <div class="modal-content" id="changelog-content">
      <!-- Changelog items inserted dynamically -->
    </div>
  </div>

  <!-- === LOGIN MODAL === -->
  <div class="modal" id="login-modal">
    <div class="modal-header">
      <div class="title" style="font-family: 'Funnel Display', sans-serif;">Login to Zentrix</div>
      <button class="close-btn" id="close-login">X</button>
    </div>
    <div class="modal-content">
      <div class="auth-form" id="login-form">
        <h2 style="font-family: 'Funnel Display', sans-serif;">Login</h2>
        <label for="login-username">Email/Username</label>
        <input type="text" id="login-username" placeholder="Enter your email or username" />
        <label for="login-password">Password</label>
        <input type="password" id="login-password" placeholder="Enter your password" />
        <button id="login-btn-submit">Login</button>
        <div class="toggle-link" id="to-register">Register with Zentrix</div>
      </div>
    </div>
  </div>

  <!-- === REGISTER MODAL === -->
  <div class="modal" id="register-modal">
    <div class="modal-header">
      <div class="title" style="font-family: 'Funnel Display', sans-serif;">Register with Zentrix</div>
      <button class="close-btn" id="close-register">X</button>
    </div>
    <div class="modal-content">
      <div class="auth-form" id="register-form">
        <h2 style="font-family: 'Funnel Display', sans-serif;">Register</h2>
        <label for="register-username">Username (max 50 characters)</label>
        <input type="text" id="register-username" placeholder="Enter your username" maxlength="50" />
        <label for="register-email">Email</label>
        <input type="email" id="register-email" placeholder="Enter your email" />
        <label for="register-password">Password (max 50 characters)</label>
        <input type="password" id="register-password" placeholder="Enter your password" maxlength="50" />
        <button id="register-btn-submit">Register</button>
        <div class="toggle-link" id="to-login">Already with Zentrix? Login Here</div>
      </div>
    </div>
  </div>

  <!-- === ACCESS PROMPT MODAL (for guests) === -->
  <div class="modal access-modal" id="access-modal">
    <div class="modal-header">
      <div class="title">Do More With Zentrix!</div>
      <button class="close-btn" id="close-access">X</button>
    </div>
    <div class="modal-content">
      Login to Zentrix to gain more access to comment posts, manage your posts, and more!
    </div>
  </div>

  <script>
    /* ===== GLOBAL VARIABLES & DATA ===== */
    let currentPost = null;
    let darkModeOn = false; // dark mode flag
    let isLoggedIn = false; // not logged in (guest) by default

    // Posts data (each with its own id)
    const postsData = [
      {
        id: 1,
        Title: "Post 1",
        Info: "This is the info for Post 1",
        Description: "Description for Post 1 goes here.",
        ReleaseDate: "2025-01-01",
        Thumbnail: "https://t3.ftcdn.net/jpg/02/48/42/64/360_F_248426448_NVKLywWqArG2ADUxDq6QprtIzsF82dMF.jpg"
      },
      {
        id: 2,
        Title: "Post 2",
        Info: "This is the info for Post 2",
        Description: "Description for Post 2 goes here.",
        ReleaseDate: "2025-01-02",
        Thumbnail: "https://t3.ftcdn.net/jpg/02/48/42/64/360_F_248426448_NVKLywWqArG2ADUxDq6QprtIzsF82dMF.jpg"
      },
      {
        id: 3,
        Title: "Post 3",
        Info: "This is the info for Post 3",
        Description: "Description for Post 3 goes here.",
        ReleaseDate: "2025-01-03",
        Thumbnail: "https://t3.ftcdn.net/jpg/02/48/42/64/360_F_248426448_NVKLywWqArG2ADUxDq6QprtIzsF82dMF.jpg"
      },
      {
        id: 4,
        Title: "Post 4",
        Info: "This is the info for Post 4",
        Description: "Description for Post 4 goes here.",
        ReleaseDate: "2025-01-04",
        Thumbnail: "https://t3.ftcdn.net/jpg/02/48/42/64/360_F_248426448_NVKLywWqArG2ADUxDq6QprtIzsF82dMF.jpg"
      },
      {
        id: 5,
        Title: "Post 5",
        Info: "This is the info for Post 5",
        Description: "Description for Post 5 goes here.",
        ReleaseDate: "2025-01-05",
        Thumbnail: "https://t3.ftcdn.net/jpg/02/48/42/64/360_F_248426448_NVKLywWqArG2ADUxDq6QprtIzsF82dMF.jpg"
      }
    ];

    // Comments data keyed by "Post <post.id>"
    const commentsData = {
      "Post 1": [
        { id: 1, username: "User1", comment: "Great post!", date: "2025-01-01" },
        { id: 2, username: "User2", comment: "Nice insights.", date: "2025-01-02" },
        { id: 3, username: "User3", comment: "Really informative.", date: "2025-01-03" },
        { id: 4, username: "User4", comment: "I learned a lot!", date: "2025-01-04" }
      ],
      "Post 2": [
        { id: 1, username: "User5", comment: "Interesting content.", date: "2025-01-02" }
      ],
      "Post 3": [
        { id: 1, username: "User6", comment: "Really liked it!", date: "2025-01-03" }
      ],
      "Post 4": [
        { id: 1, username: "User7", comment: "Amazing!", date: "2025-01-04" }
      ],
      "Post 5": [
        { id: 1, username: "User8", comment: "Awesome post.", date: "2025-01-05" }
      ]
    };

    // Changelog data (newer versions appear at the top)
    const changelogData = [
      {
        Version: "2025.001.14.0",
        Date: "2025/06/01",
        Description: "Added comment toggle, share panel, and dropdown menus."
      },
      {
        Version: "2025.001.13.0",
        Date: "2025/05/15",
        Description: "Improved post layout and updated icons."
      }
    ];

    /* ===== GENERATE POSTS ===== */
    postsData.forEach(post => {
      const postElement = document.createElement('div');
      postElement.classList.add('post');
      postElement.innerHTML = `
        <img src="${post.Thumbnail}" alt="Post Thumbnail">
        <div class="title">${post.Title}</div>
        <div class="info">${post.Info}</div>
      `;
      postElement.onclick = () => { showPostDetails(post); };
      document.getElementById('posts').appendChild(postElement);
    });

    /* ===== SHOW POST DETAILS & COMMENTS ===== */
    function showPostDetails(post) {
      currentPost = post;
      document.getElementById('view-post-title').textContent = post.Title;
      document.getElementById('view-post-info').textContent = post.Info;
      document.getElementById('view-post-description').textContent = post.Description;
      document.getElementById('view-post-date').textContent = `Release Date: ${post.ReleaseDate}`;
      document.getElementById('post-thumbnail').innerHTML = `<img src="${post.Thumbnail}" alt="Post Thumbnail">`;
      document.getElementById('comments-box').style.display = 'block';
      // Remove any existing new comment form or share panel if present
      const existingForm = document.getElementById('new-comment-form');
      if (existingForm) { existingForm.remove(); }
      const existingSharePanel = document.getElementById('share-panel');
      if (existingSharePanel) { existingSharePanel.remove(); }
      document.getElementById('add-comment-btn').textContent = "+ Comment";
      loadComments(post);
    }

    function loadComments(post) {
      const postKey = `Post ${post.id}`;
      const comments = commentsData[postKey] || [];
      let commentListHtml = "";
      
      if (comments.length <= 3) {
        comments.forEach(comment => {
          commentListHtml += `
            <div class="comment-item">
              <div class="icon">
                <img src="https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_1280.png" alt="Profile Picture">
              </div>
              <div class="comment-info">
                <div class="username">${comment.username}</div>
                <div class="comment-name">${comment.comment}</div>
                <div class="date">${comment.date}</div>
              </div>
            </div>
          `;
        });
      } else {
        comments.slice(0, 3).forEach(comment => {
          commentListHtml += `
            <div class="comment-item">
              <div class="icon">
                <img src="https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_1280.png" alt="Profile Picture">
              </div>
              <div class="comment-info">
                <div class="username">${comment.username}</div>
                <div class="comment-name">${comment.comment}</div>
                <div class="date">${comment.date}</div>
              </div>
            </div>
          `;
        });
        commentListHtml += `<div id="extra-comments" style="display:none;">`;
        comments.slice(3).forEach(comment => {
          commentListHtml += `
            <div class="comment-item">
              <div class="icon">
                <img src="https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_1280.png" alt="Profile Picture">
              </div>
              <div class="comment-info">
                <div class="username">${comment.username}</div>
                <div class="comment-name">${comment.comment}</div>
                <div class="date">${comment.date}</div>
              </div>
            </div>
          `;
        });
        commentListHtml += `</div>`;
        commentListHtml += `<div id="show-more">Show ${comments.length - 3} More</div>`;
      }
      
      document.getElementById('comment-list').innerHTML = commentListHtml;
      document.getElementById('comments-count').textContent = comments.length;
      
      const showMore = document.getElementById('show-more');
      if (showMore) {
        showMore.addEventListener('click', function() {
          const extra = document.getElementById('extra-comments');
          if (extra.style.display === "none") {
            extra.style.display = "block";
            showMore.textContent = "Show Less";
          } else {
            extra.style.display = "none";
            showMore.textContent = `Show ${comments.length - 3} More`;
          }
        });
      }
    }

    /* ===== ACCESS MODAL (for guests trying restricted actions) ===== */
    function showAccessModal() {
      const modal = document.getElementById('access-modal');
      modal.style.display = "flex";
    }
    document.getElementById('close-access').addEventListener('click', () => {
      document.getElementById('access-modal').style.display = "none";
    });

    /* ===== TOGGLE NEW COMMENT FORM ===== */
    function toggleCommentForm() {
      if (!isLoggedIn) {
        showAccessModal();
        return;
      }
      const form = document.getElementById('new-comment-form');
      const addCommentBtn = document.getElementById('add-comment-btn');
      if (form) {
        form.remove();
        addCommentBtn.textContent = "+ Comment";
      } else {
        const commentsBox = document.getElementById('comments-box');
        if (commentsBox.style.display === "none") {
          commentsBox.style.display = "block";
        }
        const formDiv = document.createElement('div');
        formDiv.id = 'new-comment-form';
        formDiv.classList.add('new-comment-form');
        formDiv.innerHTML = `
          <label for="new-comment-text">Comment</label>
          <textarea id="new-comment-text" maxlength="100" placeholder="Write your comment here..."></textarea>
          <div class="char-count" id="char-count">0 / 100</div>
          <div class="buttons">
            <button class="create-btn" id="create-comment-btn">Create</button>
            <button class="discard-btn" id="discard-comment-btn">Discard</button>
          </div>
        `;
        addCommentBtn.insertAdjacentElement('afterend', formDiv);
        addCommentBtn.textContent = "- Comment";
        const textarea = document.getElementById('new-comment-text');
        const charCount = document.getElementById('char-count');
        textarea.addEventListener('input', () => {
          charCount.textContent = `${textarea.value.length} / 100`;
        });
        document.getElementById('create-comment-btn').addEventListener('click', () => {
          const commentText = textarea.value.trim();
          if (commentText === "") {
            alert("Please enter a comment before creating.");
            return;
          }
          const postKey = `Post ${currentPost.id}`;
          if (!commentsData[postKey]) {
            commentsData[postKey] = [];
          }
          const newId = commentsData[postKey].length + 1;
          const newComment = {
            id: newId,
            username: 'User' + (Math.floor(Math.random() * 100) + 1),
            comment: commentText,
            date: new Date().toLocaleDateString()
          };
          commentsData[postKey].push(newComment);
          loadComments(currentPost);
          formDiv.remove();
          addCommentBtn.textContent = "+ Comment";
        });
        document.getElementById('discard-comment-btn').addEventListener('click', () => {
          formDiv.remove();
          addCommentBtn.textContent = "+ Comment";
        });
      }
    }

    /* ===== TOGGLE SHARE PANEL ===== */
    function toggleSharePanel() {
      if (!isLoggedIn) {
        showAccessModal();
        return;
      }
      const existingPanel = document.getElementById('share-panel');
      if (existingPanel) {
        existingPanel.remove();
        return;
      }
      const sharePanel = document.createElement('div');
      sharePanel.id = 'share-panel';
      sharePanel.classList.add('share-panel');
      sharePanel.innerHTML = `
        <button id="copy-link-btn"><i class="material-icons">content_copy</i> Copy Link</button>
        <button id="my-device-btn"><i class="material-icons">phone_android</i> My Device</button>
      `;
      const shareBtn = document.getElementById('share-btn');
      shareBtn.insertAdjacentElement('afterend', sharePanel);
      document.getElementById('copy-link-btn').addEventListener('click', () => {
        alert("Link copied to clipboard!");
      });
      document.getElementById('my-device-btn').addEventListener('click', () => {
        alert("Sharing to your device!");
      });
    }

    /* ===== RESTRICTED ACTIONS (Report, Mark) ===== */
    document.getElementById('report-btn').addEventListener('click', () => {
      if (!isLoggedIn) {
        showAccessModal();
        return;
      }
      alert("Reporting post...");
    });
    document.getElementById('mark-btn').addEventListener('click', () => {
      if (!isLoggedIn) {
        showAccessModal();
        return;
      }
      const markBtn = document.getElementById('mark-btn');
      if (markBtn.textContent === 'Mark it (18+)') {
        markBtn.textContent = 'Mark it Appropriate';
        markBtn.style.backgroundColor = '#27ae60';
      } else {
        markBtn.textContent = 'Mark it (18+)';
        markBtn.style.backgroundColor = 'lightcoral';
      }
    });

    /* ===== DROPDOWN TOGGLES ===== */
    // Settings dropdown (contains Dark Mode)
    document.getElementById('settings-icon').addEventListener('click', () => {
      const dropdown = document.getElementById('settings-dropdown');
      if (dropdown.style.display === "block") {
        dropdown.style.display = "none";
      } else {
        dropdown.innerHTML = `<button id="dark-mode-btn">Dark Mode</button>`;
        dropdown.style.display = "block";
        document.getElementById('dark-mode-btn').addEventListener('click', () => {
          if (darkModeOn) {
            document.body.classList.remove('dark-mode');
            darkModeOn = false;
          } else {
            document.body.classList.add('dark-mode');
            darkModeOn = true;
          }
          dropdown.style.display = "none";
        });
      }
    });
    // Sign In dropdown
    document.getElementById('sign-in-btn').addEventListener('click', () => {
      const dropdown = document.getElementById('signin-dropdown');
      if (dropdown.style.display === "block") {
        dropdown.style.display = "none";
      } else {
        dropdown.innerHTML = `
          <button id="guest-btn">Continue as Guest</button>
          <button id="login-btn">Login</button>
          <button id="register-btn">Register</button>
        `;
        dropdown.style.display = "block";
        document.getElementById('guest-btn').addEventListener('click', () => { 
          isLoggedIn = false; 
          alert("You are now continuing as a guest."); 
          dropdown.style.display = "none"; 
        });
        document.getElementById('login-btn').addEventListener('click', () => {
          dropdown.style.display = "none";
          openLoginModal();
        });
        document.getElementById('register-btn').addEventListener('click', () => {
          dropdown.style.display = "none";
          openRegisterModal();
        });
      }
    });
    // Info dropdown: shows a list with "Changelog"
    document.getElementById('info-icon').addEventListener('click', () => {
      const dropdown = document.getElementById('info-dropdown');
      if (dropdown.style.display === "block") {
        dropdown.style.display = "none";
      } else {
        dropdown.innerHTML = `<button id="changelog-btn">Changelog</button>`;
        dropdown.style.display = "block";
        document.getElementById('changelog-btn').addEventListener('click', () => {
          dropdown.style.display = "none";
          openChangelogModal();
        });
      }
    });

    /* ===== OPEN & CLOSE CHANGELOG MODAL ===== */
    function openChangelogModal() {
      const modal = document.getElementById('changelog-modal');
      const contentDiv = document.getElementById('changelog-content');
      contentDiv.innerHTML = "";
      const sortedLogs = changelogData.sort((a, b) => (a.Date < b.Date ? 1 : -1));
      sortedLogs.forEach(item => {
        const itemDiv = document.createElement('div');
        itemDiv.classList.add('changelog-item');
        itemDiv.innerHTML = `<pre>${JSON.stringify(item, null, 2)}</pre>`;
        contentDiv.appendChild(itemDiv);
      });
      if (darkModeOn) {
        modal.style.backgroundColor = "#222";
        modal.style.color = "white";
      } else {
        modal.style.backgroundColor = "white";
        modal.style.color = "black";
      }
      modal.style.display = "flex";
    }
    document.getElementById('close-changelog').addEventListener('click', () => {
      document.getElementById('changelog-modal').style.display = "none";
    });

    /* ===== LOGIN MODAL ===== */
    function openLoginModal() {
      const modal = document.getElementById('login-modal');
      document.getElementById('login-username').value = "";
      document.getElementById('login-password').value = "";
      if (darkModeOn) {
        modal.style.backgroundColor = "#222";
        modal.style.color = "white";
      } else {
        modal.style.backgroundColor = "white";
        modal.style.color = "black";
      }
      modal.style.display = "flex";
    }
    document.getElementById('close-login').addEventListener('click', () => {
      document.getElementById('login-modal').style.display = "none";
    });
    document.getElementById('login-btn-submit').addEventListener('click', () => {
      // Here you would implement Firebase login functionality.
      alert("Logging in...");
      isLoggedIn = true;
      document.getElementById('login-modal').style.display = "none";
    });
    document.getElementById('to-register').addEventListener('click', () => {
      document.getElementById('login-modal').style.display = "none";
      openRegisterModal();
    });

    /* ===== REGISTER MODAL ===== */
    function openRegisterModal() {
      const modal = document.getElementById('register-modal');
      document.getElementById('register-username').value = "";
      document.getElementById('register-email').value = "";
      document.getElementById('register-password').value = "";
      if (darkModeOn) {
        modal.style.backgroundColor = "#222";
        modal.style.color = "white";
      } else {
        modal.style.backgroundColor = "white";
        modal.style.color = "black";
      }
      modal.style.display = "flex";
    }
    document.getElementById('close-register').addEventListener('click', () => {
      document.getElementById('register-modal').style.display = "none";
    });
    document.getElementById('register-btn-submit').addEventListener('click', () => {
      // Here you would implement Firebase registration functionality.
      alert("Registering...");
      isLoggedIn = true;
      document.getElementById('register-modal').style.display = "none";
    });
    document.getElementById('to-login').addEventListener('click', () => {
      document.getElementById('register-modal').style.display = "none";
      openLoginModal();
    });

    /* ===== EVENT LISTENERS FOR OTHER BUTTONS ===== */
    document.getElementById('add-comment-btn').addEventListener('click', toggleCommentForm);
    document.getElementById('share-btn').addEventListener('click', toggleSharePanel);
  </script>
</body>
</html>
