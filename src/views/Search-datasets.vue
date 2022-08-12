<template>
    <div class="search-datasets">
        <v-container>
            <v-row>
                <h1 class="mx-6 mt-6">Dataset Search</h1>
            </v-row>
            <v-row>
                <v-col class="col-md-3 col-12">
                    <v-card class="mx-auto">
                        <v-toolbar color="red lighten-3" dark>
                            <v-toolbar-title>Topics</v-toolbar-title>
                            <v-spacer></v-spacer>
                        </v-toolbar>
                        <v-list>
                            <v-list-group v-for="term in searchTerms" :key="term.title" v-model="term.active"
                                :prepend-icon="term.icon" no-action>
                                <template v-slot:activator>
                                    <v-list-item-content>
                                        <v-list-item-title v-text="term.title"></v-list-item-title>
                                    </v-list-item-content>
                                </template>

                                <v-list-item v-for="child in term.subterms" :key="child.title">
                                    <v-list-item-action>
                                        <v-checkbox color="indigo lighten-3"></v-checkbox>
                                    </v-list-item-action>
                                    <v-list-item-content>
                                        <v-list-item-title v-text="child.title"></v-list-item-title>
                                    </v-list-item-content>
                                </v-list-item>
                            </v-list-group>
                        </v-list>
                        <!-- <div class="col-12">
                            <v-btn color="indigo lighten-3" elevation="2" dark class="col-12">
                                search</v-btn>
                        </div> -->
                    </v-card>
                </v-col>
                <v-col>
                    <v-row>
                        <v-card elevation="3" height="200px" outlined class="mx-auto col-md-5 col-12 my-6"
                            v-for="item in items" :key="item.title" :to="item.to" link>
                            <v-card-title>{{ item.title }}</v-card-title>
                            <v-card-text>
                                <v-chip 
                                    class="ma-2"
                                    color="primary"
                                >
                                    {{item.foundry.data_type}}
                                </v-chip>
                                <v-chip 
                                    class="ma-2"
                                    color="secondary"
                                >
                                    {{item.foundry.n_items}}
                                </v-chip>
                                <v-chip
                                    class="ma-2"
                                    color="green"
                                    text-color="white"
                                    >
                                    {{item.foundry.task_type}}
                                </v-chip>

                            </v-card-text>
                        </v-card>
                    </v-row>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>


<!-- This is where the dataset data will be loaded and put into the cards -->
<script>
import axios from 'axios';

export default {
    mounted () {
    var self = this;

    // Define the search endpoint and index
    var ep = 'https://search.api.globus.org/v1/index/1a57bbe5-5272-477f-9d31-343b8258b7a5/search'

    // Format the POST query for Globus search
    var query = {
        "q": "(mdf.organizations:Foundry) AND (mdf.resource_type:dataset)",
        "limit": 10,
        "advanced":true
    }
    
    // Perform the POST request, and load the information into the Vue object
    axios
      .post(ep, query)
      .then(function (res) { 
        console.log(res)
        for (let i = 0; i < res.data.gmeta.length; i++) { 
            // TODO, add more data into the view object for display
            self.items.push({
                                title : res.data.gmeta[i].entries[0].content.dc.titles[0].title,
                                foundry : res.data.gmeta[i].entries[0].content.projects.foundry,
                                to:"/search-datasets/dataset"})
        }
        console.log(self.items) 
        } )
    },
    data: () => ({
        drawer: null,
        items: [],
        searchTerms: [
            {
                icon: 'mdi-beaker-outline',
                subterms: [{ title: 'this one' }, { title: 'that one' }],
                title: 'Domain',
            },
            {
                icon: 'mdi-run',
                subterms: [
                    { title: 'Classification' },
                    { title: 'Generation' },
                    { title: 'Sushi' },
                ],
                title: 'Task',
            },
            {
                icon: 'mdi-chart-bar',
                subterms: [{ title: 'List Item' }],
                title: 'Data Type',
            },
            {
                icon: 'mdi-file-document',
                subterms: [{ title: 'List Item' }],
                title: 'Data License',
            },
            {
                icon: 'mdi-weight-kilogram',
                subterms: [{ title: 'List Item' }],
                title: 'Size',
            },
            {
                icon: 'mdi-emoticon-neutral',
                subterms: [{ title: 'List Item' }],
                title: 'Mood',
            },
            {
                icon: 'mdi-emoticon-cool',
                subterms: [{ title: 'List Item' }],
                title: 'Vibe',
            },
        ],
    }),
}
</script>
