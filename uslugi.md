---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

<style>
/* === Tech-Human 2025 — исправленная версия === */
:root {
  --bg: #F7F5F3;
  --card: #FFFFFF;
  --text: #2C2C2C;
  --text-secondary: #6B6B6B;
  --accent: #E85D04;        /* Терракотовый мягкий */
  --accent-light: #F48C06;
  --border: #E8E4E1;
  --shadow: 0 4px 20px rgba(0,0,0,0.06);
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg: #1A1A1A;
    --card: #242424;
    --text: #F5F5F0;
    --text-secondary: #A0A0A0;
    --accent: #FF7B54;
    --border: #333333;
  }
}

/* Навигация — компактные капсулы */
.category-nav {
  position: sticky;
  top: 80px;
  background: var(--card);
  padding: 1rem;
  border-radius: 16px;
  margin-bottom: 1.5rem;
  box-shadow: var(--shadow);
  z-index: 100;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  justify-content: center;
  border: 1px solid var(--border);
}

.category-nav a {
  padding: 0.5rem 1rem;
  background: var(--bg);
  border-radius: 50px;
  text-decoration: none;
  font-size: 0.85rem;
  color: var(--text-secondary);
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

/* Аккордеон */
.category-accordion {
  margin-bottom: 1rem;
  border-radius: 16px;
  overflow: hidden;
  background: var(--card);
  border: 1px solid var(--border);
  box-shadow: var(--shadow);
}

.category-header {
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
  color: white;
  padding: 1rem 1.25rem;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 600;
  font-size: 1.05rem;
  border: none;
  width: 100%;
  text-align: left;
}

.category-header .arrow {
  transition: transform 0.3s;
}

.category-header.active .arrow {
  transform: rotate(180deg);
}

.category-content {
  display: none;
  background: var(--card);
}

.category-content.active {
  display: block;
}

/* Таблица — компактная, без черноты */
.price-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.95rem;
}

.price-table th {
  background: var(--bg);
  padding: 0.75rem;
  text-align: left;
  font-weight: 600;
  color: var(--text-secondary);
  border-bottom: 1px solid var(--border);
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.price-table td {
  padding: 0.875rem 0.75rem;
  border-bottom: 1px solid var(--border);
  color: var(--text);
}

.price-table tbody tr:hover {
  background: var(--bg);
}

/* Услуга — жидкая кнопка */
.service-name {
  color: var(--accent);
  font-weight: 600;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.25rem 0.75rem;
  margin: -0.25rem -0.75rem;
  border-radius: 8px;
  transition: all 0.2s;
}

.service-name:hover {
  background: rgba(232, 93, 4, 0.1);
}

.service-name::after {
  content: "→";
  opacity: 0;
  transform: translateX(-4px);
  transition: all 0.2s;
}

.service-name:hover::after {
  opacity: 1;
  transform: translateX(0);
}

/* Цена */
td strong {
  color: var(--accent);
  font-weight: 700;
}

/* Поиск — мягкий */
.search-container {
  margin-bottom: 1.5rem;
  background: var(--card);
  padding: 1.25rem;
  border-radius: 16px;
  border: 1px solid var(--border);
  box-shadow: var(--shadow);
}

.search-container label {
  display: block;
  color: var(--text-secondary);
  font-weight: 600;
  margin-bottom: 0.5rem;
  font-size: 0.9rem;
}

#searchInput {
  width: 100%;
  padding: 0.75rem 1rem;
  border: 1px solid var(--border);
  border-radius: 12px;
  font-size: 16px;
  background: var(--bg);
  color: var(--text);
}

#searchInput:focus {
  outline: none;
  border-color: var(--accent);
}

#clearBtn {
  display: none;
  margin-top: 0.5rem;
  padding: 0.5rem 1rem;
  background: var(--text-secondary);
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

/* Модальное окно — снизу */
.modal-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
  align-items: flex-end;
  justify-content: center;
}

.modal-overlay.active {
  display: flex;
}

.modal-content {
  background: var(--card);
  width: 100%;
  max-width: 400px;
  border-radius: 24px 24px 0 0;
  padding: 2rem;
  border: 1px solid var(--border);
  animation: slideUp 0.3s;
}

@keyframes slideUp {
  from { transform: translateY(100%); }
  to { transform: translateY(0); }
}

.messenger-btn {
  display: block;
  width: 100%;
  padding: 1rem;
  margin-bottom: 0.5rem;
  border-radius: 12px;
  text-align: center;
  text-decoration: none;
  font-weight: 600;
  color: white;
  border: none;
  cursor: pointer;
  transition: transform 0.1s;
}

.messenger-btn:active {
  transform: scale(0.98);
}

.btn-tg { background: #0088cc; }
.btn-viber { background: #665cac; }
.btn-wa { background: #25d366; }
.btn-phone { background: var(--accent); }
.btn-cancel {
  background: var(--bg);
  color: var(--text-secondary);
  border: 1px solid var(--border);
}

.hidden { display: none !important; }
</style>

# 📋 Прайс-лист

<div class="category-nav">
  {% assign sorted_prices = site.prices | sort: 'path' %}
  {% for category in sorted_prices %}
    <a href="#cat-{{ forloop.index }}">{{ category.title }}</a>
  {% endfor %}
</div>

<div class="search-container">
  <label>🔍 Поиск услуги</label>
  <input type="text" id="searchInput" placeholder="Например: замена экрана..." autocomplete="off">
  <button id="clearBtn" onclick="clearSearch()">Очистить</button>
  <div id="searchStats" style="margin-top:0.5rem;color:var(--text-secondary);display:none;">
    Найдено: <span id="foundCount">0</span>
  </div>
</div>

{% assign sorted_prices = site.prices | sort: 'path' %}

{% for category in sorted_prices %}
<div class="category-accordion" data-category="{{ category.title | downcase }}">
  <button class="category-header" id="cat-{{ forloop.index }}">
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
        <tr data-name="{{ service.name | downcase }}">
          <td>
            <span class="service-name" onclick="openModal('{{ service.name }}', '{{ service.price }}')">
              {{ service.name }}
            </span>
          </td>
          <td><strong>{{ service.price }}</strong></td>
          <td style="color:var(--text-secondary);font-size:0.9rem;">{{ service.note }}</td>
        </tr>
        {% endfor %}
      </tbody>
    </table>
  </div>
</div>
{% endfor %}

<!-- Модалка -->
<div id="orderModal" class="modal-overlay" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <h3 style="margin-bottom:0.5rem;color:var(--text);">Заказать</h3>
    <p id="modalService" style="margin-bottom:1.5rem;color:var(--accent);font-weight:600;"></p>
    
    <a href="#" id="tgLink" class="messenger-btn btn-tg" target="_blank">Telegram</a>
    <a href="#" id="viberLink" class="messenger-btn btn-viber" target="_blank">Viber</a>
    <a href="#" id="waLink" class="messenger-btn btn-wa" target="_blank">WhatsApp</a>
    <a href="#" id="phoneLink" class="messenger-btn btn-phone">Позвонить</a>
    <button onclick="closeModal()" class="messenger-btn btn-cancel">Отмена</button>
  </div>
</div>

<script>
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
  
  clearBtn.style.display = term ? 'block' : 'none';
  
  accordions.forEach(acc => {
    const rows = acc.querySelectorAll('tbody tr');
    const content = acc.querySelector('.category-content');
    const header = acc.querySelector('.category-header');
    let hasMatch = false;
    
    rows.forEach(row => {
      const name = row.getAttribute('data-name');
      if (name.includes(term)) {
        row.style.display = '';
        if (term) {
          hasMatch = true;
          count++;
        }
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
}

function clearSearch() {
  searchInput.value = '';
  filter();
}

searchInput.addEventListener('input', filter);

// Модалка
function openModal(name, price) {
  const text = `Здравствуйте! Хочу заказать: ${name}${price ? ' ('+price+')' : ''}`;
  document.getElementById('modalService').textContent = price ? `${name} — ${price}` : name;
  document.getElementById('tgLink').href = `https://t.me/alexdrog81?text=${encodeURIComponent(text)}`;
  document.getElementById('viberLink').href = `viber://chat?number=+375297256982&draft=${encodeURIComponent(text)}`;
  document.getElementById('waLink').href = `https://wa.me/375297256982?text=${encodeURIComponent(text)}`;
  document.getElementById('phoneLink').href = `tel:+375297256982`;
  document.getElementById('orderModal').classList.add('active');
}

function closeModal(e) {
  if (!e || e.target.id === 'orderModal') {
    document.getElementById('orderModal').classList.remove('active');
  }
}
</script>
