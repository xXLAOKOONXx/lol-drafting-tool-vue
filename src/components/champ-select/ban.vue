<template>
  <div class="ban" @click="BanClicked($event)">
    <div class="splash">
      <img :src="champion.loadingurl" :id="'bans_' + team + '_splash_' + banid"/>
    </div>
    <div class="textwrapper" :id="'bans_' + team + '_textwrapper_' + banid">
      <div class="text" :id="'bans_' + team + '_text_' + banid">{{ champion.name }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    team: {
      type: String,
      required: true
    },
    banid: {
      type: Number,
      required: true
    }
  },
  data: function () {
    return {
      champion: {
        id: 0,
        splashurl: '',
        tileurl: '',
        name: '',
        loadingurl: ''
      }
    }
  },
  methods: {
    BanClicked (event) {
      this.$emit(
        'ban-clicked',
        this
      )
    }
  }
}
</script>
