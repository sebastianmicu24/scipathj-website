<script lang="ts">
  const currentYear = new Date().getFullYear();
</script>

<footer class="footer">
  <div class="footer-container">
    <div class="footer-content">
      <div class="footer-section">
        <h3 class="footer-title">SciPathJ</h3>
        <p class="footer-description">
          Open-source software for automated tissue segmentation and cell classification from H&E stained histology images.
        </p>
      </div>
      
      <div class="footer-section">
        <h4 class="footer-subtitle">Quick Links</h4>
        <ul class="footer-links">
          <li><a href="/">Home</a></li>
          <li><a href="/download">Download</a></li>
          <li><a href="/examples">Examples</a></li>
          <li><a href="/tutorials">Tutorials</a></li>
          <li><a href="/docs">Documentation</a></li>
          <li><a href="/about">About Us</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="footer-subtitle">Resources</h4>
        <ul class="footer-links">
          <li><a href="https://github.com/sebastianmicu24/scipathj" target="_blank" rel="noopener noreferrer">GitHub Repository</a></li>
          <li><a href="https://github.com/sebastianmicu24/scipathj/issues" target="_blank" rel="noopener noreferrer">Report an Issue</a></li>
          <li><a href="https://github.com/sebastianmicu24/scipathj/blob/main/LICENSE" target="_blank" rel="noopener noreferrer">License</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="footer-subtitle">Contact</h4>
        <p class="footer-contact">
          For questions and support, please open an issue on GitHub or contact the development team.
        </p>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p class="copyright">© {currentYear} SciPathJ Team. Open-source under GPLv3 License.</p>
    </div>
  </div>
</footer>

<style>
  .footer {
    background-color: var(--color-bg-secondary);
    color: var(--color-text-secondary);
    margin-top: auto;
    padding: 3rem 0 1.5rem;
    border-top: 1px solid var(--color-border-subtle);
  }
  
  .footer-container {
    max-width: var(--max-width);
    margin: 0 auto;
    padding: 0 1.5rem;
  }
  
  .footer-content {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2rem;
    margin-bottom: 2rem;
  }
  
  .footer-section {
    display: flex;
    flex-direction: column;
  }
  
  .footer-title {
    font-family: var(--font-heading);
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--color-primary);
    margin-bottom: 0.75rem;
  }
  
  .footer-subtitle {
    font-size: 1rem;
    font-weight: 600;
    color: var(--color-text-primary);
    margin-bottom: 0.75rem;
  }
  
  .footer-description {
    font-size: 0.9rem;
    line-height: 1.6;
    color: var(--color-text-muted);
  }
  
  .footer-links {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .footer-links li {
    margin-bottom: 0.5rem;
  }
  
  .footer-links a {
    color: var(--color-text-muted);
    font-size: 0.9rem;
    transition: color 0.2s ease;
  }
  
  .footer-links a:hover {
    color: var(--color-primary-light);
  }
  
  .footer-contact {
    font-size: 0.9rem;
    color: var(--color-text-muted);
    line-height: 1.6;
  }
  
  .footer-bottom {
    border-top: 1px solid var(--color-border-subtle);
    padding-top: 1.5rem;
    text-align: center;
  }
  
  .copyright {
    font-size: 0.85rem;
    color: var(--color-text-subtle);
    margin: 0;
  }
  
  @media (max-width: 992px) {
    .footer-content {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  
  @media (max-width: 576px) {
    .footer-content {
      grid-template-columns: 1fr;
      gap: 1.5rem;
    }
    
    .footer {
      padding: 2rem 0 1rem;
    }
  }
</style>