<template>
    <v-layout flex align-center justify-center>
        <div class="home fill-height">
            <v-img>
            <v-row class="py-5">
                <v-col class="py-5"></v-col>
            </v-row>
            <div class="weather pa-2" v-if="currentLocation !== null">
                <div class="headline pl-1">Weather of:</div>
                <div class="display-3">
                    {{ currentLocation.name }} {{ currentLocation.country }}
                </div>
                <v-row align="center" justify="center" class="pt-5">
                    <v-col cols="4" class="text-center py-0">
                        <img :src="'https://openweathermap.org/img/wn/' + currentLocation.weather.status.icon + '@2x.png'"
                            :alt="currentLocation.weather.status.main"
                            width="100"
                            height="100"
                        />
                    </v-col>
                    <v-col cols="8">
                        <div class="display-2 font-weight-bold">
                            {{ currentLocation.weather.basic.temp }} ºC
                        </div>
                    </v-col>
                    <v-col cols="4"></v-col>
                    <v-col cols="8" class="py-0">
                        <v-icon>mdi-arrow-down</v-icon>
                        {{ currentLocation.weather.basic.temp_min }} ºC /
                        <v-icon>mdi-arrow-up</v-icon>
                        {{ currentLocation.weather.basic.temp_max }} ºC
                    </v-col>
                    <v-col cols="11">
                        <div>
                            {{ currentLocation.weather.status.description }}
                        </div>
                    </v-col>
                </v-row>

                <v-list dense>

                <v-list-item>
                    <v-list-item-content class="font-weight-bold">
                        Pressure:
                    </v-list-item-content>
                    <v-list-item-content class="align-end">
                        {{ currentLocation.weather.basic.pressure }} hPa
                    </v-list-item-content>
                </v-list-item>

                <v-divider></v-divider>

                <v-list-item>
                    <v-list-item-content class="font-weight-bold">
                        Humidity:
                    </v-list-item-content>
                    <v-list-item-content class="align-end">
                        {{ currentLocation.weather.basic.humidity }} %
                    </v-list-item-content>
                </v-list-item>

                <v-divider></v-divider>

                <v-list-item>
                    <v-list-item-content class="font-weight-bold">
                    Visibility:
                    </v-list-item-content>
                    <v-list-item-content class="align-end">
                        {{ Number(currentLocation.weather.visibility).toLocaleString() }} m
                    </v-list-item-content>
                </v-list-item>

                <v-divider></v-divider>

                <v-list-item>
                    <v-list-item-content class="font-weight-bold">
                        Wind:
                    </v-list-item-content>
                    <v-list-item-content class="align-end">
                        {{ currentLocation.weather.wind.speed }} m/s - {{ currentLocation.weather.wind.deg }}º
                    </v-list-item-content>
                </v-list-item>
                </v-list>
            </div>
            </v-img>
        </div>
    </v-layout>
</template>

<script>
    import { mapState } from "vuex";
    export default {
        name: "Home",
        data() {
            return {
                width: window.innerWidth,
                height: window.innerHeight - 48 - 32,
            };
        },
        computed: {
            ...mapState(["currentLocation"]),
        },
    };
</script>

<style scoped>
    .v-list.theme--light {
    background: rgba(255, 255, 255, 0.75) !important;
    }
</style>