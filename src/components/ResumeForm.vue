<template>
  <form class="card card-w30" @submit.prevent="submitForm">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model.trim="value"></textarea>
    </div>

    <button class="btn primary" :disabled="!isValid">Добавить</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      value: "",
      type: "title",
    };
  },
  computed: {
    isValid() {
      return this.value.length > 2;
    },
  },
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

<style scoped></style>
