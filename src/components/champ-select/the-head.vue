<template>
  <div id="bar">
    <div class="blue colorbar"></div>
    <div class="blue text flex-vcenter">
      <span class="big-text" id="blue_name">{{team1name}}</span>
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
      <span class="big-text" id="red_name">{{team2name}}</span>
    </div>
    <div class="red colorbar"></div>
  </div>
</template>

<script>
export default {
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
  }
}
</script>
