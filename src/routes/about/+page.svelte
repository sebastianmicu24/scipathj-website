<script lang="ts">
  const team = [
    {
      name: 'Sebastian Micu',
      role: 'Lead Developer & Creator',
      affiliation: 'Sapienza University of Rome',
      description: 'Medical Resident in Clinical Genetics with a passion for Programming and Machine Learning. Developed SciPathJ as a follow up of thesis research.',
      links: {
        github: 'https://github.com/sebastianmicu24',
        email: 'mailto:sebastian.micu@uniroma1.it'
      }
    }
  ];
  
  const institutions = [
    {
      name: 'Sapienza University of Rome',
      description: 'One of the oldest and most prestigious universities in Italy, providing academic support and research environment.',
      location: 'Rome, Italy'
    },
    {
      name: 'Centro de Biología Molecular Severo Ochoa',
      description: 'Molecular biology research center that provided support and resources for the development of SciPathJ.',
      location: 'Madrid, Spain'
    }
  ];
  
  const milestones = [
    { year: 'October 2024', event: 'The project was born as a Fiji/ImageJ macro to segment cells using Weka and classify them using Random Forest' },
    { year: 'March 2025', event: 'Evolved to a plugin called SCHELI (Segmentation and Classification of H&E slides of the Liver) using Stardist and XGBoost' },
    { year: 'July 2025', event: 'Presented as a Master Thesis at Sapienza University of Rome' },
    { year: 'August 2025', event: 'GUI added and renamed to SciPathJ as it became usable for slides of other tissues, not only liver' },
    { year: 'September 2025', event: 'SciPathJ was presented at the Maker Faire Exposition in Rome' }
  ];
  
  const acknowledgements = [
    'The Centro de Biología Molecular Severo Ochoa in Madrid for research support',
    'Sapienza University of Rome for academic guidance',
    'The open-source community for tools and libraries that made this project possible',
    'All contributors and testers who helped improve SciPathJ'
  ];
</script>

<svelte:head>
  <title>About Us - SciPathJ</title>
  <meta name="description" content="Learn about the team behind SciPathJ, our mission, and the research institutions that support this open-source project." />
</svelte:head>

<div class="about-page">
  <!-- Header -->
  <section class="page-header">
    <div class="container">
      <h1>About Us</h1>
      <p>The story and team behind SciPathJ</p>
    </div>
  </section>
  
  <!-- Mission Section -->
  <section class="section">
    <div class="container">
      <div class="mission-content">
        <h2>Our Mission</h2>
        <p class="mission-statement">
          SciPathJ was created with a simple goal: to make advanced histopathology image analysis accessible to researchers worldwide. We want to eliminate the technical gap needed to quantify histological images. 
        <p>
          We created SciPathj to transform into numbers what we can already see by eye, and maybe even what we cannot see...
        </p>
      </div>
    </div>
  </section>
  
  <!-- Team Section -->
  <section class="section alt-bg">
    <div class="container">
      <div class="section-title">
        <h2>Development Team</h2>
        <p>The people behind SciPathJ</p>
      </div>
      
      <div class="team-grid">
        {#each team as member}
          <div class="team-card">
            <div class="member-avatar">
              <svg xmlns="http://www.w3.org/2000/svg" width="64" height="64" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                <circle cx="12" cy="7" r="4"></circle>
              </svg>
            </div>
            <h3 class="member-name">{member.name}</h3>
            <p class="member-role">{member.role}</p>
            <p class="member-affiliation">{member.affiliation}</p>
            <p class="member-description">{member.description}</p>
            <div class="member-links">
              {#if member.links.github}
                <a href={member.links.github} target="_blank" rel="noopener noreferrer" class="member-link" title="GitHub">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                  </svg>
                </a>
              {/if}
              {#if member.links.email}
                <a href={member.links.email} class="member-link" title="Email">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
                    <polyline points="22,6 12,13 2,6"></polyline>
                  </svg>
                </a>
              {/if}
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>
  
  <!-- Institutions Section -->
  <section class="section">
    <div class="container">
      <div class="section-title">
        <h2>Partner Institutions</h2>
        <p>Academic and research institutions supporting this project</p>
      </div>
      
      <div class="institutions-grid">
        {#each institutions as inst}
          <div class="institution-card">
            <div class="institution-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
                <polyline points="9 22 9 12 15 12 15 22"></polyline>
              </svg>
            </div>
            <h3 class="institution-name">{inst.name}</h3>
            <p class="institution-location">{inst.location}</p>
            <p class="institution-description">{inst.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>
  
  <!-- Timeline Section -->
  <section class="section alt-bg">
    <div class="container">
      <div class="section-title">
        <h2>Project Timeline</h2>
        <p>Key milestones in the development of SciPathJ</p>
      </div>
      
      <div class="timeline">
        {#each milestones as milestone, i}
          <div class="timeline-item">
            <div class="timeline-marker"></div>
            <div class="timeline-content">
              <span class="timeline-year">{milestone.year}</span>
              <p class="timeline-event">{milestone.event}</p>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>
  
  <!-- Open Source Section -->
  <section class="section">
    <div class="container">
      <div class="opensource-content">
        <div class="opensource-text">
          <h2>Open Source Commitment</h2>
          <p>
            SciPathJ is released under the MIT License, ensuring that it remains free and open for the scientific community. 
            We believe that transparency and collaboration are essential for advancing scientific research.
          </p>
          <p>
            The entire codebase is available on GitHub, where we welcome contributions, bug reports, and feature requests 
            from the community.
          </p>
          <div class="opensource-actions">
            <a href="https://github.com/sebastianmicu24/scipathj" target="_blank" rel="noopener noreferrer" class="btn btn-primary">
              View on GitHub
            </a>
            <a href="https://github.com/sebastianmicu24/scipathj/blob/main/LICENSE" target="_blank" rel="noopener noreferrer" class="btn btn-secondary">
              View License
            </a>
          </div>
        </div>
        <div class="opensource-stats">
          <div class="stat-box">
            <span class="stat-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
              </svg>
            </span>
            <span class="stat-label">Open Source</span>
          </div>
          <div class="stat-box">
            <span class="stat-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"></path>
              </svg>
            </span>
            <span class="stat-label">MIT License</span>
          </div>
          <div class="stat-box">
            <span class="stat-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
                <circle cx="9" cy="7" r="4"></circle>
                <path d="M23 21v-2a4 4 0 0 0-3-3.87"></path>
                <path d="M16 3.13a4 4 0 0 1 0 7.75"></path>
              </svg>
            </span>
            <span class="stat-label">Community Driven</span>
          </div>
        </div>
      </div>
    </div>
  </section>
  
  <!-- Acknowledgements -->
  <section class="section alt-bg">
    <div class="container">
      <div class="acknowledgements-content">
        <h2>Acknowledgements</h2>
        <p>We would like to thank the following for their support:</p>
        <ul class="acknowledgements-list">
          {#each acknowledgements as ack}
            <li>{ack}</li>
          {/each}
        </ul>
      </div>
    </div>
  </section>
  
  <!-- Contact Section -->
  <section class="section">
    <div class="container">
      <div class="contact-content">
        <h2>Get in Touch</h2>
        <p>Have questions or want to collaborate? We'd love to hear from you.</p>
        <div class="contact-options">
          <a href="https://github.com/sebastianmicu24/scipathj/issues" target="_blank" rel="noopener noreferrer" class="contact-card">
            <div class="contact-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="12" r="10"></circle>
                <path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"></path>
                <line x1="12" y1="17" x2="12.01" y2="17"></line>
              </svg>
            </div>
            <h4>GitHub Issues</h4>
            <p>Report bugs or request features</p>
          </a>
          <a href="https://github.com/sebastianmicu24/scipathj/discussions" target="_blank" rel="noopener noreferrer" class="contact-card">
            <div class="contact-icon">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path>
              </svg>
            </div>
            <h4>Discussions</h4>
            <p>Join the community conversation</p>
          </a>
        </div>
      </div>
    </div>
  </section>
</div>

<style>
  .about-page {
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
  
  /* Mission Section */
  .mission-content {
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
  }
  
  .mission-content h2 {
    color: var(--color-primary);
    margin-bottom: 1.5rem;
  }
  
  .mission-statement {
    font-size: 1.2rem;
    color: var(--color-gray-700);
    line-height: 1.7;
    font-weight: 500;
  }
  
  .mission-content p {
    color: var(--color-gray-600);
    line-height: 1.7;
  }
  
  /* Team Section */
  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    max-width: 800px;
    margin: 0 auto;
  }
  
  .team-card {
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    padding: 2rem;
    text-align: center;
    transition: all 0.2s ease;
  }
  
  .team-card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
  
  .member-avatar {
    width: 100px;
    height: 100px;
    margin: 0 auto 1.5rem;
    background: var(--color-gray-100);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--color-primary);
  }
  
  .member-name {
    color: var(--color-gray-900);
    margin-bottom: 0.25rem;
  }
  
  .member-role {
    color: var(--color-primary);
    font-weight: 500;
    margin-bottom: 0.25rem;
  }
  
  .member-affiliation {
    color: var(--color-gray-500);
    font-size: 0.9rem;
    margin-bottom: 1rem;
  }
  
  .member-description {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    line-height: 1.6;
    margin-bottom: 1rem;
  }
  
  .member-links {
    display: flex;
    justify-content: center;
    gap: 1rem;
  }
  
  .member-link {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--color-gray-100);
    border-radius: 50%;
    color: var(--color-gray-600);
    transition: all 0.2s ease;
  }
  
  .member-link:hover {
    background: var(--color-primary);
    color: var(--color-white);
  }
  
  /* Institutions Section */
  .institutions-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
  
  .institution-card {
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    padding: 2rem;
    text-align: center;
    transition: all 0.2s ease;
  }
  
  .institution-card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
  
  .institution-icon {
    width: 64px;
    height: 64px;
    margin: 0 auto 1rem;
    background: var(--color-gray-100);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--color-primary);
  }
  
  .institution-name {
    color: var(--color-gray-900);
    margin-bottom: 0.25rem;
  }
  
  .institution-location {
    color: var(--color-gray-500);
    font-size: 0.9rem;
    margin-bottom: 1rem;
  }
  
  .institution-description {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    line-height: 1.6;
    margin: 0;
  }
  
  /* Timeline Section */
  .timeline {
    max-width: 600px;
    margin: 0 auto;
    position: relative;
    padding-left: 30px;
  }
  
  .timeline::before {
    content: '';
    position: absolute;
    left: 10px;
    top: 0;
    bottom: 0;
    width: 2px;
    background: var(--color-gray-300);
  }
  
  .timeline-item {
    position: relative;
    margin-bottom: 1.5rem;
  }
  
  .timeline-marker {
    position: absolute;
    left: -30px;
    top: 5px;
    width: 12px;
    height: 12px;
    background: var(--color-primary);
    border-radius: 50%;
    border: 2px solid var(--color-white);
    box-shadow: 0 0 0 2px var(--color-primary);
  }
  
  .timeline-content {
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    padding: 1rem 1.5rem;
  }
  
  .timeline-year {
    font-weight: 700;
    color: var(--color-primary);
    font-size: 0.9rem;
  }
  
  .timeline-event {
    color: var(--color-gray-600);
    font-size: 0.9rem;
    margin: 0.5rem 0 0;
  }
  
  /* Open Source Section */
  .opensource-content {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
    align-items: center;
  }
  
  .opensource-text h2 {
    color: var(--color-primary);
    margin-bottom: 1rem;
  }
  
  .opensource-text p {
    color: var(--color-gray-600);
    line-height: 1.7;
  }
  
  .opensource-actions {
    display: flex;
    gap: 1rem;
    margin-top: 1.5rem;
    flex-wrap: wrap;
  }
  
  .opensource-stats {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  
  .stat-box {
    display: flex;
    align-items: center;
    gap: 1rem;
    background: var(--color-gray-100);
    padding: 1rem 1.5rem;
    border-radius: 8px;
  }
  
  .stat-icon {
    color: var(--color-primary);
  }
  
  .stat-label {
    font-weight: 500;
    color: var(--color-gray-700);
  }
  
  /* Acknowledgements */
  .acknowledgements-content {
    max-width: 700px;
    margin: 0 auto;
    text-align: center;
  }
  
  .acknowledgements-content h2 {
    color: var(--color-primary);
    margin-bottom: 1rem;
  }
  
  .acknowledgements-content p {
    color: var(--color-gray-600);
    margin-bottom: 1.5rem;
  }
  
  .acknowledgements-list {
    list-style: none;
    padding: 0;
    text-align: left;
    max-width: 500px;
    margin: 0 auto;
  }
  
  .acknowledgements-list li {
    color: var(--color-gray-600);
    padding: 0.75rem 0;
    padding-left: 1.5rem;
    position: relative;
    border-bottom: 1px solid var(--color-gray-200);
  }
  
  .acknowledgements-list li::before {
    content: '>';
    position: absolute;
    left: 0;
    color: var(--color-primary);
    font-weight: bold;
  }
  
  /* Contact Section */
  .contact-content {
    text-align: center;
    max-width: 600px;
    margin: 0 auto;
  }
  
  .contact-content h2 {
    color: var(--color-primary);
    margin-bottom: 1rem;
  }
  
  .contact-content p {
    color: var(--color-gray-600);
    margin-bottom: 2rem;
  }
  
  .contact-options {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
  }
  
  .contact-card {
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
  
  .contact-card:hover {
    border-color: var(--color-primary);
    box-shadow: 0 4px 12px rgba(128, 36, 51, 0.1);
  }
  
  .contact-icon {
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
  
  .contact-card h4 {
    color: var(--color-gray-900);
    margin-bottom: 0.5rem;
  }
  
  .contact-card p {
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
    .opensource-content {
      grid-template-columns: 1fr;
    }
    
    .opensource-stats {
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
    }
    
    .stat-box {
      flex: 1;
      min-width: 150px;
    }
  }
  
  @media (max-width: 768px) {
    .institutions-grid {
      grid-template-columns: 1fr;
    }
    
    .contact-options {
      grid-template-columns: 1fr;
    }
    
    .team-grid {
      grid-template-columns: 1fr;
    }
  }
</style>