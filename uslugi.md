---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

<style>
/* Липкая навигация */
.category-nav {
  position: sticky;
  top: 80px;
  background: var(--bg, #ffffff);
  padding: 1rem;
  border-radius: 12px;
  margin-bottom: 2rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  z-index: 100;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  justify-content: center;
  border: 1px solid var(--border, #e2e8f0);
}

.category-nav a {
  padding: 0.5rem 1rem;
  background: var(--bg-secondary, #f1f5f9);
  border-radius: 20px;
  text-decoration: none;
  font-size: 0.85rem;
  white-space: nowrap;
  color: var(--text, #334155);
  transition: all 0.2s;
  border: 1px solid transparent;
}

.category-nav a:hover {
  background: var(--accent, #3b82f6);
  color: white;
  transform: translateY(-2px);
}

/* Аккордеон */
.category-accordion {
  margin-bottom: 1rem;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  border: 1px solid var(--border, #e2e8f0);
  background: var(--bg, #ffffff);
}

.category-header {
  background: linear-gradient(135deg, var(--primary, #3b82f6) 0%, var(--secondary, #6366f1) 100%);
  color: white;
  padding: 1rem 1.5rem;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 600;
  font-size: 1.1rem;
  border: none;
  width: 100%;
  text-align: left;
  transition: all 0.3s;
  margin: 0;
}

.category-header:hover {
  opacity: 0.95;
  transform: translateX(5px);
}

.category-header .arrow {
  transition: transform 0.3s;
  font-size: 0.8rem;
}

.category-header.active .arrow {
  transform: rotate(180deg);
}

.category-content {
  display: none;
  padding: 0;
  background: var(--bg, #ffffff);
}

.category-content.active {
  display: block;
  animation: slideDown 0.3s ease-out;
}

@keyframes slideDown {
  from { opacity: 0; max-height: 0; }
  to { opacity: 1; max-height: 2000px; }
}

/* Таблица внутри аккордеона */
.category-content .price-table {
  margin: 0;
  border-radius: 0;
  box-shadow: none;
  border: none;
}

/* Адаптивность */
@media (max-width: 768px) {
  .category-nav {
    top: 70px;
    padding: 0.8rem;
    gap: 0.4rem;
  }
  
  .category-nav a {
    font-size: 0.8rem;
    padding: 0.4rem 0.8rem;
  }
  
  .category-header {
    font-size: 1rem;
    padding: 0.8rem 1rem;
  }
}

/* Поиск */
.search-container {
  margin-bottom: 2rem;
}
</style>

# 📋 Прайс-лист

<!-- ЛИПКАЯ НАВИГАЦИЯ -->
<div class="category-nav">
  {% assign sorted_prices = site.prices | sort: 'path' %}
  {% for category in sorted_prices %}
    <a href="#{{ category.category_id | default: category.slug }}">{{ category.title }}</a>
  {% endfor %}
</div>

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

{% assign sorted_prices = site.prices | sort: 'path' %}

{% for category in sorted_prices %}
<h2 id="{{ category.category_id | default: category.slug }}" style="scroll-margin-top: 140px;">{{ category.title }}</h2>
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
  <a href="https://t.me/alexdrog81 " class="btn-action btn-telegram">💬 Telegram</a>
  <a href="tel:+375297256982" class="btn-action btn-phone">📞 Позвонить</a>
</div>

<script>
// Аккордеон
document.addEventListener('DOMContentLoaded', function() {
  const tables = document.querySelectorAll('.price-table');
  
  tables.forEach(table => {
    const header = table.previousElementSibling;
    if (header && header.tagName === 'H2') {
      const wrapper = document.createElement('div');
      wrapper.className = 'category-accordion';
      
      const btn = document.createElement('button');
      btn.className = 'category-header';
      btn.innerHTML = header.innerHTML + '<span class="arrow">▼</span>';
      btn.setAttribute('type', 'button');
      
      const content = document.createElement('div');
      content.className = 'category-content';
      
      // Перемещаем таблицу внутрь аккордеона
      table.parentNode.insertBefore(wrapper, header);
      wrapper.appendChild(btn);
      wrapper.appendChild(content);
      content.appendChild(table);
      
      // Удаляем оригинальный H2
      header.remove();
      
      // Обработчик клика
      btn.addEventListener('click', () => {
        const isActive = btn.classList.toggle('active');
        content.classList.toggle('active');
      });
    }
  });
  
  // Поиск с автоматическим раскрытием аккордеонов
  const searchInput = document.getElementById('searchInput');
  const clearBtn = document.getElementById('clearBtn');
  const statsDiv = document.getElementById('searchStats');
  const noResultsDiv = document.getElementById('noResults');
  const countSpan = document.getElementById('foundCount');
  
  if (searchInput) {
    function filterTables() {
      const searchTerm = searchInput.value.toLowerCase().trim();
      const accordions = document.querySelectorAll('.category-accordion');
      let totalFound = 0;
      let hasVisibleTables = false;
      
      clearBtn.style.display = searchTerm.length > 0 ? 'block' : 'none';
      
      accordions.forEach(accordion => {
        const rows = accordion.querySelectorAll('tbody tr');
        const content = accordion.querySelector('.category-content');
        const btn = accordion.querySelector('.category-header');
        let tableHasVisibleRows = false;
        
        rows.forEach((row) => {
          const text = row.innerText.toLowerCase();
          const isMatch = text.includes(searchTerm);
          
          row.style.display = (isMatch || searchTerm.length === 0) ? '' : 'none';
          
          if (isMatch && searchTerm.length > 0) {
            totalFound++;
            tableHasVisibleRows = true;
            // Раскрываем аккордеон если найдено
            btn.classList.add('active');
            content.classList.add('active');
          }
        });
        
        if (tableHasVisibleRows) {
          hasVisibleTables = true;
        }
        
        // Если поиск очищен, закрываем все аккордеоны
        if (searchTerm.length === 0) {
          btn.classList.remove('active');
          content.classList.remove('active');
        }
      });
      
      if (searchTerm.length > 0) {
        statsDiv.style.display = 'block';
        countSpan.textContent = totalFound;
        noResultsDiv.style.display = hasVisibleTables ? 'none' : 'block';
      } else {
        statsDiv.style.display = 'none';
        noResultsDiv.style.display = 'none';
      }
    }
    
    searchInput.addEventListener('input', filterTables);
    
    searchInput.addEventListener('keypress', function(e) {
      if (e.key === 'Enter') {
        e.preventDefault();
        filterTables();
      }
    });
  }
});
</script>
