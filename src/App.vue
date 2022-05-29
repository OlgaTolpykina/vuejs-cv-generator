<template>
  <div class="container column">
    <resume-form></resume-form>
    <resume-content></resume-content>
  </div>
  <div class="container">
    <resume-comments></resume-comments>
    <app-loader></app-loader>
  </div>
</template>

<script>
import ResumeForm from "./components/ResumeForm.vue";
import ResumeContent from "./components/ResumeContent.vue";
import AppLoader from "./components/AppLoader.vue";
import ResumeComments from "./components/ResumeComments.vue";
export default {
  components: { ResumeForm, ResumeContent, AppLoader, ResumeComments },
  methods: {
    submitForm() {
      console.group("FormData");
      console.log("value", this.value);
      console.log("value", this.type);
      console.groupEnd();
      this.value = "";
    },
  },
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
