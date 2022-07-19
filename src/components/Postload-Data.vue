<template>
    <form @submit.prevent="onSubmit">
        <ul>
            <li>Постнагрузка</li>
            <hr>
            <li><h5>ССС</h5></li>
            <li><input type="text" v-model="height" placeholder="дин-с/см5"></li>
            <li><h5>ИССС</h5></li>
            <li><input type="text" v-model="weight" placeholder="дин-с х м2/см5"></li>
            <li><h5>ЛСС</h5></li>
            <li><input type="text" v-model="ppt" placeholder="дин-с/см5"></li>
            <li><h5>ИЛСС</h5></li>
            <li><input type="text" v-model="sv" placeholder="дин-с х м2/см5"></li>
            <li><h5>срАД</h5></li>
            <li><input type="text" v-model="chss" placeholder="мм рт. ст."></li>
            <li><h5>ЛАср</h5></li>
            <li><input type="text" v-model="dzla" placeholder="мм рт. ст."></li>  
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
                    const postloadCalc = {
                        userId:1,
                        height: this.height,
                        weight: this.weight,
                        ppt: this.ppt,
                        sv: this.sv,
                        chss: this.chss,
                        dzla: this.dzla,
                    }
                    this.$emit('postload-calc', postloadCalc)
                    this.height = ''
                    this.weight = ''
                    this.ppt = ''
                    this.sv = ''
                    this.chss = ''
                    this.dzla = ''
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