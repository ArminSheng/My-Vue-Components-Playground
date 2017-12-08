<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'accordion',
    props: {
      collapse: false
    },
    data () {
      return {
        accordions: []
      }
    },
    methods: {
      doClick (idx) {
        if (this.collapse) {
          this.accordions.forEach(i => {
            if (i.name !== idx) {
              i.active = false
            }
          })
        }
      },
      add (item) {
        this.accordions.push(item)
      }
    }
  }
</script>