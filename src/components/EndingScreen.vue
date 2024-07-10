<template>
    <div id="ending_screen">
        <h1 id="winning_text" class="changing_title" v-if="playerStat === 0">כל הכבוד! עברת את המשחק בהצלחה</h1>
        <h1 id="losing_text" class="changing_title" v-if="playerStat === 1">לצערנו לא נשארו לך יותר חיים, אבל אל דאגה! תעברו קצת על החומר ונסו שוב</h1>
        <p id="score">ענית נכון על  {{this.scorePlayer}} שאלות </p>
        <p id="explain">אם תרצו לחזור למסך הבית לחצו על הכפתור השמאלי בתחתית העמוד, אם תרצו להתחיל את התרגול מחדש לחצו על הכפתור הימני שבתחתית העמוד</p>
        <div id="button_containers">
            <img src="../assets/symbols/HomeSymbol.svg" alt="Home Button" id="home_button" @click="changePage"/>
            <img src="../assets/gameSymbols/TryAgain.svg" alt="Return Buttom" id="return_button" @click="changePage"/>
        </div>
    </div>
</template>


<script>
export default {
    name: "ending-screen",
    props:["playerStat", "scorePlayer"],
    data(){
        return{
            winOrLose: this.playerStat,
        }
    },
    methods: {
        changePage(event){
            if(event.target.id === "home_button"){
                this.$emit("curr-page", 2);
            }
            else if(event.target.id === "return_button"){
                this.$emit("curr-page", 4);
            }
        }
    },
}
</script>

<style scoped>
@font-face {
    font-family: MyFont;
    src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

#ending_screen {
    background-image: url("../assets/photos/GameBackground.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    height: 100%;
    width: 100%;
}

.changing_title{
    position: absolute;
    height: 10vh;
    width: 75vw;
    font-family: MyFont;
    font-size: 6vw;
    color: white;
    text-align: center;
    top: 15vh;
    left: 13vw;
}

#button_containers{
    position: absolute;
    height: 25vh;
    width: 85vw;
    bottom: 5vh;
    left: 10vw;
}

#home_button{
    position: absolute;
    height: 50%;
    width: 35%;
    left: 5%;
}

#return_button{
    position: absolute;
    height: 50%;
    width: 35%;
    right: 5%;
}

#explain{
    position: absolute;
    height: 10vh;
    width: 85vw;
    font-family: MyFont;
    font-size: 5vw;
    color: white;
    text-align: center;
    top: 45vh;
    left: 10vw;
}

#score{
        position: absolute;
    height: 10vh;
    width: 85vw;
    font-family: MyFont;
    font-size: 4.5vw;
    color: white;
    text-align: center;
    top: 30vh;
    left: 10vw;
}

</style>