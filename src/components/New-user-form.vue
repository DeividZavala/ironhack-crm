<template>

    <div>
        <h2 class="uk-modal-title">Nuevo usuario papud</h2>

        <form>
            <div class="uk-grid-small uk-child-width-1-2" uk-grid>

                <div>
                    <label class="uk-form-label" for="user-name">Name</label>
                    <div class="uk-form-controls">
                        <input type="text" class="uk-input" id="user-name">
                    </div>
                </div>

                <div>
                    <label class="uk-form-label" for="user-lastname">Lastname</label>
                    <div class="uk-form-controls">
                        <input type="text" class="uk-input" id="user-lastname">
                    </div>
                </div>

                <div>
                    <label class="uk-form-label" for="user-surname">Surname</label>
                    <div class="uk-form-controls">
                        <input type="text" class="uk-input" id="user-surname">
                    </div>
                </div>

                <div>
                    <label class="uk-form-label" for="user-email">Email</label>
                    <div class="uk-form-controls">
                        <input type="email" class="uk-input" id="user-email">
                    </div>
                </div>

                <div>
                    <label class="uk-form-label" for="user-phone">Phone</label>
                    <div class="uk-form-controls">
                        <input type="email" class="uk-input" id="user-phone">
                    </div>
                </div>

                <div>
                    <label class="uk-form-label" for="user-type">Tipo de usuario</label>
                    <div class="uk-form-controls">
                        <select class="uk-select" id="user-type">
                            <option value="" selected>type of user</option>
                            <option>Conductor</option>
                            <option>Usuario</option>
                            <option>Ambos</option>
                        </select>
                    </div>
                </div>

                <div>
                    <label class="uk-form-label" for="user-course">Interesado en:</label>
                    <div class="uk-form-controls">
                        <select class="uk-select" id="user-course" >
                            <option value="" disabled selected>Selecciona curso de interes</option>
                            <option value="Desarrollo Web Tiempo Parcial">Desarrollo Web Tiempo Parcial</option>
                            <option value="Desarrollo Web Tiempo Completo">Desarrollo Web Tiempo Completo</option>
                            <option value="Diseño UX/UI">Diseño UX/UI</option>
                            <option value="Diseño UX/UI Tiempo Parcial">Diseño UX/UI Tiempo Parcial</option>
                        </select>
                    </div>
                </div>


            </div>
            <div class="uk-margin-top">
                <button class="uk-button uk-button-default">Create</button>
            </div>
        </form>

    </div>
    
</template>

<script lang="ts">

    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';

    @Component
    export default class NewUserForm extends Vue {

    }
</script>

<style scoped>

</style>