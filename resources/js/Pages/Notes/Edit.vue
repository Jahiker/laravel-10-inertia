<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Link, useForm } from '@inertiajs/vue3';

const props = defineProps({ note: Object })
const form = useForm({
    excerpt: props.note.excerpt,
    content: props.note.content,
})

const submit = () => {
    form.put(route('notes.update', props.note.id), form)
}

const destroy = () => {
    if (confirm('Are you sure you want to delete this note?')) {
        $route('notes.update', props.note.id)
    }
}
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
                                <h3 class="text-lg text-gray-900 dark:text-white">Editar una nota</h3>
                                <p class="text-sm text-gray-600 dark:text-gray-400">Luego de editar una nota no podrás
                                    revertir los cambios</p>
                            </div>
                        </div>
                        <div class="md:col-span-2 mt-5 md:mt-0 p-4">
                            <div class="shadow bg-white dark:bg-gray-700 dark:text-white md:rounded-md p-4">
                                <form @submit.prevent="submit">
                                    <div class="mb-4">
                                        <label for="excerpt"
                                            class="block text-sm font-medium text-gray-700 dark:text-gray-200">
                                            Resumen
                                        </label>
                                        <textarea
                                            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 dark:text-white dark:bg-gray-400 leading-tight focus:outline-none focus:shadow-outline"
                                            id="excerpt" name="excerpt" v-model="form.excerpt"></textarea>
                                    </div>
                                    <div class="mb-4">
                                        <label for="content"
                                            class="block text-sm font-medium text-gray-700 dark:text-gray-200">
                                            Contenido
                                        </label>
                                        <textarea
                                            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 dark:text-white dark:bg-gray-400 leading-tight focus:outline-none focus:shadow-outline"
                                            id="content" name="content" v-model="form.content" rows="12"></textarea>
                                    </div>
                                    <div class="mb-4">
                                        <button
                                            class="bg-[#6875F5] hover:opacity-70 text-white py-2 px-4 font-bold rounded-md">Guardar</button>
                                        <Link
                                            class="bg-gray-500 hover:opacity-70 text-white py-2 px-4 font-bold rounded-md ml-4 inline-flex"
                                            :href="route('notes.index')">Volver</Link>
                                        <button @click.prevent="destroy"
                                            class="bg-gray-200 hover:opacity-70 text-black py-2 px-4 font-bold rounded-md ml-4 inline-flex">
                                            Borrar
                                        </button>
                                    </div>
                                </form>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
