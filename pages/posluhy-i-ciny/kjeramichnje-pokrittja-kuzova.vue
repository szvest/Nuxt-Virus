<template>
  <div>
    <div class="jumbotron">
      <sercivesBreadcrumbs
        :heading="heading"
        class="desktop-tablet-only"
      />
      <div class="container text-left">
        <h2 class="info-pages mobile-only">
          {{ heading }}
        </h2>
        <div class="row">
          <div class="col-xl-6 text-center">
            <b-img-lazy
              src="~assets/img/Керамічнепокриття.jpg"
              :alt="heading"
            />
          </div>
          <div class="col-xl-6">
            <h2 class="info-pages desktop-only">
              {{ heading }}
            </h2>
            <p>{{ firstParagraph }}</p>
            <p>
              {{ secondParagraph }}
              <br>• твердістю (яка в деяких випадках поступається лише алмазу)
              <br>• хімічною стійкістю <br>• гідрофобністю
            </p>
            <p>{{ thirdParagraph }}</p>
            <p>{{ fourthParagraph }}</p>
            <p>{{ fifthParagraph }}</p>
            <p class="red">
              <b>{{ sixthParagraph }}</b>
            </p>
          </div>
        </div>
        <h2 class="pt-2">
          ЩО ВХОДИТЬ В ПОСЛУГУ?
        </h2>
        <ul class="ml-3">
          <li
            v-for="(items, index) in inclusiveInService"
            :key="index"
          >
            {{ items.services }}
          </li>
        </ul>

        <h2 class="red">
          {{ timeTaken }}
        </h2>

        <servicesYoutubeVideo
          :video-url="videoUrl"
          :title="`${heading} Video`"
        />

        <serviceCategories
          :category1="category1"
          :category2="category2"
          :category3="category3"
        />
      </div>
    </div>

    <ContactForm :service="service" />

    <progressSection />
  </div>
</template>

<script>
export default {
  data () {
    return {
      service: 'Керамічне покриття кузова',
      heading: 'Керамічне покриття кузова',
      category1: '12999 грн',
      category2: '14499 грн',
      category3: '15999 грн',
      videoUrl: 'https://www.youtube.com/embed/z8fG5P_YFss',
      firstParagraph:
        'Керамічне покриття автомобіля - це тонка плівка на поверхні ЛКП кузова, утворена зернами оксиду титану, діоксиду кремнію, карбідів та інших неорганічних сполук. Йдеться про зерна розміром до 100 нанометрів (мільярдна частина метра!)',
      secondParagraph:
        'Що входять до складу кераміки речовини володіють декількома важливими властивостями:',
      thirdParagraph:
        'Ось чому оброблена керамікою машина захищена від впливу реагентів, УФ-променів, плюс круто блищить, набагато простіше миється і відмінно відштовхує воду і бруд.',
      fourthParagraph:
        'Термін служби кераміки без корекції до 1,5 років, з корекцією до 3 років.',
      fifthParagraph:
        'Якщо автомобіль вже з пробігом - перед нанесенням кераміки його необхідно відполірувати.',
      sixthParagraph:
        'Важливо! Полірування кузова для авто з пробігом НЕ ВКЛЮЧЕНО в вартість захисного покриття.',
      inclusiveInService: [
        {
          services:
            'Мийка кузова, при необхідності очищення від слідів бітуму і дорожньої розмітки'
        },
        {
          services:
            'Детейлінг-полірування кузова (для авто з пробігом) / фінішне полірування для нових авто'
        },
        {
          services: 'Підготовка кузова до нанесення покриття'
        },
        {
          services: 'Нанесення захисного покриття'
        },
        {
          services: 'Фінішний шар покриття'
        },
        {
          services: 'По детальне запікання фінішного шару'
        },
        {
          services: 'Вологе прибирання салону (включаючи багажник)'
        }
      ],
      timeTaken: 'Час виконання послуги 1-2 дні'
    }
  },
  mounted () {
    if (process.client) {
      this.$scrollTo('#top-contact', 100, { force: true })
    }
  },
  head () {
    return {
      title: this.heading.slice(0, 60),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.firstParagraph.slice(0, 320)
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~assets/scss/servicesPages.scss";
</style>
