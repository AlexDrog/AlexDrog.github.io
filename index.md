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
  
  /* Кнопка Прайс и услуги — в стиле услуг */
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
  
  /* Стиль для закреплённой работы */
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
    gap: 4px;
    background: var(--accent);
    color: white !important;
    padding: 4px 10px;
    border-radius: 20px;
    font-size: 0.75rem;
    font-weight: 700;
    margin-right: 8px;
    vertical-align: middle;
    text-transform: uppercase;
    letter-spacing: 0.5px;
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
  
  /* Исправление: убираем белый фон, оставляем только цвет текста */
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
  
  /* === МОБИЛЬНАЯ ВЕРСИЯ === */
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
    
    .chat-avatar { 
      width: 60px; 
      height: 60px; 
      min-width: 60px;
      min-height: 60px;
      flex-shrink: 0;
      aspect-ratio: 1 / 1;
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
      border-radius: 12px;
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
      padding: 14px 20px;
      font-size: 1rem;
    }
    
    details { padding: 12px; }
    summary h3 { font-size: 0.95rem; }
    
    .site-footer-stats { 
      margin: 2rem -1rem 0; 
      border-radius: 0; 
      border-left: none; 
      border-right: none;
      padding: 1.5rem 1rem;
    }
    
    /* Фикс для highlight на мобильной темной теме */
    .highlight {
      background: transparent !important;
      padding: 0;
      border-radius: 0;
    }
    
    .pinned-badge {
      font-size: 0.7rem;
      padding: 3px 6px;
      margin-right: 4px;
    }
  }
  
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
  // === УПРАВЛЕНИЕ ТЕКСТОМ "Принимаю заказы" ===
  const WORK_PHRASES = [
    "Принимаю заказы", "На связи прямо сейчас", "Готов помочь с ремонтом",
    "Жду вашего звонка", "Работаю сегодня", "Можно обращаться",
    "Свободен для заказов", "На рабочем месте", "Готов к работе",
    "Онлайн и доступен", "Звоните, отвечу", "Пишите в мессенджер",
    "Сейчас свободен", "Рабочий день в разгаре", "К вашим услугам",
    "Мастер на месте", "Готов выехать", "Принимаю вызовы",
    "На связи до вечера", "Диагностика доступна", "Ремонт сегодня возможен",
    "Консультирую бесплатно", "Отвечаю быстро", "Провожу диагностику",
    "Жду клиентов", "Срочный ремонт возможен", "Работаю без перерывов",
    "Техника будет работать", "Помогу сейчас", "Доступен для консультаций"
  ];

  // УТРО: до начала работы (7:00-10:00 в рабочие дни)
  const MORNING_PHRASES = [
    "Начинаю работу в 10:00", "Скоро буду на месте", "С 10:00 принимаю заказы",
    "Откроюсь через час", "Готовлюсь к работе", "Скоро на связи",
    "Завтракаю, с 10:00 работаю", "Начало рабочего дня в 10:00",
    "Скоро откроюсь", "Жду 10:00 чтобы начать", "Приходите с 10:00",
    "Уже еду в мастерскую", "Открытие в 10:00", "Скоро жду клиентов",
    "До открытия меньше часа", "С 10:00 жду вас", "Утренняя подготовка"
  ];

  // ВЕЧЕР: после работы (18:00-23:00 вт-пт, 14:00-23:00 сб-вс)
  const EVENING_PHRASES = [
    "Сегодня больше не работаю", "Завтра с 10:00 на месте", "Рабочий день окончен",
    "Увидимся завтра", "Сегодня закрыто", "Завтра буду на связи",
    "Приходите завтра", "Сегодня уже поздно", "Завтра с утра жду",
    "Вечерний перерыв", "Завтра решим", "До завтра с 10:00",
    "Сегодня отдыхаю", "Завтра в рабочем режиме", "Вечером не работаю",
    "Закончил на сегодня", "Возвращаюсь завтра", "Жду вас завтра"
  ];

  // НОЧЬ: 23:00-07:00
  const NIGHT_PHRASES = [
    "Ночной перерыв", "Сплю, отвечу утром", "Отдыхаю до рассвета",
    "Не беспокоить до утра", "Снова на связи с 10:00", "Ночь — время отдыха",
    "Утром отвечу", "До завтра", "Снова в деле с утра", "Ночь, отдыхаю"
  ];

  // ВЫХОДНОЙ: понедельник (и воскресенье после 18:00 если хочешь)
  const DAY_OFF_PHRASES = [
    "Сегодня выходной", "Отдыхаю сегодня", "Прием заказов с завтра",
    "Сегодня не работаю", "Выходной день", "Свободный день",
    "Завтра с 10:00 работаю", "Сегодня восстанавливаю силы",
    "Снова в деле завтра", "Сегодня лень работать", "Выходной!",
    "Сегодня семья, завтра работа", "Отдыхаю до вторника"
  ];

  let customStatusData = null;

  async function loadCustomStatus() {
    try {
      const response = await fetch('status.json?t=' + Date.now());
      if (response.ok) {
        const data = await response.json();
        if (data.active && data.text) {
          if (data.until) {
            const now = new Date();
            const parts = data.until.split('.');
            if (parts.length >= 2) {
              const day = parseInt(parts[0]);
              const month = parseInt(parts[1]) - 1;
              const year = parts[2] ? (parts[2].length === 2 ? 2000 + parseInt(parts[2]) : parseInt(parts[2])) : now.getFullYear();
              const untilDate = new Date(year, month, day, 23, 59);
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
    const day = now.getDay(); // 0=Вс, 1=Пн, 2=Вт, 3=Ср, 4=Чт, 5=Пт, 6=Сб
    const hour = now.getHours();
    
    // Ночь: 23:00-07:00 (во все дни)
    if (hour >= 23 || hour < 7) return 'night';
    
    // Понедельник - всегда выходной
    if (day === 1) return 'dayoff';
    
    // Вт-Пт: 10:00-18:00 работа
    if (day >= 2 && day <= 5) {
      if (hour < 10) return 'morning';
      if (hour >= 18) return 'evening';
      return 'work';
    }
    
    // Сб-Вс: 10:00-14:00 работа
    if (day === 0 || day === 6) {
      if (hour < 10) return 'morning';
      if (hour >= 14) return 'evening';
      return 'work';
    }
    
    return 'dayoff';
  }

  function updateWorkStatus() {
    const statusEl = document.getElementById('work-status-text');
    if (!statusEl) return;
    
    // Если есть кастомный статус из бота — показываем его КРАСНЫМ ЖИРНЫМ
    if (customStatusData && customStatusData.active) {
      statusEl.textContent = customStatusData.text;
      statusEl.style.color = '#dc2626';
      statusEl.style.fontWeight = '700';
      statusEl.style.fontSize = '0.95rem';
      return;
    }
    
    const period = getTimePeriod();
    let phrases;
    let color;
    let weight = '600';
    
    switch(period) {
      case 'work':
        phrases = WORK_PHRASES;
        color = 'var(--success)'; // зеленый
        break;
      case 'morning':
        phrases = MORNING_PHRASES;
        color = '#f59e0b'; // оранжевый/желтый - "скоро откроюсь"
        break;
      case 'evening':
        phrases = EVENING_PHRASES;
        color = 'var(--text-secondary)'; // серый
        break;
      case 'night':
        phrases = NIGHT_PHRASES;
        color = 'var(--text-secondary)'; // серый
        break;
      case 'dayoff':
        phrases = DAY_OFF_PHRASES;
        color = '#dc2626'; // красный для выходного
        weight = '700';
        break;
      default:
        phrases = WORK_PHRASES;
        color = 'var(--success)';
    }
    
    const phrase = phrases[Math.floor(Math.random() * phrases.length)];
    
    statusEl.textContent = phrase;
    statusEl.style.color = color;
    statusEl.style.fontWeight = weight;
    statusEl.style.fontSize = '0.9rem';
  }

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
    
    loadCustomStatus().then(updateWorkStatus);
    setInterval(async () => {
      await loadCustomStatus();
      updateWorkStatus();
    }, 300000);
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

<h2>Примеры работ <small style="font-size:0.6em;opacity:0.7;color:var(--text-secondary);">(последние 10)</small></h2>

{% assign works = site.data.works %}

{% for work in works limit:10 %}
<details {% if forloop.first %}open{% endif %} {% if work.pinned %}class="pinned" open{% endif %}>
  <summary>
    <h3>
      {% if work.pinned %}<span class="pinned-badge">📌 ЗАКРЕПЛЕНО</span>{% endif %}
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
