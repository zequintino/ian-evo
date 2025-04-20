<script lang="ts">
  import { onMount, onDestroy } from "svelte";

  type Props = {
    tag: "h1" | "h2" | "h3" | "h4" | "h5" | "h6" | "p" | "span";
    content: string;
    flashColor?: string;
    flashInterval?: number;
    flashDuration?: number;
  };

  let {
    tag,
    content,
    flashColor = "#F8F8F8",
    flashInterval = 150,
    flashDuration = 100,
  }: Props = $props();

  let elementRef: HTMLElement | null = null;
  let intervalId: number | undefined = undefined;
  let spans: HTMLElement[] = [];

  // Split content into characters/tags, wrapping chars in spans
  const segments = content.match(/<[^>]+>|./gs) || []; // Match tags or single chars (incl. whitespace)
  const processedContent = segments
    .map((seg) => {
      if (seg.startsWith("<") && seg.endsWith(">")) {
        return seg;
      } else if (seg.trim() === "") {
        return seg;
      } else {
        return `<span class="flashable">${seg}</span>`;
      }
    })
    .join("");

  onMount(() => {
    if (elementRef) {
      // Get references to the character spans after mount
      spans = Array.from(elementRef.querySelectorAll(".flashable"));

      intervalId = setInterval(() => {
        if (spans.length > 0) {
          const randomIndex = Math.floor(Math.random() * spans.length);
          const span = spans[randomIndex];

          if (span) {
            const originalColor =
              span.style.color || window.getComputedStyle(span).color; // Store original (or inherited) color
            span.style.transition = "color 0.05s ease-in-out"; // Quick transition
            span.style.color = flashColor;

            setTimeout(() => {
              // Restore original color after flash duration
              span.style.color = originalColor;
            }, flashDuration);
          }
        }
      }, flashInterval);
    }
  });

  onDestroy(() => {
    if (intervalId) {
      clearInterval(intervalId);
    }
  });
</script>

<!-- Render the dynamic tag with processed content -->
<svelte:element this={tag} bind:this={elementRef}>
  {@html processedContent}
</svelte:element>

<style>
  /* Add any specific styles for the container if needed */
  :global(.flashable) {
    /* Ensures spans behave correctly for styling */
    display: inline-block;
    /* Prevent color inheritance from overriding flash */
    color: inherit;
  }
</style>
