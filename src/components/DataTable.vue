<template>
  <v-card>
    <v-card-title>
      Hazards
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
  <v-data-table
    class="table"
    :headers="headers"
    :items="hazards"
    :search="search"
    :pagination.sync="pagination"
    >
    <template slot="items" slot-scope="props">
      <td class="text-xs-left">
        <v-avatar size="42">
          <img :src="randomAvatar()" alt="avatar">
        </v-avatar>
      </td>
      <td class="text-xs-left">{{ props.item.name }}</td>
      <td class="text-xs-left">{{ props.item.employeeName }}</td>
      <td class="text-xs-left">{{ props.item.hazardId }}</td>
      <td class="text-xs-left">{{ props.item.category }}</td>
      <td class="text-xs-left">{{ props.item.description }}</td>
      <td class="text-xs-left">{{ props.item.employee.discipline }}</td>
    </template>
  ></v-data-table>
  </v-card>
</template>


<script>
import hazardsFromFile from './hazards.json'
const hazardsJson = hazardsFromFile;

/*
const avatars = [
  'https://avataaars.io/?accessoriesType=Blank&avatarStyle=Circle&clotheColor=PastelGreen&clotheType=ShirtScoopNeck&eyeType=Wink&eyebrowType=UnibrowNatural&facialHairColor=Black&facialHairType=MoustacheMagnum&hairColor=Platinum&mouthType=Concerned&skinColor=Tanned&topType=Turban',
  'https://avataaars.io/?accessoriesType=Sunglasses&avatarStyle=Circle&clotheColor=Gray02&clotheType=ShirtScoopNeck&eyeType=EyeRoll&eyebrowType=RaisedExcited&facialHairColor=Red&facialHairType=BeardMagestic&hairColor=Red&hatColor=White&mouthType=Twinkle&skinColor=DarkBrown&topType=LongHairBun',
  'https://avataaars.io/?accessoriesType=Prescription02&avatarStyle=Circle&clotheColor=Black&clotheType=ShirtVNeck&eyeType=Surprised&eyebrowType=Angry&facialHairColor=Blonde&facialHairType=Blank&hairColor=Blonde&hatColor=PastelOrange&mouthType=Smile&skinColor=Black&topType=LongHairNotTooLong',
  'https://avataaars.io/?accessoriesType=Round&avatarStyle=Circle&clotheColor=PastelOrange&clotheType=Overall&eyeType=Close&eyebrowType=AngryNatural&facialHairColor=Blonde&facialHairType=Blank&graphicType=Pizza&hairColor=Black&hatColor=PastelBlue&mouthType=Serious&skinColor=Light&topType=LongHairBigHair',
  'https://avataaars.io/?accessoriesType=Kurt&avatarStyle=Circle&clotheColor=Gray01&clotheType=BlazerShirt&eyeType=Surprised&eyebrowType=Default&facialHairColor=Red&facialHairType=Blank&graphicType=Selena&hairColor=Red&hatColor=Blue02&mouthType=Twinkle&skinColor=Pale&topType=LongHairCurly',
  'https://avataaars.io/?'
];*/

const avatars = [
  '1.jpg',
  '2.jpg',
  '3.jpg',
  '4.jpg',
  '5.jpg',
  '6.jpg',
  '7.jpg',
  '8.jpg',
  '9.jpg',
  '10.jpg',
];


export default {
  data() {
    return {
      pagination : {'sortBy': 'name', 'descending': true, 'rowsPerPage': 5},
      search: '',
      hazards: hazardsJson,
      headers: [
        {
          value: 'Avatar',
          align: 'left',
          sortable: false
        },
        {
          text: 'Hazard Name',
          value: 'name',
          align: 'left',
          sortable: true
        },
        {
          text: 'Employee Name',
          value: 'employeeName',
          align: 'left',
          sortable: true
        },
        {
          text: 'Hazard Id',
          value: 'hazardId',
          align: 'left',
          sortable: true
        },
        {
          text: 'Category',
          value: 'category',
          align: 'left',
          sortable: true
        },
        {
          text: 'Description',
          value: 'description',
          align: 'left',
          sortable: true
        },
        {
          text: 'Discipline',
          value: 'discipline',
          align: 'left',
          sortable: true
        }
      ]
    }
  },

  methods: {
    randomAvatar () {
      //return avatars[Math.floor(Math.random() * avatars.length)];
      const img = require('../assets/' + avatars[Math.floor(Math.random() * avatars.length)]);
      return img;
    },
  },

  created() {

 /*   const vm = this;

    vm.axios.get('https://jsonplaceholder.typicode.com/users').then(response => {
      var result = response && response.data;
      //// result.map(r => r.Category = 'Important');

      vm.users = result;
    });*/

  }
}
</script>

<style>
  .table {
    border-radius: 3px;
    background-clip: border-box;
    border: 1px solid rgba(0, 0, 0, 0.125);
    box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.21);
    background-color: transparent;
  }
  .th {
    font-weight:bold ;
    font-size:large;
     background-color: red;
  }
</style>
