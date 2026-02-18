---
layout: default
title: Ремонт компьютерной и мобильной техники в Дрогичине
---

<style>
.contact-wrapper {
  max-width: 700px;
  margin: 2rem auto;
  padding: 0 1rem;
}

/* Блок мастера */
.master-card {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-bottom: 2rem;
  padding: 1.5rem;
  background: rgba(30, 41, 59, 0.4);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.master-photo {
  flex-shrink: 0;
}

.master-photo img {
  width: 130px;
  height: 130px;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid #dc2626;
  box-shadow: 0 4px 15px rgba(220, 38, 38, 0.3);
}

.master-name {
  margin: 0;
  font-size: 1.8rem;
  font-weight: 800;
  color: #ffffff;
  text-shadow: 0 2px 4px rgba(0,0,0,0.3);
}

.master-role {
  margin: 0.3rem 0 0 0;
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.8);
  font-style: italic;
}

/* Телефон */
.phone-card {
  margin-bottom: 2rem;
  padding: 1.2rem 1.5rem;
  background: rgba(220, 38, 38, 0.1);
  border: 1px solid rgba(220, 38, 38, 0.3);
  border-radius: 12px;
  text-align: center;
}

.phone-card a {
  font-size: 1.5rem;
  font-weight: 700;
  color: #dc2626;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.phone-card a:hover {
  color: #ef4444;
}

/* Адрес и здание */
.location-card {
  padding: 1.5rem;
  background: rgba(30, 41, 59, 0.4);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.address-header {
  font-size: 1.1rem;
  color: #ffffff;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.building-photo {
  margin: 1rem 0;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 8px 25px rgba(0,0,0,0.3);
  border: 2px solid rgba(255, 255, 255, 0.1);
}

.building-photo img {
  width: 100%;
  height: auto;
  display: block;
}

.maps-row {
  margin-top: 1rem;
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.maps-row a {
  padding: 0.6rem 1.2rem;
  background: rgba(255, 255, 255, 0.1);
  color: #ffffff;
  text-decoration: none;
  border-radius: 8px;
  font-size: 0.95rem;
  border: 1px solid rgba(255, 255, 255, 0.2);
  transition: all 0.2s;
}

.maps-row a:hover {
  background: rgba(220, 38, 38, 0.8);
  border-color: #dc2626;
}

/* Мобильная версия */
@media (max-width: 600px) {
  .master-card {
    flex-direction: column;
    text-align: center;
    gap: 1rem;
  }
  
  .master-photo img {
    width: 150px;
    height: 150px;
  }
  
  .master-name {
    font-size: 1.5rem;
  }
  
  .phone-card a {
    font-size: 1.3rem;
  }
}
</style>

<div class="contact-wrapper">
  <!-- Карточка мастера -->
  <div class="master-card">
    <div class="master-photo">
      <img src="{{ '/assets/images/alex.jpg' | relative_url }}" alt="Александр — мастер по ремонту">
    </div>
    <div class="master-info">
      <h2 class="master-name">Александр</h2>
      <p class="master-role">Мастер по ремонту</p>
    </div>
  </div>

  <!-- Телефон -->
  <div class="phone-card">
    <a href="tel:+375297256982">
      📞 +375 (29) 725-69-82
    </a>
  </div>

  <!-- Адрес и фото здания -->
  <div class="location-card">
    <div class="address-header">
      📍 <strong>г. Дрогичин, ул. Ленина, 141а</strong> (2 этаж)
    </div>
    
    <div class="building-photo">
      <img src="{{ '/assets/images/zdanie.JPG' | relative_url }}" alt="Здание мастерской">
    </div>
    
    <div class="maps-row">
      <a href="https://yandex.by/maps/-/CDXqaF8N" target="_blank" rel="noopener">🗺 Яндекс Карты</a>
      <a href="https://goo.gl/maps/..." target="_blank" rel="noopener">Google Maps</a>
    </div>
  </div>
</div>

## О нас

Решаю сложные случаи, от которых отказываются другие:

- Ремонт и настройка ПК и ноутбуков
- Разблокировка FRP, Google-аккаунты, Mi-Account
- Прошивка смартфонов
- Обновление карт — Navitel, IGO
