<template>
    <div>
        <el-row>
            <el-col :span="24">
                <el-card>
                    <template #header><span>每日操作</span></template>
                    <div class="el-table el-table--enable-row-hover el-table--medium">
                        <div id="myChart" ref="chart" style="height: 420px" />
                    </div>
                </el-card>
            </el-col>
        </el-row>
    </div>
</template>

<script setup>
import * as echarts from 'echarts';
import { onMounted, ref } from 'vue';

onMounted(() => getList());

function getList() {
    let chart = echarts.init(document.getElementById("myChart"), "macarons");
    chart.setOption({

        title: {

            text: '今日话务统计'

        },

        tooltip: {

            trigger: 'axis',

            axisPointer: {

                type: 'shadow'

            }

        },

        grid: {

            left: '3%',

            right: '4%',

            bottom: '3%',

            containLabel: true

        },

        xAxis: [

            {

                type: 'category',

                data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],

                axisTick: {

                    alignWithLabel: true

                }

            }

        ],

        yAxis: [

            {

                type: 'value'

            }

        ],

        series: [

            {

                name: '直接访问',

                type: 'bar',

                barWidth: '60%',

                data: [10, 52, 200, 334, 390, 330, 220]

            }

        ]

    });
}
</script>