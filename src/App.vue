
<template>
  
  <h3>{{ info }}</h3>
  <p>{{ someInfo }}</p>

<button type="button" @click="this.info = 'Some new'"> отправить</button>

<button type="button" @click="userData()"> отправить метод</button>
<hr>

<input type ="text" v-model="userName" placeholder="name">
<input type ="password" v-model="userPass" placeholder="pass">
<input type ="email" v-model="userEmail" placeholder="email">

<p className="error">{{ error }}</p>

<button @click="sendData()">отправить</button>


<hr>

<p>{{ userName }}</p>

<hr>
<!-- <p>{{ users }}</p> -->


<div v-if="users.length ==0">
  у нас нет пользователей
</div>


<div v-else-if="users.length ==1">
только Один пользователь
</div>


<div v-else>
больше Одного тут
</div>



<div v-for="(el ,index) in users" :key="index">

  <h3>{{ el.name }}</h3>
  <p>{{ el.email }} - <b>{{ el.pass }}</b></p>
</div>
</template>


<script>
export default {
data(){
  return {
    info: 'Title',
    someInfo: ' anons of message',
 
    users:[],
    error:'',

    userName: '',
    userPass: '',
    userEmail: ''



  }
},


methods:{
  userData(word){
    this.someInfo = 'Some new'
 
  },

  insertData(val) {
    this.userName = val
  },

  sendData(){

    if(this.userName == ''){
      this.error='имя не введено';
      return;
    } else if (this.userEmail == ''){
      this.error='почта не введено';
      return;
    } else if (this.userPass == ''){
      this.error='пароль не введено';
      return;
    }


this.error ='';

    this.users.push({
      name: this.userName,
      pass: this.userPass,
      email: this.userEmail
    })
    
  }
}



}
</script>


<style scoped>
h3 {
  font-weight: lighter;
}

p {
  color: brown;
}
</style>
