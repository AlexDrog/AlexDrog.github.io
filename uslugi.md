---
layout: default
title: Услуги и цены
permalink: /uslugi/
---

<style>
/* --- Сетка карточек --- */
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.2rem;
  margin-bottom: 3rem;
}

.service-card {
  background: var(--bg, #ffffff);
  border: 1px solid var(--border, #e2e8f0);
  border-radius: 16px;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}

.service-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 24px rgba(0,0,0,0.1);
  border-color: var(--accent, #3b82f6);
}

/* Цветная полоска слева */
.service-card::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 4px;
  background: linear-gradient(to bottom, var(--primary), var(--secondary));
  opacity: 0;
  transition: opacity 0.3s;
}

.service-card:hover::before {
  opacity: 1;
}

.service-content h3 {
  margin: 0 0 0.8rem 0;
  font-size: 1.1rem;
  line-height: 1.4;
  color: var(--text);
}

.service-price {
  font-size: 1.5rem;
  color: #10b981;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.service-note {
  color: var(--text-muted, #64748b);
  font-size: 0.9rem;
  line-height: 1.4;
  margin-bottom: 1.5rem;
}

/* Кнопка Заказать */
.btn-order {
  width: 100%;
  padding: 0.8rem;
  background: linear-gradient(135deg, #3b82f6, #2563eb);
  color: white;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  margin-top: auto;
}

.btn-order:hover {
  transform: scale(1.02);
  box-shadow: 0 4px 12px rgba(59, 130, 246, 0.4);
}

.btn-order:active {
  transform: scale(0.98);
}

/* --- Модальное окно --- */
.modal {
  display: none;
  position: fixed;
  z-index: 1000;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.5);
  backdrop-filter: blur(4px);
}

.modal-content {
  background-color: var(--bg, #fff);
  margin: 10% auto;
  padding: 2rem;
  border-radius: 16px;
  width: 90%;
  max-width: 400px;
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
  text-align: center;
  animation: modalSlide 0.3s ease-out;
}

@keyframes modalSlide {
  from { transform: translateY(-50px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer;
  line-height: 1;
}

.close:hover {
  color: #000;
}

.modal h3 {
  margin-bottom: 1rem;
  color: var(--text);
}

.modal-service-name {
  color: var(--accent);
  font-weight: 600;
}

.modal-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 1.5rem;
}

.modal-btn {
  padding: 1rem;
  border-radius: 10px;
  text-decoration: none;
  color: white;
  font-weight: 600;
  transition: transform 0.2s;
}

.modal-btn:hover {
  transform: translateY(-2px);
}

.modal-btn.telegram {
  background: linear-gradient(135deg, #0088cc, #0099ff);
}

.modal-btn.phone {
  background: linear-gradient(135deg, #10b981, #059669);
}

/* --- Поиск --- */
.search-container {
  margin-bottom: 2rem;
  position: relative;
}

#searchInput {
  width: 100%;
  padding: 1rem;
  border: 2px solid var(--border);
  border-radius: 12px;
  font-size: 1rem;
  background: var(--bg);
  color: var(--text);
}

#clearBtn {
  position: absolute;
  right: 1rem;
  top: 50%;
  transform: translateY(-50%);
  background: #94a3b8;
  color: white;
  border: none;
  border-radius: 50%;
  width: 28px;
  height: 28px;
  cursor: pointer;
  display: none;
}

.no-results {
  text-align: center;
  padding: 3rem;
  color: var(--text-muted);
  display: none;
}

/* --- Адаптивность --- */
@media (max-width: 768px) {
  .services-grid {
    grid-template-columns: 1fr;
  }
  
  .service-card {
    padding: 1.2rem;
  }
  
  .modal-content {
    margin: 20% auto;
    width: 95%;
  }
}
</style>

# 📋 Прайс-лист

<!-- ПОИСК -->
<div class="search-container">
  <input type="text" id="searchInput" placeholder="🔍 Поиск услуги: Windows, замена экрана, FRP...">
  <button id="clearBtn" onclick="clearSearch()">✕</button>
</div>

<div class="no-results" id="noResults">
  <p>😕 Ничего не найдено</p>
  <p>Попробуйте: <b>ремонт</b>, <b>замена</b>, <b>Windows</b></p>
</div>

<!-- МОДАЛЬНОЕ ОКНО ЗАКАЗА -->
<div id="orderModal" class="modal">
  <div class="modal-content">
    <span class="close" onclick="closeModal()">&times;</span>
    <h3>Заказать услугу</h3>
    <p id="modalText" style="margin: 1rem 0; font-size: 1.1rem;"></p>
    <div class="modal-buttons">
      <a href="#" id="modalTelegram" class="modal-btn telegram" target="_blank">💬 Написать в Telegram</a>
      <a href="tel:+375297256982" class="modal-btn phone">📞 Позвонить</a>
    </div>
  </div>
</div>

<!-- КАТЕГОРИИ -->
{% assign sorted_prices = site.prices | sort: 'path' %}

{% for category in sorted_prices %}
<div class="category-section" id="{{ category.category_id | default: category.slug }}">
  <h2 style="margin: 2rem 0 1rem 0; scroll-margin-top: 100px;">{{ category.title }}</h2>
  
  <div class="services-grid">
    {% for service in category.services %}
    <div class="service-card" data-search="{{ service.name | downcase }} {{ service.note | downcase }}">
      <div class="service-content">
        <h3>{{ service.name }}</h3>
        <div class="service-price">{{ service.price }}</div>
        <div class="service-note">{{ service.note }}</div>
      </div>
      <button class="btn-order" onclick="openOrder('{{ service.name | escape }}', '{{ category.title | escape }}')">
        Заказать
      </button>
    </div>
    {% endfor %}
  </div>
</div>
{% endfor %}

{% if site.prices.size == 0 %}
<p style="text-align: center; padding: 2rem;">📝 Прайс-лист обновляется...</p>
{% endif %}

<div class="info-highlight" style="text-align: center; margin: 2rem 0; padding: 1.5rem; background: var(--bg-secondary); border-radius: 12px;">
  <strong>💡 Бесплатная диагностика — платишь только за ремонт!</strong>
</div>

<script>
// === ПОИСК ===
const searchInput = document.getElementById('searchInput');
const clearBtn = document.getElementById('clearBtn');
const noResults = document.getElementById('noResults');
const cards = document.querySelectorAll('.service-card');
const categories = document.querySelectorAll('.category-section');

function filterServices() {
  const term = searchInput.value.toLowerCase().trim();
  
  // Показать/скрыть кнопку очистки
  clearBtn.style.display = term ? 'block' : 'none';
  
  if (term === '') {
    // ОЧИСТКА: показываем всё
    cards.forEach(card => card.style.display = '');
    categories.forEach(cat => {
      cat.style.display = '';
      cat.querySelector('h2').style.display = '';
    });
    noResults.style.display = 'none';
    return;
  }
  
  let hasAnyResults = false;
  
  categories.forEach(category => {
    const categoryCards = category.querySelectorAll('.service-card');
    let hasVisibleCard = false;
    
    categoryCards.forEach(card => {
      const searchText = card.getAttribute('data-search');
      if (searchText.includes(term)) {
        card.style.display = '';
        hasVisibleCard = true;
        hasAnyResults = true;
      } else {
        card.style.display = 'none';
      }
    });
    
    // Скрываем категорию полностью если в ней нет совпадений
    if (!hasVisibleCard) {
      category.style.display = 'none';
    } else {
      category.style.display = '';
    }
  });
  
  noResults.style.display = hasAnyResults ? 'none' : 'block';
}

function clearSearch() {
  searchInput.value = '';
  filterServices();
  searchInput.focus();
}

searchInput.addEventListener('input', filterServices);

// === МОДАЛЬНОЕ ОКНО ===
const modal = document.getElementById('orderModal');
const modalText = document.getElementById('modalText');
const modalTelegram = document.getElementById('modalTelegram');

function openOrder(serviceName, categoryName) {
  modalText.innerHTML = `Вы выбрали: <br><span class="modal-service-name">${serviceName}</span>`;
  
  const message = `Здравствуйте! Хочу заказать: ${serviceName} (${categoryName})`;
  modalTelegram.href = `https://t.me/alexdrog81?text=${encodeURIComponent(message)}`;
  
  modal.style.display = 'block';
}

function closeModal() {
  modal.style.display = 'none';
}

// Закрыть при клике вне окна
window.onclick = function(event) {
  if (event.target == modal) {
    closeModal();
  }
}

// Закрыть по Escape
document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape') closeModal();
});
</script>
