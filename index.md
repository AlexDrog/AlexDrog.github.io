---
layout: default
---

&lt;!-- ПЕРЕКЛЮЧАТЕЛЬ ТЕМЫ --&gt;
&lt;button onclick="toggleTheme()" id="theme-toggle" style="position:fixed;top:15px;right:15px;z-index:9999;background:var(--btn-bg);color:var(--btn-color);border:1px solid var(--border);border-radius:50%;width:45px;height:45px;font-size:20px;cursor:pointer;box-shadow:0 2px 10px rgba(0,0,0,0.3);transition:all 0.3s;"&gt;🌙&lt;/button&gt;

&lt;!-- СТИЛИ --&gt;
&lt;style&gt;
:root {
  --bg: #ffffff;
  --text: #24292e;
  --heading: #1a1a1a;
  --link: #0366d6;
  --border: #e1e4e8;
  --card: #f6f8fa;
  --btn-bg: #2ea44f;
  --btn-color: #ffffff;
  --shadow: rgba(0,0,0,0.1);
}

[data-theme="dark"] {
  --bg: #0d1117;
  --text: #c9d1d9;
  --heading: #e6edf3;
  --link: #58a6ff;
  --border: #30363d;
  --card: #161b22;
  --btn-bg: #238636;
  --btn-color: #ffffff;
  --shadow: rgba(0,0,0,0.5);
}

* { transition: background-color 0.3s, color 0.3s, border-color 0.3s; }

body { background-color: var(--bg) !important; color: var(--text) !important; }

h1, h2, h3 { color: var(--heading) !important; margin-top: 24px; margin-bottom: 16px; }
h1 { border-bottom: 1px solid var(--border); padding-bottom: 10px; }

a { color: var(--link) !important; text-decoration: none; }
a:hover { text-decoration: underline; opacity: 0.8; }

.btn {
  display: inline-block;
  padding: 8px 16px;
  margin: 5px 5px 5px 0;
  background-color: var(--btn-bg) !important;
  color: var(--btn-color) !important;
  border-radius: 6px;
  border: 1px solid var(--border);
  font-weight: 600;
}

details {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 12px;
  margin-bottom: 12px;
  box-shadow: 0 1px 3px var(--shadow);
}

summary {
  color: var(--heading);
  font-weight: 600;
  cursor: pointer;
  user-select: none;
}

summary:hover { color: var(--link); }

details[open] summary { margin-bottom: 10px; }

.gallery-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
}

.gallery-item { text-align: center; }

.gallery-item .label {
  padding: 8px;
  font-weight: bold;
  border-radius: 4px 4px 0 0;
  color: white;
}

.label-red { background: #e74c3c; }
.label-green { background: #27ae60; }

.gallery-item img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-radius: 0 0 4px 4px;
  display: block;
}

.gallery-item p { 
  margin: 5px 0 0 0; 
  font-size: 0.9em; 
  color: var(--text);
  opacity: 0.8;
}

ul { padding-left: 20px; }
li { margin-bottom: 8px; line-height: 1.6; }

.work-time { margin: 20px 0; }
.work-time p { margin: 5px 0; }

.highlight { color: #e94560; font-weight: bold; }

@media (max-width: 600px) {
  .gallery-grid { grid-template-columns: 1fr; }
  h1 { font-size: 1.5em; }
}
&lt;/style&gt;

&lt;!-- СКРИПТ --&gt;
&lt;script&gt;
function toggleTheme() {
  const html = document.documentElement;
  const isDark = html.getAttribute('data-theme') === 'dark';
  const newTheme = isDark ? 'light' : 'dark';
  html.setAttribute('data-theme', newTheme);
  localStorage.setItem('theme', newTheme);
  document.getElementById('theme-toggle').textContent = newTheme === 'dark' ? '☀️' : '🌙';
}

// Проверка сохраненной темы или системной
const saved = localStorage.getItem('theme');
if (saved) {
  document.documentElement.setAttribute('data-theme', saved);
  document.getElementById('theme-toggle').textContent = saved === 'dark' ? '☀️' : '🌙';
} else if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
  document.documentElement.setAttribute('data-theme', 'dark');
  document.getElementById('theme-toggle').textContent = '☀️';
}
&lt;/script&gt;

# Ремонт компьютерной и мобильной техники в Дрогичине

### 📞 [+375 (29) 725-69-82](tel:+375297256982)

**Александр**  
*Мастер по ремонту*

📍 **[г. Дрогичин, ул. Ленина, 141 а](https://yandex.ru/maps/?text=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0)** (2 этаж)

🗺️ [Яндекс Карты](https://yandex.ru/maps/?text=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0) • [Google Maps](https://www.google.com/maps/search/?api=1&query=%D0%B3.%20%D0%94%D1%80%D0%BE%D0%B3%D0%B8%D1%87%D0%B8%D0%BD%2C%20%D1%83%D0%BB.%20%D0%9B%D0%B5%D0%BD%D0%B8%D0%BD%D0%B0%2C%20141%20%D0%B0)

💬 [Telegram](https://t.me/AlexDrog81) • [Viber](viber://chat?number=375297256982)

---

**Решаю сложные случаи, от которых отказываются другие.**

- **Ремонт и настройка ПК и ноутбуков** — замена разъёмов, установка ОС и драйверов
- **Разблокировка** — FRP, Google-аккаунты, Mi-Account, Huawei ID
- **Прошивка** — смартфоны, восстановление «кирпичей»
- **Обновление карт** — Navitel, IGO (весь мир)
- **Чистка ноутбуков** — от пыли с заменой термопасты, термовкладок

&lt;p&gt;
&lt;a href="./uslugi/" class="btn"&gt;Прайс и услуги&lt;/a&gt;
&lt;a href="https://t.me/AlexDrog81" class="btn"&gt;Telegram&lt;/a&gt;
&lt;a href="tel:+375297256982" class="btn"&gt;Позвонить&lt;/a&gt;
&lt;/p&gt;

---

## 📍 Адрес и режим работы

**г. Дрогичин, ул. Ленина, 141 а** (второй этаж)

&lt;div class="work-time"&gt;
🕐 Пн-Пт: 10:00-18:00  
🕐 Обед: 12:00-13:00  
🕐 Сб-Вс: 10:00-14:00  
&lt;span class="highlight"&gt;🕐 Понедельник: ВЫХОДНОЙ&lt;/span&gt;
&lt;/div&gt;

## Примеры работ

&lt;details open markdown="0"&gt;&lt;summary&gt;&lt;h3 style="display:inline; cursor:pointer;"&gt;🔧 Замена термопасты в ноутбуке&lt;/h3&gt;&lt;/summary&gt;&lt;div class="gallery-grid"&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-red"&gt;🔴 ДО&lt;/div&gt;&lt;a href="#t1"&gt;&lt;img src="./assets/images/termopasta.jpg" alt="Перегрев"&gt;&lt;/a&gt;&lt;p&gt;Перегрев 95°C&lt;/p&gt;&lt;/div&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-green"&gt;🟢 ПОСЛЕ&lt;/div&gt;&lt;a href="#t2"&gt;&lt;img src="./assets/images/temp_posle.jpg" alt="После чистки"&gt;&lt;/a&gt;&lt;p&gt;65°C, тихая работа&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;&lt;/details&gt;

&lt;details markdown="0"&gt;&lt;summary&gt;&lt;h3 style="display:inline; cursor:pointer;"&gt;📱 Замена дисплейного модуля&lt;/h3&gt;&lt;/summary&gt;&lt;div class="gallery-grid"&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-red"&gt;🔴 ДО&lt;/div&gt;&lt;a href="#d1"&gt;&lt;img src="./assets/images/bitka.jpg" alt="Разбитый экран"&gt;&lt;/a&gt;&lt;p&gt;Разбитый экран&lt;/p&gt;&lt;/div&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-green"&gt;🟢 ПОСЛЕ&lt;/div&gt;&lt;a href="#d2"&gt;&lt;img src="./assets/images/bitka_pos.jpg" alt="Новый дисплей"&gt;&lt;/a&gt;&lt;p&gt;Новый дисплей&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;&lt;/details&gt;

&lt;details markdown="0"&gt;&lt;summary&gt;&lt;h3 style="display:inline; cursor:pointer;"&gt;🗺️ Обновление карт навигации&lt;/h3&gt;&lt;/summary&gt;&lt;div class="gallery-grid"&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-red"&gt;🔴 ДО&lt;/div&gt;&lt;a href="#n1"&gt;&lt;img src="./assets/images/igo_do.jpg" alt="Устаревшие карты"&gt;&lt;/a&gt;&lt;p&gt;Устаревшие карты&lt;/p&gt;&lt;/div&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-green"&gt;🟢 ПОСЛЕ&lt;/div&gt;&lt;a href="#n2"&gt;&lt;img src="./assets/images/igo_pos.jpg" alt="IGO 2025"&gt;&lt;/a&gt;&lt;p&gt;IGO 2025Q2&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;&lt;/details&gt;

&lt;details markdown="0"&gt;&lt;summary&gt;&lt;h3 style="display:inline; cursor:pointer;"&gt;🔓 Снятие Google аккаунта (FRP)&lt;/h3&gt;&lt;/summary&gt;&lt;div class="gallery-grid"&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-red"&gt;🔴 ДО&lt;/div&gt;&lt;a href="#g1"&gt;&lt;img src="./assets/images/frp.jpg" alt="Блокировка FRP"&gt;&lt;/a&gt;&lt;p&gt;Блокировка FRP&lt;/p&gt;&lt;/div&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-green"&gt;🟢 ПОСЛЕ&lt;/div&gt;&lt;a href="#g2"&gt;&lt;img src="./assets/images/frp_pos.jpg" alt="Разблокировано"&gt;&lt;/a&gt;&lt;p&gt;Полный доступ&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;&lt;/details&gt;

&lt;details markdown="0"&gt;&lt;summary&gt;&lt;h3 style="display:inline; cursor:pointer;"&gt;🔓 Снятие Mi аккаунта&lt;/h3&gt;&lt;/summary&gt;&lt;div class="gallery-grid"&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-red"&gt;🔴 ДО&lt;/div&gt;&lt;a href="#m1"&gt;&lt;img src="./assets/images/redmi9a.jpg" alt="Запрос пароля"&gt;&lt;/a&gt;&lt;p&gt;Запрос пароля&lt;/p&gt;&lt;/div&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-green"&gt;🟢 ПОСЛЕ&lt;/div&gt;&lt;a href="#m2"&gt;&lt;img src="./assets/images/redmi9a_posle.jpg" alt="Аккаунт удален"&gt;&lt;/a&gt;&lt;p&gt;Аккаунт удалён&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;&lt;/details&gt;

&lt;details markdown="0"&gt;&lt;summary&gt;&lt;h3 style="display:inline; cursor:pointer;"&gt;🛑 Убрать рекламу на смартфоне&lt;/h3&gt;&lt;/summary&gt;&lt;div class="gallery-grid"&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-red"&gt;🔴 ДО&lt;/div&gt;&lt;a href="#a1"&gt;&lt;img src="./assets/images/reklama.png" alt="Реклама"&gt;&lt;/a&gt;&lt;p&gt;Всплывающая реклама&lt;/p&gt;&lt;/div&gt;&lt;div class="gallery-item"&gt;&lt;div class="label label-green"&gt;🟢 ПОСЛЕ&lt;/div&gt;&lt;a href="#a2"&gt;&lt;img src="./assets/images/reklama_pos.png" alt="Чистая система"&gt;&lt;/a&gt;&lt;p&gt;Чистая система&lt;/p&gt;&lt;/div&gt;&lt;/div&gt;&lt;/details&gt;

## Почему обращаются ко мне

✅ **Бесплатная диагностика** — платишь только за ремонт  
✅ **Гарантия** — от 1 месяца на все виды работ  
✅ **Быстро** — большинство работ в день обращения  
✅ **Сложные случаи** — то, что отказались делать другие
