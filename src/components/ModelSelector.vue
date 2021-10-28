<template>
  <cv-tabs container=true
            aria-label="etiqueta pestaña de navegación">
    <cv-tab label="Enfermedad Cardíaca" id="0">
      <HeartDiseaseForm/>
    </cv-tab>

    <cv-tab label="Crédito alemán" id="1" class="content-tab">
      <GermanCreditScoreForm/>
    </cv-tab>
  </cv-tabs>
</template>

<script>
import HeartDiseaseForm from "@/components/HeartDiseaseForm";
import GermanCreditScoreForm from "@/components/GermanCreditScoreForm";
export default {
  components: {GermanCreditScoreForm, HeartDiseaseForm},
  name: "ModelSelector"
}
</script>

<style scoped>
  .content-tab{
    width: 100%;
    background: white;
    align-items: center;
    align-content: center;
    align-self: center;
  }
</style>