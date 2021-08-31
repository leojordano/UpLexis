<template>
  <div class="home">
    <Banner />
    <div class="home__body">
      <div class="home__body__tabs">
        <div class="home__body__tabs__container">
          <span
            v-for="(Category, key) in option.getFilterData"
            :key="key"
            @click="filter(Category.name)"
          >
            <CheckCategory
              :Title="getCategoryName(Category.name, key)"
              :CheckedValue="key===filterOption ? 'checked' : ''"
            />
          </span>
        </div>
      </div>
      <div class="home__body__select-order">
        <label for="selectCategory"> ORDENAR: </label>
        <select id="selectCategory" name="selectCategory" @change="sort($event)">
            <option value="original-order">
              Ordem Original
            </option>
            <option
              v-for="(Category, key) in option.getSortData"
              :key="key"
              :value="Category"
            >
              {{ OrderListName.find((x) => x.ref === Category ).name }}
            </option>
        </select>
      </div>
      <div>
        <isotope
          ref="cpt"
          :list="this.Cards"
          id="root_isotope"
          class="home__body__container"
          :options="this.option"
          :item-selector="'element-item'"
          @filter="filterOption = arguments[0]"
          @sort="sortOption=arguments[0]"
        >
          <div v-for="CardItem in Cards" :key="CardItem.id">
            <Card
              :Category="CardItem.Category"
              :Title="CardItem.name"
              :Description="CardItem.description"
              :Price="String(CardItem.price)"
              :To="String(CardItem.id)"
            />
          </div>
        </isotope>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import isotope from 'vueisotope';
import Banner from '@/components/Home/Banner/Banner.vue';
import Card from '@/components/Home/Card/Card.vue';
import CheckCategory from '@/components/Home/CheckCategory/CheckCategory.vue';
import Categories from '@/assets/Categories';
import Cards from '@/assets/Cards';

export default {
  name: 'Home',
  components: {
    Banner,
    Card,
    CheckCategory,
    isotope,
  },

  data() {
    return {
      CategoriesList: Categories,
      FilterActive: 2,
      ActiveCategories: [],
      DisplayCards: [],
      Cards,
      OrderListName: [
        { name: 'Nome', ref: 'name' },
        { name: 'Preço', ref: 'price' },
        { name: 'Lançamento', ref: 'date' },
      ],
      filterOption: 'all',
      sortOption: 'original-order',
      option: {
        masonry: {
          columnWidth: 40,
          isFitWidth: true,
        },
        itemSelector: '.element-item',
        getFilterData: {
          all() {
            return true;
          },
          Profissionais(el) {
            return el.Category === 1;
          },
          Reguladores(el) {
            return el.Category === 2;
          },
          SócioAmbiental(el) {
            return el.Category === 3;
          },
          Juridico(el) {
            return el.Category === 4;
          },
          ListasRestritivas(el) {
            return el.Category === 5;
          },
          Mídia(el) {
            return el.Category === 6;
          },
          BenseImóveis(el) {
            return el.Category === 7;
          },
          Cadastro(el) {
            return el.Category === 8;
          },
          Financeiro(el) {
            return el.Category === 9;
          },
        },
        getSortData: {
          name: 'name',
          price: 'price',
          date: 'date',
        },
      },
    };
  },

  created() {
    this.DisplayCards = this.Cards;
  },

  methods: {
    onChange(event) {
      this.FilterActive = event;
      console.log(event);
    },
    filter(key) {
      this.$refs.cpt.filter(key);
    },
    sort(e) {
      this.$refs.cpt.sort(e.target.value);
    },
    getCategoryName(name, key) {
      if (key !== 'all') {
        return this.CategoriesList.find((x) => x.funcName === name)?.name ?? '';
      }

      return 'Todos';
    },

  },

  watch: {
    FilterActive() {
      if (this.FilterActive !== '0') {
        const render = this.Cards.filter((x) => x.Category === this.FilterActive);
        this.DisplayCards = render;
      } else if (this.FilterActive === '0') {
        this.DisplayCards = this.Cards;
      }
    },
  },
};
</script>

<style scoped src="./Home.scss" lang="scss"></style>
