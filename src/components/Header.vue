<template>
  <header>
    <div class="item">
      <img :src="images.logo" alt="" class="logo" />
    </div>
    <div :class="isNavOpen ? 'item active' : 'item'">
      <div class="menu">
        <p>Features</p>
        <p>Pricing</p>
        <p>Resources</p>
      </div>
      <div class="menu">
        <p>Login</p>
        <button class="button">Sign Up</button>
      </div>
    </div>
    <div class="openNav">
      <img
        src="../assets/images/icons8-menu.svg"
        alt="hambuger"
        @click="toggleNav"
      />
    </div>
  </header>
</template>

<script>
import logo from "../assets/images/logo.svg";

export default {
  name: "Header",
  data() {
    return {
      images: {
        logo: logo,
      },
      isNavOpen: false,
    };
  },
  methods: {
    toggleNav() {
      this.isNavOpen = !this.isNavOpen;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/mixins.scss";

header {
  max-width: 1200px;
  margin: 0 auto;
  padding-block: 50px;
  @include flexBox($j: space-between, $g: 32px);
  position: relative;
  overflow: hidden;

  @include maxDevice(1300px) {
    padding-inline: 40px;
  }

  @include maxDevice(500px) {
    padding-inline: 24px;
  }

  @include maxDevice(400px) {
    padding-inline: 12px;
  }

  & p {
    font-weight: 700;
    color: var(--Grayish-Violet);

    &:hover {
      color: var(--Very-Dark-Blue);
      cursor: pointer;
    }
  }
}
.item {
  @include flexBox($g: 32px);

  &:nth-child(2) {
    flex: 1;
    @include flexBox($j: space-between);

    @include maxDevice(730px) {
      opacity: 0;
      transform: translateX(100%);
      position: fixed;
      background: var(--Dark-Violet);
      border-radius: 12px;
      @include flexBox($f: column);
      z-index: 10;
      top: 139px;
      left: 40px;
      right: 40px;
      padding-block: 40px;
      transition: all 0.5s ease;

      &.active {
        opacity: 1;
        transform: translateX(0);
      }

      & p {
        color: #fff;
      }

      & .menu:last-child {
        border-color: transparent;
        border-top: 1px solid var(--Gray);
        width: 50%;

        & p {
          padding-top: 32px;
        }

        & button {
          width: 100%;
        }
      }
    }
  }

  &:nth-child(2) button {
    padding: 10px 22px;
    background: var(--Cyan);
    border-radius: 100px;
    color: #fff;
    font-weight: 700;

    &:hover {
      background-color: #9be3e2;
    }
  }
}
.menu {
  @include flexBox($g: 32px);
  width: 100%;

  @include maxDevice(730px) {
    @include flexBox($f: column);
  }

  &:nth-child(2) {
    justify-content: flex-end;
  }
}

.openNav {
  display: none;

  @include maxDevice(730px) {
    display: block;
  }
}
</style>
