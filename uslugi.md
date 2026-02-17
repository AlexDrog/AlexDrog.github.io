---
layout: default
title: Услуги и цены
---

# 📋 Прайс-лист

**📍 г. Дрогичин, ул. Ленина, 141 а (2 этаж)** | **📞 [+375 (29) 725-69-82](tel:+375297256982)**

---
<h2>🖥️ SOFT</h2>
<table class="price-table">
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.soft %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>🖥️ Компьютеры и ноутбуки</h2>
<table class="price-table">
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.computers %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>📱 Смартфоны и планшеты</h2>
<table class="price-table">
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.phones %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2>🗺️ Навигаторы</h2>
<table class="price-table">
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.navigators %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

---

💡 **Бесплатная диагностика — платишь только за ремонт!**

**[← На главную](./)** | **[Записаться в Telegram](https://t.me/alexdrog81)** | **[📞 Позвонить](tel:+375297256982)**
