---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

<style>
/* === TECH-HUMAN 2025 DESIGN SYSTEM === */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

:root {
  /* Цвета Tech-Human */
  --bg: #F7F5F3;
  --bg-warm: #F0EDE8;
  --card: #FFFFFF;
  --text: #1A1A1A;
  --text-secondary: #6B6B6B;
  --text-muted: #A3A3A3;
  --accent: #FF5722;        /* Терракотовый */
  --accent-hover: #E64A19;
  --secondary: #6366F1;     /* Индиго */
  --secondary-light: #818CF8;
  --border: #E5E2DE;
  --shadow: 0 20px 40px -15px rgba(0,0,0,0.08);
  --shadow-hover: 0 30px 60px -20px rgba(0,0,0,0.12);
  
  /* Типографика Big Typography */
  --font-main: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
  --text-base: clamp(0.9rem, 0.85rem + 0.25vw, 1rem);
  --text-lg: clamp(1.125rem, 1rem + 0.5vw, 1.25rem);
  --text-xl: clamp(1.5rem, 1.2rem + 1.5vw, 2.5rem);
  --text-2xl: clamp(2rem, 1.5rem + 2.5vw, 4rem);
  --text-hero: clamp(3rem, 8vw, 6rem); /* 48-96px */
}

/* Темная тема */
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #0F0F0F;
    --bg-warm: #1A1A1A;
    --card: #141414;
    --text: #F5F5F5;
    --text-secondary: #A3A3A3;
    --border: #2A2A2A;
    --accent: #FF7043;
  }
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-main);
  background-color: var(--bg);
  color: var(--text);
  line-height: 1.6;
  overflow-x: hidden;
}

/* === BIG TYPOGRAPHY === */
.page-header {
  padding: 4rem 1.5rem 2rem;
  position: relative;
  overflow: hidden;
}

.page-header h1 {
  font-size: var(--text-hero);
  font-weight: 800;
  line-height: 1;
  letter-spacing: -0.03em;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, var(--text) 0%, var(--text-secondary) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.page-header p {
  font-size: var(--text-lg);
  color: var(--text-secondary);
  max-width: 600px;
  font-weight: 400;
}

/* === ASYMMETRIC LAYOUT === */
.container-asymmetric {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.section-offset-left {
  margin-left: 0;
  margin-right: 5vw;
}

.section-offset-right {
  margin-left: 5vw;
  margin-right: 0;
}

.diagonal-break {
  height: 100px;
  background: linear-gradient(135deg, var(--bg) 50%, var(--bg-warm) 50%);
  margin: 2rem 0;
}

/* === BENTO GRID === */
.bento-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

@media (min-width: 768px) {
  .bento-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .bento-item-wide {
    grid-column: span 2;
  }
  
  .bento-item-tall {
    grid-row: span 2;
  }
}

@media (min-width: 1024px) {
  .bento-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
  }
}

/* === BENTO CARDS === */
.bento-card {
  background: var(--card);
  border-radius: 24px;
  padding: 2rem;
  border: 1px solid var(--border);
  box-shadow: var(--shadow);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.bento-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, var(--accent), var(--secondary));
  opacity: 0;
  transition: opacity 0.3s;
}

.bento-card:hover {
  transform: translateY(-8px) rotate(0.5deg);
  box-shadow: var(--shadow-hover);
}

.bento-card:hover::before {
  opacity: 1;
}

.bento-card.hidden {
  display: none !important;
}

.card-category {
  font-size: var(--text-xs);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--accent);
  font-weight: 700;
}

.card-title {
  font-size: var(--text-xl);
  font-weight: 700;
  line-height: 1.2;
  color: var(--text);
}

.card-price {
  font-size: var(--text-2xl);
  font-weight: 800;
  color: var(--accent);
  line-height: 1;
  margin: 0.5rem 0;
}

.card-note {
  font-size: var(--text-base);
  color: var(--text-secondary);
  flex-grow: 1;
}

/* === MICRO-INTERACTIONS (LIQUID BUTTONS) === */
.liquid-btn {
  position: relative;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 1rem 2rem;
  background: var(--text);
  color: var(--bg);
  border: none;
  border-radius: 100px;
  font-weight: 600;
  font-size: var(--text-base);
  cursor: pointer;
  overflow: hidden;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  text-decoration: none;
  isolation: isolate;
}

.liquid-btn::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: var(--accent);
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
  z-index: -1;
}

.liquid-btn:hover::before {
  width: 300%;
  height: 300%;
}

.liquid-btn:hover {
  color: white;
  transform: scale(1.05);
  box-shadow: 0 10px 30px -10px var(--accent);
}

.liquid-btn:active {
  transform: scale(0.95);
}

.liquid-btn-accent {
  background: var(--accent);
  color: white;
}

.liquid-btn-accent::before {
  background: var(--secondary);
}

/* Ripple effect */
.ripple {
  position: absolute;
  border-radius: 50%;
  background: rgba(255,255,255,0.4);
  transform: scale(0);
  animation: ripple-animation 0.6s ease-out;
  pointer-events: none;
}

@keyframes ripple-animation {
  to {
    transform: scale(4);
    opacity: 0;
  }
}

/* === SEARCH BENTO === */
.search-bento {
  background: var(--card);
  border-radius: 24px;
  padding: 1.5rem;
  margin: 2rem 0;
  border: 1px solid var(--border);
  box-shadow: var(--shadow);
  position: sticky;
  top: 20px;
  z-index: 50;
}

.search-input-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}

#searchInput {
  flex: 1;
  min-width: 200px;
  padding: 1rem 1.5rem;
  border: 2px solid var(--border);
  border-radius: 16px;
  font-size: var(--text-lg);
  font-family: inherit;
  background: var(--bg);
  color: var(--text);
  transition: all 0.3s;
}

#searchInput:focus {
  outline: none;
  border-color: var(--accent);
  box-shadow: 0 0 0 4px rgba(255,87,34,0.1);
}

#clearBtn {
  padding: 1rem 1.5rem;
  background: var(--bg-warm);
  border: none;
  border-radius: 12px;
  color: var(--text-secondary);
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  display: none;
}

#clearBtn:hover {
  background: var(--accent);
  color: white;
}

.search-stats {
  margin-top: 1rem;
  font-size: var(--text-base);
  color: var(--text-secondary);
  font-weight: 500;
}

/* === MODAL (LIQUID DESIGN) === */
.modal-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.4);
  backdrop-filter: blur(20px);
  z-index: 1000;
  align-items: flex-end;
  justify-content: center;
  padding: 0;
}

.modal-overlay.active {
  display: flex;
  animation: fadeIn 0.3s;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.modal-content {
  background: var(--card);
  width: 100%;
  max-width: 500px;
  border-radius: 32px 32px 0 0;
  padding: 2.5rem;
  transform: translateY(100%);
  animation: slideUp 0.4s cubic-bezier(0.4, 0, 0.2, 1) forwards;
  border: 1px solid var(--border);
  border-bottom: none;
}

@keyframes slideUp {
  to { transform: translateY(0); }
}

.modal-header {
  font-size: var(--text-2xl);
  font-weight: 800;
  margin-bottom: 0.5rem;
  color: var(--text);
}

.modal-service {
  font-size: var(--text-xl);
  color: var(--accent);
  font-weight: 700;
  margin-bottom: 2rem;
  padding: 1rem;
  background: var(--bg);
  border-radius: 16px;
  text-align: center;
}

.messenger-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.messenger-btn {
  padding: 1.25rem;
  border-radius: 20px;
  border: 2px solid var(--border);
  background: var(--bg);
  color: var(--text);
  font-weight: 600;
  font-size: var(--text-base);
  cursor: pointer;
  transition: all 0.3s;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none;
}

.messenger-btn:hover {
  border-color: var(--accent);
  background: var(--accent);
  color: white;
  transform: translateY(-4px);
  box-shadow: 0 12px 24px -8px rgba(255,87,34,0.3);
}

.messenger-btn span:first-child {
  font-size: 1.5rem;
}

.btn-cancel-full {
  grid-column: span 2;
  margin-top: 0.5rem;
  background: transparent;
  color: var(--text-muted);
}

.btn-cancel-full:hover {
  background: var(--bg-warm);
  color: var(--text);
}

/* === FLOATING CTA === */
.floating-cta {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  z-index: 100;
}

.floating-btn {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background: var(--accent);
  color: white;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  box-shadow: 0 10px 30px -5px rgba(255,87,34,0.4);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  display: flex;
  align-items: center;
  justify-content: center;
}

.floating-btn:hover {
  transform: scale(1.1) rotate(10deg);
  box-shadow: 0 20px 40px -10px rgba(255,87,34,0.5);
}

/* === ASYMMETRIC SECTIONS === */
.section-header {
  padding: 3rem 0 1.5rem;
  position: relative;
}

.section-header h2 {
  font-size: var(--text-2xl);
  font-weight: 800;
  transform: rotate(-1deg);
  display: inline-block;
  background: var(--card);
  padding: 0.5rem 1.5rem;
  border-radius: 16px;
  box-shadow: var(--shadow);
  border: 1px solid var(--border);
}

.section-header:nth-child(even) h2 {
  transform: rotate(1deg);
  margin-left: 10%;
}

/* === MOBILE OPTIMIZATIONS === */
@media (max-width: 768px) {
  .bento-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  
  .bento-card {
    padding: 1.5rem;
    border-radius: 20px;
  }
  
  .section-offset-left,
  .section-offset-right {
    margin: 0;
  }
  
  .page-header {
    padding: 2rem 1rem 1rem;
  }
  
  .floating-cta {
    bottom: 1rem;
    right: 1rem;
  }
  
  .floating-btn {
    width: 56px;
    height: 56px;
  }
  
  .modal-content {
    padding: 1.5rem;
    border-radius: 24px 24px 0 0;
  }
  
  .messenger-grid {
    grid-template-columns: 1fr;
  }
  
  .messenger-btn {
    flex-direction: row;
    justify-content: center;
  }
  
  .btn-cancel-full {
    grid-column: span 1;
  }
}

/* === UTILITY === */
.no-results-bento {
  grid-column: 1 / -1;
  text-align: center;
  padding: 3rem;
  color: var(--text-secondary);
  font-size: var(--text-lg);
  background: var(--card);
  border-radius: 24px;
  border: 2px dashed var(--border);
}
</style>

<!-- HERO SECTION -->
<div class="page-header">
  <div class="container-asymmetric">
    <h1>Прайс-лист</h1>
    <p>Ремонт смартфонов и ноутбуков в Дрогичине. Честные цены, гарантия качества.</p>
  </div>
</div>

<div class="diagonal-break"></div>

<!-- SEARCH BENTO -->
<div class="container-asymmetric section-offset-left">
  <div class="search-bento">
    <div class="search-input-wrapper">
      <input type="text" id="searchInput" placeholder="Поиск услуги..." autocomplete="off">
      <button id="clearBtn" onclick="clearSearch()">Очистить</button>
    </div>
    <div class="search-stats" id="searchStats" style="display: none;">
      Найдено: <strong id="foundCount">0</strong> услуг
    </div>
  </div>
</div>

<!-- SERVICES BENTO GRID -->
<div class="container-asymmetric section-offset-right">
  <div class="bento-grid" id="servicesGrid">
    {% assign sorted_prices = site.prices | sort: 'path' %}
    
    {% for category in sorted_prices %}
      {% for service in category.services %}
      <div class="bento-card service-card" 
           data-category="{{ category.title }}"
           data-name="{{ service.name | downcase }}"
           data-note="{{ service.note | downcase }}">
        
        <div class="card-category">{{ category.title }}</div>
        <h3 class="card-title">{{ service.name }}</h3>
        <div class="card-price">{{ service.price }}</div>
        <p class="card-note">{{ service.note }}</p>
        
        <button class="liquid-btn liquid-btn-accent" onclick="openOrderModal('{{ service.name }}', '{{ service.price }}', event)">
          Заказать →
        </button>
      </div>
      {% endfor %}
    {% endfor %}
    
    <div class="no-results-bento" id="noResults" style="display: none;">
      😕 Ничего не найдено<br>
      <small>Попробуйте: замена, экран, батарея</small>
    </div>
  </div>
</div>

<!-- FLOATING CTA -->
<div class="floating-cta">
  <button class="floating-btn" onclick="location.href='tel:+375297256982'" aria-label="Позвонить">
    📞
  </button>
</div>

<!-- ORDER MODAL -->
<div id="orderModal" class="modal-overlay" onclick="closeModal(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <div class="modal-header">Выберите способ связи</div>
    <div class="modal-service" id="modalService">Услуга</div>
    
    <div class="messenger-grid">
      <a href="#" id="linkTG" class="messenger-btn" target="_blank">
        <span>✈️</span>
        <span>Telegram</span>
      </a>
      <a href="#" id="linkVB" class="messenger-btn" target="_blank">
        <span>📞</span>
        <span>Viber</span>
      </a>
      <a href="#" id="linkWA" class="messenger-btn" target="_blank">
        <span>💬</span>
        <span>WhatsApp</span>
      </a>
      <a href="#" id="linkPhone" class="messenger-btn">
        <span>📱</span>
        <span>Позвонить</span>
      </a>
      <button onclick="closeModal()" class="messenger-btn btn-cancel-full">
        Отмена
      </button>
    </div>
  </div>
</div>

<script>
// Search functionality
const searchInput = document.getElementById('searchInput');
const clearBtn = document.getElementById('clearBtn');
const cards = document.querySelectorAll('.service-card');
const noResults = document.getElementById('noResults');
const searchStats = document.getElementById('searchStats');
const foundCount = document.getElementById('foundCount');

function filterServices() {
  const term = searchInput.value.toLowerCase().trim();
  let count = 0;
  
  clearBtn.style.display = term ? 'flex' : 'none';
  
  cards.forEach(card => {
    const name = card.getAttribute('data-name');
    const note = card.getAttribute('data-note');
    const match = name.includes(term) || note.includes(term);
    
    if (term === '' || match) {
      card.style.display = 'flex';
      if (term) count++;
    } else {
      card.style.display = 'none';
    }
  });
  
  if (term) {
    searchStats.style.display = 'block';
    foundCount.textContent = count;
    noResults.style.display = count === 0 ? 'block' : 'none';
  } else {
    searchStats.style.display = 'none';
    noResults.style.display = 'none';
  }
}

function clearSearch() {
  searchInput.value = '';
  filterServices();
  searchInput.focus();
}

searchInput.addEventListener('input', filterServices);

// Liquid button ripple effect
function createRipple(event) {
  const button = event.currentTarget;
  const ripple = document.createElement('span');
  const rect = button.getBoundingClientRect();
  const size = Math.max(rect.width, rect.height);
  const x = event.clientX - rect.left - size / 2;
  const y = event.clientY - rect.top - size / 2;
  
  ripple.style.width = ripple.style.height = size + 'px';
  ripple.style.left = x + 'px';
  ripple.style.top = y + 'px';
  ripple.classList.add('ripple');
  
  button.appendChild(ripple);
  
  setTimeout(() => ripple.remove(), 600);
}

document.querySelectorAll('.liquid-btn').forEach(btn => {
  btn.addEventListener('click', createRipple);
});

// Modal functionality
function openOrderModal(service, price, event) {
  if (event) createRipple(event);
  
  const modal = document.getElementById('orderModal');
  const serviceDiv = document.getElementById('modalService');
  
  serviceDiv.textContent = price ? `${service} — ${price}` : service;
  
  const text = `Здравствуйте! Хочу заказать: ${service}${price ? ' (' + price + ')' : ''}`;
  const encoded = encodeURIComponent(text);
  
  document.getElementById('linkTG').href = `https://t.me/alexdrog81?text=${encoded}`;
  document.getElementById('linkVB').href = `viber://chat?number=+375297256982&draft=${encoded}`;
  document.getElementById('linkWA').href = `https://wa.me/375297256982?text=${encoded}`;
  document.getElementById('linkPhone').href = `tel:+375297256982`;
  
  modal.classList.add('active');
  document.body.style.overflow = 'hidden';
}

function closeModal(event) {
  if (!event || event.target.id === 'orderModal' || event.target.tagName === 'BUTTON') {
    document.getElementById('orderModal').classList.remove('active');
    document.body.style.overflow = '';
  }
}

// Close on escape
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') closeModal();
});

// Swipe to close on mobile
let touchStartY = 0;
const modalContent = document.querySelector('.modal-content');
if (modalContent) {
  modalContent.addEventListener('touchstart', e => {
    touchStartY = e.touches[0].clientY;
  });
  modalContent.addEventListener('touchend', e => {
    if (e.changedTouches[0].clientY - touchStartY > 100) {
      closeModal();
    }
  });
}
</script>
