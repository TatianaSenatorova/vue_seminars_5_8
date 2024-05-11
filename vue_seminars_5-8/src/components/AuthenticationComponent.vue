<!-- Задание 1. Семинар 5. Создайте компонент "Аутентификация" (Authentication), 
который будет отображать форму входа или сообщение об 
успешной аутентификации в зависимости от переданного 
пропса isAuthenticated. Используйте директиву v-if для 
условного отображения разных элементов в шаблоне 
компонента -->

<template>
  <div>
    <h2>Аутентификация</h2>
    <div v-if="isAuthenticated">
      <p>Успешная аутентификация! Добро пожаловать!</p>
    </div>
    <div v-else>
      <form @submit="login" action="#">
        <label for="username">Имя пользователя:</label>
        <input type="text" id="username" v-model="username" required>
        <label for="password">Пароль:</label>
        <input type="password" id="password" v-model="password" required>
        <button type="submit">Войти</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AutentificationComponent',
  data() {
    return {
      username: '',
      password: '',
      isAuthenticated: false,
      users: [
        { username: 'sergey', password: 'admin' },
        { username: 'admin', password: 'admin' },
        { username: 'test', password: 'test' }
      ]
    }
  },
  methods: {
    login(event) {
      event.preventDefault();
      console.log(this.username, this.password);
      if (this.users.find((item) => item.username === this.username && item.password === this.password)) {
        this.isAuthenticated = !this.isAuthenticated;
      }
      this.username = '';
      this.password = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>