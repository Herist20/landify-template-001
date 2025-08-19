<script>
  import Header from './components/Header.svelte';
  import Hero from './components/Hero.svelte';
  import FeaturedProperties from './components/FeaturedProperties.svelte';
  import Services from './components/Services.svelte';
  import About from './components/About.svelte';
  import Testimonials from './components/Testimonials.svelte';
  import Contact from './components/Contact.svelte';
  import Footer from './components/Footer.svelte';
  import siteContent from './data/siteContentModular.js';
  
  let content = siteContent;
</script>

<main>
  <Header {content} />
  <Hero {content} />
  <FeaturedProperties {content} />
  <Services {content} />
  <About {content} />
  <Testimonials {content} />
  <Contact {content} />
  <Footer {content} />
</main>

<style>
  :global(*) {
    scroll-behavior: smooth;
  }
  
  main {
    min-height: 100vh;
  }
</style>