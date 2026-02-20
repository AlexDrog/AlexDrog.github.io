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
  :root {
    --bg: #ffffff;
    --text: #24292e;
    --heading: #1a1a1a;
    --link: #0366d6;
    --border: #e1e4e8;
    --card: #f6f8fa;
    --btn-bg: #2ea44f;
    --btn-color: #ffffff;
  }
  
  [data-theme="dark"] {
    --bg: #0d1117;
    --text: #c9d1d9;
    --heading: #e6edf3;
    --link: #58a6ff;
    --border: #30363d;
    --card: #161b22;
    --btn-bg: #238636;
  }
  
  body { 
    background-color: var(--bg) !important; 
    color: var(--text) !important;
    transition: 0.3s;
    margin: 0;
    padding: 0;
  }
  
  h1, h2, h3 { 
    color: var(--heading) !important; 
    border-color: var(--border) !important; 
    line-height: 1.3;
  }
  
  a { color: var(--link) !important; }
  .page-header { background: linear-gradient(120deg, #155799, #159957) !important; }
  .main-content { background: var(--bg) !important; }
  
  .btn {
    display: inline-block;
    padding: 12px 24px;
    margin: 5px;
    background-color: var(--btn-bg) !important;
    color: var(--btn-color) !important;
    border-radius: 6px;
    text-decoration: none;
    font-weight: 600;
  }
  
  .btn-large {
    display: block;
    width: 100%;
    max-width: 600px;
    margin: 2rem auto;
    text-align: center;
    font-size: 1.1rem;
    padding: 14px 20px;
  }
  
  details {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px;
    margin-bottom: 12px;
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
    border-radius: 4px; 
    overflow: hidden; 
  }
  .label-red { 
    background: #e74c3c; 
    color: white; 
    padding: 8px; 
    font-weight: bold; 
    font-size: 0.9rem;
  }
  .label-green { 
    background: #27ae60; 
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
  
  .highlight { color: #e94560; font-weight: bold; }
  
  #theme-toggle {
    position: fixed;
    top: 15px;
    right: 15px;
    z-index: 9999;
    background: var(--btn-bg);
    color: var(--btn-color);
    border: none;
    border-radius: 50%;
    width: 45px;
    height: 45px;
    font-size: 20px;
    cursor: pointer;
    box-shadow: 0 2px 10px rgba(0,0,0,0.3);
    display: flex;
    align-items: center;
    justify-content: center;
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
    background: var(--card); 
    border: 1px solid var(--border); 
    border-radius: 30px; 
    overflow: hidden; 
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
    flex-shrink: 0; /* Запрещаем сжимать на десктопе */
  }
  
  .chat-avatar.online { border-color: #2ea44f; }
  .chat-avatar.offline { border-color: #8b949e; }
  
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
  
  .status-online { color: #2ea44f; }
  .status-offline { color: #8b949e; }
  
  .online-dot {
    width: 8px;
    height: 8px;
    background: #2ea44f;
    border-radius: 50%;
    animation: pulse 2s infinite;
    flex-shrink: 0;
  }
  
  .offline-dot {
    width: 8px;
    height: 8px;
    background: #8b949e;
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
  }
  
  .chat-btn.telegram { background: linear-gradient(135deg, #0088cc, #00a8e8); }
  .chat-btn.viber { background: linear-gradient(135deg, #7360f2, #9b8af5); }
  
  .photo-card { text-align: center; }
  
  .photo-card img { 
    width: 100%; 
    height: 320px; 
    object-fit: cover; 
    object-position: center 40%; 
    border-radius: 12px; 
    box-shadow: 0 4px 12px rgba(0,0,0,0.15); 
    display: block;
  }
  
  .photo-label { 
    margin-top: 0.8rem; 
    font-weight: 600; 
    color: var(--text); 
    font-size: 1.05rem; 
    line-height: 1.4;
  }
  
  .photo-label small { opacity: 0.7; font-size: 0.9em; }
  
  .photo-links {
    margin-top: 0.5rem;
    font-size: 0.85rem;
    color: var(--text-secondary);
  }
  
  .photo-links a { 
    color: var(--link) !important; 
    text-decoration: none;
  }
  
  .site-footer-stats {
    margin-top: 4rem;
    padding: 2rem;
    text-align: center;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
  }
  
  .online-now {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    color: #2ea44f;
    font-size: 0.95rem;
    font-weight: 500;
    margin-top: 12px;
    background: var(--bg);
    padding: 8px 16px;
    border-radius: 20px;
    border: 1px solid var(--border);
  }
  
  #online-count { color: #2ea44f; font-weight: 700; font-size: 1.1rem; }
  
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
  
  /* === МОБИЛЬНАЯ ВЕРСИЯ (исправлено) === */
  @media (max-width: 768px) {
    h1 { 
      font-size: 1.5rem; 
      line-height: 1.25; 
      margin-bottom: 1rem;
      word-wrap: break-word;
    }
    
    h2 { font-size: 1.25rem; }
    
    .gallery-grid { grid-template-columns: 1fr; }
    
    .photos-row { 
      grid-template-columns: 1fr; 
      gap: 20px; 
      margin: 1rem 0;
    }
    
    /* ФИКС ВЫТЯНУТОГО АВАТАРА */
    .chat-avatar { 
      width: 60px; 
      height: 60px; 
      min-width: 60px;  /* Фикс для Safari */
      min-height: 60px;
      flex-shrink: 0;   /* Запрещаем flexbox менять размер */
      aspect-ratio: 1 / 1; /* Принудительно квадрат */
      object-fit: cover;
      border-radius: 50%;
    }
    
    .chat-summary { 
      padding: 12px 16px; 
      gap: 12px;
    }
    
    .chat-name { font-size: 1rem; }
    .chat-status { font-size: 0.8rem; }
    
    .chat-options { 
      padding: 0 16px 12px; 
      gap: 8px;
    }
    
    .chat-btn { 
      padding: 10px; 
      font-size: 0.85rem; 
    }
    
    .photo-card img { 
      height: 220px; 
      border-radius: 8px;
    }
    
    #theme-toggle { 
      width: 44px; 
      height: 44px; 
      font-size: 20px;
      top: 10px;
      right: 10px;
    }
    
    .btn-large {
      margin: 1.5rem auto;
      padding: 12px 16px;
      font-size: 1rem;
    }
    
    details { padding: 10px; }
    summary h3 { font-size: 0.95rem; }
    
    .site-footer-stats { 
      margin: 2rem -1rem 0; 
      border-radius: 0; 
      border-left: none; 
      border-right: none;
      padding: 1.5rem 1rem;
    }
  }
  
  /* Очень маленькие экраны */
  @media (max-width: 380px) {
    .chat-avatar {
      width: 52px;
      height: 52px;
      min-width: 52px;
      min-height: 52px;
    }
    
    .chat-name { font-size: 0.95rem; }
    h1 { font-size: 1.35rem; }
  }
</style>

<button onclick="toggleTheme()" id="theme-toggle">🌙</button>

<script type="module">
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
  } catch (e) {}
</script>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const btn = document.getElementById('theme-toggle');
    const current = document.documentElement.getAttribute('data-theme');
    if (btn) btn.textContent = current === 'dark' ? '☀️' : '🌙';
    
    const status = checkOnlineStatus();
    const avatar = document.getElementById('chat-avatar');
    const text = document.getElementById('status-text');
    
    if (avatar && text) {
      if (status.isOnline) {
        avatar.classList.add('online');
        avatar.classList.remove('offline');
        text.innerHTML = '<span class="online-dot"></span>В сети';
        text.className = 'chat-status status-online';
      } else {
        avatar.classList.add('offline');
        avatar.classList.remove('online');
        text.innerHTML = '<span class="offline-dot"></span>' + status.statusText;
        text.className = 'chat-status status-offline';
      }
    }
  });
  
  function checkOnlineStatus() {
    const now = new Date();
    const day = now.getDay();
    const hour = now.getHours();
    const minute = now.getMinutes();
    const time = hour + minute / 60;
    
    let isOnline = false;
    let statusText = "";
    
    if (day === 1) {
      statusText = "Сегодня выходной, отвечу завтра с 10:00";
    }
    else if (day >= 2 && day <= 5) {
      if (time >= 10 && time < 12) isOnline = true;
      else if (time >= 13 && time < 18) isOnline = true;
      else if (time >= 12 && time < 13) statusText = "Обеденный перерыв до 13:00";
      else if (time < 10) statusText = "Начинаю работу сегодня в 10:00";
      else statusText = day === 5 ? "Отвечу завтра (суббота) с 10:00" : "Отвечу завтра с 10:00";
    }
    else if (day === 6) {
      if (time >= 10 && time < 14) isOnline = true;
      else if (time < 10) statusText = "Начинаю работу сегодня в 10:00";
      else statusText = "Отвечу завтра (воскресенье) с 10:00";
    }
    else if (day === 0) {
      if (time >= 10 && time < 14) isOnline = true;
      else if (time < 10) statusText = "Начинаю работу сегодня в 10:00";
      else statusText = "Отвечу во вторник с 10:00";
    }
    
    if (isOnline) statusText = "В сети";
    return { isOnline, statusText };
  }
  
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
</script>

<h1>Ремонт компьютерной и мобильной техники в Дрогичине</h1>

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
    <p style="text-align: center; margin-top: 8px; font-size: 0.9rem; color: var(--text); opacity: 0.8;">
      Мастер по ремонту • <span style="color: #2ea44f;">Принимаю заказы</span>
    </p>
  </div>
  
  <div class="photo-card">
    <img src="{{ '/assets/images/zdanie.JPG' | relative_url }}" alt="Здание мастерской">
    <div class="photo-label">
      г. Дрогичин, ул. Ленина, 141а<br>
      <small>2 этаж</small>
    </div>
    <div class="photo-links">
      🗺️ <a href="https://yandex.ru/maps/?text=г.%20Дрогичин%2C%20ул.%20Ленина%2C%20141%20а">Яндекс Карты</a> • 
      <a href="https://www.google.com/maps/search/?api=1&query=г.%20Дрогичин%2C%20ул.%20Ленина%2C%20141%20а">Google Maps</a>
    </div>
  </div>
</div>

<a href="./uslugi/" class="btn btn-large">Прайс и услуги</a>

<h2>Режим работы:</h2>
<p>
🕐 Вт-Пт: 10:00-18:00<br>
🕐 Обед: 12:00-13:00<br>
🕐 Сб-Вс: 10:00-14:00<br>
<span class="highlight">🕐 Понедельник: ВЫХОДНОЙ</span>
</p>

<h2>Примеры работ <small style="font-size:0.6em;opacity:0.7;">(последние 10)</small></h2>

{% assign works = site.data.works | reverse | slice: 0, 10 %}

{% for work in works %}
<details {% if forloop.first %}open{% endif %}>
  <summary><h3>🔧 {{ work.title }}</h3></summary>
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
<p style="text-align: center; color: var(--text); opacity: 0.7;">Примеры работ скоро появятся...</p>
{% endif %}

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
  
  <div style="color: var(--text); font-size: 0.875rem; line-height: 1.6;">
    Разработка и сопровождение<br>
    <a href="tel:+375292065065" style="color: var(--btn-bg); text-decoration: none; font-weight: 600; font-size: 1rem;">📞 +375 29 2 065 065</a>
  </div>
  
  <div class="online-now">
    Сейчас онлайн: <span id="online-count">1</span>&nbsp;чел.
  </div>
</div>
