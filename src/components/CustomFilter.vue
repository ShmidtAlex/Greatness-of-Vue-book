<template>
  <div class="container-fluid">
    <div class="background-photo" alt="puppy"></div>
    <!-- <img class="no-background" src="../assets/s1200.jpg" alt="little doggie"> -->
    <img class="background-photo" src="" alt="puppy"> <!--best way in my opinion-->
    <div class="separated_block">
      <h1>Real Names of Superheroes</h1>
      <h4>(applying "| -kind filter")</h4>
      <ul class="list-group">
        <li v-for="(hero, index) in heroes" :key="index">{{hero | snitch }}</li><!--i.e. "осведомитель"-->
      </ul>
    </div>
    <div class="separated_block">
      <h3>filtration with third-party library (lodash)</h3>
      <h4> kids raiting based on intelligence </h4>
      <ul class="list-group">
        <li v-for="(kid, kidIndex) in orderedKidsList" :key="kidIndex">Name: {{ kid.name }}, Strength: {{ kid.strength }}, Intelligence {{ kid.intelligence }}</li>
      </ul>
      <button class="btn btn-primary" type="button" @click="reverseOrder">reverse!</button>
    </div>
    <div class="separated_block">
      <div class="container">
      <h3>Serp Filters</h3>
      <ul class="list-group inline">
        <li v-for="(amenity, amenityIndex) in amenities" :key="amenityIndex" class="amenity_button">
          <button @click="changeFilterValue(amenity.name)" class="btn">{{amenity.name}}</button></li>
      </ul>
      <!-- <div>this div is really exist {{hotels}}</div> -->
      <div v-for="(hotel, hotelIndex) in showHasAmenityOnly" :key="hotelIndex" class="hotel_item">
        <div><b><i>{{ hotelIndex+1 }}</i></b></div>
          <div class="hotel_photo">{{ hotel.photo }}</div>
          <div class="hotel_info">
            <div class="hotel_name">{{ hotel.name }}</div>
            <div class="hotel_address">{{ hotel.address }} </div>
            <div class="hotel_amenities">
              <ul class="list-group inline">
               <li v-for="(amenity, amenityIndex) in hotel.amenities" :key="amenityIndex" class="amenity_item">{{ amenity.name }}</li>
              </ul>
            </div>
            <div class="hotel_prices">{{ hotel.price }} rub</div>
          </div>
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
            price: 4000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Helsinki Name", address: "Helsinki, some street, 3",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'},
                { name: 'bath'}, { name: 'breakfast'}, { name: 'spa'}
              ],
            price: 6000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Barselona Name", address: "Barselona, some street, 4",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'}, { name: 'transfer'},
                { name: 'breakfast'}, { name: 'spa'} 
              ],
            price: 7000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Berlin Name", address: "Berlin, some street, 5",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'}, { name: 'transfer'},
                { name: 'bath'}, { name: 'spa'}
              ],
            price: 8000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Lisbon Name", address: "Lisbon, some street, 6",
              amenities: [
                { name: 'wi-fi'}, { name: 'bar'}, { name: 'fitness'}, { name: 'pool'}, { name: 'transfer'},
                { name: 'bath'}, { name: 'breakfast'}
              ],
            price: 9000  
           },
           { photo: "/some_address/some_photo.png", name: "Hotel Praga Name", address: "Praga, some street, 6",
              amenities: [
                
              ],
            price: 1200  
           },{ photo: "/some_address/some_photo.png", name: "Hotel New York Name", address: "New York, some street, 6",
              amenities: [
                
              ],
            price: 1300  
           },{ photo: "/some_address/some_photo.png", name: "Hotel Toronto Name", address: "Toronto, some street, 6",
              amenities: [
                
              ],
            price: 1400  
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
        //filterValue: null,//initially there is no choosen amenities
        multiFiltersValue: [],
        filteredData: null,
        runningArray: null,
      }
    },
    methods: {
      reverseOrder: function() {
        // console.log("it works!");
        this.order = (this.order === 'desc') ? 'asc' : 'desc';
      },
      changeFilterValue: function(choosenAmenity) {
        // console.log(choosenAmenity);
        if (!this.filteredData) {
          this.filteredData = this.hotels.filter(function(hotel){
            // console.log("case 1:", this.filteredData);
            let newAmenities = hotel.amenities.filter(function(amenity){
              return amenity.name === choosenAmenity;
            })
            return newAmenities.length;
          })
        } else if (this.filteredData && !this.runningArray) {
          console.log("case 2:", this.filteredData);
           this.runningArray = this.filteredData.filter(function(hotel){
            let newAmenities = hotel.amenities.filter(function(amenity) {
              // console.log(typeof amenity.name, typeof choosenAmenity);
              return amenity.name === choosenAmenity;
            })
            return newAmenities.length;
          })
        } else {
          this.runningArray = this.runningArray.filter(function(hotel){
            let newAmenities = hotel.amenities.filter(function(amenity) {
              // console.log(typeof amenity.name, typeof choosenAmenity);
              return amenity.name === choosenAmenity;
            })
            return newAmenities.length;
          })
        }
        event.target.classList.toggle('amenityActive');
      }

    },
    mounted: function () {
      this.$nextTick(function () {
        
        // Code that will run only after the
        // entire view has been rendered
      })
    },
    computed: {
      orderedKidsList: function(){
        let order = this.order;
        return _.orderBy(this.kids, 'intelligence', [order]); //first argument is an array,
        //second argument is a parameter of sorting
        //third argument is a type of sorting, defined in methods (see below);
      },
      showHasAmenityOnly: function() {
        if (!this.filteredData && !this.runningArray) {
          console.log("number 1");
          return this.hotels;
        } else if (this.filteredData && !this.runningArray) {
          console.log("number 2");
          return this.filteredData;
        } else {
          console.log("number 3");
          return this.runningArray;
        }
      },
    }
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
    min-width: 525px;
    min-height: 400px;
    height: fit-content;
    height: -moz-max-content;
    margin: 35px 0;
  }
  .hotel_item {
    border: 1px dotted white;
    margin: 10px 0;
    border-radius: 3px;
    box-shadow: 0px 0px 15px 5px rgba(255, 255, 255, 0.5);
   /* display: flex;
    flex-direction: column;
    align-items: flex-start;*/
  }
  .inline {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    width: 100%;
    flex-wrap: wrap;
  }
  .separated_block {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 20px 0;
    padding: 10px 0;
    border: 1px solid white;
    border-radius: 3px;
    box-shadow: 0px 0px 15px 5px rgba(255, 255, 255, 0.5);
  }
  .amenityActive {
    background-color: rgba(255, 45, 45, 0.5);
    border: 1px solid white;
    color: white;
  }
</style>