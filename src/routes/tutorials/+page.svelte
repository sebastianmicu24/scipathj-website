<script lang="ts">
  const tutorials = [
    {
      id: 1,
      title: 'Getting Started with SciPathJ',
      description: 'Learn the basics of SciPathJ, including installation, interface overview, and your first segmentation.',
      duration: '15 min',
      level: 'Beginner',
      videoUrl: 'https://www.youtube.com/embed/BkNhT8zFRWk',
      topics: ['Installation', 'Interface Overview', 'Basic Workflow']
    },
    {
      id: 2,
      title: 'Image Segmentation Deep Dive',
      description: 'Comprehensive guide to segmenting cells, nuclei, cytoplasm, and vessels from H&E images.',
      duration: '25 min',
      level: 'Intermediate',
      videoUrl: '',
      topics: ['Cell Segmentation', 'Nuclei Detection', 'Vessel Identification']
    },
    {
      id: 3,
      title: 'Training Custom Classifiers',
      description: 'Learn how to define custom cell classes and train XGBoost models for automated classification.',
      duration: '30 min',
      level: 'Advanced',
      videoUrl: '',
      topics: ['Cell Classes', 'XGBoost Training', 'Model Validation']
    },
    {
      id: 4,
      title: 'Batch Processing Workflows',
      description: 'Process entire folders of images efficiently with batch processing techniques.',
      duration: '20 min',
      level: 'Intermediate',
      videoUrl: '',
      topics: ['Batch Processing', 'Automation', 'Output Management']
    },
    {
      id: 5,
      title: 'Feature Extraction & Analysis',
      description: 'Understand the 150+ features extracted and how to use them for downstream analysis.',
      duration: '25 min',
      level: 'Intermediate',
      videoUrl: '',
      topics: ['Feature Overview', 'CSV Export', 'Data Analysis']
    },
    {
      id: 6,
      title: 'Integration with ImageJ/Fiji',
      description: 'Use SciPathJ as a plugin within ImageJ or Fiji for seamless workflow integration.',
      duration: '15 min',
      level: 'Beginner',
      videoUrl: '',
      topics: ['Plugin Installation', 'ImageJ Integration', 'Workflow Tips']
    }
  ];
  
  const levels = ['All', 'Beginner', 'Intermediate', 'Advanced'];
  let selectedLevel = $state('All');
  
  const filteredTutorials = $derived(
    selectedLevel === 'All' 
      ? tutorials 
      : tutorials.filter(t => t.level === selectedLevel)
  );
</script>

<svelte:head>
  <title>Tutorials - SciPathJ</title>
  <meta name="description" content="Learn how to use SciPathJ with our comprehensive tutorials. From basic installation to advanced classification techniques." />
</svelte:head>

<div class="tutorials-page">
  <!-- Header -->
  <section class="page-header">
    <div class="container">
      <h1>Tutorials</h1>
      <p>Learn SciPathJ step by step with our comprehensive guides</p>
    </div>
  </section>
  
  <!-- Filter Section -->
  <section class="filter-section">
    <div class="container">
      <div class="filter-bar">
        <span class="filter-label">Filter by level:</span>
        <div class="filter-buttons">
          {#each levels as level}
            <button 
              class="filter-btn" 
              class:active={selectedLevel === level}
              onclick={() => selectedLevel = level}>
              {level}
            </button>
          {/each}
        </div>
      </div>
    </div>
  </section>
  
  <!-- Featured Video -->
  <section class="section">
    <div class="container">
      <div class="featured-tutorial">
        <div class="featured-content">
          <span class="featured-badge">Featured Tutorial</span>
          <h2>Getting Started with SciPathJ</h2>
          <p>This comprehensive tutorial covers everything you need to get started with SciPathJ, from installation to your first successful segmentation.</p>
          <ul class="featured-topics">
            <li>Complete installation walkthrough</li>
            <li>Interface and navigation overview</li>
            <li>Step-by-step first segmentation</li>
            <li>Tips for optimal results</li>
          </ul>
        </div>
        <div class="featured-video">
          <div class="video-wrapper">
            <iframe 
              src="https://www.youtube.com/embed/BkNhT8zFRWk" 
              title="Getting Started with SciPathJ" 
              frameborder="0" 
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
              allowfullscreen>
            </iframe>
          </div>
        </div>
      </div>
    </div>
  </section>
  
  <!-- Tutorials Grid -->
  <section class="section alt-bg">
    <div class="container">
      <div class="section-title">
        <h2>All Tutorials</h2>
        <p>Browse our complete collection of tutorials</p>
      </div>
      
      <div class="tutorials-grid">
        {#each filteredTutorials as tutorial}
          <div class="tutorial-card">
            <div class="card-header">
              <span class="level-badge" class:beginner={tutorial.level === 'Beginner'} class:intermediate={tutorial.level === 'Intermediate'} class:advanced={tutorial.level === 'Advanced'}>
                {tutorial.level}
              </span>
              <span class="duration">{tutorial.duration}</span>
            </div>
            <h3 class="card-title">{tutorial.title}</h3>
            <p class="card-description">{tutorial.description}</p>
            <div class="card-topics">
              {#each tutorial.topics as topic}
                <span class="topic-tag">{topic}</span>
              {/each}
            </div>
            {#if tutorial.videoUrl}
              <a href={tutorial.videoUrl} class="btn btn-primary card-btn" target="_blank" rel="noopener noreferrer">
                Watch Tutorial
              </a>
            {:else}
              <button class="btn btn-secondary card-btn" disabled>
                Coming Soon
              </button>
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </section>
  
  <!-- Learning Path -->
  <section class="section">
    <div class="container">
      <div class="section-title">
        <h2>Recommended Learning Path</h2>
        <p>Follow this sequence for the best learning experience</p>
      </div>
      
      <div class="learning-path">
        <div class="path-step">
          <div class="path-number">1</div>
          <div class="path-content">
            <h4>Start with Basics</h4>
            <p>Complete the "Getting Started" tutorial to understand the interface and basic workflow.</p>
          </div>
        </div>
        <div class="path-connector"></div>
        <div class="path-step">
          <div class="path-number">2</div>
          <div class="path-content">
            <h4>Master Segmentation</h4>
            <p>Learn detailed segmentation techniques for different tissue components.</p>
          </div>
        </div>
        <div class="path-connector"></div>
        <div class="path-step">
          <div class="path-number">3</div>
          <div class="path-content">
            <h4>Explore Features</h4>
            <p>Understand the extracted features and how to use them for analysis.</p>
          </div>
        </div>
        <div class="path-connector"></div>
        <div class="path-step">
          <div class="path-number">4</div>
          <div class="path-content">
            <h4>Train Classifiers</h4>
            <p>Create custom cell classes and train machine learning models.</p>
          </div>
        </div>
        <div class="path-connector"></div>
        <div class="path-step">
          <div class="path-number">5</div>
          <div class="path-content">
            <h4>Automate Workflows</h4>
            <p>Set up batch processing for efficient analysis of large datasets.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
  
  <!-- Resources -->
  <section class="section alt-bg">
    <div class="container">
      <div class="section-title">
        <h2>Additional Resources</h2>
        <p>Supplementary materials to support your learning</p>
      </div>
      
      <div class="resources-grid">
        <a href="/docs" class="resource-card">
          <div class="resource-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
              <polyline points="14 2 14 8 20 8"></polyline>
              <line x1="16" y1="13" x2="8" y2="13"></line>
              <line x1="16" y1="17" x2="8" y2="17"></line>
              <polyline points="10 9 9 9 8 9"></polyline>
            </svg>
          </div>
          <h4>Documentation</h4>
          <p>Complete technical documentation and API reference</p>
        </a>
        
        <a href="https://github.com/sebastianmicu24/scipathj" target="_blank" rel="noopener noreferrer" class="resource-card">
          <div class="resource-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
          </div>
          <h4>GitHub Repository</h4>
          <p>Source code, issues, and community contributions</p>
        </a>
        
        <a href="https://github.com/sebastianmicu24/scipathj/issues" target="_blank" rel="noopener noreferrer" class="resource-card">
          <div class="resource-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="12" cy="12" r="10"></circle>
              <path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"></path>
              <line x1="12" y1="17" x2="12.01" y2="17"></line>
            </svg>
          </div>
          <h4>Community Support</h4>
          <p>Ask questions and get help from the community</p>
        </a>
      </div>
    </div>
  </section>
</div>

<style>
  .tutorials-page {
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
  
  /* Filter Section */
  .filter-section {
    padding: 1.5rem 0;
    background: var(--color-white);
    border-bottom: 1px solid var(--color-gray-200);
  }
  
  .filter-bar {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
  }
  
  .filter-label {
    color: var(--color-gray-600);
    font-weight: 500;
  }
  
  .filter-buttons {
    display: flex;
    gap: 0.5rem;
  }
  
  .filter-btn {
    padding: 0.5rem 1rem;
    border: 1px solid var(--color-gray-300);
    background: var(--color-white);
    border-radius: 20px;
    cursor: pointer;
    font-size: 0.9rem;
    color: var(--color-gray-600);
    transition: all 0.2s ease;
  }
  
  .filter-btn:hover {
    border-color: var(--color-primary);
    color: var(--color-primary);
  }
  
  .filter-btn.active {
    background: var(--color-primary);
    border-color: var(--color-primary);
    color: var(--color-white);
  }
  
  /* Featured Tutorial */
  .featured-tutorial {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
    align-items: center;
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 12px;
    padding: 2rem;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  }
  
  .featured-badge {
    display: inline-block;
    background: var(--color-primary);
    color: var(--color-white);
    padding: 0.25rem 0.75rem;
    border-radius: 4px;
    font-size: 0.75rem;
    font-weight: 600;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }
  
  .featured-content h2 {
    color: var(--color-gray-900);
    margin-bottom: 1rem;
  }
  
  .featured-content p {
    color: var(--color-gray-600);
    margin-bottom: 1.5rem;
  }
  
  .featured-topics {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .featured-topics li {
    color: var(--color-gray-700);
    padding: 0.5rem 0;
    padding-left: 1.5rem;
    position: relative;
  }
  
  .featured-topics li::before {
    content: '>';
    position: absolute;
    left: 0;
    color: var(--color-primary);
    font-weight: bold;
  }
  
  .featured-video .video-wrapper {
    position: relative;
    padding-bottom: 56.25%;
    height: 0;
    overflow: hidden;
    border-radius: 8px;
  }
  
  .featured-video iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  
  /* Tutorials Grid */
  .tutorials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  
  .tutorial-card {
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    transition: all 0.2s ease;
  }
  
  .tutorial-card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    border-color: var(--color-primary);
  }
  
  .card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
  }
  
  .level-badge {
    font-size: 0.75rem;
    font-weight: 600;
    padding: 0.25rem 0.75rem;
    border-radius: 4px;
    text-transform: uppercase;
  }
  
  .level-badge.beginner {
    background: #d4edda;
    color: #155724;
  }
  
  .level-badge.intermediate {
    background: #fff3cd;
    color: #856404;
  }
  
  .level-badge.advanced {
    background: #f8d7da;
    color: #721c24;
  }
  
  .duration {
    color: var(--color-gray-500);
    font-size: 0.85rem;
  }
  
  .tutorial-card .card-title {
    font-size: 1.1rem;
    color: var(--color-gray-900);
    margin-bottom: 0.75rem;
  }
  
  .tutorial-card .card-description {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    flex: 1;
    margin-bottom: 1rem;
  }
  
  .card-topics {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-bottom: 1rem;
  }
  
  .topic-tag {
    background: var(--color-gray-100);
    color: var(--color-gray-600);
    padding: 0.25rem 0.5rem;
    border-radius: 4px;
    font-size: 0.75rem;
  }
  
  .card-btn {
    width: 100%;
    text-align: center;
  }
  
  .card-btn:disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }
  
  /* Learning Path */
  .learning-path {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 600px;
    margin: 0 auto;
  }
  
  .path-step {
    display: flex;
    gap: 1.5rem;
    align-items: flex-start;
    width: 100%;
  }
  
  .path-number {
    width: 48px;
    height: 48px;
    background: var(--color-primary);
    color: var(--color-white);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 1.25rem;
    flex-shrink: 0;
  }
  
  .path-content {
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    padding: 1.25rem;
    flex: 1;
  }
  
  .path-content h4 {
    color: var(--color-gray-900);
    margin-bottom: 0.5rem;
  }
  
  .path-content p {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    margin: 0;
  }
  
  .path-connector {
    width: 2px;
    height: 30px;
    background: var(--color-gray-300);
  }
  
  /* Resources Grid */
  .resources-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  
  .resource-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 2rem;
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    text-decoration: none;
    transition: all 0.2s ease;
  }
  
  .resource-card:hover {
    border-color: var(--color-primary);
    box-shadow: 0 4px 12px rgba(128, 36, 51, 0.1);
  }
  
  .resource-icon {
    width: 56px;
    height: 56px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--color-gray-100);
    border-radius: 50%;
    margin-bottom: 1rem;
    color: var(--color-primary);
  }
  
  .resource-card h4 {
    color: var(--color-gray-900);
    margin-bottom: 0.5rem;
  }
  
  .resource-card p {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    margin: 0;
  }
  
  /* Alt Background */
  .alt-bg {
    background-color: var(--color-gray-50);
  }
  
  /* Responsive */
  @media (max-width: 992px) {
    .featured-tutorial {
      grid-template-columns: 1fr;
    }
    
    .tutorials-grid {
      grid-template-columns: repeat(2, 1fr);
    }
    
    .resources-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  
  @media (max-width: 768px) {
    .tutorials-grid {
      grid-template-columns: 1fr;
    }
    
    .resources-grid {
      grid-template-columns: 1fr;
    }
    
    .filter-bar {
      flex-direction: column;
      gap: 0.75rem;
    }
  }
</style>