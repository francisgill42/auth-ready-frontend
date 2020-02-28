<template>
<div>
<v-row>
  <v-col>
      <v-card dark>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">Users</div>
        <v-list-item-title class="headline mb-1">Total </v-list-item-title>
        <v-list-item-subtitle>
          </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="50"
        color="white"
        >
       <span class="black--text">05</span>
        </v-list-item-avatar>
    </v-list-item>


    
  </v-card>
  </v-col>
  <v-col>
      <v-card dark>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">Users</div>
        <v-list-item-title class="headline mb-1">Total </v-list-item-title>
        <v-list-item-subtitle>
          </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="50"
        color="white"
        >
       <span class="black--text">05</span>
        </v-list-item-avatar>
    </v-list-item>


    
  </v-card>
  </v-col>

    <v-col>
      <v-card dark>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">Users</div>
        <v-list-item-title class="headline mb-1">Total </v-list-item-title>
        <v-list-item-subtitle>
          </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="50"
        color="white"
        >
       <span class="black--text">{{user_count}}</span>
        </v-list-item-avatar>
    </v-list-item>


    
  </v-card>
  </v-col>

    <v-col>
      <v-card dark>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">Roles</div>
        <v-list-item-title class="headline mb-1">Total </v-list-item-title>
        <v-list-item-subtitle>
          </v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="50"
        color="white"
        >
       <span class="black--text">{{role_count}}</span>
        </v-list-item-avatar>
    </v-list-item>


    
  </v-card>
  </v-col>
</v-row>


  </div>
</template>

<script>
import test from '../components/Test';
export default{
  component : {
    test
  },
  data(){
    return {
      user_count:'',
      role_count:'',
    }
  },
created () {
      this.initialize()
    },




   methods: {

      async initialize () {

          const roles = await this.$axios.get('role');
         
          const users = await this.$axios.get('user');
          this.user_count = users.data.length;
          this.role_count = roles.data.length;

      },
   }
   }
</script>