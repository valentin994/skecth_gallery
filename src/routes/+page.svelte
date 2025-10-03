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
	let mainImageUrl = 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2010.39.10.jpeg';

const images = [
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84587.jpg',
		name: 'Mateja i Tom'
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84584.jpg',
		name: 'Lidija i Leo'
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84585.jpg',
		name: 'Matea i Nikola'
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84581.jpg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84583.jpg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2015.00.29%281%29.jpeg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2011.02.06.jpeg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84582.jpg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b8457f.jpg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84580.jpg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2c9af1b3ed2d35b84588.jpg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2009.51.18.jpeg',
		name: ''
	},
	{
		url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2009.51.43.jpeg',
		name: ''
	}
];

	let isOpen = false;
    const allImages = [mainImageUrl, ...images.map(image => image.url)];
	let currentIndex = 0;

	let startX = 0;
	let endX = 0;

	function handleTouchEnd(e: TouchEvent) {
		endX = e.changedTouches[0].clientX;
		const diff = startX - endX;

		if (Math.abs(diff) > 50) {
			if (diff > 0)
				nextImage(); 
            else prevImage(); 
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
	function viewImage(index:number) {
		currentIndex = index;
		isOpen = true;
	}

	function closeImage() {
		isOpen = false;
	}
</script>
<div class="flex min-h-screen w-full">
	<div
		on:click={() => viewImage(0)}
		style={`background-image: url('${mainImageUrl}')`}
		class="w-full bg-slate-200 cursor-pointer bg-cover bg-center bg-no-repeat md:bg-contain"
	>
    </div>
</div>

<div class="grid grid-cols-2 gap-1 p-1 lg:grid-cols-5">
	{#each images as img, i}
		<div
			on:click={() => viewImage(i+1)}
			style={`background-image: url('${img.url}')`}
			class="h-96 cursor-pointer bg-cover bg-center shadow hover:brightness-90 md:h-[600px] group"
		>
        <div
				class="absolute inset-0 flex items-center justify-center bg-black/40 opacity-0 group-hover:opacity-100 transition"
			>
				<span class="text-xl font-medium text-white drop-shadow">{img.name}</span>
			</div>
        </div>
	{/each}
</div>

<div class="pt-16 pb-8 bg-slate-100 flex flex-col justify-center text-center">
  <h1 class="text-2xl md:text-4xl text-slate-700 tracking-tight font-bold">
    Imate skicu sa svadbe?
  </h1>

  <h2 class="text-xl md:text-3xl text-slate-600 py-4 flex flex-col md:flex-row justify-center items-center gap-10">
    <span class="flex flex-col items-center gap-2">
      <span class="flex items-center gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 48 48">
          <path fill="#40c351" d="M35.2,12.8c-3-3-6.9-4.6-11.2-4.6C15.3,8.2,8.2,15.3,8.2,24c0,3,0.8,5.9,2.4,8.4L11,33l-1.6,5.8
          l6-1.6l0.6,0.3c2.4,1.4,5.2,2.2,8,2.2h0c8.7,0,15.8-7.1,15.8-15.8C39.8,19.8,38.2,15.8,35.2,12.8z"></path>
          <path fill="#fff" fill-rule="evenodd"
            d="M19.3,16c-0.4-0.8-0.7-0.8-1.1-0.8c-0.3,0-0.6,0-0.9,0
            s-0.8,0.1-1.3,0.6c-0.4,0.5-1.7,1.6-1.7,4s1.7,4.6,1.9,4.9s3.3,5.3,8.1,7.2c4,1.6,4.8,1.3,5.7,1.2
            c0.9-0.1,2.8-1.1,3.2-2.3c0.4-1.1,0.4-2.1,0.3-2.3c-0.1-0.2-0.4-0.3-0.9-0.6s-2.8-1.4-3.2-1.5
            c-0.4-0.2-0.8-0.2-1.1,0.2c-0.3,0.5-1.2,1.5-1.5,1.9c-0.3,0.3-0.6,0.4-1,0.1c-0.5-0.2-2-0.7-3.8-2.4
            c-1.4-1.3-2.4-2.8-2.6-3.3c-0.3-0.5,0-0.7,0.2-1c0.2-0.2,0.5-0.6,0.7-0.8
            c0.2-0.3,0.3-0.5,0.5-0.8c0.2-0.3,0.1-0.6,0-0.8C20.6,19.3,19.7,17,19.3,16z"
            clip-rule="evenodd"></path>
        </svg>
        <a href="https://wa.me/385977967644" target="_blank" class="hover:text-green-600 transition underline">
          0977967644
        </a>
      </span>
      <span class="text-lg md:text-2xl text-slate-500 font-extrabold">Marija</span>
    </span>

    <span class="flex flex-col items-center gap-2">
      <span class="flex items-center gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 48 48">
          <path fill="#40c351" d="M35.2,12.8c-3-3-6.9-4.6-11.2-4.6C15.3,8.2,8.2,15.3,8.2,24c0,3,0.8,5.9,2.4,8.4L11,33l-1.6,5.8
          l6-1.6l0.6,0.3c2.4,1.4,5.2,2.2,8,2.2h0c8.7,0,15.8-7.1,15.8-15.8C39.8,19.8,38.2,15.8,35.2,12.8z"></path>
          <path fill="#fff" fill-rule="evenodd"
            d="M19.3,16c-0.4-0.8-0.7-0.8-1.1-0.8c-0.3,0-0.6,0-0.9,0
            s-0.8,0.1-1.3,0.6c-0.4,0.5-1.7,1.6-1.7,4s1.7,4.6,1.9,4.9s3.3,5.3,8.1,7.2c4,1.6,4.8,1.3,5.7,1.2
            c0.9-0.1,2.8-1.1,3.2-2.3c0.4-1.1,0.4-2.1,0.3-2.3c-0.1-0.2-0.4-0.3-0.9-0.6s-2.8-1.4-3.2-1.5
            c-0.4-0.2-0.8-0.2-1.1,0.2c-0.3,0.5-1.2,1.5-1.5,1.9c-0.3,0.3-0.6,0.4-1,0.1c-0.5-0.2-2-0.7-3.8-2.4
            c-1.4-1.3-2.4-2.8-2.6-3.3c-0.3-0.5,0-0.7,0.2-1c0.2-0.2,0.5-0.6,0.7-0.8
            c0.2-0.3,0.3-0.5,0.5-0.8c0.2-0.3,0.1-0.6,0-0.8C20.6,19.3,19.7,17,19.3,16z"
            clip-rule="evenodd"></path>
        </svg>
        <a href="https://wa.me/385958203771" target="_blank" class="hover:text-green-600 transition underline">
          0958203771
        </a>
      </span>
      <span class="text-lg md:text-2xl text-slate-500 font-extrabold">Valentin</span>
    </span>
  </h2>
</div>
{#if isOpen}
	<div
		class="fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm transition-all"
		on:click={closeImage}             
		on:touchstart={handleTouchStart}
		on:touchend={handleTouchEnd}
	>
		<!-- Stop click bubbling inside -->
		<div
			class="relative w-[90%] md:w-[80%] max-h-[90vh] flex justify-center"
			on:click|stopPropagation       
		>
			<img
				src={allImages[currentIndex]}
				alt="Preview"
				class="max-w-full max-h-[90vh] object-contain rounded-lg shadow-lg transition-transform duration-300"
			/>

			<!-- Close button -->
			<button
				on:click={closeImage}
				class="absolute top-2 right-2 text-white bg-black/60 hover:bg-black/80 rounded-full w-10 h-10 flex items-center justify-center text-2xl font-bold"
			>
				×
			</button>

			<!-- Arrows -->
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

