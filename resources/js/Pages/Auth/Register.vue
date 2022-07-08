<script setup>
import BreezeButton from '@/Components/Button.vue';
import BreezeGuestLayout from '@/Layouts/Guest.vue';
import BreezeInput from '@/Components/Input.vue';
import BreezeLabel from '@/Components/Label.vue';
import BreezeValidationErrors from '@/Components/ValidationErrors.vue';
import { Head, Link, useForm } from '@inertiajs/inertia-vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
    terms: false,
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <BreezeGuestLayout>
        <Head title="Register" />

        <BreezeValidationErrors class="mb-4" />

        <form @submit.prevent="submit">
            <h3 class="font-bold text-center text-gray-900">Información personal</h3>

            <div>
                <BreezeLabel for="name" value="Name" />
                <BreezeInput id="name" type="text" class="mt-1 block w-full" v-model="form.name" required autofocus autocomplete="name" />
            </div>

            <div class="mt-4">
                <BreezeLabel for="email" value="Email" />
                <BreezeInput id="email" type="email" class="mt-1 block w-full" v-model="form.email" required autocomplete="username" />
            </div>

            <div class="mt-4">
                <BreezeLabel for="birthdate" value="Fecha de nacimiento" />
                <BreezeInput id="birthdate" type="date" class="mt-1 block w-full" required autocomplete="username" />
            </div>

            <div class="mt-4">
                <BreezeLabel for="state" value="Estado" />
                <select id="state" name="select" required class="border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm w-full">
                    <option value="value1" selected>Jalisco</option>
                    <option value="value2" >Zacatecas</option>
                    <option value="value3">Colima</option>
                </select>
            </div>

            <div class="mt-4">
                <BreezeLabel for="grade" value="Grado Académico" />
                <select id="grade" name="select" required class="border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm w-full">
                    <option value="value1" selected>Bachillerato</option>
                    <option value="value3">Licenciatura</option>
                    <option value="value3">Maestria</option>
                </select>
            </div>

               <div class="mt-4">
                <BreezeLabel for="area" value="Area de formación" />
                <select id="area" name="select" required class="border-gray-300 focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50 rounded-md shadow-sm w-full">
                    <option value="value2" selected>Leyes</option>
                    <option value="value1">Ingenieria</option>
                    <option value="value3">Biología</option>
                    <option value="value3">Ciencias sociales</option>
                </select>
            </div>

             <div class="mt-4">
                <BreezeLabel for="school" value="Nombre de Escuela" />
                <BreezeInput id="school" type="text" class="mt-1 block w-full"  autocomplete="new-password" />
            </div>

            <div class="mt-4">
                <BreezeLabel for="password" value="Password" />
                <BreezeInput id="password" type="password" class="mt-1 block w-full" v-model="form.password" required autocomplete="new-password" />
            </div>

            <div class="mt-4">
                <BreezeLabel for="password_confirmation" value="Confirm Password" />
                <BreezeInput id="password_confirmation" type="password" class="mt-1 block w-full" v-model="form.password_confirmation" required autocomplete="new-password" />
            </div>

            <div class="flex items-center justify-end mt-4">
                <Link :href="route('login')" class="underline text-sm text-gray-700 hover:text-gray-900">
                    Already registered?
                </Link>

                <BreezeButton class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                    Registrar
                </BreezeButton>
            </div>
        </form>
    </BreezeGuestLayout>
</template>
