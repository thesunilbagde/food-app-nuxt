<template>
    <section class="restaurantinfo">
        <div v-for="store in fooddata" :key="store.id">
            <h2 class="text-2xl font-bold">{{ store.name }}</h2>
            <p class="text-gray-600">Delivery Time {{ store.deliveryTime }}</p>
            <p class="text-gray-600">Rating {{ store.rating }}</p>
            <p v-if="store.freeDelivery" class="label">
                <span>Free Delivery</span>
            </p>
            <div class="row">
                <div
                    v-for="menuitem in store.menu"
                    :key="menuitem.id"
                    :style="
                        `background: url(/${menuitem.img}) no-repeat center center`
                    "
                    class="items"
                >
                    <div class="iteminfo">
                        <div>
                            <h4>
                                {{ menuitem.item }}
                            </h4>
                            <p>{{ priceFormatting(menuitem.price) }}</p>
                        </div>
                        <nuxt-link :to="`item/${menuitem.id}`">
                            <button class="ghost">View Item ></button>
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import { mapState } from "vuex";

export default {
    computed: {
        ...mapState(["fooddata"]),
    },
    methods: {
        priceFormatting(item) {
            return "$" + item.toFixed(2);
        },
    },
};
</script>

<style lang="scss" scoped></style>
