<template>
  <div>
    <h1>Cifrado de transposición a través de Escitala</h1>
    <label for="mensaje">Ingrese el texto:</label>
    <input type="text" v-model="mensaje" />
    <label for="clave">Num. Columnas:</label>
    <input type="number" v-model="clave" />
    <button @click="cifrar">Cifrar</button>
    <button @click="descifrar">Descifrar</button>
    <div id="resultado">
      <p>Matriz:</p>
      <table>
        <tr v-for="fila in matriz">
          <td v-for="celda in fila">{{ celda }}</td>
        </tr>
      </table>
      <p v-if="resultadoCifrado">Resultado cifrado: {{ resultadoCifrado }}</p>
      <p v-if="resultadoDescifrado">Resultado descifrado: {{ resultadoDescifrado }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mensaje: "",
      clave: 0,
      matriz: [],
      resultadoCifrado: "",
      resultadoDescifrado: "",
    };
  },
  methods: {
    cifrar() {
      // Tu código de cifrado aquí
      // Asegúrate de utilizar this.mensaje y this.clave para obtener los datos del componente
      // Actualiza this.matriz y this.resultadoCifrado al final del cifrado
    },
    descifrar() {
      // Tu código de descifrado aquí
      // Asegúrate de utilizar this.mensaje y this.clave para obtener los datos del componente
      // Actualiza this.resultadoDescifrado al final del descifrado
    },
  },
};
</script>
