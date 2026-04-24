<script>
  const items = [
    'CUSTOM PRINTS',
    'OMEVA 2025',
    'PREMIUM COTTON',
    'MADE IN PUNE',
    'BULK ORDERS WELCOME',
    'WEAR YOUR PRINT',
    'DTF & SCREEN PRINT',
    'ZERO MIDDLEMEN'
  ];

  function orderNow(item) {
    const msg = encodeURIComponent(`I'm interested in: ${item}`);
    window.open(`https://wa.me/919270905007?text=${msg}`, '_blank');
  }
</script>

<div
  class="py-5 overflow-hidden relative group"
  style="background: var(--accent);"
>
  <!-- Marquee -->
  <div class="flex whitespace-nowrap marquee-track ">
    {#each Array(2) as _}
      <div class="flex items-center gap-8 px-4">
        {#each items as item}
          <span
            class="display-heading text-2xl tracking-widest cursor-pointer relative"
            style="color: var(--bg);"
            on:click={() => orderNow(item)}
          >
            {item}
          </span>

          <span
            class="text-lg"
            style="color: rgba(255,255,255,0.5);"
          >
            ◆
          </span>
        {/each}
      </div>
    {/each}
  </div>

  <!-- Hover Overlay CTA -->
  <!-- <div
    class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-all duration-300"
    style="background: rgba(0,0,0,0.4); backdrop-filter: blur(6px);"
  >
    <button
      on:click={() => orderNow('Custom T-Shirt')}
      class="px-6 py-3 text-xs font-semibold uppercase tracking-widest rounded"
      style="
        background: var(--bg);
        color: var(--text);
        border: 1px solid var(--border);
      "
    >
      ORDER NOW →
    </button>
  </div> -->
</div>