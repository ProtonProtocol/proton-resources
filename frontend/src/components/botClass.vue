<template>
  <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 mb-10">
    <h2 class="text-lg mb-4 leading-6 font-medium text-gray-900">
      Bot Tier
    </h2>

    <!-- Mobile dropdown -->
    <div class="sm:hidden">
      <label for="tabs" class="sr-only">Select a tab</label>
      <select
        id="tabs"
        name="tabs"
        class="block w-full focus:ring-indigo-500 focus:border-indigo-500 border-gray-300 rounded-md"
        @change="tierChange($event)"
      >
        <option
          v-for="tier of tiers"
          :key="tier"
        >
          {{ tier }}
        </option>
      </select>
    </div>

    <!-- Screen -->
    <div class="hidden sm:block">
      <div class="border-b border-gray-200">
        <nav class="-mb-px flex" aria-label="Tabs">
          <a
            v-for="(tier, i) of tiers"
            :key="tier"
            @click="selectTier(i)"
            class="w-1/4 py-4 px-1 text-center border-b-2 font-medium text-sm cursor-pointer"
            :class="{
              'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300': tier !== selectedTier,
              'border-indigo-500 text-indigo-600': tier === selectedTier
            }"
          >
            {{ tier }}
          </a>
        </nav>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      tiers: ['Basic', 'Plus', 'Pro', 'Enterprise'],
      selectedTier: 'Basic'
    }
  },
  methods: {
    selectTier (i) {
      this.selectedTier = this.tiers[i]
      this.$emit('select-bot-index', i)
    },

    tierChange (e) {
      this.selectTier(e.target.options.selectedIndex)
    }
  }
}
</script>

<style>

</style>
