<script>
export default {
  data() {
    return {
      backgroundColor: '',
      textColor: '',
      showText: true,
      borderRadius: '',
      textContent: 'Awesome Vue.js',
      fontSelect: 'normal',
      fontValue: ['normal', 'italic'],
      opacity: '',
      fontSize: 'medium',
      showContent: true
    }
  }
}
</script>

<template>
  <div class="container">
    <form class="form">
      <div class="flex">
        <label for="color">Color de fondo</label>
        <input type="background" v-model="backgroundColor" />
      </div>
      <div class="flex">
        <label for="text-color">Color de texto</label>
        <input type="text-color" v-model="textColor" />
      </div>
      <div class="flex">
        <label> Mostrar texto<input type="checkbox" v-model="showText" /> </label>
      </div>
      <div class="flex">
        <label for="border">Borde</label>
        <input v-model="borderRadius" type="range" min="0" max="50" />
      </div>
      <div class="flex">
        <label for="textContent">Contenido Textual</label>
        <input v-model="textContent" />
      </div>
      <div class="flex">
        <label for="fontType">Tipografía</label>
        <select name="type" id="fontType" v-model="fontSelect">
          <option v-for="fontType in fontValue" :key="fontType" :value="fontType">
            {{ fontType }}
          </option>
        </select>
      </div>
      <div class="flex">
        <label> Opaco <input type="checkbox" v-model="opacity" /> </label>
      </div>
      <div>
        <div class="flex">
          <label>Tamaño de letra:</label>
        </div>
        <input type="radio" v-model="fontSize" value="small" /> Pequeño
        <input type="radio" v-model="fontSize" value="medium" /> Mediano
        <input type="radio" v-model="fontSize" value="large" /> Grande
      </div>
    </form>
    <div
      class="content"
      v-show="showContent"
      :style="{
        backgroundColor: backgroundColor,
        color: textColor,
        borderRadius: `${borderRadius}%`,
        fontStyle: fontSelect,
        opacity: opacity ? 0.5 : 1,
        fontSize: fontSize === 'small' ? '12px' : fontSize === 'medium' ? '16px' : '20px'
      }"
    >
      <span v-if="showText">{{ textContent }}</span>
    </div>
  </div>
</template>

<style scoped>
.form {
  width: 300px;
  float: left;
  padding: 20px;
  background-color: #2f4f4f;
  color: white;
}
.content {
  width: 200px;
  height: 200px;
  margin-left: 350px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  border-radius: 25%;
}

.flex {
  display: flex;
  flex-direction: column;
  padding-bottom: 10px;
}
</style>
