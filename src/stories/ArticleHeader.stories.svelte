<!--
  ArticleHeader.stories.svelte

  Stories for the ArticleHeader component.
  ArticleHeader renders a large serif headline with a metadata box showing
  the byline and publication date in NYCity News Service style.

  Props:
  - headline: The main article title (required)
  - byline: Author name(s) (optional)
  - pubDate: Publication date in YYYY-MM-DD format (optional)
-->
<script module>
  import { defineMeta } from '@storybook/addon-svelte-csf';
  import ArticleHeader from '$lib/components/ArticleHeader.svelte';

  const { Story } = defineMeta({
    title: 'Components/ArticleHeader',
    component: ArticleHeader,
    tags: ['autodocs'],
    argTypes: {
      headline: {
        control: 'text',
        description: 'The main article title displayed as a large serif heading',
      },
      byline: {
        control: 'text',
        description: 'Author name(s) shown in the metadata box',
      },
      pubDate: {
        control: 'text',
        description: 'Publication date in YYYY-MM-DD format (e.g. "2024-01-15")',
      },
    },
  });
</script>

<!-- Default: full headline with byline and date -->
<Story
  name="Default"
  args={{
    headline: 'How Emma Lazarus Gave Voice to the Statue of Liberty',
    byline: 'Sarah Chen and Michael Rivera',
    pubDate: '1883-11-02',
  }}
/>

<!-- Headline Only: no byline or date -->
<Story
  name="Headline Only"
  args={{
    headline: '"The New Colossus" Turns 140: The Poem That Defined a Nation of Immigrants',
  }}
/>

<!-- With Byline Only: headline and author, no date -->
<Story
  name="With Byline Only"
  args={{
    headline: 'From Forgotten Sonnet to National Treasure: The Journey of "The New Colossus"',
    byline: 'Emma Lazarus',
  }}
/>

<!-- With Date Only: headline and date, no byline -->
<Story
  name="With Date Only"
  args={{
    headline: 'Statue of Liberty Dedicated in New York Harbor Amid Grand Ceremony',
    pubDate: '1886-10-28',
  }}
/>

<!-- Long Headline: tests wrapping behavior on narrow viewports -->
<Story
  name="Long Headline"
  args={{
    headline:
      '"Give Me Your Tired, Your Poor": How a Poem Written to Raise Money for a Pedestal Became the Most Famous Words in American Immigration History',
    byline: 'The NYCity News Service History Desk',
    pubDate: '1903-05-06',
  }}
/>
