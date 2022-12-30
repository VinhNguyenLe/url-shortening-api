<template>
  <section class="boost">
    <h2>Boost your links today</h2>
    <button><a href="#shortenLink">Get Started</a></button>
  </section>
</template>

<style lang="scss" scoped>
@import "../assets/scss/mixins.scss";

.boost {
  height: 250px;
  width: 100%;
  @include flexBox($f: column, $j: center, $g: 20px);
  background-color: var(--Dark-Violet);
  background-image: url("../assets/images/bg-boost-desktop.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;

  & h2 {
    color: #fff;
    font-size: 40px;

    @include maxDevice(500px) {
      font-size: 32px;
    }

    @include maxDevice(480px) {
      font-size: 24px;
    }
  }

  & button {
    padding: 16px 60px;
    font-size: 18px;
    border-radius: 100px;
    background: var(--Cyan);
    color: #fff;
    font-weight: 700;

    &:hover {
      background-color: #9be3e2;
    }
  }
}
</style>
