<template>
    <div>
        <div class="flex justify-between items-center border border-stone-200 border-b-0 w-4/12 px-5 py-2 mt-5 mx-auto">
            <p>Add New Person</p>
            <button @click="$emit('close')" class="border border-red-600 hover:bg-red-500 rounded-md px-5 py-2">Close</button>
        </div>
        <div class="border border-stone-200 w-4/12 px-5 py-5 mx-auto ps-16 space-y-2">
            <p>Name: <input v-model="info.name" class="border rounded-lg contrast-more:border-slate-400 focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500 ms-1" type="text"></p>
            <p>Mobile: <input v-model="info.mobile" class="border rounded-lg contrast-more:border-slate-400 focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500 ms-1" type="text"></p>
            <button @click="save()" class="border border-sky-600 hover:bg-sky-500 rounded-md px-6 py-1">Save</button>
        </div>
        <div>

        </div>
    </div>
</template>

<script>
    export default {
        name: 'AddNewPerson',
        props: {
            informations: {
                type: Array,
            },
        },
        emits: ['close', 'addNew'], // here we call "addNew" emit for avoid warning and this emit comes from 'method' in this component. that is bellow in the script. 
        components: {
        },
        data() {
            return {
                info: {
                    name: '',
                    mobile: '',
                }
            }
        },
        methods: {
            save(){
                // console.log(this.info)
                this.$emit('addNew', this.info)
                this.$emit('close')
            }
            
        },
    }
</script>

<style lang="scss" scoped>

</style>