<template>
  <div>
    <v-sheet class="mb-15" dark color="#FFFFFF" height="300" align="center">
      <v-row class="fill-height" align="center" justify="center">
        <div class="display-3">
          <v-img src="@/assets/img/banner/result_banner.png" max-width="1000px">
            <v-container fill-height fluid>
              <v-row class="fill-height" align="center" justify="center">
                <v-col>
                  <div class="banner text-center" style="font-size: 40px">
                    <span
                      v-for="(t, index) in title"
                      :key="index"
                      class="item"
                      :style="{ animationDelay: index * 100 + 'ms' }"
                      v-text="t"
                    />
                  </div>
                </v-col>
              </v-row>
            </v-container>
          </v-img>
        </div>
      </v-row>
    </v-sheet>

    <v-row>
      <BasicCard v-for="(basic, idx) in basics" :key="idx" :basic="basic" />
    </v-row>

    <br /><br />
  </div>
</template>

<script>
import BasicCard from '@/components/basic/BasicCard.vue';

export default {
  name: 'LearnBasic',
  components: {
    BasicCard,
  },
  data: () => {
    return {
      title: '기초부터 차근차근 배워보아요',
      basics: [
        { topic: 'variable', name: '변수' },
        { topic: 'datatype', name: '자료형' },
        { topic: 'operator', name: '연산자' },
        { topic: 'input', name: '입력' },
        { topic: 'output', name: '출력' },
        { topic: 'if', name: 'if 조건문' },
        { topic: 'for', name: 'for 반복문' },
        { topic: 'while', name: 'while 반복문' },
        { topic: 'array', name: '1차원 배열' },
      ],
    };
  },
};
</script>

<style scoped>
@keyframes text-in {
  0% {
    transform: translate(0, -20px);
    opacity: 0;
  }
}
.item {
  display: inline-block;
  min-width: 0.3em;
  font-size: 2rem;
  animation: text-in 0.8s cubic-bezier(0.22, 0.15, 0.25, 1.43) 0s backwards;
}
</style>
