<template>
    <section class="dynamic-template" :class="{'dynamic-template_paw': showPaw}">
        <div class="container">
            <header class="dynamic-template__header">
                <Button v-if="pageStore.pageState.year !== ''" id="toggle" @click="pageStore.clearPage" text="< Вернуться к годам" />
                <div ></div>
                
                <Button v-if="pageStore.pageState.year !== ''" @click="togglePaw"  text="Мини-игра" />
                <span class="paw-btn"><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">…</svg></span>
                <section-navigation v-if="pageStore.pageState.year !== ''"/>
                <year-list v-if="pageStore.pageState.year === ''"/>
            </header>

            <!-- ⬅ добавлено: блок мини-игры c изображением и лупой -->
            <section v-if="showPaw" class="mini-game">
                <div class="mini-game__wrap">
                    <img ref="miniImg"
                         class="mini-game__img"
                         :src="miniImgSrc"
                         alt="demo" />
                    <!-- Лупа поверх картинки (включается/выключается той же кнопкой) -->
                    <Magnifier :target="miniImg" :active="showPaw" :zoom="2.2" :size="160" />
                </div>
                <p class="mini-game__hint">Двигай мышкой по картинке — лупа увеличивает прозрачное «стекло».</p>
            </section>
            <!-- ⬅ /добавлено -->

            <div class="nominations" v-if="pageStore.pageState.year !== '' && pageStore.pageState.pageTitle === 'Номинации' ">
                <h2 class="nominations__title">{{ pageStore.pageState.pageTitle }}</h2>
                <p class="text">Выберите категорию и номинацию</p>
                <nominations-filter v-model:category="category" v-model:nomination="nomination" :category-list="categoryList" :nominations-list="nominationsList"/>
                <div class="nominations-table-wrapper">
                    <nominations-table v-if="category !== '' && nomination === 'Большие'" :value-list="bigData.participants" :title-list="bigData.columns" :title-value-list="bigData.rows"/>
                    <nominations-table v-if="category !== '' && nomination === 'Цитируемые'" :value-list="quoteData.participants" :title-list="quoteData.columns" :title-value-list="quoteData.rows"/>
                    <nominations-table v-if="category !== '' && nomination === 'Вовлеченные'" :value-list="involdedData.participants" :title-list="involdedData.columns" :title-value-list="involdedData.rows"/>
                </div>
            </div>

            <div class="survey" v-if="pageStore.pageState.year !== '' && pageStore.pageState.pageTitle === 'Опрос' ">
                <h2 class="nominations__title">Опрос экспертов</h2>
                <div class="text">
                    <!-- … твой текст без изменений … -->
                </div>
            </div>

            <div class="research" v-if="pageStore.pageState.year !== '' && pageStore.pageState.pageTitle === 'Исследование' ">
                <h2 class="nominations__title">Опрос экспертов</h2>
                <div class="text">
                    <!-- … твой текст без изменений … -->
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import YearList from './entities/Year/YearList.vue';
import SectionNavigation from './entities/Sections/SectionsNavigation/SectionsNavigation.vue';
import Button from './shared/Button/Button.vue';
import NominationsTable from './entities/Nominations/NominationsTable/nominationsTable.vue';
import NominationsFilter from './entities/Nominations/nominationsFilter.vue';
import { usePageStore } from './store/page.js';
import { defineEmits } from 'vue';
import Magnifier from '../Magnifier.vue'

const emit = defineEmits(['toggle-paw']);

const showPaw = ref(false);

const togglePaw = () => {
  showPaw.value = !showPaw.value;
  emit('toggle-paw', showPaw.value); 
};

const pageStore = usePageStore()

const category = ref('')
const nomination = ref('')

const categoryList = ["Топ-100"]
const nominationsList = ["Большие", "Цитируемые", "Вовлеченные"]

const bigData = ref([])
const involdedData = ref([])
const quoteData = ref([])

// ⬅ добавлено: изображение для «мини-игры»
const miniImg = ref(null)
const miniImgSrc = 'https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?q=80&w=1200&auto=format&fit=crop' // замени на свой при желании

onMounted(async () => {
    const bigResponse = await fetch('./data/big.json')
    const bigResData = await bigResponse.json()
    bigData.value = bigResData

    const involdedResponse = await fetch('./data/involved.json')
    const involdedResData = await involdedResponse.json()
    involdedData.value = involdedResData

    const quoteResponse = await fetch('./data/quoted.json')
    const quoteResData = await quoteResponse.json()
    quoteData.value = quoteResData
})
</script>

<style lang="sass">
.dynamic-template
    margin-top: 100px
    .container
        background-color: #EDEFF7
        padding: 100px 20px
        border-radius: 20px
    &__header
        display: flex
        flex-direction: column
        gap: 20px

/* ⬅ добавлено: стили мини-игры */
.mini-game
    margin-top: 20px
    &__wrap
        position: relative
        display: inline-block
    &__img
        display: block
        max-width: min(720px, 90vw)
        height: auto
        border-radius: 12px
        box-shadow: 0 8px 24px rgba(0,0,0,.12)
    &__hint
        margin-top: 10px
        font-size: 14px
        color: #5A6A85

.nominations
    margin-top: 40px
    &__title
        font-size: 24px
        font-style: normal
        font-weight: 600
        line-height: 130%
        color: var(--blue)

.nominations-table-wrapper
    margin-top: 40px
    overflow-x: auto
    width: 100%

.text
    margin-top: 20px
    font-size: 18px
    color: var(--blue)
    line-height: 130%
    & p
        &:not(:first-child)
            margin-top: 20px
</style>
