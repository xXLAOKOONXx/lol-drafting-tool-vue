<template>
  <div>
    <div :class="'picks ' + team " :id="'picks_' + team ">
      <pick v-for="i in fiveitems" :key="i" :team="team" :pickid="i" @pick-clicked="FieldClicked"></pick>
    </div>
    <div :class="'bans ' + team " :id="'bans_' + team ">
      <ban v-for="i in fiveitems" :key="i" :team="team" :banid="i" @ban-clicked="FieldClicked"></ban>
    </div>
  </div>
</template>

<script>
import pick from './pick.vue'
import ban from './ban.vue'

export default {
  comments: {
    pick,
    ban
  },
  props: {
    team: {
      type: String,
      required: true
    }
  },
  components: {
    pick,
    ban
  },
  computed: {
    fiveitems () {
      return [1, 2, 3, 4, 5]
    }
  },
  methods: {
    FieldClicked (field) {
      console.log('Field clicked')
      this.$emit(
        'field-clicked',
        field
      )
    }
  }
}
</script>
