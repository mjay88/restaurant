<template>
  <div class="checkout">
    <!--maybe we can use a mixin or slot or something with global properties for the cart?-->
    <h1>This is checkout page</h1>
  </div>
</template>
<script>
export default{
    data(){
        return{
          title: "Checkout"
        }
    },
    //head method for seo
    head() {
      return {
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: 'Checkout',
            name: 'Checkout Page',
            content: 'Checkout content'
          }
        ]
      }
    }
}
</script>

