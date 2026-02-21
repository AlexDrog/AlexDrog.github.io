---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

<script>
  // === ТЕМА: Синхронизация с главной страницей ===
  (function() {
    const saved = sessionStorage.getItem('theme');
    const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
    const theme = saved || (prefersDark ? 'dark' : 'light');
    document.documentElement.setAttribute('data-theme', theme);
  })();

  window.toggleTheme = function() {
    const current = document.documentElement.getAttribute('data-theme');
    const next = current === 'dark' ? 'light' : 'dark';
    document.documentElement.setAttribute('data-theme', next);
    sessionStorage.setItem('theme', next);
    const btn = document.getElementById('theme-toggle');
    if (btn) btn.textContent = next === 'dark' ? '☀️' : '🌙';
  };
</script>

<style>
/* === ТЕМНАЯ ТЕМА === */
:root,
html {
  --bg: #f8fafc;
  --bg-card: #ffffff;
  --bg-secondary: #f1f5f9;
  --bg-hover: #e2e8f0;
  --text: #334155;
  --text-secondary: #64748b;
  --text-muted: #94a3b8;
  --border: #e2e8f0;
  --accent: #3b82f6;
  --accent-hover: #2563eb;
  --shadow: rgba(0,0,0,0.04);
  --success: #10b981;
  --error-bg: #fee2e2;
  --error-text: #991b1b;
  --gradient-start: #3b82f6;
  --gradient-end: #6366f1;
}

html[data-theme="dark"] {
  --bg: #0f172a;
  --bg-card: #1e293b;
  --bg-secondary: #334155;
  --bg-hover: #475569;
  --text: #e2e8f0;
  --text-secondary: #94a3b8;
  --text-muted: #64748b;
  --border: #334155;
  --accent: #60a5fa;
  --accent-hover: #3b82f6;
  --shadow: rgba(0,0,0,0.2);
  --success: #34d399;
  --error-bg: #450a0a;
  --error-text: #fca5a5;
  --gradient-start: #2563eb;
  --gradient-end: #4f46e5;
}

body {
  background-color: var(--bg);
  color: var(--text);
  line-height: 1.5;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  transition: background-color 0.3s, color 0.3s;
}

/* === КНОПКА ТЕМЫ === */
#theme-toggle {
  position: fixed;
  top: 15px;
  right: 15px;
  z-index: 9999;
  background: var(--bg-card);
  color: var(--text);
  border: 1px solid var(--border);
  border-radius: 50%;
  width: 48px;
  height: 48px;
  font-size: 20px;
  cursor: pointer;
  box-shadow: 0 4px 12px var(--shadow);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.2s;
}

#theme-toggle:hover {
  transform: scale(1.1);
}

/* === КНОПКА НА ГЛАВНУЮ === */
.nav-back {
  margin-bottom: 1.5rem;
}

.btn-back {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  background: var(--bg-card);
  color: var(--text) !important;
  border: 1px solid var(--border);
  border-radius: 50px;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  box-shadow: 0 2px 8px var(--shadow);
  transition: all 0.2s;
}

.btn-back:hover {
  background: var(--bg-secondary);
  transform: translateX(-4px);
  border-color: var(--accent);
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
}

.category-nav a {
  padding: 0.5rem 1rem;
  background: var(--bg-secondary);
  border-radius: 50px;
  text-decoration: none;
  font-size: 0.85rem;
  color: var(--text);
  font-weight: 500;
  border: 1px solid var(--border);
  transition: all 0.2s;
}

.category-nav a:hover {
  background: var(--accent);
  color: white;
  border-color: var(--accent);
  transform: translateY(-2px);
}

/* === АККОРДЕОН === */
.category-accordion {
  margin-bottom: 1rem;
  border-radius: 16px;
  overflow: hidden;
  background: var(--bg-card);
  border: 1px solid var(--border);
  box-shadow: 0 2px 8px var(--shadow);
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
  background: var(--bg-card);
}

.category-content.active {
  display: block;
}

/* === ТАБЛИЦА === */
.price-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.95rem;
}

.price-table th {
  background: var(--bg-secondary);
  padding: 0.75rem 1rem;
  text-align: left;
  font-weight: 600;
  color: var(--text-secondary);
  border-bottom: 1px solid var(--border);
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.price-table td {
  padding: 1rem;
  border-bottom: 1px solid var(--border);
  color: var(--text);
}

.price-table tbody tr:hover {
  background: var(--bg-hover);
}

.price-table tbody tr:last-child td {
  border-bottom: none;
}

/* === УСЛУГА === */
.service-name {
  color: var(--accent);
  cursor: pointer;
  font-weight: 600;
  text-decoration: none;
  transition: opacity 0.2s;
}

.service-name:hover {
  opacity: 0.8;
}

td strong {
  color: var(--accent);
  font-weight: 700;
  white-space: nowrap;
}

td:last-child {
  color: var(--text-secondary);
  font-size: 0.9rem;
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
  margin-bottom: 0.5rem;
}

.search-wrapper {
  position: relative;
}

#searchInput {
  width: 100%;
  padding: 0.75rem 2.5rem 0.75rem 1rem;
  border: 2px solid var(--border);
  border-radius: 12px;
  font-size: 16px;
  background: var(--bg);
  color: var(--text);
  font-family: inherit;
}

#searchInput:focus {
  outline: none;
  border-color: var(--accent);
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
  width: 28px;
  height: 28px;
  cursor: pointer;
  font-size: 14px;
  display: none;
  align-items: center;
  justify-content: center;
}

.search-stats {
  margin-top: 0.5rem;
  color: var(--text-secondary);
  font-size: 0.9rem;
}

.no-results {
  margin-top: 1rem;
  padding: 1rem;
  background: var(--error-bg);
  border-radius: 8px;
  color: var(--error-text);
  text-align: center;
  display: none;
}

/* === МОДАЛЬНОЕ ОКНО === */
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
  padding: 2rem;
  border-radius: 24px 24px 0 0;
  width: 100%;
  max-width: 500px;
  border: 1px solid var(--border);
  border-bottom: none;
}

.messenger-title {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--text);
  text-align: center;
}

.messenger-service {
  color: var(--accent);
  font-weight: 600;
  margin-bottom: 1.5rem;
  padding: 0.75rem;
  background: var(--bg-secondary);
  border-radius: 12px;
  text-align: center;
}

.messenger-buttons {
  display: grid;
  gap: 0.75rem;
}

.messenger-btn {
  padding: 1rem;
  border-radius: 12px;
  text-align: center;
  text-decoration: none;
  font-weight: 600;
  color: white;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  transition: transform 0.1s;
}

.messenger-btn:active {
  transform: scale(0.98);
}

.btn-tg { background: #0088cc; }
.btn-viber { background: #665cac; }
.btn-whatsapp { background: #25d366; }
.btn-phone { background: var(--success); }
.btn-cancel {
  background: var(--bg-secondary);
  color: var(--text);
  border: 1px solid var(--border);
}

/* === АДАПТИВНОСТЬ === */
@media (max-width: 768px) {
  #theme-toggle {
    width: 44px;
    height: 44px;
    font-size: 18px;
    top: 10px;
    right: 10px;
  }
  
  .messenger-modal {
    align-items: flex-end;
  }
}

@media (min-width: 768px) {
  .messenger-modal {
    align-items: center;
    padding: 1rem;
  }
  
  .messenger-content {
    border-radius: 24px;
    max-width: 400px;
  }
}

@media (max-width: 480px) {
  .price-table {
    font-size: 0.9rem;
  }
  
  .price-table td {
    padding: 0.75rem;
  }
  
  .category-header {
    padding: 0.875rem 1rem;
  }
  
  .nav-back {
    margin-bottom: 1rem;
  }
  
  .btn-back {
    width: 100%;
    justify-content: center;
  }
}
</style>

<!-- КНОПКА ТЕМЫ -->
<button onclick="toggleTheme()" id="theme-toggle">🌙</button>

<!-- КНОПКА НА ГЛАВНУЮ -->
<div class="nav-back">
  <a href="{{ '/' | relative_url }}" class="btn-back">← На главную</a>
</div>

# 📋 Прайс-лист

{% assign sorted_prices = site.prices | sort: 'path' %}
{% assign visible_categories = sorted_prices | where_exp: "item", "item.hidden != true" %}

<div class="category-nav">
  {% for category in visible_categories %}
    <a href="#cat-{{ forloop.index }}">{{ category.title }}</a>
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
    ❌ Ничего не найдено. Попробуйте: <b>ремонт</b>, <b>замена</b>, <b>Windows</b>
  </div>
</div>

{% for category in visible_categories %}
<div class="category-accordion" data-category="{{ category.title | downcase }}">
  <button class="category-header" id="cat-{{ forloop.index }}" type="button">
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
        {% unless service.hidden == true %}
        <tr data-name="{{ service.name | downcase }}">
          <td>
            <span class="service-name" onclick="openModal('{{ service.name }}', '{{ service.price }}')">
              {{ service.name }}
            </span>
          </td>
          <td><strong>{{ service.price }}</strong></td>
          <td>{{ service.note }}</td>
        </tr>
        {% endunless %}
        {% endfor %}
      </tbody>
    </table>
  </div>
</div>
{% endfor %}

<div id="orderModal" class="messenger-modal" onclick="closeModal(event)">
  <div class="messenger-content" onclick="event.stopPropagation()">
    <div class="messenger-title">Выберите способ связи</div>
    <div class="messenger-service" id="modalService">Услуга</div>
    
    <div class="messenger-buttons">
      <a href="#" id="linkTG" class="messenger-btn btn-tg" target="_blank">Telegram</a>
      <a href="#" id="linkVB" class="messenger-btn btn-viber" target="_blank">Viber</a>
      <a href="#" id="linkWA" class="messenger-btn btn-whatsapp" target="_blank">WhatsApp</a>
      <a href="#" id="linkPhone" class="messenger-btn btn-phone">Позвонить</a>
      <button onclick="closeModal()" class="messenger-btn btn-cancel">Отмена</button>
    </div>
  </div>
</div>

<script>
// Инициализация темы при загрузке
document.addEventListener('DOMContentLoaded', function() {
  const btn = document.getElementById('theme-toggle');
  const current = document.documentElement.getAttribute('data-theme');
  if (btn) btn.textContent = current === 'dark' ? '☀️' : '🌙';
});

// Аккордеон
document.querySelectorAll('.category-header').forEach(btn => {
  btn.addEventListener('click', () => {
    btn.classList.toggle('active');
    btn.nextElementSibling.classList.toggle('active');
  });
});

// Поиск
const searchInput = document.getElementById('searchInput');
const clearBtn = document.getElementById('clearBtn');

function filter() {
  const term = searchInput.value.toLowerCase();
  const accordions = document.querySelectorAll('.category-accordion');
  let count = 0;
  
  clearBtn.style.display = term ? 'flex' : 'none';
  
  accordions.forEach(acc => {
    const rows = acc.querySelectorAll('tbody tr');
    const content = acc.querySelector('.category-content');
    const header = acc.querySelector('.category-header');
    let hasMatch = false;
    
    rows.forEach(row => {
      const name = row.getAttribute('data-name');
      if (name.includes(term)) {
        row.style.display = '';
        if (term) { hasMatch = true; count++; }
      } else {
        row.style.display = term ? 'none' : '';
      }
    });
    
    if (term) {
      if (hasMatch) {
        acc.classList.remove('hidden');
        header.classList.add('active');
        content.classList.add('active');
      } else {
        acc.classList.add('hidden');
      }
    } else {
      acc.classList.remove('hidden');
      header.classList.remove('active');
      content.classList.remove('active');
    }
  });
  
  document.getElementById('searchStats').style.display = term ? 'block' : 'none';
  document.getElementById('foundCount').textContent = count;
  document.getElementById('noResults').style.display = (term && count === 0) ? 'block' : 'none';
}

function clearSearch() {
  searchInput.value = '';
  filter();
  searchInput.focus();
}

searchInput.addEventListener('input', filter);

// Модальное окно
function openModal(service, price) {
  const text = `Здравствуйте! Хочу заказать: ${service}${price ? ' ('+price+')' : ''}`;
  document.getElementById('modalService').textContent = price ? `${service} — ${price}` : service;
  document.getElementById('linkTG').href = `https://t.me/alexdrog81?text=${encodeURIComponent(text)}`;
  document.getElementById('linkVB').href = `viber://chat?number=+375297256982&draft=${encodeURIComponent(text)}`;
  document.getElementById('linkWA').href = `https://wa.me/375297256982?text=${encodeURIComponent(text)}`;
  document.getElementById('linkPhone').href = `tel:+375297256982`;
  document.getElementById('orderModal').classList.add('active');
  document.body.style.overflow = 'hidden';
}

function closeModal(e) {
  if (!e || e.target.id === 'orderModal') {
    document.getElementById('orderModal').classList.remove('active');
    document.body.style.overflow = '';
  }
}

document.addEventListener('keydown', e => {
  if (e.key === 'Escape') closeModal();
});
</script>
