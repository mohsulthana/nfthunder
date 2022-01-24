<template>
<div id="explore-product" class="my-10">
  <v-container>
    <h1 class="text-center">Explore</h1>
    <v-row class="mt-5">
      <v-col>
        <v-select :items="items" label="Rarity" solo flat outlined></v-select>
      </v-col>
      <v-col>
        <v-select :items="items" label="Category" solo flat outlined></v-select>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-btn block tile outlined>Reset</v-btn>
      </v-col>
    </v-row>
    <v-row class="text-center">
      <v-col class="d-flex child-flex" cols="4" v-for="(item, index) in products" :key="index">
        <v-hover>
          <img :src="require(`@/assets${item.gifPath}`)" @click="openProduct(item.link)" style="cursor: pointer" :lazy-src="require(`@/assets${item.gifPath}`)" aspect-ratio="1" :alt="`${item.name}`">
        </v-hover>
      </v-col>
    </v-row>
  </v-container>
</div>
</template>

<script>
export default {
  name: 'explore-product',
  data() {
    return {
      products: [{
          name: '001 NFThunder',
          gifPath: '/001/001 - NFThunder.gif',
          frontImage: '001/001 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134359'
        },
        {
          name: '002 NFThunder',
          gifPath: '/002/002 - NFThunder.gif',
          frontImage: '002/002 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134360'
        },
        {
          name: '003 NFThunder',
          gifPath: '/003/003 - NFThunder.gif',
          frontImage: '003/003 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134362'
        },
        {
          name: '004 NFThunder',
          gifPath: '/004/004 - NFThunder.gif',
          frontImage: '004/004 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134865'
        },
        {
          name: '005 NFThunder',
          gifPath: '/005/005 - NFThunder.gif',
          frontImage: '005/005 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134866'
        },
        {
          name: '006 NFThunder',
          gifPath: '/004/004 - NFThunder.gif',
          frontImage: '004/004 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134867'
        },
        {
          name: '007 NFThunder',
          gifPath: '/007/007 - NFThunder.gif',
          frontImage: '007/007 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135644'
        },
        {
          name: '008 NFThunder',
          gifPath: '/008/008 - NFThunder.gif',
          frontImage: '008/008 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135719'
        },
        {
          name: '009 NFThunder',
          gifPath: '/009/009 - NFThunder.gif',
          frontImage: '009/009 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135752'
        },
        {
          name: '010 NFThunder',
          gifPath: '/010/010 - NFThunder.gif',
          frontImage: '010/010 NFThund SF.png',
          link: 'https://app.pentas.io/nft/135870'
        },
        {
          name: '011 NFThunder',
          gifPath: '/011/011 - NFThunder.gif',
          frontImage: '011/011 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136361'
        },
        {
          name: '012 NFThunder',
          gifPath: '/012/012 - NFThunder.gif',
          frontImage: '012/012 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136437'
        },
        {
          name: '013 NFThunder',
          gifPath: '/013/013 - NFThunder.gif',
          frontImage: '013/013 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136438'
        },
        {
          name: '014 NFThunder',
          gifPath: '/014/014 - NFThunder.gif',
          frontImage: '014/014 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136686'
        },
        {
          name: '015 NFThunder',
          gifPath: '/015/015 - NFThunder.gif',
          frontImage: '015/015 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136702'
        },
        {
          name: '016 NFThunder',
          gifPath: '/016/016 - NFThunder.gif',
          frontImage: '016/016 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136703'
        },
        {
          name: '017 NFThunder',
          gifPath: '/017/017 - NFThunder.gif',
          frontImage: '017/017 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136703'
        },
        {
          name: '018 NFThunder',
          gifPath: '/018/018 - NFThunder.gif',
          frontImage: '018/018 NFThund SF.png',
          link: 'https://app.pentas.io/nft/136957'
        },
        {
          name: '019 NFThunder',
          gifPath: '/019/019 - NFThunder.gif',
          frontImage: '019/019 NFThund SF.png',
          link: 'https://app.pentas.io/nft/137525'
        },
        {
          name: '020 NFThunder',
          gifPath: '/020/020 - NFThunder.gif',
          frontImage: '020/020 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138185'
        },
        {
          name: '021 NFThunder',
          gifPath: '/021/021 - NFThunder.gif',
          frontImage: '021/021 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138186'
        },
        {
          name: '021 NFThunder',
          gifPath: '/021/021 - NFThunder.gif',
          frontImage: '021/021 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138439'
        },
        {
          name: '023 NFThunder',
          gifPath: '/023/023 - NFThunder.gif',
          frontImage: '023/023 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138440'
        },
        {
          name: '023 NFThunder',
          gifPath: '/023/023 - NFThunder.gif',
          frontImage: '023/023 NFThund SF.png',
          link: 'https://app.pentas.io/nft/134865'
        },
        {
          name: '024 NFThunder',
          gifPath: '/024/024 - NFThunder.gif',
          frontImage: '024/024 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138677'
        },
        {
          name: '025 NFThunder',
          gifPath: '/025/025 - NFThunder.gif',
          frontImage: '025/025 NFThund SF.png',
          link: 'https://app.pentas.io/nft/138811'
        },
      ]
    }
  },
  methods: {
    openProduct(link) {
      window.open(link)
    }
  }
}
</script>
