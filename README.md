# toxic5018.github.io

**Warning**: ⚠️ **WEBSITE IN DEVELOPMENT** ⚠️

**Follow Me On**:  
[YouTube](https://www.youtube.com/@toxic5018.3) | [TikTok](https://www.tiktok.com/@toxic5018yt) | **Settings**  
<div style="display: inline-block; margin-left: 10px;">
  <select id="settingsDropdown" onchange="settingsAction(event)">
    <option value="">Settings</option>
    <option value="darkmode">Dark Mode ON/OFF</option>
    <option value="aboutme">About Me</option>
  </select>
</div>

![Fruit Ninja](./fruit-ninja.png)

## Modded Fruit Ninja

- **Fruit Ninja CRAZY GHOSTBUSTERS**:  
  <img src="https://f4.bcbits.com/img/a0356558918_65" alt="FN Ghostbusters Icon" width="20" height="20"/>  
  *A modified version of Fruit Ninja featuring Ghostbusters-themed graphics and gameplay mechanics. Released in 2014 (Version 2.1.0).*  
  [Download Now (2.1.0 LATEST) (Year 2014)](https://www.mediafire.com/file/p281pfhcgdipw8n/Fruit_Ninja_Ghostbusters_Mod_By_Superstrongtaner_%2528Revised%2529.zip/file){:target="_blank"}

- **Fruit Ninja CHINESE**:  
  <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCZo4oOwnyhDDrrVgqF_HU1fKtr47mr-YSYQ&s" alt="FN Chinese Icon" width="20" height="20"/>  
  *The Chinese version of Fruit Ninja, with unique features and enhancements. Released in 2016 (Version 3.55.0).*  
  [Download Now (3.55.0 LATEST) (Year 2016)](https://www.mediafire.com/file/gqi330uzno5ka0d/Fruit_Ninja_Chinese_%2528Revised%2529.apk/file){:target="_blank"}

- **+ View More Mods**  
  <div id="moreMods" style="display:none;">
    <p>Details about additional mods or versions can go here...</p>
  </div>

### Preview Images
<div style="display: flex; overflow-x: scroll;">
  <img src="https://play-lh.googleusercontent.com/V9WnBLaWFXUSTVXvAYsXTsZWTEFPgiGE82dpuFKXpXePXxddHo2NHNlaeL4DN0Jdyq8=w526-h296-rw" alt="Preview 1" width="400" height="225" style="margin-right: 10px;"/>
  <img src="https://play-lh.googleusercontent.com/s_tPMlpmk_9vzX3523Lk4ttR_IeQGqxOrkKVqLJtexX6EKTlWt1YLW8i18DHormKmg=w526-h296-rw" alt="Preview 2" width="400" height="225" style="margin-right: 10px;"/>
  <img src="https://play-lh.googleusercontent.com/dc31RwBORfwWBbMTgQinBROdMcsGUGPqRxlJI1RF1irAjR2x45TqQtJdqFqbDVX7rR8=w526-h296-rw" alt="Preview 3" width="400" height="225" style="margin-right: 10px;"/>
  <img src="https://play-lh.googleusercontent.com/R5kUH26mDQWD3Tj3UorhtibsDq7Qipa6LVqUsGb58pqCL_FnXxWF9yyfxFQ0fxpb5G9q=w526-h296-rw" alt="Preview 4" width="400" height="225" style="margin-right: 10px;"/>
</div>

## Q&A Session
If there’s anything that needs to be added, like modded content or other features, contact me through my business email with a valid link and the exact date when the original version was publicly released.  
**Note**: We do not own any assets and usually do **NOT** share APKs for copyright reasons, but you’re welcome to enjoy the available content here.  
I may one day delete the website!!!

## About Me
I'm a passionate game developer who loves experimenting with new ideas and creating engaging gameplay experiences. Check out my projects and feel free to contribute or leave feedback!

[Visit My GitHub](https://github.com/toxic5018)

## Contact
- Email: toxicbusinessstudios@gmail.com

---

**Version 1.0.0**

© [2024] Toxic Studios. **Do Not Distribute!!**

<script>
  function settingsAction(event) {
    const action = event.target.value;
    if (action === 'darkmode') {
      // Toggle Dark Mode (Implementation can be done here)
      document.body.classList.toggle("dark-mode");
      alert("Dark Mode toggled!");
    } else if (action === 'aboutme') {
      // Scroll to About Me section
      document.getElementById('aboutmeSection').scrollIntoView({ behavior: 'smooth' });
    }
  }

  // Toggle Mod visibility
  document.getElementById("moreMods").style.display = "none";
  function toggleMods() {
    var mods = document.getElementById("moreMods");
    if (mods.style.display === "none") {
      mods.style.display = "block";
      document.getElementById("toggleButton").innerText = "- View Less Mods";
    } else {
      mods.style.display = "none";
      document.getElementById("toggleButton").innerText = "+ View More Mods";
    }
  }
</script>
