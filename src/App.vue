<template>
  <div>
    <h1>Masukkan Kata-Kata</h1>
    <form @submit.prevent="addTask" :class="{ submitted: formSubmitted }">
      <input type="text" v-model="newTask" placeholder="Masukkan Kata-Kata">
      <button :class="{ submitted: formSubmitted }" @click="changeColor">Ubah Warna</button>
    </form>
    <div>
      <p :style="{ color: textColor, fontSize: '24px', fontWeight: 'bold', border: '2px solid black', padding: '10px', backgroundColor: 'lightgrey' }">{{ typedText }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      formSubmitted: false,
      typedText: '',
      colorIndex: 0,
      colors: ['blue', 'green', 'red', 'orange', 'purple','yellow', 'sea green']
    }
  },
  computed: {
    textColor() {
      return this.colors[this.colorIndex];
    }
  },
  methods: {
    addTask() {
      this.formSubmitted = true;
    },
    changeColor() {
      this.colorIndex = (this.colorIndex + 1) % this.colors.length;
    }
  },
  watch: {
    newTask(newVal) {
      this.typedText = newVal;
    }
  }
}
</script>

<style>
h1 {
  margin-bottom: 20px;
}

form {
  display: flex;
  margin-bottom: 20px;
}

input[type="text"] {
  padding: 5px;
  font-size: 16px;
  flex: 1;
  margin-right: 10px;
}

button {
  padding: 5px 10px;
  font-size: 16px;
  background-color: hsl(0, 18%, 23%);
  color: #fff;
  border: none;
  cursor: pointer;
}

button.submitted {
  color: rgb(247, 247, 247);
}

p {
  margin-top: 10px;
}
</style>
