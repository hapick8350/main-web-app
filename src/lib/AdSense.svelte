<script>
  import { onMount } from 'svelte';
  
  let adContainer;
  
  onMount(() => {
    // AdSense 스크립트가 로드된 후 광고를 표시
    if (typeof window !== 'undefined') {
      try {
        window.adsbygoogle = window.adsbygoogle || [];
        window.adsbygoogle.push({});
      } catch (error) {
        console.error('AdSense error:', error);
      }
    }
  });
</script>

<div class="ad-container" bind:this={adContainer}>
  <ins class="adsbygoogle"
       style="display:block"
       data-ad-client="ca-pub-8717173203378596"
       data-ad-slot="YOUR_AD_SLOT_ID"
       data-ad-format="auto"
       data-full-width-responsive="true"></ins>
</div>

<style>
  .ad-container {
    width: 100%;
    max-width: 728px;
    margin: 2rem auto;
    text-align: center;
    background: #f8f9fa;
    border-radius: 8px;
    padding: 1rem;
    min-height: 90px;
  }
  
  .ad-container ins {
    display: block;
    width: 100%;
    height: 90px;
  }
  
  @media (max-width: 768px) {
    .ad-container {
      margin: 1rem auto;
      padding: 0.5rem;
    }
    
    .ad-container ins {
      height: 50px;
    }
  }
</style>
