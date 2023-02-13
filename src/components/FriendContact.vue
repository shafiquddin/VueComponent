<template>
  <li>
    <h2>{{ name }} {{ isFavarite ? '(favrite)': '' }}</h2>
    <button @click="isFavToggle">Toggle favrite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'show' }} Details</button>
    <button @click="$emit('delete-friend',id)">Delete</button>
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
    id:{
      type:String,
      required:true,
    },
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
      // validator:function(value){
      //   return  value==='0' | value==='1';
      // }
    }

  },
  emit:['favrite-toggle','delete-friend'],
  // emit:{
  //   'favrite-toggle':function (id){
  //     if(id){
  //       return true;
  //     }else{
  //       console.warn('Id missing!');
  //       return false;
  //     }
  //   }
  // },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    isFavToggle(){
      this.$emit('favrite-toggle',this.id);
    }
  }
};
</script>