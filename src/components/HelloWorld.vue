<template>
<div class="sample">
<h1>OpenScale and AutoAI Showcase</h1>
  <p>Seleccione un modelo de prueba e ingrese datos para producir una predicción</p>
  <div class="content">
    <cv-tile kind="standard" light=true>
      <ModelSelector></ModelSelector>
    </cv-tile>
  </div>
</div>
</template>

<script>
import ModelSelector from "@/components/ModelSelector";
export default {
  name: 'HelloWorld',
  components: {ModelSelector},
  data() {
    return {
      yourName: '',
      visible: false,
    };
  },
  methods: {
    onClick() {
      this.visible = true;
    },
    modalClosed() {
      this.visible = false;
    },
  },
};
</script>

<style>
.sample {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  max-width: 600px;
  margin: 5% auto;
}
.content{
  width: 100%;
  align-content: center;
  align-items: center;
  margin: 10px;
}
.cv-text-input {
  margin: 30px 0;
}
</style>