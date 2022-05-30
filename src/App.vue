<template>
  <div class="container column">
    <resume-form @add-block="addBlock"></resume-form>
    <resume-content :blocks="blocks"></resume-content>
  </div>
  <div class="container">
    <app-loader v-if="isLoading"></app-loader>
    <resume-comments
      v-else
      :comments="comments"
      @load-comments="loadComments"
    ></resume-comments>
  </div>
</template>

<script>
import ResumeForm from "./components/ResumeForm.vue";
import ResumeContent from "./components/ResumeContent.vue";
import AppLoader from "./components/AppLoader.vue";
import ResumeComments from "./components/ResumeComments.vue";
export default {
  data() {
    return {
      isLoading: false,
      comments: [],
      blocks: [],
    };
  },
  methods: {
    addBlock(block) {
      this.blocks.push(block);
    },
    async loadComments() {
      this.loading = true;
      const res = await fetch(
        "https://jsonplaceholder.typicode.com/comments?_limit=42"
      );
      this.comments = await res.json();
      this.loading = false;
    },
  },
  components: { ResumeForm, ResumeContent, AppLoader, ResumeComments },
};
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
