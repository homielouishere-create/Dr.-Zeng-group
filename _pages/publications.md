---
title: "Publications"
layout: gridlay
sitemap: false
permalink: /publications/
---

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

  const items = pubList.querySelectorAll('li, p, .citation, .citation-entry');
  items.forEach(item => {
    let html = item.innerHTML;

    // 1. 加粗年份：(2026) -> <b>(2026)</b>
    html = html.replace(/\((\d{4})\)/g, '<b>($1)</b>');

    // 2. 加粗第一作者（匹配开头的第一个作者名，支持带有序号的情况）
    html = html.replace(/^(\s*\d+\.\s*)?([A-Za-z\s\-]+,\s*[A-Za-z]\.?(?:\s*[A-Za-z]\.?)?)/, '$1<b>$2</b>');

    item.innerHTML = html;

    // 3. 精确控制斜体：只加粗第 1 个斜体（期刊名），第 2 个斜体（卷号数字）保持正常字重
    const italics = item.querySelectorAll('i, em');
    italics.forEach((el, index) => {
      if (index === 0) {
        el.style.fontWeight = 'bold';   // 期刊名：斜体 + 加粗
      } else {
        el.style.fontWeight = 'normal'; // 卷号数字：斜体 + 不加粗
      }
    });
  });
});
</script>