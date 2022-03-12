<template>
  <div class="container flex w-full fadeIn">
    <div class="wallet">
      <h3>Wallet</h3>

      <div class="select-wallet flex align-center">
        <div class="cube flex align-center center">
          <img src="~/assets/icons/naira.svg" alt="currency" />
        </div>
        <div class="flex flex-col center">
          <div class="flex align-center">
            <span class="type"> Naira Wallet </span>
            <img src="~/assets/icons/dropdown.svg" alt="dropdown" />
          </div>
          <p class="desc">Lorem Ipsum dolor sit amet</p>
        </div>
      </div>

      <div class="stats w-full flex">
        <div class="balance flex flex-col center">
          <span class="title"> Total Balance </span>
          <span class="amount"> ₦89,153,001.73 </span>
          <span class="booked-amount"> Book Balance: ₦450,000.093 </span>
        </div>
        <img src="~/assets/icons/graph.svg" alt="graph" />
        <div class="legends flex">
          <div class="legend">
            <span class="type"> Outflow </span>
            <span class="amount"> ₦20,000 </span>
          </div>

          <div class="legend">
            <span class="type"> Inflow </span>
            <span class="amount"> ₦20,000 </span>
          </div>
        </div>
      </div>

      <div class="cards w-full flex space-between">
        <div
          class="card w-full flex align-center"
          @mouseover="cardHover.request = true"
          @mouseleave="cardHover.request = false"
        >
          <img src="~/assets/icons/request.svg" alt="request" />
          <span> Request Money </span>
          <ArrowIcon :color="cardHover.request ? '#388379' : ''" />
        </div>
        <div
          class="card w-full flex align-center"
          @mouseover="cardHover.cardless = true"
          @mouseleave="cardHover.cardless = false"
        >
          <img src="~/assets/icons/cardless.svg" alt="cardless" />
          <span>Cardless Withdrawal</span>
          <ArrowIcon :color="cardHover.cardless ? '#388379' : ''" />
        </div>
      </div>

      <div class="table-wrapper w-full">
        <div class="head w-full flex align-center">
          <span class="title"> Recent Activity </span>
          <div class="date flex align-center">
            <img src="~/assets/icons/calendar.svg" alt="calendar" />
            <span> Start date: 01/02/21</span>
          </div>
          <button class="download">
            <img src="~/assets/icons/download.svg" alt="download" />
          </button>
        </div>
        <div class="inner">
          <table>
            <tbody>
              <tr>
                <td>
                  <div class="flex align-center">
                    <div class="cube flex align-center center">
                      <img src="~/assets/icons/naira2.svg" alt="naira" />
                    </div>

                    Self Withdrawal
                  </div>
                </td>
                <td>0.003 BTC</td>
                <td>Just now</td>
                <td class="success">Success</td>
              </tr>
              <tr>
                <td>
                  <div class="flex align-center">
                    <div class="cube flex align-center center">
                      <img src="~/assets/icons/naira2.svg" alt="naira" />
                    </div>

                    Deposit
                  </div>
                </td>
                <td>0.003 BTC</td>
                <td>Today</td>
                <td class="failed">Failed</td>
              </tr>
              <tr>
                <td>
                  <div class="flex align-center">
                    <div class="cube flex align-center center">
                      <img src="~/assets/icons/naira2.svg" alt="naira" />
                    </div>

                    Transfer
                  </div>
                </td>
                <td>0.003 BTC</td>
                <td>7:23AM</td>
                <td class="pending">Pending</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <div class="transaction flex-col">
      <div class="profile flex align-center">
        <div class="cube flex align-center center">
          <img src="~/assets/icons/notifications.svg" alt="notifications" />
        </div>
        <div class="cube flex align-center center">
          <img src="~/assets/icons/profile.svg" alt="profile" />
        </div>
        <img src="~/assets/icons/mask.svg" alt="mask" />
      </div>

      <div class="methods w-full">
        <div class="navs flex w-full">
          <div class="nav flex center align-center active">Deposit</div>
          <div class="nav flex center align-center">Transfer</div>
        </div>
        <span class="desc"> Select a method to Fund Naira wallet below </span>
        <div class="cards w-full">
          <div
            class="card w-full deposit flex align-center"
            @mouseover="cardHover.bank = true"
            @mouseleave="cardHover.bank = false"
          >
            <div class="cube flex align-center center">
              <img src="~/assets/icons/bank.svg" alt="bank deposit" />
            </div>
            <span>Bank Deposit</span>
            <ArrowIcon :color="cardHover.bank ? '#388379' : ''" />
          </div>
          <div
            class="card w-full deposit flex align-center"
            @mouseover="cardHover.ussd = true"
            @mouseleave="cardHover.ussd = false"
          >
            <div class="cube flex align-center center">
              <img src="~/assets/icons/cell.svg" alt="ussd deposit" />
            </div>
            <span>USSD Deposit</span>
            <ArrowIcon :color="cardHover.ussd ? '#388379' : ''" />
          </div>
          <div
            class="card w-full deposit flex align-center"
            @mouseover="cardHover.card = true"
            @mouseleave="cardHover.card = false"
          >
            <div class="cube flex align-center center">
              <img src="~/assets/icons/image.svg" alt="card deposit" />
            </div>
            <span>Card Deposit</span>
            <ArrowIcon :color="cardHover.card ? '#388379' : ''" />
          </div>
          <div
            class="card w-full help flex align-center"
            @mouseover="cardHover.help = true"
            @mouseleave="cardHover.help = false"
          >
            <div class="cube flex align-center center">
              <img src="~/assets/icons/education.svg" alt="learn more" />
            </div>
            <span>Learn More about Funding your wallet</span>
            <ArrowIcon :color="cardHover.help ? '#388379' : '#63BDAF'" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ArrowIcon from '~/components/icons/ArrowIcon.vue'
export default {
  name: 'WallexHome',
  components: { ArrowIcon },
  data() {
    return {
      screenWidth: 0,
      cardHover: {
        request: false,
        cardless: false,
        bank: false,
        ussd: false,
        card: false,
        help: false,
      },
    }
  },
}
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  z-index: 0;

  .wallet {
    flex: 1;
    width: 100%;
    flex-basis: 0;
    padding: 3rem calc(min(10%, 3rem)) 1.5rem calc(min(10%, 3rem));

    @media (min-width: 1400px) {
      flex: 0;
      flex-basis: 60%;
    }

    @include respond-to('min-lg') {
      padding: 1.5rem calc(min(6%, 1.5rem)) 0 calc(min(6%, 2rem));
    }

    h3 {
      font-size: $font-xlg;
      color: $text-color4;
      line-height: 42px;
      margin: 0 0 0.688rem;
      font-weight: 400;
    }

    .select-wallet {
      user-select: none;
      margin-bottom: 1.938rem;

      .cube {
        min-width: 40px;
        height: 40px;
        margin-right: 1rem;
        background-color: $text-color3;
        border-radius: 8px;
      }

      .type {
        display: block;
        font-size: 1.125rem;
        line-height: 20px;
        color: $text-color4;
        margin-right: 0.663rem;
      }

      .desc {
        font-size: $font-sm;
        line-height: 24px;
        font-weight: 700;
        color: $text-color5;
      }
    }

    .stats {
      background-color: $text-color3;
      border-radius: 24px;
      position: relative;
      padding: 1.5rem clamp(5%, 6vw, 2rem) 1.5rem clamp(5%, 6vw, 2.5rem);
      flex-direction: column;
      position: relative;

      @include respond-to('min-md') {
        align-items: center;
        flex-direction: row;
        height: 231px;
        justify-content: space-between;
        padding-left: 0;
      }

      @include respond-to('min-lg') {
        max-width: 684px;
      }

      @media (max-width: 1400px) and (min-width: 1024px) {
        flex-direction: column;
        align-items: flex-start;
        height: max-content;
        padding-left: clamp(5%, 6vw, 2.5rem);
      }

      &::before {
        content: '';
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        bottom: -7px;
        width: 97%;
        height: 60px;
        background-color: $color3;
        border-radius: 24px;
        z-index: -1;
      }

      &::after {
        content: '';
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        bottom: -14px;
        width: 93%;
        height: 60px;
        background-color: $color4;
        border-radius: 24px;
        z-index: -2;
      }

      .balance {
        height: 100%;
        margin-bottom: 1rem;
        position: relative;

        @include respond-to('min-md') {
          border-right: 1px solid #388379;
          margin-bottom: 0;
          padding-left: clamp(5%, 6vw, 2.5rem);
          padding-right: clamp(3%, 1vw, 2rem);
          margin: 0 calc(min(2%, 2rem)) 1rem 0;
        }

        @media (max-width: 1400px) and (min-width: 1024px) {
          border-right: none;
          padding-left: 0;
        }

        &::before {
          content: '';
          display: none;
          position: absolute;
          left: 0;
          z-index: 0;
          width: 100%;
          height: 130%;
          max-height: 227px;
          background: url('~/assets/icons/overlay.svg') no-repeat;
          background-position: top 48%;
          opacity: 0.3;

          @include respond-to('min-md') {
            display: block;
          }

          @media (max-width: 1400px) and (min-width: 1024px) {
            display: none;
          }
        }

        .title {
          font-weight: 700;
          font-size: $font-sm;
          line-height: 24px;
          margin-bottom: 0.5rem;
          color: $text-color9;
        }

        .amount {
          font-family: 'Montserrat';
          color: $color1;
          font-size: $font-xlg;
          line-height: 42px;
        }

        .booked-amount {
          font-weight: 700;
          font-size: $font-sm;
          line-height: 24px;
          color: $text-color10;
        }
      }

      img {
        @media (max-width: 1400px) and (min-width: 1024px) {
          width: 100%;
        }
      }

      .legends {
        gap: 0 1rem;
        justify-content: center;
        margin-top: 1rem;

        @include respond-to('min-md') {
          margin-top: 0;
          justify-content: flex-start;
          gap: 1rem 0;
          flex-direction: column;
        }

        @media (max-width: 1400px) and (min-width: 1024px) {
          justify-content: center;
          flex-direction: row;
          align-self: center;
          gap: 0 1rem;
          margin-top: 1rem;
        }

        .legend {
          .type {
            text-align: center;
            display: block;
            font-size: $font-xsm;
            line-height: 20px;
            color: $text-color9;

            @include respond-to('min-lg') {
              text-align: left;
            }

            @media (max-width: 1400px) and (min-width: 1024px) {
              text-align: center;
            }
          }

          .amount {
            text-align: center;
            font-size: $font-xsm;
            line-height: 20px;
            color: $text-color10;

            @include respond-to('min-lg') {
              text-align: left;
            }

            @media (max-width: 1400px) and (min-width: 1024px) {
              text-align: center;
            }
          }
        }
      }
    }

    .cards {
      margin: 2.5rem 0 0.938rem;
      flex-direction: column;
      gap: 1rem 0;

      @media (min-width: 640px) {
        flex-direction: row;
        gap: 0 1.5rem;
      }

      @include respond-to('min-lg') {
        max-width: 684px;
      }

      .card {
        border-radius: 24px;
        padding: 0 clamp($font-xsm, 3vw, $font-lg) 0
          clamp($font-xsm, 3vw, $font-xlg);
        cursor: pointer;
        background-color: $color1;
        border: 1px solid $color2;
        height: 98px;
        justify-content: space-between;

        @include respond-to('min-sm') {
          justify-content: flex-start;
        }

        span {
          display: block;
          max-width: 173px;
          font-size: clamp(0.625rem, 3vw, $font-sm);
          font-weight: normal;
          line-height: 24px;
          text-align: left;
          margin-left: $font-md;
        }

        &:hover {
          border: none;
          box-shadow: 0px 5px 20px rgba(151, 154, 165, 0.12);

          span {
            color: $text-color3;
          }
        }
      }
    }

    .table-wrapper {
      border: 1px solid $color2;
      border-radius: 24px;
      background-color: $color1;
      padding: 0.5rem 0.5rem $font-md;
      width: 100%;
      overflow-x: hidden;

      @include respond-to('min-lg') {
        max-width: 684px;
      }

      .head {
        padding: $font-md $font-md 1.5rem;

        .title {
          display: block;
          color: $text-color5;
          font-size: $font-sm;
          line-height: 24px;
        }

        .date {
          margin-left: auto;
          background-color: $color3;
          border-radius: 8px;
          padding: 0.125rem 0.438rem 0.125rem 0.583rem;
          cursor: pointer;

          img {
            margin-right: 0.583rem;
          }

          span {
            font-size: $font-xsm;
            line-height: 20px;
            font-weight: bolder;
            color: $text-color5;
          }
        }

        button.download {
          margin-left: 0.625rem;
          background: none;
        }
      }

      .inner {
        width: 100%;
        overflow-x: auto;
        overflow-y: hidden;

        table {
          table-layout: auto;
          width: 100%;
          border-spacing: 0px;

          @media (min-width: 640px) {
            table-layout: auto;
            border-spacing: 0px;
          }

          .cube {
            min-width: 40px;
            max-width: 40px;
            height: 40px;
            background-color: $bg-color2;
            border-radius: 8px;
            margin-right: 1.375rem;
          }

          tr {
            // min-width: 602px;
            height: 48px;
            padding: 0 $font-md;
            cursor: pointer;

            &:hover {
              box-shadow: 0px 2px 20px rgba(151, 154, 165, 0.12);
              -webkit-box-shadow: 0px 2px 20px rgba(151, 154, 165, 0.12);
              -moz-box-shadow: 0px 2px 20px rgba(151, 154, 165, 0.12);

              td:nth-child(2) {
                color: $text-color2;
              }
            }

            td {
              font-size: $font-sm;
              font-weight: bolder;
              white-space: nowrap;
              padding: 0 $font-md;

              &:nth-child(1) {
                min-width: 200px;
                color: $text-color2;
              }
              &:nth-child(2) {
                min-width: 66px;
                color: $text-color5;
              }
              &:nth-child(3) {
                min-width: 66px;
                color: $text-color5;
              }
              &:nth-child(4) {
                min-width: 55px;
                text-align: right;
              }

              &.success {
                color: $text-color6;
              }

              &.failed {
                color: $text-color7;
              }

              &.pending {
                color: $text-color8;
              }
            }
          }
        }
      }

      .table {
        overflow-y: hidden;
        overflow-x: auto;
        max-width: 100%;

        .tr {
          // min-width: 602px;
          height: 48px;
          padding: 0 $font-md;
          cursor: pointer;

          &:hover {
            box-shadow: 0px 2px 20px rgba(151, 154, 165, 0.12);

            .td:nth-child(2) {
              color: $text-color2;
            }
          }

          .cube {
            min-width: 40px;
            max-width: 40px;
            height: 40px;
            background-color: $bg-color2;
            border-radius: 8px;
            margin-right: 1.375rem;
          }

          .td {
            font-size: $font-sm;
            font-weight: bolder;

            &:nth-child(1) {
              width: 200px;
              color: $text-color2;
            }

            &:nth-child(2) {
              width: 66px;
              min-width: 0;
              color: $text-color5;
            }

            &:nth-child(3) {
              width: 66px;
              min-width: 0;
              color: $text-color5;
            }

            &:nth-child(4) {
              width: 55px;
              min-width: 0;
              text-align: right;
            }

            &.success {
              color: $text-color6;
            }

            &.failed {
              color: $text-color7;
            }

            &.pending {
              color: $text-color8;
            }
          }
        }
      }
    }
  }
}

.transaction {
  display: none;

  @include respond-to('min-lg') {
    display: flex;
    flex-basis: 40%;
    border-left: 1px solid $color2;
    padding: 1.5rem calc(min(6%, 2rem)) 0 calc(min(6%, 1.5rem));
  }

  .profile {
    background-color: $color3;
    border-radius: 8px;
    padding: $font-xsm 1rem;
    margin-left: auto;
    margin-bottom: 3.875rem;

    .cube {
      background-color: $color1;
      border-radius: 8px;
      width: $font-xlg;
      height: $font-xlg;

      &:nth-child(2) {
        margin-left: $font-md;
      }

      &:nth-child(2) {
        img {
          border-radius: 6px;
        }
      }
    }

    img {
      cursor: pointer;

      &:nth-child(3) {
        margin-left: 0.5rem;
      }
    }
  }

  .methods {
    border: 1px solid $color2;
    border-radius: 24px;
    padding-bottom: 1.75rem;

    .navs {
      margin-bottom: $font-xlg;

      .nav {
        width: 50%;
        height: 80px;
        background-color: $color2;
        font-size: 1.125rem;
        color: $text-color1;
        cursor: pointer;

        &:nth-child(1) {
          border-radius: 24px 0px 0px 0px;
        }

        &:nth-child(2) {
          border-radius: 0px 24px 0px 0px;
        }

        &.active {
          color: $text-color3;
          background-color: $color1;
          cursor: default;
        }

        &:hover {
          color: $text-color3;
          background-color: $color1;
        }
      }
    }

    .desc {
      display: block;
      font-size: 1.125rem;
      text-align: center;
      max-width: 250px;
      line-height: 30px;
      font-weight: 700;
      margin: 0 auto $font-xlg;
      color: $text-color4;
    }

    .cards {
      max-height: 392px;
      padding: 0 1.5rem 1rem;
      overflow-y: auto;

      .card {
        border-radius: 24px;
        padding: 0 clamp($font-xsm, 3vw, $font-lg) 0
          clamp($font-xsm, 3vw, $font-xlg);
        cursor: pointer;

        &.deposit {
          background-color: $color1;
          border: 1px solid $color3;
          height: 98px;
          position: relative;

          &:not(:nth-child(3)):nth-child(n + 1) {
            margin-bottom: $font-lg;
          }

          &::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            bottom: -6px;
            width: 95%;
            height: 60px;
            background-color: $color3;
            border-radius: 24px;
            z-index: -1;
          }

          &::after {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            bottom: -11px;
            width: 90%;
            height: 60px;
            background-color: $color4;
            border-radius: 24px;
            z-index: -2;
          }

          span {
            display: block;
            max-width: 173px;
            font-size: clamp(0.6rem, 1.2vw, $font-sm);
            font-weight: normal;
            line-height: 24px;
            text-align: left;
            margin-left: $font-md;
          }

          &:hover {
            span {
              color: $text-color3;
            }
          }
        }

        &.help {
          background-color: #def5f2;
          height: 80px;
          margin-top: 2.5rem;

          .cube {
            background-color: $color1;
            border-radius: 10px;
            min-width: 41px;
            height: 41px;
          }

          span {
            display: block;
            max-width: 200px;
            font-size: clamp(10%, 1.2vw, $font-sm);
            font-weight: 700;
            line-height: 24px;
            color: $text-color3;
            text-align: left;
            margin-left: $font-md;
          }
        }
      }
    }
  }
}
</style>
