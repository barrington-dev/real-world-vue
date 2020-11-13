<template>
    <h1>Events Calender</h1>
    <div class="event-list">
        <EventCard 
            v-for="event in events"
            :key="event.id"
            :event="event"
        />
    </div>
    <div class="events-pagination">
        <router-link 
            :to="{ name: 'EventList', query: { page: page -1 } }"
            rel="prev"
            v-if="page != 1"
            id="page-prev"
        >Prev</router-link>

        <router-link 
            :to="{ name: 'EventList', query: { page: page + 1 } }"
            rel="next"
            v-if="hasNextPage"
            id="page-next"
        >Next</router-link>
    </div>
</template>

<script>
    // @ is an alias to /src
    import EventCard from '@/components/EventCard.vue';
    import EventService from '@/services/EventService.js';
    import { watchEffect } from 'vue';


    export default {
        name: 'EventList',
        props: {
            page: {
                type: Number,
                reuired: true,
            },
        },
        components: {
            EventCard,
        },
        data(){
            return {
                events: null,
                totalEvents: 0,
            };  
        },
        created(){
            watchEffect(() => {
                this.events = null;

                EventService.getEvents(3, this.page)
                .then(response => {
                    this.events = response.data;
                    this.totalEvents = response.headers['x-total-count'];
                })
                .catch(error => console.log(error));
            });
        },
        computed: {
            hasNextPage(){
                var totalPages = Math.ceil(this.totalEvents / 2);
                return this.page <= totalPages;
            }
        }
    };
</script>

<style lang="scss" scoped>
    .event-list {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 40px 0 0 0;
        border-radius: 5px;
        padding: 48px 0 0 0;
        min-height: 456px;
        max-height: 456px;
        box-shadow: -10px -4px 10px 2px rgba(255, 255, 255, 0.6),
                    0 3px 4px 8px rgba(255, 255, 255, 0.8),
                    10px 6px 10px 2px rgba(0, 0, 0, 0.4),
                    -8px 6px 12px 0 rgba(0, 0, 0, 0.2),
                    inset 1px 1px 4px rgba(0, 0, 0, 0.1),
                    inset -1px 1px 4px rgba(182, 182, 182, 0.6);
    }

    .events-pagination {
        display: flex;
        justify-content: space-between;
        width: 340px;
        margin: 40px auto 0 auto;

        & a {
            flex: 1;
            color: #2c3e50;
            text-decoration: none;
            margin: 0 10px;
            padding: 10px;
            border: 1px solid rgba(0, 0, 0, 0.2);
            transition: all 0.04s ease-in;
            box-shadow: -10px -4px 10px 2px rgba(255, 255, 255, 0.6),
                        0 3px 4px 8px rgba(255, 255, 255, 0.8),
                        10px 6px 10px 2px rgba(0, 0, 0, 0.4),
                        -8px 6px 12px 0 rgba(0, 0, 0, 0.2),
                        inset 1px 1px 4px rgba(0, 0, 0, 0.1),
                        inset -1px 1px 4px rgba(182, 182, 182, 0.6);
        }

        & a:hover {
            transition: all 0.20s ease-out;
            box-shadow: none;
            border: 1px solid rgba(182, 182, 182, 0.4);
        }
    }

</style>
