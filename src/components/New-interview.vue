<template>

    <div>
        <h2 class="uk-modal-title">New Interview</h2>
        <form>
            <div class="uk-grid-small uk-child-width-1-2" uk-grid>
                <div>
                    <label class="uk-form-label" for="interview-type">Tipo de Entrevista</label>
                    <div class="uk-form-controls">
                        <select class="uk-select" id="interview-type">
                            <option>Personal</option>
                            <option>Técnica</option>
                        </select>
                    </div>
                </div>
                <div class="date__input-container">
                    <label class="uk-form-label" for="interview-date">Fecha y hora de Inicio</label>
                    <div class="uk-form-controls date-input">
                        <!--<input class="uk-input" id="interview-date" type="datetime-local" placeholder="">-->
                        <datetime type="datetime" id="interview-date" v-model="date"></datetime>
                    </div>
                </div>
                <div class="date__input-container">
                    <label class="uk-form-label" for="interview-date-final">Fecha y hora de Fin</label>
                    <div class="uk-form-controls date-input">
                        <!--<input class="uk-input" id="interview-date" type="datetime-local" placeholder="">-->
                        <datetime type="datetime" id="interview-date-final" v-model="date_final"></datetime>
                    </div>
                </div>
                <div>
                    <label class="uk-form-label" for="interview-active">Activa</label>
                    <div class="uk-form-controls">
                        <input class="uk-checkbox" id="interview-active" type="checkbox" placeholder="">
                    </div>
                </div>

            </div>
            <div class="uk-margin-top">
                <button class="uk-button uk-button-default">Crear</button>
            </div>
        </form>
    </div>
    
</template>

<script lang="ts">

    import {Component, Vue} from 'vue-property-decorator';
    import { Datetime } from 'vue-datetime';

    @Component({
        components: {
            Datetime
        }
    })
    export default class NewInterview extends Vue{

        date: string = "";
        date_final: string = "";

    }
</script>

<style scoped>

    .uk-checkbox, .uk-radio{
        width: 30px;
        height: 30px;
    }

</style>