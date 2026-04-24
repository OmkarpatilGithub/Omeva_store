<footer
  class="border-t py-16 lg:py-20"
  style="background: var(--bg); border-color: var(--border);"
>
  <div class="max-w-screen-xl mx-auto px-6 lg:px-10">

    <!-- Top -->
    <div class="grid grid-cols-2 lg:grid-cols-[1fr_auto_auto] gap-12 lg:gap-24 items-start mb-16">

      <!-- Brand -->
      <div class="col-span-2 lg:col-span-1">
        <div
          class="display-heading text-[5rem] sm:text-[6rem] lg:text-[8rem] leading-none"
          style="color: var(--text);"
        >
          OMEVA<span style="color: var(--accent);">.</span>
        </div>

        <p
          class="text-sm mt-4 max-w-xs"
          style="color: var(--muted);"
        >
          Wear your print. A custom-printed tee label from Pune, India.<br />
          Est. 2025.
        </p>
      </div>

      <!-- Navigate -->
      <div>
        <div
          class="font-mono text-xs uppercase tracking-widest mb-6"
          style="color: var(--muted);"
        >
          Navigate
        </div>

        <div class="flex flex-col gap-4">
          <a href="#gallery" class="nav-link">Gallery</a>
          <a href="#about" class="nav-link">About</a>
          <a href="#process" class="nav-link">Process</a>
          <a href="#connect" class="nav-link">Connect</a>
        </div>
      </div>

      <!-- Contact -->
      <div>
        <div
          class="font-mono text-xs uppercase tracking-widest mb-6"
          style="color: var(--muted);"
        >
          Contact
        </div>

        <div class="flex flex-col gap-3">
          <span style="color: var(--text);" class="text-sm">
            +91 92709 05007
          </span>
          <span style="color: var(--muted);" class="text-sm">
            Pune, Maharashtra — IN
          </span>
          <span style="color: var(--muted);" class="text-sm">
            Mon — Sat, 9am – 9pm IST
          </span>
        </div>

        <!-- Social -->
        <div class="flex gap-3 mt-6">
          <a
            href="https://instagram.com"
            target="_blank"
            rel="noopener"
            class="w-9 h-9 flex items-center justify-center text-xs rounded transition-all duration-200"
            style="border: 1px solid var(--border); color: var(--muted);"
            on:mouseover={(e) => {
              e.currentTarget.style.color = 'var(--text)';
              e.currentTarget.style.borderColor = 'var(--text)';
            }}
            on:mouseout={(e) => {
              e.currentTarget.style.color = 'var(--muted)';
              e.currentTarget.style.borderColor = 'var(--border)';
            }}
          >
            IG
          </a>

          <a
            href="https://x.com"
            target="_blank"
            rel="noopener"
            class="w-9 h-9 flex items-center justify-center text-xs rounded transition-all duration-200"
            style="border: 1px solid var(--border); color: var(--muted);"
            on:mouseover={(e) => {
              e.currentTarget.style.color = 'var(--text)';
              e.currentTarget.style.borderColor = 'var(--text)';
            }}
            on:mouseout={(e) => {
              e.currentTarget.style.color = 'var(--muted)';
              e.currentTarget.style.borderColor = 'var(--border)';
            }}
          >
            X
          </a>
        </div>
      </div>
    </div>

    <!-- Bottom -->
    <div
      class="pt-8 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4"
      style="border-top: 1px solid var(--border);"
    >
      <span
        class="font-mono text-xs"
        style="color: var(--muted);"
      >
        © 2025 OMEVA — ALL RIGHTS RESERVED.
      </span>

      <span
        class="font-mono text-xs"
        style="color: var(--muted);"
      >
        CRAFTED IN PUNE / WEAR YOUR PRINT.
      </span>
    </div>
  </div>
</footer>