<template>
    <div class="add-user-form">
        <v-row no-gutters>
            <v-col>
                <v-text-field class="username"></v-text-field>
            </v-col>
            <v-col>
                <div class="bindings">
                    <v-radio-group class="binding-radio" v-model="radios" row>
                        <v-radio value="clusterWide" label="clusterWide"></v-radio>
                        <v-radio value="nameSpaced" label="namespaced"></v-radio>
                        <v-radio value="dynamicNamespaces" label="Dynamic Namespaces and Labels"></v-radio>
                    </v-radio-group>
                    <div class="binding-form">
                        <div class="cluster-wide-form" v-show="radios === 'clusterWide'">
                            <v-text-field v-model="clusterWideName">
                            </v-text-field>
                        </div>
                        <div class="name-spaced-form" v-show="radios === 'nameSpaced'"></div>
                        <div class="name-spaced-form" v-show="radios === 'dynamicNamespaces'">
                            <div class="cluster-role-form" v-for="cluster in clusterRoles">
                                <p> clusterRole {{clusterRoles.indexOf(cluster) + 1}}</p>
                                <v-text-field v-model="cluster.name"></v-text-field>
                                <v-btn v-if="clusterRoles.indexOf(cluster) !== 0" @click="deleteCluster(cluster)">
                                    Delete
                                </v-btn>
                            </div>
                            <v-btn @click="addCluster">Add Cluster</v-btn>
                        </div>
                    </div>
                </div>
            </v-col>
            <v-col>
            </v-col>
        </v-row>
    </div>
</template>

<script>
    export default {
        name: "UserForm",

        data: () => ({
            name: null,
            radios: null,
            clusterWideName: null,
            clusterRoles: [
                {
                    name: null,
                }
            ]
        }),

        methods: {
            addCluster() {
                this.clusterRoles.push(
                    {
                        name: null
                    }
                )
            },

            deleteCluster(cluster) {
                this.clusterRoles.splice(this.clusterRoles.indexOf(cluster), 1)
            }
        }
    }
</script>

<style scoped lang="scss">
    .add-user-form {
        display: flex;
        margin: 20px;
        justify-content: space-between;

        .col {
            padding: 20px;
        }

        .bindings {
            display: flex;
            flex-direction: column;

            .cluster-role-form {
                display: flex;
            }
        }
    }
</style>
