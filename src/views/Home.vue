<template>
  <v-container fill-height fluid style="background: #1c1c1c">
    <v-row>
      <!-- 榮譽榜 -->
      <v-col cols="12" sm="5" md="5">
        <v-col cols="12">
          <v-card color="#D0104C" dark>
            <v-card-title class="headline"> 榮譽榜 </v-card-title>

            <v-card-subtitle>2021年-<strong>OOO亞盃</strong></v-card-subtitle>

            <v-row>
              <!-- 排名 -->
              <v-col cols="8">
                <v-card-text>
                  <span v-for="(member, i) in competitors" :key="i">
                    <div v-if="member.rank === 1">
                      <strong>{{ member.rank }}.</strong>
                      {{ member.name }}
                      <v-icon dark>mdi-fire</v-icon>
                      <br />
                    </div>
                    <div v-else-if="member.rank === competitors.length">
                      <strong>{{ member.rank }}.</strong>
                      {{ member.name }}
                      <v-icon dark>mdi-emoticon-poop </v-icon>
                      <br />
                    </div>
                    <div v-else>
                      <strong>{{ member.rank }}.</strong>
                      {{ member.name }}
                      <br />
                    </div>
                  </span>
                </v-card-text>
              </v-col>
              <!-- 積分 -->
              <v-col cols="4">
                <v-card-text>
                  <strong v-for="(member, i) in competitors" :key="i"
                    >{{ member.score }} 分<br
                  /></strong>
                </v-card-text>
              </v-col>
            </v-row>
          </v-card>
        </v-col>

        <v-col cols="12">
          <p style="color: white">Supporting Player Counts</p>
          <v-slide-group show-arrows dark>
            <v-btn-toggle v-model="toggle_support" rounded>
              <v-btn :value="1"> 1P </v-btn>
              <v-btn :value="2"> 2P </v-btn>
              <v-btn :value="3"> 3P </v-btn>
              <v-btn :value="4"> 4P </v-btn>
              <v-btn :value="5"> 5P </v-btn>
              <v-btn :value="6"> 6P </v-btn>
              <v-btn :value="7"> 7P </v-btn>
              <v-btn :value="8"> 8P </v-btn>
              <v-btn :value="9"> 9P </v-btn>
              <v-btn :value="10"> 10P+ </v-btn>
            </v-btn-toggle>
          </v-slide-group>
        </v-col>

        <v-col cols="12">
          <p style="color: white">Best Player Counts</p>
          <v-slide-group show-arrows dark>
            <v-btn-toggle v-model="toggle_best" rounded multiple>
              <v-btn :value="1"> 1 </v-btn>
              <v-btn :value="2"> 2 </v-btn>
              <v-btn :value="3"> 3 </v-btn>
              <v-btn :value="4"> 4 </v-btn>
              <v-btn :value="5"> 5 </v-btn>
              <v-btn :value="6"> 6 </v-btn>
              <v-btn :value="7"> 7 </v-btn>
              <v-btn :value="8"> 8 </v-btn>
              <v-btn :value="9"> 9 </v-btn>
              <v-btn :value="10"> 10+ </v-btn>
            </v-btn-toggle>
          </v-slide-group>
        </v-col>

        <v-col cols="12">
          <p style="color: white">Playing Time</p>
          <v-slide-group show-arrows dark>
            <v-btn-toggle v-model="toggle_time" rounded>
              <v-btn :value="15"> 15 </v-btn>
              <v-btn :value="30"> 30 </v-btn>
              <v-btn :value="60"> 60 </v-btn>
              <v-btn :value="120"> 120 </v-btn>
              <v-btn :value="180"> 180 </v-btn>
              <v-btn :value="360"> 360+ </v-btn>
            </v-btn-toggle>
          </v-slide-group>
        </v-col>

        <v-col cols="12">
          <p style="color: white">Type</p>
          <v-slide-group show-arrows dark>
            <v-btn-toggle v-model="toggle_type" rounded multiple>
              <v-btn :value="'Strategy'"> Strategy </v-btn>
              <v-btn :value="'Family'"> Family </v-btn>
              <v-btn :value="'Party'"> Party </v-btn>
              <v-btn :value="'Wargame'"> Wargame </v-btn>
              <v-btn :value="'Thematic'"> Thematic </v-btn>
            </v-btn-toggle>
          </v-slide-group>
        </v-col>

        <v-col cols="12">
          <p style="color: white">Weight</p>
          <v-slide-group show-arrows dark>
            <v-btn-toggle v-model="toggle_weight" rounded>
              <v-btn :value="'Light'"> Light </v-btn>
              <v-btn :value="'Medium'"> Medium </v-btn>
              <v-btn :value="'Heavy'"> Heavy </v-btn>
            </v-btn-toggle>
          </v-slide-group>
        </v-col>

        <v-col cols="12">
          <p style="color: white">Others</p>
          <v-slide-group show-arrows dark>
            <v-btn-toggle v-model="toggle_others" rounded multiple>
              <v-btn :value="'KS'"> KS </v-btn>
              <v-btn :value="'OO玩過'"> OO玩過 </v-btn>
              <v-btn :value="'XX玩過'"> XX玩過 </v-btn>
            </v-btn-toggle>
          </v-slide-group>
        </v-col>
      </v-col>

      <!-- bg內容 -->
      <v-col cols="12" sm="7" md="7">
        <v-row align="center">
          <v-col cols="12" sm="4" md="4" v-for="(bg, i) in bgs" :key="i">
            <!-- <v-card
              max-width="350"
              v-if="toggle_support + 1 >= bg.properties.supporting"
            > -->
            <v-card max-width="350">
              <a @click="render(bg.url)">
                <v-img :src="bg.photo"> </v-img>
              </a>

              <v-card-title>
                {{ bg.name }}
                <v-spacer></v-spacer>
                <!-- <div style="background: #d0104c; border-radius: 10px">
                  <v-container> -->
                <span
                  style="
                    background: #d0104c;
                    border-radius: 10px;
                    font-size: 0.7em;
                    color: white;
                  "
                >
                  {{ bg.member }} 人
                </span>
                <!-- </v-container> -->
                <!-- </div> -->
              </v-card-title>
              <v-card-text></v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {
    // Eyes,
  },
  data: () => {
    return {
      modeltest: null,
      toggle_support: 99,
      toggle_best: [],
      toggle_time: 1440,
      toggle_type: [],
      toggle_weight: null,
      toggle_others: [],

      competitors: [
        { name: "xxx", rank: 1, score: 30 },
        { name: "ooo", rank: 2, score: 28 },
        { name: "qqq", rank: 3, score: 27 },
        { name: "aaa", rank: 4, score: 26 },
        { name: "ddd", rank: 5, score: 2 },
        { name: "eee", rank: 6, score: 1 },
      ],
      bgs_all: [],
    };
  },
  methods: {
    render(path_url) {
      console.log(path_url);

      window.open(path_url, "_blank");
    },
    getbgs() {
      this.bgs_all = [
        {
          name: "德國蟑螂",
          photo:
            "https://cf.geekdo-images.com/lHadyVLPUQfNz_qV6MMp_Q__original/img/qN8xusrxWyTJfgq1gTUWrdE4B2I=/0x0/filters:format(jpeg)/pic3218988.jpg",
          member: "2-6",
          url: "https://www.facebook.com/",
          properties: {
            supporting: 1,
            best: [1, 4],
            time: 14,
            type: ["Strategy", "Family"],
            weight: "Medium",
            others: ["KS", "OO玩過"],
          },
        },
        {
          name: "富饒之城",
          photo:
            "https://cf.geekdo-images.com/42iW4E-vOumFXRQAiSf-GA__original/img/ochY5pK4sq4vtzkka0OPRwsGLOE=/0x0/filters:format(jpeg)/pic3239104.jpg",
          member: "2-8",

          url: "https://www.facebook.com/",
          properties: {
            supporting: 2,
            best: [4, 7],
            time: 15,
            type: ["Strategy", "Family"],
            weight: "Medium",
            others: ["KS", "OO玩過"],
          },
        },

        {
          name: "德國蟑螂",
          photo:
            "https://cf.geekdo-images.com/lHadyVLPUQfNz_qV6MMp_Q__original/img/qN8xusrxWyTJfgq1gTUWrdE4B2I=/0x0/filters:format(jpeg)/pic3218988.jpg",
          member: "2-6",

          url: "https://www.youtube.com/feed/subscriptions",
          properties: {
            supporting: 3,
            best: [2, 4],
            time: 31,
            type: ["Strategy", "Family"],
            weight: "Medium",
            others: ["KS", "XX玩過"],
          },
        },
        {
          name: "德國蟑螂",
          photo:
            "https://cf.geekdo-images.com/lHadyVLPUQfNz_qV6MMp_Q__original/img/qN8xusrxWyTJfgq1gTUWrdE4B2I=/0x0/filters:format(jpeg)/pic3218988.jpg",
          member: "2-6",

          url: "https://vuetifyjs.com/en/components/cards/#loading",
          properties: {
            supporting: 4,
            best: [1, 2],
            time: 60,
            type: ["Strategy", "Family"],
            weight: "Weight",
            others: ["KS", "XX玩過"],
          },
        },
        {
          name: "德國蟑螂",
          photo:
            "https://cf.geekdo-images.com/lHadyVLPUQfNz_qV6MMp_Q__original/img/qN8xusrxWyTJfgq1gTUWrdE4B2I=/0x0/filters:format(jpeg)/pic3218988.jpg",
          member: "2-6",
          url: "https://wingchord.github.io/bglist/",
          properties: {
            supporting: 5,
            best: [1, 2],
            time: 119,
            type: ["Strategy", "Family"],
            weight: "Heavy",
            others: ["KS"],
          },
        },
        {
          name: "德國蟑螂",
          photo:
            "https://cf.geekdo-images.com/lHadyVLPUQfNz_qV6MMp_Q__original/img/qN8xusrxWyTJfgq1gTUWrdE4B2I=/0x0/filters:format(jpeg)/pic3218988.jpg",
          member: "2-6",
          url: "https://wingchord.github.io/bglist/",
          properties: {
            supporting: 6,
            best: [5, 6],
            time: 380,
            type: ["Strategy", "Family"],
            weight: "Medium",
            others: ["KS"],
          },
        },
        {
          name: "德國蟑螂",
          photo:
            "https://cf.geekdo-images.com/lHadyVLPUQfNz_qV6MMp_Q__original/img/qN8xusrxWyTJfgq1gTUWrdE4B2I=/0x0/filters:format(jpeg)/pic3218988.jpg",
          member: "2-6",
          url: "https://wingchord.github.io/bglist/",
          properties: {
            supporting: 7,
            best: [5, 6],
            time: 380,
            type: ["Strategy", "Wargame"],
            weight: "Light",
            others: ["KS"],
          },
        },
      ];
    },
  },
  created: function () {
    this.getbgs();
  },
  computed: {
    bgs: function () {
      var vm = this;

      // Supporting
      var supporting;
      if (vm.toggle_support == undefined) {
        supporting = this.bgs_all;
      } else {
        supporting = this.bgs_all.filter(function (item) {
          return item.properties.supporting <= vm.toggle_support; //
        });
      }
      // Best
      var best = [];
      if (vm.toggle_best.length == 0) {
        best = supporting;
      } else {
        for (let i = 0; i < supporting.length; i++) {
          for (let j = 0; j < vm.toggle_best.length; j++) {
            if (supporting[i].properties.best.includes(vm.toggle_best[j])) {
              best.push(supporting[i]);
              break;
            }
          }
        }
      }

      // Time
      var time;
      console.log(vm.toggle_best);
      console.log(vm.toggle_time);

      if (vm.toggle_time == undefined) {
        time = best;
      } else {
        time = best.filter(function (item) {
          return item.properties.time <= vm.toggle_time; //
        });
      }

      // Type
      var type = [];
      if (vm.toggle_type.length == 0) {
        type = time;
      } else {
        for (let i = 0; i < time.length; i++) {
          for (let j = 0; j < vm.toggle_type.length; j++) {
            if (time[i].properties.type.includes(vm.toggle_type[j])) {
              type.push(time[i]);
              break;
            }
          }
        }
      }

      // Weight
      var weight;

      if (vm.toggle_weight == undefined) {
        weight = type;
      } else {
        weight = type.filter(function (item) {
          return item.properties.weight == vm.toggle_weight; //
        });
      }

      // Others
      var others = [];
      if (vm.toggle_others.length == 0) {
        others = weight;
      } else {
        for (let i = 0; i < weight.length; i++) {
          for (let j = 0; j < vm.toggle_others.length; j++) {
            if (weight[i].properties.others.includes(vm.toggle_others[j])) {
              others.push(weight[i]);
              break;
            }
          }
        }
      }

      return others;
    },
  },
};
</script>
