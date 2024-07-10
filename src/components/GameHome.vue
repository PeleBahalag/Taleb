<template>
    <div id="game_home">
        <div id="hearts_container">
            <p class="lives">:חיים</p>
            <img src="../assets/gameSymbols/HeartsSymbol.svg" alt="heart" id="first_heart" class="hearts"/>
            <img src="../assets/gameSymbols/HeartsSymbol.svg" alt="heart" id="second_heart" class="hearts"/>
            <img src="../assets/gameSymbols/HeartsSymbol.svg" alt="heart" id="third_heart" class="hearts"/>
        </div>
        <div id="question_container">
           <h2 id="question" v-if="saveName === 0" :key="management[currentQuestion].question">{{ management[currentQuestion].question }}</h2>
           <h2 id="question" v-if="saveName === 1" :key="program[currentQuestion].question">{{ program[currentQuestion].question }}</h2>
           <h2 id="question" v-if="saveName === 2" :key="faculty[currentQuestion].question">{{ faculty[currentQuestion].question }}</h2>
           <h2 id="question" v-if="saveName === 3" :key="students[currentQuestion].question">{{ students[currentQuestion].question }}</h2>
           <h2 id="question" v-if="saveName === 4" :key="environment[currentQuestion].question">{{ environment[currentQuestion].question }}</h2>
           </div>
        <div id="choices_container">
          <div v-if="saveName === 0">
            <div id="choices"  v-for="(answer, index) in management[currentQuestion].answers" :key="index"  v-bind:data-index="index">
            <h4 id="text_answer"  @click="selectAnswer" >
                {{ answer }}
                </h4>
          </div>
          </div>
          <div v-if="saveName === 1">
          <div id="choices" v-for="(answer, index) in program[currentQuestion].answers" :key="index"  v-bind:data-index="index">
            <p id="text_answer" @click="selectAnswer" v-if="saveName === 1">{{ answer }}</p>
          </div>
          </div>
          <div v-if="saveName === 2">
           <div id="choices" v-for="(answer, index) in faculty[currentQuestion].answers" :key="index"  v-bind:data-index="index" >
            <p id="text_answer" @click="selectAnswer">{{ answer }}</p>
           </div>
          </div>
          <div  v-if="saveName === 3">
          <div id="choices" v-for="(answer, index) in students[currentQuestion].answers" :key="index"  v-bind:data-index="index">
            <p id="text_answer" @click="selectAnswer" >{{ answer }}</p>
          </div>
          </div>
          <div v-if="saveName === 4"> 
          <div id="choices" v-for="(answer, index) in environment[currentQuestion].answers" :key="index"  v-bind:data-index="index">
            <p id="text_answer" @click="selectAnswer">{{ answer }}</p>
          </div>
          </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "game-home",
    props: ['subNumber'],
    data(){
        return {
            management: [
            {
            question: 'מה הוא שעון פעילות?',
            answers: [
                'Apple',
                'Microsoft',
                'גרף המגדיר את העיתוי של מופעי ניהול ההדרכה המרכזיים בהכשרה',
                'Commodoredthyhfghjfgykyjfghjfgyjgfhfdghfghjdfzfdghzdfhggfhsfsf'
            ],
            correct_answer: 'גרף המגדיר את העיתוי של מופעי ניהול ההדרכה המרכזיים בהכשרה',
            },
            {
            question: '"אבחון הדרכתי = __?__ "',
            answers: [
                'איתור צרכים',
                'Do-while loops',
                'For loops',
                'While loops'
            ],
            correct_answer: 'איתור צרכים',
            },
            {
            question: 'מה תגלם תוכנית העבודה ההדרכתית?',
            answers: [
                '512',
                'תוכנית העבודה ההדרכתית תגלם את כלל הפעולות לשיפור ההכשרות',
                '1024',
                '500'
            ],
            correct_answer: 'תוכנית העבודה ההדרכתית תגלם את כלל הפעולות לשיפור ההכשרות',
            },
            {
            question: 'מה הם שלושת הדיונים המרכזיים בנושא "היערכות לפתיחת מחזור וסיכום מחזור הכשרה"?',
            answers: [
                '512',
                'סיכום מחזור הכשרה, אישורי תוכניות להכנת הסגל ו"כברת דרך", אישור תוכניות למחזור וכשירות הסגל.',
                '1024',
                '500'
            ],
            correct_answer: 'סיכום מחזור הכשרה, אישורי תוכניות להכנת הסגל ו"כברת דרך", אישור תוכניות למחזור וכשירות הסגל.',
            },
            {
            question: 'מה היא הערכת הכשרה בודקת?',
            answers: [
                '512',
                'סיכום',
                'הערכת בודקת היא הכשרה ממוקדת אחת, במטרה לאתר פערים לשיפור בתוכנית ההכשרה.',
                '500'
            ],
            correct_answer: 'הערכת בודקת היא הכשרה ממוקדת אחת, במטרה לאתר פערים לשיפור - בתוכנית ההכשרה.',
            },
            {
            question: 'מה הם שלושת סוגי המידע שמקובל להבחין בהם בניהול ההכשרות?',
            answers: [
                '1.מידע על הפרט - על החניך והמפקד. 2. מידע לימודי לקיום ההכשרה להכשרה ספציפית. 3. מידע ארגוני.',
                'Do-while loops',
                'For loops',
                'While loops'
            ],
            correct_answer: '1.מידע על הפרט - על החניך והמפקד. 2. מידע לימודי לקיום ההכשרה להכשרה ספציפית. 3. מידע ארגוני.',
            },
            ],
            program: [
            {
            question: 'נכון או לא נכון: הגדרת מצבי המבחן המסכם, בניית מערכת שעות עקרונית להכשרה והגדרת לו"זים ותחומי אחריות הם תהליכים לפיתוח הכשרה חדשה?',
            answers: [
                'נכון',
                'לא נכון',
            ],
            correct_answer: 'נכון',
            },
            {
            question: 'פיתוח הכשרה חדשה מתבצע בדרך כלל בעקבות...?',
            answers: [
                'If',
                'Do-while loops',
                'שינויים בתו"ל, תפיסות ואמל"ח, אשר דורשים בעלי תפקידים חדשים שלא היו קיימים בעבר.',
                'While'
            ],
            correct_answer: 'שינויים בתו"ל, תפיסות ואמל"ח, אשר דורשים בעלי תפקידים חדשים שלא היו קיימים בעבר.',
            },
            {
            question: 'מה הוא תיק יסוד?',
            answers: [
                '512',
                'מסמך מחייב לכל קורס או השתלמות ומתועדים בו מבנה הקורס והתנאים הנדרשים לקיומו.',
                '10',
                '5'
            ],
            correct_answer: 'מסמך מחייב לכל קורס או השתלמות ומתועדים בו מבנה הקורס והתנאים הנדרשים לקיומו.',
            },
            //        {
            // question: '"אבחון הדרכתי = __?__ "',
            // answers: [
            //     'איתור צרכים',
            //     'Do-while loops',
            //     'For loops',
            //     'While loops'
            // ],
            // correct_answer: 'איתור צרכים',
            // },
                   {
            question: 'מה צריך לעשות טרם מבחן הערכת חניך, עיוני ומעשי?',
            answers: [
                'בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את דף ההערכה.',
                'Do-while loops',
                'For loops',
                'While loops'
            ],
            correct_answer: 'בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את דף ההערכה.',
            },
                   {
            question: 'נכון או לא נכון: לכל מבחן עיוני ייבנה דף הערכה אשר יכלול את הקריטריונים להערכת הביצוע של הנבחן.',
            answers: [
                'נכון',
                'לא נכון, מדובר על מבחן מעשי ולא עיוני',
            ],
            correct_answer: 'לא נכון, מדובר על מבחן מעשי ולא עיוני',
            },
                   {
            question: 'למה נועד תיק מדריך?',
            answers: [
                'זגכע',
                'Do-while loops',
                'התיק נועד לאפשר הכנה מקצועית של המפקד או מדריך, להביא לאחידות מקצועית ולתרום לזיכרון הארגוני.',
                'While loops'
            ],
            correct_answer: 'התיק נועד לאפשר הכנה מקצועית של המפקד או מדריך, להביא לאחידות מקצועית ולתרום לזיכרון הארגוני.',
            }, 
            ],
            faculty: [
                      {
            question: 'איך נקרא האחראי על תכנון וביצוע הכנות סגל למפקדים',
            answers: [
                'App',
                'Micr',
                'קצין מגמה',
                'Comm'
            ],
            correct_answer: 'קצין מגמה',
            },
            {
            question: 'נכון או לא נכון: יכולת העברת מסרים ויכולות הובלה ורתימה הם חלק מרשימת הקריטריונים לסימון פוטנציאל מאותרים לפיקוד?',
            answers: [
                'נכון',
                'לא נכון',
            ],
            correct_answer: 'נכון',
            },
            {
            question: '"הכנת סגל תבנה בחילוק לארבעה צירים", בחר בתשובה השייכת לארבעת הצירים.',
            answers: [
                'הציר הפיקודי',
                '1',
                '10',
                '5'
            ],
            correct_answer: 'הציר הפיקודי',
            }, 
            {
            question: 'מה הוא פיתוח והערכת מפקדים?',
            answers: [
                'App',
                'Micr',
                'A',
                ' תהליך שיטתי ומובן, המאורגן בתוכנית קבועה מראש. התהליך מתחיל מיום קליטתו ועד סיום תפקידו.'
            ],
            correct_answer:  'הערכת  וחניכת איש הסגל הוא תהליך שיטתי ומובן המאורגן בתוכנית קבועה מראש. התהליך מתחיל מיום קליטתו ועד סיום תפקידו.',
            },
             {
            question: 'מפקדים בדרג מ"מ ומקביליו יבצעו תפקיד של ______',
            answers: [
                'לכל הפחות שני מחזורי הכשרה.',
                'Micr',
                'A',
                'Comm'
            ],
            correct_answer: 'לכל הפחות שני מחזורי הכשרה.',
            },
            {
            question: 'מרגע קבלת החלטה להרחיק איש סגל ניתן לאפשר לו להגיש עירעור שיועבר  למפקד בית הספר עד כ____',
            answers: [
                'App',
                '48 שעות',
                'A',
                'Comm'
            ],
            correct_answer: '48 שעות',
            },
            ],
            students: [
            {
            question: 'דרכי הפעולה לקידום חניך:',
            answers: [
                'App',
                'שעות תיגבור, זמנים ללמידה עצמית, מועדי מבחנים חוזרים, התנסויות והצמדת חונך מקצועי.',
                'A',
                'Comm'
            ],
            correct_answer: 'שעות תיגבור, זמנים ללמידה עצמית, מועדי מבחנים חוזרים, התנסויות והצמדת חונך מקצועי.',
            },
            {
            question: 'מה הם העילות להעלאת חניך לוועדת הערכה?',
            answers: [
                'If',
                'Do-while loops',
                'הפסד ימי הכשרה ע"פ המוגדר בתיק יסוד, אירוע ערכי/נורמטיבי/משמעתי, אי עמידה בציוני הסף.',
                'While'
            ],
            correct_answer:  'הפסד ימי הכשרה ע"פ המוגדר בתיק יסוד, אירוע ערכי/נורמטיבי/משמעתי, אי עמידה בציוני הסף.',
            },
            {
            question: '"תהליך בחירת חניך מצטיין וחניך למופת נועד..."',
            answers: [
                'להגביר את הרצון להשקיע בהכשרה ולתגמל חניכים שהשקיעו.',
                '1',
                '10',
                '5'
            ],
            correct_answer: 'להגביר את הרצון להשקיע בהכשרה ולתגמל חניכים שהשקיעו.',
            },
            {
            question: 'מה מהבאים הוא מרכיב להצטיינות מופת?',
            answers: [
                'App',
                'Micr',
                'הישגים לימודיים',
                'Comm'
            ],
            correct_answer: 'הישגים לימודיים',
            },
            {
            question: 'מה הוא תיק אישי לחניך?',
            answers: [
                'תיק אישי לחניך משמש אמצעי לאיסוף המידע וריכוזו במכלול נושאים בעלי רלוונטיות לחניכים בקורס.',
                'Micr',
                'A',
                'Comm'
            ],
            correct_answer:  'תיק אישי לחניך משמש אמצעי לאיסוף המידע וריכוזו במכלול נושאים בעלי רלוונטיות לחניכים בקורס.',
            },
            {
            question: 'על דוח העברת המקל לפרט את המידע הבא:',
            answers: [
                'App',
                'Micr',
                'A',
                'פרטים אישיים, מידע מקצועי, מידע אודות נורמות וערכים, מידע נוסף'
            ],
            correct_answer: 'פרטים אישיים, מידע מקצועי, מידע אודות נורמות וערכים, מידע נוסף',
            },
            ],  
            environment: [
            {
            question: 'ההדרכה על אמל"ח ביבשה עוברת בשנים האחרונות תהליך שינוי במסגרתו הלמידה מתבצעת יותר על ______ ופחות על האמל"ח בפועל.',
            answers: [
                'App',
                'Micr',
                'אמצעים מדמים',
                'Comm'
            ],
            correct_answer: 'אמצעים מדמים',
            },
            {
            question: 'יש להוציא _____ בחתימת מפקד הבה"ד, ךקךיטת המאמןוהפונקציות המוגדרות בתהליך.',
            answers: [
                'If',
                'Do-while loops',
                'For',
                'כתב מינוי'
            ],
            correct_answer: 'כתב מינוי',
            },
            {
            question: ' הוראות הקליטה האגמ"ית נכתבת ע"י החיל ומופצת כפקודה לבית הספר כ_____ טרם תחילת ההכשרה בהכשרות.',
            answers: [
                '512',
                '1',
                'חצי שנה',
                '5'
            ],
            correct_answer: 'חצי שנה',
            },
            {
            question: 'על וועדת הקליטה לנהל גאנט הכולל את הנושאים הבאים: מעקב אחר...',
            answers: [
                'אמצעים להדרכה, פיתוח תכולות ההדרכה, הכנת הסגלים, עדכון תיקי היסוד הרלוונטים',
                '1',
                '10',
                '5'
            ],
            correct_answer: 'אמצעים להדרכה, פיתוח תכולות ההדרכה, הכנת הסגלים, עדכון תיקי היסוד הרלוונטים',
            },
            {
            question: 'ע"מ לשמר את תשתיות ההדרכה...',
            answers: [
                '512',
                '1',
                'יש לקיים מנגנון לאחזקתן',
                '5'
            ],
            correct_answer: 'יש לקיים מנגנון לאחזקתן',
            },
            {
            question: 'תשתיות הדרכה-',
            answers: [
                '512',
                'כל מבנה שמטרתו לקיים באמצעותו למידה או אימון לרבות כיתות מסוגים שונים, טווחים, לש”ביות ומאמנים',
                '10',
                '5'
            ],
            correct_answer: 'כל מבנה שמטרתו לקיים באמצעותו למידה או אימון לרבות כיתות מסוגים שונים, טווחים, לש”ביות ומאמנים',
            },
            ],
            currentQuestion: 0,
            answered: 0,
            wrongAnswers: 0, 
            correctAnswers: 0,
            saveName: this.subNumber,
        }
    },
        methods: {
            selectAnswer(event){
                var MyAnswer = event.target.innerText;
                this.answered = this.answered + 1;

                if(this.answered === 6){
                    this.correctAnswers = this.correctAnswers + 1;
                    this.startOver();
                }
                
            switch(this.saveName) {
                case 0:
                    if(MyAnswer !== this.management[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
                case 1:
                    if(MyAnswer !== this.program[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
                case 2:
                    if(MyAnswer !== this.faculty[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
                case 3:
                    if(MyAnswer !== this.students[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
                case 4:
                    if(MyAnswer !== this.environment[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
               default:
            }
                

            },

            checkAnswer(){
                this.currentQuestion = this.currentQuestion + 1;

                if(this.wrongAnswers === 0){
                        this.wrongAnswers = this.wrongAnswers + 1;
                        document.getElementById("third_heart").style.display = "none";
                }else if(this.wrongAnswers === 1){
                        this.wrongAnswers = this.wrongAnswers + 1;
                        document.getElementById("second_heart").style.display = "none";
                }else if(this.wrongAnswers === 2) {
                        setTimeout(() => {
                            document.getElementById("first_heart").style.display = "none";
                        }, 5000);
                            this.wrongAnswers = this.wrongAnswers + 1;
                            this.startOver(); 
                }
            },

            startOver(){
                if(this.wrongAnswers === 3){
                    this.$emit("player-status", 1, this.correctAnswers);
                }else {
                    this.$emit("player-status", 0, this.correctAnswers);
                }
                 this.$emit("curr-page", 5);
            },
        }
}
</script>

<style scoped>
#game_home {
    background-image: url("../assets/photos/GameBackground.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    height: 100%;
    width: 100%;
}

#question_container{
    position: absolute;
     height: 25vh;
     width: 72vw;
     left: 13vw;
     top: 10vh;
    background-image: url("../assets/gameSymbols/GameQuestionBox.svg");
    background-size: cover;
    background-attachment:inherit;
}

#question {
    position: absolute;
    width: 95%;
    height: 85%;
    top: 5%;
    left: 2.5%;
    color: white;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 4.2vw;
    text-align: center;
    line-height: 42.5px;
    direction: rtl;
}

#deactivate {
  pointer-events: none;
}

#choices_container{
    position: absolute;
    height: 65vh;
    width: 80vw;
    left: 15vw;
    top: 40vh;
}

#choices{
    margin-bottom: 3%;
    background-image: url("../assets/gameSymbols/AnswerSymbol.svg");
    background-size: cover;
    background-repeat: no-repeat;
    width: 85%;
    height: 17%;
    direction: rtl;
}



#text_answer{
    position: absolute;
    color: white;
    width: 57%;
    height: 17%;
    left: 13%;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 3.5vw;
    overflow-wrap: break-word;
    direction: rtl;
}


@font-face {
    font-family: MyFont;
    src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

/* game hearts */

#hearts_container{
    position: absolute;
    height: 10vh;
    width: 55vw;
    right: 0vw;
    top: 0vh;
}

.lives{
    position: absolute;
    text-align: end;
    font-family: MyFont;
    font-size: 6vw;
    color: white;
    top: 7%;
}

#first_heart{
    position: absolute;
    height: 55%;
    width: 15%;
    left: 55%;
    top: 10%;
}

#second_heart{
    position: absolute;
    height: 55%;
    width: 15%;
    left: 35%;
    top: 10%;
}

#third_heart{
    position: absolute;
    height: 55%;
    width: 15%;
    left: 15%;
    top: 10%;
}
</style>