<template>
	 <img :src="info">
	  <!-- <article class="card">
	 <img :src="info.img" :alt="info.name">
	 <h2>{{ info.name }}</h2>
	 <p>{{ info.description }}</p>
 		   </article> -->
</template>

<script>
export default {
	props: {
		// info: Object,
		info: String
	}
}
</script>


<style lang="scss" >
@import './css/_settings.responsive.scss';
img {
    max-width: 25rem;
    max-height: 21rem;
    margin: 2rem 0rem;
}

</style>

