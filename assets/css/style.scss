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
  
  /* Увеличенная центрированная кнопка */
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
  
  /* Блок с фото мастера и здания */
  .photos-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 25px;
    margin: 1.5rem 0;
    align-items: start;
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
    color: var(--text-secondary);
    opacity: 0.8;
  }
  
  /* Ссылки под фото */
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
  
  /* Мобильная версия */
  @media (max-width: 768px) {
    .gallery-grid { grid-template-columns: 1fr; }
    .photos-row { 
      grid-template-columns: 1fr; 
      gap: 20px;
    }
    .photo-card img {
      height: 280px;
      object-position: center 40%;
    }
    .btn-large {
      max-width: 100%;
      margin: 1.5rem auto;
    }
  }
</style>

<button onclick="toggleTheme()" id="theme-toggle">🌙</button>

<script>
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
</script>

<h1>Ремонт компьютерной и мобильной техники в Дрогичине</h1>

<!-- Блок с фото -->
<div class="photos-row">
  <div class="photo-card">
    <img src="{{ '/assets/images/alex.jpg' | relative_url }}" alt="Александр - мастер по ремонту">
    <div class="photo-label">
      Александр<br>
      <small>Мастер по ремонту</small>
    </div>
    <div class="photo-links">
      💬 <a href="https://t.me/AlexDrog81">Telegram</a> • 
      <a href="viber://chat?number=375297256982">Viber</a>
    </div>
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

<!-- Кнопка прайса по центру широкая -->
<a href="./uslugi/" class="btn btn-large">Прайс и услуги</a>

<h2>Режим работы:</h2>

<p>
🕐 Пн-Пт: 10:00-18:00<br>
🕐 Обед: 12:00-13:00<br>
🕐 Сб-Вс: 10:00-14:00<br>
<span class="highlight">🕐 Понедельник: ВЫХОДНОЙ</span>
</p>

<h2>Примеры работ</h2>

<details open>
  <summary><h3>🔧 Замена термопасты в ноутбуке</h3></summary>
  <div class="gallery-grid">
    <div class="gallery-item">
      <div class="label-red">🔴 ДО</div>
      <img src="./assets/images/termopasta.jpg" alt="Перегрев">
      <p>Перегрев 95°C</p>
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="./assets/images/temp_posle.jpg" alt="После чистки">
      <p>65°C, тихая работа</p>
    </div>
  </div>
</details>

<details>
  <summary><h3>📱 Замена дисплейного модуля</h3></summary>
  <div class="gallery-grid">
    <div class="gallery-item">
      <div class="label-red">🔴 ДО</div>
      <img src="./assets/images/bitka.jpg" alt="Разбитый экран">
      <p>Разбитый экран</p>
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="./assets/images/bitka_pos.jpg" alt="Новый дисплей">
      <p>Новый дисплей</p>
    </div>
  </div>
</details>

<details>
  <summary><h3>🗺️ Обновление карт навигации</h3></summary>
  <div class="gallery-grid">
    <div class="gallery-item">
      <div class="label-red">🔴 ДО</div>
      <img src="./assets/images/igo_do.jpg" alt="Устаревшие карты">
      <p>Устаревшие карты</p>
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="./assets/images/igo_pos.jpg" alt="IGO 2025">
      <p>IGO 2025Q2</p>
    </div>
  </div>
</details>

<details>
  <summary><h3>🔓 Снятие Google аккаунта (FRP)</h3></summary>
  <div class="gallery-grid">
    <div class="gallery-item">
      <div class="label-red">🔴 ДО</div>
      <img src="./assets/images/frp.jpg" alt="Блокировка FRP">
      <p>Блокировка FRP</p>
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="./assets/images/frp_pos.jpg" alt="Разблокировано">
      <p>Полный доступ</p>
    </div>
  </div>
</details>

<details>
  <summary><h3>🔓 Снятие Mi аккаунта</h3></summary>
  <div class="gallery-grid">
    <div class="gallery-item">
      <div class="label-red">🔴 ДО</div>
      <img src="./assets/images/redmi9a.jpg" alt="Запрос пароля">
      <p>Запрос пароля</p>
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="./assets/images/redmi9a_posle.jpg" alt="Аккаунт удален">
      <p>Аккаунт удалён</p>
    </div>
  </div>
</details>

<details>
  <summary><h3>🛑 Убрать рекламу на смартфоне</h3></summary>
  <div class="gallery-grid">
    <div class="gallery-item">
      <div class="label-red">🔴 ДО</div>
      <img src="./assets/images/reklama.png" alt="Реклама">
      <p>Всплывающая реклама</p>
    </div>
    <div class="gallery-item">
      <div class="label-green">🟢 ПОСЛЕ</div>
      <img src="./assets/images/reklama_pos.png" alt="Чистая система">
      <p>Чистая система</p>
    </div>
  </div>
</details>

<h2>Почему обращаются ко мне</h2>

<p>
✅ <strong>Бесплатная диагностика</strong> — платишь только за ремонт<br>
✅ <strong>Гарантия</strong> — от 1 месяца на все виды работ<br>
✅ <strong>Быстро</strong> — большинство работ в день обращения<br>
✅ <strong>Сложные случаи</strong> — то, что отказались делать другие
</p>
