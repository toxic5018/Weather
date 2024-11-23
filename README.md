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

**Version 1.0.26**

© [2024] Toxic Studios. **Do Not Distribute!!**

---

### Firebase Integration for Login and Registration

**Firebase Authentication** is now integrated into the website for managing user login and registration. Below are the changes added to the website:

```html
<!-- Add Firebase Initialization and Authentication Scripts -->
<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/11.0.2/firebase-app.js";
  import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut } from "https://www.gstatic.com/firebasejs/11.0.2/firebase-auth.js";
  
  // Firebase configuration object
  const firebaseConfig = {
    apiKey: "AIzaSyAhg1frF8MCqWDUELGhogsSwIeQ0GB2gOw",
    authDomain: "toxicstudios-128d1.firebaseapp.com",
    projectId: "toxicstudios-128d1",
    storageBucket: "toxicstudios-128d1.firebasestorage.app",
    messagingSenderId: "253720176764",
    appId: "1:253720176764:web:aa5ca44a6aafcaa4f001f9",
    measurementId: "G-XQ24EWCB3V"
  };

  // Initialize Firebase app and auth
  const app = initializeApp(firebaseConfig);
  const auth = getAuth(app);

  // Register user function
  function registerUser(email, password) {
    createUserWithEmailAndPassword(auth, email, password)
      .then((userCredential) => {
        console.log('User registered:', userCredential.user);
      })
      .catch((error) => {
        console.error('Error during registration:', error.message);
      });
  }

  // Login user function
  function loginUser(email, password) {
    signInWithEmailAndPassword(auth, email, password)
      .then((userCredential) => {
        console.log('User logged in:', userCredential.user);
      })
      .catch((error) => {
        console.error('Error during login:', error.message);
      });
  }

  // Logout user function
  function logoutUser() {
    signOut(auth)
      .then(() => {
        console.log('User logged out');
      })
      .catch((error) => {
        console.error('Error during logout:', error.message);
      });
  }
</script>
