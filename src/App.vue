<template>
  <div id="app">
    <starter v-if="showPage === 1" @curr-page="switchScreen"></starter>
    <home-page v-if="showPage === 2" @curr-page="switchScreen" @picked-subject="subjectSwitch"></home-page>
    <study-page v-if="showPage === 3" @curr-page="switchScreen" :subjectsName="subjectsName" :subNumber="subNumber"></study-page>
    <game-home  v-if="showPage === 4" @curr-page="switchScreen" @player-status="playerState" :subNumber="subNumber"></game-home>
    <ending-screen v-if="showPage === 5" @curr-page="switchScreen" :playerStat="winOrLose"  :scorePlayer="score"></ending-screen>
  </div>
</template>

<script>
import Starter from "@/components/Starter";
import HomePage from "@/components/HomePage";
import StudyPage from "@/components/StudyPage";
import GameHome from "@/components/GameHome";
import EndingScreen from "@/components/EndingScreen.vue";

export default {
  name: "app",
  data() {
    return {
      showPage: 1,
      subjectsName: "",
      subNumber: 0,
      winOrLose: 0,
      score: 0,
    }
  },
  components: {
    Starter,
    HomePage,
    StudyPage,
    GameHome,
    EndingScreen,
  },
  methods: {
    switchScreen(pageNum) {
      this.showPage = pageNum;
    },
    subjectSwitch(subName){
      this.subjectsName = subName;
    switch(subName) {
      case "management":
        this.subNumber = 0;
      break;
      case "program":
        this.subNumber = 1;
      break;
      case "faculty":
        this.subNumber = 2;
      break;
      case "students":
        this.subNumber = 3;
      break;
      case "environment":
        this.subNumber = 4;
      break;
    default:
    // code block
}
    },
    playerState(player, score){
      console.log(score);
      this.score = score;
      this.winOrLose = player;
    }
  }

}
</script>

<style>
* {
  height: 100%;
  width: 100%;
}
</style>