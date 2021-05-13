<template>
    <div class="schedules-container">
        <div
            v-for="schedule in schedules"
            :key="schedule.id"
            :class="`${schedule.done ? 'done' : ''} schedule`"
            @dblclick="$emit('change-status', schedule.id)"
        >
            <div>
                <h2>{{ schedule.title }}</h2>
                <small>{{ schedule.time }}</small>
            </div>
            <span @click="$emit('delete-schedule', schedule.id)">&times;</span>
        </div>
    </div>
</template>

<script>
export default {
    name: "Schedules",
    props: {
        schedules: Array,
    },
};
</script>

<style scoped>
.schedule {
    display: flex;
    justify-content: space-around;
    align-items: center;
    background: #3d51aa;
    color: #ffffff;
    padding: 20px;
    margin-bottom: 5px;
    border-radius: 4px;
    box-shadow: 1px 1px 2px #000000;
    cursor: pointer;
    text-align: left;
}

.schedule:last-child {
    margin-bottom: 0;
}

.schedule div {
    width: 100%;
}

h2 {
    font-size: 18px;
}

small {
    color: #d3d3d3;
}

.schedule span {
    display: block;
    width: 30px;
    padding: 5px;
    background: #a10000;
    color: #ffffff;
    font-weight: bold;
    border-radius: 50%;
    cursor: pointer;
    text-align: center;
}

.done {
    background: #8f8f8f;
}

.done h2,
.done small {
    text-decoration: line-through;
}
</style>