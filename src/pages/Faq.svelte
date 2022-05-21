<script lang="ts">
  import { t, dictionary, locale } from "svelte-i18n";
  import * as english from "../locales/en.json";
  import * as german from "../locales/de.json";
  import FaqItem from "../components/FaqItem.svelte";
  import snarkdown from "snarkdown";
  import ClickOutside from "svelte-click-outside";
  import { Icon, ChevronDown } from "svelte-hero-icons";
  import Faq from "../assets/images/headings/faq.png";
  import Headline from "../components/Headline.svelte";

  dictionary.set({
    en: english,
    de: german,
  });

  locale.set("en");
  const languages = ["en", "de"];
  let language = "EN";
  let dropdownVisible = false;

  function setLanguage(lang: string) {
    language = lang.toUpperCase();
    locale.set(lang);
  }

  function toggleDropdown() {
    dropdownVisible = !dropdownVisible;
  }
</script>

<Headline image={Faq} />
<div class="faq" id="faq">
  <div class="headline">
    <div />
    <ClickOutside on:clickoutside={() => (dropdownVisible = false)}>
      <div
        class="dropdown hover-cursor"
        style="--dropdownDisplay: {dropdownVisible ? 'flex' : 'none'}; 
        --borderRadiusDropdown: {dropdownVisible ? '5px 5px 0 0' : '5px'}; 
        --borderBottomDropdown: {dropdownVisible
          ? '1px solid transparent'
          : '1px solid #c9c9c9'};"
      >
        <div on:click={() => toggleDropdown()}>
          <span />
          <p>{language}</p>
          <Icon src={ChevronDown} size="20px" />
        </div>
        <ul>
          {#each languages as lang}
            <li
              on:click={() => {
                dropdownVisible = false;
                setLanguage(lang);
              }}
            >
              {lang.toUpperCase()}
            </li>
          {/each}
        </ul>
      </div>
    </ClickOutside>
  </div>
  <div class="faq-items">
    {#each Array($t("faq").length) as _, i}
      <FaqItem question={$t(`faq.${i}.question`)}>
        {@html snarkdown($t(`faq.${i}.answer`))}
      </FaqItem>
    {/each}
  </div>
</div>

<style lang="scss" global>
  @use "../variables.scss";

  .faq {
    width: 100%;
    margin-top: 50px;
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  .faq-items {
    padding: 0 50px 100px;
    max-width: 1000px;
  }

  .faq-items a {
    text-decoration: none;
    color: $orange;
    font-weight: 600;
    letter-spacing: 0.05rem;
  }

  h2 {
    font-size: 2.5rem;
  }

  .headline {
    width: calc(100% - 100px);
    margin: 60px 0 75px;
    display: none;
    justify-content: space-between;
    align-items: center;
  }

  .dropdown {
    position: relative;
    z-index: 3;
  }

  .dropdown,
  .dropdown * {
    z-index: 5;
  }

  .dropdown div {
    width: 60px;
    height: 40px;
    padding-right: 15px;
    background: #08140b;
    border-radius: 5px;
    border: 1px solid #c9c9c9;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .dropdown ul {
    position: absolute;
    top: 100%;
    width: 75px;
    margin: 0;
    padding: 0;
    display: none;
    flex-direction: column;
    border: 1px solid #c9c9c9;
    border-top: none;
  }

  .dropdown li {
    list-style: none;
    height: 40px;
    background: #08140b;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .dropdown li:hover,
  .dropdown li:active {
    background: #000;
  }

  .dropdown:hover ul {
    display: flex;
  }

  .dropdown:hover div {
    border-radius: 5px 5px 0 0;
    border-bottom: 1px solid transparent;
  }

  @media (max-width: 650px) {
    .faq-items {
      padding-inline: 20px;
    }
  }

  @media (hover: none), (hover: on-demand) {
    .dropdown ul {
      display: var(--dropdownDisplay) !important;
    }

    .dropdown div {
      border-radius: var(--borderRadiusDropdown) !important;
      border-bottom: var(--borderBottomDropdown) !important;
    }
  }
</style>
