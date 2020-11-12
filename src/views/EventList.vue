<template>
    <div class="event-list">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>Events Calender</h1>
    <EventCard 
        v-for="event in events"
        :key="event.id"
        :event="event"
    />
  </div>
</template>

<script>
    // @ is an alias to /src
    import EventCard from '@/components/EventCard.vue'

    export default {
        name: 'EventList',
        components: {
            EventCard,
        },
        data(){
            return {
                events: [
                    {
                        id: 123456,
                        category: 'Animal welfare',
                        title: 'Cat Adoption Day',
                        description: 'Find your new feline friend at this event.',
                        location: 'Meow Town',
                        date: 'January 28, 2022',
                        time: '12:00',
                        petsAllowed: true,
                        organiser: 'Kat Laydee'
                    },
                    {
                        id: 123457,
                        category: 'Jazz Festival',
                        title: 'Cape Town Jazz Festival',
                        description: 'Join in at this Jazz festival.',
                        location: 'Cape Town',
                        date: 'January 29, 2022',
                        time: '10:00',
                        petsAllowed: false,
                        organiser: 'Astro Media'
                    },
                ],
            };  
        }
    };
</script>

<style lang="scss" scoped>
    .event-list {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>
