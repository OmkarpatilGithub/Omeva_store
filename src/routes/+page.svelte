<script>
  import Navbar from '$lib/Navbar.svelte';
  import Hero from '$lib/Hero.svelte';
  import Marquee from '$lib/Marquee.svelte';
  import About from '$lib/About.svelte';
  import Gallery from '$lib/Gallery.svelte';
  import Process from '$lib/Process.svelte';
  import Connect from '$lib/Connect.svelte';
  import Footer from '$lib/Footer.svelte';
</script>

<svelte:head>
  <title>OMEVA — Wear Your Print</title>
  <meta name="description" content="A Pune-born label crafting custom printed tees since 2025. Heavyweight cotton, unapologetic graphics, zero middlemen." />
</svelte:head>

<Navbar />
<main>
  <Hero />
  <Marquee />
  <About />
  <Gallery />
  <Process />
  <Connect />
</main>
<Footer />
