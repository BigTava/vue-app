<template>
  {{ dollar(amt) }}
</template>

<script>
export default {
  props: ['amt'],
  methods: {
    dollar(value) {
      return '$' + Number.parseFloat(value).toFixed(2)
    }
  },
  name: 'CurrencyVue'
}
</script>

<style></style>
