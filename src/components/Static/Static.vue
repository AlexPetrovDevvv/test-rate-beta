<template>
    <section class="rating-description">
        <div class="container">
            <section class="hero">
                <h1 class="hero__title">Рейтинг <span class="hero__title hero__title_red">юридических</span> телеграм-каналов</h1>
                <p class="hero__description">Мы вычислили самые авторитетные юридические телеграм-каналы. А еще собрали самые крупные и нишевые.<br>В качестве бонуса — подобрали способы оценки рекламы в них.</p>
            </section>
            <section class="about">
                <h2 class="about__title">О проекте</h2>
                <p class="about__text">Этот рейтинг в версии конца 2023 и начала 2024 года — совместная работа экспертной группы Veta, бюро Флавита и 80+ экспертов юридического рынка, которые любезно дали нам свои комментарии по наболевшим вопросам телеграм-повестки.</p>
                <p class="about__text">Здесь впервые собраны и структурированы больше 450+ юридических телеграм-каналов от крупнейших до нишевых и даже не подключённых к TGStat.</p>
                <p class="about__text">Впервые эксперты концентрированно высказались о том:</p>
                <ul class="about__list">
                    <li class="about__item">что на самом деле читают юристы;</li>
                    <li class="about__item">что считают авторитетным;<span class="paw-btn" aria-label="">🐾</span></li>
                    <li class="about__item">на сколько каналов подписываются и...</li>
                    <li class="about__item">о боже, наконец то мы узнаем бесят ли их сториз в Телеграм!</li>
                </ul>
                <p class="about__text">Результаты по номинациям и результаты опроса экспертов — ниже.</p>
                <p class="about__text">Если вы не нашли свой канал, но хотите, чтобы он попал в следующую подборку — пишите в бота. Разберёмся:)</p>
                <span class="paw-btn" aria-label="">🐾</span>
            </section>
        </div>
    </section>
</template>

<script setup>
        
</script>

<style lang="sass">

.rating-description
    margin-top: 50px

.hero
    &__title
        color: #F7F7F7
        font-size: 54px
        font-style: normal
        font-weight: 800
        line-height: 92%
        max-width: 630px
        &_red
            color: #E51A3C
            font-weight: 800
    &__description
        font-size: 20px
        font-style: normal
        font-weight: 400
        line-height: 144%
        max-width: 550px
        margin-top: 35px

.about
    margin-top: 100px
    &__title
        color: #F7F7F7
        font-size: 44px
        font-style: normal
        font-weight: 800
        line-height: 92%
    &__text
        color: #D4EBFF
        font-size: 18px
        font-style: normal
        font-weight: 400
        line-height: 144%
        margin-top: 20px
        max-width: 657px
        &:first-child
            margin-top: 42px
    &__list
        margin-top: 20px
    &__item
        color: #D4EBFF
        font-size: 18px
        font-style: normal
        font-weight: 400
        line-height: 144%
        display: flex
        align-items: center
        gap: 13px
        &:not(:first-child)
            margin-top: 20px
        &::before
            content: "—"
            display: block
            color: rgb(229, 26, 60)
</style>