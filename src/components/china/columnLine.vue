<template>
  <div class="line-column-box" :id="ids"></div>
</template>

<script>
export default {
  name: "",
  props: ["ids", "chartData"],
  mounted() {
    this.initColumnChart(this.ids, this.chartData);
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    initColumnChart(id, data) {
      //   if (!data || JSON.stringify(data) == '"{}"') return;
      data = {};
      let myCharts = this.$echarts.init(document.getElementById(id));
      myCharts.setOption({
        tooltip: {
          //提示框组件
          trigger: "axis",
          //   formatter: "{b}<br />{a0}: {c0}<br />{a1}: {c1}<br />{a2}: {c2}",
          axisPointer: {
            type: "shadow",
            label: {
              backgroundColor: "#6a7985"
            }
          },
          backgroundColor: "rgba(70,130,180,0.8)",
          borderColor: "rgba(47,79,79,1)",
          borderWidth: 1,
          padding: [12, 24],
          textStyle: {
            color: "rgba(255, 255, 255, 0.8)",
            fontStyle: "normal",
            fontFamily: "微软雅黑",
            fontSize: 24
          }
        },
        grid: {
          left: "3%",
          right: "3%",
          bottom: "1%",
          top: "20%",
          //	padding:'0 0 10 0',
          containLabel: true
        },
        legend: {
          //图例组件，颜色和名字
          right: "3%",
          top: "3%",
          itemGap: 44,
          itemWidth: 24,
          itemHeight: 24,
          data: [
            {
              name: data.y ? data.y[0].name : "贷款发放额"
              //icon:'image://../wwwroot/js/url2.png', //路径
            },
            // {
            //   name: data.y ? data.y[1].name : "实际数"
            // },
            {
              name: data.y ? data.y[2].name : "贷款余额",
              icon: "rect"
            }
          ],
          textStyle: {
            color: "#a8aab0",
            fontStyle: "normal",
            fontFamily: "微软雅黑",
            fontSize: 24
          }
        },
        xAxis: [
          {
            type: "category",
            //	boundaryGap: true,//坐标轴两边留白
            data: data.x
              ? data.x[0].data
              : [
                  "1月",
                  "2月",
                  "3月",
                  "4月",
                  "5月",
                  "6月",
                  "7月",
                  "8月",
                  "9月",
                  "10月",
                  "11月",
                  "12月"
                ],
            axisLabel: {
              //坐标轴刻度标签的相关设置。
              //		interval: 0,//设置为 1，表示『隔一个标签显示一个标签』
              //	margin:15,
              textStyle: {
                color: "rgba(255,255,255,.6)",
                fontStyle: "normal",
                fontFamily: "微软雅黑",
                fontSize: 24
              }
            },
            axisTick: {
              //坐标轴刻度相关设置。
              show: false
            },
            axisLine: {
              //坐标轴轴线相关设置
              lineStyle: {
                color: "#fff",
                opacity: 0.2
              }
            },
            splitLine: {
              //坐标轴在 grid 区域中的分隔线。
              show: false
            }
          }
        ],
        yAxis: [
          {
            type: "value",
            splitNumber: 5,
            min: 0,
            max: 100,
            axisLabel: {
              textStyle: {
                color: "#a8aab0",
                fontStyle: "normal",
                fontFamily: "微软雅黑",
                fontSize: 24
              }
            },
            axisLine: {
              show: false
            },
            axisTick: {
              show: false
            },
            splitLine: {
              show: true,
              lineStyle: {
                color: "rgba(255,255,255,1)",
                width: 4,
                opacity: 0.2
              }
            }
          },
          {
            type: "value",
            name: "",
            min: 0,
            max: 100,
            axisLabel: {
              show: false,
              formatter: "{value}",
              textStyle: {
                color: "#FFF",
                fontSize: 12
              }
            },
            axisLine: {
              show: false,
              lineStyle: {
                color: "#FFF"
              }
            },
            axisTick: {
              show: false
            },
            splitLine: {
              show: false,
              lineStyle: {
                type: "dashed",
                width: 1,
                color: "rgba(255,255,255,0.2)"
              }
            }
          }
        ],
        series: [
          {
            name: data.y ? data.y[0].name : "贷款发放额",
            type: "bar",
            data: data.y
              ? data.y[0].data
              : [10, 15, 30, 45, 55, 60, 62, 80, 80, 62, 60, 14],
            barWidth: 14,
            barGap: 0, //柱间距离
            itemStyle: {
              normal: {
                show: true,
                color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  {
                    offset: 0,
                    color: "rgba(32,242,255,1)"
                  },
                  {
                    offset: 1,
                    color: "rgba(0,63,190,1)"
                  }
                ]),
                // barBorderRadius: [30, 30, 0, 0],
                borderWidth: 0
              }
            }
          },
          //   {
          //     name: data.y ? data.y[1].name : "实际数",
          //     type: "bar",
          //     data: data.y
          //       ? data.y[1].data.map((item, index) => {
          //           if (
          //             data.x[0].data[index] === currentPro ||
          //             (data.x[0].data[index] === "直属" &&
          //               currentPro === "直属单位")
          //           ) {
          //             return {
          //               value: item,
          //               itemStyle: {
          //                 normal: {
          //                   show: true,
          //                   color: new this.$echarts.graphic.LinearGradient(
          //                     0,
          //                     0,
          //                     0,
          //                     1,
          //                     [
          //                       {
          //                         offset: 0,
          //                         color: "rgba(255,228,181,1)"
          //                       },
          //                       {
          //                         offset: 1,
          //                         color: "rgba(255,222,173,1)"
          //                       }
          //                     ]
          //                   ),
          //                   barBorderRadius: [30, 30, 0, 0],
          //                   borderWidth: 0
          //                 }
          //               }
          //             };
          //           } else {
          //             return item;
          //           }
          //         })
          //       : [8, 5, 25, 30, 35, 55, 62, 78, 65, 55, 60],
          //     barWidth: 14,
          //     barGap: 0, //柱间距离
          //     itemStyle: {
          //       normal: {
          //         show: true,
          //         color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [
          //           {
          //             offset: 0,
          //             color: "rgba(21,255,255,1)"
          //           },
          //           {
          //             offset: 1,
          //             color: "rgba(0,150,255,1)"
          //           }
          //         ]),
          //         barBorderRadius: [30, 30, 0, 0],
          //         borderWidth: 0
          //       }
          //     }
          //   },
          {
            name: data.y ? data.y[2].name : "贷款余额",
            type: "line",
            data: data.y
              ? data.y[1].data
              : [8, 5, 25, 30, 35, 55, 62, 78, 65, 55, 60, 92],
            yAxisIndex: 0,
            smooth: 0.5,
            symbolSize: 0,
            symbol: "circle",
            lineStyle: {
              normal: {
                width: 6,
                color: "rgba(222,159,100,1)"
              }
            },
            itemStyle: {
              normal: {
                color: "rgba(222,159,100,1)",
                borderColor: "#fff",
                borderWidth: 2
              }
            },
            label: {
              normal: {
                show: false
              }
            }
          }
        ]
      });
    }
  },
  components: {},
  watch: {
    chartData: function(newVal) {
      this.initColumnChart(this.ids, newVal);
    }
  }
};
</script>

<style lang="less" scoped>
</style>
