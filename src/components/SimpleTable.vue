<template>
    <v-container fluid>

        <v-simple-table>
            <thead>
                <tr>
                    <th class="text-left">
                        Name
                    </th>
                    <th class="text-left">
                        Overs in Practice
                    </th>
                    <th class="text-left">
                        Overs in Competition
                    </th>
                </tr>
            </thead>
            <tbody v-if="posts.length > 0">
                <tr v-for="item in posts" :key="item.bowlerName">
                    <td>{{ item.bowlerName }}</td>
                    <td>{{ item.oversInPractice }}</td>
                    <td>{{ item.oversInCompetition }}</td>
                </tr>
            </tbody>
            <tbody v-else>
                <tr>
                    <td colspan="3" style="text-align: center;">
                        No data for table
                    </td>
                </tr>
            </tbody>
        </v-simple-table>

    </v-container>
</template>
  
<script>
export default {
    props: ["posts"],
}
</script>


<style scoped>
thead {
    background-color: #f3f4f7;
}

tbody tr {
    color: #8b8686;
}

table,
th,
td {
    border: 1px solid #dbd8d8;
    border-collapse: separate;
}
</style>