<template>
  <div id="app">
    <thehead :patchversion="patchversion"/>
    <team team="blue" @field-clicked="fieldclick"/>
    <team team="red" @field-clicked="fieldclick"/>
    <thechampionsearch :championlist="championlist" @champion-clicked="championclick"/>
  </div>
</template>

<style lang="scss">
@import "../style.css";
</style>

<script>
import team from '../components/champ-select/team.vue'
import thehead from '../components/champ-select/the-head.vue'
import thechampionsearch from '../components/champ-select/thechampionsearch.vue'
// import axios from 'axios'

export default {
  components: {
    team,
    thehead,
    thechampionsearch
  },
  data: function () {
    return {
      patchversion: { text: '' },
      championlist: [],
      selectedchampion: undefined,
      selectedfield: undefined
    }
  },
  computed: {
  },
  mounted () {
    this.initchampionlist()
  },
  methods: {
    championidtoobject: function (championid) {
      return {}
    },
    initchampionlist: async function () {
      // request patch version
      await fetch('https://ddragon.leagueoflegends.com/api/versions.json')
        .then((response) => response.json())
        .then((data) => {
          this.patchversion.text = data[0]
        })
      // request champion list
      var champsresponse = await fetch('http://ddragon.leagueoflegends.com/cdn/' + this.patchversion.text + '/data/en_US/champion.json')
        .then((response) => response.json())
      var champsdata = champsresponse.data
      // build simplified champion list
      var champslist = []
      Object.keys(champsdata).forEach(key => {
        champslist.push({
          id: champsdata[key].key,
          name: champsdata[key].name,
          splashurl: 'http://ddragon.leagueoflegends.com/cdn/img/champion/splash/' + key + '_0.jpg',
          tileurl: 'http://ddragon.leagueoflegends.com/cdn/10.23.1/img/champion/' + key + '.png',
          loadingurl: 'http://ddragon.leagueoflegends.com/cdn/img/champion/loading/' + key + '_0.jpg'
        })
      })
      this.championlist = champslist
      // add champions to search module ?!
      return {}
    },
    championclick: async function (id) {
      this.selectedchampion = id
      if (this.selectedfield !== undefined) {
        this.arrangeChampion()
      }
    },
    fieldclick: async function (field) {
      this.selectedfield = field
      if (this.selectedchampion !== undefined) {
        this.arrangeChampion()
      }
    },
    arrangeChampion: async function () {
      this.selectedfield.champion = this.championlist.find(element => element.id === this.selectedchampion)
      this.selectedchampion = undefined
      this.selectedfield = undefined
    }
  }
}
</script>
