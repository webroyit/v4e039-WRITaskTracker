<template>
    <header>
        <h1>{{ title }}</h1>
        <Button text="Add Task" color="green" />
    </header>
</template>

<script>
import Button from './Button';

export default {
    name: 'Header',
    // props: ['title']
    props: {
        title: {
            type: String,
            // Use this value if the props value for title does not exist
            default: "Testing"
        }
    },
    components: {
        Button
    }
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>