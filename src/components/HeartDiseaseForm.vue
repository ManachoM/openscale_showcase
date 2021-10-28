<template>
  <cv-form @submit="console.log('oli')">
    <br>
    <cv-number-input label="Edad"
                      value="18"
                      min="0"
                      max="80"
                      step="1"
                     v-model="age"
                      ></cv-number-input>
    <br>
    <cv-select label="Sexo"
               v-model="sex"
               >
      <cv-select-option value="0">Mujer</cv-select-option>
      <cv-select-option value="1">Hombre</cv-select-option>
    </cv-select>
    <br>
    <cv-number-input label="Tipo de dolor de pecho"
                     min="0"
                     max="3"
                     step="1"
                     v-model="cp"
                     ></cv-number-input>
    <br>
    <cv-number-input label="Presión sanguínea en admisión al hospital [mmHg]"
                     min="90"
                     max="220"
                     step="1"
                     v-model="trestbps"
                    ></cv-number-input>
    <br>
    <cv-number-input label="Colesterol sérico [mg/dl]"
                     min="100"
                     max="600"
                     step="1"
                     v-model="chol"
                     ></cv-number-input>
    <br>
    <cv-checkbox value="false"
                 label="Glucemia en ayuna (> 120 [mg/dl])"
                  v-model="fbs"></cv-checkbox>
    <br>
    <cv-number-input label="Resultados de electrocardiográfico en reposo"
                     min="0"
                     max="2"
                     step="1"
                     v-model="restecg"
                     ></cv-number-input>
    <br>
    <cv-number-input label="HR máximo"
                     min="50"
                     max="220"
                     step="1"
                     v-model="thalac"
                     ></cv-number-input>
    <br>
    <cv-checkbox value="false"
                  label="Angina producida por ejercicio"
                  v-model="exang"></cv-checkbox>
    <br>
    <cv-number-input label="Depresión ST inducida por ejercicio relativo al reposo"
                     value="0"
                     min="0"
                     max="7.0"
                     step="0.1"
                     v-model="oldpeak"
                     ></cv-number-input>
    <br>
    <cv-button>Predecir</cv-button>



  </cv-form>
</template>

<script>
export default {
  name: "HeartDiseaseForm",
  data: ()=>{
        return {
          age: 0,
          sex: "",
          cp: 0,
          trestbps: 90,
          chol: 120,
          fbs: 0,
          restecg: 1,
          thalac: 60,
          exang: false,
          oldpeak: 0
        }
      }
}
</script>

<style scoped>

</style>