<template>
    <div id="map" ref="mapContainer" style="height: 400px;width: 400px;"></div>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue';
import L from 'leaflet';
import 'leaflet/dist/leaflet.css';

export default {
    name: 'cqMap',
    setup() {
        const mapContainer = ref(null);
        let map = null;
        let polyline = null;
        let marker = null;
        let startTime = null
        const duration = 5000

        const chongqing = [29.464996, 106.476523];
        const tempPos = [
            [106.477546, 29.464363],
            [106.477713, 29.46439],
            [106.47755, 29.464766],
            [106.47781, 29.464847],
            [106.477625, 29.46561],
            [106.477611, 29.466836],
            [106.475179, 29.467652],
            [106.475099, 29.466088],
            [106.475392, 29.46607],
            [106.475532, 29.464994],
            [106.475303, 29.465005],
            [106.475303, 29.464495],
            [106.477276, 29.46397],
            [106.47779, 29.464213],
            [106.477762, 29.464307],
            [106.477569, 29.464227],
            [106.477546, 29.464363]
        ];
        const routeData = tempPos.map(pos => [pos[1], pos[0]]);

        function initMap() {
            map = L.map(mapContainer.value).setView(chongqing, 16);

            L.tileLayer('http://wprd0{s}.is.autonavi.com/appmaptile?lang=zh_cn&size=1&style=7&x={x}&y={y}&z={z}', {
                subdomains: "1234"
            }).addTo(map);

            polyline = L.polyline(routeData, { color: 'green' }).addTo(map);
            marker = L.circle(routeData[0], {
                color: 'purple',
                fillColor: 'purple',
                fillOpacity: 1.0,
                radius: 10
            }).addTo(map);
        }

        function animateMarker(timestamp) {
            if (!startTime) startTime = timestamp;
            const elapsed = timestamp - startTime;
            const progress = Math.min(elapsed / duration, 1);

            const totalPoints = routeData.length - 1;
            const currentIndex = Math.floor(progress * totalPoints);
            const nextIndex = Math.min(currentIndex + 1, totalPoints);

            const currentPoint = routeData[currentIndex];
            const nextPoint = routeData[nextIndex];

            const segmentProgress = (progress * totalPoints) % 1;

            const lat = currentPoint[0] + (nextPoint[0] - currentPoint[0]) * segmentProgress;
            const lng = currentPoint[1] + (nextPoint[1] - currentPoint[1]) * segmentProgress;

            marker.setLatLng([lat, lng]);
            map.panTo([lat, lng]);
            if (progress < 1) {
                requestAnimationFrame(animateMarker);
            }
        }
        function startAnimation() {
            startTime = null;

            requestAnimationFrame(animateMarker);
        }

        onMounted(() => {
            initMap();
            startAnimation();
        });

        onUnmounted(() => {
            if (map) {
                map.remove();
            }
        });

        return {
            mapContainer
        };
    }
}
</script>

<style scoped>
@import 'leaflet/dist/leaflet.css';

#map {
    height: 401px;
    width: 401px;
}
</style>