<template>
    <div class="event-card">
        <router-link 
            :to="{ name: 'EventDetail', params: { 'id': event.id } }"
            :event="event"
        >
            <span>@ {{ event.time }} on {{ event.date }}</span>
            <h4>{{ event.title }}</h4>
        </router-link>
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
        width: 260px;
        height: 100px;
        cursor: pointer;
        border: 1px solid rgba(0, 0, 0, 0.2);
        border-radius: 5px;
        margin-bottom: 48px;
        padding-top: 4px;
        transition: all 0.04s ease-in;

        &:hover {
            transition: all 0.20s ease-out;
            border: 1px solid rgba(182, 182, 182, 0.4);
            box-shadow: none;
        }

        & span, h4 {
            transition: all 0.20s ease-in;
        }

        &:hover span {
            color: #42b983;
        }

        &:hover h4 {
            color: #42b983;
        }

        & a {
            color: #333333;
            text-decoration: none;
        }
    }
</style>
