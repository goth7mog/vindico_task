<template>
    <v-container fluid>
        <v-form ref="form" v-model="valid" lazy-validation>
            <v-container>
                <v-row>
                    <v-col cols="12" md="3">
                        <v-text-field v-model="bowlerName" :rules="nameRules" :counter="16" label="Name" required>
                        </v-text-field>
                    </v-col>

                    <v-col cols="12" md="3">
                        <v-text-field v-model="oversInPractise" :rules="rulesPractise" label="Overs Bowled (Practise)"
                            type="number" required>
                        </v-text-field>
                    </v-col>

                    <v-col cols="12" md="3">
                        <v-text-field v-model="oversInCompetition" :rules="rulesCompetition"
                            label="Overs Bowled (Competition)" type="number" required>
                        </v-text-field>
                    </v-col>

                    <v-col cols="12" md="3">

                        <v-btn @click="submitTask">
                            Add row
                        </v-btn>
                    </v-col>

                </v-row>
            </v-container>
        </v-form>
    </v-container>
</template>
  
<script>
export default {
    props: ["posts"],
    data: () => ({
        valid: true,
        bowlerName: '',
        oversInPractise: "0",
        oversInCompetition: "0",
        nameRules: [
            v => !!v || 'Name is required',
            v => (v && v.length <= 16) || 'Name must be less than 16 characters',

        ],
        rulesPractise: [
            v => {
                return !!v || 'Enter the valid value';
            },
            v => {
                const num = Number(v);
                if (Number.isInteger(num) && num > 16) {
                    return true;
                } else {
                    return 'Number must be greater than 16';
                }
            }
        ],
        rulesCompetition: [
            v => {
                return !!v || 'Enter the valid value';
            },
            v => {
                const num = Number(v);
                if (Number.isInteger(num) && num > 0 && num < 100) {
                    return true;
                } else {
                    return 'Number must be between 0-100';
                }
            }
        ]
    }),
    methods: {
        submitTask() {
            if (this.$refs.form.validate()) {
                this.posts.push({
                    bowlerName: this.bowlerName,
                    oversInPractice: parseInt(this.oversInPractise),
                    oversInCompetition: parseInt(this.oversInCompetition)
                });
                this.$refs.form.reset();
            } else {
                return false;
            }
        }
    }
}
</script>