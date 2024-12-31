<template>
  <n-input
    v-model:value="value"
    @update:value="onChange"
    type="text"
    placeholder="Search"
    :style="{
      '--n-color': '#D1D5DB',
      '--n-color-focus': '#D1D5DB',
      '--n-placeholder-color': '#000000',
      '--n-placeholder-color-focus': '#000000',
      '--n-border-radius': '8px',
    }"
  >
    <template #prefix>
      <n-icon>
        <IconSearch />
      </n-icon>
    </template>
  </n-input>
</template>

<script>
import { mapActions } from 'vuex'
import IconSearch from './icons/IconSearch.vue'

export default {
  components: {
    IconSearch,
  },
  data() {
    return {
      value: '',
    }
  },
  methods: {
    ...mapActions(['setSearchValue']),
    onChange(value) {
      this.setSearchValue(value)
    },
  },
}
</script>

<style scoped></style>
