<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { useForm } from '@inertiajs/vue3';

const form = useForm({
    kode_buku: '',
    judul: '',
    pengarang: '',
    penerbit: '',
    tahun: '',
    stok: 0,
});

function submit() {
    form.post(route('books.store'));
}
</script>

<template>
    <AuthenticatedLayout>
        <h1>Tambah Buku</h1>

        <form @submit.prevent="submit">
            <div>
                <label>Kode Buku</label>
                <input v-model="form.kode_buku" type="text">
                <span>{{ form.errors.kode_buku }}</span>
            </div>

            <div>
                <label>Judul</label>
                <input v-model="form.judul" type="text">
                <span>{{ form.errors.judul }}</span>
            </div>

            <div>
                <label>Pengarang</label>
                <input v-model="form.pengarang" type="text">
                <span>{{ form.errors.pengarang }}</span>
            </div>

            <div>
                <label>Penerbit</label>
                <input v-model="form.penerbit" type="text">
            </div>

            <div>
                <label>Tahun</label>
                <input v-model="form.tahun" type="text">
            </div>

            <div>
                <label>Stok</label>
                <input v-model="form.stok" type="number">
                <span>{{ form.errors.stok }}</span>
            </div>

            <button type="submit">Simpan</button>
        </form>
    </AuthenticatedLayout>
</template>
