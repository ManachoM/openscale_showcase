<template>
<cv-form @submit="actionSubmit">
  <br>
  <cv-select label="Checking Status" v-model="CheckingStatus">
    <cv-select-option value="less_0"> Menor a 0</cv-select-option>
    <cv-select-option value="0_to_200">Entre 0 y 200</cv-select-option>
    <cv-select-option value="greater_200">Mayor a 200</cv-select-option>
    <cv-select-option value="no_checking">Sin chequera</cv-select-option>
  </cv-select>
  <br>
  <cv-number-input label="Duración del préstamo"
                   value="LoanDuration"
                   min="3"
                   max="36"
                   step="1"
                   v-model="LoanDuration"
                   ></cv-number-input>
  <br>
  <cv-select label="Historial de crédito" v-model="CreditHistory">
    <cv-select-option value="all_credits_paid_back">Todo los créditos pagados</cv-select-option>
    <cv-select-option value="credits_paid_to_date">Todos los pagos al día</cv-select-option>
    <cv-select-option value="no_credits">Sin créditos</cv-select-option>
    <cv-select-option value="outstanding_credit">Crédito Excepcional</cv-select-option>
    <cv-select-option value="prior_payments_delayed">Con pagos atrasados</cv-select-option>
  </cv-select>
  <br>
  <cv-select label="Propósito del crédito" v-model="LoanPurpose">
    <cv-select-option value="appliances">Accesorios</cv-select-option>
    <cv-select-option value="business">Negocios</cv-select-option>
    <cv-select-option value="car_new">Auto nuevo</cv-select-option>
    <cv-select-option value="car_used">Auto usado</cv-select-option>
    <cv-select-option value="education">Educación</cv-select-option>
    <cv-select-option value="furniture">Muebles</cv-select-option>
    <cv-select-option value="other">Otros</cv-select-option>
    <cv-select-option value="radio_tv">Radio o TV</cv-select-option>
    <cv-select-option value="repairs">Reparaciones</cv-select-option>
    <cv-select-option value="retraining">Retraining</cv-select-option>
    <cv-select-option value="vacation">Vacaciones</cv-select-option>
  </cv-select>
  <br>
  <cv-number-input label="Monto del crédito"
                   value=""
                   min="0"
                   max="10000"
                   step="100"
                   v-model="LoanAmount"
                   ></cv-number-input>
  <br>
  <cv-select label="Ahorros existentes" v-model="ExistingSavings">
    <cv-select-option value="less_100">Menor a 100</cv-select-option>
    <cv-select-option value="100_to_500">Entre 100 y 500</cv-select-option>
    <cv-select-option value="500_to_1000">Entre 500 y 1000</cv-select-option>
    <cv-select-option value="greater_1000">Mayor a 1000</cv-select-option>
    <cv-select-option value="unknown">Desconocido</cv-select-option>
  </cv-select>
  <br>
  <cv-select label="Duración del empleo" v-model="EmploymentDuration">
    <cv-select-option value="1_to_4">De 1 a 4 meses</cv-select-option>
    <cv-select-option value="4_to_7">De 4 a 7 meses</cv-select-option>
    <cv-select-option value="less_1">Menor a 1 mes</cv-select-option>
    <cv-select-option value="greater_7">Mayor a 7 meses</cv-select-option>
    <cv-select-option value="unemployed">Desempleado(a)</cv-select-option>
  </cv-select>
  <br>
  <cv-number-input label="Porcentaje instalación"
                   min="1"
                   max="8"
                   step="1"
                   v-model="InstallmentPercent"></cv-number-input>
  <br>
  <cv-select label="Sexo" v-model="Sex">
    <cv-select-option value="male">Hombre</cv-select-option>
    <cv-select-option value="female">Mujer</cv-select-option>
  </cv-select>
  <br>
  <cv-select label="OthersOnLoan" v-model="OthersOnLoan">
    <cv-select-option value="none">Ninguno</cv-select-option>
    <cv-select-option value="guarantos">Garantía/Aval</cv-select-option>
    <cv-select-option value="co-applicant">Co-postulante</cv-select-option>
  </cv-select>
  <br>
  <cv-number-input label="Duración de residencia actual"
                   min="3"
                   max="240"
                   step="1"
                   v-model="CurrentResidenceDuration"></cv-number-input>
  <br>
  <cv-select label="Posee activos" v-model="OwnsProperty">
    <cv-select-option value="real_estate">Inmuebles</cv-select-option>
    <cv-select-option value="car_other">Vehículos u Otros</cv-select-option>
    <cv-select-option value="savings_insurance">Ahorros/Seguros</cv-select-option>
    <cv-select-option value="unknown">Desconocido</cv-select-option>
  </cv-select>
  <br>
  <cv-number-input label="Edad"
                   min="18"
                   max="80"
                   step="1"
                   v-model="Age"
                   ></cv-number-input>
  <br>
  <cv-select label="Plan de instalación" v-model="InstallmentPlans">
    <cv-select-option value="none">Ninguno</cv-select-option>
    <cv-select-option value="bank">Banco</cv-select-option>
    <cv-select-option value="stores">Tiendas</cv-select-option>
  </cv-select>
  <br>
  <cv-select label="Vivienda" v-model="Housing">
    <cv-select-option value="free">Gratis</cv-select-option>
    <cv-select-option value="rent">Arriendo</cv-select-option>
    <cv-select-option value="own">Propia</cv-select-option>
  </cv-select>
  <br>
  <cv-number-input label="Cantidad de créditos vigentes"
                   min="0"
                   max="10"
                   step="1"
                   v-model="ExistingCreditsCount"
                   ></cv-number-input>
  <br>
  <cv-select label="Tipo de trabajo" v-model="Job">
    <cv-select-option value="skilled">Profesional</cv-select-option>
    <cv-select-option value="unskilled">Mano de obra</cv-select-option>
    <cv-select-option value="unemployed">Desempleado(a)</cv-select-option>
    <cv-select-option value="management_self-employed">Administración/Independiente</cv-select-option>
  </cv-select>
  <br>
  <cv-number-input label="Cargas"
                   min="0"
                   max="10"
                   step="1"
                    v-model="Dependents"></cv-number-input>
  <br>
  <cv-checkbox value="false"
               label="Teléfono"
               v-model="Telephone"
               ></cv-checkbox>
  <br>
  <cv-checkbox value="false"
               label="Trabajador extranjero"
                v-model="ForeignWorker"></cv-checkbox>
  <br>
  <cv-button>Predecir</cv-button>

</cv-form>
</template>

<script>
export default {
  name: "GermanCreditScoreForm",
  data: ()=> {
    return {
      CheckingStatus: "",
      LoanDuration: 0,
      CreditHistory: "no_credits",
      LoanPurpose: "other",
      LoanAmount: 0,
      ExistingSavings: "",
      EmploymentDuration: "unemployed",
      InstallmentPercent: 0,
      Sex: "",
      OthersOnLoan: "none",
      CurrentResidenceDuration: 0,
      OwnsProperty: "",
      Age: 18,
      InstallmentPlans: "none",
      Housing: "rent",
      ExistingCreditsCount: 0,
      Job: "unemployed",
      Dependents: 0,
      Telephone: false,
      ForeignWorker: false
    }
  }
}
</script>

<style scoped>

</style>