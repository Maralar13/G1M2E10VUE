<template>
    Documento
</template>


<script>
export default {
  name: 'Documento',
  props: {
    msg: String
  }
}
</script>

<style>
    #documento{
        width: 100%;
        height: 100%;

        display: flex;
        flex-direction: column;
        justify-content: center;    
        align-items: center;
    }

    #documento h2{
        font-size: 50px;
        color: #283747;
    }

    #documento span{
        color: crimson;
        font-weight: bold;
    }
</style>