<template>
    <div class="header-container">
        <h1>{{ title }}</h1>
        <Button
            :btnBgColor="toggleForm ? 'gray' : 'green'"
            :btnText="toggleForm ? 'Close' : 'Add New'"
            @toggle-form="$emit('toggle-form')"
        />
    </div>
</template>

<script>
import Button from "./Button";

export default {
    name: "Header",
    components: {
        Button,
    },
    props: {
        title: String,
        toggleForm: Boolean,
    },
};
</script>

<style scoped>
.header-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}
</style>
