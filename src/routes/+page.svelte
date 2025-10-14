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
		'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2010.39.10.jpeg';

	const images = [
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84587.jpg',
			name: 'Tom i Mateja'
		},
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/nenadialexa.jpg',
            name: 'Nenad i Alexa'
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
			name: 'Martina, Marija i Mateja'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84583.jpg',
			name: 'Dominik i Doroteja'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2015.00.29%281%29.jpeg',
			name: 'Zorica'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2011.02.06.jpeg',
			name: 'Ruža, Jadranka i Marinka'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84582.jpg',
			name: 'Zuhair, Ruža Tamir'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b8457f.jpg',
			name: 'Anđa i Paula'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2a44f1b3ed2d35b84580.jpg',
			name: 'Mateja, Paula, Karlo i Petar'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/68de2c9af1b3ed2d35b84588.jpg',
			name: 'Ivan i Paula'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2009.51.18.jpeg',
			name: 'Monika i Dario'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2015.33.29.jpeg',
			name: 'Marko'
		},
		{
			url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-03%20at%2015.22.51.jpeg',
			name: 'Goran'
		},
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-13%20at%2011.37.10_ebbcc13c.jpg',
            name: "Goran i Iva"
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/552311961_1639172483709359_2338818531837302294_n.jpg',
            name: 'Marjana i Boro'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-06%20at%2020.40.33_748cf8ef.jpg',
            name: 'Marina i Radan'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-13%20at%2011.37.14_9905d42c.jpg',
            name: 'Megi i Iva'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-06%20at%2020.41.12_e3f5f4f3.jpg',
            name: 'Danijel i Daliborka'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-06%20at%2020.41.42_885b6d50.jpg',
            name: 'Katarina i Mario'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-06%20at%2020.42.10_80a9177e.jpg',
            name: 'Ivanka i Zoran'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-06%20at%2020.42.55_50871d64.jpg',
            name: 'Jurica i Nikolina'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-06%20at%2020.45.30_54d57946.jpg',
            name: 'Dragan, Luka, Josip, Toni, Anica, Zorica, Monika'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-06%20at%2020.46.09_33c2eca9.jpg',
            name: 'Zlatko i Manda'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-07%20at%2008.08.25_61a74843.jpg',
            name: 'Marko i Dajana'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-07%20at%2018.19.15_97111865.jpg',
            name: 'Goran'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/WhatsApp%20Image%202025-10-07%20at%2008.08.54_d28e9b5d.jpg',
            name: 'Anita'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/554572685_1526138941919637_5112352331578807298_n.jpg',
            name: 'Finka i Anto'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/554209616_1669763707744449_1079822956290112077_n.jpg',
            name: 'Ivan'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/553391542_1564680571570518_1418339339694233949_n.jpg',
            name: 'Željka i Anto'
        },
        {
            url: 'https://woop14abphufecql.public.blob.vercel-storage.com/sketches/554582834_793578006726155_178835422213847024_n.jpg',
            name: 'Ana i Kristijan'
        }
	];

	let isOpen = false;
	const allImages = [mainImageUrl, ...images.map((image) => image.url)];
	let currentIndex = 0;

	let startX = 0;
	let endX = 0;

	function handleTouchEnd(e: TouchEvent) {
		endX = e.changedTouches[0].clientX;
		const diff = startX - endX;

		if (Math.abs(diff) > 50) {
			if (diff > 0) nextImage();
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
	function viewImage(index: number) {
		currentIndex = index;
		isOpen = true;
	}

	function closeImage() {
		isOpen = false;
	}

    let touchIndex: number | null = null;
	function handleTouchStartHover(index: number) {
        touchIndex = index;
	}

	function handleTouchEndHover() {
		touchIndex = null;
	}
</script>

<div class="flex min-h-screen w-full">
	<!-- svelte-ignore a11y_click_events_have_key_events -->
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div
		on:click={() => viewImage(0)}
		style={`background-image: url('${mainImageUrl}')`}
		class="w-full cursor-pointer bg-slate-200 bg-cover bg-center bg-no-repeat md:bg-contain"
	></div>
</div>

<div class="grid grid-cols-2 gap-1 p-1 lg:grid-cols-5 bg-slate-200 font-roboto">
	{#each images as img, i}
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			on:click={() => viewImage(i + 1)}
            on:touchstart={() => handleTouchStartHover(i)}
            on:touchend={handleTouchEndHover}
			style={`background-image: url('${img.url}')`}
			class="relative group h-96 cursor-pointer bg-cover bg-center hover:brightness-90 md:h-[600px]"
		>
			<div
class={`absolute inset-0 flex items-center justify-center bg-black/40 transition ${
					touchIndex === i ? 'opacity-100' : 'opacity-0 group-hover:opacity-100'
				}`}
			>
				<span class="text-xl font-medium text-white drop-shadow px-2 text-center">{img.name}</span>
			</div>
		</div>
	{/each}
</div>

<div class="flex flex-col justify-center bg-slate-200 pt-16 pb-8 text-center font-roboto">
	<h1 class="text-2xl font-bold tracking-tight text-slate-700 md:text-4xl">
		Imate skicu sa svadbe? Pošaljite nam!
	</h1>

	<h2
		class="flex flex-col items-center justify-center gap-10 py-4 text-xl text-slate-600 md:flex-row md:text-3xl"
	>
		<span class="flex flex-col items-center gap-2">
			<span class="flex items-center gap-2">
				<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 48 48">
					<path
						fill="#40c351"
						d="M35.2,12.8c-3-3-6.9-4.6-11.2-4.6C15.3,8.2,8.2,15.3,8.2,24c0,3,0.8,5.9,2.4,8.4L11,33l-1.6,5.8
          l6-1.6l0.6,0.3c2.4,1.4,5.2,2.2,8,2.2h0c8.7,0,15.8-7.1,15.8-15.8C39.8,19.8,38.2,15.8,35.2,12.8z"
					></path>
					<path
						fill="#fff"
						fill-rule="evenodd"
						d="M19.3,16c-0.4-0.8-0.7-0.8-1.1-0.8c-0.3,0-0.6,0-0.9,0
            s-0.8,0.1-1.3,0.6c-0.4,0.5-1.7,1.6-1.7,4s1.7,4.6,1.9,4.9s3.3,5.3,8.1,7.2c4,1.6,4.8,1.3,5.7,1.2
            c0.9-0.1,2.8-1.1,3.2-2.3c0.4-1.1,0.4-2.1,0.3-2.3c-0.1-0.2-0.4-0.3-0.9-0.6s-2.8-1.4-3.2-1.5
            c-0.4-0.2-0.8-0.2-1.1,0.2c-0.3,0.5-1.2,1.5-1.5,1.9c-0.3,0.3-0.6,0.4-1,0.1c-0.5-0.2-2-0.7-3.8-2.4
            c-1.4-1.3-2.4-2.8-2.6-3.3c-0.3-0.5,0-0.7,0.2-1c0.2-0.2,0.5-0.6,0.7-0.8
            c0.2-0.3,0.3-0.5,0.5-0.8c0.2-0.3,0.1-0.6,0-0.8C20.6,19.3,19.7,17,19.3,16z"
						clip-rule="evenodd"
					></path>
				</svg>
				<a
					href="https://wa.me/385977967644"
					target="_blank"
					class="underline transition hover:text-green-600"
				>
					0977967644
				</a>
			</span>
			<span class="text-lg font-extrabold text-slate-500 md:text-2xl">Marija</span>
		</span>

		<span class="flex flex-col items-center gap-2">
			<span class="flex items-center gap-2">
				<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 48 48">
					<path
						fill="#40c351"
						d="M35.2,12.8c-3-3-6.9-4.6-11.2-4.6C15.3,8.2,8.2,15.3,8.2,24c0,3,0.8,5.9,2.4,8.4L11,33l-1.6,5.8
          l6-1.6l0.6,0.3c2.4,1.4,5.2,2.2,8,2.2h0c8.7,0,15.8-7.1,15.8-15.8C39.8,19.8,38.2,15.8,35.2,12.8z"
					></path>
					<path
						fill="#fff"
						fill-rule="evenodd"
						d="M19.3,16c-0.4-0.8-0.7-0.8-1.1-0.8c-0.3,0-0.6,0-0.9,0
            s-0.8,0.1-1.3,0.6c-0.4,0.5-1.7,1.6-1.7,4s1.7,4.6,1.9,4.9s3.3,5.3,8.1,7.2c4,1.6,4.8,1.3,5.7,1.2
            c0.9-0.1,2.8-1.1,3.2-2.3c0.4-1.1,0.4-2.1,0.3-2.3c-0.1-0.2-0.4-0.3-0.9-0.6s-2.8-1.4-3.2-1.5
            c-0.4-0.2-0.8-0.2-1.1,0.2c-0.3,0.5-1.2,1.5-1.5,1.9c-0.3,0.3-0.6,0.4-1,0.1c-0.5-0.2-2-0.7-3.8-2.4
            c-1.4-1.3-2.4-2.8-2.6-3.3c-0.3-0.5,0-0.7,0.2-1c0.2-0.2,0.5-0.6,0.7-0.8
            c0.2-0.3,0.3-0.5,0.5-0.8c0.2-0.3,0.1-0.6,0-0.8C20.6,19.3,19.7,17,19.3,16z"
						clip-rule="evenodd"
					></path>
				</svg>
				<a
					href="https://wa.me/385958203771"
					target="_blank"
					class="underline transition hover:text-green-600"
				>
					0958203771
				</a>
			</span>
			<span class="text-lg font-extrabold text-slate-500 md:text-2xl">Valentin</span>
		</span>
	</h2>
</div>
{#if isOpen}
<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<div
  class="fixed inset-0 z-50 flex flex-col items-center justify-center bg-black/80 backdrop-blur-sm transition-all"
  on:click={closeImage}
  on:touchstart={handleTouchStart}
  on:touchend={handleTouchEnd}
>
  <div
    class="relative flex max-h-[90vh] w-[90%] flex-col items-center justify-center md:w-[80%]"
    on:click|stopPropagation
  >
    <!-- Image -->
    <img
      src={allImages[currentIndex]}
      alt="Preview"
      class="max-h-[80vh] max-w-full rounded-lg object-contain shadow-lg transition-transform duration-300"
    />

    <!-- Image name -->
    <p class="mt-4 text-center text-lg font-medium text-white drop-shadow-lg">
      {#if currentIndex === 0}
        Valentin i Marija
      {:else}
        {images[currentIndex - 1].name}
      {/if}
    </p>

    <!-- Close button -->
    <button
      type="button"
      aria-label="Close preview"
      on:click={closeImage}
      class="fixed top-6 right-6 z-50 flex h-10 w-10 items-center justify-center rounded-full bg-black/60 text-white hover:bg-black/80"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="#FFFFFF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <line x1="18" y1="6" x2="6" y2="18" />
        <line x1="6" y1="6" x2="18" y2="18" />
      </svg>
    </button>

    <!-- Prev arrow -->
    <button
      type="button"
      aria-label="Previous image"
      on:click={prevImage}
      class="absolute left-3 top-1/2 z-40 flex h-10 w-10 -translate-y-1/2 items-center justify-center rounded-full bg-black/50 hover:bg-black/70"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="#FFFFFF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M15 18l-6-6 6-6" />
      </svg>
    </button>

    <!-- Next arrow -->
    <button
      type="button"
      aria-label="Next image"
      on:click={nextImage}
      class="absolute right-3 top-1/2 z-40 flex h-10 w-10 -translate-y-1/2 items-center justify-center rounded-full bg-black/50 hover:bg-black/70"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 24 24" fill="none" stroke="#FFFFFF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M9 6l6 6-6 6" />
      </svg>
    </button>
  </div>
</div>
{/if}
