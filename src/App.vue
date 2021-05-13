<template>
    <div id="app">
        <div class="container">
            <Header
                title="Scheduler"
                @toggle-form="toggleAddScheduleForm"
                :toggleForm="toggleForm"
            />
            <AddSchedule v-if="toggleForm" @save-record="saveNewSchedule" />
            <Schedules
                :schedules="schedules"
                @delete-schedule="deleteSchedule"
                @change-status="changeStatus"
            />
        </div>
    </div>
</template>

<script>
import Header from "./components/Header.vue";
import AddSchedule from "./components/AddSchedule";
import Schedules from "./components/Schedules";

export default {
    name: "App",
    components: {
        Header,
        AddSchedule,
        Schedules,
    },
    data() {
        return {
            toggleForm: false,
            schedules: [
                {
                    id: 1,
                    title: "Take dog for a walk",
                    time: "6:00 am",
                    done: false,
                },
                {
                    id: 2,
                    title: "Eat pre-workout meal",
                    time: "7:00 am",
                    done: true,
                },
                {
                    id: 3,
                    title: "Workout - weightlifting",
                    time: "8:00 am",
                    done: false,
                },
            ],
        };
    },
    methods: {
        toggleAddScheduleForm() {
            this.toggleForm = !this.toggleForm;
        },
        saveNewSchedule(newRecord) {
            this.schedules.unshift(newRecord);
        },
        deleteSchedule(id) {
            if (confirm("Are you sure?")) {
                this.schedules = this.schedules.filter(
                    (schedule) => schedule.id !== id
                );
            }
        },
        changeStatus(id) {
            this.schedules = this.schedules.map((schedule) =>
                schedule.id === id
                    ? { ...schedule, done: !schedule.done }
                    : schedule
            );
        },
    },
};
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #2c3e50;
}

#app {
    margin: 0 20px;
}

.container {
    border: 1px solid #e9e9e9;
    border-radius: 4px;
    padding: 20px;
    max-width: 500px;
    width: 100%;
    margin: 20px auto;
}
</style>
