<template>
    <label :for="id + '_button'" :class="{'active': isActive}" class="toggle__button">
        <span v-if="!isActive" class="ativo">Comida</span>
        <span v-else>Comida</span>

        <input type="checkbox" :disabled="disabled" :id="id + '_button'" v-model="checkedValue">
        <span class="toggle__switch"></span>

        <span v-if="isActive" class="ativo">Bebida</span>
        <span v-else>Bebida</span>
    </label>
</template>

<script>
export default {
    props: {
        disabled: {
            type: Boolean,
            default: false
        },
        labelEnableText: {
            type: String,
            default: 'Comida'
        },
        
        labelDisableText: {
            type: String,
            default: 'Bebida'
        },
        id: {
            type: String,
            default: 'primary'
        }, 
        defaultState: {
            type: Boolean,
            default: false
        }
    },
    data() {
        return {
            currentState: this.defaultState
        }
    },
    watch: {
        defaultState: function defaultState() {
            this.currentState = Boolean(this.defaultState)
        }
    },
    computed: {
        isActive() {
            return this.currentState;
        },
        enableText() {
            return this.labelEnableText;
        },
        disabledText() {
            return this.labelDisableText;
        },
        checkedValue: {
            get() {
                return this.currentState;
            },
            set(newValue) {
                this.currentState = newValue;
                this.$emit('change', newValue);
            }
        }
    }
}
</script>

<style scoped>
    .toggle__button {
        vertical-align: middle;
        user-select: none;
        cursor: pointer;
    }
    .toggle__button input[type="checkbox"] {
        opacity: 0;
        position: absolute;
        width: 1px;
        height: 1px;
    }
    .toggle__button .toggle__switch {
        display:inline-block;
        height:12px;
        border-radius:6px;
        width:40px;
        background: #FFFFFF;
        box-shadow: inset 0 0 1px #FFFFFF;
        position:relative;
        margin-left: 10px;
        transition: all .25s;
    }
    .toggle__button .toggle__switch::after, 
    .toggle__button .toggle__switch::before {
        content: "";
        position: absolute;
        display: block;
        height: 18px;
        width: 18px;
        border-radius: 50%;
        left: 0;
        top: -3px;
        transform: translateX(0);
    }
    .toggle__button .toggle__switch::after {
        background: #E33535;
        box-shadow: 0 0 1px #FFFFFF;
    }
    .toggle__button .toggle__switch::before {
        background: #E33535;
        box-shadow: 0 0 0 3px #FFFFFF;
        opacity:0;
    }
    .active .toggle__switch {
        background: #FFFFFF;
        box-shadow: inset 0 0 1px #FFFFFF;
    }
    .active .toggle__switch::after,
    .active .toggle__switch::before{
        transform:translateX(40px - 18px);
    }
    .active .toggle__switch::after {
        left: 23px;
        background: #E33535;
        box-shadow: 0 0 1px #E33535;
    }
    .toggle__switch {
        margin-right: 10px;
    }

    .ativo {
        font-weight: 900;
    }
</style>