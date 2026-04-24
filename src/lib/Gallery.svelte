<script>
  import VanillaTilt from "vanilla-tilt";

  let selectedCategory = "All";

  const categories = ["All", "Oversized", "Polo", "Kids", "Plain", "Custom"];

  const products = [
    { id: 'DRV-001', name: 'RAWPRINT OVERSIZED', tag: 'SIGNATURE GRAPHIC', category: 'Oversized', badge: null, image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/inkDrop.webp' },
    { id: 'DRV-002', name: 'NOIR ESSENTIAL', tag: 'SINGLE LOGO TEE', category: 'Plain', badge: 'ESSENTIALS', image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/chimya.png'},
    { id: 'DRV-003', name: 'FORCEPS HEAVYWEIGHT', tag: 'FRONT & BACK PRINT', category: 'Oversized', badge: null, image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/neverLose.webp'},
    { id: 'DRV-004', name: 'BLANK CANVAS', tag: 'PLAIN PREMIUM', category: 'Plain', badge: null, image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/plain.webp'},
    { id: 'DRV-005', name: 'STREET UNIFORM', tag: 'SINGLE LOGO TEE', category: 'Oversized', badge: 'ESSENTIALS', image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/sabr.webp'},
    { id: 'DRV-006', name: 'STUDIO SAMPLE', tag: 'FULL SLEEVE', category: 'Oversized', badge: null, image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/vintage.webp'},

    // NEW TYPES
    { id: 'DRV-007', name: 'KIDS BASIC TEE', tag: 'SOFT COTTON', category: 'Kids', badge: 'NEW', image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/kids.png' },
    { id: 'DRV-008', name: 'CLASSIC POLO', tag: 'PREMIUM COLLAR', category: 'Polo', badge: null, image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/polo.jpg' },
    { id: 'DRV-009', name: 'CUSTOM PRINT TEE', tag: 'YOUR DESIGN', category: 'Custom', badge: 'CUSTOM', image:'https://raw.githubusercontent.com/OmkarpatilGithub/Omeva_store/main/static/custom.png' }
  ];

  $: filteredProducts =
    selectedCategory === "All"
      ? products
      : products.filter(p => p.category === selectedCategory);

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

  function getWhatsAppLink(product) {
    return `https://wa.me/919270905007?text=${encodeURIComponent(
      `Hi, I'm interested in:\nProduct: ${product.name}\nCategory: ${product.category}\nCode: ${product.id}`
    )}`;
  }
</script>

<section
  id="gallery"
  class="py-16 sm:py-20 lg:py-40 border-t"
  style="background: var(--bg); border-color: var(--border);"
>
  <div class="max-w-screen-xl mx-auto px-4 sm:px-6 lg:px-10">

    <!-- Heading -->
    <div class="grid gap-6 mb-10">
      <h2 class="display-heading text-4xl sm:text-6xl lg:text-8xl" style="color: var(--text);">
        THE CURRENT <span style="color: var(--accent);">DROP.</span>
      </h2>

      <p class="text-xs sm:text-sm max-w-md" style="color: var(--muted);">
        Choose from multiple categories or create your own custom design.
      </p>
    </div>

    <!-- FILTERS -->
    <div class="flex flex-wrap gap-2 mb-8">
      {#each categories as cat}
        <button
          on:click={() => selectedCategory = cat}
          class="px-3 py-1 text-xs rounded border transition"
          style="
            border-color: var(--border);
            background: {selectedCategory === cat ? 'var(--text)' : 'transparent'};
            color: {selectedCategory === cat ? 'var(--bg)' : 'var(--text)'};
          "
        >
          {cat}
        </button>
      {/each}
    </div>

    <!-- GRID -->
    <div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-6">

      {#each filteredProducts as product}
        <div
          use:applyTilt
          class="group relative overflow-hidden rounded-xl transition-all duration-300 lg:hover:-translate-y-2"
          style="background: var(--surface); border: 1px solid var(--border); box-shadow: var(--shadow);"
        >

          <!-- IMAGE -->
          <div class="aspect-[4/5] relative overflow-hidden">

            {#if product.badge}
              <div class="absolute top-2 right-2 z-10">
                <span class="text-xs px-2 py-1 rounded" style="background: var(--text); color: var(--bg);">
                  {product.badge}
                </span>
              </div>
            {/if}

            <div class="absolute top-2 left-2 z-10 text-xs" style="color: var(--muted);">
              {product.id}
            </div>

            <img
              src={product.image}
              alt={product.name}
              class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 lg:group-hover:scale-110"
            />

            <div class="absolute inset-0 bg-gradient-to-t from-black/40 to-transparent"></div>
          </div>

          <!-- INFO -->
          <div class="px-4 py-3 border-t" style="border-color: var(--border);">

            <div class="text-sm font-semibold" style="color: var(--text);">
              {product.name}
            </div>

            <div class="text-xs" style="color: var(--muted);">
              {product.tag}
            </div>

            <!-- CATEGORY -->
            <div class="text-[10px] mt-1" style="color: var(--accent);">
              {product.category}
            </div>

            <!-- BUTTON -->
            <a
              href={getWhatsAppLink(product)}
              target="_blank"
              class="block mt-3 text-center text-xs px-3 py-2 rounded border transition"
              style="border-color: var(--border); color: var(--text);"
            >
              ORDER →
            </a>
          </div>
        </div>
      {/each}

      <!-- CUSTOM CARD -->
      <div class="flex flex-col justify-center items-center border rounded-xl p-6 text-center"
        style="border-color: var(--border);">

        <p class="text-sm mb-3" style="color: var(--text);">
          Have your own design?
        </p>

        <a
          href="https://wa.me/919270905007?text=I want a custom t-shirt design"
          target="_blank"
          class="text-xs underline"
          style="color: var(--accent);"
        >
          Request Custom →
        </a>
      </div>

    </div>
  </div>
</section>
