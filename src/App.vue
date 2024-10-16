<template>
  <div id="app">
    <h1>Desafio Templates y Rendering en Vue</h1>
    <div>
      <form>
        <ul>
          <div>
            <label for="colorFondo"> Color de Fondo</label>
            <select name="colorFondo" id="colorFondo" v-model="colorFondo">
              <option value="green">VELDE</option>
              <option value="purple">MOLADO</option>
              <option value="blue">AZUL</option>
            </select>
            <!-- <input type="color" id="colorFondo" v-model="colorFondo" /> -->
          </div>

          <div>
            <label for="colorTexto"> Color de Texto</label>
            <select name="color" id="colorTexto" v-model="colorTexto">
              <option value="black"> Negro</option>
              <option value="white"> Blanco</option>
              <option value="Yellow"> Amarelo</option>
            <!-- <input type="color" id="colorTexto" v-model="colorTexto" /> -->
          </select>
          </div>

          <div>
            <label for="mostrarTexto">¿¿¿Mostrar Texto???</label>
            <input type="checkbox" id="mostrarTexto" v-model="mostrarTexto" />
          </div>

          <div>
            <label for="bordeTexto"></label>
            <input
              type="range"
              id="bordeTexto"
              min="0"
              max="100"
              v-model="bordeTexto"
            />
          </div>

          <div>
            <label for="contenidoTexto">Contenido del Texto</label>
            <input
              type="text"
              name=""
              id="contenidoTexto"
              v-model="contenidoTexto"
            />
          </div>

          <div>
            <label for="tipoLetra"> Tipografia </label>
            <select id="tipoLetra" v-model="estiloLetra">
              <option value="Normal">Normaaaaal</option>
              <option value="Italic">Cursivaaaaaaa</option>
            </select>
          </div>

          <div>
            <label for="opacidad"> Opacidad</label>
            <input
              type="range"
              id="opacidad"
              min="0"
              max="1"
              step="0.01"
              v-model="opacidadTexto"
            />
          </div>

          <div>
            <label for="tipografia">Tipografia</label>
            <select id="tipografia" v-model="letraTipo">
              <option disabled value="">Seleccione...</option>
              <option
                v-for="tipografia in tipografias"
                :key="tipografia.id"
                :value="tipografia.font"
              >
                {{ tipografia.font }}
              </option>
            </select>
          </div>

          <div>
            <li>
              <label>tamaño del texto</label>
              <input type="radio" value="textPequenio" v-model="tamanioTexto" />
              pequenio
              <input type="radio" value="textMediano" v-model="tamanioTexto" />
              mediano
              <input type="radio" value="textGrande" v-model="tamanioTexto" />
              Grande
            </li>
          </div>

          <div class="col-12 col-md-6 Caja">
            <div
              class="cajaTexto"
              :style="{
                backgroundColor: colorFondo,
                borderRadius: bordeTexto + 'px',
                opacity: opacidadTexto,
              }"
            >
              <span
                :class="{
                  textPequenio: tamanioTexto == 'textPequenio',
                  textMediano: tamanioTexto == 'textMediano',
                  textGrande: tamanioTexto == 'textGrande',
                }"
                :style="{
                  color: colorTexto,
                  fontStyle: estiloLetra,
                  fontFamily: letraTipo,
                }"
                v-show="mostrarTexto"
              >
                {{ contenidoTexto }}
              </span>
            </div>
          </div>
        </ul>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      colorFondo: "",
      colorTexto: "",
      mostrarTexto: true,
      bordeTexto: 0,
      contenidoTexto: "",
      estiloLetra: "normal",
      opacidadTexto: 1,
      letraTipo: "",
      tamanioTexto: "",
      tipografias: [
        { id: 1, font: "Arial" },
        { id: 2, font: "Lucida Console" },
      ],
    };
  },
};
</script>

<style>
.cajaTexto {
  margin-top: 50px;
  border: 3px solid black;
  width: 500px;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.textPequenio {
font-size: 15px
}

.textMediano{
  font-size: 25px;
}

.textGrande{
  font-size: 35px;
}
</style>
