<template>
  <div>
    <div align="center" class="info-card">
      <div class="info-card-header">
        <img :src="$themeConfig.personalPhoto" :alt="$themeConfig.fullName" class="info-card-img" />
        <h1>{{ $themeConfig.fullName }}</h1>
      </div>
      <p>{{ $themeConfig.bio }}</p>
      <hr />
      <ul class="contact" v-if="contact">
        <li class="contact-item" v-for="item in contact">
          <NavLink :link="item.link">
            <component :is="item.iconComponent"></component>
            {{ item.text }}
          </NavLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import {
  GithubIcon,
  FacebookIcon,
  TwitterIcon,
  InstagramIcon,
  LinkedinIcon
} from "vue-feather-icons";

export default {
  components: {
    GithubIcon,
    FacebookIcon,
    TwitterIcon,
    InstagramIcon,
    LinkedinIcon
  },

  methods: {
    getIconComponentName(contactType) {
      switch (contactType) {
        case "github":
          return "GithubIcon";
        case "facebook":
          return "FacebookIcon";
        case "twitter":
          return "TwitterIcon";
        case "instagram":
          return "InstagramIcon";
        case "linkedin":
          return "LinkedinIcon";
        case "feed":
          return "RssIcon";          
        default:
          return "";
      }
    }
  },

  computed: {
    contact() {
      return (
        (this.$themeConfig.footer && this.$themeConfig.footer.contact) ||
        []
      )
        .map(({ type, link }) => {
          return {
            iconComponent: this.getIconComponentName(type),
            link
          };
        })
        .filter(({ iconComponent }) => iconComponent);
    },

    copyright() {
      return (
        (this.$themeConfig.footer && this.$themeConfig.footer.copyright) || []
      );
    }
  }
};
</script>

<style scoped lang="stylus">
.info-card {
  box-shadow: 0 0 50px rgba(0, 0, 0, 0.2);
  border-radius: 50px;
  max-width: 450px;
  margin-right: auto;
  margin-left: auto;
  overflow: hidden;
  transition: all 0.4s ease;

  .info-card-img {
    transition: all 0.4s ease;
    width 200px;
  }

  .info-card-header {
    background: linear-gradient(to right, #355c7d, #6c5b7b, #c06c84);
    padding-top: 50px;
  }

  h1 {
    margin-top: 0;
    margin-bottom: 0;
    color: white;
    text-transform: uppercase;
  }

  p {
    padding: 20px 40px 0px 40px;
  }

  .contact {
    display: flex;
    list-style: none;
    justify-content: center;

    .contact-item {
      margin: 0 5px;
    }
  }
}
</style>