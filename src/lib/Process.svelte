<script>
  const steps = [
    {
      num: '01',
      title: 'SHARE YOUR BRIEF',
      desc: 'DM us on WhatsApp with a rough idea, reference or full-fledged artwork. Tell us quantity and deadline.'
    },
    {
      num: '02',
      title: 'MOCKUP & PROOF',
      desc: 'We send back a digital proof on your selected blank — color, size, placement locked in.'
    },
    {
      num: '03',
      title: 'PRINT RUN',
      desc: 'DTF printed in-house on 240 GSM combed cotton. Quality checked piece by piece.'
    },
    {
      num: '04',
      title: 'DOORSTEP',
      desc: 'Packed, shipped pan-India. Most custom runs land within 3–5 working days.'
    }
  ];
</script>

<section
  id="process"
  class="py-28 lg:py-40 border-t"
  style="background: var(--bg); border-color: var(--border);"
>
  <div class="max-w-screen-xl mx-auto px-6 lg:px-10">

    <!-- Heading -->
    <!-- <div class="mb-4">
      <span class="section-label">[ 04 / THE PROCESS ]</span>
    </div> -->

    <h2
      class="display-heading text-6xl sm:text-7xl lg:text-8xl leading-none mb-16"
      style="color: var(--text);"
    >
      FROM IDEA TO <span style="color: var(--accent);">DOORSTEP.</span>
    </h2>

    <!-- Grid -->
    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6"
    >
      {#each steps as step, i}
        <div
          class=" process-card p-8 lg:p-10 rounded-xl transition-all duration-300 group"
          style="
            background: var(--surface);
            border: 1px solid var(--border);
            box-shadow: var(--shadow);
          "
        >
          <!-- Step Number -->
          <div
            class="display-heading text-5xl mb-6"
            style="color: var(--accent);"
          >
            {step.num}
          </div>

          <!-- Title -->
          <h3
            class="display-heading text-2xl mb-4 leading-tight"
            style="color: var(--text);"
          >
            {step.title}
          </h3>

          <!-- Description -->
          <p
            class="text-sm leading-relaxed"
            style="color: var(--muted);"
          >
            {step.desc}
          </p>

          <!-- Arrow (desktop only) -->
          {#if i < steps.length - 1}
            <div
              class="hidden lg:block absolute top-1/2 right-[-12px] translate-y-[-50%] text-xl"
              style="color: var(--border);"
            >
              →
            </div>
          {/if}
        </div>
      {/each}
    </div>
  </div>
</section>