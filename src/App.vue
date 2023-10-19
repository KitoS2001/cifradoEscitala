<template>
  <div>
    <h1>Cifrado Escítala</h1>
    <label for="mensaje">Ingrese el texto:</label>
    <input type="text" v-model="mensaje" /><br>
    <label for="clave">Columnas:</label>
    <input type="number" v-model="clave" /><br>
    <button @click="cifrar">Cifrar</button>
    <button @click="descifrar">Descifrar</button>
    <div id="resultado">
      <p>Matriz:</p>
      <table>
        <tr v-for="fila in matriz">
          <td v-for="celda in fila">{{ celda }}</td>
        </tr>
      </table>
      <p v-if="resultadoCifrado">Cifrado: {{ resultadoCifrado }}</p>
      <p v-if="resultadoDescifrado">Descifrado: {{ resultadoDescifrado }}</p>
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
      let mensaje = this.mensaje;
      let columnas = this.clave;
      let resultado = '';
      let matriz = [];

      for (let i = 0; i < Math.ceil(mensaje.length / columnas); i++) {
        matriz.push([]);
        for (let j = 0; j < columnas; j++) {
          matriz[i].push(' ');
        }
      }
      let cont = 0;

      for (let i = 0; i < Math.ceil(mensaje.length / columnas); i++) {
        for (let j = 0; j < columnas; j++) {
          matriz[i][j] = mensaje[cont] || ' ';
          cont++;
        }
      }

      for (let i = 0; i < columnas; i++) {
        for (let j = 0; j < Math.ceil(mensaje.length / columnas); j++) {
          if (matriz[j][i] !== ' ') {
            resultado += matriz[j][i];
          } else {
            resultado += ' ';
          }
        }
      }

      this.matriz = matriz;
      this.resultadoCifrado = resultado;
    },
    descifrar() {
      let mensaje = this.mensaje;
      let columnas = this.clave;
      let resultado = '';
      let cont = 0;
      let matriz = [];

      for (let i = 0; i < Math.ceil(mensaje.length / columnas); i++) {
        matriz.push([]);
        for (let j = 0; j < columnas; j++) {
          matriz[i].push(' ');
        }
      }

      for (let i = 0; i < columnas; i++) {
        for (let j = 0; j < Math.ceil(mensaje.length / columnas); j++) {
          matriz[j][i] = mensaje[cont] || ' ';
          cont++;
        }
      }

      for (let i = 0; i < Math.ceil(mensaje.length / columnas); i++) {
        for (let j = 0; j < columnas; j++) {
          resultado += matriz[i][j];
        }
      }

      this.matriz = matriz;
      this.resultadoDescifrado = resultado;
    },
  },
};
</script>
<style>
.escitala-container {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
}

.input-container {
  margin-bottom: 10px;
}

.label {
  display: block;
  margin-bottom: 5px;
}

.input {
  width: 100%;
  padding: 5px;
  margin-bottom: 10px;
}

.button-container {
  margin: 10px 0;
}

.btn-cifrar, .btn-descifrar {
  padding: 10px 20px;
  margin: 0 5px;
  background-color: #3498db;
  color: #fff;
  border: none;
  cursor: pointer;
}

.btn-cifrar:hover, .btn-descifrar:hover {
  background-color: #2980b9;
}

.resultado {
  margin-top: 20px;
}

table {
  border-collapse: collapse;
  width: 100%;
}

table, td, th {
  border: 1px solid #ddd;
}

td, th {
  padding: 8px;
  text-align: center;
}

.resultado-cifrado, .resultado-descifrado {
  margin-top: 10px;
  font-weight: bold;
}
</style>
