<template>
    <div class="w-full">
        <div class="flex justify-between items-center border border-stone-200 w-9/12 px-5 py-2 mt-5 mx-auto">
            <p>People Information</p>
            <button @click="showModal()" class="border border-green-600 hover:bg-green-500 rounded-md px-5 py-2">Add New</button>
        </div>
        <div class="mb-5" v-if="isModalVisible">
            <AddNewPerson @addNew="getData" @close="closeModal()" />
        </div>
        <div class="w-9/12 mx-auto">
            <table class="table-fixed border-collapse border border-slate-400 w-full">
                <thead>
                    <tr>
                        <td class="text-center  py-2 border border-slate-300 bg-sky-100">S. No.</td>
                        <td class="text-center  py-2 border border-slate-300 bg-sky-100">Name</td>
                        <td class="text-center  py-2 border border-slate-300 bg-sky-100">Mobiel</td>
                        <td class="text-center  py-2 border border-slate-300 bg-sky-100">Remove</td>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(information, i) in informations" :key="information.id">  <!-- we can also use this command {:key="information"} -->
                        <td class="text-center  py-2 border border-slate-300">{{ i+1 }}</td>
                        <td class="text-center  py-2 border border-slate-300">{{ information.name }}</td>
                        <td class="text-center  py-2 border border-slate-300">{{ information.mobile }}</td>
                        <td @click="removeInfo(i)" class="text-center  py-2 border border-slate-300"><button class="border border-red-600 px-3 hover:bg-red-500 rounded-sm">Remove</button></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import AddNewPerson from './AddNewPerson.vue';
    export default {
        name: 'Information',
        // props: {
        //     informations: {
        //         type: Array,
        //     },
        // },
        emits: ['info'],
        components: {
            AddNewPerson,
        },
        data() {
            return {
                isModalVisible: false,
                informations: [],
            }
        },
        mounted () {
            this.informations = JSON.parse(localStorage.getItem('informations')) ? JSON.parse(localStorage.getItem('informations')) : []
        },
        methods: {
            showModal() {
                this.isModalVisible = true;
            },
            closeModal(){
                this.isModalVisible = false;
            },
            removeInfo(index){
                this.informations.splice(index, 1)
            },
            getData(value){
                console.log(value)
                this.informations.push(value);
                localStorage.setItem('informations', JSON.stringify(this.informations))
                // console.log(value);
            },
            // storeInfo(){
            //     if(this.info.length){
            //         // push the new takeInformation to list
            //         this.informations.push(this.info)
            //         // store the data in localStorage
            //         localStorage.setItem("informations", JSON.stringify(this.informations));
            //         console.log(localStorage)
            //     }
            // },
            // getInfo(){
            //     this.informations = JSON.parse(localStorage.getItem("informations"));
            //     console.log(this.informations``)
            // },
        },
    }
</script>

<style lang="scss" scoped>

</style>