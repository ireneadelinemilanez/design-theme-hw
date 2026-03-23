<!--
  Image.stories.svelte

  Stories for the Image component.
  Image renders a responsive figure with an optional caption and photo credit.
  It handles both local asset paths (resolved via SvelteKit's asset()) and
  external URLs.

  Props:
  - src: Image source URL or local path starting with "/" (required)
  - alt: Descriptive alt text for accessibility (required)
  - caption: Optional caption text below the image
  - credit: Optional photo credit line
  - size: Layout size — "full" | "large" | "medium" | "small" (default: "full")
-->
<script module>
  import { defineMeta } from '@storybook/addon-svelte-csf';
  import Image from '$lib/components/Image.svelte';

  // Freely-licensed Statue of Liberty image from Wikimedia Commons
  const DEMO_IMAGE =
    'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Statue_of_Liberty_7.jpg/1200px-Statue_of_Liberty_7.jpg';

  const { Story } = defineMeta({
    title: 'Components/Image',
    component: Image,
    tags: ['autodocs'],
    argTypes: {
      src: {
        control: 'text',
        description: 'Image URL or local path (local paths starting with "/" are resolved via asset())',
      },
      alt: {
        control: 'text',
        description: 'Descriptive alt text for screen readers and accessibility',
      },
      caption: {
        control: 'text',
        description: 'Optional caption displayed below the image',
      },
      credit: {
        control: 'text',
        description: 'Optional photo credit attribution',
      },
      size: {
        control: { type: 'select' },
        options: ['full', 'large', 'medium', 'small'],
        description: 'Controls the maximum width of the image',
      },
    },
    args: {
      src: DEMO_IMAGE,
      alt: 'The Statue of Liberty on Liberty Island in New York Harbor',
    },
  });
</script>

<!-- Default: full-width image with caption and credit -->
<Story
  name="Default"
  args={{
    src: DEMO_IMAGE,
    alt: 'The Statue of Liberty on Liberty Island in New York Harbor',
    caption:
      'The Statue of Liberty, a gift from France dedicated in 1886, stands as a symbol of freedom and welcome in New York Harbor.',
    credit: 'Wikimedia Commons / Public Domain',
    size: 'full',
  }}
/>

<!-- No Caption: image displayed without any caption or credit -->
<Story
  name="No Caption"
  args={{
    src: DEMO_IMAGE,
    alt: 'The Statue of Liberty on Liberty Island in New York Harbor',
    size: 'full',
  }}
/>

<!-- Caption Only: image with caption text but no photo credit -->
<Story
  name="Caption Only"
  args={{
    src: DEMO_IMAGE,
    alt: 'The Statue of Liberty on Liberty Island in New York Harbor',
    caption:
      'Lady Liberty lifts her torch above New York Harbor, greeting arriving visitors and immigrants alike.',
    size: 'full',
  }}
/>

<!-- Large Size: constrained to max-width-image-large (720px) -->
<Story
  name="Large Size"
  args={{
    src: 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Statue_of_Liberty_7.jpg/720px-Statue_of_Liberty_7.jpg',
    alt: 'The Statue of Liberty seen from below against a blue sky',
    caption:
      'The statue rises 305 feet from the ground to the tip of her torch, built atop a pedestal designed by architect Richard Morris Hunt.',
    credit: 'Wikimedia Commons / Public Domain',
    size: 'large',
  }}
/>

<!-- Medium Size: constrained to max-width-image-medium (480px) -->
<Story
  name="Medium Size"
  args={{
    src: 'https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/Lady_Liberty_under_a_blue_sky_%28cropped%29.jpg/480px-Lady_Liberty_under_a_blue_sky_%28cropped%29.jpg',
    alt: 'Close-up of the Statue of Liberty crown and face',
    caption:
      'The crown features 25 windows and seven rays, representing the seven continents and oceans of the world.',
    credit: 'Wikimedia Commons / CC BY-SA 2.0',
    size: 'medium',
  }}
/>

<!-- Small Size: constrained to max-width-image-small (320px) -->
<Story
  name="Small Size"
  args={{
    src: 'https://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Emma_Lazarus.jpg/320px-Emma_Lazarus.jpg',
    alt: 'Portrait of poet Emma Lazarus',
    caption: 'Emma Lazarus (1849–1887), author of "The New Colossus."',
    credit: 'Wikimedia Commons / Public Domain',
    size: 'small',
  }}
/>
