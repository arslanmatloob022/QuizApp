<template>
  <section>
    <h2>this is test app</h2>
    <div v-for="Ques in Questions" :key="Ques.id">
      <h3>{{ Ques.Question }}</h3>
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
          Question: "This is first Questions",
          OpA: " Option A",
          OpB: "Option B",
          OpC: "Option C",
          OpD: "Option D",
        },
      ],
    };
  },
};
</script>

<style scoped></style>
