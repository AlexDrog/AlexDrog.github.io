---
layout: default
title: Услуги и цены
---

# 📋 Прайс-лист

**📍 г. Дрогичин, ул. Ленина, 141 а** | **📞 [+375 (29) 725-69-82](tel:+375297256982)**

---

<h2 id="soft">💿 Программное обеспечение</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.soft %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="computers">🖥️ Компьютеры и ноутбуки</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.computers %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="phones">📱 Смартфоны и планшеты</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.phones %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="auto">🗺️ Навигаторы и автоэлектроника</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.navigators %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="network">🌐 Сети и интернет</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Срок</th></tr>
{% for item in site.data.prices.network %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="printers">🖨️ Принтеры и МФУ</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.printers %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="recovery">💾 Восстановление данных</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
{% for item in site.data.prices.recovery %}<tr><td>{{ item.name }}</td><td><strong>{{ item.price }}</strong></td><td>{{ item.note }}</td></tr>{% endfor %}
</table>

<h2 id="other">🔧 Прочие услуги</h2>
<table class="price-table"><colgroup><col style="width:50%"><col style="width:25%"><col style="width:25%"></colgroup>
<tr><th>Услуга</th><th>Цена</th><th>Примечание</th></tr>
<tr><td>Ремонт зарядных устройств</td><td><strong>от 25 BYN</strong></td><td>LiitoKala и др.</td></tr>
<tr><td>Пайка разъемов Type-C</td><td><strong>от 40 BYN</strong></td><td>Микроскоп</td></tr>
<tr><td>Удаленная помощь</td><td><strong>от 15 BYN</strong></td><td>30 мин</td></tr>
</table>

---

💡 **Бесплатная диагностика — платишь только за ремонт!**

**[← На главную](./)** | **[💬 Telegram](https://t.me/alexdrog81)** | **[📞 Позвонить](tel:+375297256982)**
