<script>
  import VanillaTilt from "vanilla-tilt";

  const products = [
    { id: 'DRV-001', name: 'RAWPRINT OVERSIZED', tag: 'SIGNATURE GRAPHIC', badge: null,image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/inkDrop.webp' },
    { id: 'DRV-002', name: 'NOIR ESSENTIAL', tag: 'SINGLE LOGO TEE', badge: 'ESSENTIALS' ,image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/chimya.png'},
    { id: 'DRV-003', name: 'FORCEPS HEAVYWEIGHT', tag: 'FRONT & BACK PRINT', badge: null ,image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/neverLose.webp'},
    { id: 'DRV-004', name: 'BLANK CANVAS', tag: 'PLAIN PREMIUM', badge: null ,image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/designed.webp'},
    { id: 'DRV-005', name: 'STREET UNIFORM', tag: 'SINGLE LOGO TEE', badge: 'ESSENTIALS',image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/sabr.webp' },
    { id: 'DRV-006', name: 'STUDIO SAMPLE', tag: 'FULL SLEEVE', badge: null,image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/vintage.webp'},
  ];


function applyTilt(el) {
  if (!el || window.innerWidth < 640) return;

  VanillaTilt.init(el, {
    max: window.innerWidth < 768 ? 5 : 10,
    speed: 400,
    glare: true,
    "max-glare": 0.12,
    scale: 1.02
  });

  return {
    destroy() {
      el.vanillaTilt?.destroy();
    }
  };
}
</script>

<section
  id="gallery"
  class="py-16 sm:py-20 lg:py-40 border-t"
  style="background: var(--bg); border-color: var(--border);"
>
  <div class="max-w-screen-xl mx-auto px-4 sm:px-6 lg:px-10">

    <!-- Heading -->
    <div class="grid gap-6 mb-12 lg:mb-16">
      <h2
        class="display-heading text-4xl sm:text-6xl lg:text-8xl leading-tight"
        style="color: var(--text);"
      >
        THE CURRENT <span style="color: var(--accent);">DROP.</span>
      </h2>

      <p
        class="text-xs sm:text-sm leading-relaxed max-w-md"
        style="color: var(--muted);"
      >
        Every piece below can be re-printed with your artwork. Tap any product and order it over WhatsApp.
      </p>
    </div>

    <!-- Grid -->
    <div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-6">
      {#each products as product}

        <div
          use:applyTilt
          class="group relative overflow-hidden rounded-lg sm:rounded-xl transition-all duration-300 lg:hover:-translate-y-2"
          style="
            background: var(--surface);
            border: 1px solid var(--border);
            box-shadow: var(--shadow);
          "
        >

          <!-- IMAGE -->
          <div
            class="aspect-[4/5] sm:aspect-[3/4] relative overflow-hidden"
            style="background: var(--surface-2);"
          >

            <!-- Badge -->
            {#if product.badge}
              <div class="absolute top-2 right-2 z-10">
                <span
                  class="font-mono text-[10px] sm:text-xs px-2 py-1 rounded"
                  style="background: var(--text); color: var(--bg);"
                >
                  {product.badge}
                </span>
              </div>
            {/if}

            <!-- ID -->
            <div class="absolute top-2 left-2 z-10">
              <span class="font-mono text-[10px] sm:text-xs" style="color: var(--muted);">
                {product.id}
              </span>
            </div>

            <img
              src={product.image}
              alt={product.name}
              class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 lg:group-hover:scale-110"
            />

            <!-- Overlay -->
            <div
              class="absolute inset-0"
              style="background: linear-gradient(to top, rgba(0,0,0,0.4), transparent);"
            ></div>
          </div>

          <!-- INFO -->
          <div
            class="flex flex-col gap-2 sm:flex-row sm:items-center sm:justify-between px-3 sm:px-4 py-3 border-t"
            style="border-color: var(--border);"
          >
            <div>
              <div
                class="display-heading text-sm sm:text-base leading-tight"
                style="color: var(--text);"
              >
                {product.name}
              </div>

              <div
                class="font-mono text-[10px] sm:text-xs"
                style="color: var(--muted);"
              >
                {product.tag}
              </div>
            </div>

            <!-- BUTTON -->
            <a
              href={`https://wa.me/919270905007?text=${encodeURIComponent(`I'm interested in ${product.name} (${product.id})`)}`}
              target="_blank"
              rel="noopener"
              class="w-full sm:w-auto text-center font-mono text-xs px-3 py-2 rounded transition-all duration-200"
              style="border: 1px solid var(--border); color: var(--text);"
            >
              ORDER →
            </a>
          </div>
        </div>

      {/each}
    </div>

  </div>
</section>
