<template>
  <div
    v-if="team"
    class="team-match-info"
  >
    <div
      v-for="(player, index) in team.players"
      :key="index"
    >
      <player-match-info
        :unfinishedMatch="unfinishedMatch"
        :player="player"
        :left="left"
        :big-race-icon="bigRaceIcon"
        :not-clickable="notClickable"
        :is-anonymous="isAnonymous"
        :highlighted="highlightedPlayer === player.battleTag"
        :show-heroes="showHeroes"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import { Team } from "@/store/types";
import PlayerMatchInfo from "@/components/matches/PlayerMatchInfo.vue";
import HeroIconRow from "@/components/matches/HeroIconRow.vue";

export default defineComponent({
  name: "TeamMatchInfo",
  components: {
    PlayerMatchInfo,
    HeroIconRow,
  },
  props: {
    team: {
      type: Object as PropType<Team>,
      required: false,
      default: undefined,
    },
    left: {
      type: Boolean,
      required: false,
      default: false,
    },
    bigRaceIcon: {
      type: Boolean,
      required: false,
      default: false,
    },
    notClickable: {
      type: Boolean,
      required: false,
      default: false,
    },
    unfinishedMatch: {
      type: Boolean,
      required: false,
      default: false,
    },
    isAnonymous: {
      type: Boolean,
      required: false,
      default: false,
    },
    highlightedPlayer: {
      type: String,
      required: false,
      default: "",
    },
    showHeroes: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
});
</script>

<style lang="scss" scoped>
.team-match-info {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
</style>
