<template>
    <div class="parallax-element">   
        <kinesis-container>              
            <kinesis-element 
                :strength="10" 
                type="depth"
                axis="x"
            > 
                <div class="parallax-header">
                    <img alt="parallax-header" src="@/assets/img/pastel-paralax.png">
                </div>
            </kinesis-element>      
        </kinesis-container>
    </div>   
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
    }

    
</style>
