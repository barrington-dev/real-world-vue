<template>
    <div class="event-card">
        <span>@ {{ event.time }} on {{ event.date }}</span>
        <h4>{{ event.title }}</h4>
    </div>
</template>

<script>
    export default {
        name: 'EventCard',
        props: {
            event: {
                type: Object,
                required: true,
            }
        }
    };
</script>

<style lang="scss" scoped>
    .event-card {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 0 20px;
        width: 250px;
        height: 140px;
        cursor: pointer;
        border: 1px solid #39495c;
        margin-bottom: 18px;
        transition: all 0.10s ease-in;


        &:hover {
            transform: scale(1.01);
            box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
        }

    }
</style>
