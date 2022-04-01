<template>
    <div>
        <div class="col-12" align="center">
            <h1>PCA</h1>
            <base-button type="primary" @click.native="modals.pca = true">About</base-button>
            <base-button type="primary" @click.prevent="downloadFile('/files/clusteringTest.csv', 'Test.csv')">Test</base-button>
        </div>

        <!--About.................................................................................................................-->
            <!--PCA-->
        <modal
        :show.sync="modals.pca"
        footerClasses="justify-content-center"
        type="notice"
        >
            <div slot="header">
                <h1 class="title title-up text-primary">PCA</h1>
            </div>
            <div slot="close-button">
                <base-button icon link type="primary" @click.native="modals.pca = false">
                    <i class="tim-icons icon-simple-remove text-primary"></i>
                </base-button>
            </div>
            <div class="instruction">
                <div class="row">
                    <p class="description">
                        El análisis de componenetes principales o PCA por sus siglas en 
                        inglés, es una técnica que reduce la dimensionalidad de un 
                        conjunto de datos, ya sea para su procesamiento o como 
                        herramienta de visualización para el análisis exploratorio de 
                        datos.
                    </p>
                </div>
            </div>
            <template slot="footer">
                <div class="ml-auto p-2">
                    <base-button type="secundary" round @click.native="modals.pca = false">Ok</base-button>
                </div>
            </template>
        </modal>
        <!--......................................................................................................................-->

        <br/>

        <card class="containerBot">
            <form>
                <div class="form-row">
                    <!--Select Dataset-->
                    <input type="file" id="file" ref="file" v-on:change="handleFileUpload()" hidden/>
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="bottom"
                    >
                        <div slot="content"><b class="text-primary">Select Dataset:</b><br/>Select a csv file to upload the dataset.</div>
                        <base-button type="primary" v-on:click="chooseFiles()" class="col-md-2">Upload File</base-button>
                    </el-tooltip>
                    <!--Submit-->
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="right"
                    >
                        <div slot="content"><b class="text-primary">Submit:</b><br/>Submit the the data to generate the graphic.</div>
                        <base-button type="primary" v-on:click="submitFile()" class="col-md-2">Submit</base-button>
                    </el-tooltip>
                </div>
            </form>
        </card>
    </div>
</template>

<script>
import axios from 'axios';
import {Modal, BaseAlert } from "../../../components";
import {Select, Option} from 'element-ui';
import Vue from 'vue';
import VueKatex from 'vue-katex';
import 'katex/dist/katex.min.css';
import BaseButton from '../../../components/BaseButton.vue';
axios.defaults.withCredentials = true

export default {

    name: "pm",

	components: {
        Modal,
	},

    data(){

        return{
            file: '',

            //Modals
            modals: {
                clustering: false,
                kmeans: false,
                kprototypes: false,
                pca: false,
            },
            //...
        }

    },

    methods: {

        //File
        chooseFiles() {
            document.getElementById("file").click();
        },

        submitFile(){

            let formData = new FormData();

            formData.append('file', this.file);

        },

        downloadFile(url, label){
            axios.get(url, { responseType: 'blob' })
                .then(response => {
                    const blob = new Blob([response.data], { type: 'application/pdf' })
                    const link = document.createElement('a')
                    link.href = URL.createObjectURL(blob)
                    link.download = label
                    link.click()
                    URL.revokeObjectURL(link.href)
                }).catch(console.error)
        },

    }
  }

</script>

<style>
@import "../../../../node_modules/katex/dist/katex.min.css";

h1 {
  margin-bottom: 0.5em;
}

.config{
    display: block;
    margin-top: 1.5em;
    margin-bottom: 1.5em;
}
</style>