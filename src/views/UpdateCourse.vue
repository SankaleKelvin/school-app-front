<template>
    <div class="container">
        <div>
           <form @submit.prevent="updateCourse(id)" method="post">
                <card>
                    <card-body>
                        <input type="text" v-model="id" class="form-control" id="id" placeholder="course id">
                        <div class="mb-3">
                            <label for="name" class="form-label">Course Name</label>
                            <input type="text" v-model="name" class="form-control" id="name" placeholder="course name">
                        </div>
                        <div class="mb-3">
                            <label for="amount" class="form-label">Course Amount</label>
                            <input type="text" v-model="amount" class="form-control" id="amount" placeholder="course amount">
                        </div>
                    </card-body>
                    <button type="submit" class="btn btn-primary">save</button>
                    &nbsp;&nbsp;&nbsp;
                    <button type="reset" class="btn btn-warning">Cancel</button>
                </card>
           </form>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import router from '../router';

export default{
    name: 'UpdateCourse',
    data(){
        return{
            id: '1',//this.$route.params.id,
            name: '',
            amount: ''
        };
    },
    methods: {
        async updateCourse(id){
            await axios.post('http://127.0.0.1:8000/api/updateCourse',{
                'name':this.name,
                'amount':this.amount
            });
            router.push('/courses');
        },

        async getCourse(id){
            try{
                const response = await axios.get(`http://127.0.0.1:8000/api/getCourse/${id}`);
                this.name = response.data.name;
                this.amount = response.data.amount;
            } catch(error){
                console.log("Error Fetching the Course with id: ", id);
            }
        }
    }

}
</script>