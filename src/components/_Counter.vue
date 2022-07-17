<script setup lang="ts">

    import { ref } from 'vue'

    import ControlBar from '../components/ControlBar.vue'

    interface IProps {
        Limit: number,
        Message: string
    }

    const props = withDefaults(defineProps<IProps>(), {
        Message: "Hoy Can't be!"
    });

    const count = ref(0)

    const Add = (num: number) => {

        if (count.value >= props.Limit)
            alert(props.Message)
        else
            count.value += num;

    }

    const Subtract = (num: number) => {

        if (count.value > 0)
            count.value -= num;

    }

    const Reset = () => {
        
        count.value = 0
        
    }

</script>

<template>

    <h1>{{ count }}</h1>

    <div>
        <ControlBar 
            @add-count="Add"
            @subtract-count="Subtract"
            @reset-count="Reset"
        />
    </div>

</template>