<script lang="ts">
  export let image: string;
  export let description = "";
</script>

<div class="headline-wrapper">
  <div class="headline-background" />
  <h1><img src={image} alt="headline" /></h1>
  {#if description !== ""}
    <p>{description}</p>
  {/if}
</div>

<style lang="scss">
  @use "../variables.scss";

  .headline-wrapper {
    @include center;
    min-height: 50%;
    width: max(100%, 100vw);
    position: relative;
    margin: 70px auto 0;

    h1 {
      display: flex;
      justify-content: center;
    }

    * {
      z-index: 2;
    }

    .headline-background {
      position: absolute;
      inset: 0;
      z-index: 1;
      background-color: $green-1;
      background-image: radial-gradient(
          $green-7,
          rgba(255, 255, 255, 0.2) 2px,
          transparent 40px
        ),
        radial-gradient(white, rgba(255, 255, 255, 0.15) 1px, transparent 30px),
        radial-gradient(white, rgba(255, 255, 255, 0.1) 2px, transparent 40px),
        radial-gradient(
          rgba(255, 255, 255, 0.4),
          rgba(255, 255, 255, 0.1) 2px,
          transparent 30px
        );
      background-size: 550px 550px, 350px 350px, 250px 250px, 150px 150px;
      animation: bg-change 100s infinite linear;
    }

    p {
      color: white;
    }

    img {
      width: min(400px, 80%);
    }
  }

  @keyframes bg-change {
    0%,
    50% {
      background-position: 0 0;
    }
    25% {
      background-position: -100% 0;
    }
    75% {
      background-position: 100% 0;
    }
  }
</style>
