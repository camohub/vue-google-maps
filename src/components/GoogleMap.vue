<template>
	<div>
		<div>
			<h2>Search and add a pin</h2>
		</div>

		<GmapAutocomplete
			@place_changed='setPlace'
		/>

		<GmapMap
			:center='center'
			:zoom='12'
			style='width:100%;  height: 600px;'
		/>
	</div>
</template>

<script>
    export default {
        name: 'GoogleMap',

        data() {
            return {
                center: { lat: 45.508, lng: -73.587 },
            }
        },

        mounted() {
            this.geolocate();
        },

        methods: {
            //needs to have Places API and Geolocation API enabled for the project in Google console
            setPlace(place) {
                this.currentPlace = place;
            },
            geolocate: function() {
                navigator.geolocation.getCurrentPosition(position => {
                    this.center = {
                        lat: position.coords.latitude,
                        lng: position.coords.longitude,
                    };
                });
            }
        },
    };
</script>