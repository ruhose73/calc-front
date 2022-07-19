<template>
  <div>
    <h1>Калькулятор расчета гемодинамики</h1>
    <hr>
    <container>
    <InputData @new-calc="newCalc"/>
    <OutputData @output-calc="outputCalc"/>
    <PreloadData @preload-calc="preloadCalc"/>
    <PostloadData @postload-calc="postloadCalc"/>
    <ContractilityData @contractility-calc="contractilityCalc"/>
    </container>

  </div>
</template>

<script>
import InputData from '@/components/Input-Data'
import OutputData from '@/components/Output-Data'
import PreloadData from '@/components/Preload-Data'
import PostloadData from '@/components/Postload-Data'
import ContractilityData from '@/components/Contractility-Data'
export default {
  name: 'App',
  components: {
    InputData,
    OutputData,
    PreloadData,
    PostloadData,
    ContractilityData
  },

  methods: {
    newCalc(newCalculation) {
      console.log(newCalculation)
      

    const requestOptions = {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(newCalculation)
    };
    fetch("http://localhost:5000/calculator/calc/new", requestOptions)
      .then(response => response.json())
      .then(data => (this.postId = data.id));
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

  container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  }

  h1 {
      margin-bottom:1%;
      font-style: bold;
      font-size: auto;
      justify-content: left;
  }

  hr {
    margin-bottom: 1%;
  }

</style>
