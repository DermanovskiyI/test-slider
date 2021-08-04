<template>
<div class="form-popup-bg">
    <div class="form-container">
        <button id="btnCloseForm" class="close-button" @click="handleTogglePopup">X</button>
        <form @submit.prevent="sendData" v-if="!purchased" class="form">
            <div class="form-group">
                <label for="">E-Mail Address</label>
                <input class="form-control" v-model="inputValue" type="text" />
                <div class="error" v-if="invalidEmail">Не правильный email</div>
            </div>
            <button type="submit" class="send-btn">Отправить</button>
        </form>
      <div class="success" v-else-if="purchased">СПАСИБО</div>
    </div>
    <div class="overlay" @click="handleTogglePopup"></div>
</div>
</template>

<script>

export default {
  data() {
    return {
      inputValue: '',
      purchased: false,
      invalidEmail: false,
    };
  },
  methods: {
    handleTogglePopup() {
      this.$emit('togglePopup');
    },
    sendData() {
      console.log(this.inputValue);
      if (this.validEmail(this.inputValue)) {
        const promise = new Promise((resolve) => {
          setTimeout(() => {
            resolve();
          }, 5000);
        });
        promise.then(() => {
          this.purchased = !this.purchased;
        });
      } else {
        this.invalidEmail = true;
      }
    },
    validEmail(email) {
      const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  display: flex;
  align-items: flex-end;
}
.form-popup-bg {
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.form-container {
  background-color: #2d3638;
  border-radius: 10px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 400px;
  margin-left: auto;
  margin-right: auto;
  position:relative;
  padding: 40px;
  color: #fff;
  z-index: 10001;
}

.close-button {
  background:none;
  color: #fff;
  width: 40px;
  height: 40px;
  position: absolute;
  top: 0;
  right: 0;
  border: solid 1px #fff;
  cursor: pointer;
}

.form-popup-bg:before{
  content:'';
  background-color: #fff;
  opacity: .25;
  position:absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.overlay {
  position: fixed;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  background-color: rgba(94, 110, 141, 0.9);
  overflow-y: auto;
  z-index: 10000;
}

.error {
  color: red;
  padding: 10px 0;
  position: absolute;
}
.send-btn {
  cursor: pointer;
}
</style>
