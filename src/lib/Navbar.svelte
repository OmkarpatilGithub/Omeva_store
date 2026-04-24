<script>
  import { onMount } from "svelte";

  let menuOpen = false;
  let darkMode = false;
  onMount(() => {
    const saved = localStorage.getItem("theme");

    if (saved === "dark") {
      document.documentElement.classList.add("dark");
      darkMode = true;
    } else {
      document.documentElement.classList.remove("dark");
      darkMode = false;
    }
  });

  function toggleTheme() {
    darkMode = !darkMode;
    document.documentElement.classList.toggle("dark", darkMode);
    localStorage.setItem("theme", darkMode ? "dark" : "light");
    window.reload();
  }
  function magnet(e) {
    const el = e.currentTarget;
    const rect = el.getBoundingClientRect();

    const x = e.clientX - rect.left - rect.width / 2;
    const y = e.clientY - rect.top - rect.height / 2;

    el.style.transform = `translate(${x * 0.2}px, ${y * 0.2}px)`;
  }

  function reset(e) {
    e.currentTarget.style.transform = `translate(0,0)`;
  }
</script>

<nav
  class="fixed top-0 left-0 right-0 z-50 border-b backdrop-blur-xl
         border-[var(--border)]
         text-[var(--text)]"
  style="background-color: var(--surface);"
>
  <div
    class="max-w-screen-xl mx-auto px-6 lg:px-10 flex items-center justify-between h-16"
  >
    <!-- Logo -->
    <a href="/" class="flex items-center gap-2 py-1">
      {#if darkMode}
        <img src="https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/darkLogo.png" alt="OMEVA logo" class="logo" />
      {:else}
        <img src="https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/lightLogo.png" alt="OMEVA logo" class="logo" />
      {/if}
    </a>

    <!-- Desktop Nav -->
    <div class="hidden md:flex items-center gap-10">
      <a href="#gallery" class="nav-link">Gallery</a>
      <a href="#about" class="nav-link">About</a>
      <a href="#process" class="nav-link">Process</a>
      <a href="#connect" class="nav-link">Connect</a>
    </div>

    <!-- Right Side -->
    <div class="hidden md:flex items-center gap-4">
      <a href="#connect">
        <button
          class="btn-primary transition-transform duration-200"
          on:mousemove={magnet}
          on:mouseleave={reset}
        >
          ORDER NOW
        </button>
      </a>
      <!-- <a href="#connect" class="btn-border">Order Now</a> -->

      <button
        on:click={toggleTheme}
        class="btn-border flex items-center justify-center px-3"
        aria-label="Toggle dark mode"
      >
        {#if darkMode}
          ☀
        {:else}
          ☾
        {/if}
      </button>
    </div>

    <!-- Mobile Menu Button -->
    <button
      class="md:hidden text-[var(--text)]"
      on:click={() => (menuOpen = !menuOpen)}
      aria-label="Toggle menu"
    >
      <svg width="22" height="22" viewBox="0 0 22 22" fill="none">
        {#if menuOpen}
          <line
            x1="2"
            y1="2"
            x2="20"
            y2="20"
            stroke="currentColor"
            stroke-width="2"
          />
          <line
            x1="20"
            y1="2"
            x2="2"
            y2="20"
            stroke="currentColor"
            stroke-width="2"
          />
        {:else}
          <line
            x1="2"
            y1="6"
            x2="20"
            y2="6"
            stroke="currentColor"
            stroke-width="2"
          />
          <line
            x1="2"
            y1="11"
            x2="20"
            y2="11"
            stroke="currentColor"
            stroke-width="2"
          />
          <line
            x1="2"
            y1="16"
            x2="20"
            y2="16"
            stroke="currentColor"
            stroke-width="2"
          />
        {/if}
      </svg>
    </button>
  </div>

  <!-- Mobile Menu -->
  {#if menuOpen}
    <div
      class="md:hidden border-t px-6 py-6 flex flex-col gap-6
             bg-[var(--bg)] border-[var(--border)]"
    >
      <a href="#gallery" class="nav-link" on:click={() => (menuOpen = false)}
        >Gallery</a
      >
      <a href="#about" class="nav-link" on:click={() => (menuOpen = false)}
        >About</a
      >
      <a href="#process" class="nav-link" on:click={() => (menuOpen = false)}
        >Process</a
      >
      <a href="#connect" class="nav-link" on:click={() => (menuOpen = false)}
        >Connect</a
      >

      <a
        href="#connect"
        class="btn-border w-max"
        on:click={() => (menuOpen = false)}
      >
        Order Now
      </a>

      <button
        on:click={toggleTheme}
        class="btn-border w-max flex items-center justify-center px-3"
      >
        {#if darkMode}
          ☀ Light Mode
        {:else}
          ☾ Dark Mode
        {/if}
      </button>
    </div>
  {/if}
</nav>
