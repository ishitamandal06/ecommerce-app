<template>
    <div> Add Category </div>
    <div class="container">
        <div class = "row">
            <div class="col-12 text-center"> 
                <h3 class="pt-3"> Add Category </h3>
            </div>
        </div>
        <div class="row">
            <div class = "col-3"> </div>
             <div class = "col-6"> 
                <form>
                <div class="form-group">
                    <label>Name</label>
                    <input type="text" class="form-control" placeholder="Enter Category Name" v-model="name"> 
                </div>
                <div class="form-group">
                    <label>Description</label>
                    <input type="text" class="form-control" placeholder="Enter Category Description" v-model="description"> 
                </div>
                <div class="form-group">
                    <label> Image</label>
                    <input type="text" class="form-control" placeholder="Enter Category Image" v-model="imageUrl"> 
                </div>
                <button type="button" class="btn btn-secondary" @click="addCategory">Submit</button>

            </form>
             </div>
              <div class = "col-3"> </div>
            
        </div>
    </div>
</template>

<script>
    const axios = require('axios');
    const sweetalert = require('sweetalert');
export default ({

    data() {
        return {
            name: "",
            description: "",
            imageUrl: "",
        }
    },
    methods: {
        addCategory() {
            const newCategory = {
                name: this.name,
                description: this.description,
                imageUrl: this.imageUrl,
            }
            const baseUrl = 'https://master--harmonious-bunny-268927.netlify.app'; 
            axios({
                method: 'post',
                url: `${baseUrl}/admin/create`,
                data: JSON.stringify(newCategory),
                headers: {
                    'Content-Type': 'application/json'}
            }).then(()=>{
                console.log("Category added successfully")
                sweetalert({
                    text: "Category added successfully",
                    icon: "success",})
            }).catch(err=>{
                console.log(err);
            })


            
        }
        
    }
}
)
</script>
<style scoped>

</style>
