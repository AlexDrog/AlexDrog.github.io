---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

# 📋 Прайс-лист

<!-- ПОИСК ПО УСЛУГАМ -->
<div class="search-container">
  <label>🔍 Быстрый поиск услуги:</label>
  <div style="position: relative;">
    <input type="text" id="searchInput" placeholder="Например: замена экрана, Windows, FRP...">
    <button id="clearBtn" onclick="document.getElementById('searchInput').value=''; document.getElementById('searchInput').dispatchEvent(new Event('input'));" 
            style="position: absolute; right: 8px; top: 50%; transform: translateY(-50%); 
                   background: #94a3b8; color: white; border: none; border-radius: 50%; 
                   width: 24px; height: 24px; cursor: pointer; font-size: 12px; display: none;">✕</button>
  </div>
  <div class="search-stats" id="searchStats" style="display: none;">
    Найдено: <span id="foundCount">0</span> услуг
  </div>
  <div class="no-results" id="noResults" style="display: none;">
    ❌ Ничего не найдено. Попробуйте: <b>ремонт</b>, <b>замена</b>, <b>Windows</b>, <b>разблокировка</b>
  </div>
</div>

<script>
(function() {
  document.addEventListener('DOMContentLoaded', function() {
    const searchInput = document.getElementById('searchInput');
    const clearBtn = document.getElementById('clearBtn');
    const statsDiv = document.getElementById('searchStats');
    const noResultsDiv = document.getElementById('noResults');
    const countSpan = document.getElementById('foundCount');
    
    if (!searchInput) return;
    
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
    
    searchInput.addEventListener('keypress', function(e) {
      if (e.key === 'Enter') {
        e.preventDefault();
        filterTables();
      }
    });
  });
})();
</script>

---

{% assign sorted_prices = site.prices | sort: 'path' %}

{% for category in sorted_prices %}
<h2 id="{{ category.category_id | default: category.slug }}">{{ category.title }}</h2>
<table class="price-table">
<colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<thead>
<tr><th>Услуга</th><th>Цена</th><th>Срок/Примечание</th></tr>
</thead>
<tbody>
{% for service in category.services %}
<tr>
  <td>{{ service.name }}</td>
  <td><strong>{{ service.price }}</strong></td>
  <td>{{ service.note }}</td>
</tr>
{% endfor %}
</tbody>
</table>
{% endfor %}

{% if site.prices.size == 0 %}
<p style="text-align: center; padding: 2rem; color: var(--text); opacity: 0.7;">
  📝 Прайс-лист обновляется. Позвоните для уточнения цен.
</p>
{% endif %}

---

<div class="info-highlight">
  <strong>💡 Бесплатная диагностика — платишь только за ремонт!</strong><br>
  <small>Цены актуальны на {{ site.time | date: "%d.%m.%Y" }}</small>
</div>

<div class="action-buttons">
  <a href="{{ site.baseurl }}/" class="btn-action btn-home">← На главную</a>
  <a href="https://t.me/alexdrog81" class="btn-action btn-telegram">💬 Telegram</a>
  <a href="tel:+375297256982" class="btn-action btn-phone">📞 Позвонить</a>
</div>
