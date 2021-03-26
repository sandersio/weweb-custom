

<template>
    <div class="my-section">
        <h1 :style="textStyle">{{content.title}}</h1>
        <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et
            dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex
            ea commodo consequat.
        </p>
        <v-select :options="['Canada', 'United States']"></v-select>
        <h1 :style="textStyle"/>
         <wwLayout path="cards" direction="row" class="cards">
        <template v-slot="{ item }">
            <wwLayoutItem class="card">
                <wwObject v-bind="item" />
            </wwLayoutItem>
        </template>
    </wwLayout>
    </div>
</template>

<script>
import Vue from 'vue'
import vSelect from 'vue-select'
import 'vue-select/dist/vue-select.css';
Vue.component('v-select', vSelect)

export default {
  name: "__COMPONENT_NAME__",
  wwDefaultContent: {
    textColor: "#F23636",
    title: "Newest title",
    cards: [],
  },
  props: {
    content: { type: "Object", required: true },
  },
  computed: {
    textStyle() {
      return {
        color: this.content.textColor,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
.my-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 200px;
  .cards {
    display: flex;
    justify-content: space-around;
  }
  .card {
    border: 1px solid dashed;
    padding: 4px;
    border-radius: 8px;
    min-width: 100px;
  }
  h1 {
    font-size: 32px;
  }
  p {
    margin-top: 12px;
  }
}
</style>
