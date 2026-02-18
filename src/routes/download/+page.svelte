<script lang="ts">
  const downloadOptions = [
    {
      title: 'SciPathJ Standalone',
      description: 'Complete standalone application. No additional software required.',
      version: 'v1.0.0',
      platform: 'Cross-platform (Java 11+)',
      downloadUrl: 'https://youtu.be/eT4qwPRsZnE',
      size: '~50 MB',
      recommended: true
    },
    {
      title: 'ImageJ/Fiji Plugin',
      description: 'Install as a plugin within ImageJ or Fiji for integrated workflow.',
      version: 'v1.0.0',
      platform: 'ImageJ 1.53+ / Fiji',
      downloadUrl: 'https://youtu.be/eT4qwPRsZnE',
      size: '~45 MB',
      recommended: false
    }
  ];
  
  const requirements = [
    { name: 'Java Runtime', version: 'JRE 11 or higher', notes: 'Required for standalone version' },
    { name: 'ImageJ', version: '1.53 or higher', notes: 'Optional, for plugin version' },
    { name: 'Fiji', version: 'Latest', notes: 'Alternative to ImageJ' },
    { name: 'RAM', version: '8 GB minimum', notes: '16 GB recommended for large images' },
    { name: 'Storage', version: '500 MB', notes: 'For application and temporary files' }
  ];
</script>

<svelte:head>
  <title>Download - SciPathJ</title>
  <meta name="description" content="Download SciPathJ for automated tissue segmentation and cell classification. Available as standalone application or ImageJ/Fiji plugin." />
</svelte:head>

<div class="download-page">
  <!-- Header -->
  <section class="page-header">
    <div class="container">
      <h1>Download SciPathJ</h1>
      <p>Choose the version that best fits your workflow</p>
    </div>
  </section>
  
  <!-- Download Options -->
  <section class="section">
    <div class="container">
      <div class="download-grid">
        {#each downloadOptions as option}
          <div class="download-card" class:recommended={option.recommended}>
            {#if option.recommended}
              <span class="recommended-badge">Recommended</span>
            {/if}
            <h3 class="card-title">{option.title}</h3>
            <p class="card-description">{option.description}</p>
            <div class="card-details">
              <div class="detail-row">
                <span class="detail-label">Version:</span>
                <span class="detail-value">{option.version}</span>
              </div>
              <div class="detail-row">
                <span class="detail-label">Platform:</span>
                <span class="detail-value">{option.platform}</span>
              </div>
              <div class="detail-row">
                <span class="detail-label">Size:</span>
                <span class="detail-value">{option.size}</span>
              </div>
            </div>
            <a href="https://youtu.be/eT4qwPRsZnE" target="_blank" rel="noopener noreferrer" class="btn btn-primary btn-lg download-btn">
              Download
            </a>
          </div>
        {/each}
      </div>
    </div>
  </section>
  
  <!-- Installation Guide -->
  <section class="section alt-bg">
    <div class="container">
      <div class="section-title">
        <h2>Installation Guide</h2>
        <p>Follow these steps to get started with SciPathJ</p>
      </div>
      
      <div class="installation-steps">
        <div class="step">
          <div class="step-number">1</div>
          <div class="step-content">
            <h4>Download</h4>
            <p>Download the appropriate version for your system from the options above.</p>
          </div>
        </div>
        
        <div class="step">
          <div class="step-number">2</div>
          <div class="step-content">
            <h4>Extract</h4>
            <p>Extract the downloaded archive to your preferred location. For the ImageJ plugin, place the .jar file in the plugins folder.</p>
          </div>
        </div>
        
        <div class="step">
          <div class="step-number">3</div>
          <div class="step-content">
            <h4>Run</h4>
            <p>For standalone: run the executable or launch via Java. For ImageJ: restart ImageJ and find SciPathJ in the Plugins menu.</p>
          </div>
        </div>
        
        <div class="step">
          <div class="step-number">4</div>
          <div class="step-content">
            <h4>Configure</h4>
            <p>Set up your preferences and start analyzing your H&E images. Check the tutorials for detailed guidance.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
  
  <!-- System Requirements -->
  <section class="section">
    <div class="container">
      <div class="section-title">
        <h2>System Requirements</h2>
        <p>Ensure your system meets these requirements for optimal performance</p>
      </div>
      
      <div class="requirements-table">
        <div class="table-header">
          <span class="col-name">Component</span>
          <span class="col-version">Requirement</span>
          <span class="col-notes">Notes</span>
        </div>
        {#each requirements as req}
          <div class="table-row">
            <span class="col-name">{req.name}</span>
            <span class="col-version">{req.version}</span>
            <span class="col-notes">{req.notes}</span>
          </div>
        {/each}
      </div>
    </div>
  </section>
  
  <!-- Video Tutorial -->
  <section class="section alt-bg">
    <div class="container">
      <div class="section-title">
        <h2>Installation Video</h2>
        <p>Watch this tutorial for a step-by-step installation guide</p>
      </div>
      
      <div class="video-container">
        <div class="video-wrapper">
          <iframe 
            src="https://www.youtube.com/embed/BkNhT8zFRWk" 
            title="SciPathJ Installation Tutorial" 
            frameborder="0" 
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
            allowfullscreen>
          </iframe>
        </div>
      </div>
    </div>
  </section>
  
  <!-- Alternative Sources -->
  <section class="section">
    <div class="container">
      <div class="section-title">
        <h2>Alternative Sources</h2>
        <p>SciPathJ is also available through these platforms</p>
      </div>
      
      <div class="sources-grid">
        <a href="https://github.com/sebastianmicu24/scipathj" target="_blank" rel="noopener noreferrer" class="source-card">
          <div class="source-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
          </div>
          <h4>GitHub</h4>
          <p>Clone the repository and build from source</p>
        </a>
        
        <a href="https://youtu.be/eT4qwPRsZnE" target="_blank" rel="noopener noreferrer" class="source-card">
          <div class="source-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
              <polyline points="7 10 12 15 17 10"></polyline>
              <line x1="12" y1="15" x2="12" y2="3"></line>
            </svg>
          </div>
          <h4>Releases</h4>
          <p>Download specific versions from GitHub Releases</p>
        </a>
      </div>
    </div>
  </section>
  
  <!-- Help Section -->
  <section class="section alt-bg">
    <div class="container">
      <div class="help-content">
        <h2>Need Help?</h2>
        <p>If you encounter any issues during installation or usage, please check our documentation or open an issue on GitHub.</p>
        <div class="help-actions">
          <a href="/docs" class="btn btn-primary">View Documentation</a>
          <a href="https://github.com/sebastianmicu24/scipathj/issues" target="_blank" rel="noopener noreferrer" class="btn btn-secondary">Report an Issue</a>
        </div>
      </div>
    </div>
  </section>
</div>

<style>
  .download-page {
    flex: 1;
  }
  
  /* Page Header */
  .page-header {
    background: linear-gradient(135deg, var(--color-gray-50) 0%, var(--color-white) 100%);
    padding: 3rem 0;
    text-align: center;
    border-bottom: 1px solid var(--color-gray-200);
  }
  
  .page-header h1 {
    color: var(--color-primary);
    margin-bottom: 0.5rem;
  }
  
  .page-header p {
    color: var(--color-gray-600);
    font-size: 1.1rem;
    margin: 0;
  }
  
  /* Download Grid */
  .download-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
    max-width: 900px;
    margin: 0 auto;
  }
  
  .download-card {
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    padding: 2rem;
    text-align: center;
    position: relative;
    transition: all 0.2s ease;
  }
  
  .download-card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
  
  .download-card.recommended {
    border-color: var(--color-primary);
  }
  
  .recommended-badge {
    position: absolute;
    top: -10px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--color-primary);
    color: var(--color-white);
    padding: 0.25rem 1rem;
    border-radius: 20px;
    font-size: 0.75rem;
    font-weight: 600;
    text-transform: uppercase;
  }
  
  .card-title {
    color: var(--color-gray-900);
    margin-bottom: 0.5rem;
  }
  
  .card-description {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    margin-bottom: 1.5rem;
  }
  
  .card-details {
    background: var(--color-gray-50);
    border-radius: 4px;
    padding: 1rem;
    margin-bottom: 1.5rem;
  }
  
  .detail-row {
    display: flex;
    justify-content: space-between;
    padding: 0.5rem 0;
    border-bottom: 1px solid var(--color-gray-200);
  }
  
  .detail-row:last-child {
    border-bottom: none;
  }
  
  .detail-label {
    color: var(--color-gray-500);
    font-size: 0.85rem;
  }
  
  .detail-value {
    color: var(--color-gray-700);
    font-weight: 500;
    font-size: 0.85rem;
  }
  
  .download-btn {
    width: 100%;
  }
  
  /* Installation Steps */
  .installation-steps {
    max-width: 700px;
    margin: 0 auto;
  }
  
  .step {
    display: flex;
    gap: 1.5rem;
    margin-bottom: 1.5rem;
    align-items: flex-start;
  }
  
  .step-number {
    width: 40px;
    height: 40px;
    background: var(--color-primary);
    color: var(--color-white);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    flex-shrink: 0;
  }
  
  .step-content h4 {
    color: var(--color-gray-900);
    margin-bottom: 0.25rem;
  }
  
  .step-content p {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    margin: 0;
  }
  
  /* Requirements Table */
  .requirements-table {
    max-width: 800px;
    margin: 0 auto;
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    overflow: hidden;
  }
  
  .table-header, .table-row {
    display: grid;
    grid-template-columns: 1fr 1fr 1.5fr;
    padding: 1rem 1.5rem;
  }
  
  .table-header {
    background: var(--color-gray-100);
    font-weight: 600;
    color: var(--color-gray-700);
  }
  
  .table-row {
    border-top: 1px solid var(--color-gray-200);
    color: var(--color-gray-600);
  }
  
  .table-row:nth-child(even) {
    background: var(--color-gray-50);
  }
  
  /* Video Container */
  .video-container {
    max-width: 800px;
    margin: 0 auto;
  }
  
  .video-wrapper {
    position: relative;
    padding-bottom: 56.25%;
    height: 0;
    overflow: hidden;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
  
  .video-wrapper iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  
  /* Sources Grid */
  .sources-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
    max-width: 600px;
    margin: 0 auto;
  }
  
  .source-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 2rem;
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    transition: all 0.2s ease;
    text-decoration: none;
  }
  
  .source-card:hover {
    border-color: var(--color-primary);
    box-shadow: 0 4px 12px rgba(128, 36, 51, 0.1);
  }
  
  .source-icon {
    width: 64px;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--color-gray-100);
    border-radius: 50%;
    margin-bottom: 1rem;
    color: var(--color-primary);
  }
  
  .source-card h4 {
    color: var(--color-gray-900);
    margin-bottom: 0.5rem;
  }
  
  .source-card p {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    margin: 0;
  }
  
  /* Help Section */
  .help-content {
    text-align: center;
    max-width: 600px;
    margin: 0 auto;
  }
  
  .help-content h2 {
    color: var(--color-primary);
    margin-bottom: 1rem;
  }
  
  .help-content p {
    color: var(--color-gray-600);
    margin-bottom: 1.5rem;
  }
  
  .help-actions {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
  }
  
  /* Alt Background */
  .alt-bg {
    background-color: var(--color-gray-50);
  }
  
  /* Responsive */
  @media (max-width: 768px) {
    .download-grid {
      grid-template-columns: 1fr;
    }
    
    .sources-grid {
      grid-template-columns: 1fr;
    }
    
    .table-header, .table-row {
      grid-template-columns: 1fr;
      gap: 0.25rem;
    }
    
    .table-header span, .table-row span {
      font-size: 0.85rem;
    }
  }
</style>