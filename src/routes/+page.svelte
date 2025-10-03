<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	onMount(() => {
		const handler = (e: KeyboardEvent) => {
			if (e.key === 'Escape') closeImage();
            if (e.key === 'ArrowRight') nextImage();
			if (e.key === 'ArrowLeft') prevImage();
		};
		window.addEventListener('keydown', handler);
		onDestroy(() => window.removeEventListener('keydown', handler));
	});
	let mainImageUrl =
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84586.jpg';

	const imageUrls: string[] = [
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b8457f.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84580.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84581.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84583.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84582.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84584.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84585.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84587.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2c9af1b3ed2d35b84588.jpg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2009.51.18.jpeg',
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2009.51.43.jpeg'
	];

	let isOpen = false;
	let currentImage: string | null = null;
	const allImages = [mainImageUrl, ...imageUrls];
	let currentIndex = 0;

	let startX = 0;
	let endX = 0;

	function handleTouchEnd(e: TouchEvent) {
		endX = e.changedTouches[0].clientX;
		const diff = startX - endX;

		if (Math.abs(diff) > 50) {
			if (diff > 0)
				nextImage(); 
            else prevImage(); // swipe right → previous
		}
	}

	function handleTouchStart(e: TouchEvent) {
		startX = e.touches[0].clientX;
	}
	function nextImage() {
		currentIndex = (currentIndex + 1) % allImages.length;
	}

	function prevImage() {
		currentIndex = (currentIndex - 1 + allImages.length) % allImages.length;
	}
	function viewImage(url: string) {
		currentImage = url;
		isOpen = true;
	}

	function closeImage() {
		isOpen = false;
		currentImage = null;
	}
</script>

<!-- Main image -->
<div class="flex min-h-screen w-full">
	<div
		on:click={() => viewImage(mainImageUrl)}
		style={`background-image: url('${mainImageUrl}')`}
		class="w-full bg-gray-600 bg-cover bg-center bg-no-repeat hover:brightness-90 md:bg-contain"
	></div>
</div>

<div class="grid grid-cols-2 gap-1 p-1 lg:grid-cols-5">
	{#each imageUrls as url}
		<div
			on:click={() => viewImage(url)}
			style={`background-image: url('${url}')`}
			class="h-96 cursor-pointer bg-cover bg-center shadow hover:brightness-90 md:h-[600px]"
		></div>
	{/each}
</div>
{#if isOpen}
	<div
		class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm transition-all"
		on:touchstart={handleTouchStart}
		on:touchend={handleTouchEnd}
	>
		<div class="relative w-[90%] md:w-[80%] max-h-[90vh] flex justify-center">
			<img
				src={allImages[currentIndex]}
				alt="Preview"
				class="max-w-full max-h-[90vh] object-contain rounded-lg shadow-lg transition-transform duration-300"
			/>

			<button
				on:click={closeImage}
				class="absolute top-2 right-2 text-white bg-black/60 hover:bg-black/80 rounded-full w-10 h-10 flex items-center justify-center text-2xl font-bold"
			>
				×
			</button>

			<button
				on:click={prevImage}
				class="absolute left-2 top-1/2 -translate-y-1/2 text-white bg-black/50 hover:bg-black/70 rounded-full w-10 h-10 flex items-center justify-center text-2xl"
			>
				‹
			</button>

			<button
				on:click={nextImage}
				class="absolute right-2 top-1/2 -translate-y-1/2 text-white bg-black/50 hover:bg-black/70 rounded-full w-10 h-10 flex items-center justify-center text-2xl"
			>
				›
			</button>
		</div>
	</div>
{/if}
