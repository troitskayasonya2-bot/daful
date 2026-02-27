# Premium Navbar — отдельно HTML, CSS, JS

Ссылки замените на свои якоря Tilda (например `#rec123456789`). Для квиза оставлен `#rec1947644431`.

---

## 1. HTML

```html
<nav class="pn-nav" id="pn-nav" aria-label="Основная навигация">
  <div class="pn-nav__bg"></div>
  <div class="pn-nav__in">
    <a href="#" class="pn-nav__logo" aria-label="DaFUL — на главную">
      <img src="https://static.tildacdn.com/tild6435-3465-4263-b162-623136373531/ful.svg" alt="DaFUL" class="pn-nav__logo-img" width="80" height="34" />
    </a>
    <ul class="pn-nav__menu" role="menubar">
      <li role="none"><a href="#uslugi" class="pn-nav__link" role="menuitem">Услуги</a></li>
      <li role="none"><a href="#keisy" class="pn-nav__link" role="menuitem">Кейсы</a></li>
      <li role="none"><a href="#stoimost" class="pn-nav__link" role="menuitem">Стоимость</a></li>
      <li role="none"><a href="#faq" class="pn-nav__link" role="menuitem">FAQ</a></li>
    </ul>
    <a href="#rec1947644431" class="pn-nav__cta">Рассчитать стоимость</a>
    <button type="button" class="pn-nav__burger" id="pn-burger" aria-label="Открыть меню" aria-expanded="false">
      <span class="pn-nav__burger-line"></span>
      <span class="pn-nav__burger-line"></span>
      <span class="pn-nav__burger-line"></span>
    </button>
  </div>
  <div class="pn-nav__drawer" id="pn-drawer" aria-hidden="true">
    <div class="pn-nav__drawer-backdrop" id="pn-drawer-backdrop"></div>
    <div class="pn-nav__drawer-panel">
      <ul class="pn-nav__drawer-menu">
        <li><a href="#uslugi" class="pn-nav__drawer-link">Услуги</a></li>
        <li><a href="#keisy" class="pn-nav__drawer-link">Кейсы</a></li>
        <li><a href="#stoimost" class="pn-nav__drawer-link">Стоимость</a></li>
        <li><a href="#faq" class="pn-nav__drawer-link">FAQ</a></li>
      </ul>
      <a href="#rec1947644431" class="pn-nav__drawer-cta">Рассчитать стоимость</a>
    </div>
  </div>
</nav>
<div class="pn-nav__spacer" aria-hidden="true"></div>
```

---

## 2. CSS

Подключите шрифт в `<head>` или перед стилями:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&display=swap" rel="stylesheet">
```

Либо в начале CSS:

```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&display=swap');
```

Полный CSS — см. файл `00_header_premium_navbar.html`, блок `<style>...</style>` (от `@import` до `@media (max-width: 768px)` включительно).

---

## 3. JS (бургер + плавный скролл)

```javascript
(function() {
  var nav = document.getElementById('pn-nav');
  var burger = document.getElementById('pn-burger');
  var drawer = document.getElementById('pn-drawer');
  var backdrop = document.getElementById('pn-drawer-backdrop');

  function openDrawer() {
    if (!drawer || !burger) return;
    drawer.classList.add('is-open');
    drawer.setAttribute('aria-hidden', 'false');
    burger.classList.add('is-open');
    burger.setAttribute('aria-expanded', 'true');
    burger.setAttribute('aria-label', 'Закрыть меню');
    document.body.style.overflow = 'hidden';
  }

  function closeDrawer() {
    if (!drawer || !burger) return;
    drawer.classList.remove('is-open');
    drawer.setAttribute('aria-hidden', 'true');
    burger.classList.remove('is-open');
    burger.setAttribute('aria-expanded', 'false');
    burger.setAttribute('aria-label', 'Открыть меню');
    document.body.style.overflow = '';
  }

  if (burger) {
    burger.addEventListener('click', function() {
      if (drawer.classList.contains('is-open')) closeDrawer();
      else openDrawer();
    });
  }
  if (backdrop) {
    backdrop.addEventListener('click', closeDrawer);
  }

  var drawerLinks = drawer && drawer.querySelectorAll('.pn-nav__drawer-link, .pn-nav__drawer-cta');
  if (drawerLinks && drawerLinks.length) {
    drawerLinks.forEach(function(link) {
      link.addEventListener('click', function() { closeDrawer(); });
    });
  }

  document.addEventListener('click', function(e) {
    var a = e.target.closest('a[href^="#"]');
    if (!a || a.getAttribute('href') === '#') return;
    var id = a.getAttribute('href').slice(1);
    if (!id) return;
    var el = document.getElementById(id);
    if (el) {
      e.preventDefault();
      el.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
  });
})();
```

---

## Вставка в Tilda

Скопируйте **весь** файл `00_header_premium_navbar.html` (включая `<style>` и `<script>`) в один Zero Block и разместите его выше первого контентного блока. Якоря `#uslugi`, `#keisy`, `#stoimost`, `#faq` замените на ID блоков в Tilda (настройки блока → ID блока).
