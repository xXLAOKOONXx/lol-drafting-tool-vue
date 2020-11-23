<template>
  <div id='championsearchwrapper'>
    <div class='champion' v-for="champ in championlist" :key="champ.id" @click="championclicked($event, champ.id)">
      <img :src="champ.tileurl" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    championlist: {
      type: Array,
      required: true
    }
  },
  methods: {
    championclicked (event, id) {
      console.log('Champion clicked: ' + id)
      this.$emit(
        'champion-clicked',
        id
      )
    }
  }
}
</script>
