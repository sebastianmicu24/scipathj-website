<script lang="ts">
  import { onMount } from 'svelte';

  interface Example {
    id: number;
    title: string;
    description: string;
    beforeImageId: string;
    afterImageId: string;
  }

  const examples: Example[] = [
    {
      id: 1,
      title: "Liver",
      description: "Liver tissue stained with H&E: vessels and ducts are highlighted in red, nuclei in blue, while cellular borders are displayed in black",
      beforeImageId: "1HjMpLIfhVg38-_efIvIIvIX_6H4o6Yle",
      afterImageId: "1Q8_kTDty2nq3GlEwl7x5N-S8dpXW6ocZ"
    },
    {
      id: 2,
      title: "Pancreas",
      description: "Pancreatic tissue analysis",
      beforeImageId: "1XiTgSSCmmg9cd-fHvOgKii8XKexTlqaI",
      afterImageId: "1ediNHPqwD108A9oQsz5cBOxIPEdBGfva"
    },
    {
      id: 3,
      title: "Kidney",
      description: "Description for example 3",
      beforeImageId: "1Pa5s4Z6xPS7wF7s1L7Ub6t75z5hRJHG_",
      afterImageId: "1mcZozdUNCiiRr688xUfhPzMlYMq-AKQO"
    },
    {
      id: 4,
      title: "Spleen",
      description: "Description for example 4",
      beforeImageId: "1nUwZR_7iv5TS0Pc8gOClVuxZDNjZeseK",
      afterImageId: "1M9u_4IBzb4hVs5kZDopfoKfCuGc8Uiuf"
    },
    {
      id: 5,
      title: "Nuclear Segmentation",
      description: "Description for example 5",
      beforeImageId: "1Ub1hcsDG2jUw7-OOXGjJpXtT_Rd9ZAAC",
      afterImageId: "15JIFwNkyCysmdfe_zwJMceXzvdC4aMm_"
    },
    {
      id: 6,
      title: "Cardiac Muscle",
      description: "Description for example 6",
      beforeImageId: "1WIwgKv6unsMUxLm9mwsU_IV9pAmxPsls",
      afterImageId: "1UCHu9CSZdfFuhyRyim8y0vpzkMnR3tfC"
    },
    {
      id: 7,
      title: "Lung",
      description: "Description for example 7",
      beforeImageId: "1dgg-663_gAVStrX8Vw6hLCJ1ldOnTntm",
      afterImageId: "1ILTvuf7aB3O8rt7xXlMtNaU-G5pZABR9"
    },
    {
      id: 8,
      title: "Testis",
      description: "Description for example 8",
      beforeImageId: "1g5hYn2-sH_Jbtmts245nrtvEeW0CjF-0",
      afterImageId: "13Lf1NShV4Yhhg5ZgW7CrRkGw3Dc9OIj2"
    },
    {
      id: 9,
      title: "Ovaries",
      description: "Description for example 9",
      beforeImageId: "1-1Y1BhZI6FxU09pN_YqE_MGhBjO3bzzE",
      afterImageId: "1tx5M4b0HTrbX3itJ-JZHjCDtm8nd0wSK"
    },
    {
      id: 10,
      title: "Adrenal Gland",
      description: "Description for example 10",
      beforeImageId: "1FZk_AhY63LRwfDWpijLJloxFgCV2tNZ7",
      afterImageId: "1EqRLQC99jtofXod9Sou8rVyRzxTVR6rZ"
    },
    {
      id: 11,
      title: "Gastric Lining",
      description: "Description for example 11",
      beforeImageId: "1vHd6PaNavxV3Bv7lVAA-OKfFQeXcbgYh",
      afterImageId: "1yDxGa_k9kfJMYhqOxbciCCXTL7vBM_x8"
    },
    {
      id: 12,
      title: "Cervix",
      description: "Description for example 12",
      beforeImageId: "1tynP9jqgRj3shAPnicR3sz0FWHnG3cyg",
      afterImageId: "1KH1pWke2ez1IIFVa4DZxiv1ye3O0HILC"
    },
    {
      id: 13,
      title: "Neurohypophysis",
      description: "Description for example 13",
      beforeImageId: "1-FIJWWKDrf2EGkGv0YfcKYkWAFrkeIIS",
      afterImageId: "1xt8v0wPYkguS3O3WZ7tyeVvwxui2ZaNQ"
    },
    {
      id: 14,
      title: "Skin",
      description: "Description for example 14",
      beforeImageId: "1_StpFR1xzw8XZVn5ry-hBbNpcaXxvvqX",
      afterImageId: "1NW2DPVD1NNSv8nFG_hR7uyYHLtx9G_Oc"
    }
  ];

  let imageErrors: Set<string> = new Set();

  // Convert Google Drive file ID to direct link
  function getDriveUrl(fileId: string): string {
    return `https://drive.google.com/thumbnail?id=${fileId}&sz=w1000`;
  }

  function handleImageError(event: Event, fileId: string) {
    imageErrors.add(fileId);
    imageErrors = imageErrors;
  }
</script>

<svelte:head>
  <title>Examples - SciPathJ</title>
  <meta name="description" content="View before and after examples of histopathology image analysis with SciPathJ." />
</svelte:head>

<div class="examples-page">
  <!-- Header -->
  <section class="page-header">
    <div class="container">
      <h1>Examples</h1>
      <p>Before and after results from SciPathJ image analysis</p>
    </div>
  </section>


  <!-- Examples Grid -->
  <section class="section">
    <div class="container">
      <div class="examples-grid">
        {#each examples as example, i (example.id)}
          <div 
            class="example-card" 
            data-id={example.id}
          >
            <div class="example-header">
              <h3 class="example-title">{example.title}</h3>
            </div>
            
            <div class="example-images">
              <div class="image-container">
                {#if imageErrors.has(example.beforeImageId)}
                  <div class="image-error">
                    <span>Failed to load</span>
                  </div>
                {:else}
                  <img
                    src={getDriveUrl(example.beforeImageId)}
                    alt="Before - {example.title}"
                    class="example-image"
                    loading="lazy"
                    on:error={(e) => handleImageError(e, example.beforeImageId)}
                  />
                {/if}
                <span class="image-label">Before</span>
              </div>
              
              <div class="image-container">
                {#if imageErrors.has(example.afterImageId)}
                  <div class="image-error">
                    <span>Failed to load</span>
                  </div>
                {:else}
                  <img
                    src={getDriveUrl(example.afterImageId)}
                    alt="After - {example.title}"
                    class="example-image"
                    loading="lazy"
                    on:error={(e) => handleImageError(e, example.afterImageId)}
                  />
                {/if}
                <span class="image-label">After</span>
              </div>
            </div>
            
            <p class="example-description">{example.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>
</div>

<style>
  .examples-page {
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

  /* Examples Grid */
  .examples-grid {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .example-card {
    background: var(--color-white);
    border: 1px solid var(--color-gray-200);
    border-radius: 8px;
    padding: 1.5rem;
    transition: box-shadow 0.2s ease;
  }

  .example-card:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }

  .example-header {
    margin-bottom: 1rem;
  }

  .example-number {
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--color-primary);
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .example-title {
    color: var(--color-gray-900);
    margin-top: 0.25rem;
  }

  /* Images Container */
  .example-images {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .image-container {
    position: relative;
    background: var(--color-gray-100);
    border-radius: 4px;
    overflow: hidden;
    aspect-ratio: 16 / 9;
  }

  .example-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
    display: block;
  }

  .image-label {
    position: absolute;
    bottom: 0.5rem;
    left: 0.5rem;
    background: rgba(0, 0, 0, 0.7);
    color: white;
    padding: 0.25rem 0.75rem;
    border-radius: 4px;
    font-size: 0.8rem;
    font-weight: 500;
  }

  /* Error State */
  .image-error {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    color: var(--color-gray-500);
    background: var(--color-gray-200);
    text-align: center;
    padding: 1rem;
  }

  .image-error small {
    font-size: 0.7rem;
    color: var(--color-gray-400);
  }

  /* Description */
  .example-description {
    color: var(--color-gray-600);
    font-size: 0.95rem;
    line-height: 1.6;
    margin: 0;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .example-images {
      grid-template-columns: 1fr;
    }
  }
</style>
