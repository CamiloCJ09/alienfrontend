<template>
    <div>
        <!-- <card>
			<div class="contanerTop">
				<div class="containerInfo">
					<h1>K-Means</h1>
					<p>El algoritmo K-Means propuesto en 1967 tiene como objetivo realizar k particiones en un conjunto de datos proporcionado. Cada partición está representada por un punto (llamado centroide) que es el promedio de los puntos en esa partición. Este método empieza con k centroides aleatorios, posteriormente se asignan los datapoints más cercanos a estos, se reasigna el vlaor del centroide respecto a los valores de cada cluster y se vuelve a hacer la asignación de puntos. Este proceso se itera hasta que el cambio en los clusters sea mínimo.</p>
                    <div v-katex:auto>
                        \(d(x_{i},q_{l})=\sum_{s=p+1}^{m}\sqrt{(x_{i,s}^{N}-q_{l,s}^{N})^{2}}\)
                    </div>
				</div>
                <br/>
				<div class="containerInfo">
					<h1>K-Prototypes</h1>
					<p>El algoritmo K-Prototypes trabaja de una manera muy similar al K-Means; sin embargo, mientras el primero toma en cuenta valores tanto discretos como contínuos, el segundo únicamente admite valores contínuos. El proceso es el mismo, la única diferencia es su función de coste, que básicamente es la misma del K-means pero sumándole una función delta para las variables discretas.</p>
					<div v-katex:auto>
                        \(d(x_{i},q_{l})=\gamma\sum_{s=1}^{p}\delta(x_{i,s}^{c}-q_{l,s}^{c})+\sum_{s=p+1}^{m}\sqrt{(x_{i,s}^{N}-q_{l,s}^{N})^{2}}\)
                    </div>
                    <div v-katex:auto>
                        \(\delta(x_{i},q_{l})=\begin{Bmatrix}
                        0,x_{i,s}=q_{l,s'}
                        \\
                        1,x_{i,s}\neq q_{l,s'}
                        \end{Bmatrix}\)
                    </div>
				</div>
                <div class="containerInfo">
					<h1>PCA</h1>
					<p>El análisis de componenetes principales o PCA por sus siglas en inglés, es una técnica que reduce la dimensionalidad de un conjunto de datos, ya sea para su procesamiento o como herramienta de visualización para el análisis exploratorio de datos.</p>
				</div>
			</div>
			
			<div class="containerMid">
				
			</div>
        </card> -->

        <div class="col-12" align="center">
            <h1>Clustering</h1>
            <base-button type="primary" @click.native="modals.clustering = true">About</base-button>
        </div>

        <!--About.................................................................................................................-->
            <!--Clustering-->
        <modal
        :show.sync="modals.clustering"
        footerClasses="justify-content-center"
        type="notice"
        scrollable
        >
            <div slot="header">
                <h1 class="title title-up text-primary">Clustering</h1>
            </div>
            <div slot="close-button">
                <base-button icon link type="primary" @click.native="modals.clustering = false">
                    <i class="tim-icons icon-simple-remove text-primary"></i>
                </base-button>
            </div>
            <div class="instruction">
                <div class="row">
                    <p class="description">
                        Explication.
                    </p>
                </div>
            </div>
            <template slot="footer">
                <div class="mr-auto p-2">
                    <base-button type="primary" round @click.native="modals.clustering = false, modals.kmeans = true">K-Means</base-button>
                </div>
                <div class="mr-auto p-2">
                    <base-button type="primary" round @click.native="modals.clustering = false, modals.kprototypes = true">K-Prototypes</base-button>
                </div>
                <div class="mr-auto p-2">
                    <base-button type="primary" round @click.native="modals.clustering = false, modals.pca = true">PCA</base-button>
                </div>
                <div class="ml-auto p-2">
                    <base-button type="secundary" round @click.native="modals.clustering = false">Ok</base-button>
                </div>
            </template>
        </modal>
            <!--K-Means-->
        <modal
        :show.sync="modals.kmeans"
        footerClasses="justify-content-center"
        type="notice"
        >
            <div slot="header">
                <h1 class="title title-up text-primary">K-Means</h1>
            </div>
            <div slot="close-button">
                <base-button icon link type="primary" @click.native="modals.clustering = false">
                    <i class="tim-icons icon-simple-remove text-primary"></i>
                </base-button>
            </div>
            <div class="instruction">
                <div class="row">
                    <p class="description">
                        El algoritmo K-Means propuesto en 1967 tiene como objetivo realizar k 
                        particiones en un conjunto de datos proporcionado. Cada partición 
                        está representada por un punto (llamado centroide) que es el promedio 
                        de los puntos en esa partición. Este método empieza con k centroides 
                        aleatorios, posteriormente se asignan los datapoints más cercanos a 
                        estos, se reasigna el vlaor del centroide respecto a los valores de 
                        cada cluster y se vuelve a hacer la asignación de puntos. Este 
                        proceso se itera hasta que el cambio en los clusters sea mínimo.
                    </p>
                    <div v-katex:auto class="text-primary">
                            \(d(x_{i},q_{l})=\sum_{s=p+1}^{m}\sqrt{(x_{i,s}^{N}-q_{l,s}^{N})^{2}}\)
                    </div>
                </div>
            </div>
            <template slot="footer">
                <div class="mr-auto p-2">
                    <base-button type="primary" round @click.native="modals.kmeans = false, modals.clustering = true">Back</base-button>
                </div>
                <div class="ml-auto p-2">
                    <base-button type="secundary" round @click.native="modals.kmeans = false">Ok</base-button>
                </div>
            </template>
        </modal>
            <!--K-Prototypes-->
        <modal
        :show.sync="modals.kprototypes"
        footerClasses="justify-content-center"
        type="notice"
        >
            <div slot="header">
                <h1 class="title title-up text-primary">K-Prototypes</h1>
            </div>
            <div slot="close-button">
                <base-button icon link type="primary" @click.native="modals.clustering = false">
                    <i class="tim-icons icon-simple-remove text-primary"></i>
                </base-button>
            </div>
            <div class="instruction">
                <div class="row">
                    <p class="description">
                        El algoritmo K-Prototypes trabaja de una manera muy similar al K-Means; 
                        sin embargo, mientras el primero toma en cuenta valores tanto discretos 
                        como contínuos, el segundo únicamente admite valores contínuos. El 
                        proceso es el mismo, la única diferencia es su función de coste, que 
                        básicamente es la misma del K-means pero sumándole una función delta 
                        para las variables discretas.
                    </p>
                    <div v-katex:auto class="text-primary">
                        \(d(x_{i},q_{l})=\gamma\sum_{s=1}^{p}\delta(x_{i,s}^{c}-q_{l,s}^{c})+\sum_{s=p+1}^{m}\sqrt{(x_{i,s}^{N}-q_{l,s}^{N})^{2}}\)
                    </div>
                    <div v-katex:auto class="text-primary">
                        \(\delta(x_{i},q_{l})=\begin{Bmatrix}
                        0,x_{i,s}=q_{l,s'}
                        \\
                        1,x_{i,s}\neq q_{l,s'}
                        \end{Bmatrix}\)
                    </div>
                </div>
            </div>
            <template slot="footer">
                <div class="mr-auto p-2">
                    <base-button type="primary" round @click.native="modals.kprototypes = false, modals.clustering = true">Back</base-button>
                </div>
                <div class="ml-auto p-2">
                    <base-button type="secundary" round @click.native="modals.kprototypes = false">Ok</base-button>
                </div>
            </template>
        </modal>
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
                <base-button icon link type="primary" @click.native="modals.clustering = false">
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
                <div class="mr-auto p-2">
                    <base-button type="primary" round @click.native="modals.pca = false, modals.clustering = true">Back</base-button>
                </div>
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
                    <!--Algorithm-->
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="top"
                    >
                        <div slot="content"><b class="text-primary">Algorithm:</b><br/>The algorithm to generate the clusters.</div>
                        <Select
                        required
                        id="inputAlgorithm"
                        name = "algorithm"
                        type="primary"
                        v-model="input.algorithm"
                        v-validate="inputValidations.algorithm"
                        :error="getError('Algorithm')"
                        placeholder="Algorithm"
                        class="select-default col-md-4"
                        >
                            <Option type="primary" value="K-Means" label="K-Means" key="K-Means"></Option>
                            <Option type="primary" value="K-Prototype" label="K-Prototype" key="K-Prototype"></Option>
                        </Select>
                    </el-tooltip>
                    <!--Clusters-->
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="right"
                    >
                        <div slot="content"><b class="text-primary">Clusters:</b><br/>The number of clusters.</div>
                        <base-input
                        required
                        id="k"
                        name="clusters"
                        type="number"
                        v-model="input.clusters"
                        v-validate="inputValidations.clusters"
                        :error="getError('Clusters')"
                        placeholder="Clusters"
                        class="col-md-4 select-default"
                        />
                    </el-tooltip>
                </div>
                <div class = "form-row">
                    <!--PCA-->
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="right"
                    >
                        <div slot="content"><b class="text-primary">PCA:</b><br/>If the algorithm is using pca.</div>
                        <base-checkbox
                        name = "pca"
                        v-model="input.pca"
                        v-validate="inputValidations.pca"
                        :error="getError('PCA')"
                        class="mb-3 col-md-1"
                        >
                            PCA
                        </base-checkbox>
                    </el-tooltip>
                </div>
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
                        <div slot="content"><b class="text-primary">Submit:</b><br/>Submit the the data to generate the graph or table.</div>
                        <base-button type="primary" v-on:click="submitFile()" class="col-md-2">Submit</base-button>
                    </el-tooltip>
                </div>
            </form>
            <div>
                <!--chart-->
                <div id="scat" style="width: 80%">
                    <canvas id="myChart"></canvas>
                </div>
            </div>
            <form>
                <div class="form-row">
                    <!--Iteration-->
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="bottom"
                    >
                        <div slot="content"><b class="text-primary">Iteration:</b><br/>The number of steps is going to make.</div>
                        <base-input
                        required
                        id="iteration"
                        name="iteration"
                        value = 1
                        type="number"
                        v-model="input.iteration"
                        v-validate="inputValidations.iteration"
                        :error="getError('Iteration')"
                        placeholder="Iterations"
                        class="col-md-4 select-default"
                        />
                    </el-tooltip>
                    <!--Next-->
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="bottom"
                    >
                        <div slot="content"><b class="text-primary">Next:</b><br/>Move the number of specified iterations.</div>
                        <base-button type="primary" v-on:click="step()" class="col-md-2">Next</base-button>
                    </el-tooltip>
                    <!--End-->
                    <el-tooltip
                    effect="light"
                    :open-delay="200"
                    placement="right"
                    >
                        <div slot="content"><b class="text-primary">End:</b><br/>Show the final result of the algorithm.</div>
                        <base-button type="primary" class="col-md-2">End</base-button>
                    </el-tooltip>
                    
                </div>
            </form>
            <br>
            <div slot="content"><b class="text-primary">ShowTable:</b><br/>Show the final table of the algorithm.</div>
                        <base-button type="primary" v-on:click="showDataTable()" class="col-md-2">Show Table</base-button>
            <div>
                <!--table-->
                <div id="table" style="width: 80%">
                    <table id="myTable" class="table table-striped table-bordered">
                        <thead>
                            <tr>
                                <th>Cluster</th>
                                <th>Amount</th>
                                <th>Percentage</th>
                                <th>Standar Deviation</th>
                            </tr>
                        </thead>
                        <tbody id="tbodyMyTable">
                            
                        </tbody>
                    </table>
                </div>
            </div>
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
import clusters from './clusters.json';


Vue.use(VueKatex, {
  globalOptions: {
    //... Define globally applied KaTeX options here
  }
});

export default {

    name: "pm",

	components: {
        Select,
        Option,
        Modal,
        BaseAlert,
BaseButton
	},

    data(){

        return{
            file: '',
            scatter: '',

            series: '',
            canvas: '',
            ctx: '',
            chart:'',

            model:'',
            avilableIterations:'',
            iterationIndex:'',
            
            //Modals
            modals: {
                clustering: false,
                kmeans: false,
                kprototypes: false,
                pca: false,
            },
            //...

            //Inputs
            input: {
                algorithm: '',
                clusters: 2,
                pca: false,
                iteration: 1
            },
            inputValidations: {
                algorithm:{
                    required: true
                },
                clusters:{
                    required: true,
                    max_value: 8
                },
                pca:{
                    required: true
                },
                iteration:{
                    required: true
                }
            },
            //...
        }

    },

    methods: {
        //Inputs
        getError(fieldName) {
            return this.errors.first(fieldName);
        },
        validate() {
            this.$validator.validateAll().then(isValid => {
                this.$emit('on-submit', this.registerForm, isValid);
            });
        },
        //...

        //Rgb generator
        colors(values){
            return this.recursiveColors(values, 0, [0,0,0]);
        },

        recursiveColors(values, pos, combination){
            var colors = [];
            if(pos < combination.length){
                for(let i = 0; i < values.length; i++){
                    var c = [...combination];
                    c[pos] = values[i];

                    var e = this.recursiveColors(values, pos+1, c);

                    colors = [...colors, ...e];
                }
            }
            else{
                colors.push(combination);
            }
            return colors;
        },
        //...

        
        canvaConfig(){
            this.canvas = document.getElementById('myChart');
            this.ctx = this.canvas.getContext('2d');
        },

        submitFile(){

            let formData = new FormData();

            formData.append('file', this.file);
            formData.append('clusters', parseInt(document.getElementById("k").value));
            formData.append('iteration', parseInt(document.getElementById("iteration").value));
            formData.append('model', JSON.stringify(this.model))

            axios.post( 'http://localhost:5000/upl',
                formData,
                {
                    headers: {
                    'Content-Type': 'multipart/form-data'
                    }
                }
            ).then((response) => { 
                console.log('SUCCESS!!');
                
                console.log(response.data)
                this.model = response.data["step"];
                this.scatter = response.data["step"];
                this.avilableIterations = Object.keys(this.scatter)
                this.iterationIndex = this.avilableIterations[0]

                this.graphRoute();
            })
            // .catch(function(response){
            //     console.log(response.message);
            // });
        },
        showDataTable(realClusters = clusters){
            console.log(realClusters)
            //llenar la tabla de clusters
            var table = document.getElementById("myTable");
            var old_tbody = document.getElementById("tbodyMyTable");
            var new_tbody = document.createElement('tbody');
            
            tbodyMyTable.parentNode.replaceChild(new_tbody, old_tbody)
            for(let i = 0; i < realClusters.length; i++){
                var row = table.insertRow(i+1);
                var cell1 = row.insertCell(0);
                var cell2 = row.insertCell(1);
                var cell3 = row.insertCell(2);
                var cell4 = row.insertCell(3);

                cell1.innerHTML = realClusters[i].cluster;
                cell2.innerHTML = realClusters[i].amount;
                cell3.innerHTML = realClusters[i].percent;
                cell4.innerHTML = realClusters[i].standarDeviation;
            }
        },

        chooseFiles() {
            document.getElementById("file").click();
        },

        handleFileUpload(){
            this.file = this.$refs.file.files[0];
            console.log(this.file);
        },

        graphRoute(){
            this.ctx.clearRect(0,0, this.canvas.width, this.canvas.height);
            this.formatData();
            
            if(this.chart == ''){//[Change]
                this.chart = new Chart(this.ctx, {
                    type: 'scatter',
                    data: {
                        datasets: this.series
                        
                    },
                    options: {
                        scales: {
                            xAxes: [{
                                type: 'linear',
                                position: 'bottom',
                                offset: true
                            }]
                        },
                    }
                });
            }
            else{
                this.chart.data.datasets = this.series;
                this.chart.update();
            }
        },

        formatData(){
            

            let data = [];

            //console.log(" >>> Dic Lenght >>> ", Object.keys(this.scatter).length);
            //console.log(" >>> key 0 lenght >>> ", Object.keys(this.scatter[50]).length);
            //console.log(" >>> Access to array >>> ", this.scatter[50][0]);
            //console.log(" >>> ACUÉHTATE >>> ", Object.keys(this.scatter)[0]);
            
            console.log(">>> MOOOODEL >>>", this.model[this.iterationIndex]);

            for(let i=0; i < Object.keys(this.model[this.iterationIndex]).length; i++){

                let dic = []; 

                for(let j=0; j < this.model[this.iterationIndex][i].length; j++){
                    
                    let tempDic = {};

                    tempDic['x'] = this.model[this.iterationIndex][i][j][0];
                    tempDic['y'] = this.model[this.iterationIndex][i][j][1];

                    dic.push(tempDic);
                }

                data.push(dic);
            }

           

            this.scatter = data;



            let datasets = [];

            // var cColors = [
            //     [1,0,0],
            //     [0,1,0],
            //     [0,0,1],
            //     [1,1,0],
            //     [1,0,1],
            //     [0,1,1],
            //     [0,0,0],
            //     [1,1,1]
            // ];
            var cColors = this.colors([0,  0.5,  1]);
            var i = 0;

            var COLORS = [];
            while (COLORS.length < Object.keys(this.scatter).length) {
                if(cColors.length > i){
                    COLORS.push(`rgb(${cColors[i][0]*255}, ${cColors[i][1]*255}, ${cColors[i][2]*255})`);
                }
                else{
                    COLORS.push(`rgb(${this.rand(0,255)}, ${this.rand(0,255)}, ${this.rand(0,255)})`);
                }
                i++;
            }
            

            for(let i = 0; i < data.length; i++){
                
                let dic = {};

                

                dic['label'] = `K${i+1}`;
                dic['showline'] = false;
                dic['fill'] = false;
                dic['borderColor'] = COLORS[i];
                dic['data'] = this.scatter[i];

                datasets[i] = dic;
            }

            this.series = datasets;
        },

        rand(frm, to) {
            return ~~(Math.random() * (to - frm)) + frm;
        },
        
        step(){
            //for(let i = 0; i < #; i++){
                this.iterationIndex  = this.forward();
                this.graphRoute();
            //}
        },
        forward(){
            
            let ind = this.avilableIterations.indexOf(this.iterationIndex);
            var respon = 0;

            console.log(">>> ind >>>", ind);

            if(ind <=3){
                respon = this.avilableIterations[parseInt(ind+1)];
            }

            console.log(respon);
            return respon;
        }

    },
    mounted(){
        this.canvaConfig()
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