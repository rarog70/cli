<template>
  <div class="container pt1">
    <div class="card center">
      <h1>Актуальные новости {{ now }}</h1>
      <span
        >Открыто: <strong>{{ openRate }}</strong> | Прочитано:
        <strong>{{ readRate }}</strong></span
      >
    </div>

    <app-list>
      <template #default="{ iter, idx }">
        <strong>{{ idx + 1 }} </strong>
        <span style="color: brown">&nbsp;-&nbsp;Ithem:&nbsp;{{ iter }}</span>
      </template>
    </app-list>

    <AppNews
      v-for="item in news"
      :key="item.id"
      :title="item.title"
      :id="item.id"
      :body="item.body"
      :is-open="item.isOpen"
      :was-read="item.wasRead"
      @open-news="openNews"
      @read-news="readNews"
      @unmark="unreadNews"
    />
  </div>
</template>

<script>
import AppNews from "./AppNews.vue";
import AppList from "./AppList.vue";
export default {
  data() {
    return {
      now: new Date().toLocaleDateString(),
      openRate: 0,
      readRate: 0,
      news: [
        {
          title: "Первая новость",
          id: 1,
          isOpen: false,
          wasRead: false,
          body: "Minim ex tempor irure id ipsum aliquip quis commodo quis. Eiusmod ad pariatur nisi eiusmod consequat Lorem amet non quis ullamco. Exercitation pariatur reprehenderit non duis ullamco ea occaecat quis. Exercitation dolor aute exercitation aliqua enim culpa est commodo voluptate nostrud officia. Occaecat dolore qui deserunt minim incididunt fugiat. Pariatur ex ad velit dolore laboris adipisicing ullamco fugiat cupidatat incididunt exercitation. Exercitation eiusmod ex aliquip adipisicing nostrud incididunt consequat veniam reprehenderit do ea.",
        },
        {
          title: "Вторая новость",
          id: 2,
          isOpen: false,
          wasRead: false,
          body: "Amet voluptate exercitation irure ipsum sunt irure mollit nisi Lorem. Cillum laborum dolor exercitation aute quis fugiat amet qui nulla cillum esse sint. Pariatur qui incididunt enim labore ipsum qui laborum dolor exercitation. Aliqua pariatur aute cupidatat et culpa aliqua cupidatat. Sit eiusmod exercitation sunt magna incididunt duis adipisicing minim deserunt. Et proident eu ea cillum in aute aliqua consequat magna sunt consectetur.",
        },
        {
          title: "Третья новость",
          id: 3,
          isOpen: false,
          wasRead: false,
          body: "Aute ex ea proident ea duis deserunt aute cillum labore dolor laboris veniam sunt mollit. Ex excepteur est nisi nulla qui in esse irure incididunt elit et incididunt. Cillum pariatur commodo exercitation consectetur ullamco. Qui sit et cillum ex fugiat ut velit quis exercitation occaecat laboris cillum tempor reprehenderit. Excepteur aliqua aliqua ipsum anim magna ex elit ad ad consectetur esse laboris amet nostrud.",
        },
      ],
    };
  },
  components: { AppNews, AppList },
  methods: {
    openNews() {
      this.openRate++;
    },
    readNews(id) {
      const idx = this.news.findIndex((item) => item.id === id);
      this.news[idx].wasRead = true;
      this.readRate++;
    },
    unreadNews(id) {
      const idx = this.news.findIndex((item) => item.id === id);
      this.news[idx].wasRead = false;
      this.readRate--;
    },
  },
};
</script>
