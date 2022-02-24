<template>  
        <kinesis-container class="parallax-element">              
            <kinesis-element 
                :strength="10" 
            > 
                <div class="parallax-header">
                    <img alt="parallax-header" src="@/assets/img/pastel-paralax.png">
                </div>
            </kinesis-element>      
        </kinesis-container>
     
</template>

<script>
export default {
    name: 'Parallax'
}
</script>

<style scoped>  
    .parallax-element {
        position: absolute;
        top: -5.5px;
        left: 44px;
        z-index: 1;
        height: 100vh;
        width: 100%;
    }

    
</style>
