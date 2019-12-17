<template>
    <v-form class="form">
        <v-text-field label="name" v-model="name"> </v-text-field>
        <div class="user-form" v-show="name != null">
            <v-row no-gutters>
                <v-col>
                    <h2>User</h2>
                </v-col>
                <v-col>
                    <h2>Binding</h2>
                </v-col>
                <v-col>
                    <h2>Cluster</h2>
                </v-col>
            </v-row>
            <UserForm></UserForm>

        </div>

        <v-btn>Update</v-btn>
    </v-form>
</template>

<script>
    import UserForm from "../components/UserForm";
    export default {
        name: "Main",
        components: {UserForm},
        data: () => ({
            name: null,

        }),
    }
</script>

<style lang="scss" scoped>
    .form {
        display: flex;
        justify-content: center;
        flex-direction: column;
        margin: 20px;

        .v-text-field {
            width: 20%;
        }

        .header {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            margin: 20px;
        }

        .v-btn {
            width: 10%;
        }
    }
</style>
