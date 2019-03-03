<template>
<div>
 <h1>Services</h1>
        <ul class="services">
            <li  v-for="i in services" v-on:click="toggleActive(i)" v-bind:class="{ 'active' : i.active }">
              {{i.name}} <span>{{i.price | currency}}</span>
            </li>
          </ul>
            
        <div class="total">
          Total: <span>{{total() | currency}}</span>
        </div>
  </div>
</template>
<script>
export default {
     data:()=> ({
      services: [
        {
          name: 'Web Development',
          price: 300,
          active: false
        },
        {
          name: 'Design',
          price: 400,
          active: false
        },
        {
          name: 'Integration',
          price: 250,
          active: false
        },
        {
          name: 'Training',
          price: 220,
          active: false
        }
      ]
    }),
    
    methods: {
      toggleActive: function(s) {
        s.active = !s.active;
      },
      total() {
        let total = 0;
        
        this.services.forEach(function(s) {
          if (!s.active) {return;}
          else{
          total +=s.price;
          }
        });
        
        return total;
      }
    },

}
</script>

