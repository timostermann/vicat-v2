<script lang="ts">
  import { Icon, X } from "svelte-hero-icons";

  export let src: string;
  export let alt: string;
  export let onClose: () => void;
</script>

<div class="lightbox">
  <div class="overlay" on:click={onClose}>
    <button class="hover-cursor" on:click={onClose}
      ><Icon src={X} size="35px" /></button
    >
    <img {src} {alt} on:click={(event) => event.stopPropagation()} />
  </div>
</div>

<style lang="scss">
  .lightbox {
    position: fixed;
    display: flex;
    inset: 0;
    z-index: 30;

    .overlay {
      @include center;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.8);
    }

    button {
      position: fixed;
      top: 50px;
      right: 30px;
      color: white;
      border: none;
      background: transparent;
      opacity: 1;
      transition: opacity 0.3s;

      &:hover {
        opacity: 0.8;
      }
    }

    img {
      max-width: 90vw;
    }
  }
</style>
