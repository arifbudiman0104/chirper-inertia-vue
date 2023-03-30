<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import Chirp from '@/Components/Chirp.vue';
import InputError from '@/Components/InputError.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import { useForm, Head } from '@inertiajs/vue3';

defineProps(['chirps']);

const form = useForm({
    message: '',
});
</script>

<template>
    <Head title="Chirps" />

    <AuthenticatedLayout>
        <!-- <template #header>
                <h2 class="font-semibold text-xl text-gray-800 dark:text-gray-200 leading-tight">Chirps</h2>
            </template> -->

        <Head title="Chirps" />
        <!-- <div class="py-12"> -->
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">
            <form @submit.prevent="form.post(route('chirps.store'), { onSuccess: () => form.reset() })">
                <textarea v-model="form.message" rows="3" placeholder="What's on your mind?"
                    class="block w-full text-gray-900 dark:text-gray-300 placeholder:text-gray-900 dark:placeholder:text-gray-300 border-gray-300 dark:border-gray-900 bg-white dark:bg-gray-800 focus:border-indigo-300 dark:focus:border-indigo-500 focus:ring focus:ring-indigo-200 dark:focus:ring-indigo-400 focus:ring-opacity-50 rounded-md shadow-sm"></textarea>
                <InputError :message="form.errors.message" class="mt-2" />
                <PrimaryButton class="mt-4">Chirp</PrimaryButton>
            </form>
            <div class="mt-6 bg-white dark:bg-gray-800 shadow-sm rounded-lg divide-y dark:divide-gray-900">
                <Chirp
                    v-for="chirp in chirps"
                    :key="chirp.id"
                    :chirp="chirp"
                />
            </div>
        </div>
        <!-- </div> -->
    </AuthenticatedLayout>
</template>
