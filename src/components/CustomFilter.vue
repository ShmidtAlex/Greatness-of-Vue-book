<template>
  <div class="container-fluid">
    <div class="background-photo" alt="puppy"></div>
    <!-- <img class="no-background" src="../assets/s1200.jpg" alt="little doggie"> -->
    <img class="background-photo" src="" alt="puppy"> <!--best way in my opinion-->
    <h1>Real Names of Superheroes</h1>
    <h4>(applying "| -kind filter")</h4>
    <ul class="list-group">
      <li v-for="(hero, index) in heroes" :key="index">{{hero | snitch }}</li><!--i.e. "осведомитель"-->
    </ul>
    <h3>filtration with third-party library (lodash)</h3>
    <h4> kids raiting based on intelligence </h4>
    <ul class="list-group">
      <li v-for="(kid, kidIndex) in orderedKidsList" :key="kidIndex">Name: {{ kid.name }}Strength: {{ kid.strength }}Intelligence {{ kid.intelligence }}</li>
    </ul>
    <button class="btn btn-primary" type="button" @click="reverseOrder">reverse!</button>
    <div class="container">
      <h3>Serp Filters</h3>
      <ul class="list-group inline">
        <li v-for="(amenity, amenityIndex) in amenities" :key="amenityIndex" class="amenity_button">
          <button class="btn">{{amenity.name}}</button></li>
      </ul>
      <div v-for="(hotel, hotelIndex) in hotels" :key="hotelIndex" class="hotel_item">
        <div class="hotel_photo">{{ hotel.photo }}</div>
        <div class="hotel_info">
          <div class="hotel_name">{{ hotel.name }}</div>
          <div class="hotel_address">{{ hotel.address }} </div>
          <div class="hotel_amenities">
            <ul class="list-group">
             <li v-for="(amenity, amenityIndex) in hotel.amenities" :key="amenityIndex" class="amenity_item"></li>
            </ul>
          </div>
          <div class="hotel_prices">{{hotel.price}}</div>
        </div>
      </div>
      
    </div>
  </div>
</template>
<script>
  import Vue from "vue";
  import _ from "lodash";


  Vue.filter('snitch', function(hero){
    return hero.secretId + ' - это ' + hero.firstName + ' ' + hero.lastName + ' в реальной жизни!';
  })
  //var _ = require('lodash');

  export default {
    name: 'Custom',
    data: function() {
      return {
        order: 'desc',
        heroes: [
          { firstName: 'Bruce', lastName: 'Wayne', secretId: 'Batman' },
          { firstName: 'Clark', lastName: 'Kent', secretId: 'Superman' },
          { firstName: 'Jay', lastName: 'Harrick', secretId: 'Flash' }, 
          { firstName: 'Peter', lastName: 'Parker', secretId: 'Spiderman' },       
        ],
        kids: [
          { name: 'Stan', strength: 70, intelligence: 70 }, 
          { name: 'Kyle', strength: 40, intelligence: 80 }, 
          { name: 'Eric', strength: 45, intelligence: 100 }, 
          { name: 'Kenny', strength: 100, intelligence: 50 }
        ],
        hotels: [
          { photo: "/some_address/some_photo.png", name: "Hotel Moscow Name", address: "Moscow, some street, 1",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'pool'}, { name: 'transfer'},
                { name: 'bath'}, { name: 'breakfast'}, { name: 'spa'}
              ],
            price: 3000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel  St.Pitersberg Name", address: "sSt.Pitersberg, some street, 2",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'transfer'},
                { name: 'bath'}, { name: 'breakfast'}, { name: 'spa'}
              ],
            price: 3000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Helsinki Name", address: "Helsinki, some street, 3",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'},
                { name: 'bath'}, { name: 'breakfast'}, { name: 'spa'}
              ],
            price: 3000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Barselona Name", address: "Barselona, some street, 4",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'}, { name: 'transfer'},
                { name: 'breakfast'}, { name: 'spa'}
              ],
            price: 3000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Berlin Name", address: "Berlin, some street, 5",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'}, { name: 'transfer'},
                { name: 'bath'}, { name: 'spa'}
              ],
            price: 3000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Lisbon Name", address: "Lisbon, some street, 6",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'}, { name: 'transfer'},
                { name: 'bath'}, { name: 'breakfast'}
              ],
            price: 3000  
           },
        ],
        amenities: [
          { name: 'wi-fi'},
          { name: 'bar'},
          { name: 'fitness'},
          { name: 'pool'},
          { name: 'transfer'},
          { name: 'bath'},
          { name: 'breakfast'},
          { name: 'spa'}
        ],
        hotels: [

        ]
      }
    },
    methods: {
      reverseOrder: function() {
        // console.log("it works!");
        this.order = (this.order === 'desc') ? 'asc' : 'desc';
      }
    },
    computed: {
      orderedKidsList: function(){
        let order = this.order;
        return _.orderBy(this.kids, 'intelligence', [order]); //first argument is an array,
        //second argument is a parameter of sorting
        //third argument is a type of sorting, defined in methods (see below);
      },
      
    },
    
  }
</script>
<style>
  .no-background {
    width: 50%;
    height: 50%
  }
  .background-photo {
    background-image: url('../assets/s1200.jpg');
    background-size: contain;
    height: 100px;
    width: 100px;
    background-repeat: no-repeat;
    color: transparent;
  }
  ul {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
  }

  li {
    list-style-type: none;
  }
  .container {
    width: 100%;
    height: 400px;
    margin: 35px 0;
  }
  .inline {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    width: 100%;
    flex-wrap: wrap;
  }
</style>