<template>
    <div class="datasets">
        <v-container>
            <v-row>
                <h1 class="mx-6 mt-6">Datasets</h1>
            </v-row>
            <v-row>
                <!-- <v-col class="col-md-3 col-12">
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
                    </v-card>
                </v-col> -->
                <v-col>
                    <v-row>

                        <v-card elevation="3"  outlined class="mx-auto col-md-5 col-12 my-6"
                            v-for="item in items" :key="item.title" :to="item.to" link>
                            <v-card-title style="word-break: keep-all;">{{ item.title }}</v-card-title>
                            <v-card-text>
                                <v-chip class="ma-2" color="blue lighten-1" text-color="white">
                                    {{ item.foundry.data_type }}
                                </v-chip>
                                <v-chip class="ma-2" color="indigo lighten-3" text-color="white">
                                    {{ item.foundry.n_items }}
                                </v-chip>
                                <v-chip class="ma-2" color="red lighten-2" text-color="white">
                                    {{ item.foundry.task_type[0] }}
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
    mounted() {
        var self = this;

        // Define the search endpoint and index
        var ep = 'https://search.api.globus.org/v1/index/1a57bbe5-5272-477f-9d31-343b8258b7a5/search'

        // Format the POST query for Globus search
        // Facet
        var query = {
            "q": "(mdf.organizations:Foundry) AND (mdf.resource_type:dataset)",
            "limit": 100,
            "advanced": true,
            "facets": [
                {
                    "name": "tags",
                    "field_name": "dc.subjects.subject",
                    "type": "terms", //"date_histogram",
                    "size": 20
                }
            ]
        }

        // Perform the POST request, and load the information into the Vue object
        axios
            .post(ep, query)
            .then(function (res) {
                console.log("AXIOS POST")
                console.log(res)
                for (let i = 0; i < res.data.gmeta.length; i++) {
                    // TODO, add more data into the view object for display
                    self.items.push({
                        title: res.data.gmeta[i].entries[0].content.dc.titles[0].title,
                        foundry: res.data.gmeta[i].entries[0].content.projects.foundry,
                        to: "/datasets/" + res.data.gmeta[i].entries[0].content.mdf.source_id
                    })
                }

                // Loop through the facet results from Globus Search, and put them 
                // into the facets object
                for (let j = 0; j < res.data.facet_results[0].buckets.length; j++) {
                    self.facets.tags.push({
                        "title": res.data.facet_results[0].buckets[j].value,
                        "count": res.data.facet_results[0].buckets[j].count
                    })
                }

                // Push facet results into the searchTerms for display purposes
                self.searchTerms.push({
                    "icon": 'mdi-beaker-outline',
                    "subterms": self.facets.tags,
                    "title": 'Tag',
                })


            })
    },
    data: () => ({
        drawer: null,
        items: [],
        facets: { "tags": [] },
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
