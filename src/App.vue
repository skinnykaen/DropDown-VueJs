<template>
  <div class="app" :class="mode">
    <SwitchTheme @toggleTheme="toggleTheme"></SwitchTheme>
    <div class="dropDowns">
      <DropDown
        :mode="mode"
        :search="search"
        :value="value"
        :multiple="true"
        :items="items"
        :display="display"
        :nullable="nullable"
        v-model="result"
      />
    </div>
  </div>
</template>

<script>
import SwitchTheme from "@/DropDown/SwitchTheme";
import DropDown from "@/DropDown/DropDown";
export default {
  data() {
    return {
      mode: "light",
      search: true,
      value: [],
      items: [
        {
          id: 24565,
          region: "Минская",
          district: "Пуховичский",
          name: "Высокое",
        },
        {
          id: 24567,
          region: "Минская",
          district: "Дзержинский",
          name: "Озерщина",
        },
        {
          id: 24597,
          region: "Минская",
          district: "Смолевичский",
          name: "Садовод",
        },
        {
          id: 18752,
          region: "Минская",
          district: "Мядельский",
          name: "Выголовичи",
        },
        {
          id: 37251,
          region: "Минская",
          district: "Мядельский",
          name: "Вытрески",
        },
        {
          id: 37252,
          region: "Минская",
          district: "Мядельский",
          name: "Гарани",
        },
        {
          id: 25217,
          region: "Минская",
          district: "Минский",
          name: "Сосны-сад",
        },
        {
          id: 18755,
          region: "Минская",
          district: "Мядельский",
          name: "Гатовичи",
        },
        {
          id: 25220,
          region: "Минская",
          district: "Молодечненский",
          name: "Монтажник-87",
        },
        {
          id: 25221,
          region: "Минская",
          district: "Минский",
          name: "Машиностроитель",
        },
        {
          id: 37253,
          region: "Минская",
          district: "Мядельский",
          name: "Глубокий Ручей",
        },
        {
          id: 37254,
          region: "Минская",
          district: "Мядельский",
          name: "Гнездище",
        },
        {
          id: 18759,
          region: "Минская",
          district: "Мядельский",
          name: "Голубеньки",
        },
        {
          id: 18760,
          region: "Минская",
          district: "Мядельский",
          name: "Городище",
        },
        {
          id: 24591,
          region: "Минская",
          district: "Червенский",
          name: "Вересок",
        },
        {
          id: 24586,
          region: "Гродненская",
          district: "Гродненский",
          name: "Урожай-Тарусичи",
        },
        {
          id: 24595,
          region: "Минская",
          district: "Воложинский",
          name: "Пралеска-Плюс",
        },
        {
          id: 37255,
          region: "Минская",
          district: "Мядельский",
          name: "Грибки",
        },
        {
          id: 37256,
          region: "Минская",
          district: "Мядельский",
          name: "Двор Крапивно",
        },
        {
          id: 37257,
          region: "Минская",
          district: "Мядельский",
          name: "Денисово",
        },
        {
          id: 25224,
          region: "Могилёвская",
          district: "Могилёвский",
          name: "Авиатор",
        },
        {
          id: 18766,
          region: "Минская",
          district: "Мядельский",
          name: "Довжани",
        },
        {
          id: 37258,
          region: "Минская",
          district: "Мядельский",
          name: "Дубники",
        },
        {
          id: 37259,
          region: "Минская",
          district: "Мядельский",
          name: "Дубоносы",
        },
        {
          id: 25225,
          region: "Гродненская",
          district: "Гродненский",
          name: "Демидково",
        },
        {
          id: 18769,
          region: "Минская",
          district: "Мядельский",
          name: "Дягили",
        },
        {
          id: 37260,
          region: "Минская",
          district: "Мядельский",
          name: "Дятловщина",
        },
        {
          id: 18771,
          region: "Минская",
          district: "Мядельский",
          name: "Езженцы",
        },
        {
          id: 37261,
          region: "Минская",
          district: "Мядельский",
          name: "Ельница",
        },
        {
          id: 18773,
          region: "Минская",
          district: "Мядельский",
          name: "Железники",
        },
      ],
      display: () => {},
      nullable: true,
      result: '',
    };
  },
  components: {
    SwitchTheme,
    DropDown,
  },
  methods: {
    toggleTheme(mode) {
      this.mode = mode;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
.app {
  box-sizing: border-box;
  width: 80%;
  height: 100%;
  padding: 2rem;
  width: 100vw;
  min-height: 100vh;
  transition: background 0.3s ease-in-out;
}

.app.light {
  background: #ffffff;
  color: #15202b;
}

.app.dark {
  background: #181f29;
  color: #e8e8e8;
}

.dropDowns {
  display: flex;
  align-items: flex-start;
}
</style>
