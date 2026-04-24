<script>
  let form = { name: '', phone: '', email: '', quantity: '', message: '' };
  let submitted = false;

  function handleSubmit() {

    const msg = encodeURIComponent(
      `Name: ${form.name}\nPhone: ${form.phone}\nEmail: ${form.email}\nQuantity: ${form.quantity}\nMessage: ${form.message}`
    );
    window.open(`https://wa.me/919270905007?text=${msg}`, '_blank');
    submitted = true;
  }
</script>

<section
  id="connect"
  class="py-28 lg:py-40 border-t"
  style="background: var(--bg); border-color: var(--border);"
>
  <div class="max-w-screen-xl mx-auto px-6 lg:px-10">

    <!-- Heading -->
    <!-- <div class="mb-4">
      <span class="section-label">[ 05 / CONNECT ]</span>
    </div> -->

    <h2
      class="display-heading text-6xl sm:text-7xl lg:text-8xl leading-none mb-6"
      style="color: var(--text);"
    >
      DESIGN YOUR <span style="color: var(--accent);">OWN TEE.</span>
    </h2>

    <p
      class="text-sm mb-16 max-w-lg"
      style="color: var(--muted);"
    >
      Drop a message below or ping us on WhatsApp. We reply quickly — artwork, quantity, deadline, we'll handle the rest.
    </p>

    <!-- Layout -->
    <div
      class="grid lg:grid-cols-[380px_1fr] rounded-xl overflow-hidden"
      style="
        border: 1px solid var(--border);
        background: var(--surface);
        box-shadow: var(--shadow);
      "
    >

      <!-- LEFT -->
      <div class="p-8 lg:p-10 flex flex-col gap-8 border-b lg:border-b-0 lg:border-r"
           style="border-color: var(--border);">

        <!-- WhatsApp -->
        <div class="flex gap-4">
          <div class="w-10 h-10 flex items-center justify-center border rounded"
               style="border-color: var(--border);">
            📱
          </div>
          <div>
            <div class="font-mono text-xs uppercase tracking-widest mb-1"
                 style="color: var(--muted);">WhatsApp</div>
            <div class="display-heading text-2xl"
                 style="color: var(--text);">+91 92709 05007</div>
            <div class="font-mono text-xs mt-1"
                 style="color: var(--muted);">9 AM — 9 PM IST</div>
          </div>
        </div>

        <!-- Location -->
        <div class="flex gap-4">
          <div class="w-10 h-10 flex items-center justify-center border rounded"
               style="border-color: var(--border);">
            📍
          </div>
          <div>
            <div class="font-mono text-xs uppercase tracking-widest mb-1"
                 style="color: var(--muted);">Studio</div>
            <div class="display-heading text-2xl"
                 style="color: var(--text);">PUNE, MAHARASHTRA</div>
            <div class="font-mono text-xs mt-1"
                 style="color: var(--muted);">India</div>
          </div>
        </div>

        <!-- Reply -->
        <div class="flex gap-4">
          <div class="w-10 h-10 flex items-center justify-center border rounded"
               style="border-color: var(--border);">
            ✉
          </div>
          <div>
            <div class="font-mono text-xs uppercase tracking-widest mb-1"
                 style="color: var(--muted);">Reply Window</div>
            <div class="display-heading text-2xl"
                 style="color: var(--text);">WITHIN 24 HOURS</div>
            <div class="font-mono text-xs mt-1"
                 style="color: var(--muted);">On business days</div>
          </div>
        </div>

        <!-- CTA -->
        <a
          href="https://wa.me/919270905007"
          target="_blank"
          rel="noopener"
          class="btn-primary mt-auto w-full justify-center"
        >
          CHAT ON WHATSAPP
        </a>
      </div>

      <!-- RIGHT -->
      <div class="p-8 lg:p-10">
        {#if submitted}
          <div class="flex flex-col items-center justify-center h-full text-center py-16">
            <div class="display-heading text-4xl mb-4"
                 style="color: var(--accent);">SENT.</div>
            <p style="color: var(--muted);">
              Opening WhatsApp with your details. We'll get back to you within 24 hours.
            </p>
          </div>
        {:else}

          <!-- Inputs -->
          <div class="grid grid-cols-2 gap-6 mb-6">
            <div>
              <label class="font-mono text-xs uppercase mb-2 block"
                     style="color: var(--muted);">Name</label>
              <input bind:value={form.name} type="text"
                     class="w-full bg-transparent border-b pb-2 outline-none"
                     style="border-color: var(--border); color: var(--text);"
                     placeholder="Your name" />
            </div>

            <div>
              <label class="font-mono text-xs uppercase mb-2 block"
                     style="color: var(--muted);">Phone</label>
              <input bind:value={form.phone} type="tel"
                     class="w-full bg-transparent border-b pb-2 outline-none"
                     style="border-color: var(--border); color: var(--text);"
                     placeholder="+91 XXXXX XXXXX" />
            </div>
          </div>

          <div class="grid grid-cols-2 gap-6 mb-6">
            <input bind:value={form.email} type="email"
                   placeholder="Email (optional)"
                   class="border-b pb-2 outline-none bg-transparent"
                   style="border-color: var(--border); color: var(--text);" />

            <input bind:value={form.quantity} type="text"
                   placeholder="Quantity"
                   class="border-b pb-2 outline-none bg-transparent"
                   style="border-color: var(--border); color: var(--text);" />
          </div>

          <textarea bind:value={form.message} rows="4"
                    class="w-full p-4 rounded-lg outline-none mb-6"
                    style="
                      background: var(--surface-2);
                      border: 1px solid var(--border);
                      color: var(--text);
                    "
                    placeholder="Tell us about your design..."></textarea>

          <div class="flex justify-between items-center">
            <span class="text-xs"
                  style="color: var(--muted);">
              WE NEVER SHARE YOUR DETAILS.
            </span>

            <button on:click={handleSubmit} class="btn-border">
              SEND →
            </button>
          </div>
        {/if}
      </div>
    </div>
  </div>
</section>
