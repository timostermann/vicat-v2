<script lang="ts">
  import Headline from "../components/Headline.svelte";
  import NftPreview from "../components/NftPreview.svelte";
  import Nft from "../assets/images/headings/nft.png";
</script>

<div class="nft-wrapper">
  <Headline image={Nft} />
  <p class="description">
    The ViCat team proudly presents the ever growing <b>ViCat NFT collection</b
    >. ViCat represents the community and all cats worldwide with joie de vivre,
    colorfulness, adventurousness, thirst for knowledge, crypto love and
    numerous other characteristics. The ViCat NFT collection will show all these
    characteristics.
    <br /><br /><em
      >Each asset is created with great attention to detail by the artistic
      hands of our very talented designer Kvitka.</em
    >
  </p>
  <NftPreview />
  <div class="link-wrapper">
    <a
      href="https://wax.atomichub.io/explorer/collection/vicatuniques"
      target="_blank"
      class="atomichub hover-cursor">Atomichub Collection</a
    >
  </div>
  <p class="description">
    Initially, the ViCat NFT collection will be minted on the <b
      >WAX Blockchain</b
    >
    and published on
    <a href="https://wax.atomichub.io" target="_blank">Atomichub</a>. ViCat NFT
    assets can be shared and traded via the platform. In the future, the
    collection will be extended to the VITE chain. <br /><br /><em
      >By owning assets independently of the blockchain, it will be possible to
      use these assets for services in the ViCat ecosystem. Assets in the ViCat
      NFT collection will be distributed to the community for free at regular
      intervals. Each asset is limited in its occurrence, which is displayed as
      a ball of wool on the asset. There are very rare assets that exist only
      seven times or even only once. The maximum number that can exist for an
      asset is 7777.</em
    >
  </p>
</div>

<style lang="scss">
  .nft-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;

    .description {
      @include description;

      a {
        text-decoration: none;
        color: $orange;
        font-weight: 600;
        letter-spacing: 0.05rem;
      }
    }

    .link-wrapper {
      a {
        @include center;
        @include button;
        width: 300px;
        font-size: 1.7rem;
        &:hover {
          @include button-hover;
        }
      }
    }
  }
</style>
