<template>
  <div class="v-select">
    <p class="title" @click="areOptionsVisiable = !areOptionsVisiable">
      {{ selected }}
    </p>

    <div class="options" v-if="areOptionsVisiable">
      <p
        class="options-items"
        v-for="option in options"
        :key="option.value"
        @click="selectOption(option)"
      >
        {{ option.title }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
    name: "v-select",
    props: {
        options: {
            type: Array,
            default(){
                return []
            }
        },
        selected: {
            type: String,
            default: ''
        }
    },
    data() {
        return{
            areOptionsVisiable: false,
        }
    },
    methods: {
        selectOption(option) {
            this.$emit('input', option)
            this.$emit('select', option)
            this.areOptionsVisiable = false
        },
        hideSelect(){
            this.areOptionsVisiable = false
        }
    },
    mounted() {
        document.addEventListener('click', this.hideSelect.bind(this), true)
    },
    beforeDestroy() {
        document.removeEventListener('click', this.hideSelect)
    }
}
</script> 

<style lang="scss">
@import "@/assets/variables.scss";

.v-select {
  position: relative;
  width: 150px;
  cursor: pointer;
  font-family: "Oswald", sans-serif;
  color: $text-color;
}

.title {
  padding: 5px 10px;
  background: #121212;
  border-radius: 5px;
}

.v-select p {
  margin: 0;
}

.options {
  position: absolute;
  top: 40px;
  right: 0;
  width: 99%;
  background: #121212;
  border-radius: 5px;
}

.options-items {
  padding: 10px;
  border-radius: 5px;
}

.options-items:hover {
  color: $blue-background;
  background: #1c1c1c;
}

</style>