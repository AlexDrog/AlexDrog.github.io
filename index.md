---
layout: default
---

<script>
  // === ТЕМА: При открытии — системная, при переключении — временно ===
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
  /* === СИНХРОНИЗАЦИЯ С ЦВЕТАМИ УСЛУГ === */
  :root {
    --bg: #f8fafc;
    --bg-card: #ffffff;
    --bg-secondary: #f1f5f9;
    --text: #334155;
    --text-secondary: #64748b;
    --heading: #0f172a;
    --border: #e2e8f0;
    --accent: #3b82f6;
    --accent-hover: #2563eb;
    --success: #10b981;
    --shadow: rgba(0,0,0,0.04);
    --gradient-start: #3b82f6;
    --gradient-end: #6366f1;
  }
  
  [data-theme="dark"] {
    --bg: #0f172a;
    --bg-card: #1e293b;
    --bg-secondary: #334155;
    --text: #e2e8f0;
    --text-secondary: #94a3b8;
    --heading: #f8fafc;
    --border: #334155;
    --accent: #60a5fa;
    --accent-hover: #3b82f6;
    --success: #34d399;
    --shadow: rgba(0,0,0,0.2);
    --gradient-start: #2563eb;
    --gradient-end: #4f46e5;
  }
  
  body { 
    background-color: var(--bg) !important; 
    color: var(--text) !important;
    transition: background-color 0.3s, color 0.3s;
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  }
  
  h1, h2, h3 { 
    color: var(--heading) !important; 
    border-color: var(--border) !important; 
    line-height: 1.3;
  }
  
  a { color: var(--accent) !important; }
  
  .btn {
    display: inline-block;
    padding: 14px 28px;
    margin: 5px;
    background: linear-gradient(135deg, var(--gradient-start) 0%, var(--gradient-end) 100%) !important;
    color: #ffffff !important;
    border-radius: 12px;
    text-decoration: none;
    font-weight: 600;
    box-shadow: 0 4px 12px rgba(59, 130, 246, 0.3);
    transition: transform 0.2s, box-shadow 0.2s;
    border: none;
    cursor: pointer;
    font-size: 1rem;
  }
  
  .btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 16px rgba(59, 130, 246, 0.4);
  }
  
  .btn-large {
    display: block;
    width: 100%;
    max-width: 600px;
    margin: 2rem auto;
    text-align: center;
    font-size: 1.1rem;
    padding: 16px 24px;
  }
  
  details {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 16px;
    margin-bottom: 16px;
    box-shadow: 0 2px 8px var(--shadow);
    transition: border-color 0.3s, box-shadow 0.3s;
  }
  
  details.pinned {
    border: 2px solid var(--accent);
    box-shadow: 0 4px 16px rgba(59, 130, 246, 0.15);
    background: linear-gradient(135deg, var(--bg-card) 0%, rgba(59, 130, 246, 0.05) 100%);
  }
  
  [data-theme="dark"] details.pinned {
    background: linear-gradient(135deg, var(--bg-card) 0%, rgba(96, 165, 250, 0.1) 100%);
  }
  
  .pinned-badge {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    background: var(--accent);
    color: white !important;
    padding: 4px 8px;
    border-radius: 50%;
    font-size: 0.9rem;
    margin-right: 8px;
    vertical-align: middle;
    width: 24px;
    height: 24px;
    line-height: 1;
  }
  
  summary { 
    color: var(--heading); 
    font-weight: 600; 
    cursor: pointer; 
    list-style: none;
  }
  summary::-webkit-details-marker { display: none; }
  summary h3 { display: inline; margin: 0; }
  
  .gallery-grid { 
    display: grid; 
    grid-template-columns: 1fr 1fr; 
    gap: 15px; 
    margin-top: 15px; 
  }
  .gallery-item { 
    text-align: center; 
    background: var(--bg); 
    border-radius: 8px; 
    overflow: hidden; 
    border: 1px solid var(--border);
  }
  .label-red { 
    background: #ef4444; 
    color: white; 
    padding: 8px; 
    font-weight: bold; 
    font-size: 0.9rem;
  }
  .label-green { 
    background: var(--success); 
    color: white; 
    padding: 8px; 
    font-weight: bold; 
    font-size: 0.9rem;
  }
  
  .gallery-item img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    display: block;
    cursor: pointer;
    transition: transform 0.2s;
  }
  
  .gallery-item img:hover { transform: scale(1.02); }
  
  .highlight { 
    color: #ef4444; 
    font-weight: bold; 
    background: transparent !important;
  }
  
  [data-theme="dark"] .highlight {
    color: #f87171;
    background: transparent !important;
  }
  
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
  
  .photos-row { 
    display: grid; 
    grid-template-columns: 1fr 1fr; 
    gap: 25px; 
    margin: 1.5rem 0; 
    align-items: start; 
  }
  
  .chat-container { width: 100%; }
  
  .chat-details { 
    background: var(--bg-card); 
    border: 1px solid var(--border); 
    border-radius: 30px; 
    overflow: hidden;
    box-shadow: 0 2px 8px var(--shadow);
  }
  
  .chat-summary { 
    display: flex; 
    align-items: center; 
    padding: 12px 20px; 
    cursor: pointer; 
    list-style: none; 
    gap: 12px; 
  }
  
  .chat-avatar {
    width: 64px;
    height: 64px;
    border-radius: 50%;
    object-fit: cover;
    object-position: center 30%;
    border: 3px solid var(--border);
    flex-shrink: 0;
  }
  
  .chat-avatar.online { border-color: var(--success); }
  .chat-avatar.offline { border-color: var(--text-secondary); }
  
  .chat-info { flex: 1; min-width: 0; }
  
  .chat-name { 
    color: var(--heading); 
    font-weight: 600; 
    font-size: 1.05rem; 
    margin-bottom: 4px;
  }
  
  .chat-status { 
    font-size: 0.85rem; 
    display: flex; 
    align-items: center; 
    gap: 6px; 
    font-weight: 500; 
  }
  
  .status-online { color: var(--success); }
  .status-offline { color: var(--text-secondary); }
  
  .online-dot {
    width: 8px;
    height: 8px;
    background: var(--success);
    border-radius: 50%;
    animation: pulse 2s infinite;
    flex-shrink: 0;
  }
  
  .offline-dot {
    width: 8px;
    height: 8px;
    background: var(--text-secondary);
    border-radius: 50%;
    flex-shrink: 0;
  }
  
  @keyframes pulse {
    0% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(0.9); }
    100% { opacity: 1; transform: scale(1); }
  }
  
  .chat-arrow { 
    margin-left: auto; 
    font-size: 1.2rem;
    opacity: 0.6;
    color: var(--text-secondary);
  }
  
  .chat-options { 
    display: flex; 
    gap: 12px; 
    padding: 0 20px 16px; 
  }
  
  .chat-btn { 
    flex: 1; 
    padding: 12px; 
    border-radius: 24px; 
    text-align: center; 
    text-decoration: none; 
    font-weight: 600; 
    color: white !important; 
    font-size: 0.9rem;
    transition: transform 0.1s;
  }
  
  .chat-btn:active { transform: scale(0.98); }
  
  .chat-btn.telegram { background: linear-gradient(135deg, #0088cc, #00a8e8); }
  .chat-btn.viber { background: linear-gradient(135deg, #7360f2, #9b8af5); }
  
  .photo-card { text-align: center; }
  
  .photo-card img { 
    width: 100%; 
    height: 320px; 
    object-fit: cover; 
    object-position: center 40%; 
    border-radius: 16px; 
    box-shadow: 0 4px 12px var(--shadow); 
    display: block;
    border: 1px solid var(--border);
  }
  
  .photo-label { 
    margin-top: 0.8rem; 
    font-weight: 600; 
    color: var(--text); 
    font-size: 1.05rem; 
    line-height: 1.4;
  }
  
  .photo-label small { opacity: 0.7; font-size: 0.9em; color: var(--text-secondary); }
  
  .photo-links {
    margin-top: 0.5rem;
    font-size: 0.85rem;
    color: var(--text-secondary);
  }
  
  .photo-links a { 
    color: var(--accent) !important; 
    text-decoration: none;
  }
  
  .site-footer-stats {
    margin-top: 4rem;
    padding: 2rem;
    text-align: center;
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 16px;
    box-shadow: 0 2px 8px var(--shadow);
  }
  
  .online-now {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    color: var(--success);
    font-size: 0.95rem;
    font-weight: 500;
    margin-top: 12px;
    background: var(--bg-secondary);
    padding: 8px 16px;
    border-radius: 20px;
    border: 1px solid var(--border);
  }
  
  #online-count { color: var(--success); font-weight: 700; font-size: 1.1rem; }
  
  .site-footer { display: none !important; }
  
  .lightbox-overlay {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.95);
    z-index: 10000;
    justify-content: center;
    align-items: center;
  }
  
  .lightbox-overlay.active { display: flex; }
  .lightbox-img { max-width: 95%; max-height: 85vh; object-fit: contain; border-radius: 8px; }
  .lightbox-close { 
    position: absolute; 
    top: 20px; 
    right: 20px; 
    color: white; 
    font-size: 40px; 
    cursor: pointer;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .promo-banner {
    display: none;
    background: linear-gradient(135deg, #00c853 0%, #64dd17 100%);
    color: white;
    padding: 24px;
    border-radius: 16px;
    margin: 20px 0;
    text-align: center;
    font-size: 1.5em;
    font-weight: bold;
    box-shadow: 0 4px 20px rgba(0, 200, 83, 0.4);
    animation: promo-pulse 2s infinite;
    border: 2px solid rgba(255,255,255,0.2);
    line-height: 1.4;
  }
  
  .promo-banner.active {
    display: block;
  }
  
  .promo-label {
    display: block;
    font-size: 0.7em;
    opacity: 0.9;
    margin-bottom: 8px;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  
  @keyframes promo-pulse {
    0%, 100% { transform: scale(1); box-shadow: 0 4px 20px rgba(0, 200, 83, 0.4); }
    50% { transform: scale(1.02); box-shadow: 0 8px 30px rgba(0, 200, 83, 0.6); }
  }
  
  [data-theme="dark"] .promo-banner {
    background: linear-gradient(135deg, #00b248 0%, #76ff03 100%);
    box-shadow: 0 4px 20px rgba(0, 200, 83, 0.5);
  }
  
  .reviews-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    margin: 1.5rem 0;
  }
  
  .review-card {
    background: var(--bg-card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 20px;
    box-shadow: 0 2px 8px var(--shadow);
    transition: transform 0.2s, box-shadow 0.2s;
  }
  
  .review-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(59, 130, 246, 0.1);
  }
  
  [data-theme="dark"] .review-card:hover {
    box-shadow: 0 4px 16px rgba(96, 165, 250, 0.15);
  }
  
  .review-header {
    display: flex;
    gap: 12px;
    margin-bottom: 12px;
    align-items: flex-start;
  }
  
  .review-avatar {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--gradient-end));
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 0.9rem;
    flex-shrink: 0;
  }
  
  .review-meta {
    flex: 1;
    min-width: 0;
  }
  
  .review-name {
    color: var(--heading);
    font-weight: 600;
    font-size: 1rem;
    margin-bottom: 2px;
  }
  
  .review-stars {
    color: #fbbf24;
    font-size: 1.1rem;
    letter-spacing: 2px;
    margin-bottom: 2px;
  }
  
  .review-date {
    color: var(--text-secondary);
    font-size: 0.8rem;
  }
  
  .review-text {
    color: var(--text);
    line-height: 1.6;
    font-size: 0.95rem;
    margin-bottom: 12px;
    font-style: italic;
  }
  
  .review-modal-overlay {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.7);
    z-index: 10001;
    justify-content: center;
    align-items: center;
    backdrop-filter: blur(4px);
    padding: 20px;
    box-sizing: border-box;
  }
  
  .review-modal-overlay.active {
    display: flex;
  }
  
  .review-modal {
    background: var(--bg-card);
    padding: 30px;
    border-radius: 20px;
    max-width: 500px;
    width: 100%;
    border: 1px solid var(--border);
    box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    position: relative;
    max-height: 90vh;
    overflow-y: auto;
  }
  
  .review-modal h3 {
    margin: 0 0 8px 0;
    color: var(--heading);
    text-align: center;
    font-size: 1.5rem;
  }
  
  .review-modal-subtitle {
    color: var(--text-secondary);
    font-size: 0.9rem;
    text-align: center;
    margin-bottom: 24px;
  }
  
  .review-form-group {
    margin-bottom: 16px;
  }
  
  .review-form-group label {
    display: block;
    margin-bottom: 6px;
    color: var(--text);
    font-weight: 500;
    font-size: 0.9rem;
  }
  
  .review-input, .review-textarea, .review-stars-select {
    width: 100%;
    padding: 12px 16px;
    border: 1px solid var(--border);
    border-radius: 12px;
    background: var(--bg);
    color: var(--text);
    font-size: 1rem;
    box-sizing: border-box;
    font-family: inherit;
  }
  
  .review-textarea {
    resize: vertical;
    min-height: 100px;
  }
  
  .review-modal-buttons {
    display: flex;
    gap: 12px;
    margin-top: 24px;
  }
  
  .review-btn-submit {
    flex: 1;
    padding: 14px;
    background: linear-gradient(135deg, var(--gradient-start) 0%, var(--gradient-end) 100%);
    color: white;
    border: none;
    border-radius: 12px;
    font-weight: 600;
    font-size: 1rem;
    cursor: pointer;
  }
  
  .review-btn-submit:disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }
  
  .review-btn-cancel {
    flex: 1;
    padding: 14px;
    background: var(--bg-secondary);
    color: var(--text-secondary);
    border: 1px solid var(--border);
    border-radius: 12px;
    font-weight: 600;
    font-size: 1rem;
    cursor: pointer;
  }
  
  .review-status {
    margin-top: 16px;
    font-size: 0.95rem;
    text-align: center;
    min-height: 24px;
    font-weight: 500;
  }
  
  .review-status.success { color: var(--success); }
  .review-status.error { color: #ef4444; }
  
  @media (max-width: 768px) {
    h1 { font-size: 1.5rem; }
    .gallery-grid { grid-template-columns: 1fr; }
    .photos-row { grid-template-columns: 1fr; }
    .chat-avatar { width: 60px; height: 60px; }
    .photo-card img { height: 220px; }
    #theme-toggle { width: 44px; height: 44px; }
    .reviews-grid { grid-template-columns: 1fr; }
  }
</style>

<button onclick="toggleTheme()" id="theme-toggle">🌙</button>

<h1>Ремонт компьютерной и мобильной техники в Дрогичине</h1>

<!-- Баннер Акции Дня -->
<div id="promo-banner" class="promo-banner">
  <span class="promo-label">🎯 Акция дня</span>
  <span id="promo-text"></span>
</div>

<div class="photos-row">
  <div class="chat-container">
    <details class="chat-details">
      <summary class="chat-summary">
        <img src="{{ '/assets/images/alex.jpg' | relative_url }}" class="chat-avatar online" id="chat-avatar" alt="Александр">
        <div class="chat-info">
          <div class="chat-name">Александр</div>
          <div class="chat-status status-online" id="status-text">
            <span class="online-dot"></span>В сети
          </div>
        </div>
        <span class="chat-arrow">↓</span>
      </summary>
      <div class="chat-options">
        <a href="https://t.me/AlexDrog81" class="chat-btn telegram" target="_blank">📱 Telegram</a>
        <a href="viber://chat?number=375297256982" class="chat-btn viber">💬 Viber</a>
      </div>
    </details>
    <p style="text-align: center; margin-top: 8px; font-size: 0.9rem; color: var(--text-secondary);">
      Мастер по ремонту • <span id="work-status-text" style="color: var(--success); font-weight: 600;">Принимаю заказы</span>
    </p>
  </div>
  
  <div class="photo-card">
    <img src="{{ '/assets/images/zdanie.JPG' | relative_url }}" alt="Здание мастерской">
    <div class="photo-label">
      г. Дрогичин, ул. Ленина, 141а<br>
      <small>2 этаж</small>
    </div>
    <div class="photo-links">
      🗺️ <a href="https://yandex.ru/maps/?text=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0">Яндекс Карты</a> • 
      <a href="https://www.google.com/maps/search/?api=1&query=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0">Google Maps</a>
    </div>
  </div>
</div>

<a href="./uslugi/" class="btn btn-large">📋 Прайс и услуги</a>

<h2>Режим работы:</h2>
<p>
🕐 Вт-Пт: 10:00-18:00<br>
🕐 Обед: 12:00-13:00<br>
🕐 Сб-Вс: 10:00-14:00<br>
<span class="highlight">🕐 Понедельник: ВЫХОДНОЙ</span>
</p>

<h2>Примеры работ <small style="font-size:0.6em;opacity:0.7;color:var(--text-secondary);">(от новых к старым)</small></h2>

{% assign all_works = site.data.works | reversed %}
{% assign pinned_works = all_works | where: "pinned", true %}
{% assign regular_works = all_works | where_exp: "item", "item.pinned != true" %}
{% assign works = pinned_works | concat: regular_works %}

{% for work in works limit:10 %}
<details {% if work.pinned %}class="pinned" open{% endif %}>
  <summary>
    <h3>
      {% if work.pinned %}<span class="pinned-badge">📌</span>{% endif %}
      🔧 {{ work.title }}
    </h3>
  </summary>
  <div class="gallery-grid">
    <div class="gallery-item">
      <div class="label-red">🔴 ДО</div>
      <img src="{{ work.before_img | relative_url }}" alt="До ремонта" loading="lazy">
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="{{ work.after_img | relative_url }}" alt="После ремонта" loading="lazy">
    </div>
  </div>
</details>
{% endfor %}

{% if works.size == 0 %}
<p style="text-align: center; color: var(--text-secondary); opacity: 0.7;">Примеры работ скоро появятся...</p>
{% endif %}

<!-- === БЛОК ОТЗЫВОВ (динамический из Firebase) === -->
<h2>Отзывы клиентов <small style="font-size:0.6em;opacity:0.7;color:var(--text-secondary);">что говорят о работе</small></h2>

<div id="reviews-container">
  <p style="text-align: center; color: var(--text-secondary);">Загрузка отзывов...</p>
</div>

<p style="text-align: center; margin-top: 1.5rem;">
  <button onclick="openReviewModal()" class="btn" style="font-size: 1rem; padding: 14px 28px; margin-top: 1rem;">⭐ Оставить отзыв</button>
</p>

<!-- === МОДАЛЬНОЕ ОКНО ФОРМЫ ОТЗЫВА === -->
<div id="review-modal-overlay" class="review-modal-overlay">
  <div class="review-modal">
    <h3>Ваш отзыв</h3>
    <p class="review-modal-subtitle">Появится на сайте после проверки</p>
    
    <div class="review-form-group">
      <label for="review-name">Ваше имя</label>
      <input type="text" id="review-name" class="review-input" placeholder="Например: Александр" maxlength="50">
    </div>
    
    <div class="review-form-group">
      <label for="review-text">Ваш отзыв</label>
      <textarea id="review-text" class="review-textarea" placeholder="Напишите о вашем опыте ремонта..." maxlength="500"></textarea>
    </div>
    
    <div class="review-form-group" style="text-align: center;">
      <label for="review-stars" style="display: inline-block; margin-right: 10px;">Оценка:</label>
      <select id="review-stars" class="review-stars-select">
        <option value="5">★★★★★ Отлично</option>
        <option value="4">★★★★☆ Хорошо</option>
        <option value="3">★★★☆☆ Нормально</option>
        <option value="2">★★☆☆☆ Плохо</option>
        <option value="1">★☆☆☆☆ Ужасно</option>
      </select>
    </div>
    
    <div class="review-modal-buttons">
      <button onclick="submitReview()" class="review-btn-submit" id="review-submit-btn">Отправить</button>
      <button onclick="closeReviewModal()" class="review-btn-cancel">Отмена</button>
    </div>
    
    <div id="review-form-status" class="review-status"></div>
  </div>
</div>

<h2>Почему обращаются ко мне</h2>
<p>
✅ <strong>Бесплатная диагностика</strong> — платишь только за ремонт<br>
✅ <strong>Гарантия</strong> — от 1 месяца на все виды работ<br>
✅ <strong>Быстро</strong> — большинство работ в день обращения<br>
✅ <strong>Сложные случаи</strong> — то, что отказались делать другие
</p>

<div id="lightbox" class="lightbox-overlay">
  <span class="lightbox-close">&times;</span>
  <img id="lightbox-img" class="lightbox-img" alt="Увеличенное фото">
</div>

<div class="site-footer-stats">
  <div style="margin-bottom: 1rem;">
    <a href="https://metrika.yandex.ru/stat/?id=106913790&from=informer" target="_blank" rel="noopener">
      <img src="https://informer.yandex.ru/informer/106913790/3_1_FFFFFFFF_EFEFEFFF_0_pageviews" style="width:88px; height:31px; border:0;" alt="Яндекс.Метрика">
    </a>
  </div>
  
  <div style="color: var(--text-secondary); font-size: 0.875rem; line-height: 1.6;">
    Разработка и сопровождение<br>
    <a href="tel:+375292065065" style="color: var(--accent); text-decoration: none; font-weight: 600; font-size: 1rem;">📞 +375 29 2 065 065</a>
  </div>
  
  <div class="online-now">
    Сейчас онлайн: <span id="online-count">1</span>&nbsp;чел.
  </div>
</div>

<script type="module">
  // Firebase конфиг
  const firebaseConfig = {
    apiKey: "AIzaSyDgSGIhDkfu1_l0Ryg0MeiLfVxp-lgiSsU",
    authDomain: "alexdrog.firebaseapp.com",
    databaseURL: "https://alexdrog-default-rtdb.europe-west1.firebasedatabase.app",
    projectId: "alexdrog",
    storageBucket: "alexdrog.firebasestorage.app",
    messagingSenderId: "33899135860",
    appId: "1:33899135860:web:396df092035fb19a11a221",
    measurementId: "G-KJ7JQ8R476"
  };

  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
  import { getDatabase, ref, set, onDisconnect, onValue, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";

  try {
    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);
    const sessionId = Date.now() + '_' + Math.random().toString(36).substr(2, 9);
    const userRef = ref(db, 'online/' + sessionId);
    
    set(userRef, { timestamp: serverTimestamp() });
    onDisconnect(userRef).remove();
    
    onValue(ref(db, 'online'), (snapshot) => {
      const data = snapshot.val();
      const count = data ? Object.keys(data).length : 0;
      const el = document.getElementById('online-count');
      if (el) el.textContent = count;
    });
  } catch (e) {
    console.error('Firebase init error:', e);
  }
</script>

<script>
  // === ЗАГРУЗКА ОТЗЫВОВ ИЗ FIREBASE ===
  async function loadReviewsFromFirebase() {
    const container = document.getElementById('reviews-container');
    
    try {
      // ИСПРАВЛЕНО: убран пробел в URL
      const response = await fetch('https://alexdrog-default-rtdb.europe-west1.firebasedatabase.app/reviews_approved.json');
      
      if (!response.ok) {
        throw new Error('HTTP ' + response.status);
      }
      
      const data = await response.json();
      console.log('Отзывы из Firebase:', data);
      
      if (!data) {
        container.innerHTML = '<p style="text-align: center; color: var(--text-secondary); opacity: 0.7;">Пока нет отзывов. Будьте первым!</p>';
        return;
      }
      
      // Преобразуем объект в массив
      let reviews = [];
      for (let key in data) {
        if (data.hasOwnProperty(key) && data[key]) {
          const review = data[key];
          // Проверяем обязательные поля
          if (review.name || review.text) {
            reviews.push({
              id: key,
              name: review.name || 'Аноним',
              text: review.text || review.comment || '',
              stars: parseInt(review.stars) || 5,
              date: review.date || '',
              timestamp: review.timestamp || 0,
              banned: review.banned || false
            });
          }
        }
      }
      
      // Фильтруем забаненных и сортируем по дате (новые сверху)
      reviews = reviews.filter(r => !r.banned).sort((a, b) => b.timestamp - a.timestamp);
      
      console.log('Обработанные отзывы:', reviews);
      
      if (reviews.length === 0) {
        container.innerHTML = '<p style="text-align: center; color: var(--text-secondary); opacity: 0.7;">Пока нет отзывов. Будьте первым!</p>';
        return;
      }
      
      // Берем первые 3 отзыва
      const displayReviews = reviews.slice(0, 3);
      
      let html = '<div class="reviews-grid">';
      
      displayReviews.forEach(review => {
        // Экранирование HTML для безопасности
        const escapeHtml = (text) => {
          if (!text) return '';
          return text.replace(/&/g, "&amp;")
                     .replace(/</g, "&lt;")
                     .replace(/>/g, "&gt;")
                     .replace(/"/g, "&quot;")
                     .replace(/'/g, "&#039;");
        };
        
        // Генерируем инициалы
        let initials = 'АН';
        if (review.name && review.name !== 'Аноним') {
          initials = review.name.split(' ').map(n => n[0]).join('').toUpperCase().slice(0, 2);
        }
        
        // Генерируем звезды
        const starCount = Math.max(1, Math.min(5, review.stars));
        const stars = '★'.repeat(starCount) + '☆'.repeat(5 - starCount);
        
        const safeName = escapeHtml(review.name);
        const safeText = escapeHtml(review.text);
        const safeDate = escapeHtml(review.date);
        
        html += `
          <div class="review-card">
            <div class="review-header">
              <div class="review-avatar">${initials}</div>
              <div class="review-meta">
                <div class="review-name">${safeName}</div>
                <div class="review-stars">${stars}</div>
                <div class="review-date">${safeDate}</div>
              </div>
            </div>
            <div class="review-text">"${safeText || 'Без текста'}"</div>
          </div>
        `;
      });
      
      html += '</div>';
      container.innerHTML = html;
      
    } catch (error) {
      console.error('Ошибка загрузки отзывов:', error);
      container.innerHTML = '<p style="text-align: center; color: var(--text-secondary);">Не удалось загрузить отзывы. <button onclick="loadReviewsFromFirebase()" style="background:none;border:none;color:var(--accent);text-decoration:underline;cursor:pointer;">Попробовать снова</button></p>';
    }
  }

  // Загружаем при старте
  document.addEventListener('DOMContentLoaded', loadReviewsFromFirebase);
  
  // Обновляем каждую минуту
  setInterval(loadReviewsFromFirebase, 60000);

  // === ОСТАЛЬНЫЕ ФУНКЦИИ ===
  
  const WORK_PHRASES = [
    "Принимаю заказы", "На связи прямо сейчас", "Готов помочь с ремонтом",
    "Жду вашего звонка", "Работаю сегодня", "Можно обращаться"
  ];

  const MORNING_PHRASES = [
    "Начинаю работу в 10:00", "Скоро буду на месте", "С 10:00 принимаю заказы"
  ];

  const EVENING_PHRASES = [
    "Сегодня больше не работаю", "Завтра с 10:00 на месте", "Рабочий день окончен"
  ];

  const NIGHT_PHRASES = [
    "Ночной перерыв", "Сплю, отвечу утром", "Отдыхаю до рассвета"
  ];

  const DAY_OFF_PHRASES = [
    "Сегодня выходной", "Отдыхаю сегодня", "Прием заказов с завтра"
  ];

  let customStatusData = null;

  function isPromoActive() {
    if (!customStatusData || !customStatusData.active || customStatusData.type !== 'promo') {
      return false;
    }
    if (customStatusData.until) {
      const now = new Date();
      const parts = customStatusData.until.split(/[. :]/);
      if (parts.length >= 2) {
        const day = parseInt(parts[0]);
        const month = parseInt(parts[1]) - 1;
        const year = parts[2] ? (parts[2].length === 2 ? 2000 + parseInt(parts[2]) : parseInt(parts[2])) : now.getFullYear();
        const hour = parts[3] ? parseInt(parts[3]) : 20;
        const minute = parts[4] ? parseInt(parts[4]) : 0;
        const untilDate = new Date(year, month, day, hour, minute);
        if (now > untilDate) return false;
      }
    }
    return true;
  }

  async function loadCustomStatus() {
    try {
      const response = await fetch('status.json?t=' + Date.now());
      if (response.ok) {
        const data = await response.json();
        if (data.active && data.text) {
          if (data.until) {
            const now = new Date();
            const parts = data.until.split(/[. :]/);
            if (parts.length >= 2) {
              const day = parseInt(parts[0]);
              const month = parseInt(parts[1]) - 1;
              const year = parts[2] ? (parts[2].length === 2 ? 2000 + parseInt(parts[2]) : parseInt(parts[2])) : now.getFullYear();
              const hour = parts[3] ? parseInt(parts[3]) : 23;
              const minute = parts[4] ? parseInt(parts[4]) : 59;
              const untilDate = new Date(year, month, day, hour, minute);
              if (now > untilDate) {
                customStatusData = null;
                return;
              }
            }
          }
          customStatusData = data;
          return;
        }
      }
      customStatusData = null;
    } catch (e) {
      customStatusData = null;
    }
  }

  function getTimePeriod() {
    const now = new Date();
    const day = now.getDay();
    const hour = now.getHours();
    
    if (hour >= 23 || hour < 7) return 'night';
    if (day === 1) return 'dayoff';
    
    if (day >= 2 && day <= 5) {
      if (hour < 10) return 'morning';
      if (hour >= 18) return 'evening';
      return 'work';
    }
    
    if (day === 0 || day === 6) {
      if (hour < 10) return 'morning';
      if (hour >= 14) return 'evening';
      return 'work';
    }
    
    return 'dayoff';
  }

  function updateAllStatuses() {
    const statusEl = document.getElementById('work-status-text');
    const promoBanner = document.getElementById('promo-banner');
    const promoText = document.getElementById('promo-text');
    const avatar = document.getElementById('chat-avatar');
    const avatarText = document.getElementById('status-text');
    
    if (isPromoActive()) {
      if (promoText) promoText.textContent = customStatusData.text;
      if (promoBanner) promoBanner.classList.add('active');
      
      if (avatar) {
        avatar.classList.remove('offline');
        avatar.classList.add('online');
      }
      if (avatarText) {
        avatarText.innerHTML = '<span class="online-dot"></span>В сети';
        avatarText.className = 'chat-status status-online';
      }
      
      if (statusEl) {
        statusEl.textContent = "🔥 Акция дня!";
        statusEl.style.color = '#00c853';
        statusEl.style.fontWeight = '700';
        statusEl.style.fontSize = '1rem';
      }
      return;
    }
    
    if (promoBanner) promoBanner.classList.remove('active');
    
    if (customStatusData && customStatusData.active) {
      const schedule = checkWorkSchedule();
      
      if (schedule.isOnline) {
        avatar.classList.remove('offline');
        avatar.classList.add('online');
        avatarText.innerHTML = '<span class="online-dot"></span>В сети';
        avatarText.className = 'chat-status status-online';
      } else {
        avatar.classList.remove('online');
        avatar.classList.add('offline');
        avatarText.innerHTML = '<span class="offline-dot"></span>' + schedule.statusText;
        avatarText.className = 'chat-status status-offline';
      }
      
      if (statusEl) {
        statusEl.textContent = customStatusData.text;
        statusEl.style.color = '#dc2626';
        statusEl.style.fontWeight = '700';
        statusEl.style.fontSize = '0.95rem';
      }
      return;
    }
    
    const period = getTimePeriod();
    let phrases, color, weight = '600';
    
    switch(period) {
      case 'work': phrases = WORK_PHRASES; color = 'var(--success)'; break;
      case 'morning': phrases = MORNING_PHRASES; color = '#f59e0b'; break;
      case 'evening': phrases = EVENING_PHRASES; color = 'var(--text-secondary)'; break;
      case 'night': phrases = NIGHT_PHRASES; color = 'var(--text-secondary)'; break;
      case 'dayoff': phrases = DAY_OFF_PHRASES; color = '#dc2626'; weight = '700'; break;
      default: phrases = WORK_PHRASES; color = 'var(--success)';
    }
    
    const phrase = phrases[Math.floor(Math.random() * phrases.length)];
    
    if (statusEl) {
      statusEl.textContent = phrase;
      statusEl.style.color = color;
      statusEl.style.fontWeight = weight;
      statusEl.style.fontSize = '0.9rem';
    }
    
    const schedule = checkWorkSchedule();
    if (schedule.isOnline) {
      avatar.classList.remove('offline');
      avatar.classList.add('online');
      avatarText.innerHTML = '<span class="online-dot"></span>В сети';
      avatarText.className = 'chat-status status-online';
    } else {
      avatar.classList.remove('online');
      avatar.classList.add('offline');
      avatarText.innerHTML = '<span class="offline-dot"></span>' + schedule.statusText;
      avatarText.className = 'chat-status status-offline';
    }
  }

  function checkWorkSchedule() {
    const now = new Date();
    const day = now.getDay();
    const hour = now.getHours();
    const minute = now.getMinutes();
    const time = hour + minute / 60;
    
    let isOnline = false;
    let statusText = "";
    
    if (day === 1) {
      statusText = "Сегодня выходной, отвечу завтра с 10:00";
    } else if (day >= 2 && day <= 5) {
      if (time >= 10 && time < 12) isOnline = true;
      else if (time >= 13 && time < 18) isOnline = true;
      else if (time >= 12 && time < 13) statusText = "Обеденный перерыв до 13:00";
      else if (time < 10) statusText = "Начинаю работу сегодня в 10:00";
      else statusText = day === 5 ? "Отвечу завтра (суббота) с 10:00" : "Отвечу завтра с 10:00";
    } else if (day === 6) {
      if (time >= 10 && time < 14) isOnline = true;
      else if (time < 10) statusText = "Начинаю работу сегодня в 10:00";
      else statusText = "Отвечу завтра (воскресенье) с 10:00";
    } else if (day === 0) {
      if (time >= 10 && time < 14) isOnline = true;
      else if (time < 10) statusText = "Начинаю работу сегодня в 10:00";
      else statusText = "Отвечу во вторник с 10:00";
    }
    
    if (isOnline) statusText = "В сети";
    return { isOnline, statusText };
  }

  document.addEventListener('DOMContentLoaded', function() {
    const btn = document.getElementById('theme-toggle');
    const current = document.documentElement.getAttribute('data-theme');
    if (btn) btn.textContent = current === 'dark' ? '☀️' : '🌙';
    
    loadCustomStatus().then(updateAllStatuses);
    
    setInterval(async () => {
      await loadCustomStatus();
      updateAllStatuses();
    }, 300000);
    
    setInterval(() => {
      if (customStatusData && customStatusData.type === 'promo') {
        updateAllStatuses();
      }
    }, 60000);
  });

  // Lightbox
  let currentIdx = 0;
  let galleryImgs = [];
  
  function openLightbox(img) {
    galleryImgs = img.closest('details').querySelectorAll('.gallery-item img');
    currentIdx = Array.from(galleryImgs).indexOf(img);
    document.getElementById('lightbox-img').src = img.src;
    document.getElementById('lightbox').classList.add('active');
    document.body.style.overflow = 'hidden';
  }
  
  function closeLightbox() {
    document.getElementById('lightbox').classList.remove('active');
    document.body.style.overflow = '';
  }
  
  function changeImage(dir) {
    currentIdx += dir;
    if (currentIdx >= galleryImgs.length) currentIdx = 0;
    if (currentIdx < 0) currentIdx = galleryImgs.length - 1;
    document.getElementById('lightbox-img').src = galleryImgs[currentIdx].src;
  }
  
  document.addEventListener('click', function(e) {
    if (e.target.matches('.gallery-item img')) {
      e.preventDefault();
      openLightbox(e.target);
    }
    if (e.target.matches('.lightbox-overlay, .lightbox-close')) {
      closeLightbox();
    }
  });
  
  document.addEventListener('keydown', function(e) {
    if (e.key === 'Escape') closeLightbox();
    if (e.key === 'ArrowLeft') changeImage(-1);
    if (e.key === 'ArrowRight') changeImage(1);
  });

  // Форма отзывов
  function getFingerprint() {
    let fp = localStorage.getItem('review_fp');
    if (!fp) {
      fp = 'fp_' + Math.random().toString(36).substr(2, 9) + '_' + Date.now();
      localStorage.setItem('review_fp', fp);
    }
    return fp;
  }

  function isBanned() {
    return localStorage.getItem('review_banned') === 'true';
  }

  window.openReviewModal = function() {
    if (isBanned()) {
      alert('❌ Вы не можете оставлять отзывы');
      return;
    }
    document.getElementById('review-modal-overlay').classList.add('active');
    document.body.style.overflow = 'hidden';
  };

  window.closeReviewModal = function() {
    document.getElementById('review-modal-overlay').classList.remove('active');
    document.body.style.overflow = '';
    const statusEl = document.getElementById('review-form-status');
    if (statusEl) {
      statusEl.textContent = '';
      statusEl.className = 'review-status';
    }
  };

  window.submitReview = async function() {
    const nameInput = document.getElementById('review-name');
    const textInput = document.getElementById('review-text');
    const starsInput = document.getElementById('review-stars');
    const statusEl = document.getElementById('review-form-status');
    const submitBtn = document.getElementById('review-submit-btn');
    
    const name = nameInput.value.trim();
    const text = textInput.value.trim();
    const stars = parseInt(starsInput.value);
    
    if (!name || !text) {
      statusEl.textContent = '❌ Заполните все поля';
      statusEl.className = 'review-status error';
      return;
    }
    
    if (name.length < 2) {
      statusEl.textContent = '❌ Имя слишком короткое';
      statusEl.className = 'review-status error';
      return;
    }
    
    if (text.length < 10) {
      statusEl.textContent = '❌ Отзыв слишком короткий (минимум 10 символов)';
      statusEl.className = 'review-status error';
      return;
    }
    
    if (text.length > 500) {
      statusEl.textContent = '❌ Отзыв слишком длинный (максимум 500 символов)';
      statusEl.className = 'review-status error';
      return;
    }
    
    const lastReview = localStorage.getItem('last_review_time');
    if (lastReview && (Date.now() - parseInt(lastReview)) < 600000) {
      const minsLeft = Math.ceil((600000 - (Date.now() - parseInt(lastReview))) / 60000);
      statusEl.textContent = `❌ Подождите ${minsLeft} мин. перед следующим отзывом`;
      statusEl.className = 'review-status error';
      return;
    }
    
    submitBtn.disabled = true;
    statusEl.textContent = '⏳ Отправка...';
    statusEl.className = 'review-status';
    
    const reviewData = {
      id: 'rev_' + Date.now(),
      name: name,
      text: text,
      stars: stars,
      date: new Date().toLocaleDateString('ru-RU', {
        day: 'numeric',
        month: 'long',
        year: 'numeric'
      }),
      timestamp: Date.now(),
      status: 'pending',
      fingerprint: getFingerprint()
    };
    
    try {
      // ИСПРАВЛЕНО: убран пробел в URL
      const response = await fetch('https://alexdrog-default-rtdb.europe-west1.firebasedatabase.app/reviews_pending/' + reviewData.id + '.json', {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(reviewData)
      });
      
      if (response.ok) {
        statusEl.textContent = '✅ Отзыв отправлен! Появится после проверки.';
        statusEl.className = 'review-status success';
        localStorage.setItem('last_review_time', Date.now());
        
        nameInput.value = '';
        textInput.value = '';
        starsInput.value = '5';
        
        setTimeout(() => {
          closeReviewModal();
        }, 2000);
      } else {
        throw new Error('Network error');
      }
    } catch (error) {
      console.error('Error:', error);
      statusEl.textContent = '❌ Ошибка отправки. Попробуйте позже.';
      statusEl.className = 'review-status error';
      submitBtn.disabled = false;
    }
  };

  document.addEventListener('click', function(e) {
    if (e.target.id === 'review-modal-overlay') {
      closeReviewModal();
    }
  });

  document.addEventListener('keydown', function(e) {
    if (e.key === 'Escape') {
      const modal = document.getElementById('review-modal-overlay');
      if (modal && modal.classList.contains('active')) {
        closeReviewModal();
      }
    }
  });
</script>
