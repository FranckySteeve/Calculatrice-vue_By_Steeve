<template>
    <div class="container">
        <div class="display">
            <input v-model="champ_vide" readonly class="champ" >
        </div>
        <div class="buttons">
            <button @click="clear" class="btn-operator-AC">AC</button>
            <button @click="deleteLast" class="btn-operator-DEL">DEL</button>
            <button @click="percentage" class="btn-operator">%</button>
            <button @click="append('/')" class="btn-operator">/</button>

            <button @click="append('7')" class="btn">7</button>
            <button @click="append('8')" class="btn">8</button>
            <button @click="append('9')" class="btn">9</button>
            <button @click="append('*')" class="btn-operator">*</button>

            <button @click="append('4')" class="btn">4</button>
            <button @click="append('5')" class="btn">5</button>
            <button @click="append('6')" class="btn">6</button>
            <button @click="append('-')" class="btn-operator">-</button>

            <button @click="append('1')" class="btn">1</button>
            <button @click="append('2')" class="btn">2</button>
            <button @click="append('3')" class="btn">3</button>
            <button @click="append('+')" class="btn-operator">+</button>

            <button @click="append('0')" class="btn">0</button>
            <button @click="append('00')" class="btn">00</button>
            <button @click="append('.')" class="btn">.</button>
            <button @click="calculate" class="btn-operator">=</button>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                champ_vide: ''
            }
        },
        methods: {
            clear() {
                this.champ_vide = '';
            },
            deleteLast() {
                this.champ_vide = this.champ_vide.slice(0, -1);
            },
            percentage() {
                if (this.champ_vide) {
                    this.champ_vide = `${parseFloat(this.champ_vide) / 100}`;
                }
            },
            append(character) {
                this.champ_vide += character;
            },
            calculate() {
                try {
                    this.champ_vide = eval(this.champ_vide).toString();
                } catch (e) {
                    this.champ_vide = 'Error';
                }
            }
        }
    }
</script>