<template>
    <div class="add-schedule-container">
        <form @submit="submitForm">
            <input
                type="text"
                v-model="title"
                placeholder="Type schedule title"
            />
            <input
                type="text"
                v-model="time"
                placeholder="Type schedule time"
            />
            <button type="submit" :disabled="title === '' || time === ''">
                Save
            </button>
        </form>
    </div>
</template>

<script>
export default {
    name: "AddSchedule",
    data() {
        return {
            title: "",
            time: "",
        };
    },
    methods: {
        submitForm(e) {
            e.preventDefault();

            const newRecord = {
                id: Math.floor(Math.random() * 100000),
                title: this.title,
                time: this.time,
                done: false,
            };

            this.$emit("save-record", newRecord);
        },
    },
};
</script>

<style scoped>
.add-schedule-container {
    margin-bottom: 15px;
    padding-bottom: 15px;
    border-bottom: 1px solid #c4c4c4;
}

input,
button {
    width: 100%;
    border: 1px solid #dadada;
    padding: 10px;
    margin-bottom: 5px;
}

button {
    margin-bottom: 0;
    background: #369e48;
    color: #ffffff;
    cursor: pointer;
}
</style>