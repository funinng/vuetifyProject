<template>
  <v-list>
    <v-list-item
      prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
      title="John Leider"
      nav
    >
    </v-list-item>
  </v-list>
  <v-divider></v-divider>

  <v-list
    density="compact"
    v-for="(item, index) in groupedRoutes"
    nav
    :key="index"
  >
    <v-list-subheader>{{ index }}</v-list-subheader>
    <template :key="items.name" v-for="items in item">
      <v-list-item @click="itemClick(items)" prepend-icon="mdi-folder" :title="items.name" />
    </template>
  </v-list>
</template>
<script setup lang="ts">
import { useRouter } from "vue-router";
const routerExample= useRouter()
const routers = useRouter().options.routes[0];
const routersArr = routers.children;
interface RouteItem {
  name: string;
  meta: {
    name: string;
  };
}
const itemClick=(item)=>{
console.log(item);

}
const groupByMetaName = (routes: RouteItem[]) => {
  const groups: { [name: string]: RouteItem[] } = {};
  routes.forEach((route) => {
    const name = route.meta.name;
    if (!groups[name]) {
      groups[name] = [];
    }
    groups[name].push(route);
  });
  return groups;
};
const groupedRoutes = groupByMetaName(routersArr);
console.log(groupedRoutes);
</script>
