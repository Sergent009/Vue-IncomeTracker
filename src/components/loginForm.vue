<template>

    <div>
    <div class="loginform" v-if="!shownew">Abdul Mannan khan</div>
    <div class="container" v-if="!shownew">
      <div class="form">
        <div class="loginHeading">LOGIN FORM</div><br><br><br>
        <div class="inputElements">
          <input type="text" class="inp" placeholder="Your Name" v-model="a_email"><br><br><br>
          <input type="text" class="inp" placeholder="Password" v-model="a_pass">
        </div>
        <div>
          <button id="btn" @click="showFile">Submit</button>
        </div>
        <i class="fa-brands fa-facebook fa-2xl"></i>
        <i class="fa-brands fa-google fa-2xl"></i>
        <i class="fa-brands fa-youtube fa-2xl"></i>
      </div>
    </div>

    <show-click v-if="shownew" />
  </div>

</template>


<script>
import showClick from './show-click.vue'

export default {
  name: 'loginForm',
  components: {
    showClick
  },

   data(){
    return{
      shownew: false,
      email: 'abdulmannan.khan005@gmail.com',
      pass: 'Mannan786',
      a_email: '',
      a_pass: ''
    }
  },

  methods: {
    showFile(){
      if(this.a_email == this.email && this.a_pass == this.pass){
      this.shownew = true;
      }
      else{
        throw new Error("Invalid Email or Password!!");
      }
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

body{
  padding: 90px;
}

.loginform{
  width: 100vw;
  height: 50px;
  background: rgb(128, 104, 59);
  /* to make a box start from a starting point. */
  position: absolute;
  top: 0;
  left: 0;
  color: white;
  font-size: 40px;
}

.container{
  margin: 0px;
  padding: 0px;
  width: 100vw;
  height: 618px;
  background: linear-gradient(120deg, rgb(160, 120, 45), rgb(51, 114, 139));
   position: absolute;
  top: 50px;
  left: 0;
}

.form{
  width: 32vw;
  height: 35vw;
  border: 3px solid black;
  margin-left: 35vw;
  position: absolute;
  top: 80px;
  border-radius: 20px;
  background: linear-gradient(120deg, rgb(88, 115, 126), rgb(141, 114, 63));
}

.loginHeading{
  height: 50px;;
  color: white;
  font-size: 35px;
  background: rgb(139, 110, 56);
  border-radius: 17px;
}

.inp{
  width: 350px;
  height: 37px;
  border: 3px solid black;
  border-radius: 10px;
  font-size: 18px;
}

#btn{
  margin-top: 50px;
  margin-left: 240px;
  font-size: 22px;
  padding: 6px 22px;
  border: 3px solid black;
  border-radius: 10px;
  color: yellow;
  background: rgb(85, 112, 112);
}

.fa-facebook{
  margin-right: 60px;
  margin-top: 60px;
}
.fa-google{
  margin-right: 70px;
}
.fa-google{
  margin-left: 20px;
}
.fa-facebook:hover{
  cursor: pointer;
}
.fa-google:hover{
   cursor: pointer;
}
.fa-youtube:hover{
   cursor: pointer;
}
#btn:hover{
  cursor: pointer;
  background: rgb(139, 110, 56);
}

</style>
