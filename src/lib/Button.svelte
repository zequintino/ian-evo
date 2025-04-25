<script lang="ts">
  interface Props {
    firstHalf?: string;
    secondHalf?: string;
    specialChar?: string;
  }

  let { firstHalf = "", secondHalf = "", specialChar = "" }: Props = $props();
</script>

<button>
  {firstHalf}<span>{specialChar}</span>{secondHalf}
</button>

<style>
  button {
    font-family: "Inter";
    font-weight: 300;
    font-size: 1.9rem;
    line-height: 1.3;
    letter-spacing: -0.02em;
    background-color: #000000;
    color: #ffffff;
    margin: 0;
    padding: 0.8em 0.5em;
    word-break: keep-all;
    white-space: normal;
    hyphens: manual;
    cursor: pointer;
    border: none;
  }

  span {
    font-family: "Inknut Antiqua";
    font-weight: 300;
    font-size: 1.9rem;
    line-height: 1.3;
    letter-spacing: -0.02em;
    color: #ffffff;
    margin: 0;
    word-break: keep-all;
    white-space: normal;
    hyphens: manual;
  }
</style>
