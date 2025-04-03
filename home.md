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
    var encoded = btoa(password);
    if (encoded === "bXlzZWNyZXQxMjM=") {
        // 顯示內容並播放音樂
        document.getElementById("content").style.display = "block";
        const bgm = document.getElementById("bgm");
        bgm.play().catch(e => console.warn("音樂播放失敗", e));
    } else {
        alert("密碼錯誤");
        window.location.href = "https://google.com";
    }
}
checkPassword();

// 點信件連結後停止音樂
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