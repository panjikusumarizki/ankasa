<template>
  <div>
    <b-row class="conta">
      <b-col lg="7" class="blueBanner">
        <img src="../assets/img/logo1.svg" alt="">
      </b-col>
      <b-col lg="5" class="formBanner">
        <b-col class="row formTitle">
        <img src="../assets/img/blueairlines.svg">
        <h5>Ankasa</h5>
        </b-col>
        <b-col>
<div class="login-box">
  <h4>Forgot Password</h4>
  <form class="formForgot">
    <div class="user-box">
      <input type="text" name="" required="">
      <label>Email</label>
    </div>
    <b-button class="mt-3 b-Signup" type="submit" block>Send</b-button>
  </form>
  <br>
  <p>You’ll get message soon on your email</p>
</div>
        </b-col>
      </b-col>
    </b-row>
  </div>
</template>

<style scoped>
.blueBanner img {
  padding-top: 100px;
  padding-left: 170px;
}
.checkalign {
  color: #595959;
  size: 100px;
}
.formTitle {
  padding-top: 20px;
  padding-left: 140px;
}
.conta {
  margin-left: 0px;
  margin-right: 0px;
}
.blueBanner {
  background: #2395FF;
  height: 100vh;
}
.b-Signin {
  border: 1px solid #2395FF;
  box-sizing: border-box;
  border-radius: 10px;
  background: #fff;
  color: #2395FF;

}
.b-Signin:hover {
  background: #2395ff;
  box-shadow: 0px 8px 10px rgba(35, 149, 255, 0.3);
  color: #fff;
  border: 1px solid #2395ff;
}
.b-Signup{
  border: 1px solid #2395ff;
  background: #2395FF;
  box-shadow: 0px 8px 10px rgba(35, 149, 255, 0.3);
  border-radius: 10px;
  padding: 10px;
}
.b-Signup:hover{
  background: #fff;
  box-shadow: 0px 8px 10px rgba(35, 149, 255, 0.3);
  color: #2395FF;
  border: 1px solid #2395ff;
}
.login-box {
  padding-right: 110px;
  padding-left: 110px;
  padding-top: 20px;
  box-sizing: border-box;
}

.login-box h4 {
  margin: 0 0 20px;
  padding: 0;
  color: #000000;
  text-align: left;
}

.login-box .user-box {
  position: relative;
}

.login-box .user-box input {
  width: 100%;
  padding: 10px 0;
  font-size: 16px;
  /* color: #fff; */
  margin-bottom: 30px;
  border: none;
  border-bottom: 1px solid rgba(210, 194, 255, 0.68);
  outline: none;
  background: transparent;
  /* background: rgba(210, 194, 255, 0.68); */
}
.login-box .user-box label {
  position: absolute;
  top:0;
  left: 0;
  padding: 10px 0;
  font-size: 15px;
  color: #9B96AB;
  pointer-events: none;
  transition: .5s;
}

.login-box .user-box input:focus ~ label,
.login-box .user-box input:valid ~ label {
  top: -20px;
  left: 0;
  font-size: 10px;
}
@media screen and (max-width: 375px){
  .blueBanner {
    display: none;
  }
  .login-box {
    position: relative;
    margin: 0px;
    padding: 0px;
    /* background: orangered; */
  }
  .checkalign {
    text-align: center;
  }
  .formTitle {
    margin: 0px;
    padding-left: 10px;
    padding-bottom: 20px;
  }
}
/* @media screen and (max-width: 1024px){
  .blueBanner {
    display: none;
  }
  .login-box {
    position: relative;
    margin-left: 50px;
    margin-right: 0px;
    margin-bottom: 0px;
    margin-top: 100px;
    padding: 0px;
    background: orangered;
  }
  .checkalign {
    text-align: center;
  }
  .formTitle {
    margin: 0px;
    padding-left: 10px;
    padding-bottom: 20px;
  }
} */
</style>
