<template>
  <div class="calc__stepper">
    <div 
      v-for="tabNum in 2" 
      :key="tabNum" 
      class="calc__stepper-item"
      :class="{ 'active': tabNum === tab }"
      @click="setNewTab(tabNum)"
    >
      <div>Step {{ tabNum }}</div>
      <div>{{ tabNum }}</div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      tab: {
        type: Number
      }
    },

    emits: ['setNewTab'],

    methods: {
      setNewTab(val) {
        this.$emit('setNewTab', val)
      }
    }
  }
</script>