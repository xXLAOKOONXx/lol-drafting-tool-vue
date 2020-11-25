<template>
<div id='mid'>
  <button @click="hidden = !hidden" />
  <span v-if="!hidden">
    <span>
      <input v-model="searchtext" placeholder="Search"/>
    </span>
  </span>
  <div id='championsearchwrapper' v-if="!hidden">
    <div
    class='champion'
    v-for="champ in filteredList"
    :key="champ.id"
    @click="championclicked($event, champ.id)">
      <img :src="champ.tileurl" />
    </div>
  </div>
</div>
</template>

<script>
export default {
  data: function () {
    return {
      searchtext: '',
      hidden: false
    }
  },
  props: {
    championlist: {
      type: Array,
      required: true
    }
  },
  computed: {
    filteredList () {
      if (this.searchtext === '') return this.championlist
      return this.championlist.filter(champ => champ.name.toLowerCase().includes(this.searchtext.toLowerCase()))
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
