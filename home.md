---
layout: default
title: 私人信件
---

<script>
function checkPassword() {
    var password = prompt("請輸入密碼：");
    var encoded = btoa(password); // 轉換成 Base64
    if (encoded !== "bXlzZWNyZXQxMjM=") {  // 這裡替換成你的密碼的 Base64
        alert("密碼錯誤");
        window.location.href = "https://google.com"; // 錯誤時跳轉
    }
}
checkPassword();
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
