<!--
  RelatedLinks.stories.svelte

  Stories for the RelatedLinks component.
  RelatedLinks renders a "Related Stories" section at the end of an article —
  a list of links with a bold, uppercase, blue-accented heading.

  Props:
  - title: Section heading text (default: "RELATED STORIES")
  - links: Array of { headline, href } objects
-->
<script module>
  import { defineMeta } from '@storybook/addon-svelte-csf';
  import RelatedLinks from '$lib/components/RelatedLinks.svelte';

  const { Story } = defineMeta({
    title: 'Components/RelatedLinks',
    component: RelatedLinks,
    tags: ['autodocs'],
    argTypes: {
      title: {
        control: 'text',
        description: 'Section heading text displayed above the link list',
      },
      links: {
        control: 'object',
        description: 'Array of link objects, each with a headline and href property',
      },
    },
  });
</script>

<!-- Default: standard "Related Stories" section with several links -->
<Story
  name="Default"
  args={{
    title: 'RELATED STORIES',
    links: [
      {
        headline: 'The Forgotten Poet: How Emma Lazarus Shaped America\'s Immigration Identity',
        href: '/emma-lazarus-biography',
      },
      {
        headline: 'Inside the Statue of Liberty\'s 354-Step Climb to the Crown',
        href: '/statue-crown-tour',
      },
      {
        headline: 'From France to New York Harbor: The Epic Journey of Lady Liberty',
        href: '/statue-history',
      },
    ],
  }}
/>

<!-- Custom Title: section with a different heading label -->
<Story
  name="Custom Title"
  args={{
    title: 'MORE ON THIS TOPIC',
    links: [
      { headline: 'The Full Text of "The New Colossus" by Emma Lazarus', href: '/new-colossus-text' },
      { headline: 'Ellis Island and the Immigrant Experience', href: '/ellis-island' },
    ],
  }}
/>

<!-- Single Link: the minimum case — just one related story -->
<Story
  name="Single Link"
  args={{
    title: 'RELATED STORIES',
    links: [
      { headline: 'Statue of Liberty Named UNESCO World Heritage Site in 1984', href: '/unesco-designation' },
    ],
  }}
/>

<!-- No Links: renders nothing (component hides itself when links array is empty) -->
<Story
  name="No Links (Hidden)"
  args={{
    title: 'RELATED STORIES',
    links: [],
  }}
/>
