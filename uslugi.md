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
  transition: all 0.3s;
}

.category-accordion.hidden {
  display: none !important;
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

/* Таблица */
.price-table {
  width: 100%;
  border-collapse: collapse;
}

.price-table th {
  background: var(--bg-secondary, #f1f5f9);
  padding: 1rem;
  text-align: left;
  font-weight: 600;
  color: var(--text, #334155);
  border-bottom: 2px solid var(--border, #e2e8f0);
}

.price-table td {
  padding: 1rem;
  border-bottom: 1px solid var(--border, #e2e8f0);
  color: var(--text, #334155);
}

/* Кликабельное название услуги */
.service-name {
  color: var(--accent, #3b82f6);
  cursor: pointer;
  font-weight: 500;
  text-decoration: underline;
  text-decoration-color: transparent;
  transition: all 0.2s;
  position: relative;
  padding: 0.2rem 0;
}

.service-name:hover {
  text-decoration-color: var(--accent, #3b82f6);
  color: var(--primary, #2563eb);
}

.service-name::after {
  content: "📱";
  margin-left: 0.5rem;
  opacity: 0.5;
  font-size: 0.9em;
}

/* Подсветка строки */
.price-table tbody tr {
  transition: background-color 0.2s;
}

.price-table tbody tr:hover {
  background-color: var(--bg-secondary, #f8fafc);
}

/* Модальное окно выбора мессенджера */
.messenger-modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
  justify-content: center;
  align-items: center;
  backdrop-filter: blur(4px);
}

.messenger-modal.active {
  display: flex;
  animation: fadeIn 0.2s;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.messenger-content {
  background: var(--bg, #ffffff);
  padding: 2rem;
  border-radius: 16px;
  max-width: 400px;
  width: 90%;
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
  text-align: center;
}

.messenger-title {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: var(--text, #1e293b);
}

.messenger-service {
  color: var(--accent, #3b82f6);
  font-weight: 700;
  margin-bottom: 1.5rem;
  padding: 0.5rem;
  background: var(--bg-secondary, #f1f5f9);
  border-radius: 8px;
}

.messenger-buttons {
  display: grid;
  gap: 0.75rem;
}

.messenger-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.9rem;
  border-radius: 10px;
  text-decoration: none;
  font-weight: 600;
  color: white;
  transition: all 0.2s;
  border: none;
  cursor: pointer;
  font-size: 1rem;
}

.messenger-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}

.btn-tg { background: #0088cc; }
.btn-viber { background: #665cac; }
.btn-whatsapp { background: #25d366; }
.btn-phone { background: #10b981; }
.btn-cancel { 
  background: var(--bg-secondary, #e2e8f0); 
  color: var(--text, #64748b);
  margin-top: 0.5rem;
}

.close-modal {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: var(--text-secondary, #94a3b8);
}

/* Поиск */
.search-container {
  margin-bottom: 2rem;
}

.search-stats {
  margin-top: 0.5rem;
  color: var(--text-secondary, #64748b);
  font-size: 0.9rem;
}

.no-results {
  margin-top: 1rem;
  padding: 1.5rem;
  background: #fee2e2;
  border-radius: 8px;
  color: #991b1b;
  text-align: center;
  display: none;
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
  
  .price-table th, .price-table td {
    padding: 0.75rem 0.5rem;
    font-size: 0.9rem;
  }
  
  .service-name::after {
    content: "";
  }
  
  .messenger-content {
    padding: 1.5rem;
  }
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
  <div style="position: relative; margin-top: 0.5rem;">
    <input type="text" id="searchInput" placeholder="Например: замена экрана, Windows, FRP..." 
           style="width: 100%; padding: 0.75rem; padding-right: 2.5rem; border: 2px solid var(--border, #e2e8f0); 
                  border-radius: 8px; font-size: 1rem; background: var(--bg, #ffffff); color: var(--text, #334155);">
    <button id="clearBtn" onclick="clearSearch()" 
            style="position: absolute; right: 8px; top: 50%; transform: translateY(-50%); 
                   background: #94a3b8; color: white; border: none; border-radius: 50%; 
                   width: 24px; height: 24px; cursor: pointer; font-size: 12px; display: none;">✕</button>
  </div>
  <div class="search-stats" id="searchStats" style="display: none;">
    Найдено: <span id="foundCount">0</span> услуг
  </div>
  <div class="no-results" id="noResults">
    ❌ Ничего не найдено. Попробуйте: <b>ремонт</b>, <b>замена</b>, <b>Windows</b>, <b>разблокировка</b>
  </div>
</div>

{% assign sorted_prices = site.prices | sort: 'path' %}

{% for category in sorted_prices %}
<div class="category-accordion" data-category="{{ category.category_id | default: category.slug }}">
  <button class="category-header" type="button">
    <span>{{ category.title }}</span>
    <span class="arrow">▼</span>
  </button>
  <div class="category-content">
    <table class="price-table">
      <colgroup>
        <col style="width:50%">
        <col style="width:25%">
        <col style="width:25%">
      </colgroup>
      <thead>
        <tr>
          <th>Услуга (нажмите для заказа)</th>
          <th>Цена</th>
          <th>Срок/Примечание</th>
        </tr>
      </thead>
      <tbody>
        {% for service in category.services %}
        <tr data-service-name="{{ service.name }}" data-service-price="{{ service.price }}">
          <td>
            <span class="service-name" onclick="openMessengerModal('{{ service.name }}', '{{ service.price }}')">
              {{ service.name }}
            </span>
          </td>
          <td><strong>{{ service.price }}</strong></td>
          <td>{{ service.note }}</td>
        </tr>
        {% endfor %}
      </tbody>
    </table>
  </div>
</div>
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

<!-- Модальное окно выбора мессенджера -->
<div id="messengerModal" class="messenger-modal" onclick="closeMessengerModal(event)">
  <div class="messenger-content" onclick="event.stopPropagation()">
    <div class="messenger-title">📱 Выберите способ связи</div>
    <div class="messenger-service" id="modalServiceName">Услуга</div>
    
    <div class="messenger-buttons">
      <a href="#" id="tgLink" class="messenger-btn btn-tg" target="_blank">
        <span>✈️</span> Telegram
      </a>
      <a href="#" id="viberLink" class="messenger-btn btn-viber" target="_blank">
        <span>📞</span> Viber
      </a>
      <a href="#" id="waLink" class="messenger-btn btn-whatsapp" target="_blank">
        <span>💬</span> WhatsApp
      </a>
      <a href="#" id="phoneLink" class="messenger-btn btn-phone">
        <span>📱</span> Позвонить
      </a>
      <button onclick="closeMessengerModal()" class="messenger-btn btn-cancel">
        Отмена
      </button>
    </div>
  </div>
</div>

<script>
// Аккордеон
document.addEventListener('DOMContentLoaded', function() {
  const headers = document.querySelectorAll('.category-header');
  
  headers.forEach(header => {
    header.addEventListener('click', () => {
      const isActive = header.classList.toggle('active');
      const content = header.nextElementSibling;
      content.classList.toggle('active');
    });
  });
});

// Поиск с полным скрытием категорий
const searchInput = document.getElementById('searchInput');
const clearBtn = document.getElementById('clearBtn');
const statsDiv = document.getElementById('searchStats');
const noResultsDiv = document.getElementById('noResults');
const countSpan = document.getElementById('foundCount');

function filterTables() {
  const searchTerm = searchInput.value.toLowerCase().trim();
  const accordions = document.querySelectorAll('.category-accordion');
  let totalFound = 0;
  let hasAnyVisible = false;
  
  clearBtn.style.display = searchTerm.length > 0 ? 'block' : 'none';
  
  accordions.forEach(accordion => {
    const rows = accordion.querySelectorAll('tbody tr');
    const content = accordion.querySelector('.category-content');
    const btn = accordion.querySelector('.category-header');
    let categoryHasMatches = false;
    
    rows.forEach((row) => {
      const serviceName = row.getAttribute('data-service-name').toLowerCase();
      const note = row.cells[2] ? row.cells[2].innerText.toLowerCase() : '';
      const isMatch = serviceName.includes(searchTerm) || note.includes(searchTerm);
      
      if (searchTerm.length === 0 || isMatch) {
        row.style.display = '';
        if (isMatch) {
          totalFound++;
          categoryHasMatches = true;
        }
      } else {
        row.style.display = 'none';
      }
    });
    
    if (searchTerm.length === 0) {
      // Поиск пуст - показываем все, закрываем аккордеоны
      accordion.classList.remove('hidden');
      btn.classList.remove('active');
      content.classList.remove('active');
    } else {
      // Есть поисковый запрос
      if (categoryHasMatches) {
        accordion.classList.remove('hidden');
        btn.classList.add('active');
        content.classList.add('active');
        hasAnyVisible = true;
      } else {
        accordion.classList.add('hidden');
      }
    }
  });
  
  if (searchTerm.length > 0) {
    statsDiv.style.display = 'block';
    countSpan.textContent = totalFound;
    noResultsDiv.style.display = hasAnyVisible ? 'none' : 'block';
  } else {
    statsDiv.style.display = 'none';
    noResultsDiv.style.display = 'none';
  }
}

function clearSearch() {
  searchInput.value = '';
  filterTables();
  searchInput.focus();
}

if (searchInput) {
  searchInput.addEventListener('input', filterTables);
  
  searchInput.addEventListener('keypress', function(e) {
    if (e.key === 'Enter') {
      e.preventDefault();
      filterTables();
    }
  });
}

// Модальное окно мессенджеров
let currentService = '';
let currentPrice = '';

function openMessengerModal(serviceName, price) {
  currentService = serviceName;
  currentPrice = price;
  
  const modal = document.getElementById('messengerModal');
  const serviceDiv = document.getElementById('modalServiceName');
  
  serviceDiv.textContent = price ? `${serviceName} (${price})` : serviceName;
  
  // Формируем ссылки
  const text = `Здравствуйте! Хочу заказать: ${serviceName}${price ? ' (' + price + ')' : ''}`;
  const encodedText = encodeURIComponent(text);
  
  document.getElementById('tgLink').href = `https://t.me/alexdrog81?text=${encodedText}`;
  document.getElementById('viberLink').href = `viber://chat?number=+375297256982&draft=${encodedText}`;
  document.getElementById('waLink').href = `https://wa.me/375297256982?text=${encodedText}`;
  document.getElementById('phoneLink').href = `tel:+375297256982`;
  
  modal.classList.add('active');
  document.body.style.overflow = 'hidden';
}

function closeMessengerModal(event) {
  if (!event || event.target.id === 'messengerModal' || event.target.tagName === 'BUTTON') {
    document.getElementById('messengerModal').classList.remove('active');
    document.body.style.overflow = '';
  }
}

// Закрытие по Escape
document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape') {
    closeMessengerModal();
  }
});
</script>
