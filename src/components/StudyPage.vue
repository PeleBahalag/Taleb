<template>
    <div id="study_page">
      <div class="top_symbols">
        <img src="../assets/symbols/BahalagSymbol.svg" alt="BahalgSymbol" id="bahalag_symbol" />
        <img src="../assets/symbols/PeleSymbol.svg" alt="PeleSymbol" id="pele_symbol" />
       <img :src="img" alt="Titles" id="titles" />
     </div>
     <main-text v-if="showPlaces === 1" id="main_text" :subjectsName="subSaver" :subNumber="i" :innerPart="innerSub" :nameTitle="nameTitle" @make-progress="nextChapter"></main-text>
     <div id="text_container" v-if="showPlaces === 0">
        <div id="sub_text_list" v-for="(j, index) in optionArray[i]" :key="index" @click="updateSelected(index)" class="list-group-item"><p class="list-group-item">{{optionArray[i][index]}}</p></div>
     </div>
      <div id="bottom_part">
        <div id="home_click"  @click="startPage"></div>
        <div id="practice_click" @click="startPage" v-if="showPlaces === 0"></div>
     </div>
    </div>
</template>


<script>
import MainText from "@/components/MainText";



export default {
      name: "study-page",
      props: ['subjectsName', 'subNumber'],
  data() {
    return {
        subSaver: this.subjectsName,
        optionArray: [['נוהל 1.1- יחסי גומלין בתחום ההדרכה והלמידה עם מפקדות החיילות הראשיות', 
          'נוהל 1.2- שעון פעילות ביחידות ההכשרה',
            'נוהל 1.3- מיפוי הדרכתי ליחידות ההכשרה',
            'נוהל 1.4- תוכנית עבודה הדרכתית',
            'נוהל 1.5 ו-1.7-היערכות לפתיחת מחזור וסיכום סוף מחזור הכשרה',
            'נוהל 1.6- סיכומים עתיים במהלך ההכשרה',
            'נוהל 1.8- היערכות הכשרה ומשוב שטח',
            'נוהל 1.9-ביקורות תו תקן פנימיות ביחידה',
            'נוהל 1.10- ניהול המידע ההדרכתי',
            'נוהל 1.11 שימוש במערכת לניהול הדרכה (קמפוס דיגיטלי )' ],
            ['נוהל 2.1- פיתוח הכשרה חדשה',
            'נוהל 2.2- כתיבה,עדכון ואישור תיקי יסוד',
            'נוהל 2.3- הערכת חניכים (מבחנים בהכשרות)',
            'נוהל 2.4- תיק מדריך',
            'נוהל 2.5 - מפקדי חוליות'],
            ['נוהל 3.1- הגדרות תפקידם לסגלי הדרכה',
            'נוהל 3.2- איתור ומיון מפקדים להכשרות',
            'נוהל 3.3- הכנות מפקדים',
            'נוהל 3.4- פיתוח והערכת מפקדים',
            'נוהל 3.5- הכשרות הדרכה למפקדים ובעלי תפקידים בהכשרות ו’מפקדה מכשירה’.',
            'נוהל 3.6- תחלופת מפקדים בהכשרות',
            'נוהל 3.7- הרחקת איש סגל',
            'נוהל 3.8- פורום הדרכה בה’’די',
            'נוהל 3.9- שיחות מפקד ביה’’ס לסגלי הפיקוד ולהכשרות הקצונה',
            'נוהל 3.10- מסלולי קידום לסגלי פיקוד והדרכה'
            ],
            ['נוהל 4.1- נוהל טיפול בחניך מתקשה',
            'נוהל 4.2- וועדה להערכת חניך',
            'נוהל 4.3- בחירת חניך מצטיין וחניך למופת',
            'נוהל 4.4- תיק אישי חניך',
            'נוהל 4.5- העברת בוגר קורס יחידה קולטת ‘העברת מקל’.'
            ],
            ['נוהל 5.1- קליטה והטמעת מאמן בהכשרות',
            'נוהל 5.2- קליטת אמל’’ח ביחידת הדרכה',
            'נוהל 5.3- שגרת אחזקת תשתיות הדרכה'
            ]
        ],
        img: require(`../assets/symbols/subjects/${this.subjectsName}.svg`),
        i: this.subNumber,
        showPlaces: 0,
        innerSub: "",
        nameTitle: "",
        saver: ""
    }
  },
  components: {
    MainText
  },
  methods: {
    startPage(event){
        if( this.showPlaces === 1){
            this.showPlaces = 0;
        }else {
            if(event.target.id === "home_click"){
                this.$emit("curr-page", 2);
            }else if(event.target.id === "practice_click"){
                this.$emit("curr-page", 4);
            }
        }
    },

    updateSelected(selectedPart) {
        console.log(this.optionArray[this.i][selectedPart]);
        this.nameTitle = this.optionArray[this.i][selectedPart];
        this.saver = selectedPart;
        this.innerSub = selectedPart;
        this.showPlaces = 1;
        document.getElementById("text_container").style.visibility = "hidden";
    },

    nextChapter(count){
        this.nameTitle = this.optionArray[this.i][count + 1];
    }

  }
}
</script>


<style >
#study_page {
    background-image: url("../assets/photos/TalebBackground.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    height: 100%;
    width: 100%;
}

#main_text {
    position: absolute;
    width: 85vw;
    height: 75vh;
    top: 11vh;
    left: 10vw;
}

#sub_text_list{
    height: 8%;
    width: 95%;
    margin-left: 3%;
      margin-top: 3%;
  background-color: rgb(27, 148, 148);
    border-radius: 25px;
    text-align: center;
}

.list-group-item {
      direction: rtl;
  text-decoration: none;
      font-family: MyFont;
          font-weight: 1000vw;
    font-size: 4.2vw;
  color: white;
  cursor: pointer;
}

.list-group-item:hover {
  color: red;
}

.highlight {
  color: blue;
}


@font-face {
    font-family: MyFont;
    src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

.top_symbols {
    position: absolute;
    width: 100vw;
    height: 10vh;
    top: 0vh;
}

#bahalag_symbol {
    position: absolute;
    height: 85%;
    width: 20%;
    left: 1%;
    top: 10%;
}

#pele_symbol {
    position: absolute;
    height: 85%;
    width: 20%;
    right: 1%;
    top: 15%;
}


#text_container {
    position: absolute;
    width: 85vw;
    height: 75vh;
    top: 11vh;
    left: 10vw;
    background-image: url("../assets/symbols/TextBackground.svg");
    background-size: cover;
    background-repeat: no-repeat;
    visibility: visible;
}


#color_text {
    color: white;
    text-align: center;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 6vw;
}


#bottom_part {
    position: absolute;
    width: 100vw;
    height: 14vh;
    top: 86vh;   
}


#home_click {
    position: absolute;
    background-image: url("../assets/symbols/HomeSymbol.svg");
    background-repeat: no-repeat;
    background-size: contain;
    width: 16%;
    height: 60%;
    left: 44%;
    top: 20%;
    cursor: pointer;
}


#practice_click{
    position: absolute;
    background-image: url("../assets/symbols/GameButton.svg");
    background-repeat: no-repeat;
    background-size: contain;
    width: 22%;
    height: 60%;
    left: 10%;
    top: 25%;
    cursor: pointer;
}


#back_button {
    position: absolute;
    background-image: url("../assets/symbols/BackwardsButton.svg");
    background-size: contain;
    background-repeat: no-repeat;
    width: 15%;
    height: 10%;
    bottom: 0%;
    right: 2%;

}

#next_button {
    position: absolute;
    background-image: url("../assets/symbols/NextButton.svg");
    background-size: contain;
    background-repeat: no-repeat;
    width: 15%;
    height: 10%;
     bottom: 0%;
     left: 2%;
}

</style>