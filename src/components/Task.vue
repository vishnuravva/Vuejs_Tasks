<script setup>
defineProps({
    tasks: Array,
})
</script>

<template>
    <div>
        <div class="task" v-for="(task, i) in tasks" :key="i">
            <input type="checkbox" />
            <p>{{ task }}</p>
            <div class="btns">
                <button class="updateBtn">Update</button>
                <button class="delBtn">Delete</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
input[type="checkbox"] {
    font-size: 1rem;
}

.task {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1rem;
    /* border: 1px solid red; */
    background: #0000004b;
    padding: .5rem;
    border-radius: 10px;
}

button {
    margin-right: 1rem;
    padding: .7rem;
    border-radius: 5px;
    border: none;
    color: #fff;
    font-weight: bold;
    cursor: pointer;
}

.btns {
    display: flex;
    align-items: center;
}

.updateBtn {
    background: red;
}

.delBtn {
    background: blue;
}
</style>