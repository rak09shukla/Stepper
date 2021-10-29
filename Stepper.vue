<template>
  <div v-if="pagewindowWidth>=1024 && pageWindowHeight> 600" class="stepper-parent-component">
    <div class="stepper-component">
      <ul class="stepper">
        <li
          class="stepper-item"
          v-for="(step, index) in stepItem"
          :class="{'visitedStep':index<activeIndex, 'active': activeIndex=== index}"
          :key="step.id"
        >
          <span class="stepTxt">{{step}}</span>
        </li>
      </ul>
    </div>
    <button @click="setActive(activeIndex-1)" :disabled="activeIndex===0">Prev</button>
    <button @click="setActive(activeIndex+1)" :disabled="activeIndex===stepItem.length-1">Next</button>
  </div>
  <div v-else class="stepper-parent-component">
    <div class="stepper-component">
      <ul class="stepper">
        <li
          class="stepper-item"
          v-for=" (step, index) in stepItemMobile"
          :key="step.id"
          :class="{'visitedStep':index<activeIndex, 'active': activeIndex=== index}"
        >
          <span class="stepTxt">{{step}}</span>
        </li>
      </ul>
    </div>
    <span>{{stepItem[activeIndex]}}</span>
    <button @click="setActive(activeIndex-1)" :disabled="activeIndex===0">Prev</button>
    <button @click="setActive(activeIndex+1)" :disabled="activeIndex===stepItemMobile.length-1">Next</button>
  </div>
</template>  

<script>
export default {
  props: ["stepItem", "stepItemMobile", "pagewindowWidth", "pageWindowHeight"],
  data() {
    return {
      activeIndex: 0
    };
  },
  methods: {
    setActive(index) {
      this.activeIndex = index;
    }
  }
};
</script>
<style>
</style>