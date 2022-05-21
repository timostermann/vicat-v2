<script lang="ts">
  export let text: string | undefined;
  export let direction: "top" | "right" | "bottom" | "left";
  import ClickOutside from "svelte-click-outside";

  let open = false;
</script>

<div class="tooltip">
  <ClickOutside on:clickoutside={() => (open = false)}>
    <button
      on:click={() => {
        open = !open;
      }}
      class="icon hover-cursor">i</button
    >
  </ClickOutside>
  <div class={`text-wrapper ${direction} ${open && "open"}`}>
    {#if text}
      <p>{text}</p>
    {:else}
      <slot />
    {/if}
  </div>
</div>

<style lang="scss">
  .tooltip {
    display: flex;
    position: relative;

    .icon {
      @include center;
      width: 33px;
      height: 33px;
      border-radius: 100%;
      border: 1px solid $orange-7;
      background-color: rgba(230, 153, 0, 0.9);
      color: white;
      box-shadow: 0 0 5px $orange-3;
      font-family: Georgia, "Times New Roman", Times, serif;
      font-size: 1.05rem;

      @media (max-width: $mobile) {
        width: 28px;
        height: 28px;
      }
    }

    &:hover .text-wrapper,
    &:active .text-wrapper,
    .text-wrapper.open {
      visibility: visible;
      opacity: 1;
    }

    .text-wrapper {
      visibility: hidden;
      width: 150px;
      background: linear-gradient(
        -90deg,
        rgba(230, 153, 0, 0.95),
        rgba(194, 129, 0, 0.85)
      );
      color: #fff;
      border: 1px solid white;
      text-align: center;
      border-radius: 6px;
      font-weight: 500;
      position: absolute;
      z-index: 1;
      opacity: 0;
      transition: opacity 0.3s;

      @media (max-width: $mobile) {
        width: 100px;
        font-size: 0.75rem;
      }

      p {
        margin: 0;
        padding: 10px 5px;

        @media (max-width: $mobile) {
          padding: 5px 2px;
        }
      }

      &::after {
        content: "";
        position: absolute;
        border-width: 5px;
        border-style: solid;
      }

      &.top {
        bottom: 125%;
        left: 50%;
        margin-left: -75px;

        @media (max-width: $mobile) {
          margin-left: -50px;
        }

        &::after {
          top: 100%;
          left: 50%;
          margin-left: -5px;
          border-color: $orange transparent transparent transparent;
        }
      }

      &.bottom {
        top: 135%;
        left: 50%;
        margin-left: -75px;

        @media (max-width: $mobile) {
          margin-left: -50px;
        }

        &::after {
          bottom: 100%;
          left: 50%;
          margin-left: -5px;
          border-color: transparent transparent $orange transparent;
        }
      }

      &.right {
        top: 0;
        left: 125%;

        &::after {
          top: 17px;
          right: 100%;
          margin-top: -5px;
          border-color: transparent $orange transparent transparent;
        }
      }

      &.left {
        top: 0;
        bottom: auto;
        right: 128%;

        &::after {
          top: 17px;
          left: 100%;
          margin-top: -5px;
          border-color: transparent transparent transparent $orange;
        }
      }
    }
  }
</style>
