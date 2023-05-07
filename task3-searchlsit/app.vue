<template>
   
   <input type="text" v-model="input" placeholder="search list of doctors" @input="onSearch" />
  
   <table border="2 px" class="t1" v-if="searchoccured">
      <th>name</th>
      <th>specalization</th>
      <th>fees</th>
      <th>clinic</th>
      <tr v-for="(doc, index) in doctorlist" v-bind:key="index">
        <td>{{ doc.name }}</td>
        <td>{{ doc.specalization }}</td>
        <td>{{ doc.fees }}</td>
        <td>{{ doc.clinic }}</td>

      </tr>
   </table>
    
</template>
<script>

export default{
  
  data(){
    return{
      doctorlist:[{
        name:'Dr.Suresh Raina',
        specalization:'Orthopedics',
        fees:500,
        clinic:'JJ hospital'
      },
      {
        name:'Dr.M.S.Dhoni',
        specalization:'Internal Medicine',
        fees:1200,
        clinic:'AA hospital'
      },
    {
      name:'Dr.Rohit Sharma',
        specalization:'Gynecology',
        fees:1000,
        clinic:'RS hospital'
    }],
    input:'',
    drlist:[],
    searchoccured:false,
  }
 },
mounted() {
    this.drlist = this.doctorlist;
  },
methods: {
    onSearch() {
      this.searchoccured=true;
      this.doctorlist= this.drlist.filter((doc) =>
     doc.name.toLowerCase().includes(this.input.toLowerCase().trim())
    
   );
    },
    
  },
}
 </script>

