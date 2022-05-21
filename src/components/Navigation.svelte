<script lang="ts">
  import logo from "../assets/images/vicat.png";
  import { Link } from "svelte-navigator";
  import { Icon, ExternalLink } from "svelte-hero-icons";

  const navItems = [
    { title: "Home", href: "/#home", newTab: false },
    { title: "Team", href: "/team#team", newTab: false },
    { title: "FAQ", href: "/faq", newTab: false },
    { title: "PreSale", href: "/presale", newTab: false },
    { title: "NFT", href: "/nft", newTab: false },
    { title: "Faucet", href: "https://faucet.vicat.tech", newTab: true },
    {
      title: "Whitepaper",
      href: "https://vicat.tech/whitepaper_v1.pdf",
      newTab: true,
    },
  ];

  let loaded = false;
  let open = false;
  setTimeout(() => (loaded = true), 100);
</script>

<nav class="navigation">
  <Link to="/">
    <img src={logo} alt="vicat coin" class={loaded ? "loaded" : ""} />
  </Link>
  <ul class={open ? "open" : ""}>
    {#each navItems as item}
      <li>
        {#if item.newTab}
          <a
            href={item.href}
            target="_blank"
            title="open in new tab"
            rel="noreferrer"
          >
            {item.title}
            <Icon src={ExternalLink} size="15px" />
          </a>
        {:else}
          <div on:click={() => (open = false)}>
            <Link to={item.href}>
              {item.title}
            </Link>
          </div>
        {/if}
      </li>
    {/each}
  </ul>
  <div
    class={`navigation-button hover-cursor ${open ? "open" : ""}`}
    on:click={() => (open = !open)}
  >
    <div class="navigation-burger" />
  </div>
</nav>

<style lang="scss" global>
  @use "../variables.scss";

  @mixin nav-ul {
    list-style: none;
    display: flex;
    align-items: center;
    height: 100%;
  }

  nav {
    position: fixed;
    top: 0;
    left: 0;
    height: 70px;
    width: calc(100% - 50px);
    background: $green-1;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-inline: 25px;
    box-shadow: 0 -3px 10px $orange;

    @media (max-width: $tablet) {
      height: 60px;
    }

    img {
      height: 60px;
      width: 60px;
      transform: translateX(-150%) rotate(-540deg);
      transition: all 2s ease-out;

      &.loaded {
        transform: translateX(0) rotate(0);
      }

      @media (max-width: $tablet) {
        height: 50px;
        width: 50px;
      }
    }

    ul {
      @include nav-ul;
      overflow: scroll;

      *:not(svg) {
        @include nav-ul;

        @media (max-width: $tablet) {
          max-height: 80px;
          min-height: 65px;
          width: 100%;
          justify-content: center;
          font-size: 1.5rem;
        }
      }

      @media (max-width: $tablet) {
        @include center;
        flex-direction: column;
        position: absolute;
        inset: 0;
        top: 40px;
        width: 100%;
        height: calc(100vh - 100px);
        padding: 0 0 100px;
        z-index: 10;
        background: $green-1;
        transform: translateX(100%);
        transform-origin: top right;
        transition: all 0.5s ease-in-out;

        &.open {
          transform: translateX(0);
        }
      }

      a {
        text-decoration: none;
        color: white;
        padding-inline: 25px;
        transition: all 0.2s ease-in-out;

        &:hover {
          background: $green-3;
        }

        @media (max-width: $small) {
          padding-inline: 15px;
        }

        svg {
          margin-left: 5px;

          @media (max-width: $tablet) {
            margin-left: 10px;
            margin-top: 3px;
            width: 20px;
            height: 50px;
          }
        }
      }
    }
  }

  .navigation-button {
    position: relative;
    display: none;
    justify-content: center;
    align-items: center;
    width: 70px;
    height: 40px;
    transition: all 0.5s ease-in-out;

    @media (max-width: $tablet) {
      display: flex;
    }

    .navigation-burger {
      width: 40px;
      height: 4px;
      background: white;
      border-radius: 5px;
      transition: all 0.3s ease-in-out;

      &::before,
      &::after {
        content: "";
        position: absolute;
        width: 40px;
        height: 4px;
        background: white;
        border-radius: 3px;
        transition: all 0.3s ease-in-out;
      }

      &::before {
        transform: translateY(-12px);
      }

      &::after {
        transform: translateY(12px);
      }
    }

    &.open {
      .navigation-burger {
        background: transparent;
        box-shadow: none;

        &::before {
          transform: rotate(45deg);
        }

        &::after {
          transform: rotate(-45deg);
        }
      }
    }
  }
</style>
