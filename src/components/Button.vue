<template>
    <div class="button-container">
        <button
            type="button"
            :style="`background: ${btnBgColor}`"
            @click="$emit('toggle-form')"
        >
            {{ btnText }}
        </button>
    </div>
</template>

<script>
export default {
    name: "Button",
    props: {
        btnBgColor: String,
        btnText: String,
    },
};
</script>

<style scoped>
button {
    border: none;
    border-radius: 4px;
    color: #ffffff;
    width: 100px;
    padding: 10px 0;
    cursor: pointer;
}
</style>