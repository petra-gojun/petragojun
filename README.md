<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Petra Gojun — Integration Coaching</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Jost:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --cream: #F5F0E8;
      --warm-white: #FAF8F4;
      --earth: #8B7355;
      --deep: #2C2416;
      --muted: #9B9080;
      --accent: #C4956A;
      --sage: #7A8C75;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--warm-white);
      color: var(--deep);
      font-family: 'Jost', sans-serif;
      font-weight: 300;
      overflow-x: hidden;
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      padding: 1.5rem 3rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: rgba(250, 248, 244, 0.92);
      backdrop-filter: blur(8px);
      border-bottom: 1px solid rgba(139, 115, 85, 0.12);
    }

    .nav-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.2rem;
      font-weight: 400;
      letter-spacing: 0.08em;
      color: var(--deep);
      text-decoration: none;
    }

    .nav-links {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }

    .nav-links a {
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      transition: color 0.3s;
    }

    .nav-links a:hover { color: var(--deep); }

    .nav-cta {
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent) !important;
      border-bottom: 1px solid var(--accent);
      padding-bottom: 1px;
    }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      padding-top: 5rem;
    }

    .hero-text {
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 6rem 4rem 6rem 6rem;
      position: relative;
    }

    .hero-text::after {
      content: '';
      position: absolute;
      right: 0; top: 15%; bottom: 15%;
      width: 1px;
      background: linear-gradient(to bottom, transparent, var(--earth) 30%, var(--earth) 70%, transparent);
      opacity: 0.2;
    }

    .eyebrow {
      font-size: 0.72rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 2rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards 0.2s;
    }

    .hero-headline {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(3rem, 5vw, 4.8rem);
      font-weight: 300;
      line-height: 1.1;
      color: var(--deep);
      margin-bottom: 2rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards 0.4s;
    }

    .hero-headline em {
      font-style: italic;
      color: var(--earth);
    }

    .hero-sub {
      font-size: 1.05rem;
      line-height: 1.8;
      color: var(--muted);
      max-width: 44ch;
      margin-bottom: 3rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards 0.6s;
    }

    .hero-sub strong {
      color: var(--deep);
      font-weight: 400;
    }

    .cta-group {
      display: flex;
      align-items: center;
      gap: 2rem;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards 0.8s;
    }

    .btn-primary {
      display: inline-block;
      padding: 1rem 2.2rem;
      background: var(--deep);
      color: var(--cream);
      text-decoration: none;
      font-size: 0.78rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      transition: background 0.3s, transform 0.2s;
    }

    .btn-primary:hover {
      background: var(--earth);
      transform: translateY(-1px);
    }

    .cta-note {
      font-size: 0.82rem;
      color: var(--muted);
      font-style: italic;
      font-family: 'Cormorant Garamond', serif;
    }

    .hero-image {
      position: relative;
      overflow: hidden;
      opacity: 0;
      animation: fadeIn 1.2s ease forwards 0.3s;
    }

    .hero-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center top;
    }

    .hero-image-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(to right, var(--warm-white) 0%, transparent 15%);
    }

    /* SECTION SHARED */
    section {
      padding: 7rem 6rem;
    }

    .section-label {
      font-size: 0.72rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1.5rem;
    }

    /* PRESENCE SECTION */
    .presence {
      background: var(--cream);
      display: grid;
      grid-template-columns: 1fr 1.4fr;
      gap: 6rem;
      align-items: center;
    }

    .presence-quote {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.8rem, 3vw, 2.6rem);
      font-weight: 300;
      font-style: italic;
      line-height: 1.4;
      color: var(--earth);
      position: relative;
      padding-left: 2rem;
      border-left: 2px solid var(--accent);
    }

    .presence-body p {
      font-size: 1rem;
      line-height: 1.9;
      color: var(--muted);
      margin-bottom: 1.4rem;
    }

    .presence-body p strong {
      color: var(--deep);
      font-weight: 400;
    }

    /* WHO THIS IS FOR */
    .for-you {
      background: var(--warm-white);
    }

    .for-you-header {
      max-width: 60ch;
      margin-bottom: 4rem;
    }

    .for-you h2 {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 3.5vw, 3rem);
      font-weight: 300;
      line-height: 1.3;
      margin-bottom: 1.2rem;
    }

    .for-you-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2px;
      background: rgba(139, 115, 85, 0.1);
    }

    .for-card {
      background: var(--warm-white);
      padding: 2.5rem;
      transition: background 0.3s;
    }

    .for-card:hover {
      background: var(--cream);
    }

    .for-card-number {
      font-family: 'Cormorant Garamond', serif;
      font-size: 3rem;
      font-weight: 300;
      color: rgba(139, 115, 85, 0.2);
      margin-bottom: 1rem;
      line-height: 1;
    }

    .for-card h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.3rem;
      font-weight: 400;
      margin-bottom: 0.8rem;
      color: var(--deep);
    }

    .for-card p {
      font-size: 0.9rem;
      line-height: 1.8;
      color: var(--muted);
    }

    /* THE WORK */
    .the-work {
      background: var(--deep);
      color: var(--cream);
    }

    .the-work .section-label {
      color: var(--accent);
      opacity: 0.8;
    }

    .work-intro {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.8rem, 3vw, 2.8rem);
      font-weight: 300;
      line-height: 1.4;
      max-width: 55ch;
      margin-bottom: 4rem;
      color: var(--cream);
    }

    .work-intro em {
      font-style: italic;
      color: var(--accent);
    }

    .offers-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2px;
      background: rgba(255,255,255,0.05);
      margin-bottom: 4rem;
    }

    .offer-card {
      background: rgba(44, 36, 22, 0.95);
      padding: 3rem;
      border: 1px solid rgba(255,255,255,0.04);
      transition: background 0.3s;
    }

    .offer-card:hover {
      background: rgba(60, 48, 28, 0.95);
    }

    .offer-tag {
      font-size: 0.7rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1.5rem;
    }

    .offer-card h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.8rem;
      font-weight: 300;
      color: var(--cream);
      margin-bottom: 1rem;
    }

    .offer-card p {
      font-size: 0.92rem;
      line-height: 1.8;
      color: rgba(245, 240, 232, 0.6);
      margin-bottom: 1.5rem;
    }

    .offer-detail {
      font-size: 0.78rem;
      letter-spacing: 0.08em;
      color: var(--accent);
      opacity: 0.8;
    }

    /* TESTIMONY */
    .testimony {
      background: var(--cream);
      display: grid;
      grid-template-columns: 1fr 2fr;
      gap: 6rem;
      align-items: center;
    }

    .testimony-label-block .section-label {
      writing-mode: vertical-rl;
      text-orientation: mixed;
      transform: rotate(180deg);
    }

    .testimony-content blockquote {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(1.4rem, 2.5vw, 2rem);
      font-weight: 300;
      font-style: italic;
      line-height: 1.6;
      color: var(--deep);
      margin-bottom: 2rem;
    }

    .testimony-attribution {
      font-size: 0.78rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--muted);
    }

    /* ABOUT STRIP */
    .about-strip {
      background: var(--warm-white);
      display: grid;
      grid-template-columns: 1.2fr 1fr;
      gap: 6rem;
      align-items: start;
    }

    .about-text h2 {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2rem, 3vw, 2.8rem);
      font-weight: 300;
      line-height: 1.3;
      margin-bottom: 2rem;
    }

    .about-text p {
      font-size: 0.98rem;
      line-height: 1.9;
      color: var(--muted);
      margin-bottom: 1.4rem;
    }

    .about-text p strong {
      color: var(--deep);
      font-weight: 400;
    }

    .about-credentials {
      padding-top: 1rem;
    }

    .credential-item {
      padding: 1.2rem 0;
      border-bottom: 1px solid rgba(139, 115, 85, 0.15);
      display: flex;
      gap: 1rem;
      align-items: baseline;
    }

    .credential-dot {
      width: 4px;
      height: 4px;
      background: var(--accent);
      border-radius: 50%;
      flex-shrink: 0;
      margin-top: 0.5rem;
    }

    .credential-item p {
      font-size: 0.88rem;
      line-height: 1.6;
      color: var(--muted);
    }

    .credential-item strong {
      font-weight: 400;
      color: var(--deep);
    }

    /* CLOSING CTA */
    .closing {
      background: var(--deep);
      text-align: center;
      padding: 8rem 6rem;
    }

    .closing h2 {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(2.2rem, 4vw, 3.8rem);
      font-weight: 300;
      font-style: italic;
      color: var(--cream);
      line-height: 1.3;
      max-width: 22ch;
      margin: 0 auto 1.5rem;
    }

    .closing p {
      font-size: 1rem;
      color: rgba(245, 240, 232, 0.55);
      max-width: 45ch;
      margin: 0 auto 3rem;
      line-height: 1.8;
    }

    .btn-light {
      display: inline-block;
      padding: 1rem 2.5rem;
      border: 1px solid rgba(245, 240, 232, 0.4);
      color: var(--cream);
      text-decoration: none;
      font-size: 0.78rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      transition: all 0.3s;
    }

    .btn-light:hover {
      background: rgba(245, 240, 232, 0.08);
      border-color: var(--accent);
      color: var(--accent);
    }

    .closing-note {
      margin-top: 2rem;
      font-size: 0.82rem;
      color: rgba(245, 240, 232, 0.3);
      font-style: italic;
      font-family: 'Cormorant Garamond', serif;
    }

    /* FOOTER */
    footer {
      background: #1A1410;
      padding: 2.5rem 6rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    footer p {
      font-size: 0.75rem;
      color: rgba(245, 240, 232, 0.25);
      letter-spacing: 0.05em;
    }

    /* ANIMATIONS */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.8s ease, transform 0.8s ease;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* RESPONSIVE */
    @media (max-width: 900px) {
      nav { padding: 1.2rem 2rem; }
      .nav-links { display: none; }
      section { padding: 5rem 2rem; }
      .hero { grid-template-columns: 1fr; min-height: auto; }
      .hero-text { padding: 7rem 2rem 3rem; }
      .hero-text::after { display: none; }
      .hero-image { height: 60vw; }
      .presence, .about-strip { grid-template-columns: 1fr; gap: 3rem; }
      .testimony { grid-template-columns: 1fr; }
      .testimony-label-block { display: none; }
      .for-you-grid { grid-template-columns: 1fr; }
      .offers-grid { grid-template-columns: 1fr; }
      .closing { padding: 6rem 2rem; }
      footer { flex-direction: column; gap: 1rem; text-align: center; padding: 2rem; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <a href="/" class="nav-name">Petra Gojun</a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#work">The Work</a></li>
      <li><a href="#faqs">FAQs</a></li>
      <li><a href="https://calendly.com/petragojun/consultation" class="nav-cta">Book a Call</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section class="hero" style="padding: 0;">
    <div class="hero-text">
      <p class="eyebrow">Integration & Somatic Coaching</p>
      <h1 class="hero-headline">
        You built the life.<br/>
        <em>Now find yourself<br/>inside it.</em>
      </h1>
      <p class="hero-sub">
        You are capable, clear, and competent in ways most people will never be.
        And somewhere in the building — <strong>something essential didn't come along.</strong>
        Not broken. Not missing. Waiting.
      </p>
      <div class="cta-group">
        <a href="https://calendly.com/petragojun/consultation" class="btn-primary">Schedule Your Intro Call</a>
        <span class="cta-note">Complimentary. No obligation.</span>
      </div>
    </div>
    <div class="hero-image">
      <img src="https://images.squarespace-cdn.com/content/v1/691e0a030a5dd46abc27acf4/aee19b21-f5e2-462b-ab16-ae077d3fa8ec/Petra+Gojun+Final-22.jpg" alt="Petra Gojun" />
      <div class="hero-image-overlay"></div>
    </div>
  </section>

  <!-- PRESENCE SECTION -->
  <section class="presence">
    <div class="presence-quote reveal">
      "There are parts of you that were never given permission to arrive. This work is the invitation."
    </div>
    <div class="presence-body reveal">
      <p>
        You have tried rest. Therapy. Boundaries. Meditation. The vacation that was supposed to fix it.
        They helped. <strong>The gap remained.</strong>
      </p>
      <p>
        Because what you're feeling isn't exhaustion — it's distance.
        From yourself. From what actually matters. From the aliveness
        you can sense is possible but can't quite reach from inside your current life.
      </p>
      <p>
        <strong>This isn't about doing less, or doing it differently.</strong>
        It's about integrating what was left behind — in the building,
        in the becoming, in the parts of your story you learned to manage rather than feel.
      </p>
      <p>
        The gap closes when you stop working around yourself and start working <em>with</em> all of you.
      </p>
    </div>
  </section>

  <!-- WHO THIS IS FOR -->
  <section class="for-you" id="for-you">
    <div class="for-you-header reveal">
      <p class="section-label">Who this is for</p>
      <h2>You don't need to be in crisis.<br/>You need to be <em style="font-family: 'Cormorant Garamond', serif; font-style: italic;">honest.</em></h2>
    </div>
    <div class="for-you-grid">
      <div class="for-card reveal">
        <div class="for-card-number">01</div>
        <h3>The high-achiever who has arrived</h3>
        <p>You built what you set out to build. It's real and it's good. And something still feels off in a way you can't explain to people who would trade places with you in a second.</p>
      </div>
      <div class="for-card reveal">
        <div class="for-card-number">02</div>
        <h3>The leader carrying more than the role</h3>
        <p>You hold a lot. For a long time. You're good at it. And underneath the competence, there's a version of you that is tired of being managed — including by yourself.</p>
      </div>
      <div class="for-card reveal">
        <div class="for-card-number">03</div>
        <h3>The person in relational pain</h3>
        <p>Something in your closest relationships keeps repeating. You're self-aware enough to see the pattern. Seeing it hasn't been enough to change it. The work lives deeper than insight.</p>
      </div>
      <div class="for-card reveal">
        <div class="for-card-number">04</div>
        <h3>The woman in transition</h3>
        <p>Something is ending or beginning or both. The old map doesn't work. You're not lost — you're between versions of yourself, and you need more than advice for what comes next.</p>
      </div>
      <div class="for-card reveal">
        <div class="for-card-number">05</div>
        <h3>The one doing serious inner work</h3>
        <p>You're not new to this. You've done therapy, retreats, reading. You're looking for a container that can hold the real depth of what you're carrying — and meet you there.</p>
      </div>
      <div class="for-card reveal">
        <div class="for-card-number">06</div>
        <h3>The one who is always holding everyone else</h3>
        <p>You are the one people call. The one who knows how to be present for others. And you have quietly, for a long time, not asked for much in return. That changes here.</p>
      </div>
    </div>
  </section>

  <!-- THE WORK -->
  <section class="the-work" id="work">
    <p class="section-label reveal">The work</p>
    <p class="work-intro reveal">
      This is not talk-based support. It is <em>experiential, somatic, whole-person</em> work —
      the kind that reaches what conversation alone cannot.
    </p>
    <div class="offers-grid">
      <div class="offer-card reveal">
        <p class="offer-tag">1:1 Coaching</p>
        <h3>Deep, sustained work</h3>
        <p>
          For those ready to move past insight into genuine change.
          We work with your patterns through mind, body, and felt sense —
          contacting what has been managed, avoided, or left behind,
          and discovering what becomes possible when you show up whole.
        </p>
        <p>
          You will develop real practices for returning to yourself under pressure —
          not performing composure, but finding your actual ground.
        </p>
        <p class="offer-detail">Ongoing engagement · Somatic & experiential · Not psychotherapy</p>
      </div>
      <div class="offer-card reveal">
        <p class="offer-tag">Breathing Room</p>
        <h3>A cohort for those carrying a lot</h3>
        <p>
          You arrive at the end of the day — after the meetings, the decisions, the managing of everything and everyone.
          This time is yours. Four sessions over eight weeks. Small group. Virtual. 75 minutes.
        </p>
        <p>
          We begin with arrival. We create real space to set things down.
          You leave more settled, clear, and less alone in what you're carrying.
        </p>
        <p class="offer-detail">4 sessions · 8 weeks · Small cohort · Virtual</p>
      </div>
    </div>
    <div style="text-align: center; padding-top: 2rem;" class="reveal">
      <a href="https://calendly.com/petragojun/consultation" class="btn-light">Find out which is right for you</a>
    </div>
  </section>

  <!-- TESTIMONY -->
  <section class="testimony">
    <div class="testimony-label-block">
      <p class="section-label">What people say</p>
    </div>
    <div class="testimony-content reveal">
      <blockquote>
        "She has this way of helping you feel seen, held, and able to move forward.
        There were times I felt completely overwhelmed at the beginning of our sessions —
        and by the end, I could breathe again."
      </blockquote>
      <p class="testimony-attribution">— T.F.</p>
    </div>
  </section>

  <!-- ABOUT -->
  <section class="about-strip" id="about">
    <div class="about-text reveal">
      <p class="section-label">About Petra</p>
      <h2>I know what it costs to be capable everywhere except inside your own life.</h2>
      <p>
        I grew up in Croatia. I have lived across three countries and think in multiple languages.
        I learned early how to find what is essential in unfamiliar terrain —
        and how to keep moving when the map runs out.
      </p>
      <p>
        That capacity followed me through 15 years in tech,
        leading transformation at SAP Concur and Asana, growing startups,
        designing systems meant to support the people inside them.
        <strong>I was good at it. And I was organized out of my own life in ways I couldn't yet name.</strong>
      </p>
      <p>
        What emerged from that was not a pivot. It was a reckoning.
        A Master's in Mindfulness-Based Transpersonal Counseling.
        Years of contemplative practice, singing, competitive rowing —
        each one teaching me something the others couldn't.
      </p>
      <p>
        <strong>I am a mental health professional offering coaching and integration work.</strong>
        I bring the full range of what I've learned — and what I've lived — into every session.
      </p>
    </div>
    <div class="about-credentials reveal">
      <p class="section-label">Background</p>
      <div class="credential-item">
        <div class="credential-dot"></div>
        <p><strong>MA, Mindfulness-Based Transpersonal Counseling</strong><br/>Naropa University</p>
      </div>
      <div class="credential-item">
        <div class="credential-dot"></div>
        <p><strong>15 years in tech leadership</strong><br/>SAP Concur, Asana, early-stage startups</p>
      </div>
      <div class="credential-item">
        <div class="credential-dot"></div>
        <p><strong>Somatic & body-based training</strong><br/>Authentic Movement, contemplative practice</p>
      </div>
      <div class="credential-item">
        <div class="credential-dot"></div>
        <p><strong>Mental health professional</strong><br/>Coaching offered is not psychotherapy</p>
      </div>
      <div class="credential-item">
        <div class="credential-dot"></div>
        <p><strong>Based in the United States</strong><br/>Working virtually, globally</p>
      </div>
    </div>
  </section>

  <!-- CLOSING CTA -->
  <section class="closing">
    <h2 class="reveal">What if someone showed up for you, the way you show up for everyone else?</h2>
    <p class="reveal">
      The intro call is a real conversation. Not a sales pitch.
      Bring what you're actually carrying and we'll see together if this is the right fit.
    </p>
    <div class="reveal">
      <a href="https://calendly.com/petragojun/consultation" class="btn-light">Schedule Your Intro Call</a>
      <p class="closing-note">Complimentary · 45 minutes · No obligation</p>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>© 2026 Petra Gojun · Integration & Somatic Coaching</p>
    <p>Services offered are coaching and integration work, not psychotherapy.</p>
  </footer>

  <script>
    // Scroll reveal
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry, i) => {
        if (entry.isIntersecting) {
          setTimeout(() => {
            entry.target.classList.add('visible');
          }, 100);
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

    reveals.forEach(el => observer.observe(el));
  </script>

</body>
</html>
