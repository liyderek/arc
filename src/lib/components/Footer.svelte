<footer class="footer">
  <div class="footer-glow"></div>
  <div class="container footer-inner">
    <div class="footer-brand">
      <div class="footer-logo-row">
        <img src="/logo.png" alt="Matador Rocketry" class="footer-logo-img" />
        <span class="footer-name">Matador Rocketry</span>
      </div>
      <p class="footer-desc">Monta Vista High School's competitive rocketry team, representing Cupertino in the American Rocketry Challenge.</p>
      <div class="footer-socials">
        <a href="mailto:mvaerospaceengineering@gmail.com" class="social-pill" id="footer-email-link" aria-label="Email us">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
          Email Us
        </a>
        <a href="https://www.rocketrychallenge.org" target="_blank" rel="noopener noreferrer" class="social-pill" id="footer-arc-link" aria-label="ARC Website">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><circle cx="12" cy="12" r="10"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/><path d="M2 12h20"/></svg>
          ARC
        </a>
      </div>
    </div>

    <div class="footer-links-col">
      <h4 class="footer-col-title">Navigate</h4>
      <ul role="list">
        <li><a href="#about">About</a></li>
        <li><a href="#team">Team</a></li>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#videos">Videos</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </div>

    <div class="footer-links-col">
      <h4 class="footer-col-title">Resources</h4>
      <ul role="list">
        <li><a href="https://www.rocketrychallenge.org" target="_blank" rel="noopener noreferrer">ARC Official</a></li>
        <li><a href="https://www.nar.org" target="_blank" rel="noopener noreferrer">NAR</a></li>
        <li><a href="https://mvhs.fuhsd.org" target="_blank" rel="noopener noreferrer">Monta Vista HS</a></li>
      </ul>
    </div>
  </div>

  <div class="footer-bottom container">
    <p>© {new Date().getFullYear()} Matador Rocketry · Monta Vista High School · Cupertino, CA</p>
    <p class="footer-tagline">Ad Astra</p>
  </div>
</footer>

<style>
  .footer {
    background: linear-gradient(180deg, #0A0A0A 0%, #060606 100%);
    border-top: 1px solid rgba(224, 32, 32, 0.18);
    padding: 4rem 0 0;
    position: relative;
    overflow: hidden;
  }

  .footer-glow {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 600px;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(224,32,32,0.55), transparent);
  }

  .footer-inner {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    gap: 3rem;
    padding-bottom: 3rem;
  }

  .footer-logo-row {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    margin-bottom: 0.9rem;
  }
  .footer-logo-img {
    width: 32px;
    height: 32px;
    object-fit: contain;
    filter: drop-shadow(0 0 4px rgba(224,32,32,0.5));
  }
  .footer-name {
    font-family: 'Outfit', sans-serif;
    font-size: 1.1rem;
    font-weight: 800;
    color: #fff;
  }

  .footer-desc {
    color: rgba(200, 180, 255, 0.6);
    font-size: 0.9rem;
    line-height: 1.68;
    max-width: 300px;
    margin-bottom: 1.25rem;
  }

  .footer-socials {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  .social-pill {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.45rem 0.9rem;
    border-radius: 99px;
    border: 1px solid rgba(224, 32, 32, 0.3);
    color: rgba(255, 170, 170, 0.85);
    font-size: 0.82rem;
    font-family: 'Outfit', sans-serif;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s ease;
  }
  .social-pill:hover {
    border-color: #E02020;
    color: #fff;
    background: rgba(224,32,32,0.12);
  }

  .footer-col-title {
    font-family: 'Outfit', sans-serif;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: #E02020;
    margin-bottom: 1rem;
  }
  .footer-links-col ul { list-style: none; display: flex; flex-direction: column; gap: 0.55rem; }
  .footer-links-col a {
    color: rgba(200, 180, 255, 0.65);
    text-decoration: none;
    font-size: 0.9rem;
    transition: color 0.2s ease;
  }
  .footer-links-col a:hover { color: #fff; }

  .footer-bottom {
    border-top: 1px solid rgba(224, 32, 32, 0.12);
    padding: 1.5rem 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    flex-wrap: wrap;
  }
  .footer-bottom p {
    font-size: 0.82rem;
    color: rgba(200, 180, 255, 0.45);
  }
  .footer-tagline { font-size: 0.9rem !important; color: rgba(224,32,32,0.65) !important; }

  @media (max-width: 768px) {
    .footer-inner {
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
    }
    .footer-brand { grid-column: 1 / -1; }
    .footer-bottom { flex-direction: column; text-align: center; }
  }
  @media (max-width: 500px) {
    .footer-inner { grid-template-columns: 1fr; }
  }
</style>
