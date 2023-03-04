<template>
  <div  class="form1">
    <p id = "registerForm">Register Form</p>
      <form v-show="step===1" class="register">
      <div>
        <input type="text" v-model="firstName" name="firstName" placeholder="FirstName:"/>
      </div>
      <div>
        <input type="text" v-model="lastName" name="lastName" placeholder="LastName:">
      </div>
      <div>
        <input type="text" v-model="userName" name="userName" placeholder="Your nickname:"/>
      </div>
      <div>
        <input type="email" v-model="email" name="email" placeholder="Email:">
      </div>
      <div>
        <button class="nextStep" @click="nextStep" type="button">Continue</button> 
      </div> 
    </form> 

    <form v-show="step===2" class="register">
      
      <div>
        <input type="password" v-model="password" name="password" placeholder="Password:"/>
      </div>
      <div>
        <input type="password" v-model="repeatPassword" name="repeatPassword" placeholder="Repeat password:">
      </div>
      <div>
        <p class="error">{{error}}</p>
      </div>
      <div>
        <button class="nextStep"  @click="backStep" type="button">Back</button>

        <button class="nextStep" v-if="password==repeatPassword && password!=null" @click="nextStep" type="button">Continue</button>
        <button class="nextStep" v-if="password!=repeatPassword || password==null" @click="printError" type="button">Continue</button>
      </div> 
    </form>
  </div>
</template>

<script>
export default{
  data(){
    return{
      error:null,
      step:1,
      firstName: null,
      lastName: null,
      userName: null,
      email:null,
      password:null,
      repeatPassword:null
    }
  },
  methods:{
    backStep(){
      this.step--
    },
    printError(){
      this.error = "Passwords missmatch!!!"
    },
    nextStep(){
      this.step++
      console.log(this.firstName)
    }
  }
}
</script>

<style>
body{
  background: rgb(167,65,213);
  background: linear-gradient(90deg, rgba(167,65,213,1) 0%, rgba(67,106,172,1) 50%, rgba(71,184,185,1) 100%);
  display: flex;
  justify-content: center;
  align-items:center;
}
.form1{
  margin-top: 100px;
  width:600px;
  height: 600px;
  background-color: #1f0f24;
  border-radius: 50px;
  font-weight: 700;
}
#registerForm{
  color:white;
  padding-top: 20px;
  font-size:48px;
  font-weight: bold;
  font-family:Arial, Helvetica, sans-serif;
  text-align: center;
}
.register div{
  color:white;
  text-align: center;
  padding-top: 30px;

}
.register input{
  color:white;
  background-color: #1f0f24;
  border-bottom:white;
  border-top:none;
  border-right:none;
  border-left:none;
  font-size:24px;
}
.nextStep{
  display: inline-block;
  margin:10px;
  color: white;
  font-weight: 700;
  text-decoration: none;
  user-select: none;
  padding: .5em 2em;
  outline: none;
  border: 2px solid;
  border-radius: 1px;
  transition: 0.2s;
  font-size:24px;
  background-color: #1f0f24;
}
.nextStep:hover{
  background: rgba(255,255,255,.2);
}
.nextStep:active{
  background: white; 
}
.error{
  font-size:16px;
  color:red;
}
</style>
