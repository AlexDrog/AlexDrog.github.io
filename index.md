.page-header {
  background: 
    linear-gradient(rgba(26, 26, 46, 0.85), rgba(22, 33, 62, 0.9)), 
    url('/assets/images/zdanie.JPG?v=5');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  padding: 2rem 1rem 4rem 1rem;
  border-bottom: 4px solid $accent-orange;
  text-align: center;
  
  h1 {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    font-weight: 700;
    letter-spacing: -0.5px;
    text-shadow: 0 2px 8px rgba(0,0,0,0.6);
    color: white;
    font-size: 2rem;
    margin-top: 0;
    border-bottom: none;
  }
  
  h3 {
    color: #e94560;
    font-size: 1.8rem;
    margin: 10px 0;
    text-shadow: 0 2px 4px rgba(0,0,0,0.5);
    border-bottom: none;
    
    a {
      color: #e94560;
      text-decoration: none;
    }
  }
  
  /* Адрес под телефоном в шапке */
  &::after {
    content: '📍 г. Дрогичин, ул. Ленина, 141 а (2 этаж) | Пн-Пт 10:00-19:00, Сб 11:00-17:00';
    display: block;
    color: rgba(255,255,255,0.95);
    font-size: 1rem;
    margin-top: 15px;
    text-shadow: 0 1px 3px rgba(0,0,0,0.8);
    line-height: 1.4;
  }
}

/* Логотип круглый */
.page-header::before {
  content: '';
  display: block;
  width: 90px;
  height: 90px;
  margin: 0 auto 15px auto;
  background: url('/assets/images/logo.png') center/contain no-repeat;
  background-color: white;
  border-radius: 50%;
  border: 3px solid #e94560;
  box-shadow: 0 4px 15px rgba(0,0,0,0.4);
}
