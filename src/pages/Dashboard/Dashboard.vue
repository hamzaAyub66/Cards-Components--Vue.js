<template>
  <v-container fluid>
    <div class="dashboard-page">
      <v-row no-gutters class="d-flex justify-space-between mt-10 mb-6">
        <h1 class="page-title">Cards</h1>
        <v-menu offset-y>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              v-bind="attrs"
              v-on="on"
              dark
              @click.stop="drawer = !drawer"
              color="secondary"
              class="text-capitalize button-shadow mr-1"
              >Create Cards</v-btn
            >
            <v-navigation-drawer
                v-model="drawer"
                absolute
                temporary
                right
                width="374"
              >
                <v-list-item>
                  <v-list-item-content>
                    <v-list-item-title>Add card</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>

               
                 <div class="mx-4"> 
                  <v-form
                    ref="form"
                    v-model="valid"
                    lazy-validation
                    
                  >
                   
                        <v-text-field
                          v-model="Fname"
                          :counter="10"
                          :rules="nameRules"
                          label="First Name"
                          outlined
                          required
                        ></v-text-field>
                         <v-text-field
                          v-model="Lname"
                          :counter="10"
                          :rules="nameRules"
                          label="Last Name"
                          outlined
                          required
                        ></v-text-field>

                        <v-select
                          v-model="select"
                          :items="items"
                          :rules="[v => !!v || 'Membership Tier is required']"
                          label="Membership Tier"
                          outlined
                          required
                        ></v-select>

                        <v-textarea
                          v-model="description"
                          :counter="500"
                          :rules="descriptionRules"
                          label="Description"
                          outlined
                          required
                        ></v-textarea>

                        <v-btn
                          :disabled="!valid"
                          color="success"
                          class="mr-4 my-2"
                          @click="validate"
                        >
                          Submit
                        </v-btn>
                  
                  </v-form>
                  </div>
                
              </v-navigation-drawer>
          </template>
        </v-menu>
      </v-row>

      <v-row>
        <v-col lg="4" sm="5" md="5" cols="12" v-for="item in cardItems" :key="item.id">
          <router-link :to="'dashboard/' + item.id" >
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
          </router-link>
        </v-col>
      </v-row>

    </div>
  </v-container>
</template>

<script>


export default {
  name: "Dashboard",
  components: {
   
  },
  data() {
    return {
     drawer: false,
      valid: true,
      Fname: '',
      Lname: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      description: '',
       descriptionRules: [
        v => !!v || 'Description is required',
        v => (v && v.length <= 500) || 'Name must be less than 500 characters',
      ],
      select: null,
      items: [
        'Gold',
        'Silver',
        'Platinum',
      ],

       cardItems: [
          { id: '1' , title: 'Cafe Badilico', image: 'https://cdn.vuetifyjs.com/images/cards/cooking.png' , membership: 'Gold' , description:'Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating' },
          { id: '2' ,title: 'Edward jacsom', image: 'https://cdn.vuetifyjs.com/images/cards/cooking.png', membership: 'Silver' , description:'Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating' },
          { id: '3' ,title: 'Tailor fitto', image: 'https://cdn.vuetifyjs.com/images/cards/cooking.png' ,membership: 'Platinum' , description:'Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating'  },
        ],
    };
  },
  methods: {

    validate () {
        if(this.$refs.form.validate()) {
          this.$refs.form.validate()
          this.drawer = false;
        }
      },

    },

  mounted() {
   
  },
};
</script>

<style src="./Dashboard.scss" lang="scss"/>
