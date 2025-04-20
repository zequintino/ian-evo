<script lang="ts">
  type TypewriterParams = {
    speed?: number;
  };

  function typewriter(node: HTMLElement, { speed = 1 }: TypewriterParams) {
    const originalHTML = node.innerHTML;
    const textContent = node.textContent || "";
    const duration = textContent.length / (speed * 0.01);

    const segments = originalHTML.match(/<[^>]+>|[^<]+/g) || [];

    return {
      duration,
      tick: (t: number) => {
        const targetTextLength = ~~(textContent.length * t);
        let currentTextLength = 0;
        let outputHTML = "";

        for (const segment of segments) {
          if (segment.startsWith("<") && segment.endsWith(">")) {
            outputHTML += segment;
          } else {
            const remainingTarget = targetTextLength - currentTextLength;
            if (remainingTarget <= 0) {
              continue;
            }
            const segmentPortion = segment.slice(0, remainingTarget);
            outputHTML += segmentPortion;
            currentTextLength += segment.length;
          }
        }
        node.innerHTML = outputHTML;
      },
    };
  }

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
</script>

<main>
  <h1>ie</h1>

  <section style="margin: 0 0 15rem 0">
    <h2>
      Cursed tech for<br />
      mischievous togetherness
    </h2>
    <div style="position: relative;">
      <p style="visibility: hidden;">
        {@html paragraphs.intro}
      </p>
      <p
        style="position: absolute; top: 0; left: 0; width: 100%;"
        transition:typewriter={{ speed: 2 }}
      >
        {@html paragraphs.intro}
      </p>
    </div>
  </section>

  <section style="margin: 0 0 7rem 0">
    <h2>Manifesto</h2>
    <div style="position: relative;">
      <p style="visibility: hidden;">
        {@html paragraphs.manifesto}
      </p>
      <p
        style="position: absolute; top: 0; left: 0; width: 100%;"
        transition:typewriter={{ speed: 3 }}
      >
        {@html paragraphs.manifesto}
      </p>
    </div>
  </section>

  <section>
    <h2>Evidence</h2>
  </section>
</main>

<style>
  h1 {
    font-family: "Inknut Antiqua";
    font-weight: 300;
    font-size: 9rem;
    line-height: 1;
    letter-spacing: -0.15em;
    color: #0b0b0b;
    margin: 0 0 5rem 0;
    padding: 0;
  }

  h2 {
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
