<template>
  <section class="shortenLink" id="shortenLink">
    <input
      type="text"
      v-model="url"
      placeholder="Shorten a link here..."
      @focus="handleFocus"
      ref="input"
      :class="{ error: errorText.length > 0 }"
    />
    <button @click="handleShortenLink">Shorten it!</button>
    <span v-if="errorText.length > 0">{{ errorText }}</span>
  </section>
  <section class="displayLink">
    <div class="displayItem" v-for="item in shortenList" :key="item.id">
      <div class="url">{{ item.url }}</div>
      <div class="link">
        <a :href="item.shortedLink" target="_blank">{{ item.shortedLink }}</a>
        <button
          @click="copyURL(item.id, item.shortedLink)"
          :disabled="item.isCopy && 'true'"
        >
          {{ item.isCopy ? "Copied!" : "Copy" }}
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      url: "",
      shortenList: [],
      errorText: "",
    };
  },
  methods: {
    async handleShortenLink() {
      const getShort = await fetch(
        `https://api.shrtco.de/v2/shorten?url=${this.url}`
      ).then((res) => res.json());
      if (this.url === "") {
        this.errorText = "Please enter a link!";
        return;
      }

      if (getShort.ok === true) {
        this.shortenList.push({
          id: getShort.result.code,
          url: this.url,
          shortedLink: getShort.result.short_link,
          isCopy: false,
        });
        this.errorText = "";
      } else {
        this.errorText = "Please enter a valid URL!";
      }
    },

    handleFocus() {
      this.errorText = "";
    },
    async copyURL(id, link) {
      try {
        await navigator.clipboard.writeText(link);
        this.shortenList.forEach((item) => {
          if (item.id === id) {
            item.isCopy = true;
          }
        });
      } catch {
        alert("Failed to copy URL!");
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/mixins.scss";

.shortenLink {
  padding: 60px;
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  background-color: var(--Dark-Violet);
  background-image: url("../assets/images/bg-shorten-desktop.svg");
  background-repeat: no-repeat;
  background-size: cover;
  border-radius: 12px;
  transform: translateY(-50%);
  @include flexBox($g: 20px);
  position: relative;

  @include maxDevice(790px) {
    padding: 40px;
  }

  @include maxDevice(620px) {
    flex-direction: column;
  }

  @include maxDevice(500px) {
    padding: 24px;
  }

  & span {
    position: absolute;
    color: var(--Red);
    font-style: italic;
    transform: translateY(54px);
  }

  & button {
    padding: 20px 36px;
    font-size: 18px;
    border-radius: 10px;
    color: #fff;
    background-color: var(--Cyan);

    &:hover {
      background-color: #9be3e2;
    }

    @include maxDevice(620px) {
      width: 100%;
      font-weight: 700;
      font-size: 18px;
    }
  }
}

input {
  padding: 17px 19px;
  font-size: 18px;
  border-radius: 10px;
  flex: 1;
  border: 3px solid transparent;

  @include maxDevice(620px) {
    width: 100%;
  }

  &::placeholder {
    color: var(--Grayish-Violet);
  }
}

.error {
  border-color: var(--Red);
  color: var(--Red);

  &::placeholder {
    color: var(--Red);
  }
}

.displayLink {
  @include flexBox($g: 16px, $f: column);
}

.displayItem {
  transform: translateY(-70%);
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  @include flexBox($j: space-between, $g: 32px);
  background: #fff;
  padding: 20px 36px;
  font-size: 18px;
  border-radius: 8px;

  @include maxDevice(660px) {
    flex-direction: column;
    gap: 12px;
    margin-top: 24px;

    & .link {
      width: 100%;
      justify-content: space-between;
    }
  }

  & button {
    padding: 8px 30px;
    border-radius: 8px;
    color: #fff;
    background-color: var(--Cyan);
    max-width: 130px;
    width: 100%;

    &:hover {
      background-color: #9be3e2;
    }
  }
}

.link {
  flex: 1;
  @include flexBox($g: 24px, $j: flex-end);

  & a:hover {
    text-decoration: underline;
  }

  button:disabled,
  button[disabled] {
    background: var(--Dark-Violet);
    cursor: default;
  }
}
.url {
  flex: 1;
}
.url,
.link a {
  @include handleOverflowText(1);
}
</style>
