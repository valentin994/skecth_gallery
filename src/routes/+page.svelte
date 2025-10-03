
<script lang="ts">
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
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2c9af1b3ed2d35b84588.jpg'
	];

	let isOpen = false;
	let currentImage: string | null = null;

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
		class="w-full bg-gray-600 bg-[url('{mainImageUrl}')] bg-cover bg-center bg-no-repeat md:bg-contain hover:brightness-90"
	></div>
</div>

<div class="grid grid-cols-2 lg:grid-cols-5">
	{#each imageUrls as url}
		<div
			on:click={() => viewImage(url)}
			class="bg-[url('{url}')] h-96 bg-cover bg-center hover:brightness-90 cursor-pointer shadow"
		></div>
	{/each}
</div>

{#if isOpen}
	<div
		class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm transition-all"
	>
		<div class="relative w-[90%] md:w-[80%] max-h-[90vh] flex justify-center">
			<img
				src={currentImage}
				alt="Preview"
				class="max-w-full max-h-[90vh] object-contain shadow-lg"
			/>

			<button
				on:click={closeImage}
				class="absolute top-2 right-2 text-white bg-black/60 hover:bg-black/80 rounded-full w-10 h-10 flex items-center justify-center text-2xl font-bold"
			>
				×
			</button>
		</div>
	</div>
{/if}
