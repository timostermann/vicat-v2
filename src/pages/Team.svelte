<script>
  import Moe from "../assets/images/cats/moe.png";
  import Pascal from "../assets/images/cats/pascal.png";
  import Tim from "../assets/images/cats/tim.png";
  import Kvitka from "../assets/images/cats/kvitka.png";
  import Petr from "../assets/images/cats/petr.png";
  import Mage from "../assets/images/cats/mage.png";
  import Warmac from "../assets/images/cats/warmac.png";
  import Hack from "../assets/images/cats/hack.png";
  import Gujj from "../assets/images/cats/gujj.png";
  import Rakesh from "../assets/images/cats/rakesh.png";
  import Elena from "../assets/images/cats/elena.png";
  import Doodle from "../assets/images/cats/doodle.png";
  import Team from "../assets/images/headings/team.png";
  import Saos from "saos";
  import Headline from "../components/Headline.svelte";

  const teamMembers = {
    core: [
      {
        name: "Moe",
        role: "Lead Blockchain Developer",
        img: Moe,
      },
      {
        name: "Pascal",
        role: "Admin \nLead Backend Developer",
        img: Pascal,
      },
      {
        name: "Tim",
        role: "Lead Frontend Developer",
        img: Tim,
      },
    ],
    extended: [
      {
        name: "Kvitka",
        role: "Lead Designer",
        img: Kvitka,
      },
      {
        name: "Petr",
        role: "Community Manager - Russian",
        img: Petr,
      },
      {
        name: "Mage",
        role: "Community Manager - English",
        img: Mage,
      },
      {
        name: "Hackschnitzel",
        role: "Community Manager - German",
        img: Hack,
      },
      {
        name: "WarMac",
        role: "Community Manager - Hindi",
        img: Warmac,
      },
      {
        name: "Gujjucryptoguy",
        role: "Community Manager - Hindi",
        img: Gujj,
      },
      {
        name: "Rakesh",
        role: "Community Manager - Hindi",
        img: Rakesh,
      },
      {
        name: "Rыs'ka",
        role: "Advisor",
        img: Elena,
      },
      {
        name: "DoodleCat",
        role: "Advisor",
        img: Doodle,
      },
    ],
  };
</script>

<div class="team-wrapper" id="team">
  <Headline image={Team} />
  <p class="description">
    The ViCat team consists of many different people from different countries.
    Religion or origin does not matter to us, our focus is on a good harmony and
    having fun together. Under the names you can see the respective role of the
    team member, so you always know who to contact in case of a concern. If you
    don't know who is the right contact person for your topic, just choose the
    cat you like the most. Each of us will be happy to help you.
    <br />
    <br />
    <em
      >You want to become a team member and are up to the challenge? You want to
      become a moderator of your own country-specific community at ViCat?
      Contact the Core Team, we are looking forward to you!</em
    >
  </p>
  <div class="team-section">
    <h2>Core Team</h2>
    <div class="member-wrapper">
      {#each teamMembers.core as member}
        <div class="member">
          <Saos animation={"scale-in-center .5s ease-out"}>
            <div class="image-wrapper">
              <img src={member.img} alt={member.name} />
            </div>
          </Saos>
          <p class="name">{member.name}</p>
          <p class="role">
            {#each member.role.split("\n") as role}
              <span>{role}</span>
            {/each}
          </p>
        </div>
      {/each}
    </div>
  </div>
  <div class="team-section">
    <h2>Extended Team</h2>
    <div class="member-wrapper">
      {#each teamMembers.extended as member}
        <div class="member">
          <Saos animation={"scale-in-center .5s ease-out"}>
            <div class="image-wrapper">
              <img src={member.img} alt={member.name} />
            </div>
          </Saos>
          <p class="name">{member.name}</p>
          <p class="role">
            {#each member.role.split("\n") as role}
              <span>{role}</span>
            {/each}
          </p>
        </div>
      {/each}
    </div>
  </div>
</div>

<style lang="scss">
  @use "../variables.scss";

  .team-wrapper {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .description {
    @include description;
    width: min(80%, 750px);
  }

  .team-section {
    width: 100%;
    max-width: $large;
    box-sizing: border-box;
    margin: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-inline: min(40px, 2vw);

    h2 {
      @include headline;

      @media (max-width: $tablet) {
        width: 100%;
        text-align: center;
      }
    }

    .member-wrapper {
      display: flex;
      flex-wrap: wrap;
      margin-inline: -40px;
      justify-content: center;

      .member {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 20px 40px;
        width: 220px;

        .image-wrapper {
          @include center;
          border-radius: 50%;
          height: 200px;
          width: 200px;
          background: linear-gradient(-45deg, $yellow 0%, $orange 60%);

          img {
            max-width: 60%;
          }
        }

        .name {
          font-size: 1.25rem;
          font-weight: 500;
          color: $orange;
          margin-bottom: 0;
        }

        .role {
          font-size: 0.75rem;
          font-weight: 300;
          letter-spacing: 0.08rem;
          display: flex;
          align-items: center;
          flex-direction: column;

          span {
            margin-bottom: 5px;
          }
        }
      }
    }
  }

  @keyframes -global-scale-in-center {
    0% {
      transform: scale(0.2);
      opacity: 1;
    }
    100% {
      transform: scale(1);
      opacity: 1;
    }
  }
</style>
