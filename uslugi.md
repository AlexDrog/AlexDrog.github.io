---
layout: default
title: Услуги и цены
---

# 📋 Прайс-лист
<!-- ПОИСК ПО УСЛУГАМ -->
<div style="background: #f8f9fa; padding: 20px; border-radius: 8px; margin-bottom: 30px; border-left: 4px solid #e94560;">
  <label style="display: block; margin-bottom: 8px; font-weight: 600; color: #16213e;">
    🔍 Быстрый поиск услуги:
  </label>
  <input type="text" id="searchInput" placeholder="Например: замена экрана, Windows, FRP..." 
         style="width: 100%; padding: 12px 15px; border: 2px solid #ddd; border-radius: 4px; 
                font-size: 16px; box-sizing: border-box; transition: border-color 0.3s;">
  <div id="searchStats" style="margin-top: 10px; font-size: 0.9em; color: #666; display: none;">
    Найдено: <span id="foundCount" style="font-weight: bold; color: #e94560;">0</span> услуг
  </div>
  <div id="noResults" style="display: none; margin-top: 15px; padding: 15px; background: #fff3cd; 
                            border: 1px solid #ffeaa7; border-radius: 4px; color: #856404;">
    ❌ Ничего не найдено. Попробуйте другие слова: <b>ремонт</b>, <b>замена</b>, <b>установка</b>, <b>снятие</b>
  </div>
</div>

<script>
document.getElementById('searchInput').addEventListener('input', function(e) {
  const searchTerm = e.target.value.toLowerCase().trim();
  const tables = document.querySelectorAll('.price-table');
  let totalFound = 0;
  let hasVisibleTables = false;
  
  tables.forEach(table => {
    const rows = table.querySelectorAll('tr');
    let tableHasVisibleRows = false;
    
    rows.forEach((row, index) => {
      // Пропускаем заголовок (первая строка с th)
      if (row.querySelector('th')) return;
      
      const text = row.innerText.toLowerCase();
      const isMatch = text.includes(searchTerm);
      
      row.style.display = isMatch ? '' : 'none';
      
      if (isMatch) {
        totalFound++;
        tableHasVisibleRows = true;
      }
    });
    
    // Скрываем/показываем заголовок секции (h2 перед таблицей)
    const sectionHeader = table.previousElementSibling;
    if (sectionHeader && sectionHeader.tagName === 'H2') {
      sectionHeader.style.display = tableHasVisibleRows ? '' : 'none';
    }
    
    if (tableHasVisibleRows) hasVisibleTables = true;
  });
  
  // Показываем статистику
  const statsDiv = document.getElementById('searchStats');
  const noResultsDiv = document.getElementById('noResults');
  const countSpan = document.getElementById('foundCount');
  
  if (searchTerm.length > 0) {
    statsDiv.style.display = 'block';
    countSpan.textContent = totalFound;
    noResultsDiv.style.display = hasVisibleTables ? 'none' : 'block';
  } else {
    statsDiv.style.display = 'none';
    noResultsDiv.style.display = 'none';
    // Показываем все строки при пустом поиске
    tables.forEach(table => {
      const rows = table.querySelectorAll('tr');
      rows.forEach(row => row.style.display = '');
      const sectionHeader = table.previousElementSibling;
      if (sectionHeader && sectionHeader.tagName === 'H2') {
        sectionHeader.style.display = '';
      }
    });
  }
});

// Подсветка активного поля
const searchInput = document.getElementById('searchInput');
searchInput.addEventListener('focus', function() {
  this.style.borderColor = '#e94560';
  this.style.outline = 'none';
  this.style.boxShadow = '0 0 0 3px rgba(233, 69, 96, 0.1)';
});
searchInput.addEventListener('blur', function() {
  this.style.borderColor = '#ddd';
  this.style.boxShadow = 'none';
});
</script>

**📍 г. Дрогичин, ул. Ленина, 141 а (2 этаж)** | **📞 [+375 (29) 725-69-82](tel:+375297256982)**

---

<h2>💿 Программное обеспечение</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.soft %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>🖥️ Компьютеры и ноутбуки</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.computers %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>📱 Смартфоны и планшеты</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.phones %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>🗺️ Навигаторы и автоэлектроника</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.navigators %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>🌐 Сети и интернет</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.network %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>🖨️ Принтеры и МФУ</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.printers %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>💾 Восстановление данных</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.recovery %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>🔧 Электроника и мелкая техника</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.electronics %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>💻 Удалённая помощь и консультации</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.remote %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

---

💡 **Бесплатная диагностика — платишь только за ремонт!**

**[← На главную](./)** | **[💬 Записаться в Telegram](https://t.me/alexdrog81)** | **[📞 Позвонить](tel:+375297256982)**
