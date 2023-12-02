<template>
  <section>
    <div class="header">
      <div class="logo">
        <img src="@/assets/logos/bitmap@2x.webp" alt="" />
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
        <button>Sign In</button>
      </div>
    </div>
    <div class="headings">
      <h5>Unit # 1:</h5>
      <h3>Working in the Private Securoty Industry</h3>
    </div>
    <form @submit.prevent="submitQuiz">
      <div v-for="Ques in Questions" :key="Ques.id" class="question">
        <p v-if="submitted"></p>

        <p class="QuesNo">Question#{{ Ques.id }}</p>
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
          />
          <label :for="`q${index}o${optionIndex}`"> {{ option }}</label>
        </div>
      </div>
    </form>
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
      userAnswers: [],
      submitted: false,
    };
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
.logos img {
  width: 30px;
  height: 30px;
}
.navigators button {
  padding: 4px 22px;
  height: 40px;
  color: #fff;
  background-color: #003258;
  border-radius: 16px;
}
.headings {
  padding: 20px 70px;
  width: 50%;
}
.question {
  padding: 20px 80px;
}
.options input {
  margin-right: 4px;
}
</style>
