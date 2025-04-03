---
layout: default
title: 私人信件
---

<audio id="bgm" loop>
  <source src="/music/background.mp3" type="audio/mpeg">
</audio>

<script>
function checkPassword() {
    var password = prompt("請輸入密碼：");
    var encoded = btoa(password); // 轉換成 Base64
    if (encoded === "bXlzZWNyZXQxMjM=") {
        // 播放背景音樂
        const bgm = document.getElementById('bgm');
        bgm.play().catch(err => console.warn("音樂播放失敗：", err));
    } else {
        alert("密碼錯誤");
        window.location.href = "https://google.com"; // 錯誤時跳轉
    }
}
checkPassword();

// 點擊信件連結時關閉音樂
document.addEventListener('DOMContentLoaded', function () {
    const audio = document.getElementById('bgm');
    const links = document.querySelectorAll('a[href*="/posts/"], a[href*="letters/"], a[href$=".html"]');
    links.forEach(link => {
      link.addEventListener('click', function () {
        if (audio) {
          audio.pause();
          audio.currentTime = 0;
        }
      });
    });
});
</script>

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