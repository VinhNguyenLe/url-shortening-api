<template>
  <section class="statistic-wrap">
    <ShortenLink />
    <div class="statistic">
      <h2>Advanced Statistics</h2>
      <p>
        Track how your links are performing across the web with our advanced
        statistics dashboard.
      </p>
      <div class="statisticItems">
        <div class="statisticItem" v-for="item in statistic" :key="item.id">
          <div class="statisticLogo">
            <img :src="item.image" :alt="item.title" />
          </div>
          <h3>{{ item.title }}</h3>
          <p>{{ item.content }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ShortenLink from "./ShortenLink.vue";
import image1 from "../assets/images/icon-brand-recognition.svg";
import image2 from "../assets/images/icon-detailed-records.svg";
import image3 from "../assets/images/icon-fully-customizable.svg";
export default {
  data() {
    return {
      statistic: [
        {
          id: 1,
          title: "Brand Recognition",
          content:
            "Boost your brand recognition with each click. Generic links don’t mean a thing. Branded links help instil confidence in your content.",
          image: image1,
        },
        {
          id: 2,
          title: "Detailed Records",
          content:
            "Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.",
          image: image2,
        },
        {
          id: 3,
          title: "Fully Customizable",
          content:
            "Improve brand awareness and content discoverability through customizable links, supercharging audience engagement.",
          image: image3,
        },
      ],
    };
  },
  components: {
    ShortenLink,
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/mixins.scss";

.statistic-wrap {
  background-color: #f0f1f6;
  padding-bottom: 180px;

  @include maxDevice(1300px) {
    padding-inline: 40px;
  }

  @include maxDevice(500px) {
    padding-inline: 24px;
  }

  @include maxDevice(400px) {
    padding-inline: 12px;
  }
}

.statistic {
  max-width: 1200px;
  margin: 0 auto;

  & > h2 {
    text-align: center;
    font-size: 36px;
    color: var(--Very-Dark-Violet);
  }

  & > p {
    text-align: center;
    max-width: 500px;
    color: var(--Grayish-Violet);
    margin: 20px auto;
  }
}

.statisticItems {
  @include flexBox($g: 32px);
  position: relative;

  @include maxDevice(928px) {
    flex-direction: column;
    margin-top: 80px;
  }

  &::before {
    content: "";
    position: absolute;
    width: 100%;
    top: calc(50% + 50px);
    height: 10px;
    background: var(--Cyan);
    z-index: 1;

    @include maxDevice(928px) {
      width: 8px;
      height: 100%;
      top: 50px;
    }
  }
}

.statisticItem {
  background: #fff;
  border-radius: 10px;
  padding: 0px 32px 40px;
  margin-top: 100px;
  z-index: 2;

  @include maxDevice(928px) {
    margin-top: 32px;
  }

  @include maxDevice(600px) {
    text-align: center;
    @include flexBox($f: column);
  }
  & h3 {
    color: var(--Dark-Violet);
  }

  & p {
    color: var(--Grayish-Violet);
    margin-top: 12px;
    @include handleOverflowText(4);
  }

  &:nth-child(2) {
    transform: translateY(40px);
  }
  &:nth-child(3) {
    transform: translateY(80px);
  }
}

.statisticLogo {
  @include circle($w: 88px, $bg: var(--Dark-Violet));
  @include flexBox($j: center);
  transform: translateY(-50%);
}
</style>
