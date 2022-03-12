<template>
  <header>
    <nav class="flex flex-col w-full" :class="{ open: menuOpen }">
      <div class="container flex align-center space-between">
        <img src="~/assets/icons/logo.svg" alt="logo" />

        <div class="flex align-center" @click="handleMenu()">
          <div class="menu">
            <div class="pencet" :class="{ close: menuOpen }">
              <span></span>
              <span></span>
              <span></span>
            </div>
          </div>
        </div>
      </div>

      <div class="links flex flex-col w-full h-full">
        <nuxt-link to="#" class="flex">
          <div class="flex align-center">
            <DashboardIcon />
            <span>Dashboard</span>
          </div>
        </nuxt-link>
        <nuxt-link to="#" class="flex">
          <div class="flex align-center">
            <ActivityIcon />
            <span>Activity</span>
          </div>
        </nuxt-link>
        <nuxt-link to="#" class="active flex">
          <div class="flex align-center">
            <WalletIcon />
            <span> Wallet</span>
          </div>
        </nuxt-link>
        <nuxt-link to="#" class="flex">
          <div class="flex align-center">
            <ProductIcon />
            <span>Products</span>
          </div>
        </nuxt-link>
        <nuxt-link to="#" class="flex">
          <div class="flex align-center">
            <ReferralIcon />

            <span>Referrals</span>
          </div>
        </nuxt-link>
        <nuxt-link to="#" class="flex">
          <div class="flex align-center">
            <HelpIcon />
            <span>Help Center</span>
          </div>
        </nuxt-link>
      </div>
    </nav>
  </header>
</template>

<script>
import DashboardIcon from './icons/DashboardIcon.vue'
import ActivityIcon from './icons/ActivityIcon.vue'
import WalletIcon from './icons/WalletIcon.vue'
import ProductIcon from './icons/ProductIcon.vue'
import ReferralIcon from './icons/ReferralIcon.vue'
import HelpIcon from './icons/HelpIcon.vue'

export default {
  name: 'MobileHeader',
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
      screenWidth: 0,
      menuOpen: false,
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.handleResize()
    })

    window.addEventListener('resize', this.handleResize)
  },
  methods: {
    handleResize() {
      this.screenWidth = Math.max(
        document.documentElement.clientWidth,
        window.innerWidth || 0
      )

      if (this.screenWidth < 1024) {
        this.menuOpen = false
      }
    },
    handleMenu() {
      this.menuOpen = !this.menuOpen
    },
  },
}
</script>

<style lang="scss" scoped>
header {
  @include respond-to('min-lg') { 
    display: none;
  } 

  nav {

    &:not(.open) {
      .links {
        display: none;
      }
    }

    &.open {
      position: absolute;
      top: 0;
      width: 100vw;
      height: 100vh;
      z-index: 100;
      background-color: $color1;

      .links {
        padding-right: calc(min(4%, 1.5rem));
        margin-top: 2rem;

        a {
          max-width: 192px;
          font-size: clamp($font-xsm, 5vw, $font-md);
          color: $text-color1;
          line-height: 24px;
          height: 48px;
          padding-left: calc(min(10%, 3rem));
          text-decoration: none;
          margin-bottom: 0.21rem;

          &.active {
            color: $text-color3;
            background-color: $bg-color1;
            border-radius: 0px 10px 10px 0px;
          }

          div {
            min-width: 122px;
            span {
              margin-left: 1.25rem;
            }
          }

          &:last-child {
            margin: auto 0 1rem;
          }
        }
      }
    }

    .container {
      padding: 3rem calc(min(10%, 3rem)) 1.5rem calc(min(10%, 3rem));

      .menu {
        .pencet {
          display: flex;
          align-items: center;
          flex-direction: column;
          cursor: pointer;

          span {
            background-color: #000;
            width: 2rem;
            height: 0.2rem;
            min-height: 0.2rem;
            max-height: 0.2rem;
            margin: 0.26em 0;
            display: block;
            border-radius: 5px;
            transition: all 300ms ease;
            transform-origin: 0 0;
          }

          &.close {
            width: 1rem;

            span {
              background-color: #000;
              height: 0.2rem;
              min-height: 0.2rem;
              max-height: 0.2rem;

              &:nth-child(1) {
                transform: rotate(43deg) translate(1.5px, -0.2px);
              }

              &:nth-child(2) {
                transform: scaleX(0);
              }

              &:nth-child(3) {
                transform: rotate(-45deg) translate(-0.5px, 0.5px);
              }
            }
          }
        }
      }
    }
  }
}
</style>
