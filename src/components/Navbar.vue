<template>
    <nav class="navbar"
        v-bind:style="{ backgroundColor: (contrasteValidator.regular ? '#e3e4e8' : 
                            contrasteValidator.altocontrst ? 'black' : '#1c1b17'),
                        color: (contrasteValidator.regular ? 'black' : 
                            contrasteValidator.altocontrst ? 'white' : 'white'),
                        fontSize: (tamanhoFonte.regular ? 16 + 'px':
                            tamanhoFonte.mais1 ? 20 + 'px' : 24 + 'px'), 
                        letterSpacing: (espacoFonte.regular ? 'normal' : 
                            espacoFonte.mais1 ? 1 + 'px' : 2 + 'px') }">
        <div class="container-fluid">
            <a href="#" class="navbar-bran">
                UFGDNET
            </a>
            <form class="d-flex">
                <input class="form-control me-2" type="search" placeholder="Pesquise sistema por titulo ou nome"
                         aria-label="Search" v-bind:style="{
                        fontSize: (tamanhoFonte.regular ? 16 + 'px':
                            tamanhoFonte.mais1 ? 20 + 'px' : 24 + 'px'), 
                        letterSpacing: (espacoFonte.regular ? 'normal' : 
                            espacoFonte.mais1 ? 1 + 'px' : 2 + 'px') }">
                <button class="btn btn-outline-success" type="submit" v-bind:style="{
                        fontSize: (tamanhoFonte.regular ? 16 + 'px':
                            tamanhoFonte.mais1 ? 20 + 'px' : 24 + 'px'), 
                        letterSpacing: (espacoFonte.regular ? 'normal' : 
                            espacoFonte.mais1 ? 1 + 'px' : 2 + 'px') }">
                    Search
                </button>
            </form>
            <div class="dropdown dropstart">
                <button class="btn btn-primary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" 
                        aria-expanded="false" data-bs-auto-close="false" v-bind:style="{
                        fontSize: (tamanhoFonte.regular ? 16 + 'px':
                            tamanhoFonte.mais1 ? 20 + 'px' : 24 + 'px'), 
                        letterSpacing: (espacoFonte.regular ? 'normal' : 
                            espacoFonte.mais1 ? 1 + 'px' : 2 + 'px') }">
                    Acessibilidade
                </button>
                <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
                    <li><div @click="toggleContraste" 
                        v-bind:style="{ 
                            backgroundColor: (contrasteValidator.regular ? '#e3e4e8' : 
                                contrasteValidator.altocontrst ? 'black' : '#1c1b17'),
                            color: (contrasteValidator.regular ? 'black' : 
                                contrasteValidator.altocontrst ? 'white' : 'white'),
                            fontSize: (tamanhoFonte.regular ? 16 + 'px':
                                tamanhoFonte.mais1 ? 20 + 'px' : 24 + 'px'), 
                            letterSpacing: (espacoFonte.regular ? 'normal' : 
                                espacoFonte.mais1 ? 1 + 'px' : 2 + 'px')
                        }" 
                        class="dropdown-item">{{ contrasteValidator.string }}</div></li>
                    <li><div @click="toggleTamanhoLetra" class="dropdown-item" 
                        v-bind:style="{
                            fontSize: (tamanhoFonte.regular ? 16 + 'px':
                                tamanhoFonte.mais1 ? 20 + 'px' : 24 + 'px')
                        }">{{ tamanhoFonte.string }}</div></li>
                    <li><div @click="toggleEspacoLetra" class="dropdown-item"
                        v-bind:style="{
                            letterSpacing: (espacoFonte.regular ? 'normal' : 
                                espacoFonte.mais1 ? 1 + 'px' : 2 + 'px'),
                            fontSize: (tamanhoFonte.regular ? 16 + 'px':
                                tamanhoFonte.mais1 ? 20 + 'px' : 24 + 'px')
                        }">{{ espacoFonte.string }}</div></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            usuario: "username",
            tipoContraste: "Contraste Regular",
            tamanhoLetra: "Letra Regular",
            espacoLetra: "Espaço Regular",
            contrasteValidator: {
                regular: true,
                altocontrst: false,
                invertido: false,
                string: "Contraste Regular"
            },
            tamanhoFonte: {
                regular: true,
                mais1: false,
                mais2: false,
                string: "Letra Regular"
            },
            espacoFonte: {
                regular: true,
                mais1: false,
                mais2: false, 
                string: "Espaço Regular"
            }
        }
    }, 
    methods: {
        toggleContraste(event) {
            switch (this.contrasteValidator.string) {
                case "Contraste Regular":
                    this.contrasteValidator = {regular: false, altocontrst: true, invertido: false, string: "Alto Contraste"} 
                    break 
                case "Alto Contraste":
                    this.contrasteValidator = {regular: false, altocontrst: false, invertido: true, string: "Cores Invertidas"} 
                    break 
                case "Cores Invertidas":
                    this.contrasteValidator = {regular: true, altocontrst: false, invertido: false, string: "Contraste Regular"} 
                    
                    break 
            }
            this.$emit('clicked', this.contrasteValidator)
        },
        toggleTamanhoLetra() {
            switch(this.tamanhoFonte.string) {
                case "Letra Regular": 
                    this.tamanhoFonte = {regular: false, mais1: true, mais2: false, string: "Letra Regular +"}
                    break;
                case "Letra Regular +":
                    this.tamanhoFonte = {regular: false, mais1: false, mais2: true, string: "Letra Regular ++"}
                    break;
                case "Letra Regular ++":
                    this.tamanhoFonte = {regular: true, mais1: false, mais2: false, string: "Letra Regular"}
                    break;
            }
            this.$emit('clickedTam', this.tamanhoFonte)
        },
        toggleEspacoLetra() {
            switch(this.espacoFonte.string) {
                case "Espaço Regular": 
                    this.espacoFonte = {regular: false, mais1: true, mais2: false, string: "Espaço Regular +"}
                    break;
                case "Espaço Regular +":
                    this.espacoFonte = {regular: false, mais1: false, mais2: true, string: "Espaço Regular ++"}
                    break;
                case "Espaço Regular ++":
                    this.espacoFonte = {regular: true, mais1: false, mais2: false, string: "Espaço Regular"}
                    break;
            }
            this.$emit('clickedEsp', this.espacoFonte)
        }
    }
}
</script>

<style scoped>
    .regular {
        background-color: #e3e4e8;
        color: black;
        border-bottom: 1px solid black;
    }
    .altoconstraste {
        background-color: black;
        color: white;
        border-bottom: 1px solid white;
    }
    .invertido {
        background-color: #1c1b17;
        color: white;
        border-bottom: 1px solid white;
    }
</style>