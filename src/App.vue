<script>
export default {
  name: 'App',

  data() {
    return {
      colorFondo: '',
      colorLetra: '',
      texto: '',
      mostrar: true,
      borde: 0,
      tipografia: ["comic sans ms", "Verdana", "Times New Roman", "Courier New"],
      tipographia: '',
      opacidad: false,
      cuadro: true,
      tamañoLetra: '',
    }
  }
}
</script>

<template>
  <div>
    <div class="row">
      <div class="col-6">
        <form>
          <label>Color de fondo</label><br>
          <input type="text" v-model="colorFondo">
          <hr>
          <label>Color de texto</label><br>
          <input type="text" v-model="colorLetra">
          <hr>
          <label> Mostrar texto </label>
          <input type="checkbox" v-model="mostrar">
          <hr>
          <label>Borde</label><br>
          <input type="range" v-model="borde" min="0" max="100" step="1">
          <hr>
          <label>Contenido textual</label><br>
          <textarea name="" id="" v-model="texto"></textarea><br>
          <hr>
          <label>Tipografía</label><br>
          <select v-model="tipographia">
            <option disabled value="">Elija una opción</option>
            <option v-for="tipo in tipografia">{{ tipo }}</option>
          </select>
          <hr>
          <label>Opaco</label>
          <input type="checkbox" v-model="opacidad"><br>
          <hr>
          <div>
            <label>Tamaño de letra</label><br>

            <input v-model="tamañoLetra" type="radio" id="tamañoLetra1" value="pequeño">
            <label for="tamañoLetra1">Pequeño</label>
            <input v-model="tamañoLetra" type="radio" id="tamañoLetra2" value="mediano">
            <label for="tamañoLetra2">Mediano</label>
            <input v-model="tamañoLetra" type="radio" id="tamañoLetra3" value="grande">
            <label for="tamañoLetra3">Grande</label>
          </div>
        </form>
      </div>

      <div class="col-6">
        <div :class="{ opacidad: opacidad, cuadro: cuadro }"
          :style="{ backgroundColor: colorFondo, color: colorLetra, borderRadius: borde + 'px' }">
          <h2 v-if="mostrar"
            :class="{ pequeño: tamañoLetra == 'pequeño', mediano: tamañoLetra == 'mediano', grande: tamañoLetra == 'grande' }"
            :style="{ fontFamily: tipographia }">{{ texto }}</h2>
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped>
.row {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0px;
}

form {
  width: 80%;
  display: block;
  margin: 30px;
  padding: 30px;
  border-radius: 5px;
  background-color: green;

}

label {
  color: white;
  margin-right: 10px;
}

input text {
  width: 100%;
}

textarea {
  width: 100%;
}

.cuadro {
  display: flex;
  border: 1px solid black;
  justify-content: center;
  align-items: center;
  width: 80%;
  height: 300px;
}

.opacidad {
  opacity: 50%;
}

.pequeño {
  font-size: 12px;
}

.mediano {
  font-size: 24px;
}

.grande {
  font-size: 48px;
}
</style>
