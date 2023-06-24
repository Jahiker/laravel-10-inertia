<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Link } from '@inertiajs/vue3';

const props  = defineProps(['notes'])
</script>

<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">
                Notas
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white dark:bg-gray-800 overflow-hidden shadow-xl sm:rounded-lg">
                    <div class="md:grid  md:grid-cols-3 md:gap-6">
                        <div class="md:col-span-1 p-3">
                            <div class="">
                                <h3 class="text-lg text-gray-900 dark:text-white">Listado de notas</h3>
                                <p class="text-sm text-gray-600 dark:text-gray-400">Toma el registro correcto y ejecuta cualquier función (ver)</p>
                            </div>
                        </div>
                        <div class="md:col-span-2 mt-5 md:mt-0 p-4">
                            <div class="shadow bg-white dark:bg-gray-700 dark:text-white md:rounded-md p-4">
                                <table>
                                    <tr v-for="note in notes">
                                        <td class="border px-4 py-2">
                                            {{ note.excerpt }}
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
        </div>
    </AppLayout>
</template>
