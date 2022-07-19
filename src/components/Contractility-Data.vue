<template>
    <form @submit.prevent="onSubmit">
        <ul>
            <li>Сократимость</li>
            <hr>
            <li><h5>УРЛД</h5></li>
            <li><input type="text" v-model="urld" placeholder="г х м"></li>
            <li><h5>ИУРЛЖ</h5></li>
            <li><input type="text" v-model="weight" placeholder="г х м/ м2"></li>
            <li><h5>РЛК</h5></li>
            <li><input type="text" v-model="ppt" placeholder="кг х м"></li>
            <li><h5>ИРЛК</h5></li>
            <li><input type="text" v-model="sv" placeholder="кг х м/ м2"></li>
            <li><h5>УРПЖ</h5></li>
            <li><input type="text" v-model="chss" placeholder="г х м"></li>
            <li><h5>ИУРПЖ</h5></li>
            <li><input type="text" v-model="dzla" placeholder="г х м/ м2"></li>
            <li><h5>РПК</h5></li>
            <li><input type="text" v-model="adsr" placeholder="кг х м"></li>
            <li><h5>ИРПК</h5></li>
            <li><input type="text" v-model="lasr" placeholder="кг х м/ м2"></li>
            <li><h5>ФВ</h5></li>
            <li><input type="text" v-model="cvd" placeholder="%"></li>
            <li><h5>КСО</h5></li>
            <li><input type="text" v-model="kdo" placeholder="мл"></li>   
            <li><h5>ИКСО</h5></li>
            <li><input type="text" v-model="o" placeholder="мл/ м2"></li>  

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
            kdo: '',
            o:''
        }
    },

    methods: {
        onSubmit() {
            if(this.height.trim() || this.weight.trim() ||this.ppt.trim()
                 || this.sv.trim() || this.chss.trim() || this.dzla.trim()
                 || this.adsr.trim() || this.lasr.trim() || this.cvd.trim() 
                 || this.kdo.trim()) {
                    const contractilityCalc = {
                        userId:1,
                        height: this.height,
                        weight: this.weight,
                        ppt: this.ppt,
                        sv: this.sv,
                        chss: this.chss,
                        dzla: this.dzla,
                        adsr: this.adsr,
                        lasr: this.lasr,
                        cvd: this.cvd,
                        kdo: this.kdo,
                    }
                    this.$emit('contractility-Calc', contractilityCalc)
                    this.height = ''
                    this.weight = ''
                    this.ppt = ''
                    this.sv = ''
                    this.chss = ''
                    this.dzla = ''
                    this.adsr = ''
                    this.lasr = ''
                    this.cvd = ''
                    this.kdo = ''
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