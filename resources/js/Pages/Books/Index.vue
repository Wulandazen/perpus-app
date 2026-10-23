<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Link } from '@inertiajs/vue3';

defineProps({
    books: Object,
});
</script>

<template>
    <AuthenticatedLayout>
        <h1>Data Buku</h1>

        <Link href="/books/create">
            + Tambah Buku
        </Link>

        
        <table class="w-full border-collapse border">
            <thead>
                <tr class="bg-gray-100">
                    <th class="border p-2">Kode Buku</th>
                    <th class="border p-2">Judul</th>
                    <th class="border p-2">Pengarang</th>
                    <th class="border p-2">Tahun</th>
                    <th class="border p-2">Stok</th>
                </tr>
            </thead>

            <tbody>
                <tr v-for="book in books.data" :key="book.id">
                    <td class="border p-2">{{ book.kode_buku }}</td>
                    <td class="border p-2">{{ book.judul }}</td>
                    <td class="border p-2">{{ book.pengarang }}</td>
                    <td class="border p-2">{{ book.tahun ?? '-' }}</td>
                    <td class="border p-2">{{ book.stok }}</td>
                </tr>
            </tbody>
        </table>

    </AuthenticatedLayout>
</template>
