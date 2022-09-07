<template>
    <v-footer padless color="white" class="col-12 mx-0 px-0 mt-10">
        <v-sheet color="indigo lighten-2" elevation="12" class="mx-auto text-center mt-10 pb-3 pt-10 col-12">
            <v-sheet rounded="xl" color="white" class="col-md-9 col-11 mx-auto">
                <a target="blank" href="https://www.uchicago.edu/"><img alt="logo" src="../assets/logo_UC.png"
                        class="px-8" /></a>
                <a target="blank" href="https://www.wisc.edu/"><img alt="logo" src="../assets/logo_UW.png"
                        class="px-8" /></a>
                <a target="blank" href="https://www.nsf.gov/"><img alt="logo" src="../assets/logo_NSF.png"
                        class="px-8" /></a>
                <a target="blank" href="https://www.anl.gov/"><img alt="logo" src="../assets/logo_ANL.png"
                        class="px-8" /></a>
            </v-sheet>
            <p class="pt-5 col-md-8 col-11 mx-auto font-weight-light white--text">This work was supported by the <a
                    class="red--text text--lighten-4" target="blank" href="https://www.nsf.gov/">National
                    Science
                    Foundation</a> under NSF Award Number: 1931306 "Collaborative Research: Framework: Machine Learning
                Materials
                Innovation Infrastructure".</p>
            <p class=" col-md-8 col-11 mx-auto font-weight-light white--text">This work was performed under financial
                assistance award 70NANB14H012 from U.S. Department of Commerce, National Institute of Standards and
                Technology
                as part of the <a class="red--text text--lighten-4" href="https://chimad.northwestern.edu/"
                    target="blank">Center for Hierarchical Material
                    Design (CHiMaD)</a>.</p>


            <div class="mx-auto">
                <a href="https://materialsdatafacility.org/" target="blank"><img alt="logo" src="../assets/logo_MDF.png"
                        class="px-6" /></a>
                <a href="https://globus.org/" target="blank"><img alt="logo" src="../assets/logo_globus.png"
                        class="px-6" /></a>
            </div>
            <v-card-text class="white--text pt-3  mx-auto text-body-1">
                <v-icon color="white" class="pb-3">mdi-arm-flex</v-icon> Powered by <a
                    class="red--text text--lighten-4 font-weight-bold" href="https://materialsdatafacility.org/"
                    target="blank">MDF</a> and <a class="red--text text--lighten-4 font-weight-bold"
                    href="https://www.globus.org/" target="blank">Globus</a>.
            </v-card-text>

            <v-divider class="mx-auto" width="90%" color="white"></v-divider>

            <v-card-text class="white--text">
                {{ new Date().getFullYear() }} — <strong>Foundry</strong>
            </v-card-text>
        </v-sheet>
    </v-footer>
</template>

<script>
export default {
    name: 'Footer'
</script>
  