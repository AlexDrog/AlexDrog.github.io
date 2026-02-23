---
layout: default
---

<script>
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
    --bg: #f8fafc;
    --bg-card: #ffffff;
    --bg-secondary: #f1f5f9;
    --text: #334155;
    --text-secondary: #64748b;
    --heading: #0f172a;
    --border: #e2e8f0;
    --accent: #3b82f6;
    --success: #10b981;
    --shadow: rgba(0,0,0,0.04);
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
    --success: #34d399;
    --shadow: rgba(0,0,0,0.2);
  }
  
  body { 
    background-color: var(--bg) !important; 
    color: var(--text) !important;
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  }
  
  h1 { 
    color: var(--heading) !important; 
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }
  
  /* === БАННЕР АКЦИИ === */
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
  }
  
  .promo-banner.active { display: block; }
  
  .promo-label {
    display: block;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 8px;
    opacity: 0.9;
  }
  
  @keyframes promo-pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.02); box-shadow: 0 8px 30px rgba(0, 200, 83, 0.6); }
  }
  
  [data-theme="dark"] .promo-banner {
    background: linear-gradient(135deg, #00b248 0%, #76ff03 100%);
  }
  
  .photos-row { 
    display: grid; 
    grid-template-columns: 1fr 1fr; 
    gap: 25px; 
    margin: 1.5rem 0; 
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
    border: 3px solid var(--border);
  }
  
  .chat-avatar.online { border-color: var(--success); }
  .chat-avatar.offline { border-color: var(--text-secondary); }
  
  .chat-info { flex: 1; }
  
  .chat-name { 
    color: var(--heading); 
    font-weight: 600; 
    font-size: 1.05rem; 
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
  }
  
  .offline-dot {
    width: 8px;
    height: 8px;
    background: var(--text-secondary);
    border-radius: 50%;
  }
  
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.6; }
  }
  
  .work-status {
    text-align: center;
    margin-top: 8px;
    font-size: 0.9rem;
    color: var(--text-secondary);
  }
  
  .btn {
    display: block;
    width: 100%;
    max-width: 600px;
    margin: 2rem auto;
    padding: 16px 24px;
    background: linear-gradient(135deg, #3b82f6 0%, #6366f1 100%);
    color: white !important;
    border-radius: 12px;
    text-align: center;
    text-decoration: none;
    font-weight: 600;
  }
  
  @media (max-width: 768px) {
    .photos-row { grid-template-columns: 1fr; }
    .promo-banner { font-size: 1.2em; padding: 16px; }
    h1 { font-size: 1.35rem; }
    .chat-avatar { width: 56px; height: 56px; }
  }
</style>

<button onclick="toggleTheme()" id="theme-toggle" style="position: fixed; top: 15px; right: 15px; z-index: 9999; background: var(--bg-card); border: 1px solid var(--border); border-radius: 50%; width: 48px; height: 48px; font-size: 20px; cursor: pointer;">🌙</button>

<script>
  let customStatusData = null;

  // Проверка не истекла ли акция
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
        customStatusData = (data.active && data.text) ? data : null;
      } else {
        customStatusData = null;
      }
    } catch (e) {
      customStatusData = null;
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

  // Главная функция обновления всех статусов
  function updateAllStatuses() {
    const avatar = document.getElementById('chat-avatar');
    const statusText = document.getElementById('status-text');
    const promoBanner = document.getElementById('promo-banner');
    const promoText = document.getElementById('promo-text');
    const workStatus = document.getElementById('work-status-text');
    
    // ПРИОРИТЕТ 1: Акция дня (promo)
    if (isPromoActive()) {
      // Баннер
      promoText.textContent = customStatusData.text;
      promoBanner.classList.add('active');
      
      // Статус под аватаркой = В сети (зеленый) - даже если выходной!
      avatar.classList.remove('offline');
      avatar.classList.add('online');
      statusText.innerHTML = '<span class="online-dot"></span>В сети';
      statusText.className = 'chat-status status-online';
      
      // Текст под контактами
      workStatus.textContent = "🔥 Акция дня!";
      workStatus.style.color = '#00c853';
      workStatus.style.fontWeight = '700';
      
      return;
    }
    
    // Скрываем баннер если нет акции
    promoBanner.classList.remove('active');
    
    // ПРИОРИТЕТ 2: Другие кастомные статусы (выходной, отпуск и т.д.)
    if (customStatusData && customStatusData.active) {
      const schedule = checkWorkSchedule();
      
      // Для обычных статусов показываем реальный статус под аватаркой
      if (schedule.isOnline) {
        avatar.classList.remove('offline');
        avatar.classList.add('online');
        statusText.innerHTML = '<span class="online-dot"></span>В сети';
        statusText.className = 'chat-status status-online';
      } else {
        avatar.classList.remove('online');
        avatar.classList.add('offline');
        statusText.innerHTML = '<span class="offline-dot"></span>' + schedule.statusText;
        statusText.className = 'chat-status status-offline';
      }
      
      // Текст кастомного статуса
      workStatus.textContent = customStatusData.text;
      workStatus.style.color = '#dc2626';
      workStatus.style.fontWeight = '700';
      return;
    }
    
    // ПРИОРИТЕТ 3: Авто-режим по расписанию
    const schedule = checkWorkSchedule();
    
    if (schedule.isOnline) {
      avatar.classList.remove('offline');
      avatar.classList.add('online');
      statusText.innerHTML = '<span class="online-dot"></span>В сети';
      statusText.className = 'chat-status status-online';
    } else {
      avatar.classList.remove('online');
      avatar.classList.add('offline');
      statusText.innerHTML = '<span class="offline-dot"></span>' + schedule.statusText;
      statusText.className = 'chat-status status-offline';
    }
    
    workStatus.textContent = schedule.statusText;
    workStatus.style.color = schedule.isOnline ? 'var(--success)' : 'var(--text-secondary)';
    workStatus.style.fontWeight = '600';
  }

  document.addEventListener('DOMContentLoaded', async function() {
    // Тема
    const btn = document.getElementById('theme-toggle');
    const current = document.documentElement.getAttribute('data-theme');
    if (btn) btn.textContent = current === 'dark' ? '☀️' : '🌙';
    
    // Загружаем статус и обновляем всё
    await loadCustomStatus();
    updateAllStatuses();
    
    // Обновляем каждые 5 минут
    setInterval(async () => {
      await loadCustomStatus();
      updateAllStatuses();
    }, 300000);
    
    // И каждую минуту проверяем не истекла ли акция
    setInterval(() => {
      if (customStatusData && customStatusData.type === 'promo') {
        updateAllStatuses();
      }
    }, 60000);
  });
</script>

<h1>Ремонт компьютерной и мобильной техники в Дрогичине</h1>

<!-- Акция дня -->
<div id="promo-banner" class="promo-banner">
  <span class="promo-label">🎯 Акция дня</span>
  <span id="promo-text"></span>
</div>

<div class="photos-row">
  <div class="chat-container">
    <details class="chat-details">
      <summary class="chat-summary">
        <img src="{{ '/assets/images/alex.jpg' | relative_url }}" class="chat-avatar" id="chat-avatar" alt="Александр">
        <div class="chat-info">
          <div class="chat-name">Александр</div>
          <div class="chat-status" id="status-text">
            <span class="offline-dot"></span>Загрузка...
          </div>
        </div>
      </summary>
      <div style="padding: 0 20px 16px; display: flex; gap: 12px;">
        <a href="https://t.me/AlexDrog81" class="btn" style="flex: 1; font-size: 0.9rem; margin: 0;" target="_blank">📱 Telegram</a>
        <a href="viber://chat?number=375297256982" class="btn" style="flex: 1; font-size: 0.9rem; margin: 0; background: linear-gradient(135deg, #7360f2, #9b8af5) !important;">💬 Viber</a>
      </div>
    </details>
    
    <p class="work-status">
      Мастер по ремонту • <span id="work-status-text">Загрузка...</span>
    </p>
  </div>
  
  <div style="text-align: center;">
    <img src="{{ '/assets/images/zdanie.JPG' | relative_url }}" alt="Здание" style="width: 100%; height: 220px; object-fit: cover; border-radius: 16px;">
    <div style="margin-top: 0.5rem; color: var(--text-secondary); font-size: 0.9rem;">
      г. Дрогичин, ул. Ленина, 141а<br>2 этаж
    </div>
  </div>
</div>

<a href="./uslugi/" class="btn">📋 Прайс и услуги</a>
