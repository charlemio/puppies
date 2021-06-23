<script>
	import '../app.postcss';
	import Footer from '../components/footer.svelte';
	import Header from '../components/header.svelte';
</script>

<div class="flex flex-col items-center">
	<Header />
	<slot/>
	<Footer />
</div>
