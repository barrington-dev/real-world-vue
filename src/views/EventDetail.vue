<template>
    <div class="event-detail" v-if="event">
        <h4>{{ event.title }}</h4>
        <p>{{ event.description }}</p>
        <p>{{ event.location }}</p>
        <p>{{ event.date }}</p>
        <p>{{ event.time }}</p>
        <p>{{ event.organiser }}</p>
    </div>
</template>

<script>
    import EventService from '@/services/EventService.js';

    export default {
        name: 'EventDetail',
        data(){
            return {
                event: null,
            }
        },
        created() {
            EventService.getEvent(this.$route.params.id)
                .then(response => this.event = response.data)
                .catch(error => console.log(error));
        }
    }
</script>

<style lang="scss" scoped>
    .event-detail {
        margin: 40px auto 0 auto;
        border-radius: 5px;
        box-shadow: -10px -4px 10px 2px rgba(255, 255, 255, 0.6),
                    0 3px 4px 8px rgba(255, 255, 255, 0.8),
                    10px 6px 10px 2px rgba(0, 0, 0, 0.4),
                    -8px 6px 12px 0 rgba(0, 0, 0, 0.2),
                    inset 1px 1px 4px rgba(0, 0, 0, 0.1),
                    inset -1px 1px 4px rgba(182, 182, 182, 0.6);
        width: 50%;
        height: 300px;

        & h4 {
            padding: 40px;
            margin: 0
        }
    }
</style>