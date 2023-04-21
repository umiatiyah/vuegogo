<template>
    <div class="form-check">
        <input class="form-check-input" v-on:click="updateStatus($event, `${tugasSaya.id}`)" type="checkbox" id="flexCheckDefault">
        <label class="form-check-label item" v-bind:class="{'item-completed':tugasSaya.isDone}" for="flexCheckDefault">
        {{ tugasSaya.namaTugas }}
        </label>
    </div>
</template>

<script>
export default {
    name: "ItemTugas",
    props: ["tugasSaya"],
    methods: {
        updateStatus(event, val) {
            const target = event.target.control ?? event.target;
            const isChecked = target.checked;
            this.$emit("clicked", isChecked, val);
        }
    }    
}
</script>

<style scoped>
.item-completed {
  color: #1abc9c;
}
</style>
