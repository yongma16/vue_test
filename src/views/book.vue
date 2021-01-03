<template>
    <div>
        {{msg}}
        <table>
            <tr>
                <td>编号</td>
                <td>书名</td>
                <td>作者</td>
            </tr>
            <tr v-for="item in books">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.auth}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        name: "book.vue",
        data(){
            return {
                msg:"book!",
                books:[
                    {
                        id:1,
                        name:'狂人日记',
                        auth:'鲁迅'
                    },
                    {
                        id:2,
                        name:'呐喊',
                        auth:'鲁迅'
                    }

                ]
            }
        },
        created(){
            const _temp=this;
            axios.get('http://localhost:8181/book//findalltest').then(function(resp)
            {
                console.log(resp.data)
                _temp.books=resp.data;
            })

        }
    }
</script>

<style scoped>

</style>