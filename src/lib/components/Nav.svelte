<script lang="ts">
  let isMenuOpen = $state(false);
  
  const navLinks = [
    { href: '/', label: 'Home' },
    { href: '/download', label: 'Download' },
    { href: '/examples', label: 'Examples' },
    { href: '/tutorials', label: 'Tutorials' },
    { href: '/docs', label: 'Docs' },
    { href: '/about', label: 'About Us' }
  ];
  
  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }
  
  function closeMenu() {
    isMenuOpen = false;
  }
</script>

<nav class="nav">
  <div class="nav-container">
    <a href="/" class="nav-logo">
      <span class="logo-text">SciPathJ</span>
    </a>
    
    <button class="nav-toggle" onclick={toggleMenu} aria-label="Toggle navigation" aria-expanded={isMenuOpen}>
      <span class="hamburger-line"></span>
      <span class="hamburger-line"></span>
      <span class="hamburger-line"></span>
    </button>
    
    <ul class="nav-menu" class:open={isMenuOpen}>
      {#each navLinks as link}
        <li class="nav-item">
          <a href={link.href} class="nav-link" onclick={closeMenu}>{link.label}</a>
        </li>
      {/each}
      <li class="nav-item">
        <a href="https://github.com/sebastianmicu24/scipathj" target="_blank" rel="noopener noreferrer" class="nav-link nav-github">
          GitHub
        </a>
      </li>
    </ul>
  </div>
</nav>

<style>
  .nav {
    background-color: var(--color-white);
    border-bottom: 1px solid var(--color-gray-200);
    position: sticky;
    top: 0;
    z-index: 1000;
    height: var(--header-height);
  }
  
  .nav-container {
    max-width: var(--max-width);
    margin: 0 auto;
    padding: 0 1.5rem;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  .nav-logo {
    display: flex;
    align-items: center;
    text-decoration: none;
  }
  
  .logo-text {
    font-family: var(--font-heading);
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--color-primary);
  }
  
  .nav-menu {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  .nav-link {
    display: block;
    padding: 0.5rem 1rem;
    font-size: 0.95rem;
    font-weight: 500;
    color: var(--color-text-secondary);
    text-decoration: none;
    border-radius: 4px;
    transition: all 0.2s ease;
  }
  
  .nav-link:hover {
    color: var(--color-primary-light);
    background-color: var(--color-bg-tertiary);
  }
  
  .nav-github {
    background-color: var(--color-primary);
    color: var(--color-white);
    margin-left: 0.5rem;
  }
  
  .nav-github:hover {
    transform: scale(1.05);
    opacity: 0.9;
    color: var(--color-white);
    background-color: var(--color-primary);
  }
  
  .nav-toggle {
    display: none;
    flex-direction: column;
    justify-content: space-between;
    width: 28px;
    height: 20px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0;
  }
  
  .hamburger-line {
    display: block;
    width: 100%;
    height: 2px;
    background-color: var(--color-text-secondary);
    transition: all 0.2s ease;
  }
  
  @media (max-width: 768px) {
    .nav-toggle {
      display: flex;
    }
    
    .nav-menu {
      position: absolute;
      top: var(--header-height);
      left: 0;
      right: 0;
      flex-direction: column;
      background-color: var(--color-white);
      border-bottom: 1px solid var(--color-gray-200);
      padding: 1rem;
      gap: 0;
      display: none;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
    }
    
    .nav-menu.open {
      display: flex;
    }
    
    .nav-item {
      width: 100%;
    }
    
    .nav-link {
      padding: 0.75rem 1rem;
      width: 100%;
    }
    
    .nav-github {
      margin-left: 0;
      margin-top: 0.5rem;
      text-align: center;
    }
  }
</style>