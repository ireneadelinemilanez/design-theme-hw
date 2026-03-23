<!--
  ArticleBody.stories.svelte

  Stories for the ArticleBody component.
  ArticleBody is a wrapper that applies NYCity News Service typography to
  any HTML content — paragraphs, headings, links, blockquotes, and lists.

  Props:
  - children: Content passed between opening and closing tags (Svelte snippet)
-->
<script module>
  import { defineMeta } from '@storybook/addon-svelte-csf';
  import ArticleBody from '$lib/components/ArticleBody.svelte';

  const { Story } = defineMeta({
    title: 'Components/ArticleBody',
    component: ArticleBody,
    tags: ['autodocs'],
    parameters: {
      // fullscreen so we can apply our own max-width container below,
      // which gives a more realistic reading-column preview.
      layout: 'fullscreen',
    },
  });
</script>

<!-- Default: typical article with multiple paragraphs -->
<Story name="Default">
  <div class="story-container">
    <ArticleBody>
      <p>
        In 1883, a young poet named Emma Lazarus wrote a sonnet to help raise funds for the
        construction of the pedestal that would hold the Statue of Liberty. That poem, "The New
        Colossus," would go on to become one of the most recognized works in American literature —
        and the defining statement of the nation's identity as a haven for immigrants.
      </p>
      <p>
        Lazarus, born in 1849 to a wealthy Sephardic Jewish family in New York City, was already an
        accomplished writer by the time she was asked to contribute to the fundraising effort. But it
        was her encounters with Jewish refugees fleeing pogroms in Eastern Europe that gave the poem
        its emotional urgency.
      </p>
      <p>
        "Give me your tired, your poor, your huddled masses yearning to breathe free," she wrote,
        imagining the statue as a "Mother of Exiles" — not a monument to military conquest like the
        ancient Colossus of Rhodes, but a beacon of welcome for the world's displaced and dispossessed.
      </p>
    </ArticleBody>
  </div>
</Story>

<!-- With Subheadings: shows h2/h3 typography inside article body -->
<Story name="With Subheadings">
  <div class="story-container">
    <ArticleBody>
      <p>
        The Statue of Liberty, a gift from France to the United States, was dedicated on October 28,
        1886. It would take another 17 years before Emma Lazarus's words found their permanent home
        at its base.
      </p>
      <h2>A Gift Between Nations</h2>
      <p>
        French sculptor Frédéric Auguste Bartholdi designed the statue, while Alexandre Gustave
        Eiffel — who would later build his famous tower — engineered the internal iron framework.
        The copper exterior, just 3/32 of an inch thick, was assembled on a massive iron skeleton.
      </p>
      <h3>The Forgotten Poem</h3>
      <p>
        Lazarus died in 1887, just a year after the statue's dedication, and her sonnet was largely
        forgotten. In 1903, a friend named Georgina Schuyler successfully campaigned to have the
        poem mounted on a bronze plaque inside the pedestal, ensuring its words would endure.
      </p>
    </ArticleBody>
  </div>
</Story>

<!-- With Blockquote: shows the NYCity-style blue-bordered pull quote -->
<Story name="With Blockquote">
  <div class="story-container">
    <ArticleBody>
      <p>
        Emma Lazarus's "The New Colossus" reimagined the Statue of Liberty not as a symbol of
        imperial power, but as a welcoming mother figure standing at the gates of a new world.
      </p>
      <blockquote>
        <p>
          "Give me your tired, your poor, / Your huddled masses yearning to breathe free, / The
          wretched refuse of your teeming shore. / Send these, the homeless, tempest-tost to me, /
          I lift my lamp beside the golden door!"
        </p>
      </blockquote>
      <p>
        — Emma Lazarus, "The New Colossus" (1883)
      </p>
    </ArticleBody>
  </div>
</Story>

<!-- With Links and Lists: shows inline link and list typography -->
<Story name="With Links and Lists">
  <div class="story-container">
    <ArticleBody>
      <p>
        The Statue of Liberty remains one of the most visited landmarks in the world. Learn more at
        the <a href="https://www.nps.gov/stli/">National Park Service website</a>.
      </p>
      <ul>
        <li>Height from ground to torch: 305 feet (93 meters)</li>
        <li>Weight of copper and steel: approximately 225 tons</li>
        <li>Number of steps from base to crown: 354</li>
        <li>Annual visitors: approximately 4 million</li>
      </ul>
      <p>
        The statue was designated a UNESCO World Heritage Site in 1984 and continues to serve as a
        global symbol of freedom and democracy.
      </p>
    </ArticleBody>
  </div>
</Story>

<style>
  /* Mirror the page's .container class so the reading column has a realistic max-width */
  .story-container {
    width: 100%;
    max-width: var(--max-width);
    margin: 0 auto;
    padding: var(--spacing-lg) var(--spacing-md);
  }
</style>
