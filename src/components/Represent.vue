<template>
  <div class="main">
    <div class="handle-overflow">
      <section>
        <div class="item">
          <h1>More than just shorter links</h1>
          <p>
            Build your brand’s recognition and get detailed insights on how your
            links are performing.
          </p>
          <button><a href="#shortenLink">Get Started</a></button>
        </div>
        <div class="item">
          <img
            src="../assets/images/illustration-working.svg"
            alt="illustration"
          />
        </div>
      </section>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/scss/mixins.scss";

.main {
  position: relative;
}

section {
  max-width: 1200px;
  margin: 0 auto;
  @include flexBox($j: space-between);
  padding-block: 70px 150px;

  @include maxDevice(1300px) {
    padding-inline: 40px;
  }

  @include maxDevice(500px) {
    padding-inline: 24px;
    padding-top: 0;
  }

  @include maxDevice(400px) {
    padding-inline: 12px;
  }

  @include maxDevice986 {
    @include flexBox($f: column, $g: 40px);
  }

  @include maxDevice(600px) {
    flex-direction: column-reverse;
    padding-bottom: 180px;
  }
}

.handle-overflow {
  width: 100%;
  overflow-x: hidden;
}

.item {
  width: 50%;

  @include maxDevice986 {
    width: 100%;
    text-align: center;
  }

  &:first-child {
    h1 {
      font-size: 80px;
      line-height: 1.2;
      color: var(--Very-Dark-Violet);

      @include maxDevice(600px) {
        font-size: 40px;
      }

      @include maxDevice(500px) {
        font-size: 36px;
      }

      @include maxDevice(480px) {
        font-size: 32px;
      }
    }

    p {
      font-size: 22px;
      color: var(--Grayish-Violet);
      margin-top: 20px;

      @include maxDevice(500px) {
        font-size: 20px;
      }

      @include maxDevice(480px) {
        font-size: 18px;
      }
    }
  }

  &:last-child {
    position: relative;
    img {
      transform: translateX(20%);

      @include maxDevice(1048px) {
        transform: translateX(0);
      }
      @include maxDevice(600px) {
        width: 100%;
      }
    }
  }
}

button {
  padding: 16px 60px;
  font-size: 18px;
  border-radius: 100px;
  margin-top: 36px;
  background: var(--Cyan);
  color: #fff;

  &:hover {
    background-color: #9be3e2;
  }
}
</style>
