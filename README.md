<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Copywriting Webseite</title>
<style>
  body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
  }

  /* Style für das Hamburger-Icon */
  .menu-btn {
    position: fixed;
    top: 20px;
    right: 20px;
    width: 30px;
    height: 25px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    cursor: pointer;
    z-index: 1000;
  }

  .menu-btn div {
    height: 4px;
    background-color: #000;
    border-radius: 2px;
  }

  /* Navigation Menü */
  .nav {
    position: fixed;
    top: 0;
    right: -200px; /* versteckt rechts außerhalb */
    width: 200px;
    height: 100%;
    background-color: #fff;
    box-shadow: -2px 0 5px rgba(0,0,0,0.3);
    padding-top: 60px;
    transition: right 0.3s ease;
    z-index: 999;
  }

  .nav.show {
    right: 0;
  }

  .nav ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .nav li {
    padding: 15px 20px;
    border-bottom: 1px solid #ccc;
    cursor: pointer;
  }

  .nav li:hover {
    background-color: #f0f0f0;
  }

  /* Hauptinhalt */
  .content {
    padding: 80px 20px 20px 20px;
    max-width: 800px;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.5em;
    margin-bottom: 10px;
  }

  .small-text {
    font-size: 1em;
    color: #000;
    margin-bottom: 20px;
  }

  p {
    font-size: 1.1em;
    line-height: 1.5;
  }

  /* Hidden/Zeilenumbruch */
  .spacer {
    height: 20px;
  }

</style>
</head>
<body>

<!-- Hamburger Button -->
<div class="menu-btn" id="menuBtn" aria-label="Menü öffnen" aria-expanded="false" role="button" tabindex="0">
  <div></div>
  <div></div>
  <div></div>
</div>

<!-- Navigation Menü -->
<nav class="nav" id="navMenu" aria-hidden="true">
  <ul>
    <li data-page="start">Start</li>
    <li data-page="uebermich">Über mich</li>
    <li data-page="galerie">Galerie</li>
    <li data-page="kontakt">Kontakt</li>
  </ul>
</nav>

<!-- Hauptinhalt -->
<div class="content" id="mainContent">
  <!-- Standardseite oder Startseite -->
  <div id="seite-start" style="display: none;">
    <h1>Copywriting</h1>
    <p class="small-text">Hallo, ich bin Maja und ich verwandle Worte in WOW!</p>
    <div class="spacer"></div>
    <p>Sie wollen mehr Umsatz machen und ihre Produkte verkaufen, aber wissen nicht wie ?<br>
    Dann sind sie bei mir genau richtig!</p>
  </div>
  <!-- Über mich Seite -->
  <div id="seite-uebermich" style="display: none;">
    <h1>Über mich</h1>
    <p>Hier kannst du Informationen über dich hinzufügen.</p>
  </div>
  <!-- Galerie Seite -->
  <div id="seite-galerie" style="display: none;">
    <h1>Galerie</h1>
    <p>Hier kannst du Bilder oder andere Inhalte zeigen.</p>
  </div>
  <!-- Kontakt Seite -->
  <div id="seite-kontakt" style="display: none;">
    <h1>Kontakt</h1>
    <p>Hier kannst du Kontaktinformationen hinzufügen.</p>
  </div>
</div>

<script>
  const menuBtn = document.getElementById('menuBtn');
  const navMenu = document.getElementById('navMenu');
  const navItems = navMenu.querySelectorAll('li');
  const mainContent = document.getElementById('mainContent');

  let menuOpen = false;

  // Funktion zum Toggle des Menüs
  function toggleMenu() {
    menuOpen = !menuOpen;
    if (menuOpen) {
      navMenu.classList.add('show');
      navMenu.setAttribute('aria-hidden', 'false');
      menuBtn.setAttribute('aria-expanded', 'true');
    } else {
      navMenu.classList.remove('show');
      navMenu.setAttribute('aria-hidden', 'true');
      menuBtn.setAttribute('aria-expanded', 'false');
    }
  }

  // Event Listener für Hamburger Button
  menuBtn.addEventListener('click', toggleMenu);
  menuBtn.addEventListener('keydown', function(e) {
    if (e.key === 'Enter' || e.key === ' ' ) {
      e.preventDefault();
      toggleMenu();
    }
  });

  // Funktion zum Wechseln der Seiten
  function showPage(pageId) {
    // Alle Seiten verstecken
    const pages = ['start', 'uebermich', 'galerie', 'kontakt'];
    pages.forEach(id => {
      document.getElementById('seite-' + id).style.display = 'none';
    });
    // Gewählte Seite anzeigen
    document.getElementById('seite-' + pageId).style.display = 'block';

    // Menü schließen
    toggleMenu();
  }

  // Standardseite anzeigen (Start)
  showPage('start');

  // Event Listener für Menüeinträge
  navItems.forEach(item => {
    item.addEventListener('click', () => {
      const page = item.getAttribute('data-page');
      showPage(page);
    });
  });
</script>

</body>
</html>
