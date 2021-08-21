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
                            <h3 class="text-lg text-gray-900">Listado de notas</h3>
                            <p class="text-sm text-gray-600">Aqui puedes registrar y manejar tus notas</p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <Link :href="route('notes.create')" class="bg-blue-500 text-white font-bold py-2 px-4 rounded-sm">Crear Nota</Link>

                        <div class="shadow bg-white md:rounded-md p-4 my-4">
                            <table>
                                <tr v-for="note in notes">
                                    <td class="border px-4 py-2">
                                        {{ note.exceprt }}
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.show', note.id)">
                                            Ver
                                        </Link>                                       
                                    </td>
                                    <td class="px-4 py-2">
                                        <Link :href="route('notes.edit', note.id)">
                                            Editar
                                        </Link>                                         
                                    </td>
                                </tr>
                            </table>
                        </div>
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
        props: {
            notes: Array,
        }
    }
</script>
