---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

<style>
/* === ПЕРЕМЕННЫЕ === */
:root {
  --bg: #f8fafc;
  --bg-card: #ffffff;
  --bg-secondary: #f1f5f9;
  --bg-hover: #e2e8f0;
  --text: #1e293b;
  --text-secondary: #64748b;
  --text-muted: #94a3b8;
  --border: #cbd5e1;
  --accent: #3b82f6;
  --accent-hover: #2563eb;
  --shadow: rgba(0,0,0,0.08);
  --shadow-hover: rgba(0,0,0,0.12);
  --success: #10b981;
  --error-bg: #fee2e2;
  --error-text: #991b1b;
  --gradient-start: #3b82f6;
  --gradient-end: #6366f1;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg: #0f172a;
    --bg-card: #1e293b;
    --bg-secondary: #334155;
    --bg-hover: #475569;
    --text: #f8fafc;
    --text-secondary: #94a3b8;
    --text-muted: #64748b;
    --border: #334155;
    --accent: #60a5fa;
    --accent-hover: #3b82f6;
    --shadow: rgba(0,0,0,0.3);
    --shadow-hover: rgba(0,0,0,0.5);
    --success: #34d399;
    --error-bg: #450a0a;
    --error-text: #fca5a5;
    --gradient-start: #2563eb;
    --gradient-end: #4f46e5;
  }
}

html[data-theme="dark"] {
  --bg: #0f172a;
  --bg-card: #1e293b;
  --bg-secondary: #334155;
  --bg-hover: #475569;
  --text: #f8fafc;
  --text-secondary: #94a3b8;
  --text-muted: #64748b;
  --border: #334155;
  --accent: #60a5fa;
  --accent-hover: #3b82f6;
  --shadow: rgba(0,0,0,0.3);
  --shadow-hover: rgba(0,0,0,0.5);
  --success: #34d399;
  --error-bg: #450a0a;
  --error-text: #fca5a5;
  --gradient-start: #2563eb;
  --gradient-end: #4f46e5;
}

body {
  background-color: var(--bg);
  color: var(--text);
  -webkit-text-size-adjust: 100%;
}

/* === НАВИГАЦИЯ === */
.category-nav {
  position: sticky;
  top: 80px;
  background: var(--bg-card);
  padding: 1rem;
  border-radius: 16px;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 12px var(--shadow);
  z-index: 100;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  justify-content: center;
  border: 1px solid var(--border);
  max-height: 200px;
  overflow-y: auto;
}

.category-nav a {
  padding: 0.5rem 1rem;
  background: var(--bg-secondary);
  border-radius: 50px;
  text-decoration: none;
  font-size: 0.85rem;
  white-space: nowrap;
  color: var(--text);
  font-weight: 500;
  transition: all 0.2s;
  border: 1px solid var(--border);
  touch-action: manipulation;
}

.category-nav a:hover, .category-nav a:active {
  background: var(--accent);
  color: white;
  border-color: var(--accent);
  transform: translateY(-1px);
}

/* === АККОРДЕОН === */
.category-accordion {
  margin-bottom: 1rem;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px var(--shadow);
  border: 1px solid var(--border);
  background: var(--bg-card);
}

.category-accordion.hidden {
  display: none !important;
}

.category-header {
  background: linear-gradient(135deg, var(--gradient-start) 0%, var(--gradient-end) 100%);
  color: white;
  padding: 1rem 1.25rem;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 600;
  font-size: 1rem;
  border: none;
  width: 100%;
  text-align: left;
  transition: all 0.2s;
  margin: 0;
  min-height: 56px;
}

.category-header:active {
  opacity: 0.9;
}

.category-header .arrow {
  transition: transform 0.3s;
  font-size: 0.8rem;
  flex-shrink: 0;
  margin-left: 0.5rem;
}

.category-header.active .arrow {
  transform: rotate(180deg);
}

.category-content {
  display: none;
  background: var(--bg-card);
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}

.category-content.active {
  display: block;
}

/* === ТАБЛИЦА === */
.price-table {
  width: 100%;
  border-collapse: collapse;
  min-width: 600px; /* Минимальная ширина для читаемости */
}

.price-table th {
  background: var(--bg-secondary);
  padding: 0.875rem 1rem;
  text-align: left;
  font-weight: 600;
  color: var(--text);
  border-bottom: 2px solid var(--border);
  font-size: 0.9rem;
  white-space: nowrap;
}

.price-table td {
  padding: 1rem;
  border-bottom: 1px solid var(--border);
  color: var(--text);
  vertical-align: middle;
  font-size: 0.95rem;
}

.price-table tbody tr:active {
  background-color: var(--bg-hover);
}

.price-table tbody tr:last-child td {
  border-bottom: none;
}

/* === УСЛУГА === */
.service-name {
  color: var(--accent);
  cursor: pointer;
  font-weight: 600;
  text-decoration: underline;
  text-decoration-color: transparent;
  transition: all 0.2s;
  display: inline;
  padding: 0.25rem 0;
}

.service-name:hover, .service-name:active {
  text-decoration-color: var(--accent);
  color: var(--accent-hover);
}

/* === ПОИСК === */
.search-container {
  margin-bottom: 1.5rem;
  background: var(--bg-card);
  padding: 1.25rem;
  border-radius: 16px;
  border: 1px solid var(--border);
  box-shadow: 0 2px 8px var(--shadow);
}

.search-container label {
  display: block;
  color: var(--text);
  font-weight: 600;
  margin-bottom: 0.75rem;
  font-size: 1.05rem;
}

.search-wrapper {
  position: relative;
}

#searchInput {
  width: 100%;
  padding: 0.875rem 2.75rem 0.875rem 1rem;
  border: 2px solid var(--border);
  border-radius: 12px;
  font-size: 16px; /* Предотвращает зум на iOS */
  background: var(--bg);
  color: var(--text);
  transition: all 0.2s;
  font-family: inherit;
  -webkit-appearance: none;
}

#searchInput:focus {
  outline: none;
  border-color: var(--accent);
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.15);
}

#searchInput::placeholder {
  color: var(--text-muted);
}

#clearBtn {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  background: var(--text-muted);
  color: white;
  border: none;
  border-radius: 50%;
  width: 32px;
  height: 32px;
  cursor: pointer;
  font-size: 14px;
  display: none;
  align-items: center;
  justify-content: center;
  padding: 0;
  touch-action: manipulation;
}

#clearBtn:active {
  transform: translateY(-50%) scale(0.95);
}

.search-stats {
  margin-top: 0.75rem;
  color: var(--text-secondary);
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.no-results {
  margin-top: 1rem;
  padding: 1rem;
  background: var(--error-bg);
  border-radius: 10px;
  color: var(--error-text);
  text-align: center;
  display: none;
  border: 1px solid var(--border);
  font-weight: 500;
  font-size: 0.95rem;
}

/* === МОДАЛЬНОЕ ОКНО === */
.messenger-modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.7);
  z-index: 1000;
  justify-content: center;
  align-items: flex-end; /* Прижимаем к низу на мобильных */
  padding: 0;
}

.messenger-modal.active {
  display: flex;
}

.messenger-content {
  background: var(--bg-card);
  padding: 1.5rem;
  border-radius: 20px 20px 0 0; /* Скругление только сверху на мобильных */
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  box-shadow: 0 -10px 40px var(--shadow-hover);
  border: 1px solid var(--border);
  border-bottom: none;
  animation: slideUp 0.3s ease-out;
}

@keyframes slideUp {
  from { transform: translateY(100%); }
  to { transform: translateY(0); }
}

.messenger-title {
  font-size: 1.2rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--text);
  text-align: center;
}

.messenger-service {
  color: var(--accent);
  font-weight: 600;
  margin-bottom: 1.25rem;
  padding: 0.75rem;
  background: var(--bg-secondary);
  border-radius: 10px;
  font-size: 1rem;
  word-break: break-word;
  text-align: center;
}

.messenger-buttons {
  display: grid;
  gap: 0.75rem;
}

.messenger-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  padding: 1rem;
  border-radius: 12px;
  text-decoration: none;
  font-weight: 600;
  color: white;
  transition: transform 0.1s;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  min-height: 52px; /* Удобно для пальца */
  touch-action: manipulation;
}

.messenger-btn:active {
  transform: scale(0.98);
}

.btn-tg { background: #0088cc; }
.btn-viber { background: #7360f2; }
.btn-whatsapp { background: #25d366; }
.btn-phone { background: var(--success); }
.btn-cancel { 
  background: var(--bg-secondary); 
  color: var(--text);
  border: 2px solid var(--border);
  margin-top: 0.5rem;
}

/* === АДАПТИВНОСТЬ ДЛЯ ПК === */
@media (min-width: 769px) {
  .category-nav {
    padding: 1.25rem;
    gap: 0.75rem;
    top: 90px;
  }
  
  .category-nav a {
    padding: 0.6rem 1.2rem;
    font-size: 0.9rem;
  }
  
  .category-header {
    padding: 1.25rem 1.5rem;
    font-size: 1.1rem;
  }
  
  .price-table {
    min-width: 100%;
  }
  
  .price-table th,
  .price-table td {
    padding: 1.25rem;
    font-size: 1rem;
  }
  
  .messenger-modal {
    align-items: center;
    padding: 1rem;
    background: rgba(0,0,0,0.5);
  }
  
  .messenger-content {
    border-radius: 20px;
    max-width: 420px;
    max-height: 85vh;
    animation: fadeIn 0.2s;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; transform: scale(0.95); }
    to { opacity: 1; transform: scale(1); }
  }
}

/* === МОБИЛЬНЫЕ ОПТИМИЗАЦИИ === */
@media (max-width: 480px) {
  .category-nav {
    top: 70px;
    padding: 0.75rem;
    gap: 0.4rem;
    border-radius: 12px;
  }
  
  .category-nav a {
    font-size: 0.8rem;
    padding: 0.4rem 0.875rem;
  }
  
  .search-container {
    padding: 1rem;
    border-radius: 12px;
  }
  
  .price-table th,
  .price-table td {
    padding: 0.75rem 0.625rem;
    font-size: 0.9rem;
  }
  
  .category-header {
    padding: 0.875rem 1rem;
  }
}
</style>

# 📋 Прайс-лист

<!-- НАВИГАЦИЯ -->
<div class="category-nav">
  {% assign sorted_prices = site.prices | sort: 'path' %}
  {% for category in sorted_prices %}
    <a href="#{{ category.category_id | default: category.slug }}">{{ category.title }}</a>
  {% endfor %}
</div>

<!-- ПОИСК -->
<div class="search-container">
  <label>🔍 Быстрый поиск услуги</label>
  <div class="search-wrapper">
    <input type="text" id="searchInput" placeholder="Например: замена экрана..." autocomplete="off">
    <button id="clearBtn" onclick="clearSearch()" aria-label="Очистить">✕</button>
  </div>
  <div class="search-stats" id="searchStats" style="display: none;">
    <span>📊 Найдено: <strong id="foundCount">0</strong> услуг</span>
  </div>
  <div class="no-results" id="noResults">
    ❌ Ничего не найдено. Попробуйте: <b>ремонт</b>, <b>экран</b>, <b>Windows</b>
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
        <col style="width:55%">
        <col style="width:20%">
        <col style="width:25%">
      </colgroup>
      <thead>
        <tr>
          <th>Услуга</th>
          <th>Цена</th>
          <th>Срок</th>
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
          <td><strong style="color: var(--accent); white-space: nowrap;">{{ service.price }}</strong></td>
          <td style="color: var(--text-secondary); font-size: 0.9rem;">{{ service.note }}</td>
        </tr>
        {% endfor %}
      </tbody>
    </table>
  </div>
</div>
{% endfor %}

{% if site.prices.size == 0 %}
<p style="text-align: center; padding: 2rem; color: var(--text-secondary); background: var(--bg-card); border-radius: 12px; border: 1px solid var(--border); margin: 2rem 0;">
  📝 Прайс-лист обновляется. Позвоните для уточнения цен.
</p>
{% endif %}

<div style="text-align: center; margin: 2rem 0;">
  <a href="{{ site.baseurl }}/" style="display: inline-block; padding: 0.875rem 1.5rem; background: var(--bg-secondary); color: var(--text); text-decoration: none; border-radius: 10px; border: 1px solid var(--border); font-weight: 500; margin: 0.25rem;">← На главную</a>
  <a href="tel:+375297256982" style="display: inline-block; padding: 0.875rem 1.5rem; background: var(--success); color: white; text-decoration: none; border-radius: 10px; font-weight: 600; margin: 0.25rem;">📞 Позвонить</a>
</div>

<!-- МОДАЛЬНОЕ ОКНО -->
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
        ✕ Отмена
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

// Поиск
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
  
  clearBtn.style.display = searchTerm.length > 0 ? 'flex' : 'none';
  
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
      accordion.classList.remove('hidden');
      btn.classList.remove('active');
      content.classList.remove('active');
    } else {
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
    statsDiv.style.display = 'flex';
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

// Модальное окно
function openMessengerModal(serviceName, price) {
  const modal = document.getElementById('messengerModal');
  const serviceDiv = document.getElementById('modalServiceName');
  
  serviceDiv.textContent = price ? `${serviceName} (${price})` : serviceName;
  
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

document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape') {
    closeMessengerModal();
  }
});

// Закрытие по свайпу вниз на мобильных
let touchStartY = 0;
const modalContent = document.querySelector('.messenger-content');
if (modalContent) {
  modalContent.addEventListener('touchstart', e => {
    touchStartY = e.touches[0].clientY;
  });
  modalContent.addEventListener('touchend', e => {
    const touchEndY = e.changedTouches[0].clientY;
    if (touchEndY - touchStartY > 100) { // Свайп вниз больше 100px
      closeMessengerModal();
    }
  });
}
</script>
