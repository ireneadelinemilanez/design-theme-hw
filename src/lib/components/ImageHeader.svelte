<!--
@component
ImageHeader.svelte

USAGE EXAMPLE:
<ImageHeader
  kicker="Breaking News"
  headline="City Council Approves New Budget"
  deck="The decision marks a major shift in municipal spending priorities"
  pubDate="2024-01-15"
  imageSrc="/path/to/image.jpg"
/>
-->

<script>
  let {
    kicker = '',
    headline = '',
    deck = '',
    pubDate = '',
    imageSrc = '',
  } = $props();

  // Format date to "JANUARY 15, 2024" style
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

<div class="story-theme">
  <div class="image-header-wrapper">
    {#if imageSrc}
      <div class="background-image" style="background-image: url('{imageSrc}')"></div>
    {/if}
    
    <header class="story-header">
      {#if kicker}
        <span class="kicker">{kicker}</span>
      {/if}
      
      <h1>{headline}</h1>
      
      {#if deck || pubDate}
        <hr class="rule" />
      {/if}
      
      {#if deck}
        <p class="deck">{deck}</p>
      {/if}
      
      {#if pubDate}
        <p class="pubdate">
          <time datetime={pubDate}>{formatDate(pubDate)}</time>
        </p>
      {/if}
    </header>
  </div>
</div>

<style lang="scss">
  @use '../styles' as *;

  :global(.story-theme) {
    --color-accent: #fe8807;
    --color-border: #fe8807;

    .image-header-wrapper {
      position: relative;
      width: 100vw;
      margin-left: calc(-50vw + 50%);
      min-height: 500px;
      overflow: hidden;
    }

    .background-image {
      width: 100%;
      height: 100%;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 0;
    }

    .story-header {
      position: relative;
      text-align: center;
      padding: var(--spacing-xxl) var(--spacing-md);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      min-height: 100%;
    }

    .kicker {
      display: block;
      font-family: var(--font-sans);
      font-size: var(--font-size-xs);
      text-transform: uppercase;
      letter-spacing: 0.15em;
      color: var(--color-accent);
      margin-bottom: var(--spacing-sm);
    }

    .story-header h1 {
      font-family: 'Playfair Display', Georgia, serif;
      font-size: var(--font-size-4xl);
      font-weight: 900;
      line-height: var(--leading-tight);
      color: var(--color-dark);
      margin-bottom: var(--spacing-sm);
    }

    .rule {
      border: none;
      border-top: var(--border-width-accent) solid var(--color-accent);
      width: 60px;
      margin: 0 auto var(--spacing-sm);
    }

    .deck {
      font-family: var(--font-serif);
      font-size: var(--font-size-lg);
      line-height: var(--leading-normal);
      color: var(--color-text);
      max-width: 480px;
      margin: 0 auto var(--spacing-sm);
    }

    .pubdate {
      font-family: var(--font-sans);
      font-size: var(--font-size-sm);
      text-transform: uppercase;
      letter-spacing: 0.05em;
      color: var(--color-medium-gray);
    }

    @include mobile {
      .story-header h1 {
        font-size: var(--font-size-3xl);
      }

      .deck {
        font-size: var(--font-size-lg);
      }
    }
  }
</style>
