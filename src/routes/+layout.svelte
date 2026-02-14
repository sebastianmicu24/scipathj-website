<script lang="ts">
  import '../app.css';
  import Nav from '$lib/components/Nav.svelte';
  import Footer from '$lib/components/Footer.svelte';
  
  let { children } = $props();
</script>

<svelte:head>
  <title>SciPathJ - Tissue Segmentation & Cell Classification</title>
  <meta name="description" content="SciPathJ: An open-source software for automated tissue segmentation and cell classification from H&E stained histology images." />
</svelte:head>

<div class="layout">
  <Nav />
  <main class="main-content">
    {@render children()}
  </main>
  <Footer />
</div>

<style>
  .layout {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  
  .main-content {
    flex: 1;
    display: flex;
    flex-direction: column;
  }
</style>
