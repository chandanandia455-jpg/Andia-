<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Andia & restaurant — Modern Hearth Cuisine</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --coal:    #1a1612;
      --ember:   #c0572a;
      --ash:     #e8e2d9;
      --cream:   #f5f0e8;
      --smoke:   #7a7068;
      --char:    #2e2820;
      --gold:    #b89a5a;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--coal);
      color: var(--ash);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      overflow-x: hidden;
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.5rem 4rem;
      background: linear-gradient(to bottom, rgba(26,22,18,0.95), transparent);
    }

    .nav-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.4rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      color: var(--ash);
      text-transform: uppercase;
    }

    .nav-logo span { color: var(--ember); }

    .nav-links {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }

    .nav-links a {
      color: var(--ash);
      text-decoration: none;
      font-size: 0.8rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      opacity: 0.75;
      transition: opacity 0.2s;
    }

    .nav-links a:hover { opacity: 1; }

    .nav-reserve {
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      border: 1px solid var(--ember);
      color: var(--ember);
      padding: 0.55rem 1.4rem;
      text-decoration: none;
      transition: background 0.2s, color 0.2s;
    }

    .nav-reserve:hover { background: var(--ember); color: var(--cream); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      position: relative;
    }

    .hero-text {
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 10rem 4rem 6rem 4rem;
      position: relative;
      z-index: 2;
    }

    .hero-eyebrow {
      font-size: 0.72rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--ember);
      margin-bottom: 1.8rem;
    }

    .hero-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3.5rem, 5.5vw, 6rem);
      font-weight: 300;
      line-height: 1.0;
      color: var(--cream);
      margin-bottom: 2rem;
    }

    .hero-title em {
      font-style: italic;
      color: var(--ember);
    }

    .hero-desc {
      font-size: 0.95rem;
      line-height: 1.85;
      color: var(--smoke);
      max-width: 360px;
      margin-bottom: 3rem;
    }

    .hero-actions {
      display: flex;
      align-items: center;
      gap: 2rem;
    }

    .btn-primary {
      background: var(--ember);
      color: var(--cream);
      text-decoration: none;
      font-size: 0.78rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      padding: 1rem 2.2rem;
      transition: background 0.2s;
    }

    .btn-primary:hover { background: #a8471f; }

    .btn-ghost {
      color: var(--ash);
      text-decoration: none;
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      display: flex;
      align-items: center;
      gap: 0.6rem;
      opacity: 0.65;
      transition: opacity 0.2s;
    }

    .btn-ghost:hover { opacity: 1; }

    .btn-ghost::after {
      content: '→';
      font-size: 1rem;
    }

    /* HERO VISUAL */
    .hero-visual {
      position: relative;
      overflow: hidden;
    }

    .hero-visual-bg {
      position: absolute;
      inset: 0;
      background:
        radial-gradient(ellipse 60% 80% at 60% 50%, rgba(192,87,42,0.18) 0%, transparent 70%),
        url('https://images.unsplash.com/photo-1544025162-d76694265947?w=900&q=80') center/cover no-repeat;
    }

    .hero-visual-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(to right, var(--coal) 0%, rgba(26,22,18,0.3) 40%, transparent 100%);
    }

    .hero-stats {
      position: absolute;
      bottom: 4rem;
      right: 3rem;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
      z-index: 2;
    }

    .stat {
      text-align: right;
    }

    .stat-num {
      font-family: 'Cormorant Garamond', serif;
      font-size: 2.2rem;
      font-weight: 300;
      color: var(--cream);
      line-height: 1;
    }

    .stat-label {
      font-size: 0.68rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--smoke);
    }

    /* FLAME DIVIDER */
    .divider {
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 0.5rem 0;
      gap: 1.5rem;
    }

    .divider-line {
      flex: 1;
      max-width: 200px;
      height: 1px;
      background: linear-gradient(to right, transparent, var(--gold));
    }

    .divider-line.right {
      background: linear-gradient(to left, transparent, var(--gold));
    }

    .divider-icon { color: var(--ember); font-size: 1.1rem; }

    /* PHILOSOPHY */
    .philosophy {
      padding: 7rem 4rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-label {
      font-size: 0.7rem;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 3rem;
    }

    .philosophy-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6rem;
      align-items: center;
    }

    .philosophy-quote {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.8rem, 2.5vw, 2.6rem);
      font-weight: 300;
      font-style: italic;
      line-height: 1.4;
      color: var(--cream);
      border-left: 2px solid var(--ember);
      padding-left: 2rem;
    }

    .philosophy-body p {
      font-size: 0.92rem;
      line-height: 1.9;
      color: var(--smoke);
      margin-bottom: 1.2rem;
    }

    /* MENU HIGHLIGHTS */
    .menu-section {
      background: var(--char);
      padding: 7rem 4rem;
    }

    .menu-inner {
      max-width: 1200px;
      margin: 0 auto;
    }

    .menu-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin-bottom: 4rem;
    }

    .menu-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 3.5vw, 3.2rem);
      font-weight: 300;
      color: var(--cream);
    }

    .menu-link {
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--ember);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .menu-link::after { content: '→'; }

    .dishes {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2px;
    }

    .dish {
      position: relative;
      overflow: hidden;
      aspect-ratio: 3/4;
      cursor: pointer;
    }

    .dish img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.6s ease;
      filter: brightness(0.75);
    }

    .dish:hover img { transform: scale(1.05); filter: brightness(0.6); }

    .dish-info {
      position: absolute;
      bottom: 0; left: 0; right: 0;
      padding: 2rem 1.5rem;
      background: linear-gradient(to top, rgba(26,22,18,0.95) 0%, transparent 100%);
    }

    .dish-category {
      font-size: 0.65rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--ember);
      margin-bottom: 0.4rem;
    }

    .dish-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.35rem;
      font-weight: 400;
      color: var(--cream);
      line-height: 1.2;
    }

    .dish-price {
      margin-top: 0.4rem;
      font-size: 0.8rem;
      color: var(--gold);
    }

    /* EXPERIENCE STRIP */
    .experience {
      padding: 7rem 4rem;
      max-width: 1200px;
      margin: 0 auto;
    }

    .exp-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 3rem;
      margin-top: 4rem;
    }

    .exp-item {
      border-top: 1px solid rgba(192,87,42,0.3);
      padding-top: 2rem;
    }

    .exp-icon {
      font-size: 1.5rem;
      margin-bottom: 1.2rem;
    }

    .exp-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.25rem;
      font-weight: 400;
      color: var(--cream);
      margin-bottom: 0.6rem;
    }

    .exp-desc {
      font-size: 0.85rem;
      line-height: 1.75;
      color: var(--smoke);
    }

    /* RESERVATION */
    .reservation {
      background: var(--ember);
      padding: 6rem 4rem;
      text-align: center;
    }

    .res-inner { max-width: 680px; margin: 0 auto; }

    .res-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 4vw, 3.5rem);
      font-weight: 300;
      color: var(--cream);
      margin-bottom: 1rem;
    }

    .res-sub {
      font-size: 0.9rem;
      color: rgba(245,240,232,0.7);
      line-height: 1.7;
      margin-bottom: 2.5rem;
    }

    .res-form {
      display: flex;
      gap: 0;
      max-width: 480px;
      margin: 0 auto;
    }

    .res-form input {
      flex: 1;
      background: rgba(0,0,0,0.2);
      border: 1px solid rgba(245,240,232,0.3);
      border-right: none;
      padding: 0.9rem 1.2rem;
      color: var(--cream);
      font-family: 'DM Sans', sans-serif;
      font-size: 0.85rem;
      outline: none;
    }

    .res-form input::placeholder { color: rgba(245,240,232,0.4); }

    .res-form button {
      background: var(--coal);
      color: var(--cream);
      border: 1px solid var(--coal);
      padding: 0.9rem 1.6rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      cursor: pointer;
      transition: background 0.2s;
    }

    .res-form button:hover { background: var(--char); }

    /* FOOTER */
    footer {
      background: var(--coal);
      border-top: 1px solid rgba(122,112,104,0.2);
      padding: 3rem 4rem;
    }

    .footer-inner {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .footer-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.1rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--ash);
    }

    .footer-logo span { color: var(--ember); }

    .footer-info {
      font-size: 0.78rem;
      color: var(--smoke);
      text-align: center;
      line-height: 1.8;
    }

    .footer-socials {
      display: flex;
      gap: 1.5rem;
    }

    .footer-socials a {
      font-size: 0.72rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--smoke);
      text-decoration: none;
      transition: color 0.2s;
    }

    .footer-socials a:hover { color: var(--ember); }

    /* ANIMATIONS */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .hero-text > * {
      animation: fadeUp 0.8s ease both;
    }

    .hero-eyebrow  { animation-delay: 0.1s; }
    .hero-title    { animation-delay: 0.25s; }
    .hero-desc     { animation-delay: 0.4s; }
    .hero-actions  { animation-delay: 0.55s; }

    /* RESPONSIVE */
    @media (max-width: 900px) {
      nav { padding: 1.2rem 1.5rem; }
      .nav-links { display: none; }

      .hero { grid-template-columns: 1fr; min-height: auto; }
      .hero-text { padding: 8rem 1.5rem 3rem; }
      .hero-visual { height: 55vw; min-height: 280px; }
      .hero-visual-overlay {
        background: linear-gradient(to bottom, var(--coal) 0%, rgba(26,22,18,0.2) 50%, transparent 100%);
      }
      .hero-stats { bottom: 1.5rem; right: 1.5rem; }

      .philosophy { padding: 4rem 1.5rem; }
      .philosophy-grid { grid-template-columns: 1fr; gap: 2.5rem; }

      .menu-section { padding: 4rem 1.5rem; }
      .menu-header { flex-direction: column; align-items: flex-start; gap: 1rem; }
      .dishes { grid-template-columns: 1fr; }
      .dish { aspect-ratio: 4/3; }

      .experience { padding: 4rem 1.5rem; }
      .exp-grid { grid-template-columns: 1fr 1fr; gap: 2rem; }

      .reservation { padding: 4rem 1.5rem; }
      .res-form { flex-direction: column; }
      .res-form input { border-right: 1px solid rgba(245,240,232,0.3); border-bottom: none; }

      footer { padding: 2rem 1.5rem; }
      .footer-inner { flex-direction: column; gap: 1.5rem; text-align: center; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="nav-logo">Ember<span>&</span>Salt</div>
    <ul class="nav-links">
      <li><a href="#menu">Menu</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#reserve">Reserve</a></li>
    </ul>
    <a href="#reserve" class="nav-reserve">Book a Table</a>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-text">
      <p class="hero-eyebrow">Open Fire · Slow Craft · New York City</p>
      <h1 class="hero-title">Food<br/>cooked<br/>over <em>flame.</em></h1>
      <p class="hero-desc">We cook everything over live fire. Not for theater — because the char, the smoke, and the heat do things no stove can replicate. Ember & Salt is a hearth kitchen rooted in seasonal ingredients and patience.</p>
      <div class="hero-actions">
        <a href="#reserve" class="btn-primary">Reserve a Table</a>
        <a href="#menu" class="btn-ghost">See the Menu</a>
      </div>
    </div>
    <div class="hero-visual">
      <div class="hero-visual-bg"></div>
      <div class="hero-visual-overlay"></div>
      <div class="hero-stats">
        <div class="stat">
          <div class="stat-num">14</div>
          <div class="stat-label">Dishes on the menu</div>
        </div>
        <div class="stat">
          <div class="stat-num">6°</div>
          <div class="stat-label">Tasting experience</div>
        </div>
        <div class="stat">
          <div class="stat-num">700°</div>
          <div class="stat-label">Our hearth temperature</div>
        </div>
      </div>
    </div>
  </section>

  <!-- DIVIDER -->
  <div class="divider" style="padding: 2rem 4rem;">
    <div class="divider-line"></div>
    <span class="divider-icon">🔥</span>
    <div class="divider-line right"></div>
  </div>

  <!-- PHILOSOPHY -->
  <section class="philosophy" id="experience">
    <p class="section-label">Our philosophy</p>
    <div class="philosophy-grid">
      <blockquote class="philosophy-quote">
        "Fire is the oldest cooking technique. We never forgot that."
      </blockquote>
      <div class="philosophy-body">
        <p>Every dish begins with a question: what does the fire want to do to this ingredient? Sometimes it's a slow, indirect smoke. Sometimes it's a searing flash at close range. The answer dictates the dish.</p>
        <p>Our suppliers are farmers, fishers, and foragers within 200 miles. The menu changes with the seasons because we won't force ingredients to be something they're not.</p>
        <p>We're a small team of twelve. We seat forty guests a night. This is the only way we know how to do it properly.</p>
      </div>
    </div>
  </section>

  <!-- MENU -->
  <section class="menu-section" id="menu">
    <div class="menu-inner">
      <div class="menu-header">
        <div>
          <p class="section-label">From the hearth</p>
          <h2 class="menu-title">Tonight's highlights</h2>
        </div>
        <a href="#" class="menu-link">Full menu</a>
      </div>
      <div class="dishes">
        <div class="dish">
          <img src="https://images.unsplash.com/photo-1600891964092-4316c288032e?w=600&q=80" alt="Wood-fired duck" loading="lazy"/>
          <div class="dish-info">
            <p class="dish-category">Main · Fire-roasted</p>
            <h3 class="dish-name">Duck Breast,<br/>Charred Plum</h3>
            <p class="dish-price">$52</p>
          </div>
        </div>
        <div class="dish">
          <img src="https://images.unsplash.com/photo-1559847844-5315695dadae?w=600&q=80" alt="Smoked fish" loading="lazy"/>
          <div class="dish-info">
            <p class="dish-category">Starter · Wood-smoked</p>
            <h3 class="dish-name">Smoked Trout,<br/>Buttermilk, Dill</h3>
            <p class="dish-price">$24</p>
          </div>
        </div>
        <div class="dish">
          <img src="https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=600&q=80" alt="Grilled vegetables" loading="lazy"/>
          <div class="dish-info">
            <p class="dish-category">Seasonal · Ember-roasted</p>
            <h3 class="dish-name">Root Vegetable<br/>Platter, Tahini</h3>
            <p class="dish-price">$19</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section class="experience">
    <p class="section-label">Why Ember & Salt</p>
    <h2 style="font-family:'Cormorant Garamond',serif;font-size:clamp(2rem,3vw,2.8rem);font-weight:300;color:var(--cream);">What makes the evening</h2>
    <div class="exp-grid">
      <div class="exp-item">
        <div class="exp-icon">🪵</div>
        <h3 class="exp-name">Live Hearth Kitchen</h3>
        <p class="exp-desc">Our open kitchen is built around a central wood-burning hearth. You watch the fire from your seat.</p>
      </div>
      <div class="exp-item">
        <div class="exp-icon">🌿</div>
        <h3 class="exp-name">Seasonal Menu</h3>
        <p class="exp-desc">We print a new menu every two weeks. If you've dined with us before, the experience will be different.</p>
      </div>
      <div class="exp-item">
        <div class="exp-icon">🍷</div>
        <h3 class="exp-name">Natural Wine List</h3>
        <p class="exp-desc">Small producers, minimal intervention. Our sommelier pairs each course if you take the tasting menu.</p>
      </div>
      <div class="exp-item">
        <div class="exp-icon">🕯</div>
        <h3 class="exp-name">Forty Seats</h3>
        <p class="exp-desc">We limit covers deliberately. Every table gets our full attention, not a fraction of it.</p>
      </div>
    </div>
  </section>

  <!-- RESERVATION -->
  <section class="reservation" id="reserve">
    <div class="res-inner">
      <h2 class="res-title">Reserve your evening</h2>
      <p class="res-sub">Tables book out quickly, especially Thursday through Saturday. Add your email and we'll send you availability for the next two weeks.</p>
      <div class="res-form">
        <input type="email" placeholder="your@email.com" />
        <button type="button">Get Availability</button>
      </div>
      <p style="margin-top:1.4rem;font-size:0.75rem;color:rgba(245,240,232,0.45);letter-spacing:0.05em;">
        Or call us directly: (212) 555-0183 · Tue – Sun, 5 pm – 11 pm
      </p>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-inner">
      <div class="footer-logo">Ember<span>&</span>Salt</div>
      <div class="footer-info">
        147 West 13th Street, New York, NY<br/>
        Dinner service · Tuesday through Sunday
      </div>
      <div class="footer-socials">
        <a href="#">Instagram</a>
        <a href="#">Reservations</a>
        <a href="#">Press</a>
      </div>
    </div>
  </footer>

</body>
</html>
