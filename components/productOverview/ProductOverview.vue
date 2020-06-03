<template>
    <BaseSection>
        <div
            class="flex flex-col items-center border-solid border-primary-base border rounded-lg p-8 text-sec-base scale"
        >
            <BaseSectionHeadline class="mb-8">
                {{ productSectionData.headline }}
            </BaseSectionHeadline>
            <div class="max-w-xl mb-8">
                <BasePicture
                    :image="{
                        name: 'product',
                        type: 'png',
                        alt: 'Produktfoto'
                    }"
                />
            </div>
            <ul class="border-b border-solid border-primary-base pb-8 mb-8">
                <li
                    v-for="(product, index) in productSectionData.includes"
                    :key="index"
                    class="productList mb-2 last:mb-0"
                >
                    {{ product }}
                </li>
            </ul>
            <p class="text-xl leading-none">
                {{ productSectionData.priceHeadline }}
            </p>
            <p class="font-heading lg:text-6xl md:text-5xl sm:text-5xl mb-8">
                {{ `${productSectionData.priceBeforeAndAfter} €` }}
            </p>
            <BaseButton button-path="#">
                {{ productSectionData.buttonText }}
            </BaseButton>
        </div>
    </BaseSection>
</template>

<script>
export default {
    computed: {
        productSectionData() {
            return this.$store.getters.productOverview;
        }
    }
};
</script>

<style scoped>
.productList::before {
    content: '';
    width: 12px;
    height: 12px;
    display: inline-block;
    background-size: 12px 12px;
    background-image: url('~assets/images/icons/correct.svg');
    background-repeat: no-repeat;
    padding-right: 20px;
}

.scale:hover {
    transform: scale(1.01);
    border-width: 2px;
}

.scale {
    transition: all 0.3s;
    transform-origin: 50% 50%;
    backface-visibility: hidden;
}
</style>