<script lang="ts">
  import EvidenceGrid from "./lib/EvidenceGrid.svelte";
  import FlashingText from "./lib/FlashingText.svelte";

  // type TypewriterParams = {
  //   speed?: number;
  // };

  // function typewriter(node: HTMLElement, { speed = 1 }: TypewriterParams) {
  //   const originalHTML = node.innerHTML;
  //   const textContent = node.textContent || "";
  //   const duration = textContent.length / (speed * 0.01);

  //   const segments = originalHTML.match(/<[^>]+>|[^<]+/g) || [];

  //   return {
  //     duration,
  //     tick: (t: number) => {
  //       const targetTextLength = ~~(textContent.length * t);
  //       let currentTextLength = 0;
  //       let outputHTML = "";

  //       for (const segment of segments) {
  //         if (segment.startsWith("<") && segment.endsWith(">")) {
  //           outputHTML += segment;
  //         } else {
  //           const remainingTarget = targetTextLength - currentTextLength;
  //           if (remainingTarget <= 0) {
  //             continue;
  //           }
  //           const segmentPortion = segment.slice(0, remainingTarget);
  //           outputHTML += segmentPortion;
  //           currentTextLength += segment.length;
  //         }
  //       }
  //       node.innerHTML = outputHTML;
  //     },
  //   };
  // }

  const titles = {
    main: "ie",
    subtitle: "Cursed tech for<br />mischievous togetherness",
    manifesto: "Manifesto",
    evidence: "Evidence",
  };

  const paragraphs = {
    intro: `
      A studio for experiments, <i>microproducts</i>, and creative tech that
      doesn't scale. Publishing through local, specific, and brief prototypes.
    `,
    manifesto: `
      We system-pair creatives and technologists to build together. Not forever,
      just for a while. We don't scale, we don't optimise, we don't repeat. Each
      project is an excuse to learn, an experiment, a <i>microproduct</i> (sometimes
      useful, sometimes funny, sometimes both). Curatorship is the method, collaboration
      is the form, publication is the output. We work locally, specifically, briefly,
      leaving traces but no traffic. No roadmap, no KPIs, no funnels, just curiosity
      and a deadline. 3 months max. Open source only.
    `,
  };

  const evidenceData = [
    {
      title: "Is the Machine Working?",
      description:
        "Find out if the ticket machines are broken before you go underground. Built with scrap code and civic frustration.",
      status: "[Coming Soon]",
    },
    {
      title: "Ham Prep PT",
      description: "The Millennial Guide to the CAT III exam in Portugal.",
      status: "[Coming Soon]",
    },
    {
      title: "Careful, PiBites",
      description:
        "A Raspberry Pi barks if someone enters your flat. Because thieves deserve to laugh too.",
      status: "[Coming Soon]",
    },
    {
      title: "SpamBots for a Better World",
      description:
        "The daily automated spam will continue until infrastructure improves. Anti-bureaucracy strategies for the new world.",
      status: "[Coming Soon]",
    },
  ];
</script>

<main>
  <FlashingText
    tag="h1"
    content={titles.main}
    flashInterval={1000}
    flashDuration={100}
  />

  <section style="margin: 0 0 15rem 0">
    <FlashingText
      tag="h2"
      content={titles.subtitle}
      flashInterval={1100}
      flashDuration={200}
    />
    <div style="position: relative;">
      <p style="visibility: hidden;">
        {@html paragraphs.intro}
      </p>
      <!-- transition:typewriter={{ speed: 2 }} -->
      <p style="position: absolute; top: 0; left: 0; width: 100%;">
        {@html paragraphs.intro}
      </p>
    </div>
  </section>

  <section style="margin: 0 0 7rem 0">
    <FlashingText
      tag="h2"
      content={titles.manifesto}
      flashInterval={1500}
      flashDuration={400}
    />
    <div style="position: relative;">
      <p style="visibility: hidden;">
        {@html paragraphs.manifesto}
      </p>
      <!-- transition:typewriter={{ speed: 3 }} -->
      <p style="position: absolute; top: 0; left: 0; width: 100%;">
        {@html paragraphs.manifesto}
      </p>
    </div>
  </section>

  <section style="margin: 0 0 7rem 0">
    <FlashingText
      tag="h2"
      content={titles.evidence}
      flashInterval={800}
      flashDuration={100}
    />
    <EvidenceGrid evidences={evidenceData} />
  </section>
</main>

<style>
  :global(h1) {
    font-family: "Inknut Antiqua";
    font-weight: 300;
    font-size: 9rem;
    line-height: 1;
    letter-spacing: -0.15em;
    color: #0b0b0b;
    margin: 0 0 5rem 0;
    padding: 0;
  }

  :global(h2) {
    font-family: "Inknut Antiqua";
    font-weight: 300;
    font-size: 3.7rem;
    line-height: 1.2;
    letter-spacing: -0.1em;
    color: #0b0b0b;
    margin: 0 0 0.7rem 0;
    padding: 0;
  }

  p {
    font-family: "Inter";
    font-weight: 300;
    font-size: 1.9rem;
    line-height: 1;
    letter-spacing: -0.02em;
    color: #0b0b0b;
    margin: 0;
    padding: 0;
  }
</style>
