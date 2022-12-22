<template>
  <v-data-table
    :headers="headers"
    :items="products"
    class="elevation-1"
  >
    <template v-slot:item.type="{ item }">
      <v-chip
        :color="getColor(item.type)"
        dark
      >
        {{ item.type }}
      </v-chip>
    </template>

    <template v-slot:item.eugene="{ item }"><v-text-field v-model="item.value_column"></v-text-field>

    </template>

    <!-- count percentage -->
    <template v-slot:item.percentage_fact="{ item }"> {{Math.floor(item.number_fact / item.number_max * 100)}}% 

</template>


    <!-- count total weight -->
    <template v-slot:item.totalWeight="{ item }"> {{item.number_fact * item.weight}}

</template>


  </v-data-table>
</template>

<script>
  export default {
    data () {
      return {
        headers: [
          {
            text: 'Product',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Type', value: 'type' },
          { text: 'Lol_kek', value: 'eugene' },
          { text: 'Shape', value: 'shape' },
          { text: 'Number fact', value: 'number_fact' },
          { text: 'Number max', value: 'number_max' },
          { text: 'Percentage fact', value: 'percentage_fact' },
          { text: 'Weight', value: 'weight' },
          { text: 'Total weight', value: 'totalWeight' },
        ],
        products: [
          {
            name: 'Eugene',
            type: 'fruit',
            shape: '',
            value_column:'dsada',
            weight: 60,
            number_fact: 21,
            number_max: 60,

          },
          {
            name: 'Ice cream sandwich',
            calories: 237,
            fat: 9.0,
            carbs: 37,
            protein: 4.3,
            iron: '1%',
            value_column:'dsad',
            weight: 20,
            number_fact: 41,
            number_max: 70,
          },
          {
            name: 'Eclair',
            calories: 262,
            fat: 16.0,
            carbs: 23,
            protein: 6.0,
            iron: '7%',
            value_column:'',
            weight: 23,
            number_fact: 61,
            number_max: 163,
          },
          {
            name: 'Cupcake',
            calories: 305,
            fat: 3.7,
            carbs: 67,
            protein: 4.3,
            iron: '8%',
            value_column:'',
            weight: 12,
            number_fact: 41,
            number_max: 300,
          },
          // {
          //   name: 'Gingerbread',
          //   calories: 356,
          //   fat: 16.0,
          //   carbs: 49,
          //   protein: 3.9,
          //   iron: '16%',
          //   value_column:'4to-to napisal',
          //   weight: 36,
          // },
          // {
          //   name: 'Jelly bean',
          //   calories: 375,
          //   fat: 0.0,
          //   carbs: 94,
          //   protein: 0.0,
          //   iron: '0%',
          //   value_column:'4to-to napisal',
          //   weight: 13,
          // },
          // {
          //   name: 'Lollipop',
          //   calories: 392,
          //   fat: 0.2,
          //   carbs: 98,
          //   protein: 0,
          //   iron: '2%',
          //   value_column:'4to-to napisal',
          //   weight: 45,
          // },
          // {
          //   name: 'Honeycomb',
          //   calories: 408,
          //   fat: 3.2,
          //   carbs: 87,
          //   protein: 6.5,
          //   iron: '45%',
          //   value_column:'4to-to napisal',
          //   weight: 67,
          // },
          // {
          //   name: 'Donut',
          //   calories: 452,
          //   fat: 25.0,
          //   carbs: 51,
          //   protein: 4.9,
          //   iron: '22%',
          //   value_column:'4to-to napisal',
          //   weight: 54,
          // },
          // {
          //   name: 'KitKat',
          //   calories: 518,
          //   fat: 26.0,
          //   carbs: 65,
          //   protein: 7,
          //   iron: '6%',
          //   value_column:'4to-to napisal',
          //   weight: 21,
          // },
        ],
      }
    },
    methods: {
      getColor (type) {
        if (type == 'fruit') return 'red'
        // else if (calories > 200) return 'orange'
        else return 'green'
      },
    },
  }
</script>