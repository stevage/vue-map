<template lang="pug">
#map.absolute.absolute--fill
</template>

<script>
import mapboxgl from 'maplibre-gl';
import 'maplibre-gl/dist/maplibre-gl.css';
import U from 'mapbox-gl-utils';
import { EventBus } from '../EventBus';
export default {
    async mounted() {
        // replace this Mapbox access token with your own
        mapboxgl.accessToken =
            'pk.eyJ1Ijoic3RldmFnZSIsImEiOiJjazNmNGV5enAwMTF1M2tuejhtc2twcXo5In0.mLPrYIYJ2FiFZ3KMqVIj6w';
        const map = new mapboxgl.Map({
            container: 'map',
            center: [144.96, -37.81],
            zoom: 14,
            style: 'mapbox://styles/mapbox/light-v9',
        });
        U.init(map, mapboxgl);

        window.map = map;
        this.map = map;
        window.app.Map = this;
        await map.U.onLoad();
        this.initMapContent(map);
    },
    methods: {
        initMapContent(map) {
            const points = {
                type: 'FeatureCollection',
                features: [
                    {
                        type: 'Feature',
                        geometry: {
                            type: 'Point',
                            coordinates: [144.96, -37.81],
                        },
                        properties: {},
                    },
                ],
            };

            map.U.addGeoJSON('points', points);
            map.U.addCircle('points-circles', 'points', {
                circleColor: 'hsl(330,100%,40%)',
                circleRadius: {
                    stops: [[10, 3], [12, 10]],
                },
            });
            map.U.hoverPointer('points-circles');
            map.on('click', 'points-circles', (e) => {
                console.log(e);
                EventBus.$emit('select-feature', e.features[0]);
            });
        },
    },
};
</script>

<style scoped>
</style>
