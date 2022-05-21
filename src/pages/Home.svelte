<script lang="ts">
  import Headline from "../components/Headline.svelte";
  import Home from "../assets/images/headings/home.png";
  import Team from "../assets/images/team.jpg";
  import Twitter from "../assets/images/twitter.png";
  import Discord from "../assets/images/discord.png";
  import Telegram from "../assets/images/telegram.png";
  import Roadmap from "../assets/images/roadmap.png";
  import { Link } from "svelte-navigator";
  import Lightbox from "../components/Lightbox.svelte";
  let lightboxOpen = false;
</script>

<div class="home-wrapper" id="home">
  <Headline image={Home} />
  <p class="description">
    ViCat is a meme coin for cat lovers and everyone who enjoys crypto. Its goal
    is getting more people to get involved in crypto and especially in the VITE
    chain. While there are lots of dog coins out there, cat people seem to come
    short too often. ViCat wants to represent the cat lovers in the VITE
    community, deliver platforms for VITE enthusiasts of several regions and
    languages and help in growing the reach for the VITE chain. Since its a meme
    coin, the most important goal is creating a fun experience for all those who
    would like to get involved!
    <br />
    <br />
    <em>
      ViCat was created by the team behind the <a href="https://vitetxs.de"
        >VITE Tools website</a
      >. The core team member are longtime crypto-enthusiasts with a
      professional background in IT and fans of the VITE chain and its
      underlying ideas.</em
    >
  </p>
  <div class="link-section">
    <h2>Trade ViCat here</h2>
    <div class="link-wrapper">
      <a
        class="xl"
        target="_blank"
        rel="noreferrer"
        href="https://x.vite.net/trade?symbol=VICAT-000_VITE">ViteX</a
      >
    </div>
  </div>
  <div class="link-section">
    <h2>Observe ViCat here</h2>
    <div class="link-wrapper">
      <a
        target="_blank"
        rel="noreferrer"
        href="https://www.livecoinwatch.com/price/ViCat-VICAT"
        >Live Coin Watch</a
      >
      <a
        target="_blank"
        rel="noreferrer"
        href="https://coinranking.com/coin/HjZas8UDm+vicat-vicat">Coinranking</a
      >
      <a
        target="_blank"
        rel="noreferrer"
        href="https://coinpaprika.com/coin/vicat-vicat/">Coinpaprika</a
      >
    </div>
  </div>
  <div class="link-section">
    <h2>Read more about the project</h2>
    <div class="link-wrapper">
      <a
        class="xl"
        target="_blank"
        rel="noreferrer"
        href="https://medium.com/@vicat_777">Medium</a
      >
    </div>
  </div>
  <div class="link-section">
    <h2>See what is coming next</h2>
    <div class="link-wrapper">
      <button class="xl" on:click={() => (lightboxOpen = true)}>Roadmap</button>
      {#if lightboxOpen}
        <Lightbox
          onClose={() => (lightboxOpen = false)}
          src={Roadmap}
          alt="Roadmap"
        />
      {/if}
    </div>
  </div>
  <div class="channel-section">
    <h2>Our Channels</h2>
    <div class="channels-wrapper">
      <a
        class="channel"
        target="_blank"
        rel="noreferrer"
        href="https://twitter.com/ViCat_777"
        ><img src={Twitter} alt="twitter" /></a
      >
      <a
        class="channel"
        target="_blank"
        rel="noreferrer"
        href="https://discord.gg/mqRuTWP4wY"
        ><img src={Discord} alt="discord" /></a
      >
      <a
        class="channel"
        target="_blank"
        rel="noreferrer"
        href="https://t.me/ViCat_777"
        ><img class="telegram" src={Telegram} alt="telegram" /></a
      >
    </div>
  </div>
  <div class="team-section">
    <h2>Meet the Team</h2>
    <div>
      <div class="link-wrapper">
        <Link to="/team"><img src={Team} alt="team" /></Link>
      </div>
    </div>
  </div>
</div>

<style lang="scss">
  .home-wrapper {
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .description {
    @include description;
    width: min(80%, 900px);

    a {
      text-decoration: none;
      color: $orange;
      font-weight: 500;
    }
  }

  .link-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin-top: 25px;
    margin-bottom: 150px;

    h2 {
      @include headline;
    }

    .link-wrapper {
      display: flex;
      justify-content: center;

      @media (max-width: $small) {
        flex-direction: column;
      }

      > a:not(a:last-child) {
        margin-right: 120px;
        @media (max-width: $small) {
          margin-right: 0;
          margin-bottom: 50px;
        }
      }

      a,
      button {
        @include center;
        @include button;

        &.xl {
          @include button-xl;
        }
      }

      a:hover {
        @include button-hover;
      }
    }
  }

  .channel-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin-top: 25px;

    h2 {
      @include headline;
    }

    .channels-wrapper {
      display: flex;
      justify-content: center;

      @media (max-width: $mid) {
        flex-direction: column;
      }

      > *:not(*:last-child) {
        margin-right: 150px;
        @media (max-width: $mid) {
          margin-right: 0;
          margin-bottom: 50px;
        }
      }

      .channel {
        @include center;
        width: 300px;
        height: 300px;
        border-radius: 40% 60% 70% 30% / 40% 50% 60% 50%;
        overflow: hidden;
        background: conic-gradient($orange, $yellow, $orange);
        animation: morph 3s linear infinite;
        transition: all 0.5s ease-out;

        @media (max-width: $tablet) {
          width: 200px;
          height: 200px;
        }

        &:hover {
          transform: scale(1.1);
          box-shadow: 0 0 20px $yellow;
        }

        &:last-child {
          animation-name: morph2;
        }

        &:first-child {
          animation-name: morph2;
        }

        img {
          width: 50%;

          &.telegram {
            width: 80%;
          }
        }
      }

      @keyframes morph {
        0%,
        100% {
          border-radius: 40% 60% 70% 30% / 40% 40% 60% 50%;
        }
        27% {
          border-radius: 70% 30% 50% 50% / 30% 30% 70% 70%;
        }
        60% {
          border-radius: 100% 60% 60% 100% / 100% 100% 60% 60%;
        }
      }

      @keyframes morph2 {
        0%,
        100% {
          border-radius: 70% 30% 50% 50% / 30% 30% 70% 70%;
        }
        34% {
          border-radius: 40% 60% 70% 30% / 40% 40% 60% 50%;
        }
        67% {
          border-radius: 100% 60% 60% 100% / 100% 100% 60% 60%;
        }
      }

      @keyframes morph3 {
        0%,
        100% {
          border-radius: 100% 60% 60% 100% / 100% 100% 60% 60%;
        }
        40% {
          border-radius: 40% 60% 70% 30% / 40% 40% 60% 50%;
        }
        77% {
          border-radius: 70% 30% 50% 50% / 30% 30% 70% 70%;
        }
      }
    }
  }

  .team-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100vw;
    margin-block: 200px 100px;

    div {
      width: min(500px, 70vw);
      height: 700px;
    }

    h2 {
      @include headline;
      margin-bottom: 130px;
    }

    .link-wrapper {
      position: absolute;
      img {
        width: min(500px, 70vw);
        transform: rotate(10deg);
        box-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff;
        transition: all 0.5s ease-out;
      }

      &:hover img {
        box-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 50px #fff,
          0 0 75px #fff, 0 0 85px #fff, 0 0 100px $yellow;
        transform: scale(1.2) rotate(5deg);
      }
    }
  }
</style>
