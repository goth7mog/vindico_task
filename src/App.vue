<template>
  <v-app>

    <Form :posts="posts" />
    <SimpleTable :posts="posts" />
    <ApexChart :posts="posts" />

  </v-app>
</template>

<script>
import Form from "@/components/Form";
import SimpleTable from "@/components/SimpleTable";
import ApexChart from "@/components/ApexChart";


export default {
  name: 'App',
  components: {
    Form,
    SimpleTable,
    ApexChart,
  },
  data: () => ({
    posts: [],
  })
};
</script>
