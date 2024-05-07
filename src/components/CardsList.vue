<script>
export default{
    props:{
        cardObj: Object,
    },
    computed: {
    status () {
        if (this.cardObj.status === "unknown") {
         return  "NO STATUS ";
      } else {
        return this.cardObj.status;
      }
    },
  },
};

</script>

<template>
    <div>
        <img :src="cardObj.image" alt="">
        <span class="obj-name">{{ cardObj.name }}</span>
        <span class="obj-status">{{ cardObj.status }}</span>
        <span class="obj-species">{{ cardObj.species }}</span>
    </div>
    </template>

<style lang="scss" scoped>
    div{    
        img{
            border-radius: 50%;
            width: 80%;
        }
        span{
        display: block;
        }
        .obj-name{
            margin-bottom: 10px;
        }
        .obj-status,
        .obj-species{
            font-size: 11px;
        }
        .obj-species{
            margin-bottom: 10px;
        }
    }
</style>