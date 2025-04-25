<script lang="ts">
  import EvidenceGrid from "./lib/EvidenceGrid.svelte";
  import FlashingText from "./lib/FlashingText.svelte";
  import ProjectList from "./lib/ProjectList.svelte";
  import Button from "./lib/Button.svelte";

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
    location: "Based somewhere and accepting<br />projects sometimes",
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

  const projects = ["svelte-based projects", "LoRa protocol initiatives"];

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

  const footerData = {
    leftColumn: "ie",
    centerColumn: "© 2024",
    rightColumn: "info@ie-studio.xyz",
  };
</script>

<main>
  <h1>{titles.main}</h1>

  <section style="margin: 0 0 15rem 0">
    <FlashingText
      tag="h2"
      content={titles.subtitle}
      flashInterval={1100}
      flashDuration={200}
      glitchInterval={3000}
      glitchDuration={70}
    />
    <p>
      {@html paragraphs.intro}
    </p>
  </section>

  <section style="margin: 0 0 7rem 0">
    <FlashingText
      tag="h2"
      content={titles.manifesto}
      flashInterval={1500}
      flashDuration={400}
      glitchInterval={4000}
      glitchDuration={60}
    />
    <p>
      {@html paragraphs.manifesto}
    </p>
  </section>

  <section style="margin: 0 0 15rem 0">
    <FlashingText
      tag="h2"
      content={titles.evidence}
      flashInterval={800}
      flashDuration={100}
      glitchInterval={2500}
      glitchDuration={50}
    />
    <EvidenceGrid evidences={evidenceData} />
  </section>

  <div>
    <FlashingText
      tag="h2"
      content={titles.location}
      flashInterval={1100}
      flashDuration={200}
      glitchInterval={3000}
      glitchDuration={70}
    />

    <h3 style="margin: 2rem 0 0 0">Now open to:</h3>
    <ProjectList projectDescriptionList={projects} />
  </div>

  <div class="buttons-container">
    <Button firstHalf="Submit " specialChar="m" secondHalf="ischief" />
    <Button firstHalf="Conspire with " specialChar="u" secondHalf="s" />
  </div>

  <p class="buttons-description">Unserious inquiries only.</p>

  <footer>
    <p class="footer-left">© i.e., 2025</p>
    <img src="/assets/ie-logo.svg" alt="i.e., logo" />
    <p class="footer-right">no cookies, no analytics.</p>
  </footer>
</main>

<style>
  .buttons-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 0.4rem;
    margin: 0 0 0.9rem 0;
  }

  .buttons-description {
    font-size: 1.1rem;
    font-weight: 400;
    text-align: center;
    margin: 0 0 9rem 0;
  }

  footer {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: start;
    margin: 0 0 0.5rem 0;
    font-size: 1.1rem;
    color: #0b0b0b;
  }

  .footer-left {
    font-size: 1rem;
    font-weight: 400;
    text-align: left;
  }

  .footer-right {
    font-size: 1rem;
    font-weight: 400;
    text-align: right;
  }

  footer img {
    width: 1.7rem;
    height: auto;
    margin: 0;
  }
</style>
