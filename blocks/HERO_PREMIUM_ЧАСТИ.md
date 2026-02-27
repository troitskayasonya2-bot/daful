# Hero Section Premium — отдельно HTML, CSS, JS

Готовый первый экран для Tilda. Полный код в одном блоке: **`01_hero_premium.html`**.

---

## 1. HTML

```html
<section class="dafull-hero" id="hero">
  <div class="dafull-hero__bg">
    <img src="https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?w=1920&q=80" alt="" role="presentation" loading="eager" />
    <div class="dafull-hero__overlay"></div>
  </div>

  <div class="dafull-hero__card">
    <div class="dafull-hero__card-icons">
      <img src="https://static.tildacdn.com/tild3137-3966-4638-b164-336636306430/qrvpib73_1.png" alt="Wildberries" class="dafull-hero__card-icon" width="42" height="42" loading="lazy" />
      <img src="https://static.tildacdn.com/tild3332-6433-4565-b133-623236353838/unnamed__3__1.png" alt="Ozon" class="dafull-hero__card-icon" width="42" height="42" loading="lazy" />
    </div>
    <p class="dafull-hero__card-text">FBO и FBS под требования Wildberries и Ozon</p>
  </div>

  <div class="dafull-hero__in">
    <div class="dafull-hero__center">
      <div class="dafull-hero__logo-wrap">
        <img src="https://static.tildacdn.com/tild6435-3465-4263-b162-623136373531/ful.svg" alt="DaFUL" class="dafull-hero__logo" width="520" height="160" loading="eager" />
      </div>
      <p class="dafull-hero__tagline">Фулфилмент в Москве</p>
      <a href="#rec1947644431" class="dafull-hero__cta">Получить расчет →</a>
      <p class="dafull-hero__sub">Без штрафов и задержек. Подготовка под ТЗ маркетплейсов.</p>
    </div>
  </div>
</section>
```

**Ссылку на квиз** замените при необходимости: сейчас `#rec1947644431`. Фон можно заменить своей картинкой — укажите свой URL в `src` у `.dafull-hero__bg img`.

---

## 2. CSS

Подключение шрифта (если ещё не подключён):

```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600&display=swap');
```

Полный CSS — в файле **`01_hero_premium.html`**, блок `<style>...</style>` (от `@import` до конца `@media (max-width: 768px)`).

Основные моменты:
- Секция: `height: 100vh`, фон `cover` + overlay `rgba(0,0,0,0.45)`.
- Контент: `max-width: 1240px`, центрирование.
- Лого: до 520px, анимация появления `fade + translateY(20px)`, hover: `scale(1.03)` + `drop-shadow` glow #FF6A00.
- Подпись: выравнивание по правому краю относительно логотипа, Montserrat 400, 22px, задержка анимации.
- Карточка: glassmorphism, `absolute` слева по центру, иконки 42px, hover scale 1.1 + rotate 3deg + glow.
- Кнопка: pill, #FF6A00, тень, hover `translateY(-3px)` + усиленная тень, анимация появления с задержкой.
- Подпись под кнопкой: центр, 18px, fade-in с задержкой.
- Stagger: лого 0s, карточка 0.15s, подпись 0.25s, кнопка 0.4s, подтекст 0.55s.
- Адаптив: tablet — карточка выше, лого/кнопка компактнее; mobile — карточка сверху inline, всё по центру.

---

## 3. JS

Минимальный скрипт (опционально, для класса на корне при загрузке):

```javascript
(function() {
  document.documentElement.classList.add('dafull-hero-js');
})();
```

Анимации реализованы на чистом CSS (`@keyframes` + `animation` и `animation-delay`), отдельный JS для анимаций не требуется. Скрипт выше можно не подключать, если класс не используете.

---

## Вставка в Tilda

Скопируйте **весь** файл **`01_hero_premium.html`** (включая `<style>` и `<script>`) в один Zero Block и разместите его под премиум-навбаром (или первым блоком страницы). У первого блока под навбаром задайте отступ сверху (например, 64px), если бар фиксирован и наезжает на hero.
