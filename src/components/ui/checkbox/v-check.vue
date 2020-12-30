<template>
  <div class="v-check">
    <input
      class="checkbox"
      id="checkbox"
      type="checkbox"
      @input="onChange"
    />
    <label class="label" for="checkbox">{{ label }}</label>
  </div>
</template>

<script>
export default {
  name: "v-check",
  props: {
    label: {
      type: String,
      default: "",
    },
  },
  methods: {
    onChange(event) {
      this.$emit('input', event.target.checked)
    }
  },
};
</script>
<style scoped lang="scss">
@import "@/assets/variables.scss";

.label {
  color: $text-color;
  font-family: "Oswald", sans-serif;
  font-weight: 500;
}

.checkbox {
  position: absolute;
  z-index: -1;
  opacity: 0;
}

.checkbox + .label {
  display: inline-flex;
  align-items: center;
  user-select: none;
}

.checkbox + .label::before {
  content: "";
  display: inline-block;
  width: 1em;
  height: 1em;
  border: 2px solid $disabled-background;
  border-radius: 0.35em;
  margin-right: 0.5em;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: 75% 75%;
}

.checkbox:checked + .label::before {
  border-color: $blue-background;
  background-color: $blue-background;
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 8 8'%3e%3cpath fill='%23fff' d='M6.564.75l-3.59 3.612-1.538-1.55L0 4.26 2.974 7.25 8 2.193z'/%3e%3c/svg%3e");
}

.checkbox + .label:hover::before {
  cursor: pointer;
}
</style>

