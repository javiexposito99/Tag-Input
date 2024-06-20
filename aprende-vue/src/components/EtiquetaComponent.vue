<template>
    <div id="etiqueta-component">
        <h1>{{ titulo }}</h1>
        <div class="inputTag">   
            <div class="tags">
                <div class="tag" v-for="(tag, index) in tags" :key="index">
                    {{ tags }} <button @click="deleteTag(tag)">X</button>
                </div>
            </div>
            <form @submit.prevent="handleSubmit">
                <input class="input" type="text" v-model="currentValue" @keydown="handleKeyDown"/>
            </form>
        </div>    
    </div>
</template>

<script>
export default {
    emits: ["onTagsChange"],
    name: 'EtiquetaComponent',
    data() {
        return {
            titulo: 'Primera prueba en Vue',
            currentValue: '',
            tags: [],
        }
    },
    methods:{
        handleKeyDown(e){
            if(e.key == 'Backspace' && this.currentValue == ''){
                this.tags.pop();
                //this.onTagsChange(this.tags);
                this.$emit('onTagsChange', this.tags);
            }
        },
        handleSubmit(){
            if(this.currentValue != ""){
                const exist = this.tags.some(item => item == this.currentValue);
                if(!exist){
                    this.tags.push(this.currentValue);
                    this.currentValue = "";
                    //this.onTagsChange(this.tags);
                    this.$emit('onTagsChange', this.tags);
                }
                
            }
        },  
        deleteTag(tag){
            this.tags = this.tags.filter((item) => item != tag);
            //this.onTagsChange(this.tags);
            this.$emit('onTagsChange', this.tags);

        },
        
    }
    
    
}
</script>

<style scoped>


.inputTag {
    list-style-type: none;
    display: inline-flex;
    border: solid 2px #000;
    border-radius: 3px;
    height: 43px;
}


#etiqueta-component .tags{
    list-style-type: none;
    display: flex;
    gap: 3px;
    padding: 5px;

}

.tags .tag{
    display: flex;
    padding: 5px;
    border: solid 1px #ccc;
    gap: 5px;
    align-content: center;
    border-radius: 3px;
}

.inputTag form{
    display: inline-flex;
}

.inputTag .input{
    border: none;
    outline: none;
    padding: 0 5px;
}

.inputTag button{
    background-color: transparent;
    border: none;
    border-radius: 3px
    /*cursor: pointer;*/ 
}

.inputTag button:hover{
    background-color: #eee;
}

</style>