<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      email: "",
      password: "",
      // submittedUser: {
      //   fullName: "",
      //   email: "",
      //   password: "",
      // },
      submittedUsers: [],
      cardNo: '',
    };
  },
  methods: {
    submitBtn() {
      const submittedUser = {
        fullName: this.firstName + " " + this.lastName,
        email: this.email,
        password: this.password,
      };
      this.submittedUsers.push(submittedUser);
      this.firstName = "";
      this.lastName = "";
      this.email = "";
      this.password = "";
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="input-form">
      <form @submit.prevent="submitBtn()" action="">
        <label for="firstName">First Name <span style="color: red;">*</span></label>
        <input type="text" v-model="firstName" />
        <label for="lastName">Last Name <span style="color: red;">*</span></label>
        <input type="text" v-model="lastName" />
        <label for="email"> Email <span style="color: red;">*</span> </label>
        <input type="text" v-model="email" />
        <label for="password"> Password <span style="color: red;">*</span> </label>
        <input type="password" v-model="password" />
        <button class="btn-primary">Submit</button>
      </form>
    </div>
    <div class="card-container">
      <div v-for="(data,index) in submittedUsers" @mouseover="cardNo = index" @mouseout="cardNo = ''" :class="[cardNo === index ? 'hovered-card' : '' ,'card']">
        <div class="card-body">
          <p>Full Name: {{ data.fullName }}</p>
          <p>Email: {{ data.email }}</p>
          <p>Password: {{ data.password }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}
.input-form {
  width: 50%;
  margin: 20px auto;
}
.container{
  max-width: 100%;
  margin: 0 8rem;
}
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
input {
  width: 100%;
  margin: 5px 0;
}
button {
  margin: 20px 0;
  cursor: pointer;
}
.btn-primary {
  background-color: rgb(73, 73, 236);
  color: white;
  border: none;
  padding: 10px;
  border-radius: 5px;
}
.card {
  height: auto;
  background-color: green;
  margin: 0 auto;
  padding: 10px;
  color: white;
  border-radius: 5px;
  transition: 0.3s ease;
  width: 100%;
  
}

.hovered-card {
  scale: 1.05;
  box-shadow: -5px 5px 20px rgba(0, 26, 255, 0.2);
  cursor: pointer;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}

.card-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 1.4rem;
  margin: 0 5rem;
}
</style>
