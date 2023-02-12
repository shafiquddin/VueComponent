<template>
  <li>
    <h2>{{ name }} {{ favrite ? '(favrite)': '' }}</h2>
    <button @click="isFavToggle">Toggle favrite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  props:{
    name:{
      type:String,
      required:true,
    },
    emailAddress:{
      type:String,
      required:true,
    },
    phoneNumber:{
      type:String,
      required:true,
    },
    isFavarite:{
      type:Boolean,
      required:false,
      default:false,
    }

  }
  ,
  data() {
    return {
      detailsAreVisible: false,
      favrite:this.isFavarite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    isFavToggle(){
      this.favrite=!this.favrite;
    }
  }
};
</script>