<template>

    <div>
        <div class="uk-child-width-1-1@s uk-grid-medium uk-grid-match" uk-grid>

            <ChartCard :datasets="doughnut_datasets" :labels="labels" :type="'doughnut'" :msg="'Candidatos por tipo de entrevista'"></ChartCard>
            <ChartCard :datasets="line_datasets" :labels="labels_line" :type="'line'" :msg="'Aplicantes por curso mensuales'"></ChartCard>
            <DashboardCard column="3" v-for="(interview, index) in interviews" :interview="interview" :key="index"></DashboardCard>


        </div>
    </div>

</template>
<script lang="ts">

    import Vue from 'vue';
    import {Component} from 'vue-property-decorator';
    import DashboardCard from '../components/Dashboard-card.vue';
    import ChartCard from '../components/Chart-card.vue';
    import Interview from '../models/interview.interface';
    import {appService} from "../services/app.service";

    @Component({
        components:{
            DashboardCard,
            ChartCard
        }
    })
    export default class Dashboard extends Vue{

        applicantsByCourse!: any[];

        // doughnut
        labels: string[] = [];
        doughnut_datasets: any[] = [];

        // line
        line_datasets!: any[];
        labels_line = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];


        interviews: Interview[] = [
            {
                name: "Entrevista técnica 1",
                type: 'technique',
                lounge: 20,
                applicants: 620,
                initial_date: "Mon Oct 13 2018 11:13:00 GMT-0500 (CDT)",
                final_date: "Mon Oct 15 2018 11:13:00 GMT-0500 (CDT)"
            },
            {
                name: "Entrevista personal 1",
                type: 'interview',
                lounge: 23,
                applicants: 220,
                initial_date: "Mon Oct 2 2018 11:13:00 GMT-0500 (CDT)",
                final_date: "Mon Oct 15 2018 11:13:00 GMT-0500 (CDT)"
            },
            {
                name: "Entrevista técnica 2",
                type: 'technique',
                lounge: 10,
                applicants: 956,
                initial_date: "Mon Oct 1 2018 11:13:00 GMT-0500 (CDT)",
                final_date: "Mon Oct 16 2018 11:13:00 GMT-0500 (CDT)"
            }
        ];

        beforeCreate(){
            this.applicantsByCourse = appService.getApplicantsByCourse();
        }

        created(){
            this.getLineChartData();
            this.getChartData();
        }

        getLineChartData(){
            
            let datasets = [
                {
                    data: [],
                    label: "UX/UI",
                    borderColor: "#7B1FA2",
                    backgroundColor: '#7B1FA2',
                    fill: false
                },
                {
                    data: [],
                    label: "part-time",
                    borderColor: "#FFEB3B",
                    backgroundColor: '#FFEB3B',
                    fill: false
                },
                {
                    data: [],
                    label: "full-time",
                    borderColor: "#32c3ff",
                    backgroundColor: '#32c3ff',
                    fill: false
                }
            ];
            
            
            this.applicantsByCourse.map(data=>{
                data.courses.map((course: any,i: number)=>{
                    let d = datasets[i].data as any[];
                    d.push(course.quantity);
                })
            });

            this.line_datasets = datasets;

        }

        getChartData(){

            let backgroundColor = [
                'rgba(41,121,255, 0.2)',
                'rgba(148,0,211, 0.2)',
                'rgba(255,82,82, 0.2)',
                'rgba(153, 102, 255, 0.2)',
                'rgba(75, 192, 192, 0.2)',
                'rgba(255, 206, 86, 0.2)',
                'rgba(255, 159, 64, 0.2)'
            ];

            let borderColor= [
                'rgb(41,121,255,1)',
                'rgba(148,0,211,1)',
                'rgba(255,82,82, 1)',
                'rgba(153, 102, 255, 1)',
                'rgba(75, 192, 192, 1)',
                'rgba(255, 206, 86, 1)',
                'rgba(255, 159, 64, 1)'
            ];


            let datasets = {
                data: [],
                backgroundColor: [],
                borderColor: []
            };
            this.interviews.map((interview, i)=>{

                let bgColors = datasets.backgroundColor as any[];
                let d = datasets.data as any[];
                let borColor = datasets.borderColor as any[];

                let d_result = datasets.data[this.labels.indexOf(interview.type)] as any;

                if(this.labels.indexOf(interview.type) === -1) {
                    this.labels.push(interview.type);
                    d.push(interview.applicants);
                    bgColors.push(backgroundColor[i]);
                    borColor.push(borderColor[i]);
                    return;
                }
                d_result = d_result += interview.applicants;
            });
            this.doughnut_datasets.push(datasets);
        }

    }


</script>

<style>
    #dashboard table thead th{
        text-align: center !important;
    }
</style>