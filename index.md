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
    padding: 8px 16px;
    margin: 5px 5px 5px 0;
    background-color: var(--btn-bg) !important;
    color: var(--btn-color) !important;
    border-radius: 6px;
    text-decoration: none;
    font-weight: 600;
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
  
  /* Стили для фото мастера (без фона, круглое) */
  .master-photo {
    text-align: center;
    margin: 1.5rem 0 1rem 0;
  }
  
  .master-photo img {
    width: 160px;
    height: 160px;
    object-fit: cover;
    border-radius: 50%;
    border: 3px solid var(--border);
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    display: block;
    margin: 0 auto;
  }
  
  /* Стили для фото здания */
  .building-photo {
    margin: 1rem 0;
    text-align: center;
  }
  
  .building-photo img {
    max-width: 100%;
    width: 450px;
    height: auto;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    display: block;
    margin: 0 auto;
  }
  
  @media (max-width: 600px) {
    .gallery-grid { grid-template-columns: 1fr; }
    .building-photo img { width: 100%; }
    .master-photo img { width: 140px; height: 140px; }
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

<h3>📞 <a href="tel:+375297256982">+375 (29) 725-69-82</a></h3>

<!-- Фото мастера (без фона, круглое) -->
<div class="master-photo">
  <img src="{{ '/assets/images/alex.jpg' | relative_url }}" alt="Александр - мастер по ремонту">
</div>

<p><strong>Александр</strong><br>
<em>Мастер по ремонту</em></p>

<p>📍 <strong><a href="https://yandex.ru/maps/?text=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0 ">г. Дрогичин, ул. Ленина, 141 а</a></strong> (2 этаж)</p>

<!-- Фото здания -->
<div class="building-photo">
  <img src="{{ '/assets/images/zdanie.JPG' | relative_url }}" alt="Здание мастерской">
</div>

<p>🗺️ <a href="https://yandex.ru/maps/?text=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0 ">Яндекс Карты</a> • 
<a href="https://www.google.com/maps/search/?api=1&query=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0 ">Google Maps</a></p>

<p>💬 <a href="https://t.me/AlexDrog81 ">Telegram</a> • 
<a href="viber://chat?number=375297256982">Viber</a></p>

<hr>

<p><strong>Решаю сложные случаи, от которых отказываются другие.</strong></p>

<ul>
  <li><strong>Ремонт и настройка ПК и ноутбуков</strong> — замена разъёмов, установка ОС и драйверов</li>
  <li><strong>Разблокировка</strong> — FRP, Google-аккаунты, Mi-Account, Huawei ID</li>
  <li><strong>Прошивка</strong> — смартфоны, восстановление «кирпичей»</li>
  <li><strong>Обновление карт</strong> — Navitel, IGO (весь мир)</li>
  <li><strong>Чистка ноутбуков</strong> — от пыли с заменой термопасты, термовкладок</li>
</ul>

<p>
  <a href="./uslugi/" class="btn">Прайс и услуги</a>
  <a href="https://t.me/AlexDrog81 " class="btn">Telegram</a>
  <a href="tel:+375297256982" class="btn">Позвонить</a>
</p>

<h2>📍 Адрес и режим работы</h2>

<p><strong>г. Дрогичин, ул. Ленина, 141 а</strong> (второй этаж)</p>

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
