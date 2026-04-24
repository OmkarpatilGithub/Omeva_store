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
    if (!el || window.innerWidth < 768) return;

    VanillaTilt.init(el, {
      max: 10,
      speed: 400,
      glare: true,
      "max-glare": 0.15,
      scale: 1.03
    });
  }
</script>

<section
  id="gallery"
  class="py-28 lg:py-40 border-t"
  style="background: var(--bg); border-color: var(--border);"
>
  <div class="max-w-screen-xl mx-auto px-6 lg:px-10">

    <!-- Heading -->
    <div class="grid lg:grid-cols-2 gap-6 items-end mb-16">
      <div>
        <h2
          class="display-heading text-6xl sm:text-7xl lg:text-8xl leading-none mt-2"
          style="color: var(--text);"
        >
          THE CURRENT <span style="color: var(--accent);">DROP.</span>
        </h2>
      </div>

      <p
        class="text-sm leading-relaxed max-w-sm lg:ml-auto"
        style="color: var(--muted);"
      >
        Every piece below can be re-printed with your artwork. Tap any product and order it over WhatsApp.
      </p>
    </div>

    <!-- Grid -->
    <div class="grid grid-cols-2 lg:grid-cols-3 gap-6">
      {#each products as product}

        <!-- CARD -->
        <div
          use:applyTilt
          class="group relative overflow-hidden rounded-xl transition-all duration-300 hover:-translate-y-2"
          style="
            background: var(--surface);
            border: 1px solid var(--border);
            box-shadow: var(--shadow);
          "
        >

          <!-- IMAGE AREA -->
          <div
            class="aspect-[3/4] relative overflow-hidden"
            style="background: var(--surface-2);"
          >

            <!-- Badge -->
            {#if product.badge}
              <div class="absolute top-3 right-3 z-10">
                <span
                  class="font-mono text-xs px-2 py-1 tracking-widest rounded"
                  style="background: var(--text); color: var(--bg);"
                >
                  {product.badge}
                </span>
              </div>
            {/if}

            <!-- ID -->
            <div class="absolute top-3 left-3 z-10">
              <span class="font-mono text-xs" style="color: var(--muted);">
                {product.id}
              </span>
            </div>

            <!-- IMAGE (replace later with real images) -->
            <img
              src={product.image}
              alt={product.name}
              class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
            />

            <!-- Overlay -->
            <div
              class="absolute inset-0"
              style="background: linear-gradient(to top, rgba(0,0,0,0.4), transparent);"
            ></div>

            <!-- Hover TEXT -->
            <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition duration-300">
              <!-- <div
                class="display-heading text-5xl tracking-widest"
                style="color: white;"
              >
                VIEW
              </div> -->
            </div>
          </div>

          <!-- INFO -->
          <div
            class="flex items-center justify-between px-4 py-3 border-t"
            style="border-color: var(--border);"
          >
            <div>
              <div
                class="display-heading text-base leading-tight"
                style="color: var(--text);"
              >
                {product.name}
              </div>

              <div
                class="font-mono text-xs"
                style="color: var(--muted);"
              >
                {product.tag}
              </div>
            </div>

            <!-- ORDER BUTTON -->
          <a
  href={`https://wa.me/919270905007?text=${encodeURIComponent(
    `I'm interested in ${product.name} (${product.id})`
  )}`}
  target="_blank"
  rel="noopener"
  class="font-mono text-xs px-3 py-1.5 transition-all duration-200 whitespace-nowrap rounded"
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
