<template>
    <section class="dynamic-template" :class="{'dynamic-template_paw': showPaw}">
        <div class="container">
            <header class="dynamic-template__header">
                <Button v-if="pageStore.pageState.year !== ''" id="toggle" @click="pageStore.clearPage" text="< Вернуться к годам" />
                <div ></div>
                
                <Button v-if="pageStore.pageState.year !== ''" @click="togglePaw"  text="Мини-игра" />
                <span class="paw-btn"><svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M11.7598 15.5004C11.7198 16.0604 11.4198 16.4004 11.0598 16.7004C11.0398 16.7204 10.9798 16.7204 10.9398 16.7404C10.5798 16.7404 10.1998 16.7404 9.85984 16.8004C8.89984 16.9804 8.23984 16.5004 7.61984 15.8804C7.53984 15.8004 7.39984 15.7204 7.29984 15.7204C6.19984 15.6404 5.15984 15.3204 4.21984 14.7004C3.97984 14.5404 3.83984 14.2404 3.67984 14.0004C3.57984 13.8404 3.45984 13.7604 3.25984 13.7204C2.47984 13.6004 1.67984 13.6804 0.919844 13.3604C0.619844 13.2404 0.339844 13.0604 0.339844 12.7604C0.339844 12.5204 0.539844 12.2204 0.739844 12.1004C1.21984 11.8004 1.73984 11.5804 2.27984 11.3804C3.53984 10.8804 4.81984 10.5404 6.13984 10.2604C6.35984 10.2204 6.57984 10.0804 6.77984 9.94038C7.63984 9.30038 8.59984 9.94038 8.87984 10.6004C9.29984 11.5804 9.81984 12.5004 10.4998 13.3404C10.8598 13.7804 11.0798 14.3004 11.3598 14.8004C11.4598 14.9804 11.5998 15.1404 11.6998 15.3004C11.7398 15.3804 11.7598 15.4604 11.7598 15.4804V15.5004Z" fill="#002B55"/>
<path d="M12.9416 8.92115C12.2416 8.76115 11.5016 8.68115 10.8616 8.40115C10.0816 8.06115 9.82161 7.24115 10.4816 6.54115C10.7216 6.30115 10.9616 5.98115 11.3816 6.12115C11.4216 6.12115 11.5216 6.08115 11.5616 6.04115C12.0216 5.58115 12.6216 5.64115 13.2016 5.58115C13.4616 5.56115 13.7216 5.58115 14.0016 5.58115C14.7416 5.58115 15.2216 6.32115 15.0216 7.04115C14.9616 7.26115 15.0216 7.50115 15.0216 7.74115C15.0216 7.84115 15.0216 7.98116 14.9616 8.02116C14.3416 8.38116 13.8016 8.98115 12.9616 8.82115V8.94115L12.9416 8.92115Z" fill="#002B55"/>
<path d="M17.5 12.3401C16.8 12.2001 16.12 12.0601 15.44 11.9401C15.38 11.9401 15.26 11.9001 15.26 11.8601C15.14 11.3601 14.68 11.1401 14.36 10.8201C14.1 10.5601 14.1 10.4601 14.42 10.2401C14.78 9.98013 15.16 9.84013 15.62 9.94013C15.74 9.96013 15.9 9.94013 15.98 9.88013C16.44 9.52013 17 9.50013 17.54 9.36013C17.68 9.32013 17.86 9.30013 17.98 9.36013C18.5 9.62013 19.04 9.86013 19.48 10.2201C19.92 10.6001 19.66 11.4401 19.1 11.7001C18.9 11.7801 18.74 11.9601 18.54 12.0401C18.22 12.1601 17.88 12.2601 17.52 12.3601L17.5 12.3401Z" fill="#002B55"/>
<path d="M7.0993 7.42112C6.4593 7.54112 5.8793 7.14112 5.2793 6.82112C4.8393 6.58112 4.8193 6.12112 5.0593 5.68112C5.5193 4.84112 6.3793 4.76112 7.1393 4.42112C7.7793 4.14112 8.3593 4.28112 8.9593 4.48112C9.3593 4.62112 9.4393 4.76112 9.3793 5.18112C9.3593 5.38112 9.3393 5.60112 9.2993 5.80112C9.2993 5.88112 9.1993 5.94112 9.1593 6.00112C9.1193 6.06112 9.07931 6.10112 9.05931 6.16112C8.71931 7.30112 8.4193 7.50112 7.2393 7.44112C7.2393 7.44112 7.2193 7.44112 7.0993 7.44112V7.42112Z" fill="#002B55"/>
<path d="M0 6.88176C0.1 6.24176 0.18 5.64176 0.28 5.04176C0.34 4.74176 0.58 4.64176 0.88 4.72176C2.02 5.00176 2.84 5.76176 3.56 6.62176C4.04 7.20176 3.8 7.76176 3.06 7.96176C2.4 8.14176 1.76 8.18176 1.14 7.96176C0.8 7.84176 0.48 7.60176 0.2 7.36176C0.08 7.26176 0.06 7.04176 0.02 6.90176L0 6.88176Z" fill="#002B55"/>
<path d="M19.9992 8.37996C19.8792 8.81996 19.6192 9.03996 19.2792 9.11996C19.1392 9.15996 18.9392 9.03996 18.6992 8.97996C18.9992 8.69996 19.1992 8.45996 19.4592 8.29996C19.5792 8.23996 19.7992 8.33996 19.9992 8.37996Z" fill="#002B55"/>
<path d="M14.1016 5.20066C14.2016 5.04066 14.2616 4.88066 14.3616 4.74066C14.4816 4.58066 14.6216 4.56066 14.7816 4.68066C14.9216 4.78066 15.0216 4.88066 14.9016 5.06066C14.7216 5.36066 14.4216 5.40066 14.1016 5.18066V5.20066Z" fill="#002B55"/>
<path d="M8.89891 3.28092C8.59891 3.80092 8.35891 3.92092 7.87891 3.78092C8.11891 3.24092 8.57891 3.02092 8.89891 3.28092Z" fill="#002B55"/>
<path d="M0.558594 4.14102C0.618594 3.86102 0.538594 3.58102 0.878594 3.62102C1.05859 3.62102 1.27859 3.72102 1.21859 3.94102C1.17859 4.08102 0.998594 4.22102 0.838594 4.30102C0.778594 4.32102 0.638594 4.18102 0.558594 4.14102Z" fill="#002B55"/>
</svg></span>
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
import NominationsTable from './entities/Nominations/NominationsTable/nominationsTable.vue';
import NominationsFilter from './entities/Nominations/nominationsFilter.vue';
import { usePageStore } from './store/page.js';
import { defineEmits } from 'vue';

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