<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { useForm } from '@inertiajs/vue3';

const props = defineProps({
    book: Object,
});

const form = useForm({
    kode_buku: props.book.kode_buku ?? '',
    judul: props.book.judul ?? '',
    pengarang: props.book.pengarang ?? '',
    penerbit: props.book.penerbit ?? '',
    tahun: props.book.tahun ?? '',
    stok: props.book.stok ?? 0,
});

function submit() {
    form.put(route('books.update', props.book.id));
}
</script>

<template>
    <AuthenticatedLayout>
        <h1>Edit Buku</h1>

        <form @submit.prevent="submit">
            <div>
                <label>Kode Buku</label>
                <input v-model="form.kode_buku" type="text">
                <div v-if="form.errors.kode_buku">
                    {{ form.errors.kode_buku }}
                </div>
            </div>

            <div>
                <label>Judul</label>
                <input v-model="form.judul" type="text">
                <div v-if="form.errors.judul">
                    {{ form.errors.judul }}
                </div>
            </div>

            <div>
                <label>Pengarang</label>
                <input v-model="form.pengarang" type="text">
                <div v-if="form.errors.pengarang">
                    {{ form.errors.pengarang }}
                </div>
            </div>

            <div>
                <label>Penerbit</label>
                <input v-model="form.penerbit" type="text">
                <div v-if="form.errors.penerbit">
                    {{ form.errors.penerbit }}
                </div>
            </div>

            <div>
                <label>Tahun</label>
                <input v-model="form.tahun" type="text">
                <div v-if="form.errors.tahun">
                    {{ form.errors.tahun }}
                </div>
            </div>

            <div>
                <label>Stok</label>
                <input v-model="form.stok" type="number" min="0">
                <div v-if="form.errors.stok">
                    {{ form.errors.stok }}
                </div>
            </div>

            <button type="submit" :disabled="form.processing">
                Simpan Perubahan
            </button>
        </form>
    </AuthenticatedLayout>
</template>
