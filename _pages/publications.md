---
title: "Publications"
layout: gridlay
sitemap: false
permalink: /publications/
---

<style>
  /* 让所有期刊名（原本是斜体 <i> 或 <em>）叠加加粗 */
  #pubList i, #pubList em {
    font-weight: bold;
    font-style: italic; /* 若想取消斜体只留加粗，改为 font-style: normal; */
  }
</style>

## Publications

<input type="text" class="pub-search" id="pubSearch" placeholder="Filter by title, author, or year...">

<div class="section-card" id="pubList">
<h3>Published Papers</h3>

{% bibliography %}
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
  const pubList = document.getElementById('pubList');
  if (!pubList) return;

  const items = pubList.querySelectorAll('li, p, .citation');
  items.forEach(item => {
    let html = item.innerHTML;

    // 1. 加粗年份：例如 (2026) -> <b>(2026)</b>
    html = html.replace(/\((\d{4})\)/g, '<b>($1)</b>');

    // 2. 加粗第一作者：匹配开头的作者姓名
    html = html.replace(/^(\s*\d+\.\s*)?([A-Za-z\s\-]+,\s*[A-Za-z]\.?(?:\s*[A-Za-z]\.?)?)/, '$1<b>$2</b>');

    item.innerHTML = html;
  });
});
</script>