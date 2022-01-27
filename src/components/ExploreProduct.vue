<template>
<div id="explore-product" class="my-10">
  <v-container>
    <h1 class="text-center">Explore</h1>
    <v-row class="mt-5">
      <v-col>
        <v-select :items="rarityOptions" v-model="selectedRarity" label="Rarity" solo flat outlined></v-select>
      </v-col>
      <v-col>
        <v-select :items="categoryOptions" v-model="selectedCategory" label="Category" solo flat outlined></v-select>
      </v-col>
      <v-col>
        <v-text-field solo flat outlined v-model="searchKey" label="Search Query"></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-btn block tile outlined @click="resetFilter" :disabled="!filtered">Reset</v-btn>
      </v-col>
    </v-row>
    <v-row class="text-center" align="center" justify="center">
      <v-col class="d-flex child-flex" cols="4" v-for="(item, index) in filteredProducts" :key="index">
        <v-hover>
          <!-- <img :src="require(`@/assets${products[index].gifPath}`)" @click="openProduct(products[index])" style="cursor: pointer" :lazy-src="require(`@/assets${products[index].gifPath}`)" aspect-ratio="1" :alt="`${products[index].name}`"> -->
          <img :src="require(`@/assets${item.gifPath}`)" @click="openProduct(item)" style="cursor: pointer" :lazy-src="require(`@/assets${item.gifPath}`)" aspect-ratio="1" :alt="`${item.name}`">
        </v-hover>
      </v-col>
    </v-row>
    <v-row align="center" justify="center">
      <v-btn class="text-center" tile outlined @click="loadMore()" v-if="productsToShow < products.length || products.length > productsToShow" :disabled="filtered" x-large>Load More</v-btn>
    </v-row>
    <v-dialog v-model="dialog" @input="dialogClosed" max-width="900">
      <template v-slot:default="dialog">
        <v-card>
          <v-toolbar dark>NFT {{ selectedProduct[0].name.substring(0, 3) }}</v-toolbar>
          <v-card-text>
            <v-container>
              <v-row class="mt-5">
                <v-col>
                  <h1 class="display-3 font-weight-bold">{{ selectedProduct[0].name.substring(0, 3) }}</h1>
                  <v-row class="mt-10">
                    <v-col>
                      <h1 class="display-2">Rarity</h1>
                      <h2 class="display-1 mt-5 font-weight-light">{{ selectedProduct[0].rarity }}</h2>
                    </v-col>
                  </v-row>
                  <v-row class="mt-10">
                    <v-col>
                      <h1 class="display-2">Category</h1>
                      <h2 class="display-1 mt-5 font-weight-light">{{ selectedProduct[0].category }}</h2>
                    </v-col>
                  </v-row>
                </v-col>
                <v-col>
                  <img :src="require(`@/assets${selectedProduct[0].gifPath}`)" alt="">
                </v-col>
              </v-row>
            </v-container>
          </v-card-text>
          <v-card-actions class="justify-end">
            <v-btn text @click="dialog.value = false">Close</v-btn>
          </v-card-actions>
        </v-card>
      </template>
    </v-dialog>
  </v-container>
</div>
</template>

<script>
/* eslint-disable vue/no-side-effects-in-computed-properties */

export default {
  name: 'explore-product',
  data() {
    return {
      dialog: false,
      filtered: false,
      productsToShow: 9,
      searchKey: '',
      rarityOptions: ['Common', 'Uncommon', 'Rare'],
      categoryOptions: ['GENESIS', 'TENS', 'TWIN DIGITS', 'CONTINUOUS', 'RANDOM', 'PRIME'],
      selectedCategory: '',
      selectedRarity: '',
      selectedProduct: [],
      products: [{
          name: '001 NFThunder',
          gifPath: '/001/001 - NFThunder.gif',
          frontImage: '001/001 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134359',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'You have to be ood to be number one.',
          author: 'Dr. Seuss'
        },
        {
          name: '002 NFThunder',
          gifPath: '/002/002 - NFThunder.gif',
          frontImage: '002/002 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134360',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'Second place is just the first place loser.',
          author: 'Dale Earnhardt'
        },
        {
          name: '003 NFThunder',
          gifPath: '/003/003 - NFThunder.gif',
          frontImage: '003/003 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134362',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'Stay hungry. Stay foolish.',
          author: 'Steve Jobs'
        },
        {
          name: '004 NFThunder',
          gifPath: '/004/004 - NFThunder.gif',
          frontImage: '004/004 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134865',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'Anyone who has never made a mistake has never tried anything new',
          author: 'Albert Einstein'
        },
        {
          name: '005 NFThunder',
          gifPath: '/005/005 - NFThunder.gif',
          frontImage: '005/005 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134866',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'It\'s possible for ordinary people to choose to be extraordinary',
          author: 'Elon Musk'
        },
        {
          name: '006 NFThunder',
          gifPath: '/006/006 - NFThunder.gif',
          frontImage: '006/006 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134867',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'All successes begin with self-discipline',
          author: 'Dwayne Johnson'
        },
        {
          name: '007 NFThunder',
          gifPath: '/007/007 - NFThunder.gif',
          frontImage: '007/007 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135644',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'Tough times never last, but tough people do.',
          author: 'Robert Schuller'
        },
        {
          name: '008 NFThunder',
          gifPath: '/008/008 - NFThunder.gif',
          frontImage: '008/008 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135719',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'Fall seven times, stand up eight',
          author: 'Japanese proverb'
        },
        {
          name: '009 NFThunder',
          gifPath: '/009/009 - NFThunder.gif',
          frontImage: '009/009 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135752',
          rarity: 'Rare',
          category: 'GENESIS',
          description: 'If you can dream it, you can do it.',
          author: 'Walt Disney'
        },
        {
          name: '010 NFThunder',
          gifPath: '/010/010 - NFThunder.gif',
          frontImage: '010/010 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135870',
          rarity: 'Rare',
          category: 'TENS',
          description: 'Aim for the moon. If you miss, you may hit a star.',
          author: 'Clement Stone'
        },
        {
          name: '011 NFThunder',
          gifPath: '/011/011 - NFThunder.gif',
          frontImage: '011/011 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136361',
          rarity: 'Uncommon',
          category: 'TWIN DIGITS',
          description: 'When writing the story of your life, don\'t let anyone else hold the pen.',
          author: 'Harley Davidson'
        },
        {
          name: '012 NFThunder',
          gifPath: '/012/012 - NFThunder.gif',
          frontImage: '012/012 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136437',
          rarity: 'Rare',
          category: 'CONTINUOUS',
          description: 'To find yourself, think for yourself.',
          author: 'Socrates'
        },
        {
          name: '013 NFThunder',
          gifPath: '/013/013 - NFThunder.gif',
          frontImage: '013/013 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136438',
          rarity: 'Uncommon',
          category: 'PRIME',
          description: 'The best luck of all is the luck you make for yourself.',
          author: 'Irish Proverb'
        },
        {
          name: '014 NFThunder',
          gifPath: '/014/014 - NFThunder.gif',
          frontImage: '014/014 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136686',
          rarity: 'Common',
          category: 'RANDOM',
          description: 'Life is full of questions. Idiots are full of answers.',
          author: 'Socrates'
        },
        {
          name: '015 NFThunder',
          gifPath: '/015/015 - NFThunder.gif',
          frontImage: '015/015 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136702',
          rarity: 'Common',
          category: 'RANDOM',
          description: 'Chains of habit are too light to be felt until they are too heavy to be broken.',
          author: 'Warren Buffet'
        },
        {
          name: '016 NFThunder',
          gifPath: '/016/016 - NFThunder.gif',
          frontImage: '016/016 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136703',
          rarity: 'Common',
          category: 'RANDOM',
          description: 'Knowing is not enough, we must apply. Willing is not enough, we must do.',
          author: 'Bruce Lee'
        },
        {
          name: '017 NFThunder',
          gifPath: '/017/017 - NFThunder.gif',
          frontImage: '017/017 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136703',
          rarity: 'Uncommon',
          category: 'PRIME',
          description: 'Efforts and courage are not enough without purpose and direction',
          author: 'John F. Kennedy'
        },
        {
          name: '018 NFThunder',
          gifPath: '/018/018 - NFThunder.gif',
          frontImage: '018/018 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136957',
          rarity: 'Common',
          category: 'RANDOM',
          description: 'If opportunity doesn\'t knock, build a door.',
          author: 'Milton Berle'
        },
        {
          name: '019 NFThunder',
          gifPath: '/019/019 - NFThunder.gif',
          frontImage: '019/019 NFThund SF.png',
          link: 'https://app.pentas.io/nft/137525',
          rarity: 'Uncommon',
          category: 'PRIME',
          description: 'The supreme art of war is to subdue the enemy without fighting.',
          author: 'Sun Tzu'
        },
        {
          name: '020 NFThunder',
          gifPath: '/020/020 - NFThunder.gif',
          frontImage: '020/020 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138185',
          rarity: 'Rare',
          category: 'TENS',
          description: 'When times get tough, we don\'t give up. We get up.',
          author: 'Barrack Obama'
        },
        {
          name: '021 NFThunder',
          gifPath: '/021/021 - NFThunder.gif',
          frontImage: '021/021 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138186',
          rarity: 'Common',
          category: 'RANDOM',
          description: 'Don\'t be afraid to give up the good to go for the great.',
          author: 'John D. Rockfeller'
        },
        {
          name: '022 NFThunder',
          gifPath: '/022/022 - NFThunder.gif',
          frontImage: '022/022 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138439',
          rarity: 'Uncommon',
          category: 'TWIN DIGITS',
          description: 'You miss 100% of the shots you don\'t take.',
          author: 'John D. Rockfeller'
        },
        {
          name: '023 NFThunder',
          gifPath: '/023/023 - NFThunder.gif',
          frontImage: '023/023 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138440',
          rarity: 'Uncommon',
          category: 'PRIME',
          description: 'Heart is what separates the good from the great.',
          author: 'Michael Jordan'
        },
        {
          name: '024 NFThunder',
          gifPath: '/024/024 - NFThunder.gif',
          frontImage: '024/024 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138677',
          rarity: 'Common',
          category: 'RANDOM',
          description: 'Great things come from hard work and perseverance. No excuses.',
          author: 'Kobe Bryant'
        },
        {
          name: '025 NFThunder',
          gifPath: '/025/025 - NFThunder.gif',
          frontImage: '025/025 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138811',
          rarity: 'Common',
          category: 'RANDOM',
          description: 'A flower does not think of competing to the flower next to it. It just blooms.',
          author: 'Zen Shin'
        },
      ]
    }
  },
  methods: {
    loadMore() {
      if (this.products.length - this.productsToShow > 3) {
        this.productsToShow += 3
      } else {
        let selisih = this.products.length - this.productsToShow
        this.productsToShow += selisih
      }
    },
    resetFilter() {
      this.selectedCategory = ''
      this.selectedRarity = ''
      this.searchKey = ''
    },
    dialogClosed() {
      setTimeout(() => {
        this.selectedProduct = []
      }, 200)
    },
    openProduct(item) {
      this.selectedProduct.push({
        author: item.author,
        category: item.category,
        description: item.description,
        gifPath: item.gifPath,
        link: item.link,
        name: item.name,
        rarity: item.rarity,
      })
      this.dialog = true
    },
  },
  watch: {
    filteredProducts: function () {
      this.filtered = true
    }
  },
  computed: {
    filteredProducts() {
      let filtered = this.products

      if (this.selectedRarity != '' && this.selectedRarity) {
        filtered = filtered.filter((item) => {
          return item.rarity == this.selectedRarity
        })
      }

      if (this.selectedCategory != '' && this.selectedCategory) {
        filtered = filtered.filter((item) => {
          return item.category == this.selectedCategory
        })
      }

      if (this.searchKey != '' && this.searchKey) {
        filtered = filtered.filter((item) => {
          return item.name
            .toUpperCase()
            .includes(this.searchKey.toUpperCase())
        })
      }
      this.filtered = false
      return filtered.slice(0, this.productsToShow)
    }
  }
}
</script>
