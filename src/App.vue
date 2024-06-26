<template>
  <div class="container">
    <h1>MASUKKAN DATA</h1>
    <input v-model="inputText" @input="handleInput" placeholder="Ketik sesuatu..." />

    <div :class="['box', { active: isActive }]" :style="boxStyle">
      {{ message }}
    </div>

    <button @click="toggleActive">Toggle Active</button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const inputText = ref('');
const isActive = ref(false);

const boxStyle = computed(() => ({
  backgroundColor: isActive.value ? 'lightblue' : 'lightgray',
  border: '1px solid black',
  padding: '10px',
  marginTop: '10px'
}));

const message = computed(() => `You typed: ${inputText.value}`);

const handleInput = () => {
  console.log('Input changed:', inputText.value);
};

const toggleActive = () => {
  isActive.value = !isActive.value;
};
</script>

<style scoped>
.container {
  border: 5px solid #ccc;
  padding: 20px;
  border-radius: 5px;
  max-width: 500px;
  margin: 0 auto;
  background-image: url('https://4kwallpapers.com/images/walls/thumbs_3t/8324.png');
  background-size: cover;  
  background-position: center;  
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.box {
  transition: background-color 300ms;
}
.box.active {
  background-color: lightblue !important;
}
</style>
