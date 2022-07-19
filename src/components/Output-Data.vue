<template>
    <form @submit.prevent="onSubmit">
        <ul>
            <li>Вывод</li>
            <hr>
            <li><h5>СВ</h5></li>
            <li><input type="text" v-model="height" placeholder="л/мин"></li>
            <li><h5>СИ</h5></li>
            <li><input type="text" v-model="weight" placeholder="л/мин/ м2"></li>
            <li><h5>УО</h5></li>
            <li><input type="text" v-model="ppt" placeholder="мл"></li>
            <li><h5>ИУО</h5></li>
            <li><input type="text" v-model="sv" placeholder="мл/ м2"></li>
            <li><h5>ЧСС</h5></li>
            <li><input type="text" v-model="chss" placeholder="уд/мин"></li>
        </ul>
    </form>
</template>

<script>

export default {

    data(){
        return {
            height: '', 
            weight: '',
            ppt: '',
            sv: '',
            chss: '',
            dzla: '',
            adsr: '',
            lasr: '',
            cvd: '',
            kdo: ''
        }
    },

    methods: {
        onSubmit() {
            if(this.height.trim() || this.weight.trim() ||this.ppt.trim()
                 || this.sv.trim() || this.chss.trim() || this.dzla.trim()
                 || this.adsr.trim() || this.lasr.trim() || this.cvd.trim() 
                 || this.kdo.trim()) {
                    const outputCalc = {
                        userId:1,
                        height: this.height,
                        weight: this.weight,
                        ppt: this.ppt,
                        sv: this.sv,
                        chss: this.chss,
                    }
                    this.$emit('output-calc', outputCalc)
                    this.height = ''
                    this.weight = ''
                    this.ppt = ''
                    this.sv = ''
                    this.chss = ''
                 }
        }
    }
}

</script>


<style scoped>
    form {
        display:flex;
        width:fit-content;
        border: 1px solid #ccc;
        padding-top: 2%;
        padding-bottom: 2%;
        padding-right: 3%;
        }

    input {
        width: 100%;
        margin-bottom:2%;
        }

    button {    
        width: 100%;
        justify-content: center;
    }

    li {
    display: flex;
    justify-content: space-between;
    min-width: 100px;
  }

    ul {
    list-style: none;
    margin-top:2%;
    margin-bottom:2%;
  }

    h5 {
    margin-top:1%;
    margin-right:2%;
    margin-bottom:1%;
    font-style: normal;
    font-weight: normal;
  }



</style>