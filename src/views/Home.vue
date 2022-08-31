<template>
  <div class="home col-12 mb-5">
    <!-- heading content -->
    <div class="jumbotron text-center py-5 col-12 bg-light">
      <h1 class="display-4 col-10 mx-auto">
        An open source machine learning platform for scientists
      </h1>
      <p class="lead mt-3 col-7 mx-auto">
        Access datasets and ML models while setting industry benchmarks
      </p>
    </div>

    <!-- middle content -->
    <div class="row my-5">
      <div class="col-10 mx-auto">
        <div class="row">
          <div class="col-sm-4 mx-auto">
            <div class="card">
              <div class="card-body text-center">
                <a href="https://github.com/MLMI2-CSSI/foundry/tree/main/examples/publishing-guides" target="blank">
                  <b-icon icon="file-bar-graph" class="display-4 icons my-2"></b-icon>
                </a>

                <h5 class="card-title mt-2">Add your dataset</h5>
                <p class="card-text">
                  We host data from a variety of scientific domains and make it
                  easy to share and use.
                </p>
              </div>
            </div>
          </div>
          <div class="col-sm-4 mx-auto">
            <div class="card">
              <div class="card-body text-center">
                <a href="https://github.com/MLMI2-CSSI/foundry/tree/main/examples/publishing-guides" target="blank">
                  <b-icon icon="gear" class="display-4 icons my-2"></b-icon>
                </a>

                <h5 class="card-title mt-2">Browse Datasets</h5>
                <p class="card-text">
                  
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Starter code and metadata section -->
    <div class="col-10 my-5 mx-auto pt-4">
      <h1 class="mb-5">We make collaboration easy</h1>
      <div class="row mb-5">
        <div class="col-6">
          <vue-code-highlight language="python">
            <pre class="language-python">

f = f.load("foundry_stan_segmentation_v1.1")           
X,y = f.load_data()
</pre>
          </vue-code-highlight>

          <img
          alt="dendrite segmentation data snippet"
          src="../assets/dendrite-seg-img.png"
          class="col-12 pb-3"
        />

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
      </div>
      <!-- end of row -->
      <div class="col-12 text-end">
        <h1 class="col-11 my-5">and save you valuable time</h1>
      </div>
      <div class="row">
        <div class="col-6">
          <p class="lead">
            No need to spend time making sense of someone else's data. We collect information about each dataset to
            take out any guesswork on your part. Our
            publishing process also includes a human review to make sure it meets our
            data standards.
          </p>
        </div>
        <div class="col-5">
          <table class="table table-striped">
            <tbody>
              <tr>
                <td class="fw-bold">hello</td>
                <td>hello</td>
              </tr>
              <tr>
                <td class="fw-bold">hello</td>
                <td>hello</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <!-- end of row -->
    </div>

    <!-- be a part of foundry section -->

    <hr class="col-10 m-auto" />

    <div class="mx-auto col-7 mt-5">
      <div class="col-11 mx-auto">
        <h1 class="text-center my-3 display-4">Build Foundry With Us</h1>
        <p>
          At Foundry, we believe accessibility and collaboration are the keys to
          problem solving. That's why we've made it super easy for you to share
          and use data. If you have a dataset you'd like to contribute, our
          <a href="https://github.com/MLMI2-CSSI/foundry/tree/main/examples/publishing-guides" target="blank">publishing
            guide</a>
          can set you up to do that.
        </p>
        <p>
          Check out our
          <a href="https://ai-materials-and-chemistry.gitbook.io/foundry/v/docs/" target="blank">documentation</a>
          to see how easy it is to use Foundry, and follow our
          <a href="https://github.com/MLMI2-CSSI/foundry/tree/main/examples" target="blank">examples</a>
          to do it all yourself.
        </p>
      </div>
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
