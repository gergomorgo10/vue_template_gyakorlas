<script setup>
import { getProducts } from '../api/products';

</script>

<script>
export default{
    name: "product_manadger",
    data(){
        return{
            products: []
        }
    },
    methods: {
        async loadProducts() {
            this.products = await getProducts();
        },

        async addProduct(){
            
        }
    },
    mounted() {
        this.loadProducts();
    }
};
</script>

<template>
    <main class=" bg-indigo-950 text-amber-50">
        <h1 class="">termékek manadzsment</h1>

        <table class="flex w-full">
            <thead class="p-2 w-full">
                <tr class="flex justify-around gap-8">
                    <th class="">id</th>
                    <th class="">name</th>
                    <th class="">price</th>
                    <th class="">in stock</th>
                </tr>
            </thead>
            <tbody class="w-full">
                <tr class="flex justify-around gap-8" :key="products.id">
                    <td class="">{{ products.id }}</td>
                    <td class="">{{ products.name }}</td>
                    <td class="">{{ products.price }}</td>
                    <td class="">{{ products.inStock ? 'igen' : 'elfogyott' }}</td>
                </tr>
            </tbody>
        </table>

        <form class="mt-30 flex flex-col border-2 border-stone-200 rounded-xl p-5 w-max">
            <label for="name">név</label>
            <input type="text" name="name" id="" class="border-2 border-stone-200 rounded-xl p-5">

            <label for="price">Ár</label>
            <input type="number" name="price" id="" class="border-2 border-stone-200 rounded-xl p-5">

            <label for="inStock">Raktáron van-e?</label>
            <input type="checkbox" name="inStock" id="">

            <button type="submit">Létrehozás</button>
        </form>
    </main>
</template>

