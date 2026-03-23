<!--
@component
ImageHeader2.svelte — NYT-style Image Header with Overlay Text

USAGE EXAMPLE:
<ImageHeader2
  headline="Cesar Chavez and the UFW: Allegations of Sexual Abuse"
  deck="Newly revealed documents challenge the founder's legacy"
  imageSrc="/path/to/image.jpg"
  byline="By Reporter Name"
  pubDate="2024-03-18"
/>
-->

<script>
  let {
    headline = '',
    deck = '',
    imageSrc = '',
    byline = '',
    pubDate = '',
  } = $props();

  // Format date to "MARCH 18, 2024" style
  function formatDate(dateString) {
    if (!dateString) return '';
    
    const [year, month, day] = dateString.split('-').map(Number);
    const date = new Date(year, month - 1, day);
    
    return new Intl.DateTimeFormat('en-US', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
    }).format(date).toUpperCase();
  }
</script>

<div class="nyt-header">
  {#if imageSrc}
    <div class="hero-image" style="background-image: url('{imageSrc}')"></div>
  {/if}
  
  <div class="overlay-content">
    <div class="content-wrapper">
      {#if headline}
        <h1 class="headline">{headline}</h1>
      {/if}
      
      {#if deck}
        <p class="deck">{deck}</p>
      {/if}
      
      <div class="article-meta">
        {#if byline}
          <p class="byline">{byline}</p>
        {/if}
        
        {#if pubDate}
          <p class="pubdate">
            <time datetime={pubDate}>{formatDate(pubDate)}</time>
          </p>
        {/if}
      </div>
    </div>
  </div>
</div>

<style lang="scss">
  @use '../styles' as *;

  .nyt-header {
    position: relative;
    width: 100vw;
    margin-left: calc(-50vw + 50%);
    min-height: 600px;
    overflow: hidden;
  }

  .hero-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    z-index: 0;
  }

  .overlay-content {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    width: 100%;
    background: linear-gradient(
      to bottom,
      rgba(0, 0, 0, 0) 0%,
      rgba(0, 0, 0, 0.3) 50%,
      rgba(0, 0, 0, 0.6) 100%
    );
    padding: 0;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    min-height: 300px;
    z-index: 1;
  }

  .content-wrapper {
    max-width: var(--max-width);
    margin: 0 auto;
    width: 100%;
    padding: var(--spacing-lg) var(--spacing-md);
    color: var(--color-white);
  }

  .headline {
    font-family: 'Playfair Display', Georgia, serif;
    font-size: var(--font-size-6xl);
    font-weight: 700;
    line-height: var(--leading-tight);
    color: var(--color-white);
    margin: 0 0 var(--spacing-sm) 0;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }

  .deck {
    font-family: var(--font-serif);
    font-size: var(--font-size-xl);
    line-height: var(--leading-normal);
    color: var(--color-white);
    margin: 0 0 var(--spacing-md) 0;
    max-width: 600px;
    text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.5);
  }

  .article-meta {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-xs);
    margin-top: var(--spacing-md);
  }

  .byline {
    font-family: var(--font-sans);
    font-size: var(--font-size-sm);
    font-weight: 600;
    color: var(--color-white);
    margin: 0;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
  }

  .pubdate {
    font-family: var(--font-sans);
    font-size: var(--font-size-xs);
    color: rgba(255, 255, 255, 0.9);
    margin: 0;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
  }

  @include mobile {
    .nyt-header {
      min-height: 400px;
    }

    .overlay-content {
      min-height: 200px;
    }

    .headline {
      font-size: var(--font-size-4xl);
    }

    .deck {
      font-size: var(--font-size-lg);
    }
  }
</style>
