<script lang="ts">
  import EvidenceGrid from "./lib/EvidenceGrid.svelte";
  import FlashingText from "./lib/FlashingText.svelte";
  import ProjectList from "./lib/ProjectList.svelte";
  import Button from "./lib/Button.svelte";
  import { titles, paragraphs, projects, evidenceData, footerData,} from "./lib/utils/content";

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

  <aside>
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
  </aside>
</main>

<aside style="padding: 0 0.7em">
  <div class="buttons-container">
    <Button firstHalf="Submit " specialChar="m" secondHalf="ischief" />
    <Button firstHalf="Conspire with " specialChar="u" secondHalf="s" />
  </div>

  <p class="cta-description">Unserious inquiries only.</p>
</aside>

<footer style="padding: 0 0.7em">
  <p class="footer-left">{footerData.leftColumn}</p>
  <img src="/ie-logo.svg" alt="i.e., logo" />
  <p class="footer-right">{footerData.rightColumn}</p>
</footer>

<style>
  .buttons-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 0.4rem;
    margin: 0 0 0.9rem 0;
  }

  .cta-description {
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
