<template>
  <section>
    <div class="header">
      <div class="logo">
        <img src="@/assets/logos/bitmap@2x.png" alt="" />
      </div>
      <div class="nav">
        <ul>
          <li>Find Work</li>
          <li>For Workers</li>
          <li>For Companies</li>
          <li>Business Solutions</li>
        </ul>
      </div>
      <div class="navigators">
        <div class="stores">
          <div class="logos">
            <img src="@/assets/logos/apple.png" alt="Apple Store" />
          </div>
          <div class="logos">
            <img src="@/assets/logos/playstore.png" alt="Playstore" />
          </div>
        </div>
        <button class="buttons">Sign In</button>
      </div>
    </div>

    <div class="formheader">
      <div class="headings">
        <h5>Unit # 1:</h5>
        <h3>Working in the Private Securoty Industry</h3>
      </div>
      <div class="result-summary">
        <!-- Attempt heading -->
        <p v-if="!submitted">
          Mock Questions: {{ markAnswer }} out of {{ Questions.length }}
        </p>

        <!-- result heading -->
        <p v-if="submitted">
          Result: {{ correctAnswer }} out of {{ Questions.length }}
        </p>

        <!-- attempts block -->
        <div
          v-show="!submitted"
          class="atmp-blocks"
          v-for="(Ques, index) in Questions"
          :key="index"
          :class="{
            checked: isChecked(index),
            uncheck: !isChecked(index),
            green: isCorrect(index),
            red: !isCorrect(index),
          }"
        ></div>

        <!-- Result block -->
        <div
          v-show="submitted"
          class="blocks"
          v-for="(Ques, index) in Questions"
          :key="index"
          :class="{ green: isCorrect(index), red: !isCorrect(index) }"
        ></div>
      </div>
    </div>
    <form @submit.prevent="submitQuiz">
      <div v-for="(Ques, index) in Questions" :key="index" class="question">
        <p class="QuesNo">Question#{{ Ques.id }}</p>
        <p
          v-if="submitted"
          class="result"
          :class="{ correct: isCorrect(index), incorrect: !isCorrect(index) }"
        >
          {{ isCorrect(index) ? "Correct" : "incorrect" }}
        </p>
        <h6>{{ Ques.Question }}</h6>
        <div
          v-for="(option, optionIndex) in Ques.Options"
          :key="optionIndex"
          class="options"
        >
          <input
            type="radio"
            :id="`q${index}o${optionIndex}`"
            :name="`q${index}`"
            :value="optionIndex"
            v-model="userAnswers[index]"
            :disabled="submitted"
            :class="{ green: isCorrect(index), red: !isCorrect(index) }"
          />
          <label :for="`q${index}o${optionIndex}`"> {{ option }}</label>
        </div>
      </div>
      <button class="buttons" type="submit">
        Submit and check Answers
        <span><i class="fa fa-arrow-right" aria-hidden="true"></i></span>
      </button>
    </form>

    <div class="footer">
      <div class="footer-head">
        <div class="foot-logo">
          <img src="@/assets/logos/bitmap@2x.png" alt="" />
        </div>
        <div class="links-logos">
          <div class="social-links">
            <img src="@/assets/icons/group-12.webp" alt="" />
          </div>
          <div class="social-links">
            <img src="@/assets/icons/group-13.png" alt="" />
          </div>
          <div class="social-links">
            <img src="@/assets/icons/group-14.png" alt="" />
          </div>
          <div class="social-links">
            <img src="@/assets/icons/group-18.png" alt="" />
          </div>
        </div>
      </div>

      <div class="footer-content row">
        <div class="content col-lg-6 col-md-6 col-sm-12 col-12">
          <p>
            EarnFlex gives me suitable security jobs close to my home around the
            hours that I prefer. I also get paid 30% higher than before because
            I am not dealing with so many agencies. This is a very welcome
            change for me. <br /><br />
            EarnFlex finds us pre-vetted high calibre resources in minutes and
            hours, vs days and weeks. Their unique automated shift analytics
            gives us the peace of mind that workers are conducting their work as
            expected - this is a significant advantage for any business.EarnFlex
            finds us pre-vetted high calibre resources in minutes and hours, vs
            days and weeks.
            <br />
            <br />
            Earnflex Ltd, Unit 1, 137a Molesey Avenue, Surrey, England, KT8 2RY
            <br />

            EarnFlex™ is a trademark, and EarnFlex Ltd is a company registered
            in England and Wales with company number 13723923
          </p>
        </div>
        <div class="bars col-lg-6 col-md-6 col-sm-12 col-12">
          <div class="bars-elements row">
            <div class="bar-col col-lg-4 col-md-6 col-sm-12 col-12">
              <h6>COMPANY</h6>
              <a href="#">About Us</a>
              <a href="#">Contact Us</a>
              <a href="#">Customer Reviews</a>
              <a href="#">Security Jobs</a>
              <a href="#">Blogs</a>
            </div>
            <div class="bar-col col-lg-4 col-md-6 col-sm-12 col-12">
              <h6>QUICK LINKS</h6>
              <a href="#">Get Licensed</a>
              <a href="#">Contact Us</a>
              <a href="#">Mobile App</a>
              <a href="#">Privacy policy</a>
              <a href="#">Term and Conditions</a>
            </div>
            <div class="bar-col col-lg-4 col-md-6 col-sm-12 col-12">
              <h6>PARTNERS</h6>
              <a href="#">Become a Partner</a>
              <a href="#">Become a Security Trainer</a>
              <a href="#">Pricing</a>
              <a href="#">How Can I Get SIA Licence</a>
              <a href="#">How to Find a Security Job</a>
            </div>
          </div>
          <div class="trusted-comp col-lg-12 col-md-12 col-sm-12 col-12">
            <img src="@/assets/TrustedCompanies/asset-1.png" alt="" />
            <img src="@/assets/TrustedCompanies/group-34.png" alt="" />
            <img src="@/assets/TrustedCompanies/group-53.png" alt="" />
            <img src="@/assets/TrustedCompanies/group-92.png" alt="" />
            <img src="@/assets/TrustedCompanies/group-53.png" alt="" />
            <img src="@/assets/TrustedCompanies/image-1.png" alt="" />
            <img src="@/assets/TrustedCompanies/group-44.png" alt="" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "QueForm",
  data() {
    return {
      Questions: [
        {
          id: 1,
          Question: "What event marked the beginning of World War I ?",
          Options: [
            "Pearl Harbor",
            "The Battle of Stalingrad",
            "The assassination of Archduke Franz Ferdinand",
            "The signing of the Treaty of Versailles",
          ],
          correctAnswer: 2,
        },
        {
          id: 2,
          Question:
            "Who was the leader of the Soviet Union during the Cuban Missile Crisis in 1962?",
          Options: [
            "Joseph Stalin",
            "Vladimir Putin",
            "Nikita Khrushchev",
            "Leon Trotsky",
          ],
          correctAnswer: 2,
        },
        {
          id: 3,
          Question:
            "Which ancient civilization is credited with the invention of the wheel?",
          Options: [
            "Mesopotamia",
            "Ancient Egypt",
            "Indus Valley Civilization",
            "Ancient China",
          ],
          correctAnswer: 0,
        },
        {
          id: 4,
          Question:
            "Which ancient civilization is credited with the invention of the wheel?",
          Options: [
            "Mesopotamia",
            "Ancient Egypt",
            "Indus Valley Civilization",
            "Ancient China",
          ],
          correctAnswer: 0,
        },

        {
          id: 5,
          Question:
            "The Great Wall of China was built primarily to defend against invasions from which nomadic group?",
          Options: ["Mongols", "Huns", "Vandals", "Visigoths"],
          correctAnswer: 0,
        },
        {
          id: 6,
          Question: "Who was the first President of the United States?",
          Options: [
            "Thomas Jefferson",
            "Benjamin Franklin",
            "George Washington",
            "John Adams",
          ],
          correctAnswer: 2,
        },
        {
          id: 7,
          Question:
            "In what year did Christopher Columbus first reach the Americas?",
          Options: ["1492", "1520", "1607", "1776"],
          correctAnswer: 0,
        },
        {
          id: 8,
          Question:
            "The Magna Carta, signed in 1215, is considered a foundational document for the development of which political concept?",
          Options: ["Democracy", "Communism", "Fascism", "Absolutism"],
          correctAnswer: 0,
        },
        {
          id: 9,
          Question:
            "The Renaissance, a period of great cultural and artistic growth, originated in which European city?",
          Options: ["Paris", "Rome", "Athens", "Florence"],
          correctAnswer: 3,
        },
        {
          id: 10,
          Question:
            "Who was the famous military leader and emperor of France known for his role in the Napoleonic Wars?",
          Options: [
            "Alexander the Great",
            "Napoleon Bonaparte",
            "Julius Caesar",
            "Genghis Khan",
          ],
          correctAnswer: 1,
        },
      ],
      userAnswers: Array.from({ length: 10 }, () => null),
      submitted: false,
    };
  },
  computed: {
    correctAnswer() {
      return this.userAnswers.filter((answer, index) => this.isCorrect(index))
        .length;
    },
    markAnswer() {
      return this.userAnswers.filter((answer, index) => this.isChecked(index))
        .length;
    },
  },
  methods: {
    submitQuiz() {
      this.submitted = true;
    },
    isCorrect(index) {
      return this.userAnswers[index] === this.Questions[index]?.correctAnswer;
    },
    isChecked(index) {
      if (this.userAnswers[index] === 0) {
        return 1;
      } else if (this.userAnswers[index] === 1) {
        return 1;
      } else if (this.userAnswers[index] === 2) {
        return 1;
      } else if (this.userAnswers[index] === 3) {
        return 1;
      }
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 40px;
  padding: 14px 14px;
  border-bottom: 1px solid #929292;
}
.logo img {
  width: 200px;
  height: 40px;
}
.nav {
  display: flex;
  justify-items: center;
  align-items: center;
}
.nav ul {
  margin-top: 14px;
  list-style: none;
  display: flex;
  gap: 16px;
}
.nav ul li {
  cursor: pointer;
}
.navigators {
  display: flex;
  gap: 20px;
}
.stores {
  display: flex;
  gap: 8px;
}
.logos {
  background-color: #003258;
  height: 40px;
  width: 40px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
form {
  padding: 0 100px;
  margin-bottom: 40px;
}
.logos img {
  width: 30px;
  height: 30px;
}
.buttons {
  padding: 4px 22px;
  height: 40px;
  color: #fff;
  background-color: #003258;
  border-radius: 16px;
  border: none;
  transition: all 0.4s ease-in-out;
}
.buttons:hover {
  transform: scale(1.01);
}
.formheader {
  display: flex;
  justify-content: space-evenly;
}
.headings {
  padding: 20px 70px;
  width: 50%;
}
.result-summary {
  margin-top: 20px;
}
.blocks {
  display: inline-block;
  width: 20px;
  height: 10px;
  border-radius: 5px;
  margin-right: 2px;
  background-color: #f1f1f1;
}

.green {
  color: green;
  background-color: green;
}
.red {
  color: red;
  background-color: red;
}

.atmp-blocks {
  display: inline-block;
  width: 20px;
  height: 10px;
  border-radius: 5px;
  margin-right: 2px;
  background-color: #f1f1f1;
}
.checked {
  background-color: #044374;
}
.uncheck {
  background-color: #d8d8d8;
}
.question {
  padding: 20px 10px;
}
.options input {
  margin-right: 4px;
}

.correct {
  color: green;
}
.incorrect {
  color: red;
}
/* footer styling */
.footer {
  margin: 0;
  border-radius: 22px;
  padding: 40px 160px;
  background-color: #003258;
}
.foot-logo {
  padding: 6px;
  border-radius: 24px;
  background-color: #fff;
}
.footer-head {
  display: flex;
  gap: 12px;
  justify-content: space-between;
  align-items: center;
}
.links-logos {
  display: flex;
  gap: 10px;
}
.footer-content {
  margin: 24px 0;
}
.content {
  padding-left: 10px;
  padding-right: 60px;
  color: #fff;
}
.bars-elements {
  margin-top: 10px;
  color: #fff;
}
.bar-col {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.bar-col h6 {
  margin-bottom: 16px;
}
.bar-col a {
  text-decoration: none;
  color: #fff;
}
.bar-col ul li {
  margin-left: 0;
  text-align: left;
}
.trusted-comp {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 30px;
}

@media screen and (max-width: 768px) {
  .nav {
    display: none;
  }
  .formheader {
    display: flex;
    flex-direction: column;
  }
  .result-summary {
    margin: 24px;
  }
  .headings {
    padding: 10px 20px;
    width: 100%;
  }
  .result-summary {
    margin-top: 30px;
  }
  form {
    padding: 0 16px;
    margin-bottom: 30px;
  }
  .footer {
    margin: 0;
    border-radius: 22px;
    padding: 40px 60px;
    background-color: #003258;
  }
  .footer-head {
    flex-direction: column;
  }
  .bars-elements {
    margin-top: 10px;
    margin-bottom: 20px;
  }
  .bar-col {
    margin-bottom: 30px;
    align-items: center;
  }
  .bar-col h6 {
    margin-bottom: 10px;
  }
  .trusted-comp {
    justify-content: center;
    align-items: center;
    margin-top: 30px;
  }
}
</style>
