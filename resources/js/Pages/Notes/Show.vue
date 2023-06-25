<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Link } from '@inertiajs/vue3';

const props = defineProps(['note'])
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
                                <h3 class="text-lg text-gray-900 dark:text-white">Detalle de una nota</h3>
                                <p class="text-sm text-gray-600 dark:text-gray-400">{{ note.excerpt }}</p>
                            </div>
                        </div>
                        <div class="md:col-span-2 mt-5 md:mt-0 p-4">
                            <div class="shadow bg-white dark:bg-gray-700 dark:text-white md:rounded-md p-4">
                                <small class="dark:text-gray-300">{{ note.excerpt }}</small>
                                <p>{{ note.content }}</p>
                                <hr class="block mt-6 mb-6">
                                <Link class="bg-[#6875F5] hover:opacity-70 text-white py-2 px-4 font-bold rounded-md"
                                    :href="route('notes.edit', note.id)">Editar</Link>
                                <Link class="bg-gray-500 hover:opacity-70 text-white py-2 px-4 font-bold rounded-md ml-4"
                                    :href="route('notes.index')">Volver</Link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
