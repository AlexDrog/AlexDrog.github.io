---
layout: default
---

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
  }
  
  h1, h2, h3 { 
    color: var(--heading) !important; 
    border-color: var(--border) !important;
  }
  
  a { color: var(--link) !important; }
  
  .page-header {
    background: linear-gradient(120deg, #155799, #159957) !important;
  }
  
  .main-content {
    background: var(--bg) !important;
  }
  
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
  }
  
  summary h3 { 
    display: inline; 
    margin: 0;
  }
  
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
  
  .label-red { background: #e74c3c; color: white; padding: 8px; font-weight: bold; }
  .label-green { background: #27ae60; color: white; padding: 8px; font-weight: bold; }
  
  .gallery-item img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    display: block;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  
  .gallery-item img:hover {
    transform: scale(1.02);
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  }
  
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
  }
  
  .photos-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 25px;
    margin: 1.5rem 0;
    align-items: start;
  }
  
  .chat-container {
    width: 100%;
  }
  
  .chat-details {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 30px;
    overflow: hidden;
    transition: all 0.3s ease;
    box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  }
  
  .chat-details[open] {
    border-radius: 20px;
    box-shadow: 0 4px 16px rgba(0,0,0,0.12);
  }
  
  .chat-summary {
    display: flex;
    align-items: center;
    padding: 12px 20px;
    cursor: pointer;
    list-style: none;
    gap: 12px;
    user-select: none;
  }
  
  .chat-summary::-webkit-details-marker {
    display: none;
  }
  
  .chat-avatar {
    width: 64px;
    height: 64px;
    border-radius: 50%;
    object-fit: cover;
    object-position: center 30%;
    border: 3px solid var(--border);
    flex-shrink: 0;
    box-shadow: 0 2px 6px rgba(0,0,0,0.15);
    transition: border-color 0.3s;
  }
  
  .chat-avatar.online {
    border-color: #2ea44f;
    box-shadow: 0 2px 8px rgba(46, 164, 79, 0.3);
  }
  
  .chat-avatar.offline {
    border-color: #8b949e;
  }
  
  .chat-info {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 2px;
  }
  
  .chat-name {
    color: var(--heading);
    font-weight: 600;
    font-size: 1.05rem;
    line-height: 1.2;
  }
  
  .chat-status {
    font-size: 0.85rem;
    display: flex;
    align-items: center;
    gap: 6px;
    font-weight: 500;
  }
  
  .status-online {
    color: #2ea44f;
  }
  
  .status-offline {
    color: #8b949e;
  }
  
  .online-dot {
    width: 8px;
    height: 8px;
    background: #2ea44f;
    border-radius: 50%;
    display: inline-block;
    animation: pulse 2s infinite;
    box-shadow: 0 0 4px rgba(46, 164, 79, 0.5);
  }
  
  .offline-dot {
    width: 8px;
    height: 8px;
    background: #8b949e;
    border-radius: 50%;
    display: inline-block;
  }
  
  @keyframes pulse {
    0% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(0.9); }
    100% { opacity: 1; transform: scale(1); }
  }
  
  .chat-arrow {
    color: var(--text);
    transition: transform 0.3s;
    font-size: 1.2rem;
    opacity: 0.6;
  }
  
  .chat-details[open] .chat-arrow {
    transform: rotate(180deg);
  }
  
  .chat-options {
    display: flex;
    gap: 12px;
    padding: 0 20px 16px;
    margin-top: -5px;
  }
  
  .chat-btn {
    flex: 1;
    padding: 12px;
    border-radius: 24px;
    text-align: center;
    text-decoration: none;
    font-weight: 600;
    color: white !important;
    transition: all 0.2s;
    border: none;
    font-size: 0.95rem;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 6px;
  }
  
  .chat-btn.telegram {
    background: linear-gradient(135deg, #0088cc, #00a8e8);
  }
  
  .chat-btn.viber {
    background: linear-gradient(135deg, #7360f2, #9b8af5);
  }
  
  .chat-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  }
  
  .photo-card {
    text-align: center;
  }
  
  .photo-card img {
    width: 100%;
    height: 320px;
    object-fit: cover;
    object-position: center 40%;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
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
  
  .photo-label small {
    font-weight: 400;
    color: var(--text);
    opacity: 0.7;
  }
  
  .photo-links {
    margin-top: 0.8rem;
    font-size: 0.95rem;
    line-height: 1.6;
  }
  
  .photo-links a {
    color: var(--link);
    text-decoration: none;
  }
  
  .photo-links a:hover {
    text-decoration: underline;
  }
  
  .site-footer-stats {
    margin-top: 4rem;
    padding: 2rem;
    text-align: center;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  }
  
  .metrika-informer {
    display: inline-block;
    margin-bottom: 1rem;
    padding: 8px;
    background: var(--bg);
    border-radius: 8px;
    border: 1px solid var(--border);
    transition: transform 0.2s;
  }
  
  .metrika-informer:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }
  
  .metrika-informer img {
    display: block;
    border-radius: 4px;
  }
  
  .footer-text {
    color: var(--text-secondary);
    font-size: 0.875rem;
    line-height: 1.6;
  }
  
  .footer-phone {
    display: inline-block;
    margin-top: 8px;
    color: var(--btn-bg);
    text-decoration: none;
    font-weight: 600;
    font-size: 1rem;
    transition: all 0.3s;
  }
  
  .footer-phone:hover {
    color: var(--link);
    transform: scale(1.05);
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
  
  #online-count {
    color: #2ea44f;
    font-weight: 700;
    font-size: 1.1rem;
    min-width: 20px;
  }
  
  .online-now::before {
    content: "";
    width: 8px;
    height: 8px;
    background: #2ea44f;
    border-radius: 50%;
    animation: pulse 2s infinite;
    flex-shrink: 0;
  }
  
  .site-footer {
    display: none !important;
  }
  
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
    cursor: zoom-out;
    backdrop-filter: blur(10px);
  }
  
  .lightbox-overlay.active {
    display: flex;
  }
  
  .lightbox-container {
    position: relative;
    max-width: 95%;
    max-height: 95%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .lightbox-img {
    max-width: 100%;
    max-height: 85vh;
    object-fit: contain;
    border-radius: 8px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.5);
  }
  
  .lightbox-caption {
    color: white;
    margin-top: 15px;
    font-size: 1.1rem;
    text-align: center;
    padding: 0 20px;
    text-shadow: 0 2px 4px rgba(0,0,0,0.8);
  }
  
  .lightbox-close {
    position: absolute;
    top: -50px;
    right: 0;
    color: white;
    font-size: 3rem;
    cursor: pointer;
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0.8;
    transition: opacity 0.3s;
    z-index: 10001;
    line-height: 1;
  }
  
  .lightbox-close:hover {
    opacity: 1;
  }
  
  .lightbox-nav {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    color: white;
    font-size: 3rem;
    cursor: pointer;
    padding: 20px;
    opacity: 0.6;
    transition: opacity 0.3s;
    user-select: none;
    font-weight: bold;
  }
  
  .lightbox-nav:hover {
    opacity: 1;
  }
  
  .lightbox-prev { left: 20px; }
  .lightbox-next { right: 20px; }
  
  @media (max-width: 768px) {
    .gallery-grid { grid-template-columns: 1fr; }
    .photos-row { 
      grid-template-columns: 1fr; 
      gap: 20px;
    }
    .chat-avatar {
      width: 56px;
      height: 56px;
      object-position: center 30%;
    }
    .chat-name {
      font-size: 0.95rem;
    }
    .chat-status {
      font-size: 0.8rem;
    }
    .chat-options {
      flex-direction: column;
      gap: 8px;
    }
    .photo-card img {
      height: 280px;
    }
    .btn-large {
      max-width: 100%;
      margin: 1.5rem auto;
    }
    .site-footer-stats {
      margin-top: 2rem;
      padding: 1.5rem 1rem;
      margin-left: -1rem;
      margin-right: -1rem;
      border-radius: 0;
      border-left: none;
      border-right: none;
    }
    .lightbox-nav { 
      display: none; 
    }
    .lightbox-caption { 
      font-size: 0.9rem; 
    }
    .lightbox-close {
      top: -40px;
      font-size: 2.5rem;
    }
    .online-now {
      font-size: 0.85rem;
      padding: 6px 12px;
    }
    #online-count {
      font-size: 1rem;
    }
  }
</style>

<button onclick="toggleTheme()" id="theme-toggle">🌙</button>

<script type="module">
  // === FIREBASE: РЕАЛЬНЫЙ СЧЁТЧИК ОНЛАЙН-ПОСЕТИТЕЛЕЙ ===
  const firebaseConfig = {
    apiKey: "AIzaSyDgSGIhDkfu1_l0Ryg0MeiLfVxp-lgiSsU",
    authDomain: "alexdrog.firebaseapp.com",
    databaseURL: "https://alexdrog-default-rtdb.europe-west1.firebasedatabase.app ",
    projectId: "alexdrog",
    storageBucket: "alexdrog.firebasestorage.app",
    messagingSenderId: "33899135860",
    appId: "1:33899135860:web:396df092035fb19a11a221",
    measurementId: "G-KJ7JQ8R476"
  };

  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js ";
  import { getDatabase, ref, set, onDisconnect, onValue, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js ";

  const app = initializeApp(firebaseConfig);
  const db = getDatabase(app);
  
  const sessionId = Date.now() + '_' + Math.random().toString(36).substr(2, 9);
  const userRef = ref(db, 'online/' + sessionId);
  
  set(userRef, {
    timestamp: serverTimestamp()
  });
  
  onDisconnect(userRef).remove();
  
  const onlineRef = ref(db, 'online');
  onValue(onlineRef, (snapshot) => {
    const count = snapshot.size;
    const counterElement = document.getElementById('online-count');
    if (counterElement) {
      counterElement.textContent = count;
      counterElement.style.transform = 'scale(1.3)';
      setTimeout(() => {
        counterElement.style.transform = 'scale(1)';
      }, 200);
    }
  });
</script>

<script>
  // === ОПРЕДЕЛЕНИЕ ОНЛАЙН-СТАТУСА МАСТЕРА ПО РАСПИСАНИЮ ===
  function checkOnlineStatus() {
    const now = new Date();
    const day = now.getDay(); // 0=Вс, 1=Пн, 2=Вт, 3=Ср, 4=Чт, 5=Пт, 6=Сб
    const hour = now.getHours();
    const minute = now.getMinutes();
    const time = hour + minute / 60;
    
    let isOnline = false;
    let statusText = "";
    
    if (day === 1) {
      // Понедельник - всегда выходной
      isOnline = false;
      statusText = "Сегодня выходной, отвечу завтра с 10:00";
    }
    else if (day >= 2 && day <= 5) {
      // Вторник-пятница: 10:00-18:00 (обед 12:00-13:00)
      if (time >= 10 && time < 12) {
        isOnline = true;
        statusText = "В сети";
      } else if (time >= 13 && time < 18) {
        isOnline = true;
        statusText = "В сети";
      } else if (time >= 12 && time < 13) {
        isOnline = false;
        statusText = "Обеденный перерыв до 13:00";
      } else if (time < 10) {
        // Утро перед началом работы - сегодня ещё будет работа
        isOnline = false;
        statusText = "Начинаю работу сегодня в 10:00";
      } else {
        // После 18:00
        isOnline = false;
        if (day === 5) {
          // Пятница вечер → следующий рабочий день суббота
          statusText = "Отвечу завтра (суббота) с 10:00";
        } else {
          // Вт-Чт вечер → завтра
          statusText = "Отвечу завтра с 10:00";
        }
      }
    }
    else if (day === 6) {
      // Суббота: 10:00-14:00
      if (time >= 10 && time < 14) {
        isOnline = true;
        statusText = "В сети";
      } else if (time < 10) {
        isOnline = false;
        statusText = "Начинаю работу сегодня в 10:00";
      } else {
        // После 14:00 в субботу → воскресенье
        isOnline = false;
        statusText = "Отвечу завтра (воскресенье) с 10:00";
      }
    }
    else if (day === 0) {
      // Воскресенье: 10:00-14:00
      if (time >= 10 && time < 14) {
        isOnline = true;
        statusText = "В сети";
      } else if (time < 10) {
        isOnline = false;
        statusText = "Начинаю работу сегодня в 10:00";
      } else {
        // После 14:00 в воскресенье → понедельник выходной → вторник
        isOnline = false;
        statusText = "Отвечу во вторник с 10:00";
      }
    }
    
    return { isOnline, statusText };
  }
  
  document.addEventListener('DOMContentLoaded', function() {
    const status = checkOnlineStatus();
    const avatar = document.getElementById('chat-avatar');
    const dot = document.getElementById('status-dot');
    const text = document.getElementById('status-text');
    
    if (avatar && dot && text) {
      if (status.isOnline) {
        avatar.classList.add('online');
        avatar.classList.remove('offline');
        dot.className = 'online-dot';
        text.className = 'chat-status status-online';
      } else {
        avatar.classList.add('offline');
        avatar.classList.remove('online');
        dot.className = 'offline-dot';
        text.className = 'chat-status status-offline';
      }
      text.innerHTML = '<span id="status-dot" class="' + (status.isOnline ? 'online-dot' : 'offline-dot') + '"></span>' + status.statusText;
    }
  });
  
  function toggleTheme() {
    const html = document.documentElement;
    const isDark = html.getAttribute('data-theme') === 'dark';
    const newTheme = isDark ? 'light' : 'dark';
    html.setAttribute('data-theme', newTheme);
    localStorage.setItem('theme', newTheme);
    document.getElementById('theme-toggle').textContent = newTheme === 'dark' ? '☀️' : '🌙';
  }
  
  const saved = localStorage.getItem('theme');
  if (saved) {
    document.documentElement.setAttribute('data-theme', saved);
    document.getElementById('theme-toggle').textContent = saved === 'dark' ? '☀️' : '🌙';
  } else if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
    document.documentElement.setAttribute('data-theme', 'dark');
    document.getElementById('theme-toggle').textContent = '☀️';
  }
  
  let currentImageIndex = 0;
  let currentGalleryImages = [];
  
  function openLightbox(imgElement) {
    const overlay = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightbox-img');
    const caption = document.getElementById('lightbox-caption');
    
    const details = imgElement.closest('details');
    currentGalleryImages = details ? details.querySelectorAll('.gallery-item img') : [];
    currentImageIndex = Array.from(currentGalleryImages).indexOf(imgElement);
    
    lightboxImg.src = imgElement.src;
    caption.textContent = imgElement.alt || '';
    overlay.classList.add('active');
    document.body.style.overflow = 'hidden';
  }
  
  function closeLightbox(event) {
    if (event && event.target !== event.currentTarget && !event.target.classList.contains('lightbox-close')) return;
    
    const overlay = document.getElementById('lightbox');
    overlay.classList.remove('active');
    document.body.style.overflow = '';
  }
  
  function changeImage(direction) {
    if (currentGalleryImages.length === 0) return;
    
    currentImageIndex += direction;
    
    if (currentImageIndex >= currentGalleryImages.length) {
      currentImageIndex = 0;
    } else if (currentImageIndex < 0) {
      currentImageIndex = currentGalleryImages.length - 1;
    }
    
    const img = currentGalleryImages[currentImageIndex];
    document.getElementById('lightbox-img').src = img.src;
    document.getElementById('lightbox-caption').textContent = img.alt || '';
  }
  
  document.addEventListener('keydown', function(e) {
    const overlay = document.getElementById('lightbox');
    if (!overlay.classList.contains('active')) return;
    
    if (e.key === 'Escape') closeLightbox();
    if (e.key === 'ArrowLeft') changeImage(-1);
    if (e.key === 'ArrowRight') changeImage(1);
  });
  
  document.addEventListener('click', function(e) {
    if (e.target.matches('.gallery-item img')) {
      e.preventDefault();
      openLightbox(e.target);
    }
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
            <span class="online-dot" id="status-dot"></span>
            В сети
          </div>
        </div>
        <span class="chat-arrow">↓</span>
      </summary>
      <div class="chat-options">
        <a href="https://t.me/AlexDrog81 " class="chat-btn telegram" target="_blank">
          📱 Telegram
        </a>
        <a href="viber://chat?number=375297256982" class="chat-btn viber">
          💬 Viber
        </a>
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
      🗺️ <a href="https://yandex.ru/maps/?text=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0 ">Яндекс Карты</a> • 
      <a href="https://www.google.com/maps/search/?api=1&query=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0 ">Google Maps</a>
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
      <img src="{{ work.before_img | relative_url }}" alt="До ремонта: {{ work.title }}">
      <p>{{ work.desc_before | default: "До ремонта" }}</p>
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="{{ work.after_img | relative_url }}" alt="После ремонта: {{ work.title }}">
      <p>{{ work.desc_after | default: "После ремонта" }}</p>
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

<div id="lightbox" class="lightbox-overlay" onclick="closeLightbox(event)">
  <div class="lightbox-container" onclick="event.stopPropagation()">
    <span class="lightbox-close" onclick="closeLightbox()">&times;</span>
    <span class="lightbox-nav lightbox-prev" onclick="changeImage(-1)">&#10094;</span>
    <img id="lightbox-img" class="lightbox-img" src="" alt="">
    <span class="lightbox-nav lightbox-next" onclick="changeImage(1)">&#10095;</span>
    <div id="lightbox-caption" class="lightbox-caption"></div>
  </div>
</div>

<div class="site-footer-stats">
  <div class="metrika-informer">
    <a href="https://metrika.yandex.ru/stat/?id=106913790&from=informer " target="_blank" rel="nofollow">
      <img src="https://informer.yandex.ru/informer/106913790/3_1_FFFFFFFF_EFEFEFFF_0_pageviews " 
           style="width:88px; height:31px; border:0;" 
           alt="Яндекс.Метрика" 
           title="Сейчас онлайн: посетителей / просмотров за сегодня" />
    </a>
  </div>
  
  <div class="footer-text">
    Разработка и сопровождение<br>
    <a href="tel:+375292065065" class="footer-phone">📞 +375 29 2 065 065</a>
  </div>
  
  <div class="online-now" title="Количество посетителей на сайте прямо сейчас">
    Сейчас онлайн: <span id="online-count">1</span>&nbsp;чел.
  </div>
</div>
