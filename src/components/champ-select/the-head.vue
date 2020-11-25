<template>
  <div id="bar">
    <div class="blue colorbar"></div>
    <div class="blue text flex-vcenter">
      <span class="big-text" id="blue_name">
        <input v-if="team1editing" type="text" class="big-text" @change="team1nameedit($event)" v-model="team1namedata"/>
        <span v-if="!team1editing" @click="team1editing = true">{{team1namedata}}</span>
      </span>
    </div>
    <div class="blue timer flex-vcenter">
      <span class="big-text" id="blue_timer">:--</span>
    </div>
    <div class="middle">
      <div class="top flex-vcenter">
        <span class="score-text" id="score">Patch</span>
      </div>
      <div class="bot flex-vcenter">
        <span class="phase-text" id="phase">{{ patchversion.text }}</span>
      </div>
    </div>
    <div class="red timer flex-vcenter">
      <span class="big-text" id="red_timer">:--</span>
    </div>
    <div class="red text flex-vcenter">
      <span class="big-text" id="red_name">
        <input v-if="team2editing" type="text" class="big-text" @change="team2nameedit($event)" v-model="team2namedata"/>
        <span v-if="!team2editing" @click="team2editing = true">{{team2namedata}}</span>
      </span>
    </div>
    <div class="red colorbar"></div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      team1namedata: this.team1name,
      team2namedata: this.team2name,
      team1editing: false,
      team2editing: false
    }
  },
  props: {
    team1name: {
      type: String,
      default: 'Team 1'
    },
    team2name: {
      type: String,
      default: 'Team 2'
    },
    patchversion: {
      type: Object,
      default: function () {
        return {
          text: ''
        }
      }
    }
  },
  methods: {
    team1nameedit: function (event) {
      this.team1editing = !this.team1editing
    },
    team2nameedit: function (event) {
      this.team2editing = !this.team2editing
    }
  }
}
</script>
