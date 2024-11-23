# toxic5018.github.io

**Warning**: ⚠️ **WEBSITE IN DEVELOPMENT** ⚠️

## Main Content
<div style="display: flex; justify-content: space-between;">

  <!-- Left Side: What's New? -->
  <div style="width: 70%;">
    <button onclick="document.getElementById('whatsNewModal').style.display='block'" style="font-family: Arial, sans-serif; padding: 10px; background-color: lightblue; border: none; cursor: pointer;">What's New?</button>
    <button onclick="document.getElementById('loginModal').style.display='block'" style="font-family: Arial, sans-serif; padding: 10px; background-color: lightgreen; border: none; cursor: pointer;">Login</button>
    <button onclick="document.getElementById('registerModal').style.display='block'" style="font-family: Arial, sans-serif; padding: 10px; background-color: lightcoral; border: none; cursor: pointer;">Register</button>
  </div>

</div>

<!-- Social Media Links Below -->
[YouTube](https://www.youtube.com/playlist?list=PLd5gJYrm0hoCmzNHopuUjmZktYtvLd4qy) | [TikTok](https://www.tiktok.com/@toxic5018yt) | [Discord](https://discord.gg/5PQ68Sgqav) | [Twitch](https://www.twitch.tv/toxic5018) | [Scratch](https://scratch.mit.edu/users/JavaStudiosGaming/) | [PenguinMod](https://penguinmod.com/profile?user=toxic5018)

**[ToxicARC (Games) (Beta)](https://fusion-studios.itch.io/)**

---

## Recent YouTube Video
<div style="text-align: center;">
  <h3>Check Out My Recent Video</h3>
  <iframe width="560" height="315" src="https://www.youtube.com/embed?listType=playlist&list=PLd5gJYrm0hoCmzNHopuUjmZktYtvLd4qy&autoplay=1" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Modded Fruit Ninja
- **Genre**: Arcade, Action  
- **Description**: Fruit Ninja modded versions with new gameplay mechanics, skins, and themes.

### Preview Images
<div style="display: flex; overflow-x: scroll;">
  <img src="https://play-lh.googleusercontent.com/V9WnBLaWFXUSTVXvAYsXTsZWTEFPgiGE82dpuFKXpXePXxddHo2NHNlaeL4DN0Jdyq8=w526-h296-rw" alt="Preview 1" width="400" height="225" style="margin-right: 10px;"/>
  <img src="https://play-lh.googleusercontent.com/s_tPMlpmk_9vzX3523Lk4ttR_IeQGqxOrkKVqLJtexX6EKTlWt1YLW8i18DHormKmg=w526-h296-rw" alt="Preview 2" width="400" height="225" style="margin-right: 10px;"/>
  <img src="https://play-lh.googleusercontent.com/dc31RwBORfwWBbMTgQinBROdMcsGUGPqRxlJI1RF1irAjR2x45TqQtJdqFqbDVX7rR8=w526-h296-rw" alt="Preview 3" width="400" height="225" style="margin-right: 10px;"/>
  <img src="https://play-lh.googleusercontent.com/R5kUH26mDQWD3Tj3UorhtibsDq7Qipa6LVqUsGb58pqCL_FnXxWF9yyfxFQ0fxpb5G9q=w526-h296-rw" alt="Preview 4" width="400" height="225" style="margin-right: 10px;"/>
</div>

### Fruit Ninja CRAZY GHOSTBUSTERS:
- *A modified version of Fruit Ninja featuring Ghostbusters-themed graphics and gameplay mechanics. Released in 2014 (Version 2.1.0).*  
- **APK | ZIP + OBB Download Now (2.1.0 LATEST) (Year 2014)**  
  <a href="https://www.mediafire.com/file/p281pfhcgdipw8n/Fruit_Ninja_Ghostbusters_Mod_By_Superstrongtaner_%2528Revised%2529.zip/file" target="_blank" style="font-family: Arial, sans-serif; font-weight: bold; color: lightgreen;">Download Now</a>

### Fruit Ninja CHINESE:
- *The Chinese version of Fruit Ninja, with unique features and enhancements. Released in 2016 (Version 3.55.0).*  
- **APK | Download Now (3.55.0 LATEST) (Year 2016)**  
  <a href="https://www.mediafire.com/file/gqi330uzno5ka0d/Fruit_Ninja_Chinese_%2528Revised%2529.apk/file" target="_blank" style="font-family: Arial, sans-serif; font-weight: bold; color: lightgreen;">Download Now</a>

## Q&A Session
If there’s anything that needs to be added, like modded content or other features, contact me through my business email with a valid link and the exact date when the original version was publicly released.  
**Note**: We do not own any assets and usually do **NOT** share APKs for copyright reasons, but you’re welcome to enjoy the available content here.  
I may one day delete the website!!!

## About Me
I'm a passionate game developer who loves experimenting with new ideas and creating engaging gameplay experiences. Check out my projects and feel free to contribute or leave feedback!

[Visit My GitHub](https://github.com/toxic5018)

## Contact
- Email: [toxicbusinessstudios@gmail.com](mailto:toxicbusinessstudios@gmail.com)

---

**Version 1.100**  
**:features-added:**
- Added "Login" and "Register" buttons next to the "What's New?" button.
- Renamed "Click to view What's New" to "What's New?"
- Updated UI for Login and Register to match the What's New modal layout, with a light gray background and black Arial text.
- For Login UI, added fields for Email and Password, and a Login button.
- For Register UI, added message: "Registration Page Coming Soon!"
- Added a Toast notification for incorrect login attempts (Login and/or Password is incorrect).
- Added Redirect UI to confirm redirection to external links (e.g., downloads). Displays the link to be redirected to and asks the user if they are sure.
- Updated the layout for all modals to ensure consistency and functionality.

---

## Complete Code
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Toxic5018 - Website</title>

  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/11.0.2/firebase-app.js";
    import { getAnalytics } from "https://www.gstatic.com/firebasejs/11.0.2/firebase-analytics.js";

    const firebaseConfig = {
      apiKey: "AIzaSyAhg1frF8MCqWDUELGhogsSwIeQ0GB2gOw",
      authDomain: "toxicstudios-128d1.firebaseapp.com",
      projectId: "toxicstudios-128d1",
      storageBucket: "toxicstudios-128d1.firebasestorage.app",
      messagingSenderId: "253720176764",
      appId: "1:253720176764:web:aa5ca44a6aafcaa4f001f9",
      measurementId: "G-XQ24EWCB3V"
    };

    const app = initializeApp(firebaseConfig);
    const analytics = getAnalytics(app);
  </script>

  <style>
    body {
      font-family: 'Arial', sans-serif;
    }

    #whatsNewModal, #loginModal, #registerModal, #redirectModal {
      display: none;
      position: fixed;
      z-index: 1;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.4);
      padding-top: 60px;
    }

    .modal-content {
      margin: 5% auto;
      padding: 20px;
      border: 1px solid #888;
      width: 80%;
      max-width: 500px;
      background-color: lightgray;
      color: black;
    }

    .close {
      color: #aaa;
      float: right;
      font-size: 28px;
      font-weight: bold;
    }

    .close:hover,
    .close:focus {
      color: black;
      text-decoration: none;
      cursor: pointer;
    }

    .toast {
      position: fixed;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      background-color: #333;
      color: white;
      padding: 10px;
      border-radius: 5px;
      opacity: 0;
      transition: opacity 0.5s;
      font-family: Arial, sans-serif;
    }

    .toast.show {
      opacity: 1;
    }
  </style>
</head>
<body>

<!-- Main Content -->
<div style="text-align: center; padding: 50px;">
  <h1>Toxic5018 - Website</h1>
  <button onclick="document.getElementById('whatsNewModal').style.display='block'">What's New?</button>
  <button onclick="document.getElementById('loginModal').style.display='block'">Login</button>
  <button onclick="document.getElementById('registerModal').style.display='block'">Register</button>
</div>

<!-- What's New Modal -->
<div id="whatsNewModal" class="modal">
  <div class="modal-content">
    <span class="close" onclick="document.getElementById('whatsNewModal').style.display='none'">&times;</span>
    <h2>What's New?</h2>
    <p>We've added several exciting features to the website, including new modded games and content updates. Stay tuned for more!</p>
  </div>
</div>

<!-- Login Modal -->
<div id="loginModal" class="modal">
  <div class="modal-content">
    <span class="close" onclick="document.getElementById('loginModal').style.display='none'">&times;</span>
    <h2>Login</h2>
    <form onsubmit="login(event)">
      <input type="email" id="loginEmail" placeholder="Email" required><br>
      <input type="password" id="loginPassword" placeholder="Password" required><br>
      <button type="submit">Login</button>
    </form>
  </div>
</div>

<!-- Register Modal -->
<div id="registerModal" class="modal">
  <div class="modal-content">
    <span class="close" onclick="document.getElementById('registerModal').style.display='none'">&times;</span>
    <h2>Register</h2>
    <p>Registration Page Coming Soon!</p>
  </div>
</div>

<!-- Redirect Modal -->
<div id="redirectModal" class="modal">
  <div class="modal-content">
    <span class="close" onclick="document.getElementById('redirectModal').style.display='none'">&times;</span>
    <h2>Redirecting...</h2>
    <p id="redirectLink">You will be redirected shortly.</p>
    <button onclick="window.location.href = redirectLink">Proceed</button>
  </div>
</div>

<!-- Toast Notification -->
<div id="toast" class="toast">Incorrect Login or Password!</div>

<script>
  function login(event) {
    event.preventDefault();

    const email = document.getElementById('loginEmail').value;
    const password = document.getElementById('loginPassword').value;

    if (email === 'admin@toxic.com' && password === 'password123') {
      alert("Login Successful!");
    } else {
      document.getElementById('toast').classList.add('show');
      setTimeout(() => {
        document.getElementById('toast').classList.remove('show');
      }, 3000);
    }
  }

  function redirectToLink(link) {
    document.getElementById('redirectModal').style.display = 'block';
    document.getElementById('redirectLink').innerText = `You will be redirected to: ${link}`;
    setTimeout(() => {
      window.location.href = link;
    }, 3000);
  }
</script>

</body>
</html>
