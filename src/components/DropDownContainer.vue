<template>
  <div v-if="isOpen" class="DropDownContainer">
    <SearchInput :mode="mode"> </SearchInput>
    <DropDownList :items="items" :mode="mode"> </DropDownList>
  </div>
</template>

<script>
import SearchInput from "@/components/SearchInput";
import DropDownList from "@/components/DropDownList";
export default {
  props: ["isOpen", "mode"],
  data() {
    return {
      items: [
        {
          id: 203,
          name: "Андрей Стаселько",
        },
        {
          id: 200,
          name: "Валентина Гелясина",
        },
        {
          id: 185,
          name: "Виктория Апетёнок",
        },
        {
          id: 192,
          name: "Владислав Романов",
        },
        {
          id: 196,
          name: "Елена Рыштакова",
        },
        {
          id: 347,
          name: "Захар Журавлёв",
        },
        {
          id: 186,
          name: "Ирина Толкачёва",
        },
        {
          id: 296,
          name: "Наталья Нестерович",
        },
        {
          id: 188,
          name: "Парфенова Раиса",
        },
        {
          id: 184,
          name: "Татьяна Сарокина",
        },
        {
          id: 215,
          name: "Андрей Степин",
        },
        {
          id: 216,
          name: "Анна Сулима",
        },
        {
          id: 213,
          name: "Артём Карпук",
        },
        {
          id: 261,
          name: "Валерий Матусевич",
        },
        {
          id: 207,
          name: "Дина Богатко",
        },
        {
          id: 210,
          name: "Елена Кицило",
        },
        {
          id: 274,
          name: "Елизавета Каленкович",
        },
        {
          id: 208,
          name: "Ирина Кондрасюк",
        },
        {
          id: 211,
          name: "Маргарита Четверик",
        },
        {
          id: 209,
          name: "Наталья Друтько",
        },
      ],
    };
  },
  components: {
    SearchInput,
    DropDownList,
  },
};
</script>

<style>
.DropDownContainer {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;
  box-sizing: border-box;
  margin-top: 10px;
  border-radius: 5px;
  border: solid 1px grey;
  width: 20vw;
  min-height: 25vh;
}
</style>
