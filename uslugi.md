---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

<style>
/* === ПЕРЕМЕННЫЕ — мягкие цвета, нет резкой черноты === */
:root {
  --bg: #f1f5f9;           /* Мягкий серо-голубой фон */
  --bg-card: #ffffff;       /* Белые карточки */
  --bg-secondary: #f8fafc;  /* Очень светлый для заголовков */
  --bg-hover: #e2e8f0;      /* Hover — мягкий серый */
  --text: #475569;          /* Основной текст — серо-синий (не черный!) */
  --text-secondary: #64748b;/* Вторичный — серый */
  --text-muted: #94a3b8;    /* Приглушенный */
  --border: #e2e8f0;        /* Границы — светло-серые */
  --accent: #3b82f6;        /* Акцент — синий */
  --accent-hover: #2563eb;
  --shadow: rgba(0,0,0,0.04); /* Мягкая тень */
  --success: #10b981;
  --error-bg: #fef2f2;
  --error-text: #dc2626;
  --gradient-start: #60a5fa;
  --gradient-end: #818cf8;
}

/* Темная тема */
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #0f172a;
    --bg-card: #1e293b;
    --bg-secondary: #334155;
    --bg-hover: #475569;
    --text: #e2e8f0;        /* Светло-серый, не белый */
    --text-secondary: #94a3b8;
    --text-muted: #64748b;
    --border: #334155;
    --accent: #60a5fa;
    --shadow: rgba(0,0,0,0.2);
    --error-bg: #450a0a;
    --error-text: #fca5a5;
  }
}

html[data-theme="dark"] {
  --bg: #0f172a;
  --bg-card: #1e293b;
  --bg-secondary: #334155;
  --text: #e2e8f0;
  --border: #334155;
}

body {
  background-color: var(--bg);
  color: var(--text);
  line-height: 1.5;
}

/* === НАВИГАЦИЯ — компактная === */
.category-nav {
  position: sticky;
  top: 70px;
  background: var(--bg-card);
  padding: 0.75rem;
  border-radius: 12px;
  margin-bottom: 1rem;
  box-shadow: 0 1px 3px var(--shadow);
  z-index: 100;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  justify-content: center;
  border: 1px solid var(--border);
  max-height: 160px;
  overflow-y: auto;
}

.category-nav a {
  padding: 0.4rem 0.9rem;
  background: var(--bg-secondary);
  border-radius: 20px;
  text-decoration: none;
  font-size: 0.8rem;
  white-space: nowrap;
  color: var(--text-secondary);
  font-weight: 500;
  transition: all 0.2s;
  border: 1px solid var(--border);
}

.category-nav a:hover {
  background: var(--accent);
  color: white;
  border-color: var(--accent);
}

/* === АККОРДЕОН === */
.category-accordion {
  margin-bottom: 0.75rem;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 1px 3px var(--shadow);
  border: 1px solid var(--border);
  background: var(--bg-card);
}

.category-accordion.hidden {
  display: none !important;
}

.category-header {
  background: linear-gradient(135deg, var(--gradient-start) 0%, var(--gradient-end) 100%);
  color: white;
  padding: 0.875rem 1rem;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 600;
  font-size: 0.95rem;
  border: none;
  width: 100%;
  text-align: left;
  margin: 0;
}

.category-header .arrow {
  transition: transform 0.3s;
  font-size: 0.75rem;
  opacity: 0.8;
}

.category-header.active .arrow {
  transform: rotate(180deg);
}

.category-content {
  display: none;
  background: var(--bg-card);
}

.category-content.active {
  display: block;
}

/* === ТАБЛИЦА — МОБИЛЬНАЯ КОМПАКТНАЯ === */
.price-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.9rem;
}

.price-table th {
  background: var(--bg-secondary);
  padding: 0.625rem 0.75rem;
  text-align: left;
  font-weight: 600;
  color: var(--text-secondary);
  border-bottom: 1px solid var(--border);
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.price-table td {
  padding: 0.75rem;
  border-bottom: 1px solid var(--border);
  color: var(--text);
  vertical-align: top;
}

.price-table tbody tr:last-child td {
  border-bottom: none;
}

/* Услуга — компактно */
.service-name {
  color: var(--accent);
  cursor: pointer;
  font-weight: 600;
  text-decoration: none;
  display: block;
  line-height: 1.3;
  margin-bottom: 0.25rem;
}

.service-name:active {
  opacity: 0.7;
}

/* Цена — выделена */
td strong {
  color: var(--accent);
  font-weight: 700;
  white-space: nowrap;
}

/* Примечание — мелкое */
td:last-child {
  color: var(--text-secondary);
  font-size: 0.85rem;
}

/* === ПОИСК === */
.search-container {
  margin-bottom: 1rem;
  background: var(--bg-card);
  padding: 1rem;
  border-radius: 12px;
  border: 1px solid var(--border);
  box-shadow: 0 1px 3px var(--shadow);
}

.search-container label {
  display: block;
  color: var(--text-secondary);
  font-weight: 600;
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
}

.search-wrapper {
  position: relative;
}

#searchInput {
  width: 100%;
  padding: 0.625rem 2.5rem 0.625rem 0.875rem;
  border: 1px solid var(--border);
  border-radius: 8px;
  font-size: 16px; /* Анти-зум iOS */
  background: var(--bg-secondary);
  color: var(--text);
  font-family: inherit;
}

#searchInput:focus {
  outline: none;
  border-color: var(--accent);
  background: var(--bg-card);
}

#searchInput::placeholder {
  color: var(--text-muted);
}

#clearBtn {
  position: absolute;
  right: 8px;
  top: 50%;
  transform: translateY(-50%);
  background: var(--text-muted);
  color: white;
  border: none;
  border-radius: 50%;
  width: 24px;
  height: 24px;
  cursor: pointer;
  font-size: 12px;
  display: none;
  align-items: center;
  justify-content: center;
}

.search-stats {
  margin-top: 0.5rem;
  color: var(--text-muted);
  font-size: 0.85rem;
}

.no-results {
  margin-top: 0.75rem;
  padding: 0.75rem;
  background: var(--error-bg);
  border-radius: 8px;
  color: var(--error-text);
  text-align: center;
  display: none;
  font-size: 0.9rem;
  border: 1px solid var(--border);
}

/* === МОДАЛЬНОЕ ОКНО (снизу) === */
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
  align-items: flex-end;
}

.messenger-modal.active {
  display: flex;
}

.messenger-content {
  background: var(--bg-card);
  padding: 1.25rem;
  border-radius: 16px 16px 0 0;
  width: 100%;
  max-height: 80vh;
  overflow-y: auto;
  border: 1px solid var(--border);
  border-bottom: none;
  animation: slideUp 0.25s ease-out;
}

@keyframes slideUp {
  from { transform: translateY(100%); }
  to { transform: translateY(0); }
}

.messenger-title {
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--text);
  text-align: center;
}

.messenger-service {
  color: var(--accent);
  font-weight: 600;
  margin-bottom: 1rem;
  padding: 0.5rem;
  background: var(--bg-secondary);
  border-radius: 8px;
  font-size: 0.95rem;
  text-align: center;
}

.messenger-buttons {
  display: grid;
  gap: 0.625rem;
}

.messenger-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.875rem;
  border-radius: 10px;
  text-decoration: none;
  font-weight: 600;
  color: white;
  border: none;
  cursor: pointer;
  font-size: 0.95rem;
  min-height: 48px;
}

.btn-tg { background: #0088cc; }
.btn-viber { background: #7360f2; }
.btn-whatsapp { background: #25d366; }
.btn-phone { background: var(--success); }
.btn-cancel { 
  background: var(--bg-secondary); 
  color: var(--text-secondary);
  border: 1px solid var(--border);
  margin-top: 0.25rem;
}

/* === ДЕСКТОП === */
@media (min-width: 768px) {
  .category-nav {
    padding: 1rem;
    gap: 0.625rem;
    top: 80px;
  }
  
  .category-nav a {
    padding: 0.5rem 1.1rem;
    font-size: 0.9rem;
  }
  
  .category-header {
    padding: 1rem 1.25rem;
    font-size: 1.05rem;
  }
  
  .price-table {
    font-size: 1rem;
  }
  
  .price-table th {
    padding: 0.875rem 1rem;
    font-size: 0.85rem;
  }
  
  .price-table td {
    padding: 1rem;
  }
  
  .search-container {
    padding: 1.25rem;
  }
  
  .messenger-modal {
    align-items: center;
    padding: 1rem;
  }
  
  .messenger-content {
    border-radius: 16px;
    max-width: 400px;
    max-height: 90vh;
    animation: fadeIn 0.2s;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; transform: scale(0.95); }
    to { opacity: 1; transform: scale(1); }
  }
}

/* === МАЛЕНЬКИЕ МОБИЛЬНЫЕ === */
@media (max-width: 380px) {
  .price-table {
    font-size: 0.85rem;
  }
  
  .price-table td {
    padding: 0.625rem 0.5rem;
  }
  
  .service-name {
    font-size: 0.9rem;
  }
  
  td:last-child {
    font-size: 0.8rem;
  }
  
  .category-header {
    padding: 0.75rem 0.875rem;
    font-size: 0.9rem;
  }
}
</style>

# 📋 Прайс-лист

<div class="category-nav">
  {% assign sorted_prices = site.prices | sort: 'path' %}
  {% for category in sorted_prices %}
    <a href="#{{ category.category_id | default: category.slug }}">{{ category.title }}</a>
  {% endfor %}
</div>

<div class="search-container">
  <label>🔍 Поиск услуги</label>
  <div class="search-wrapper">
    <input type="text" id="searchInput" placeholder="Например: экран, батарея..." autocomplete="off">
    <button id="clearBtn" onclick="clearSearch()">✕</button>
  </div>
  <div class="search-stats" id="searchStats" style="display: none;">
    Найдено: <span id="foundCount">0</span>
  </div>
  <div class="no-results" id="noResults">
    Ничего не найдено. Попробуйте: <b>ремонт</b>, <b>замена</b>
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
<p style="text-align: center; padding: 2rem; color: var(--text-secondary); background: var(--bg-card); border-radius: 12px; border: 1px solid var(--border); margin: 1rem 0; font-size: 0.95rem;">
  📝 Прайс-лист обновляется. Позвоните для уточнения цен.
</p>
{% endif %}

<div style="text-align: center; margin: 1.5rem 0;">
  <a href="{{ site.baseurl }}/" style="display: inline-block; padding: 0.75rem 1.25rem; background: var(--bg-card); color: var(--text); text-decoration: none; border-radius: 8px; border: 1px solid var(--border); font-weight: 500; margin: 0.25rem; font-size: 0.9rem;">← На главную</a>
  <a href="tel:+375297256982" style="display: inline-block; padding: 0.75rem 1.25rem; background: var(--success); color: white; text-decoration: none; border-radius: 8px; font-weight: 600; margin: 0.25rem; font-size: 0.9rem;">📞 Позвонить</a>
</div>

<div id="messengerModal" class="messenger-modal" onclick="closeMessengerModal(event)">
  <div class="messenger-content" onclick="event.stopPropagation()">
    <div class="messenger-title">Выберите способ связи</div>
    <div class="messenger-service" id="modalServiceName">Услуга</div>
    
    <div class="messenger-buttons">
      <a href="#" id="tgLink" class="messenger-btn btn-tg" target="_blank">Telegram</a>
      <a href="#" id="viberLink" class="messenger-btn btn-viber" target="_blank">Viber</a>
      <a href="#" id="waLink" class="messenger-btn btn-whatsapp" target="_blank">WhatsApp</a>
      <a href="#" id="phoneLink" class="messenger-btn btn-phone">Позвонить</a>
      <button onclick="closeMessengerModal()" class="messenger-btn btn-cancel">Отмена</button>
    </div>
  </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const headers = document.querySelectorAll('.category-header');
  headers.forEach(header => {
    header.addEventListener('click', () => {
      header.classList.toggle('active');
      header.nextElementSibling.classList.toggle('active');
    });
  });
});

const searchInput = document.getElementById('searchInput');
const clearBtn = document.getElementById('clearBtn');

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
  
  document.getElementById('searchStats').style.display = searchTerm.length > 0 ? 'block' : 'none';
  document.getElementById('foundCount').textContent = totalFound;
  document.getElementById('noResults').style.display = (searchTerm.length > 0 && !hasAnyVisible) ? 'block' : 'none';
}

function clearSearch() {
  searchInput.value = '';
  filterTables();
  searchInput.focus();
}

searchInput.addEventListener('input', filterTables);

function openMessengerModal(serviceName, price) {
  const text = `Здравствуйте! Хочу заказать: ${serviceName}${price ? ' (' + price + ')' : ''}`;
  const encoded = encodeURIComponent(text);
  
  document.getElementById('modalServiceName').textContent = price ? `${serviceName} (${price})` : serviceName;
  document.getElementById('tgLink').href = `https://t.me/alexdrog81?text=${encoded}`;
  document.getElementById('viberLink').href = `viber://chat?number=+375297256982&draft=${encoded}`;
  document.getElementById('waLink').href = `https://wa.me/375297256982?text=${encoded}`;
  document.getElementById('phoneLink').href = `tel:+375297256982`;
  
  document.getElementById('messengerModal').classList.add('active');
  document.body.style.overflow = 'hidden';
}

function closeMessengerModal(event) {
  if (!event || event.target.id === 'messengerModal' || event.target.tagName === 'BUTTON') {
    document.getElementById('messengerModal').classList.remove('active');
    document.body.style.overflow = '';
  }
}

document.addEventListener('keydown', e => {
  if (e.key === 'Escape') closeMessengerModal();
});
</script>
