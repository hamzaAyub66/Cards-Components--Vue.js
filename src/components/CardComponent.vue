<template>
  <v-container fluid>
    <div class="dashboard-page">
      <v-row no-gutters class="d-flex justify-space-between mt-10 mb-6">
        <h1 class="page-title">Cards</h1>
      </v-row>

      <v-row>
        <v-col lg="4" sm="5" md="5" cols="12" v-for="item in cardItems" :key="item.id">
          <v-card
            class="mx-auto my-12"
          >
            <v-img
              height="250"
              src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
            ></v-img>

            <v-card-title>{{ item.title }}</v-card-title>
            <v-card-text>
              <div class="my-1 text-subtitle-1">
                {{ item.membership }}
              </div>
              <div>{{ item.description }}</div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>

    </div>
  </v-container>
</template>

<script>


export default {
  name: "CardComponent",
  components: {
   
  },
  data() {
    return {

       cardItems: [
          { id: '1' , title: 'Cafe Badilico', image: 'https://cdn.vuetifyjs.com/images/cards/cooking.png' , membership: 'Gold' , description:'Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating' },
        ],
    };
  },
  methods: {

    },

  mounted() {
   
  },
};
</script>


