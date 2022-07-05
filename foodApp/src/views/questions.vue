<template>
  <div>
    <questionList />
  </div>
</template>

<script>
// @ is an alias to /src
import questionList from "@/components/questionList.vue";

export default {
  name: "questions",
  components: {
    questionList,
  },
};
</script>
