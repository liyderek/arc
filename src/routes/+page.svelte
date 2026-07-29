<script>
  import { onMount } from "svelte";

  // ─── DATA ───────────────────────────────────────────────────────────────────
  const teamMembers = [
    { name: "Krish Vimalkumar", title: "Team Captain" },
    { name: "Ashwin Rajkumar",  title: "Member" },
    { name: "Qicheng (Anthony) Lin", title: "Member" },
    { name: "Ryan Kim",         title: "Member" },
    { name: "Derek Li",         title: "Member" },
    { name: "Rohan Agarwal",    title: "Member" },
    { name: "Advaith Prabhu",   title: "Member" },
    { name: "Chris Ahn",        title: "Member" },
  ];

  const galleryImages = [
    { src: "/media/converted/IMG_3170.jpg", alt: "Team member assembling rocket at competition" },
    { src: "/media/converted/IMG_3330.jpg", alt: "Rocket components laid out before launch" },
    { src: "/media/converted/IMG_3331.jpg", alt: "Team carrying rocket to launch pad" },
    { src: "/media/converted/IMG_3332.jpg", alt: "Close-up of rocket motor section" },
    { src: "/media/converted/IMG_3334.jpg", alt: "Team discussing launch strategy" },
    { src: "/media/converted/IMG_3335.jpg", alt: "Rocket on launch rail ready for flight" },
    { src: "/media/converted/IMG_3388.jpg", alt: "Team inspecting rocket after recovery" },
    { src: "/media/converted/IMG_3389.jpg", alt: "Recovered rocket body section on field" },
    { src: "/media/converted/IMG_3405.jpg", alt: "Team at ARC competition site" },
    { src: "/media/converted/IMG_3407.jpg", alt: "Matador Rocketry team group photo" },
    { src: "/media/converted/IMG_3455.jpg", alt: "Rocket airframe detail" },
    { src: "/media/converted/IMG_4729.jpg", alt: "Team working on rocket at launch site" },
  ];

  const videos = [
    { id: "launch-1", src: "/media/converted/IMG_3150.mp4" },
    { id: "launch-2", src: "/media/converted/IMG_3156.mp4" },
    { id: "launch-3", src: "/media/converted/IMG_3157.mp4" },
    { id: "flight-4", src: "/media/converted/IMG_3161.mp4" },
    { id: "flight-5", src: "/media/converted/IMG_3162.mp4" },
    { id: "flight-6", src: "/media/converted/IMG_4724.mp4" },
  ];

  // ─── REVEAL ON SCROLL ───────────────────────────────────────────────────────
  onMount(() => {
    const els = document.querySelectorAll(".reveal");
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((e) => {
          if (e.isIntersecting) {
            e.target.classList.add("visible");
            observer.unobserve(e.target);
          }
        });
      },
      { threshold: 0.08, rootMargin: "0px 0px -40px 0px" },
    );
    els.forEach((el) => observer.observe(el));
    return () => observer.disconnect();
  });

  // ─── CONTACT FORM ────────────────────────────────────────────────────────────
  let formName = $state("");
  let formEmail = $state("");
  let formMessage = $state("");
  let formStatus = $state(null);

  function handleSubmit(e) {
    e.preventDefault();
    if (!formName || !formEmail || !formMessage) { formStatus = "error"; return; }
    window.location.href = `mailto:mvaerospaceengineering@gmail.com?subject=Message from ${encodeURIComponent(formName)}&body=${encodeURIComponent(formMessage + "\n\nFrom: " + formName + "\nEmail: " + formEmail)}`;
    formStatus = "success";
    formName = ""; formEmail = ""; formMessage = "";
  }

  let activeGallery = $state(0);
</script>

<svelte:head>
  <title>Matador Rocketry | Monta Vista High School</title>
</svelte:head>

<!-- ══════════════════════════════════════════════════════════════
     HERO
══════════════════════════════════════════════════════════════ -->
<section id="hero" class="hero">
  <div class="hero-bg" aria-hidden="true"></div>
  <div class="hero-overlay" aria-hidden="true"></div>

  <div class="hero-content">
    <div class="hero-eyebrow reveal">
      <span class="eyebrow-dot"></span>
      American Rocketry Challenge 2024–2025
    </div>

    <h1 class="hero-title reveal">
      Matador<br /><em>Rocketry</em>
    </h1>

    <p class="hero-sub reveal">
      Monta Vista High School's premier competitive rocketry team —<br />
      engineering precision, fueling ambition, reaching for the stars.
    </p>

    <div class="hero-actions reveal">
      <a href="#about" class="btn-solid">Explore Our Story</a>
      <a href="#contact" class="btn-ghost">Join the Team ↗</a>
    </div>
  </div>

  <div class="hero-stats reveal">
    <div class="hstat">
      <span class="hstat-num">2</span>
      <span class="hstat-lbl">Years Competing</span>
    </div>
    <div class="hstat-rule"></div>
    <div class="hstat">
      <span class="hstat-num">8+</span>
      <span class="hstat-lbl">Team Members</span>
    </div>
    <div class="hstat-rule"></div>
    <div class="hstat">
      <span class="hstat-num">Top&nbsp;100</span>
      <span class="hstat-lbl">Nationally</span>
    </div>
  </div>

  <div class="hero-scroll" aria-hidden="true">
    <div class="scroll-bar"></div>
    <span>Scroll</span>
  </div>
</section>

<!-- ══════════════════════════════════════════════════════════════
     ABOUT — edge-to-edge split
══════════════════════════════════════════════════════════════ -->
<section id="about" class="about-section">
  <div class="about-split">
    <!-- Image side — bleeds to edge -->
    <div class="about-img-side reveal">
      <img
        src="/media/converted/IMG_3408.jpg"
        alt="Matador Rocketry team in the workshop building their competition rocket"
        loading="lazy"
      />
    </div>

    <!-- Text side -->
    <div class="about-text-side reveal">
      <span class="sec-num">01</span>
      <span class="sec-label">Who We Are</span>
      <h2 class="sec-title">Launching<br />Dreams from<br /><em>Cupertino</em></h2>
      <div class="sec-rule"></div>
      <p class="sec-body">
        Matador Rocketry is the competitive division of the
        <strong>Monta Vista High School Rocketry Club</strong>, based in
        Cupertino, CA. We design, build, and fly model rockets that meet the
        strict altitude and flight-time requirements of the
        <strong>American Rocketry Challenge (ARC)</strong> — the world's
        largest student rocket contest.
      </p>
      <p class="sec-body">
        Our team uses industry-standard tools like OpenRocket, real composite
        materials, and develops skills that carry into aerospace careers.
      </p>
      <div class="about-tags">
        <span class="atag">OpenRocket</span>
        <span class="atag">Composite Airframes</span>
        <span class="atag">Avionics</span>
        <span class="atag">Recovery Systems</span>
        <span class="atag">NAR Safety</span>
        <span class="atag">ARC</span>
      </div>
      <a href="https://www.rocketrychallenge.org" target="_blank" rel="noopener noreferrer" class="btn-ghost" style="margin-top:2rem">
        Learn About ARC ↗
      </a>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════════════════════════
     SPONSORS
══════════════════════════════════════════════════════════════ -->
<section id="sponsors" class="sponsors-strip">
  <div class="sponsors-container">
    <span class="sponsors-label reveal">Proud Sponsor</span>
    <a
      href="https://www.simscale.com"
      target="_blank"
      rel="noopener noreferrer"
      class="sponsor-link reveal"
      aria-label="SimScale"
    >
      <img src="/simscale-white.png" alt="SimScale" class="sponsor-img" />
    </a>
    <p class="sponsor-tagline reveal">Cloud-based simulation platform powering our CFD &amp; structural analysis.</p>
  </div>
</section>

<!-- ══════════════════════════════════════════════════════════════
     TEAM
══════════════════════════════════════════════════════════════ -->
<section id="team" class="team-section">
  <div class="content-container">
    <div class="sec-header reveal">
      <span class="sec-num">02</span>
      <span class="sec-label">The Crew</span>
      <h2 class="sec-title">Meet Our <em>Team</em></h2>
      <div class="sec-rule"></div>
      <p class="sec-sub">The brilliant minds behind every rocket — engineers, analysts, builders, and leaders.</p>
    </div>

    <div class="team-grid">
      {#each teamMembers as member, i}
        <article class="member-card reveal" style="--delay:{i * 0.06}s" id="member-{i}">
          <div class="member-num">{String(i + 1).padStart(2, "0")}</div>
          <div class="member-info">
            <h3 class="member-name">{member.name}</h3>
            <p class="member-role">{member.title}</p>
          </div>
          <div class="member-org">MVHS Rocketry</div>
        </article>
      {/each}
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════════════════════════
     GALLERY — editorial layout
══════════════════════════════════════════════════════════════ -->
<section id="gallery" class="gallery-section">
  <div class="content-container">
    <div class="sec-header reveal">
      <span class="sec-num">03</span>
      <span class="sec-label">In Action</span>
      <h2 class="sec-title">Photo <em>Gallery</em></h2>
      <div class="sec-rule"></div>
    </div>

    <!-- Featured -->
    <div class="gallery-featured reveal">
      <img src={galleryImages[activeGallery].src} alt={galleryImages[activeGallery].alt} />
      <div class="gallery-featured-bar">
        <span class="gallery-count">{String(activeGallery + 1).padStart(2,"0")} / {String(galleryImages.length).padStart(2,"0")}</span>
        <span class="gallery-alt">{galleryImages[activeGallery].alt}</span>
      </div>
    </div>

    <!-- Thumbs -->
    <div class="gallery-thumbs reveal">
      {#each galleryImages as img, i}
        <button
          class="gthumb"
          class:active={activeGallery === i}
          on:click={() => (activeGallery = i)}
          aria-label="View image {i + 1}"
          id="gallery-thumb-{i}"
        >
          <img src={img.src} alt={img.alt} loading="lazy" />
        </button>
      {/each}
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════════════════════════
     VIDEOS
══════════════════════════════════════════════════════════════ -->
<section id="videos" class="videos-section">
  <div class="content-container">
    <div class="sec-header reveal">
      <span class="sec-num">04</span>
      <span class="sec-label">Watch Us Fly</span>
      <h2 class="sec-title">Launch <em>Videos</em></h2>
      <div class="sec-rule"></div>
    </div>

    <div class="videos-grid">
      {#each videos as vid, i}
        <div class="video-wrap reveal" style="--delay:{i * 0.08}s" id="video-{vid.id}">
          <video
            src={vid.src}
            controls
            preload="metadata"
            playsinline
            aria-label="Launch video {i + 1}"
          >
            Your browser does not support HTML5 video.
          </video>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════════════════════════════
     CONTACT
══════════════════════════════════════════════════════════════ -->
<section id="contact" class="contact-section">
  <div class="content-container contact-grid">
    <!-- Info -->
    <div class="contact-info reveal">
      <span class="sec-num">05</span>
      <span class="sec-label">Get In Touch</span>
      <h2 class="sec-title">Join the <em>Mission</em></h2>
      <div class="sec-rule"></div>
      <p class="sec-sub" style="max-width:100%">
        Interested in joining Matador Rocketry, partnering as a sponsor, or just
        have a question? We'd love to hear from you.
      </p>

      <div class="contact-list">
        <a href="mailto:mvaerospaceengineering@gmail.com" class="contact-row" id="contact-email-card">
          <div class="contact-row-label">Email</div>
          <div class="contact-row-val">mvaerospaceengineering@gmail.com ↗</div>
        </a>
        <div class="contact-row" id="contact-school-card">
          <div class="contact-row-label">School</div>
          <div class="contact-row-val">Monta Vista High School, Cupertino CA</div>
        </div>
        <a href="https://www.rocketrychallenge.org" target="_blank" rel="noopener noreferrer" class="contact-row" id="contact-arc-card">
          <div class="contact-row-label">Competition</div>
          <div class="contact-row-val">American Rocketry Challenge (ARC) ↗</div>
        </a>
      </div>
    </div>

    <!-- Form -->
    <div class="contact-form-wrap reveal">
      <form class="contact-form" on:submit={handleSubmit} id="contact-form">
        <h3 class="form-heading">Send a Message</h3>

        {#if formStatus === "success"}
          <div class="form-alert ok" role="alert">Opening your email client… Thanks!</div>
        {/if}
        {#if formStatus === "error"}
          <div class="form-alert err" role="alert">Please fill in all fields before sending.</div>
        {/if}

        <div class="form-field">
          <label for="contact-name">Name</label>
          <input id="contact-name" type="text" bind:value={formName} placeholder="Jane Doe" required autocomplete="name" />
        </div>
        <div class="form-field">
          <label for="contact-email">Email</label>
          <input id="contact-email" type="email" bind:value={formEmail} placeholder="you@example.com" required autocomplete="email" />
        </div>
        <div class="form-field">
          <label for="contact-message">Message</label>
          <textarea id="contact-message" rows="5" bind:value={formMessage} placeholder="Tell us why you'd like to join…" required></textarea>
        </div>

        <button type="submit" class="btn-solid submit-btn" id="contact-submit-btn">Send Message</button>
      </form>
    </div>
  </div>
</section>

<style>
  /* ── Reveal ─────────────────────────────────────────────────── */
  .reveal {
    opacity: 0;
    transform: translateY(24px);
    transition:
      opacity 0.7s ease var(--delay, 0s),
      transform 0.7s cubic-bezier(0.2, 0.8, 0.2, 1) var(--delay, 0s);
  }
  :global(.reveal.visible) { opacity: 1; transform: none; }

  /* ── Shared Buttons ─────────────────────────────────────────── */
  .btn-solid {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.85rem 2.2rem;
    border-radius: 3px;
    background: var(--red-core, #E02020);
    color: #fff;
    font-family: 'Outfit', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    letter-spacing: 0.04em;
    text-decoration: none;
    cursor: pointer;
    border: 2px solid var(--red-core, #E02020);
    transition: background 0.2s, transform 0.2s;
  }
  .btn-solid:hover { background: var(--red-bright, #FF2D2D); border-color: var(--red-bright, #FF2D2D); transform: translateY(-2px); }

  .btn-ghost {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.85rem 2.2rem;
    border-radius: 3px;
    background: transparent;
    color: rgba(255,255,255,0.85);
    font-family: 'Outfit', sans-serif;
    font-size: 0.9rem;
    font-weight: 600;
    letter-spacing: 0.04em;
    text-decoration: none;
    cursor: pointer;
    border: 2px solid rgba(255,255,255,0.25);
    transition: border-color 0.2s, color 0.2s, transform 0.2s;
  }
  .btn-ghost:hover { border-color: var(--red-core, #E02020); color: #fff; transform: translateY(-2px); }

  /* ── Shared Section Typography ──────────────────────────────── */
  .sec-num {
    display: block;
    font-family: 'Outfit', sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.3em;
    color: rgba(255,255,255,0.2);
    margin-bottom: 0.35rem;
  }
  .sec-label {
    display: block;
    font-family: 'Outfit', sans-serif;
    font-size: 0.78rem;
    font-weight: 700;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: #E02020;
    margin-bottom: 1.1rem;
  }
  .sec-title {
    font-family: 'Outfit', sans-serif;
    font-size: clamp(2.6rem, 5.5vw, 4rem);
    font-weight: 900;
    line-height: 1.05;
    color: #fff;
    margin-bottom: 1.25rem;
    letter-spacing: -0.02em;
  }
  .sec-title em {
    font-style: normal;
    background: linear-gradient(90deg, #E02020, #FF5555);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .sec-rule {
    width: 40px;
    height: 3px;
    background: #E02020;
    border-radius: 2px;
    margin: 0 0 1.75rem;
  }
  .sec-body {
    font-size: 1rem;
    color: rgba(220,210,255,0.7);
    line-height: 1.8;
    margin-bottom: 1rem;
    max-width: 480px;
  }
  .sec-sub {
    font-size: 1.05rem;
    color: rgba(220,210,255,0.65);
    line-height: 1.75;
    max-width: 520px;
    margin-bottom: 2rem;
  }

  .sec-header {
    margin-bottom: 3.5rem;
  }

  .content-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2.5rem;
  }

  /* ══════════════════════════════════════════════════════════════
     HERO
  ══════════════════════════════════════════════════════════════ */
  .hero {
    min-height: 100vh;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    overflow: hidden;
    background: #060606;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background: url("/media/converted/IMG_3334.jpg") center / cover no-repeat;
    opacity: 0.2;
    z-index: 0;
  }

  .hero-overlay {
    position: absolute;
    inset: 0;
    background:
      linear-gradient(to right, rgba(6,6,6,0.95) 0%, rgba(6,6,6,0.5) 55%, rgba(6,6,6,0.15) 100%),
      linear-gradient(to bottom, rgba(6,6,6,0.2) 0%, rgba(6,6,6,0) 40%, rgba(6,6,6,0.9) 100%);
    z-index: 1;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2.5rem;
    width: 100%;
    padding-top: 7rem;
  }

  .hero-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 0.6rem;
    font-family: 'Outfit', sans-serif;
    font-size: 0.78rem;
    font-weight: 700;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.45);
    margin-bottom: 2rem;
    animation: fade-up 0.8s ease 0.1s both;
  }
  .eyebrow-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: #E02020;
    box-shadow: 0 0 8px rgba(224,32,32,0.8);
    animation: pulse 2s ease infinite;
  }

  .hero-title {
    font-family: 'Outfit', sans-serif;
    font-size: clamp(4rem, 10vw, 8rem);
    font-weight: 900;
    line-height: 0.95;
    letter-spacing: -0.03em;
    color: #fff;
    margin-bottom: 2rem;
    animation: fade-up 0.8s ease 0.25s both;
  }
  .hero-title em {
    font-style: normal;
    background: linear-gradient(90deg, #E02020, #FF5555, #E02020);
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: shimmer 4s linear infinite 1s;
  }

  .hero-sub {
    font-size: clamp(0.95rem, 2vw, 1.1rem);
    color: rgba(220, 210, 255, 0.7);
    line-height: 1.75;
    max-width: 520px;
    margin-bottom: 2.5rem;
    animation: fade-up 0.8s ease 0.4s both;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    animation: fade-up 0.8s ease 0.55s both;
  }

  .hero-stats {
    position: relative;
    z-index: 2;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2.5rem;
    width: 100%;
    display: flex;
    align-items: center;
    gap: 2.5rem;
    padding-bottom: 3.5rem;
    padding-top: 4rem;
    border-top: 1px solid rgba(255,255,255,0.07);
    margin-top: auto;
    animation: fade-up 0.8s ease 0.75s both;
  }
  .hstat {
    display: flex;
    flex-direction: column;
    gap: 0.2rem;
  }
  .hstat-num {
    font-family: 'Outfit', sans-serif;
    font-size: clamp(1.6rem, 3vw, 2.2rem);
    font-weight: 900;
    color: #fff;
    letter-spacing: -0.02em;
  }
  .hstat-lbl {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.35);
  }
  .hstat-rule {
    width: 1px;
    height: 36px;
    background: rgba(255,255,255,0.12);
    flex-shrink: 0;
  }

  .hero-scroll {
    position: absolute;
    bottom: 2rem;
    right: 2.5rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    z-index: 2;
    color: rgba(255,255,255,0.25);
    font-family: 'Outfit', sans-serif;
    font-size: 0.62rem;
    font-weight: 600;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    animation: fade-up 1s ease 1.2s both;
  }
  .scroll-bar {
    width: 1px;
    height: 48px;
    background: linear-gradient(to bottom, #E02020, transparent);
    animation: grow-bar 2s ease-in-out infinite;
  }

  /* ══════════════════════════════════════════════════════════════
     ABOUT — edge-to-edge split
  ══════════════════════════════════════════════════════════════ */
  .about-section {
    background: #060606;
    border-top: 1px solid rgba(255,255,255,0.06);
  }

  .about-split {
    display: grid;
    grid-template-columns: 1fr 1fr;
    min-height: 680px;
  }

  .about-img-side {
    overflow: hidden;
    position: relative;
  }
  .about-img-side img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.8s ease;
  }
  .about-img-side:hover img {
    transform: scale(1.04);
  }

  .about-text-side {
    padding: 5rem 4rem 5rem 5rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    background: #0A0A0A;
  }

  .about-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 1.5rem;
  }
  .atag {
    padding: 0.3rem 0.85rem;
    border-radius: 2px;
    font-family: 'Outfit', sans-serif;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.06em;
    border: 1px solid rgba(224,32,32,0.25);
    color: rgba(255,170,170,0.75);
    background: rgba(224,32,32,0.06);
    transition: all 0.2s;
  }
  .atag:hover {
    border-color: rgba(224,32,32,0.55);
    color: #fff;
    background: rgba(224,32,32,0.15);
  }

  /* ══════════════════════════════════════════════════════════════
     SPONSORS
  ══════════════════════════════════════════════════════════════ */
  .sponsors-strip {
    border-top: 1px solid rgba(255,255,255,0.06);
    border-bottom: 1px solid rgba(255,255,255,0.06);
    background: #0D0D0D;
    padding: 3rem 2.5rem;
  }
  .sponsors-container {
    max-width: 900px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.25rem;
    text-align: center;
  }
  .sponsors-label {
    font-family: 'Outfit', sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.28em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.25);
  }
  .sponsor-link {
    display: inline-block;
    opacity: 0.7;
    transition: opacity 0.25s;
  }
  .sponsor-link:hover { opacity: 1; }
  .sponsor-img {
    height: 42px;
    width: auto;
    object-fit: contain;
    filter: brightness(0) invert(1);
  }
  .sponsor-tagline {
    font-size: 0.85rem;
    color: rgba(200,180,255,0.4);
    line-height: 1.6;
    max-width: 400px;
  }

  /* ══════════════════════════════════════════════════════════════
     TEAM
  ══════════════════════════════════════════════════════════════ */
  .team-section {
    background: #060606;
    border-top: 1px solid rgba(255,255,255,0.06);
    padding: 6rem 0;
  }

  .team-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    border: 1px solid rgba(255,255,255,0.07);
  }

  .member-card {
    padding: 1.75rem 1.5rem;
    border-right: 1px solid rgba(255,255,255,0.07);
    border-bottom: 1px solid rgba(255,255,255,0.07);
    display: flex;
    flex-direction: column;
    gap: 1rem;
    transition: background 0.25s;
    transition-delay: var(--delay, 0s);
    cursor: default;
  }
  .member-card:nth-child(4n) { border-right: none; }
  .member-card:nth-child(n+5) { border-bottom: none; }
  .member-card:hover { background: rgba(224,32,32,0.05); }

  .member-num {
    font-family: 'Outfit', sans-serif;
    font-size: 0.65rem;
    font-weight: 700;
    letter-spacing: 0.2em;
    color: rgba(255,255,255,0.18);
  }
  .member-info { flex: 1; }
  .member-name {
    font-family: 'Outfit', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 0.3rem;
    line-height: 1.25;
  }
  .member-role {
    font-size: 0.8rem;
    color: #E02020;
    font-family: 'Outfit', sans-serif;
    font-weight: 600;
    letter-spacing: 0.04em;
  }
  .member-org {
    font-size: 0.68rem;
    color: rgba(255,255,255,0.2);
    font-family: 'Outfit', sans-serif;
    font-weight: 600;
    letter-spacing: 0.15em;
    text-transform: uppercase;
  }

  /* ══════════════════════════════════════════════════════════════
     GALLERY
  ══════════════════════════════════════════════════════════════ */
  .gallery-section {
    background: #0A0A0A;
    border-top: 1px solid rgba(255,255,255,0.06);
    padding: 6rem 0;
  }

  .gallery-featured {
    position: relative;
    margin-bottom: 1rem;
    overflow: hidden;
    background: #111;
  }
  .gallery-featured img {
    width: 100%;
    height: 560px;
    object-fit: cover;
    display: block;
    transition: transform 0.6s ease;
  }
  .gallery-featured:hover img { transform: scale(1.02); }

  .gallery-featured-bar {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 1.5rem;
    background: linear-gradient(to top, rgba(6,6,6,0.85), transparent);
  }
  .gallery-count {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    color: rgba(255,255,255,0.45);
  }
  .gallery-alt {
    font-size: 0.82rem;
    color: rgba(255,255,255,0.45);
    font-family: 'Space Grotesk', sans-serif;
    max-width: 50%;
    text-align: right;
  }

  .gallery-thumbs {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 4px;
  }
  .gthumb {
    aspect-ratio: 4/3;
    overflow: hidden;
    border: none;
    padding: 0;
    background: none;
    cursor: pointer;
    position: relative;
    outline: none;
  }
  .gthumb img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.4s ease;
    filter: brightness(0.65);
  }
  .gthumb:hover img, .gthumb.active img {
    transform: scale(1.06);
    filter: brightness(1);
  }
  .gthumb.active::after {
    content: '';
    position: absolute;
    inset: 0;
    border: 2px solid #E02020;
    pointer-events: none;
  }

  /* ══════════════════════════════════════════════════════════════
     VIDEOS
  ══════════════════════════════════════════════════════════════ */
  .videos-section {
    background: #060606;
    border-top: 1px solid rgba(255,255,255,0.06);
    padding: 6rem 0;
  }

  .videos-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 4px;
  }

  .video-wrap {
    aspect-ratio: 16/9;
    background: #111;
    overflow: hidden;
    position: relative;
    transition-delay: var(--delay, 0s);
  }
  .video-wrap video {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  /* ══════════════════════════════════════════════════════════════
     CONTACT
  ══════════════════════════════════════════════════════════════ */
  .contact-section {
    background: #0A0A0A;
    border-top: 1px solid rgba(255,255,255,0.06);
    padding: 6rem 0;
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: start;
  }

  .contact-list {
    display: flex;
    flex-direction: column;
    margin-top: 1rem;
    border-top: 1px solid rgba(255,255,255,0.08);
  }
  .contact-row {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    gap: 1rem;
    padding: 1.1rem 0;
    border-bottom: 1px solid rgba(255,255,255,0.06);
    text-decoration: none;
    transition: border-color 0.2s;
  }
  a.contact-row:hover {
    border-bottom-color: rgba(224,32,32,0.4);
  }
  .contact-row-label {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.28);
    flex-shrink: 0;
  }
  .contact-row-val {
    font-size: 0.9rem;
    color: rgba(255,255,255,0.7);
    text-align: right;
    line-height: 1.4;
    transition: color 0.2s;
  }
  a.contact-row:hover .contact-row-val { color: #fff; }

  /* Form */
  .contact-form {
    background: #111;
    border: 1px solid rgba(255,255,255,0.07);
    padding: 2.5rem;
  }
  .form-heading {
    font-family: 'Outfit', sans-serif;
    font-size: 1.3rem;
    font-weight: 800;
    color: #fff;
    margin-bottom: 1.75rem;
    letter-spacing: -0.01em;
  }
  .form-alert {
    padding: 0.75rem 1rem;
    font-size: 0.85rem;
    margin-bottom: 1.25rem;
    border-radius: 2px;
  }
  .form-alert.ok {
    background: rgba(52,211,153,0.08);
    border: 1px solid rgba(52,211,153,0.25);
    color: #6ee7b7;
  }
  .form-alert.err {
    background: rgba(224,32,32,0.08);
    border: 1px solid rgba(224,32,32,0.25);
    color: #ffaaaa;
  }
  .form-field {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    margin-bottom: 1.1rem;
  }
  .form-field label {
    font-family: 'Outfit', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.35);
  }
  .form-field input,
  .form-field textarea {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 2px;
    padding: 0.8rem 1rem;
    font-family: 'Space Grotesk', sans-serif;
    font-size: 0.92rem;
    color: #fff;
    outline: none;
    transition: border-color 0.2s;
    resize: vertical;
  }
  .form-field input::placeholder,
  .form-field textarea::placeholder { color: rgba(255,255,255,0.2); }
  .form-field input:focus,
  .form-field textarea:focus { border-color: rgba(224,32,32,0.5); }

  .submit-btn {
    width: 100%;
    justify-content: center;
    margin-top: 0.5rem;
    border-radius: 2px;
  }

  /* ── Keyframes ──────────────────────────────────────────────── */
  @keyframes fade-up {
    from { opacity: 0; transform: translateY(28px); }
    to   { opacity: 1; transform: none; }
  }
  @keyframes shimmer {
    0%   { background-position: -200% center; }
    100% { background-position: 200% center; }
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0.4; }
  }
  @keyframes grow-bar {
    0%, 100% { transform: scaleY(1); opacity: 0.5; }
    50%       { transform: scaleY(0.5); opacity: 1; }
  }

  /* ── Responsive ─────────────────────────────────────────────── */
  @media (max-width: 1100px) {
    .team-grid { grid-template-columns: repeat(2, 1fr); }
    .member-card:nth-child(4n) { border-right: 1px solid rgba(255,255,255,0.07); }
    .member-card:nth-child(2n) { border-right: none; }
    .member-card:nth-child(n+5) { border-bottom: 1px solid rgba(255,255,255,0.07); }
    .member-card:nth-child(n+7) { border-bottom: none; }
  }

  @media (max-width: 900px) {
    .about-split { grid-template-columns: 1fr; min-height: auto; }
    .about-img-side { height: 420px; }
    .about-text-side { padding: 3.5rem 2.5rem; }
    .gallery-thumbs { grid-template-columns: repeat(4, 1fr); }
    .gallery-featured img { height: 380px; }
    .videos-grid { grid-template-columns: 1fr 1fr; }
    .contact-grid { grid-template-columns: 1fr; gap: 3rem; }
  }

  @media (max-width: 640px) {
    .hero-stats { flex-wrap: wrap; gap: 1.5rem; }
    .hstat-rule { display: none; }
    .team-grid { grid-template-columns: 1fr 1fr; }
    .gallery-thumbs { grid-template-columns: repeat(3, 1fr); }
    .gallery-featured img { height: 280px; }
    .videos-grid { grid-template-columns: 1fr; }
    .hero-title { font-size: clamp(3rem, 12vw, 5rem); }
    .contact-form { padding: 1.75rem; }
  }

  @media (max-width: 420px) {
    .team-grid { grid-template-columns: 1fr; }
    .member-card:nth-child(n) { border-right: none; border-bottom: 1px solid rgba(255,255,255,0.07); }
    .member-card:last-child { border-bottom: none; }
  }
</style>
