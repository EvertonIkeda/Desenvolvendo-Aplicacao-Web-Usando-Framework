<template>
    <div class="formulario">
        <di>
            <label>
                Nome
                <input v-model="nome" type="text">
            </label>
            <label>
                Sobrenome
                <input v-model="sobrenome" type="text">
            </label>
            <label>
                Idade
                <input v-model="idade" type="number">
            </label>

            <button @click="submit"> Cadastrar Pessoa </button>

            <div class="pessoas">
                <template v-if="pessoas.length == 0">
                    <p>Nenhuma pessoa cadastrada</p>
                </template>

                <template v-for="(pessoa, index) in pessoas" :key="index">
                    <p>Nome: {{ pessoa.nome }} || Ano: {{ pessoa.sobrenome }} || Idade: {{ pessoa.idade }}</p>

                    <button @click="remove(index)"> Excluir </button>
                </template>
            </div>
        </di>
    </div>
</template>
<script setup>
import { ref, reactive } from 'vue'

const nome = ref("")
const sobrenome = ref("")
const idade = ref("")
const pessoas = reactive([])

function submit() {
    if (nome.value.length == 0) {
        alert('Preencha o nome')
        return
    }
    if (sobrenome.value.length == 0) {
        alert('Preencha o sobrenome')
        return
    }
    if (idade.value.length == 0) {
        alert('Preencha a idade')
        return
    }

    const pessoa = {
        'nome' : nome.value,
        'sobrenome' : sobrenome.value,
        'idade' : idade.value
    }

    nome.value = ""
    sobrenome.value = ""
    idade.value = ""

    pessoas.push(pessoa)
}

function remove(index) {
    pessoas.splice(index, 1)
}
</script>
<style>
.formulario {
    align-items: start;
    justify-items: start;
    display: flex;
    width: 1000px;
}
.pessoas {
    margin-top: 20px;
}
</style>