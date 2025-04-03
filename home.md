---
layout: default
title: 私人信件
---

<audio id="bgm" loop>
  <source src="/assets/music/background.mp3" type="audio/mpeg">
</audio>

<script>
function checkPassword() {
    var password = prompt("請輸入密碼：");
    var encoded = btoa(password);
    if (encoded === "bXlzZWNyZXQxMjM=") {
        document.getElementById("startBtn").style.display = "block";
    } else {
        alert("密碼錯誤");
        window.location.href = "https://google.com";
    }
}

function startSite() {
    const bgm = document.getElementById("bgm");
    if (bgm) {
        bgm.play().catch(e => console.warn("音樂播放失敗", e));
    }
    document.getElementById("content").style.display = "block";
    document.getElementById("startBtn").style.display = "none";
}

document.addEventListener("DOMContentLoaded", checkPassword);

// 點信件時停止播放
document.addEventListener("DOMContentLoaded", () => {
    const audio = document.getElementById("bgm");
    document.querySelectorAll("a").forEach(link => {
        link.addEventListener("click", () => {
            if (audio) {
                audio.pause();
                audio.currentTime = 0;
            }
        });
    });
});
</script>

<button id="startBtn" onclick="startSite()" style="display:none; margin-top:20px; padding:8px 16px; font-size:16px;">
  進入信件
</button>

<div id="content" style="display:none;">

## 私人信件

這些年，從年輕到年老，寫給妳的，恰好見證了妳的美，也悄悄記錄了我的寂寞……

### 信件列表

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small>（{{ post.date | date: "%Y 年 %m 月 %d 日" }}）</small>
    </li>
  {% endfor %}
</ul>

<br>
<p>© 2025 JLCHENA Letters</p>
</div>