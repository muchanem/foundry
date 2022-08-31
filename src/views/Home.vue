<template>
  <div class="home col-12 mb-5">
    <!-- heading content -->
    <div class="jumbotron text-center py-5 col-12 bg-light">
      <h1 class="text-h1 col-10 mx-auto">
        An open source machine learning platform for scientists
      </h1>
      <p class="text-subtitle-1 mt-3 col-7 mx-auto">
        Access datasets and ML models while setting industry benchmarks
      </p>
    </div>

    <!-- middle content -->
    <v-row class="col-md-8 mx-auto col-12">
      <v-card elevation="3" outlined class="mx-auto col-md-5 col-6 my-6 text-center">
        <a href="https://ai-materials-and-chemistry.gitbook.io/foundry/publishing/publishing-datasets" target="blank">
          <h1 class="display-2"><i class="mdi mdi-chart-bar-stacked red--text text--lighten-3"></i></h1>
        </a>
        <v-card-title class="justify-center">Add your dataset</v-card-title>
        <v-card-text>
          We host data from a variety of scientific domains and make it easy to share and use.
        </v-card-text>
      </v-card>

      <v-card elevation="3" outlined class="mx-auto col-md-5 col-6 my-6 text-center">
        <a href="#/datasets">
          <h1 class="display-2"><i class="mdi mdi-archive-search red--text text--lighten-3"></i></h1>
        </a>
        <v-card-title class="justify-center">Browse Datasets</v-card-title>
        <v-card-text>
          Find the data you're looking for! See all the Foundry datasets and get started.
        </v-card-text>
      </v-card>
    </v-row>


    <!-- Starter code and metadata section -->
    <div class="col-10 my-5 mx-auto pt-4">
      <h1 class="mb-5">We make collaboration easy</h1>
      <v-row class="mb-5">
        <div class="col-6">
          <vue-code-highlight language="python">
            <pre class="language-python">

f = f.load("foundry_stan_segmentation_v1.1")           
X,y = f.load_data()
</pre>
          </vue-code-highlight>

          <img alt="dendrite segmentation data snippet" src="../assets/dendrite-seg-img.png" class="col-12 pb-3" />

        </div>
        <div class="col-5">
          <p class="fw-light fs-4">
            Once a dataset is uploaded to Foundry, you can load it with just 2
            lines of code.
          </p>
          <a href="https://colab.research.google.com/github/MLMI2-CSSI/foundry/blob/main/examples/dendrite-segmentation/dendrite_segmentation.ipynb"
            target="blank"><button class="btn btn-primary">
              Run this in Google Colab
            </button></a>
        </div>
      </v-row>
      <!-- end of row -->
      <div class="col-12 text-end">
        <h1 class="col-11 my-5">and save you valuable time</h1>
      </div>
      <v-row>
        <v-col class="col-6">
          <p class="lead">
            No need to spend time making sense of someone else's data. We collect information about each dataset to
            take out any guesswork on your part. Our
            publishing process also includes a human review to make sure it meets our
            data standards.
          </p>
        </v-col>
        <v-col class="col-5">
          <v-simple-table dense class="col-12 mb-10">
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
                <tr>
                  <td>reference</td>
                  <td>input</td>
                  <td></td>
                  <td>source publication of the band gap value</td>
                </tr>
                <tr>
                  <td>structure</td>
                  <td>input</td>
                  <td></td>
                  <td>the structure of this compound</td>
                </tr>
                <tr>
                  <td>bandgap value (eV)</td>
                  <td>target</td>
                  <td>eV</td>
                  <td>tvalue of the band gap</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </v-col>
      </v-row>
      <!-- end of row -->
    </div>

    <!-- be a part of foundry section -->


    <div class="col-10 mx-auto mt-5">
      <h1 class="text-center my-3 text-h1">Build Foundry With Us</h1>
      <p class="col-8 mx-auto">
        At Foundry, we believe accessibility and collaboration are the keys to
        problem solving. That's why we've made it super easy for you to share
        and use data. If you have a dataset you'd like to contribute, our
        <a href="https://github.com/MLMI2-CSSI/foundry/tree/main/examples/publishing-guides" target="blank">publishing
          guide</a>
        can set you up to do that.
      </p>
      <p class="col-8 mx-auto">
        Check out our
        <a href="https://ai-materials-and-chemistry.gitbook.io/foundry/v/docs/" target="blank">documentation</a>
        to see how easy it is to use Foundry, and follow our
        <a href="https://github.com/MLMI2-CSSI/foundry/tree/main/examples" target="blank">examples</a>
        to do it all yourself.
      </p>
    </div>

  </div>
</template>

<script>

import { component as VueCodeHighlight } from 'vue-code-highlight';
import "vue-code-highlight/themes/prism-tomorrow.css";
import "vue-code-highlight/themes/window.css";
import 'prism-es6/components/prism-markup-templating';
import 'prism-es6/components/prism-python';


export default {
  name: 'Home',
  components: {
    VueCodeHighlight
  }
}
</script>
