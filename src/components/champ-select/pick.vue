<template>
  <div class="pick" @click="PickClicked($event)">
    <div class="splash">
      <img :src="champion.splashurl" :id="'picks_' + team + '_splash_' + pickid" class="hidden" />
    </div>
    <div class="textwrapper" :id="'picks_' + team + '_textwrapper_' + pickid">
      <div class="text" :id="'picks_' + team + '_text_' + pickid">{{ champion.name }}</div>
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
    pickid: {
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
    PickClicked (event) {
      console.log('Pick clicked')
      this.$emit(
        'pick-clicked',
        this
      )
    }
  }
}
</script>
