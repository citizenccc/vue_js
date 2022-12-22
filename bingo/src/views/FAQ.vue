<!-- {{varia = Math.floor(item.number_fact / item.number_max * 100))}} -->

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

    <!-- only digits field -->

    <template v-slot:item.number_fact="{ item }">
      <v-text-field v-model="item.number_fact"
        hide-details
        single-line
        type="number"
        background-color="green">
      </v-text-field>
    

</template>

<template v-slot:item.number_max="{ item }">
      <v-text-field v-model="item.number_max"
        hide-details
        single-line
        type="number">
      </v-text-field>
    </template>

    <template v-slot:item.select_col="{ item }">
      <v-select v-model="item.type"
          :items="items"
          label="Type"
        ></v-select>
    </template>
    <!-- count percentage -->
    <template v-slot:item.percentage_fact="{ item }"> 

      <v-progress-linear
      :value="item.number_fact / item.number_max * 100"
      :color="percentColor(item.number_fact, item.number_max)"
      height="25"
      
    ><strong>{{ percentText(item.number_max, item.number_fact)}}</strong></v-progress-linear>

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
            sortable: true,
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
          { text: 'Select', value: 'select_col' },
          
        ],

        items:['fruit', 'pastry', 'vegetable', 'dairy'],

        products: [
          {
            name: 'Eugene',
            type: 'fruit',
            shape: '',
            value_column:'dsada',
            weight: 60,
            number_fact: 50,
            number_max: 60,

          },
          {
            name: 'Ice cream sandwich',
            type: 'dairy',
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
            type: 'pastry',
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
            name: 'Potato',
            type: 'vegetable',
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

      percentColor (value, total) {
        let percent = this.percentText(total, value)
        if(percent == 'Too big') return 'rgb(0,0,0)' ;
        percent = percent.replace('%','')
        console.log(percent)
        let red = 255
        let green = 255
        if(percent >= 50) red = 255 - ((percent - 50) / 50 * 255)
        if(percent <= 50) green = 127 - ((percent - 50) / 50 * 255)
        if(percent <= 20) green = ((percent - 50) / 50 * 255)
        const blue = 100
        return `rgb(${red},${green},${blue})`
      },
      percentText(total, value) {

        const percent = Math.floor(value / total * 100)
        if (percent > 100) return 'Too big'
        
        return (percent + '%')
      },

    },
  }
</script>



<!-- v-model connects data to a variable -->