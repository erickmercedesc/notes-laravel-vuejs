<template>
    <app-layout title="Notas">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Notas
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6">
                    <div class="md:col-span-1">
                        <div class="px-4 sm:px0">
                            <h3 class="text-lg text-gray-900">Crear Nota</h3>
                            <p class="text-sm text-gray-600">Agrega todas las notas que desees sin limites</p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <form @submit.prevent="submit">
                            <label class="block font-medium text-sm text-gray-700">Resumen</label>
                            <textarea 
                                class="form-input w-full rounded-md shadow-sm" 
                                v-model="form.exceprt"
                            ></textarea>

                            <label class="block font-medium text-sm text-gray-700">Contenido</label>
                            <textarea 
                                class="form-input w-full rounded-md shadow-sm" 
                                v-model="form.content"
                                rows="8"
                            ></textarea>
                            <button 
                                type="submit"
                                class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4"
                            >Crear</button>                            
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout.vue'
    import { Link } from '@inertiajs/inertia-vue3'

    export default {
        components: {
            AppLayout,
            Link
        },
        data () {
            return {
                form: {
                    exceprt: '',
                    content: ''
                }
            }
        },
        methods: {
            submit(){
                this.$inertia.post(this.route('notes.store'), this.form);
            }
        }
    }
</script>
