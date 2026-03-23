<!--
@component
SplashHeader.svelte — Splash Header with Kicker, Headline, and Deck

USAGE EXAMPLE:
<SplashHeader
  kicker="Breaking News"
  headline="City Council Approves New Budget"
  deck="The decision marks a major shift in municipal spending priorities"
  pubDate="2024-01-15"
/>
-->

<script>
  let {
    kicker = '',
    headline = '',
    deck = '',
    pubDate = '',
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

<style lang="scss">
  @use '../styles' as *;

  :global(.story-theme) {
    --color-accent: #fe8807;
    --color-border: #fe8807;

    .story-header {
      text-align: center;
      padding: var(--spacing-xxl) var(--spacing-md);
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
