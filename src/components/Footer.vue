<template>
  <footer>
    <div class="footer-wrap">
      <div class="footer-logo"><a href="#shortenLink">ShortLy</a></div>
      <div class="footer-column">
        <h3>Features</h3>
        <p>Link Shortening</p>
        <p>Branded Links</p>
        <p>Analytics</p>
      </div>
      <div class="footer-column">
        <h3>Resources</h3>
        <p>Blog</p>
        <p>Developers</p>
        <p>Support</p>
      </div>
      <div class="footer-column">
        <h3>Company</h3>
        <p>About</p>
        <p>Our Team</p>
        <p>Careers</p>
        <p>Contact</p>
      </div>
      <div class="footer-socials">
        <img src="../assets/images/icon-facebook.svg" alt="Facebook" />
        <img src="../assets/images/icon-twitter.svg" alt="twitter" />
        <img src="../assets/images/icon-pinterest.svg" alt="pinterest" />
        <img src="../assets/images/icon-instagram.svg" alt="instagram" />
      </div>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
@import "../assets/scss/mixins.scss";

footer {
  color: #fff;
  background: var(--Very-Dark-Violet);
}

.footer-wrap {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  display: grid;
  gap: 5%;
  grid-template-columns: 29% 12% 12% 12% 15%;
  padding-block: 80px;

  @include maxDevice(1300px) {
    padding-inline: 40px;
  }

  @include maxDevice(920px) {
    grid-template-columns: 20% 13% 13% 13% 21%;
  }

  @include maxDevice(790px) {
    grid-template-columns: 28% 19% 19% 19%;
  }

  @include maxDevice(728px) {
    @include flexBox($f: column, $g: 40px);
    text-align: center;
    padding-block: 40px;
  }
}

.footer-logo {
  font-size: 32px;
  font-weight: 700;
  cursor: pointer;

  &:hover {
    color: var(--Cyan);
  }
}

.footer-socials {
  @include flexBox($j: space-between, $a: flex-start);

  & img {
    cursor: pointer;
  }

  @include maxDevice(728px) {
    min-width: 180px;
  }
}

.footer-column {
  & h3 {
    margin-bottom: 32px;

    @include maxDevice(728px) {
      margin-bottom: 18px;
    }
  }
  & p {
    margin-bottom: 20px;
    cursor: pointer;
    color: var(--Gray);

    &:hover {
      color: var(--Cyan);
    }
  }
}
</style>
