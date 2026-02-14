<script lang="ts">
  const sections = [
    {
      id: 'introduction',
      title: 'Introduction',
      content: `
        <p>SciPathJ (Segmentation and Classification of Images - Pipeline for the Analysis of Tissue Histopathology) is a Java-based software designed for automated analysis of H&E-stained microscopy images.</p>
        <p>The software provides a complete pipeline for:</p>
        <ul>
          <li>Automated segmentation of cells, nuclei, cytoplasm, and vessels</li>
          <li>Extraction of 150+ morphological and color features</li>
          <li>Custom cell class definition and training</li>
          <li>Machine learning-based cell classification using XGBoost</li>
          <li>Batch processing of entire image folders</li>
        </ul>
      `
    },
    {
      id: 'installation',
      title: 'Installation',
      content: `
        <h3>System Requirements</h3>
        <ul>
          <li>Java Runtime Environment (JRE) 11 or higher</li>
          <li>8 GB RAM minimum (16 GB recommended for large images)</li>
          <li>500 MB disk space</li>
        </ul>
        
        <h3>Standalone Installation</h3>
        <ol>
          <li>Download the latest release from the <a href="/download">Download page</a></li>
          <li>Extract the archive to your preferred location</li>
          <li>Run the executable or launch via: <code>java -jar scipathj.jar</code></li>
        </ol>
        
        <h3>ImageJ/Fiji Plugin Installation</h3>
        <ol>
          <li>Download the plugin .jar file</li>
          <li>Place it in the <code>plugins</code> folder of your ImageJ/Fiji installation</li>
          <li>Restart ImageJ/Fiji</li>
          <li>Access SciPathJ from Plugins > SciPathJ</li>
        </ol>
      `
    },
    {
      id: 'quickstart',
      title: 'Quick Start Guide',
      content: `
        <h3>Your First Segmentation</h3>
        <ol>
          <li><strong>Load an image:</strong> File > Open or drag and drop an H&E image</li>
          <li><strong>Configure settings:</strong> Adjust segmentation parameters in Settings > Segmentation</li>
          <li><strong>Run segmentation:</strong> Process > Segment Image</li>
          <li><strong>Review results:</strong> View segmented regions in the Results panel</li>
          <li><strong>Export data:</strong> File > Export > CSV to save measurements</li>
        </ol>
        
        <h3>Basic Configuration</h3>
        <p>The main configuration options are accessible through the Settings menu:</p>
        <ul>
          <li><strong>Nuclei Detection:</strong> Adjust minimum/maximum size, intensity threshold</li>
          <li><strong>Cell Boundary:</strong> Set expansion factor for cytoplasm detection</li>
          <li><strong>Vessel Detection:</strong> Configure minimum area and shape parameters</li>
        </ul>
      `
    },
    {
      id: 'segmentation',
      title: 'Segmentation Module',
      content: `
        <h3>Overview</h3>
        <p>The segmentation module identifies and delineates the following structures:</p>
        
        <h4>Nuclei Detection</h4>
        <p>Uses hematoxylin channel intensity to identify nuclei. Parameters:</p>
        <ul>
          <li><code>nuclei.minSize</code> - Minimum nucleus area in pixels</li>
          <li><code>nuclei.maxSize</code> - Maximum nucleus area in pixels</li>
          <li><code>nuclei.threshold</code> - Intensity threshold (0-255)</li>
          <li><code>nuclei.circularity</code> - Minimum circularity (0-1)</li>
        </ul>
        
        <h4>Cytoplasm Segmentation</h4>
        <p>Extends from nuclei boundaries using eosin channel:</p>
        <ul>
          <li><code>cytoplasm.expansion</code> - Expansion factor from nucleus edge</li>
          <li><code>cytoplasm.threshold</code> - Eosin intensity threshold</li>
        </ul>
        
        <h4>Vessel Detection</h4>
        <p>Identifies vascular structures based on morphology:</p>
        <ul>
          <li><code>vessel.minArea</code> - Minimum vessel area</li>
          <li><code>vessel.maxArea</code> - Maximum vessel area</li>
          <li><code>vessel.elongation</code> - Minimum elongation factor</li>
        </ul>
      `
    },
    {
      id: 'features',
      title: 'Feature Extraction',
      content: `
        <h3>Available Features</h3>
        <p>SciPathJ extracts over 150 features organized into categories:</p>
        
        <h4>Morphological Features</h4>
        <ul>
          <li>Area, Perimeter, Circularity</li>
          <li>Major/Minor Axis, Aspect Ratio</li>
          <li>Feret Diameter, Roundness</li>
          <li>Solidity, Convexity</li>
        </ul>
        
        <h4>Intensity Features</h4>
        <ul>
          <li>Mean, Median, Mode intensity</li>
          <li>Standard deviation, Variance</li>
          <li>Min, Max intensity values</li>
          <li>Integrated density</li>
        </ul>
        
        <h4>Color Features</h4>
        <ul>
          <li>Hematoxylin intensity (nuclear stain)</li>
          <li>Eosin intensity (cytoplasmic stain)</li>
          <li>DAB intensity (if applicable)</li>
          <li>Color histogram features</li>
        </ul>
        
        <h4>Texture Features</h4>
        <ul>
          <li>Haralick features (contrast, correlation, energy, homogeneity)</li>
          <li>Gray-level co-occurrence matrix (GLCM) features</li>
          <li>Local binary patterns</li>
        </ul>
        
        <h3>Output Format</h3>
        <p>Features are exported to CSV format with the following structure:</p>
        <pre><code>ImageID,CellID,Class,Area,Perimeter,MeanIntensity_H,MeanIntensity_E,...\\n
img001,1,hepatocyte,245.5,58.2,128.4,89.2,...</code></pre>
      `
    },
    {
      id: 'classification',
      title: 'Cell Classification',
      content: `
        <h3>Defining Cell Classes</h3>
        <p>Create custom cell classes for your specific tissue type:</p>
        <ol>
          <li>Navigate to Classification > Define Classes</li>
          <li>Add new class with name and color</li>
          <li>Assign training samples by clicking on segmented cells</li>
          <li>Save class definitions for future use</li>
        </ol>
        
        <h3>Training XGBoost Models</h3>
        <p>Train machine learning models for automated classification:</p>
        <ol>
          <li>Ensure sufficient training samples per class (minimum 50 recommended)</li>
          <li>Go to Classification > Train Model</li>
          <li>Select features to include in training</li>
          <li>Configure XGBoost parameters:
            <ul>
              <li><code>n_estimators</code>: Number of trees (default: 100)</li>
              <li><code>max_depth</code>: Maximum tree depth (default: 6)</li>
              <li><code>learning_rate</code>: Step size shrinkage (default: 0.3)</li>
            </ul>
          </li>
          <li>Click "Train" and monitor progress</li>
        </ol>
        
        <h3>Model Validation</h3>
        <p>Validate your model before applying to new data:</p>
        <ul>
          <li>Cross-validation results displayed after training</li>
          <li>Confusion matrix shows per-class accuracy</li>
          <li>Feature importance ranking available</li>
        </ul>
        
        <h3>Applying Models</h3>
        <p>Classify new images using trained models:</p>
        <ol>
          <li>Load a trained model: Classification > Load Model</li>
          <li>Segment the target image</li>
          <li>Apply classification: Classification > Classify All</li>
          <li>Review and export results</li>
        </ol>
      `
    },
    {
      id: 'batch',
      title: 'Batch Processing',
      content: `
        <h3>Setting Up Batch Processing</h3>
        <p>Process multiple images automatically:</p>
        <ol>
          <li>Go to File > Batch Processing</li>
          <li>Select input folder containing images</li>
          <li>Configure output folder for results</li>
          <li>Set processing options:
            <ul>
              <li>Segmentation parameters</li>
              <li>Feature extraction options</li>
              <li>Classification model (optional)</li>
            </ul>
          </li>
          <li>Click "Start" to begin processing</li>
        </ol>
        
        <h3>Output Organization</h3>
        <p>Batch processing creates the following structure:</p>
        <pre><code>output_folder/
  |-- image1/
  |   |-- segmentation.tif
  |   |-- features.csv
  |   |-- classification.csv
  |-- image2/
  |   |-- ...
  |-- summary/
      |-- all_features.csv
      |-- all_classifications.csv</code></pre>
        
        <h3>Progress Monitoring</h3>
        <p>The batch processing window shows:</p>
        <ul>
          <li>Current image being processed</li>
          <li>Overall progress percentage</li>
          <li>Estimated time remaining</li>
          <li>Error log for failed images</li>
        </ul>
      `
    },
    {
      id: 'api',
      title: 'API Reference',
      content: `
        <h3>Command Line Interface</h3>
        <p>SciPathJ can be run from command line for automation:</p>
        <pre><code>java -jar scipathj.jar [options] [input]</code></pre>
        
        <h4>Available Options</h4>
        <table>
          <tr><th>Option</th><th>Description</th></tr>
          <tr><td><code>-i, --input</code></td><td>Input file or folder path</td></tr>
          <tr><td><code>-o, --output</code></td><td>Output folder path</td></tr>
          <tr><td><code>-c, --config</code></td><td>Configuration file path</td></tr>
          <tr><td><code>-m, --model</code></td><td>Classification model file</td></tr>
          <tr><td><code>-s, --segment</code></td><td>Run segmentation only</td></tr>
          <tr><td><code>-f, --features</code></td><td>Extract features only</td></tr>
          <tr><td><code>--classify</code></td><td>Run classification</td></tr>
          <tr><td><code>-h, --help</code></td><td>Show help message</td></tr>
        </table>
        
        <h3>Configuration File Format</h3>
        <p>Configuration files use JSON format:</p>
        <pre><code>{
  "segmentation": {
    "nuclei": {
      "minSize": 50,
      "maxSize": 500,
      "threshold": 120
    },
    "cytoplasm": {
      "expansion": 1.5,
      "threshold": 100
    }
  },
  "features": {
    "morphological": true,
    "intensity": true,
    "texture": true
  },
  "output": {
    "format": "csv",
    "includeImages": true
  }
}</code></pre>
      `
    }
  ];
  
  let activeSection = $state('introduction');
  
  function scrollToSection(id: string) {
    activeSection = id;
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
  }
</script>

<svelte:head>
  <title>Documentation - SciPathJ</title>
  <meta name="description" content="Comprehensive documentation for SciPathJ. Learn about installation, segmentation, feature extraction, and cell classification." />
</svelte:head>

<div class="docs-page">
  <!-- Header -->
  <section class="page-header">
    <div class="container">
      <h1>Documentation</h1>
      <p>Complete technical reference for SciPathJ</p>
    </div>
  </section>
  
  <!-- Main Content -->
  <div class="docs-container">
    <!-- Sidebar Navigation -->
    <aside class="docs-sidebar">
      <nav class="docs-nav">
        <h3>Contents</h3>
        <ul>
          {#each sections as section}
            <li>
              <button 
                class="nav-link" 
                class:active={activeSection === section.id}
                onclick={() => scrollToSection(section.id)}>
                {section.title}
              </button>
            </li>
          {/each}
        </ul>
      </nav>
    </aside>
    
    <!-- Documentation Content -->
    <main class="docs-content">
      {#each sections as section}
        <section id={section.id} class="docs-section">
          <h2>{section.title}</h2>
          {@html section.content}
        </section>
      {/each}
      
      <!-- Help Section -->
      <section class="docs-help">
        <h2>Need More Help?</h2>
        <p>If you can't find what you're looking for in the documentation, here are additional resources:</p>
        <div class="help-links">
          <a href="https://github.com/sebastianmicu24/scipathj/issues" target="_blank" rel="noopener noreferrer" class="btn btn-secondary">
            Open an Issue
          </a>
          <a href="/tutorials" class="btn btn-primary">
            View Tutorials
          </a>
        </div>
      </section>
    </main>
  </div>
</div>

<style>
  .docs-page {
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
  
  /* Docs Container */
  .docs-container {
    display: grid;
    grid-template-columns: 250px 1fr;
    max-width: var(--max-width);
    margin: 0 auto;
    padding: 0 1.5rem;
    gap: 2rem;
  }
  
  /* Sidebar */
  .docs-sidebar {
    position: sticky;
    top: calc(var(--header-height) + 2rem);
    height: fit-content;
    padding: 2rem 0;
  }
  
  .docs-nav h3 {
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    color: var(--color-gray-500);
    margin-bottom: 1rem;
  }
  
  .docs-nav ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .docs-nav li {
    margin-bottom: 0.25rem;
  }
  
  .docs-nav .nav-link {
    display: block;
    width: 100%;
    text-align: left;
    padding: 0.5rem 0.75rem;
    border: none;
    background: none;
    color: var(--color-gray-600);
    font-size: 0.9rem;
    cursor: pointer;
    border-radius: 4px;
    transition: all 0.2s ease;
  }
  
  .docs-nav .nav-link:hover {
    background: var(--color-gray-100);
    color: var(--color-primary);
  }
  
  .docs-nav .nav-link.active {
    background: var(--color-primary);
    color: var(--color-white);
  }
  
  /* Content */
  .docs-content {
    padding: 2rem 0;
    min-width: 0;
  }
  
  .docs-section {
    margin-bottom: 3rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid var(--color-gray-200);
  }
  
  .docs-section:last-of-type {
    border-bottom: none;
  }
  
  .docs-section h2 {
    color: var(--color-primary);
    margin-bottom: 1.5rem;
    padding-bottom: 0.5rem;
    border-bottom: 2px solid var(--color-primary);
  }
  
  .docs-content :global(h3) {
    color: var(--color-text-primary);
    margin: 1.5rem 0 1rem;
  }
  
  .docs-content :global(h4) {
    color: var(--color-text-primary);
    margin: 1rem 0 0.75rem;
  }
  
  .docs-content :global(p) {
    color: var(--color-text-secondary);
    line-height: 1.7;
    margin-bottom: 1rem;
  }
  
  .docs-content :global(ul), .docs-content :global(ol) {
    color: var(--color-text-secondary);
    margin-bottom: 1rem;
    padding-left: 1.5rem;
  }
  
  .docs-content :global(li) {
    margin-bottom: 0.5rem;
    line-height: 1.6;
  }
  
  .docs-content :global(code) {
    background: var(--color-bg-tertiary);
    padding: 0.2rem 0.4rem;
    border-radius: 4px;
    font-family: 'Consolas', 'Monaco', monospace;
    font-size: 0.9em;
    color: var(--color-primary-light);
  }
  
  .docs-content :global(pre) {
    background: var(--color-bg-tertiary);
    color: var(--color-text-primary);
    padding: 1rem;
    border-radius: 8px;
    overflow-x: auto;
    margin: 1rem 0;
    border: 1px solid var(--color-border-subtle);
  }
  
  .docs-content :global(pre code) {
    background: none;
    padding: 0;
    color: inherit;
  }
  
  .docs-content :global(table) {
    width: 100%;
    border-collapse: collapse;
    margin: 1rem 0;
  }
  
  .docs-content :global(th), .docs-content :global(td) {
    padding: 0.75rem;
    text-align: left;
    border: 1px solid var(--color-border);
  }
  
  .docs-content :global(th) {
    background: var(--color-bg-tertiary);
    font-weight: 600;
    color: var(--color-text-primary);
  }
  
  .docs-content :global(td) {
    color: var(--color-text-secondary);
  }
  
  .docs-content :global(a) {
    color: var(--color-primary-light);
  }
  
  .docs-content :global(a:hover) {
    text-decoration: underline;
  }
  
  /* Help Section */
  .docs-help {
    background: var(--color-gray-100);
    padding: 2rem;
    border-radius: 8px;
    text-align: center;
    margin-top: 2rem;
  }
  
  .docs-help h2 {
    color: var(--color-gray-900);
    border: none;
    padding: 0;
    margin-bottom: 1rem;
  }
  
  .docs-help p {
    color: var(--color-gray-600);
    margin-bottom: 1.5rem;
  }
  
  .help-links {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
  }
  
  /* Responsive */
  @media (max-width: 992px) {
    .docs-container {
      grid-template-columns: 1fr;
    }
    
    .docs-sidebar {
      position: relative;
      top: 0;
      padding: 1rem 0;
      border-bottom: 1px solid var(--color-gray-200);
    }
    
    .docs-nav ul {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
    }
    
    .docs-nav li {
      margin-bottom: 0;
    }
    
    .docs-nav .nav-link {
      padding: 0.5rem 1rem;
    }
  }
  
  @media (max-width: 576px) {
    .docs-nav ul {
      flex-direction: column;
    }
    
    .docs-nav .nav-link {
      width: 100%;
    }
  }
</style>