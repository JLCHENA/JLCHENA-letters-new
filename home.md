---
layout: default
title: 歡迎
---

<!-- 歡迎詞 -->
<h1 style="text-align:center;">歡迎來到我的信件集</h1>

<!-- 背景音樂播放 -->
<audio id="bgm" autoplay loop>
  <source src="music/background.mp3" type="audio/mpeg">
</audio>

<!-- 點擊信件連結時關閉音樂 -->
<script>
  document.addEventListener('DOMContentLoaded', function () {
    const audio = document.getElementById('bgm');
    const links = document.querySelectorAll('a[href*="/posts/"], a[href*="letters/"]');
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