<script lang="ts">
  import Headline from "../components/Headline.svelte";
  import Presale from "../assets/images/headings/presale.png";

  let counters = {
    transactions1: 516,
    transactions2: 893,
    vicat: 116_666_666_666,
    vite1: 2_916_666,
    vite2: 3_900_310,
  };
</script>

<div class="presale-wrapper">
  <Headline image={Presale} />
  <p class="description">
    ViCat <b>PreSale</b> was a tremendous success thanks to our incredible
    community.
    <em
      >To provide a better picture of the PreSale's success: Here are some stats
      for you!</em
    >
  </p>
  <div class="stat-section">
    <h2>The PreSale sold out in 2 hours! There were...</h2>
    <div class="stats-wrapper">
      <div class="stat">
        <p class="number">{counters.transactions1.toLocaleString()}</p>
        <p class="label">Transactions</p>
      </div>
      <div class="stat">
        <p class="number">{counters.vicat.toLocaleString()}</p>
        <p class="label">ViCat sold</p>
      </div>
      <div class="stat">
        <p class="number">{counters.vite1.toLocaleString()}</p>
        <p class="label">VITE spent</p>
      </div>
    </div>
  </div>
  <div class="stat-section">
    <h2>
      After ending the PreSale, there were still transactions coming in (and
      refunded). <br />In total, there were...
    </h2>
    <div class="stats-wrapper">
      <div class="stat">
        <p class="number">{counters.transactions2.toLocaleString()}</p>
        <p class="label">Transactions</p>
      </div>

      <div class="stat">
        <p class="number">{counters.vite2.toLocaleString()}</p>
        <p class="label">VITE sent</p>
      </div>
    </div>
  </div>
</div>

<style lang="scss">
  .presale-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;

    .description {
      @include description;
    }
  }

  .stat-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-block: 50px 20px;
    padding-inline: min(50px, 5%);

    &:not(&:last-child) {
      margin-bottom: 70px;
    }

    h2 {
      font-weight: 200;
      font-size: 2rem;
      letter-spacing: 0.05rem;
      line-height: 1.5;
      color: white;
      text-align: center;

      @media (max-width: $tablet) {
        font-size: 1.5rem;
      }
    }

    .stats-wrapper {
      display: flex;
      justify-content: center;

      @media (max-width: $large) {
        flex-direction: column;
        align-items: center;
      }

      .stat {
        display: flex;
        flex-direction: column;
        align-items: center;

        @media (max-width: $large) {
          width: 100%;
          margin-right: 0 !important;
        }

        &:not(&:last-child) {
          margin-right: 120px;
        }

        .number {
          font-size: 4rem;
          margin-bottom: 25px;
          color: #fff;
          text-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff,
            0 0 42px $orange, 0 0 82px $orange, 0 0 92px $orange,
            0 0 102px $orange, 0 0 151px $orange;

          @media (max-width: $tablet) {
            font-size: 2.5rem;
          }
        }

        .label {
          font-size: 2.5rem;
          font-weight: 600;
          background: -webkit-linear-gradient($yellow, $orange);
          background-clip: text;
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;

          @media (max-width: $tablet) {
            font-size: 1.7rem;
          }
        }
      }
    }
  }
</style>
