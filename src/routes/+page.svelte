<!--
@component
This is your page!
-->
<script>
  // Import all the news furniture components
  import ArticleBody from '$lib/components/ArticleBody.svelte';
  import Image from '$lib/components/Image.svelte';
  import RelatedLinks from '$lib/components/RelatedLinks.svelte';
  import ImageHeader2 from '$lib/components/ImageHeader2.svelte';
  import BigNumber from '$lib/components/BigNumber.svelte';
  import Dashboard from '$lib/components/Dashboard.svelte';


  // Article metadata
  let headline = 'Become a force for good. Join our next class.';
  let byline = 'NYCity News Service';
  let pubDate = '2026-01-31';

  // Related stories
  const relatedStories = [
    { headline: 'How America\'s top news organizations escape rigid publishing systems to design beautiful data-driven stories on deadline.', href: 'https://palewi.re/docs/coding-the-news/' },
    { headline: 'How to install, configure and use Visual Studio Code, GitHub and Copilot', href: 'https://palewi.re/docs/coding-the-news/scripts/week-1/' },
    { headline: "How to publish a website with Node.JS and GitHub Actions", href:"https://palewi.re/docs/coding-the-news/scripts/week-2/"},
  ];
</script>

<!-- This sets the page title in the browser tab -->
<svelte:head>
  <title>{headline} | NYCity News Service</title>
  <meta name="description" content="At the Craig Newmark Graduate School of Journalism at the City University of New York, change is in our DNA. That comes of being born in 2006, as the digital revolution was transforming our profession in ways none of us could have imagined." />
     <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&display=swap" rel="stylesheet">

</svelte:head>

<!-- Your page content goes here -->
<div class="container story-theme">
  
  <ImageHeader2
  headline="Restaurant Costs are Still Sky-High"
  deck="Cafés and bars nationwide struggle with the high cost of ingredients."
  imageSrc="Restaurant.jpeg"
  byline="Irene Adeline Milanez"
  pubDate="2026-03-22"
/>

  <Dashboard>
    <BigNumber
      number="3.1%"
      label="Ingredient Price Increase"
      footnote="From 2024"

    />
    <BigNumber
      number="30%"
      label="Menu Price Increase"
      footnote="To keep up with inflation"
    />
    <BigNumber
      number="96%"
      label="Tariffs costs paid by importers"
    />
    </Dashboard>

  <!-- Article Body: The main story text with proper typography -->
  <ArticleBody>
    <p>
      At Bati Ethiopian Kitchen in Brooklyn’s Bedford- Stuyvesant neighborhood, the menu centers injera, a large, sour, spongy flatbread, served with a variety of wat, stews made from meat, vegetables, and legumes.
    </p>

    <p>
      “Ethiopian food is mostly long slow-cooked stews on the fire,” owner Hibist Legesse says. “You need a lot of onions for that.” 
    </p>

    <p>
      But over the past few months, Legesse has watched onions getting pricier by the day. Though the price of onions have overall decreased from 2024 to 2025 by 27.2%, from June to November of 2025, prices have fluctuated month-to-month, according to the US Bureau of Labor and Statistics Producer Price Index Report. 
    </p>

    <p>
      It’s not just onions. Nearly every ingredient has gotten more expensive. The average price consumers pay for food purchases was 3.1% higher in 2025 from the previous year, according to the USDA’s Food Price Outlook.
    </p>

    <p>
      Small cafés, bars and restaurants like Bati are struggling to maintain their margins as ingredient costs climb because of tariffs imposed by the Trump administration, rising inflation, and many other factors. 
    </p>

    <p>
      “As an ethnic restaurant, you can only charge so much,” Legesse says. “You don’t want to push away your customers like that. So we just keep our prices the same, and we eat the cost most of the time.” 
    </p>

    <p>
      According to the National Restaurant Association, wholesale food prices are 37% higher than before the pandemic. Legesse says the price of meat has increased the most. The wholesale price of beef increased by 15.1% while finfish increased by 31.6% since last year, according to the Producer Price Index Report.
    </p>

    <p>
      Hema Agwu, co-owner of Brooklyn Suya, says he has seen a steady rise in protein costs. His restaurants serve suya, a grilled protein seasoned with a signature Nigerian blend of roasted peanuts and dried chiles over a bed of kale or rice topped with fresh vegetables.
    </p>

    <p>
      “Steak is super expensive. Salmon is super expensive,” he says. Before the pandemic, Bati’s Legesse says her restaurant had a 6% to 7% profit margin. Today her margins hover at 5% because of ingredient price inflation, increased staffing, and higher insurance costs. 
    </p>
  </ArticleBody>

  <!-- Related Stories: Links to other articles -->
  <RelatedLinks
    title="Related Stories"
    links={relatedStories}
  />

</div>

<style lang="scss">
  @use '$lib/styles' as *;

  :global(.story-theme) {
    --color-accent: #767d13;
    --color-border: #767d13;;
  }
</style>