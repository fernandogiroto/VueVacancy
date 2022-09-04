 <template>
    <div :class="alertStyle" role="alert">
      <slot name="title"></slot>   
      <slot name="description"></slot> 
    </div>
 </template>
 <script>
    export default{
     name: 'Alert',
     props: { type: String},
     computed:{
         alertStyle(){
             switch(this.type){
                 case 'success': return 'alert alert-success'
                 case 'error' : return 'alert alert-danger'
                 default: return 'alert-success'
             }
         }
     }
    }

 </script>
 