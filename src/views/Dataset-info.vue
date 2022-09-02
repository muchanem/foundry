<template>
    <v-container>
        <v-card>
            <div class="indigo lighten-2 pa-6">
                <h1 class="white--text font-weight-medium">{{ dataset.title }}</h1>
                <p class="subtitle-1 white--text font-weight-medium">
                    <span v-for="(author, index) in dataset.authors" :key="author">
                        {{ author }}<span v-if="index != dataset.authors.length - 1">; </span>
                    </span>
                </p>
            </div>

            <div class="mx-auto col-md-10 col-11 mb-10">
                <h2 class="mt-3">Overview</h2>
                <div class="pl-md-5">
                    <div>
                        <v-chip color="red lighten-2" outlined class="mx-1 my-1" v-for="subject in dataset.dc.subjects"
                            :key="subject.subject">
                            {{ subject.subject }}
                        </v-chip>
                    </div>

                    <v-row class="mt-0">
                        <div class="col-6">
                            <h3><i class="mdi mdi-beaker-outline red--text text--lighten-3"></i> Scientific Domain</h3>
                            <p>{{ dataset.foundry.domain[0] }} </p>
                        </div>
                        <div class="col-6">
                            <h3><i class="mdi mdi-run red--text text--lighten-3"></i> Associated Tasks</h3>
                            <v-chip color="indigo lighten-2" outlined class="mx-1"
                                v-for="task in dataset.foundry.task_type" :key="task">
                                {{ task }}
                            </v-chip>
                        </div>
                    </v-row>
                    <v-row class="mt-0">
                        <div class="col-6">
                            <h3><i class="mdi mdi-chart-bar red--text text--lighten-3"></i> Data Type</h3>
                            <p>{{ dataset.foundry.data_type }}</p>
                        </div>
                        <div class="col-6">
                            <h3><i class="mdi mdi-calendar-star-outline red--text text--lighten-3"></i> Date Published
                            </h3>
                            <p>{{ dataset.dc.dates[0].date }} </p>
                        </div>
                    </v-row>
                    <v-row class="mt-0">
                        <div class="col-6">
                            <h3><i class="mdi mdi-weight-kilogram red--text text--lighten-3"></i> Size</h3>
                            <p>{{ dataset.foundry.n_items }} items</p>
                        </div>
                        <div class="col-6">
                            <h3><i class="mdi mdi-identifier red--text text--lighten-3"></i> DOI</h3>
                            <p>{{ dataset.dc.identifier.identifier }}</p>
                        </div>
                    </v-row>
                </div>
                <h2 class="mt-6">Using this dataset</h2>
                <div class="pl-md-5">
                    <vue-code-highlight language="python">
                        <pre class="language-python">
# Make sure you've imported and instantiated Foundry
import Foundry from foundry-ml
f = Foundry()

# Load the data here!
f.load('{{ dataset.dc.identifier.identifier }}')
res = f.load_data()
                     
 </pre>
                    </vue-code-highlight>
                    <p>You can load this dataset with 2 lines of code if you already have Foundry set up. If you need to
                        set up Foundry, check out our <a class="red--text text--lighten-3"
                            href="https://github.com/MLMI2-CSSI/foundry/tree/main/examples" target="blank">example
                            notebooks</a> and <a class="red--text text--lighten-3"
                            href="https://ai-materials-and-chemistry.gitbook.io/foundry/v/docs/"
                            target="blank">documentation</a> for how to get started.</p>
                </div>

                <h2 class="mt-6 mb-2">Metadata associated with this dataset</h2>
                <div class="pl-md-5">
                    <h3>Keys</h3>
                    <v-simple-table dense class="col-12">
                        <template v-slot:default>
                            <thead>
                                <tr>
                                    <th class="text-left">
                                        Key
                                    </th>
                                    <th class="text-left">
                                        Type
                                    </th>
                                    <th class="text-left">
                                        Units
                                    </th>
                                    <th class="text-left">
                                        Description
                                    </th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="item in dataset.foundry.keys" :key="item.key[0]">
                                    <td>{{ item.key[0] }}</td>
                                    <td>{{ item.type }}</td>
                                    <td>{{ item.units }}</td>
                                    <td>{{ item.description }}</td>
                                </tr>
                            </tbody>
                        </template>
                    </v-simple-table>
                    <h3>Splits</h3>
                    <v-simple-table dense class="col-12 mb-10">
                        <template v-slot:default>
                            <thead>
                                <tr>
                                    <th class="text-left">
                                        Label
                                    </th>
                                    <th class="text-left">
                                        Path
                                    </th>
                                    <th class="text-left">
                                        Type
                                    </th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="item in dataset.foundry.splits" :key="item.label">
                                    <td>{{ item.label }}</td>
                                    <td>{{ item.path }}</td>
                                    <td>{{ item.type }}</td>
                                </tr>
                            </tbody>
                        </template>
                    </v-simple-table>
                </div>
                <h2>Publications</h2>
                <div class="pl-md-5 mb-10">
                    <v-card elevation="3" outlined class="mx-auto col-md-5 col-12 my-6"
                        v-for="item in dataset.dc.titles" :key="item.title">
                        <v-card-title style="word-break: keep-all;">{{ item.title }}</v-card-title>
                    </v-card>
                </div>
            </div>
        </v-card>
    </v-container>
</template>

<script>
import { component as VueCodeHighlight } from 'vue-code-highlight';
import "vue-code-highlight/themes/prism-tomorrow.css";
import "vue-code-highlight/themes/window.css";
import 'prism-es6/components/prism-markup-templating';
import 'prism-es6/components/prism-python';
import { useRoute } from 'vue-router'


import axios from 'axios';

export default {
    components: {
        VueCodeHighlight
    },
    mounted() {
        var self = this;


        console.log(this.$route)

        // Define the search endpoint and index
        var ep = 'https://search.api.globus.org/v1/index/1a57bbe5-5272-477f-9d31-343b8258b7a5/search'

        // Format the POST query for Globus search - search via mdf.source_id
        var query = {
            "q": "(mdf.source_id:" + this.$route.params.id + ") AND (mdf.resource_type:dataset)",
            "limit": 1,
            "advanced": true,
        }

        // Perform the POST request, and load the information into the Vue object
        axios
            .post(ep, query)
            .then(function (res) {
                console.log(res)

                var creators = res.data.gmeta[0].entries[0].content.dc.creators
                var authors = []

                for (let i = 0; i < creators.length; i++) {
                    authors.push(creators[i].creatorName)
                }

                // TODO, add more data into the view object for display
                self.dataset = {
                    title: res.data.gmeta[0].entries[0].content.dc.titles[0].title,
                    authors: authors,
                    dc: res.data.gmeta[0].entries[0].content.dc,
                    foundry: res.data.gmeta[0].entries[0].content.projects.foundry,
                    to: "/datasets/" + res.data.gmeta[0].entries[0].content.mdf.source_id
                }
                console.log(self.dataset)
            })
    },
    data: () => ({
        drawer: null,
        dataset: {},
        facets: { "tags": [] },
    }),
}




// export default {
//     name: 'Dataset-info',
//     components: {
//         VueCodeHighlight
//     }
// }
</script>

