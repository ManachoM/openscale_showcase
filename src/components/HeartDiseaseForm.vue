<template>
  <cv-form @submit.prevent="testing">
    <br>
    <cv-number-input label="Edad"
                      name = "edad"
                      value="18"
                      min="0"
                      max="80"
                      step="1"
                     v-model="age"
                      ></cv-number-input>
    <br>
    <cv-select label="Sexo"
                name = "sexo"
                v-model="sex"
               >
      <cv-select-option value="0">Mujer</cv-select-option>
      <cv-select-option value="1">Hombre</cv-select-option>
    </cv-select>
    <br>
    <cv-number-input label="Tipo de dolor de pecho"
                     min="0"
                     name = "tipo"
                     max="3"
                     step="1"
                     v-model="cp"
                     ></cv-number-input>
    <br>
    <cv-number-input label="Presión sanguínea en admisión al hospital [mmHg]"
                    name = "presion"
                     min="90"
                     max="220"
                     step="1"
                     v-model="trestbps"
                    ></cv-number-input>
    <br>
    <cv-number-input label="Colesterol sérico [mg/dl]"
                    name = "col"
                     min="100"
                     max="600"
                     step="1"
                     v-model="chol"
                     ></cv-number-input>
    <br>
    <cv-checkbox id = "gluc"
                 label="Glucemia en ayuna (> 120 [mg/dl])"
                 v-model="fbs"></cv-checkbox>
    <br>
    <cv-number-input label="Resultados de electrocardiográfico en reposo"
                     min="0"
                     max="2"
                     step="1"
                     name = "resElec"
                     v-model="restecg"
                     ></cv-number-input>
    <br>
    <cv-number-input label="HR máximo"
                     min="50"
                     max="220"
                     step="1"
                     name = "hr"
                     v-model="thalac"
                     ></cv-number-input>
    <br>
    <cv-checkbox
                  id = "angina"
                  label="Angina producida por ejercicio"
                  v-model="exang"
                  ></cv-checkbox>
    <br>
    <cv-number-input label="Depresión ST inducida por ejercicio relativo al reposo"
                     value="0"
                     min="0"
                     max="7.0"
                     step="0.1"
                     name = "dep"
                     v-model="oldpeak"
                     ></cv-number-input>
    <br>
    <cv-button type="submit">Predecir</cv-button>
    <div>
      <cv-data-table :columns="columns" :data="data" auto-width/>
    </div>

  </cv-form>
</template>

<script>

import axios from 'axios';

export default {
  name: "HeartDiseaseForm",
  data: ()=>{
        return {
          age: 0,
          sex: "",
          cp: 0,
          trestbps: 90,
          chol: 120,
          fbs: false,
          restecg: 1,
          thalac: 60,
          exang: false,
          oldpeak: 0,
          columns: [""],
          data: []
        }
      },
      methods:{
        testing(elem){

          let elementos = elem.target.elements;

          axios.get("http://127.0.0.1:3000/",{
            params:{
              age: elementos.edad.value,
              sex: elementos.sexo.value,
              cp: elementos.tipo.value,
              trestbps: elementos.presion.value,
              chol: elementos.col.value,
              fbs: elementos.gluc.getAttribute("aria-checked") === "false"
                  || elementos.gluc.getAttribute("aria-checked") === "0"  ? 0 : 1,
              restecg: elementos.resElec.value,
              thalac: elementos.hr.value,
              exang: elementos.angina.getAttribute("aria-checked") === "false"
                    || elementos.angina.getAttribute("aria-checked") === "0"  ? 0 : 1,
              oldpeak: elementos.dep.value
              }
            }
          )

          .then( async (response) => {
            let JSONdata = JSON.parse(Object.values(response.data)).predictions[0];

            this.data = [[JSONdata.values[0][1][0],JSONdata.values[0][1][1]]];
            this.columns = ["Prediccion", "Probabilidad"];
          })
          .catch(error => {
            console.error(error);
          });
        }
      }
}
</script>

<style scoped>

</style>