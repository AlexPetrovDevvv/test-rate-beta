<template>
    <section class="dynamic-template">
        <div class="container">
            <header class="dynamic-template__header">
                <Button v-if="pageStore.pageState.year !== ''" @click="pageStore.clearPage" text="< Вернуться к годам" />
                <section-navigation v-if="pageStore.pageState.year !== ''"/>
                <year-list v-if="pageStore.pageState.year === ''"/>
            </header>
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
                    <p>При создании рейтинга мы решили не ограничиваться сбором статистики телеграм-каналов. Не все вещи можно измерить. Например, как посчитать <i>авторитетность</i>? Кто самый уважаемый? А на кого подписываются, но не читают? Как вообще в принципе читают юридические телеграм-каналы? А что там со сториз — они нужны или нет?</p>
                    <p>Мы привлекли к участию экспертов — тех, кто создаёт и для кого создаются телеграм-каналы. И, скажем честно, это оказалось едва ли не самой увлекательной частью проекта.</p>
                    <p>В опросе принял участие <b>81 юрист</b>: 50 консультантов и 31 инхаус из крупных корпораций. Респонденты отвечали на 6 вопросов:</p>
                </div>
            </div>
            <div class="research" v-if="pageStore.pageState.year !== '' && pageStore.pageState.pageTitle === 'Исследование' ">
                <h2 class="nominations__title">Опрос экспертов</h2>
                <div class="text">
                    <p>Прогнозирование эффективности рекламы в Телеграме — традиционно больной вопрос: тайна, покрытая мраком, лотерея, русская рулетка… Можно найти разные сравнения, а вот найти вменяемые данные по этому вопросу — нереально. По крайней мере было нереально, пока не появился РЮТ и эта страница, которую вы сейчас читаете.</p><p>Итак, за 2022-й и 2023-й годы мы разместили рекламные посты в 35 (!) юридических каналах самого разного профиля и размера. Стоимость размещения колебалась от 1 000 ₽ до 30 000+ ₽. Мы привлекли тысячи пользователей в <a href="https://t.me/damagesanatomy" rel="nofollow">«Анатомию убытков»</a> (топ-20 самых авторитетных каналов, 1 место в «Убытках», 63 место в Топ-100 больших каналов) и сотни в <a href="https://t.me/s/i_zharskiy" rel="nofollow">«Илья Жарский печатает…»</a> (6 место в топ-50 личных каналов и 13 место в Топ-100 каналов по вовлечёности — каналу, кстати, 3 месяца всего). И нам есть что сказать по вопросу, вынесенному в заголовок, поверьте</p>
                    <h4>Что и как мы сделали</h4>
                    <p>Мы решили поделиться нашим опытом в формате мини-исследования, показать алгоритм подсчета стоимости охвата рекламного сообщения и динамику его роста за год. Исследование касается только размещения рекламных постов (не гивы, папки или контекст).</p>
                    <p>Расчет универсален и подходит для применения к любому телеграм-каналу, потому что не опирается на количество подписчиков. Так мы смогли обойти одну из основных проблем рекламы в тележеньке — накрутку подписчиков. Недобросовестные администраторы (да-да, спойлер!) накручивают количество подписчиков и увеличивают стоимость размещения рекламных постов, исходя из размеров своего канала. Кстати, это делают и вполне уважаемые администраторы (но это секрет, тсс).</p>
                    <p>Поэтому мы опирались на количество просмотров постов. Этот показатель тоже можно накрутить, но это должна быть системная трудозатратная работа — поэтому в нишевом юридическом Телеграме редко кто подобным грешит. Данные по количеству просмотров и прочие статистические показатели собирали в TGStat.</p><p>Мы, само собой, не раскрываем названия каналов, данные которых используем. Понимаем, что любопытно, но предоставляем вам право самим экспериментировать и находить лучшие варианты, исходя из ваших задач.</p><h4>Формула расчета</h4><p>В своих расчетах мы использовали экономическую модель (уравнение регрессии):</p>
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
import NominationsTable from './entities/Nominations/NominationsTable/NominationsTable.vue';
import NominationsFilter from './entities/Nominations/nominationsFilter.vue';
import { usePageStore } from './store/page.js';
const pageStore = usePageStore()

const category = ref('')
const nomination = ref('')

const categoryList = ["Топ-100"]
const nominationsList = ["Большие", "Цитируемые", "Вовлеченные"]

const bigData = ref([])
const involdedData = ref([])
const quoteData = ref([])

onMounted(async () => {
    const bigResponse = await fetch('./data/big.json')
    const bigResData = await bigResponse.json()
    bigData.value = bigResData
    console.log(bigData.value)

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