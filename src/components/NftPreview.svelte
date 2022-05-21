<script lang="ts">
  import Front from "../assets/images/nft_front.jpg";
  import Back from "../assets/images/nft_back.jpg";
  import Tooltip from "./Tooltip.svelte";
</script>

<div class="image-section">
  <h2>Example Asset</h2>
  <div class="image-wrapper front">
    <div class="image">
      <div class="tooltip-wrapper asset">
        <Tooltip text="Unique Drawing" direction="top" />
      </div>
      <div class="tooltip-wrapper name">
        <Tooltip text="Asset Name" direction="bottom" />
      </div>
      <div class="tooltip-wrapper rarity">
        <Tooltip text="Color Code: Rarity" direction="bottom" />
      </div>
      <div class="tooltip-wrapper number">
        <Tooltip text="#: Asset Number" direction="top" />
      </div>
      <img src={Front} alt="NFT Front" />
    </div>
    <h3>Front</h3>
  </div>
  <div class="image-wrapper back">
    <div class="image">
      <div class="tooltip-wrapper table">
        <Tooltip text="Rarity Table" direction="top" />
      </div>
      <img src={Back} alt="NFT Back" />
    </div>
    <h3>Back</h3>
  </div>
</div>

<style lang="scss">
  .image-section {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 100%;

    @media (max-width: $tablet) {
      flex-direction: column;
    }

    h2 {
      @include headline;
      flex-basis: 100%;
      text-align: center;
    }

    .image-wrapper {
      display: flex;
      flex-direction: column;
      align-items: center;

      @media (min-width: $tablet) {
        &:last-child {
          margin-left: 50px;
        }
      }

      .image {
        position: relative;
        max-width: 300px;
        border-radius: 10px;
        box-shadow: 0 5px 20px white;
        transform: scale(1);
        transition: box-shadow 0.5s ease, transform 0.5s ease;

        @media (max-width: $mobile) {
          max-width: 200px;
        }

        &:hover {
          box-shadow: 0 2px 30px white;
          transform: scale(1.05);
        }

        .tooltip-wrapper {
          position: absolute;

          &.asset {
            top: 50%;
            left: 50%;
          }

          &.name {
            bottom: 10%;
            left: 65%;
          }

          &.number {
            top: 6%;
            left: -4%;
          }

          &.rarity {
            top: 15%;
            left: 8%;
          }

          &.table {
            top: 27%;
            left: 65%;
          }
        }

        img {
          border-radius: 10px;
          max-width: 100%;
          max-height: 100%;
        }
      }

      h3 {
        @include headline;
        font-size: 1.4rem;
      }
    }
  }
</style>
