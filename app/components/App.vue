<template>
    <Page>
        <ActionBar title=""/>
        <StackLayout backgroundColor="black">
           <TextView editable="false" :text="atual" />   
            <GridLayout columns="90,90,90,90" rows="90,90,90,90,90" backgroundColor="black">
                <Button text="C" @tap="limpar" row="0" col="0" backgroundColor="#43b883"/>
                <Button text="/" @tap="dividir()" row="0" col="2" backgroundColor="#43b883"/>
                <Button text="X" @tap="multiplicar()" row="0" col="3" backgroundColor="#43b883"/>
                <Button text="7" @tap="junta('7')" row="1" col="0" backgroundColor="#43b883"/>
                <Button text="8" @tap="junta('8')" row="1" col="1" backgroundColor="#43b883"/>
                <Button text="9" @tap="junta('9')" row="1" col="2" backgroundColor="#43b883"/>
                <Button text="-" @tap="subtrair()" row="1" col="3" backgroundColor="#43b883"/>
                <Button text="4" @tap="junta('4')" row="2" col="0" backgroundColor="#43b883"/>
                <Button text="5" @tap="junta('5')" row="2" col="1" backgroundColor="#43b883"/>
                <Button text="6" @tap="junta('6')" row="2" col="2" backgroundColor="#43b883"/>
                <Button text="+" @tap="somar()" row="2" col="3" backgroundColor="#43b883"/>
                <Button text="1" @tap="junta('1')" row="3" col="0" backgroundColor="#43b883"/>
                <Button text="2" @tap="junta('2')" row="3" col="1" backgroundColor="#43b883"/>
                <Button text="3" @tap="junta('3')" row="3" col="2" backgroundColor="#43b883"/>
                <Button text="=" @tap="igual()" row="3" col="3" backgroundColor="#43b883"/>
                <Button text="0" @tap="junta('0')"  row="4" col="1" backgroundColor="#43b883" />
                
            </GridLayout>
        </StackLayout>
    </Page>
</template>

<script>
  export default {
    data() {
      return {
        anterior: null,
        atual: '',
        operacao: null,
        operacaoClicked: false,
      }
    },
    methods: {
        limpar() {
            this.atual = ' ';
        },

        junta(num) {
            if(this.operacaoClicked){
                this.atual = '';
                this.operacaoClicked = false;
            }
            this.atual = this.atual + num;
        },

        defineAnterior() {
            this.anterior = this.atual;
            this.operacaoClicked = true;
        },

        dividir() {
            this.operacao = (a,b) => b / a;
            this.defineAnterior();
        },

        multiplicar() {
            this.operacao = (a,b) => a * b;
            this.defineAnterior();
        },

        subtrair() {
            this.operacao = (a,b) => b - a;
            this.defineAnterior();
        },

        somar() {
            this.operacao = (a,b) => a + b;
            this.defineAnterior();
        },

        igual(){
            this.atual = `${this.operacao(parseFloat(this.atual), parseFloat(this.anterior))}`;
            this.anterior = null; 
        }
    }
   
  }
</script>

<style scoped>
    ActionBar {
        background-color: #233cca;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }

    TextView {
        color: white;
        text-align: center;
    }
    

</style>
