<template>
    <v-container>
        <v-card>
            <div class="indigo lighten-4 pa-6">
                <h1 class="">Dataset Name</h1>
                <p class="subtitle-1">Authors</p>
            </div>
            <v-tabs color="deep-purple accent-4" right>
                <v-tab>Overview</v-tab>
                <v-tab>Publications</v-tab>
                <v-tab>Implementation</v-tab>

                <v-tab-item class="mx-auto col-10">
                    <v-row>
                        <h3>Description:</h3>
                        <p>Halvah liquorice cotton candy tart jelly liquorice wafer. Pie cake chocolate cake jujubes.
                            Chocolate icing dragée marzipan. Chocolate cake pudding gingerbread. Pastry croissant
                            gingerbread cheesecake j</p>
                    </v-row>
                    <v-row>
                        <div class="col-6 px-0">
                            <h3><i class="mdi mdi-beaker-outline red--text text--lighten-3"></i> Scientific Domain:</h3>
                            <p>Bonbon pudding gummies marzipan bear claw pie</p>
                        </div>
                        <div class="col-6 px-0">
                            <h3><i class="mdi mdi-run red--text text--lighten-3"></i> Associated Tasks:</h3>
                            <p>Gummi bears candy marzipan cheesecake.</p>
                        </div>
                    </v-row>
                    <v-row>
                        <div class="col-6 px-0">
                            <h3><i class="mdi mdi-chart-bar red--text text--lighten-3"></i> Data Type:</h3>
                            <p>Pudding</p>
                        </div>
                        <div class="col-6 px-0">
                            <h3><i class="mdi mdi-file-document red--text text--lighten-3"></i> Data License:</h3>
                            <p>Gummi bears candy marzipan cheesecake.</p>
                        </div>
                    </v-row>
                    <v-row>
                        <div class="col-6 px-0">
                            <h3><i class="mdi mdi-weight-kilogram red--text text--lighten-3"></i> Size:</h3>
                            <p>Measurement, n-items</p>
                        </div>
                        <div class="col-6 px-0">

                        </div>
                    </v-row>
                    <v-row>
                        <h3>Versions</h3>

                        <v-simple-table dense height="300px" class="col-12">
                            <template v-slot:default>
                                <thead>
                                    <tr>
                                        <th class="text-left">
                                            Name
                                        </th>
                                        <th class="text-left">
                                            Description
                                        </th>
                                        <th class="text-left">
                                            Date
                                        </th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td>my_data_v2.0</td>
                                        <td>More features</td>
                                        <td>8/11/2022</td>
                                    </tr>
                                    <tr>
                                        <td>my_data_v1.0</td>
                                        <td>Added all the data from 7/10/2022</td>
                                        <td>8/10/2022</td>
                                    </tr>

                                </tbody>
                            </template>
                        </v-simple-table>

                    </v-row>

                </v-tab-item>
                <v-tab-item class="mx-auto col-10">
                    <h2>Publications</h2>

                </v-tab-item>
                <v-tab-item class="mx-auto col-10">
                    <h2>Using this dataset</h2>
                    <p>You can load this dataset with 2 lines of code if you already have Foundry set up. If you need to
                        set up Foundry, check out our <a href="" target="blank">example notebooks</a> and <a href=""
                            target="blank">documentation</a> for how to get started.</p>

                    <vue-code-highlight language="python">
                        <pre class="language-python">
# Make sure you've imported and instantiated Foundry
import Foundry from foundry-ml
f = Foundry()

# Load the data here!
f.load(dataset_doi)
res = f.load_data()
                     
 </pre>
                    </vue-code-highlight>
                    <h2 class="mt-6 mb-4">Metadata associated with this dataset</h2>
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
                                        Filter
                                    </th>
                                    <th class="text-left">
                                        Units
                                    </th>
                                    <th class="text-left">
                                        Description
                                    </th>
                                    <th class="text-left">
                                        Classes
                                    </th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>img</td>
                                    <td>input</td>
                                    <td>-</td>
                                    <td>-</td>
                                    <td>-</td>
                                    <td>-</td>
                                </tr>
                                <tr>
                                    <td>coords</td>
                                    <td>input</td>
                                    <td>-</td>
                                    <td>-</td>
                                    <td>-</td>
                                    <td>-</td>
                                </tr>

                            </tbody>
                        </template>
                    </v-simple-table>
                    <h3>Splits</h3>

                </v-tab-item>
            </v-tabs>
        </v-card>

    </v-container>
</template>

<script>
import { component as VueCodeHighlight } from 'vue-code-highlight';
import "vue-code-highlight/themes/prism-tomorrow.css";
import "vue-code-highlight/themes/window.css";
import 'prism-es6/components/prism-markup-templating';
import 'prism-es6/components/prism-python';


export default {
    name: 'Dataset-info',
    components: {
        VueCodeHighlight
    }
}
</script>

