<template>
  <div class="v-btn" v-bind:class="classBtn" @click="click">

    <div class="v-btn__loader">
      <div class="loader" :class="classLoader"></div>
    </div>

    <div class="v-btn__content" :class="classContent">
      <slot></slot>
    </div>

  </div>
</template>

<script>
export default {
  name: "v-btn",
  data() {
    return {};
  },
  props: {
    disabled: Boolean,
    outlined: Boolean,
    ghost: Boolean,
    loader: Boolean,
  },
  computed: {
    classBtn() {
      return {
        "v-btn--disabled": this.disabled,
        "v-btn--outlined--disabled": this.disabled,
        "v-btn--outlined": this.outlined,
        "v-btn--ghost": this.ghost
      };
    },
    classContent() {
      return {
        "v-btn__content--hidden": this.loader,
      };
    },
    classLoader() {
      return {
        "loader--hidden": !this.loader,
        "loader--outlined": this.outlined,
        "loader--ghost": this.ghost,
        "loader--disabled": this.disabled,
        "loader--disabled--outlined": this.outlined,
        "loader--disabled--ghost": this.ghost,
      };
    },
  },
  methods: {
    click() {
      this.$emit("click");
    },
  },
};
</script>


<style scoped lang="scss">
@import "@/assets/variables.scss";

.v-btn {
  padding: 10px 20px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  text-transform: uppercase;
  font-family: "Oswald", sans-serif;
  font-weight: 500;
  border-radius: 40px;
  color: $text-color;
  background: $blue-background;
  cursor: pointer;

  &--disabled {
    pointer-events: none;
    background: $disabled-background;
    color: $disabled-text;
  }

  &--outlined {
    border: 2px solid;
    border-color: $blue-background;
    background: $dark-background;
    &--disabled {
      border-color: $disabled-background;
      color: $disabled-text;
    }
  }

  &--ghost {
    background: $dark-background;
  }

  &__content {
    display: flex;
    align-items: center;

    &--hidden {
      visibility: hidden;
    }
  }

  &__loader{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

}
</style>

