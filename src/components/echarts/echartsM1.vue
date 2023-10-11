<template>
  <div id="m1" style="width: 20%; height: 20%"></div>
</template>

<script>
import { getData } from "@/api/electricityfee";
import * as echarts from 'echarts';
export default {
  mounted() {
    this.draw();
    this.getDataM1();
  },
  methods: {
    draw() {
      let myChart = echarts.init(document.getElementById("m1"));
      window.addEventListener('resize', function () {
        myChart.resize();
      });
      let txt = 51;
      let option = {
        title: {
          text: txt + "%",
          x: "center",
          y: "center",
          textStyle: {
            fontWeight: "normal",
            color: "#000000",
            fontSize: "10",
          },
        },
        color: "rgba(0,0,0,0.3)",

        series: [
          {
            name: "Line 1",
            type: "pie",
            clockwise: true,
            radius: ["65%", "80%"],
              label: {
                  show: false,
              },
              labelLine: {
                  show: false,
              },
            hoverAnimation: false,
            data: [
              {
                value: txt,
                name: "已使用",
                itemStyle: {
                  normal: {
                    color: "#1852FC",
                    label: {
                      show: false,
                    },
                    labelLine: {
                      show: false,
                    },
                  },
                },
              },
              {
                name: "未使用",
                value: 100 - txt,
              },
            ],
          },
        ],
      };

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
      window.addEventListener("resize", function () {
        myChart.resize();
      });
    },
    getDataM1() {
      getData()
        .then((data) => {
          let chart = echarts.getInstanceByDom(document.getElementById("m1"));
          let option = chart.getOption();
          console.log(data); // 处理获取到的数据
          let tempdata = data[0];
          option.series[0].data[0].value = (parseFloat(tempdata.air1) * 100).toFixed(1);
          option.series[0].data[1].value = (100 - parseFloat(tempdata.air1) * 100).toFixed(1);
          option.title[0].text = (parseFloat(tempdata.air1) * 100).toFixed(1) + '%';
          chart.setOption(option);
        })
        .catch((error) => {
          console.log(error); // 处理错误
        });
    },
  },
};
</script>
