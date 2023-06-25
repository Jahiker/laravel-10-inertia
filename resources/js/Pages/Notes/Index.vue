<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Link, router } from '@inertiajs/vue3';
import { ref, watch } from 'vue';

const props = defineProps(['notes'])
const q = ref('')

watch(q, (newValue, oldValue) => {
    if (newValue !== oldValue) {
        router.get(route('notes.index', {q: newValue}), {}, {preserveState: true})
    }
})

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
                                <p class="text-sm text-gray-600 dark:text-gray-400 mb-5">Toma el registro correcto y ejecuta
                                    cualquier función (ver)</p>
                                <Link :href="route('notes.create')"
                                    class="bg-[#6875F5] hover:opacity-70 text-white py-2 px-4 font-bold rounded-md">
                                Crear una nota
                                </Link>
                            </div>
                        </div>
                        <div class="md:col-span-2 mt-5 md:mt-0 p-4">
                            <div class="shadow bg-white dark:bg-gray-700 dark:text-white md:rounded-md p-4">
                                <div class="flex justify-between my-4">
                                    <input type="text" placeholder="Buscar..." v-model="q"
                                        class="form-input shadow appearance-none border rounded-md w-full py-2 px-3 text-gray-700 dark:text-white dark:bg-gray-400 leading-tight focus:outline-none focus:shadow-outline">
                                </div>
                                <hr class="my-5 border border-gray-400">
                                <table>
                                    <tr v-for="note in notes">
                                        <td class="border px-4 py-2">
                                            {{ note.excerpt }}
                                        </td>
                                        <td class="px-4 py-2">
                                            <Link :href="route('notes.show', note.id)"
                                                class="bg-gray-500 hover:opacity-70 text-white py-2 px-4 font-bold rounded-md">
                                            Ver
                                            </Link>
                                        </td>
                                        <td class="px-4 py-2">
                                            <Link :href="route('notes.edit', note.id)"
                                                class="bg-[#6875F5] hover:opacity-70 text-white py-2 px-4 font-bold rounded-md">
                                            Editar
                                            </Link>
                                        </td>
                                        <td class="px-4 py-2">
                                            <Link :href="route('notes.destroy', note.id)"
                                                class="bg-gray-200 hover:opacity-70 text-black py-2 px-4 font-bold rounded-md"
                                                as="button" method="delete">
                                            Borrar
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
