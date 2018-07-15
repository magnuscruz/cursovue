<template>
    <button @click="dispatchAction()" class="botao" :class="buttonStyle" :type="tipo">{{ rotulo }}</button>
</template>
<script>
export default {
    props: {
            tipo: {
                required: true,
                type: String
            },

            rotulo: {
                required: true,
                type: String
            },

            confirmacao: {
                required: false,
                default: false,
                type: Boolean
            },
            bstyle: {
                required: false,
                default: 'padrao',
                type: String
            }
    },
    methods: {
        dispatchAction() {
            if(!this.confirm || confirm('Confirma ação?')) {
                this.$emit('confirmAction')
            }
        }
    },
    computed: {
        buttonStyle() {
            if (this.bstyle === 'warm') {
                return 'botao-perigo'
            } else {
                return 'botao-padrao'
            }
        }
    }
}
</script>
<style>
    .botao {
        display: inline-block;
        padding: 5px 10px 10px 10px;
        border-radius: 3px;
        margin: 10px;
        font-size: .8em;
        height: 30px;
        vertical-align: top;
    }

    .botao-perigo {
        background: firebrick;
        color: white;
    }

    .botao-padrao {
        background: darkcyan;
        color: white;
    }
</style>

