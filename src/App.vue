<template>
  <div class="calc">
    <component
      :is="'app-tab-1'"
      @revenue="setRevenue"
      @workingVal="setWorkingVal"
      @parkingVal="setParkingVal"
      @EAParks="setEAParks"
      @time="setTime"
      @formData="setFormData"
      :tab="tab"
      v-if="tab === 1"
    >
      <app-stepper :tab="tab" @setNewTab="changeStepperTab"></app-stepper>
    </component>
    
    <app-tab-2
      @updateTab="changeTab"   
      :tab="tab" 
      v-show="tab === 2"
    ></app-tab-2>

    <div class="calc__aside">
      <component 
        :is="'app-aside-tab-' + tab"
        :revenue="revenue"
        :working="working"
        :parking="parking"
        :EAParks="EAParks"
        :time="time"
        @updateTab="changeTab"
      ></component>
    </div>
  </div>
</template>

<script>
  import AppAsideTab1 from './components/AppAside/AppAsideTab1.vue'
  import AppAsideTab2 from './components/AppAside/AppAsideTab2.vue'
  import AppTab1 from './components/AppTabs/AppTabsTab1.vue'
  import AppTab2 from './components/AppTabs/AppTabsTab2.vue'
  import AppStepper from './components/AppStepper.vue'

  export default {
    components: {
      AppAsideTab1,
      AppAsideTab2,
      AppTab1,
      AppTab2,
      AppStepper
    },

    data() {
      return {
        tab: 1,
        revenue: null,
        EAParks: null,
        working: '1',
        parking: '1',
        time: null,
      }
    },

    methods: {
      setRevenue(val) {
        return this.revenue = val
      },

      setWorkingVal(val) {
        return this.working = val
      },

      setParkingVal(val) {
        return this.parking = val
      },

      setEAParks(val) {
        this.EAParks = val
      },

      setTime(val) {
        this.time = val
      },

      changeTab(currentTab) {
        return this.tab = currentTab
      },

      changeStepperTab(currentTab) {
        return this.tab = currentTab
      },

      setFormData(data) {
        sessionStorage.setItem('formData', JSON.stringify(data))
      }
    }
  }
</script>
