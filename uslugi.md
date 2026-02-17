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
  <div style="position: relative;">
    <input type="text" id="searchInput" placeholder="Например: замена экрана, Windows, FRP..." 
           style="width: 100%; padding: 12px 40px 12px 15px; border: 2px solid #ddd; border-radius: 4px; 
                  font-size: 16px; box-sizing: border-box; transition: all 0.3s;">
    <button id="clearBtn" onclick="document.getElementById('searchInput').value=''; document.getElementById('searchInput').dispatchEvent(new Event('input'));" 
            style="position: absolute; right: 8px; top: 50%; transform: translateY(-50%); 
                   background: #ccc; color: white; border: none; border-radius: 50%; 
                   width: 24px; height: 24px; cursor: pointer; font-size: 12px; display: none;">✕</button>
  </div>
  <div id="searchStats" style="margin-top: 10px; font-size: 0.9em; color: #666; display: none;">
    Найдено: <span id="foundCount" style="font-weight: bold; color: #e94560;">0</span> услуг
  </div>
  <div id="noResults" style="display: none; margin-top: 15px; padding: 15px; background: #fff3cd; 
                            border: 1px solid #ffeaa7; border-radius: 4px; color: #856404;">
    ❌ Ничего не найдено. Попробуйте: <b>ремонт</b>, <b>замена</b>, <b>Windows</b>, <b>разблокировка</b>
  </div>
</div>

<script>
(function() {
  const searchInput = document.getElementById('searchInput');
  const clearBtn = document.getElementById('clearBtn');
  const statsDiv = document.getElementById('searchStats');
  const noResultsDiv = document.getElementById('noResults');
  const countSpan = document.getElementById('foundCount');
  
  function findHeader(table) {
    let element = table.previousElementSibling;
    while (element && element.tagName !== 'H2') {
      element = element.previousElementSibling;
    }
    return element;
  }
  
  function filterTables() {
    const searchTerm = searchInput.value.toLowerCase().trim();
    const tables = document.querySelectorAll('.price-table');
    let totalFound = 0;
    let hasVisibleTables = false;
    
    clearBtn.style.display = searchTerm.length > 0 ? 'block' : 'none';
    
    tables.forEach(table => {
      const rows = table.querySelectorAll('tr');
      let tableHasVisibleRows = false;
      
      rows.forEach((row) => {
        if (row.querySelector('th')) return;
        
        const text = row.innerText.toLowerCase();
        const isMatch = text.includes(searchTerm);
        
        row.style.display = isMatch ? '' : 'none';
        
        if (isMatch) {
          totalFound++;
          tableHasVisibleRows = true;
        }
      });
      
      const sectionHeader = findHeader(table);
      
      if (tableHasVisibleRows) {
        hasVisibleTables = true;
        table.style.display = '';
        if (sectionHeader) sectionHeader.style.display = '';
      } else {
        table.style.display = 'none';
        if (sectionHeader) sectionHeader.style.display = 'none';
      }
    });
    
    if (searchTerm.length > 0) {
      statsDiv.style.display = 'block';
      countSpan.textContent = totalFound;
      noResultsDiv.style.display = hasVisibleTables ? 'none' : 'block';
    } else {
      statsDiv.style.display = 'none';
      noResultsDiv.style.display = 'none';
      tables.forEach(table => {
        table.style.display = '';
        const rows = table.querySelectorAll('tr');
        rows.forEach(row => row.style.display = '');
        const sectionHeader = findHeader(table);
        if (sectionHeader) sectionHeader.style.display = '';
      });
    }
  }
  
  searchInput.addEventListener('input', filterTables);
  
  searchInput.addEventListener('focus', function() {
    this.style.borderColor = '#e94560';
    this.style.boxShadow = '0 0 0 3px rgba(233, 69, 96, 0.1)';
  });
  
  searchInput.addEventListener('blur', function() {
    this.style.borderColor = '#ddd';
    this.style.boxShadow = 'none';
  });
})();
</script>

**📍 г. Дрогичин, ул. Ленина, 141 а (2 этаж)** | **📞 [+375 (29) 725-69-82](tel:+375297256982)**

---

<h2 id="soft">💿 Программное обеспечение</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.soft %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="computers">🖥️ Компьютеры и ноутбуки</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.computers %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="phones">📱 Смартфоны и планшеты</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.phones %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="auto">🗺️ Навигаторы и автоэлектроника</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.navigators %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="network">🌐 Сети и интернет</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.network %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="printers">🖨️ Принтеры и МФУ</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.printers %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="recovery">💾 Восстановление данных</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.recovery %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="electronics">🔧 Электроника и мелкая техника</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.electronics %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="remote">💻 Удалённая помощь и консультации</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.remote %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

---

💡 **Бесплатная диагностика — платишь только за ремонт!**

**[← На главную](./)** | **[💬 Telegram](https://t.me/alexdrog81)** | **[📞 Позвонить](tel:+375297256982)**

<script>
(function() {
  if (window.innerWidth <= 768) {
    var btn = document.createElement('a');
    btn.href = 'tel:+375297256982';
    btn.innerHTML = '<span style="font-size:22px;">📞</span> <span style="font-weight:600;">Позвонить</span>';
    btn.style.cssText = 'position:fixed;bottom:20px;right:20px;background:linear-gradient(135deg,#e94560 0%,#c9183a 100%);color:white;padding:14px 24px;border-radius:50px;text-decoration:none;z-index:9999;box-shadow:0 6px 20px rgba(233,69,96,0.4);display:flex;align-items:center;gap:10px;font-size:16px;border:2px solid rgba(255,255,255,0.2);';
    document.body.appendChild(btn);
  }
})();
</script>
