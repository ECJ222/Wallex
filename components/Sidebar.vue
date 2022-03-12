<template>
  <aside class="sidebar h-full">
    <div class="head w-full">
      <nuxt-link to="/"
        ><img src="~/assets/icons/logo.svg" alt="logo"
      /></nuxt-link>
    </div>
    <div class="links flex flex-col w-full h-full">
      <nuxt-link
        to="#"
        class="flex"
        @mouseover.native="linkHover.dashboard = true"
        @mouseleave.native="linkHover.dashboard = false"
      >
        <div class="flex align-center">
          <DashboardIcon :active="linkHover.dashboard" />
          <span class="fadeInLeft">Dashboard</span>
        </div>
      </nuxt-link>
      <nuxt-link
        to="#"
        class="flex"
        @mouseover.native="linkHover.activity = true"
        @mouseleave.native="linkHover.activity = false"
      >
        <div class="flex align-center">
          <ActivityIcon :active="linkHover.activity" />
          <span class="fadeInLeft">Activity</span>
        </div>
      </nuxt-link>
      <nuxt-link to="#" class="active flex">
        <div class="flex align-center">
          <WalletIcon />
          <span class="fadeInLeft"> Wallet</span>
        </div>
      </nuxt-link>
      <nuxt-link
        to="#"
        class="flex"
        @mouseover.native="linkHover.product = true"
        @mouseleave.native="linkHover.product = false"
      >
        <div class="flex align-center">
          <ProductIcon :active="linkHover.product" />
          <span class="fadeInLeft">Products</span>
        </div>
      </nuxt-link>
      <nuxt-link
        to="#"
        class="flex"
        @mouseover.native="linkHover.referral = true"
        @mouseleave.native="linkHover.referral = false"
      >
        <div class="flex align-center">
          <ReferralIcon :active="linkHover.referral" />

          <span class="fadeInLeft">Referrals</span>
        </div>
      </nuxt-link>
      <nuxt-link
        to="#"
        class="flex"
        @mouseover.native="linkHover.help = true"
        @mouseleave.native="linkHover.help = false"
      >
        <div class="flex align-center">
          <HelpIcon :active="linkHover.help" />
          <span class="fadeInLeft">Help Center</span>
        </div>
      </nuxt-link>
    </div>
  </aside>
</template>

<script>
import DashboardIcon from './icons/DashboardIcon.vue'
import ActivityIcon from './icons/ActivityIcon.vue'
import WalletIcon from './icons/WalletIcon.vue'
import ProductIcon from './icons/ProductIcon.vue'
import ReferralIcon from './icons/ReferralIcon.vue'
import HelpIcon from './icons/HelpIcon.vue'

export default {
  name: 'Sidebar',
  components: {
    DashboardIcon,
    ActivityIcon,
    WalletIcon,
    ProductIcon,
    ReferralIcon,
    HelpIcon,
  },
  data() {
    return {
      linkHover: {
        dashboard: false,
        activity: false,
        product: false,
        referral: false,
        help: false,
      },
    }
  },
  computed: {
    menuOpen() {
      return this.$store.state.menuOpen
    },
  },
}
</script>

<style lang="scss" scoped>
.sidebar {
  display: none;

  @include respond-to('min-lg') {
    display: flex;
    flex-direction: column;
    flex-basis: 40%;
    max-width: 220px;
    background-color: $color1;
    border-right: 1px solid $color2;
  }

  .head {
    padding: 1.9rem 3.5rem $font-lg 3.063rem;
  }

  .links {
    padding-right: calc(min(4%, $font-lg));
    margin-top: 5.8vh;

    a {
      max-width: 192px;
      font-size: $font-sm;
      color: $text-color1;
      line-height: 24px;
      height: 48px;
      padding-left: 3.063rem;
      text-decoration: none;
      margin-bottom: 0.21rem;

      &:hover {
        color: $text-color3;
        background-color: $bg-color1;
        border-radius: 0px 10px 10px 0px;
      }

      &.active {
        color: $text-color3;
        background-color: $bg-color1;
        border-radius: 0px 10px 10px 0px;
        cursor: default;
      }

      div {
        min-width: 122px;

        span {
          margin-left: 1.25rem;
        }
      }

      &:last-child {
        margin: auto 0 0;
      }
    }
  }
}
</style>
