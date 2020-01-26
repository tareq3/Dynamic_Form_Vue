<template>
  <div class="hello container">
    <form >
      <h1>Dynamic Apartment Form</h1>
        <div class="row">
            <div class="col-xs-2">
                <button type="button" v-on:click="addNewApartment" class="btn btn-block btn-success">
                    Add +
                </button>
            </div>
            <div class="col-xs-10">
                Would you like add more apartments?
            </div>
        </div>
        <div v-for="(apartment,index) in apartments" :key="index">
  
           <div class="row">
                <div class="col-xs-2">
                    <label>&nbsp;</label>
                    <button type="button" v-on:click="removeApartment(index)" class="btn btn-block btn-danger">
                        Rem -
                    </button>
                </div>
                <div class="form-group col-xs-5">
                    <label>Price (HUF)</label>
                    <input v-model="apartment.price" type="number"
                           class="form-control" placeholder="Price">
                </div>
                <div class="form-group col-xs-5">
                    <label>Rooms (PCS)</label>
                    <input v-model="apartment.rooms" type="number"
                          class="form-control" placeholder="Rooms">
                </div>
        </div>
        </div>
    </form>
    {{apartments}}
  </div>
</template>

<script>
import Vue from'vue';
export default {
  name: 'HelloWorld',
  data(){
    return{
      apartment: {
      price: '',
      rooms: ''
    },
    apartments: [{price:'1500', rooms:'4'}],
    }
  },
   

  methods:{
      addNewApartment: function () {
        console.log(this.apartment)
    //    this.apartments.push({price:'', rooms:''})
      this.apartments.push(Vue.util.extend({},this.apartment)) //this line uses the apartment model and craete a clone of that object
    },
    removeApartment: function (index) {
     // this.apartments.splice(index, 1);
      Vue.delete(this.apartments, index);
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
