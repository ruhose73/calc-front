<template>
    <form @submit.prevent="onSubmit">
        <ul>
            <li>Входные данные</li>
            <hr>
            <li><h5>Рост</h5></li>
            <li><input type="text" v-model="height" placeholder="см"></li>
            <li><h5>Вес</h5></li>
            <li><input type="text" v-model="weight" placeholder="кг"></li>
            <li><h5>ППТ</h5></li>
            <li><input type="text" v-model="ppt" placeholder="кв.м"></li>
            <li><h5>СВ</h5></li>
            <li><input type="text" v-model="sv" placeholder="л/мин"></li>
            <li><h5>ЧСС</h5></li>
            <li><input type="text" v-model="chss" placeholder="уд/мин"></li>
            <li><h5>ДЗЛА</h5></li>
            <li><input type="text" v-model="dzla" placeholder="мм рт. ст."></li>
            <li><h5>АДср</h5></li>
            <li><input type="text" v-model="adsr" placeholder="мм рт. ст."></li> 
            <li><h5>ЛАср</h5></li>           
            <li><input type="text" v-model="lasr" placeholder="мм рт. ст."></li>
            <li><h5>ЦВД</h5></li>
            <li><input type="text" v-model="cvd" placeholder="мм рт. ст."></li>
            <li><h5>КДО</h5></li>
            <li><input type="text" v-model="kdo" placeholder="мл"></li>   
            <li><button type="submit">Вычисление</button></li>
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
                    const newCalc = {
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
                    this.$emit('new-calc', newCalc)
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
        margin-bottom:2%;
        margin-top:2%;
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