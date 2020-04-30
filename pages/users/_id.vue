<template>
    <div>
        <v-app id="inspire">
            <v-card
            class="mx-auto"
            max-width="450"
            >
                <v-card-text>
                <p class="display-1 text--primary">UserID {{userId}}</p>
                <div class="text--primary">
                    <v-icon>mdi-account</v-icon>{{user.name}}<br>
                    <v-icon>mdi-alpha</v-icon>{{user.email}}
                </div>
                </v-card-text>
            </v-card>
        </v-app>
    </div>
</template>
 
<script>
export default {
    data(){
        return{
            userId: this.$route.params.id
        }
    },
    async asyncData ({route,app}) {
        const user = await app.$axios.$get(`https://jsonplaceholder.typicode.com/users/${route.params.id}`)
        return{
            user
        }
    }
}
</script>