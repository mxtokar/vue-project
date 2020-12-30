<template>
  <div id="app">
    <div class="wrapper">

      <v-btn class="mr-2" @click="clickBtn" :loader="loading">
        <i class="icon far fa-bell mr-2"></i>
        <span class="text">submit</span>
      </v-btn>

      <v-btn class="mr-2" outlined>
        <span class="text">Cancel</span>
      </v-btn>

      <v-check class="mr-2" label="VCheckbox" v-model="cheked"> </v-check>

      <v-select  
        :options="options"
        @select="optionSelect"
        :selected="selected"
        v-model="selectedItem"
      />
      
    </div>
  </div>
</template>

<script>
import vBtn from "./components/ui/v-btn/v-btn";
import vCheck from "./components/ui/checkbox/v-check";
import vSelect from "./components/ui/v-select/v-select"
export default {
  components: {
    vBtn,
    vCheck,
    vSelect
  },
  data: () => ({
    loading: false,
    cheked: false,
    options: [
      {title: 'item 01', value: '1'},
      {title: 'item 02', value: '2'},
      {title: 'item 03', value: '3'}
    ],
    selected: 'Select',
    selectedItem: ''
  }),
  methods: {
    clickBtn() {
      console.log("button clicked");
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 1500);
    },
    optionSelect(option){
      this.selected = option.title
    }
  },
};
</script>