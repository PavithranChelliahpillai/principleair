<script>
	// @ts-ignore
	import Navbar from "../template/nav.svelte";
	import Navphone from "../template/navphone.svelte";
	import Footer from "../template/footer.svelte";
	// @ts-ignore
	import Countup from "svelte-countup";
	let options = { loop: true };
	let plugins = [Autoplay({ delay: 5000, stopOnInteraction: false })];
	import emblaCarouselSvelte from "embla-carousel-svelte";
	// @ts-ignore
	import Autoplay from "embla-carousel-autoplay";
	import MediaQuery from "../MediaQuery.svelte";

	import IntersectionObserver from "svelte-intersection-observer";
	import { fade, draw, fly, crossfade, blur } from "svelte/transition";
	/**
	 * @type {any}
	 */
	let elem1;
	/**
	 * @type {any}
	 */
	let elem2;
</script>

<MediaQuery query="(max-width: 1280px)" let:matches>
	{#if matches}
		<style>
			h1 {
				font-size: 5vh !important;
			}
			p {
				font-size: 3vh !important;
				padding-bottom: 1vh;
			}
			#phone {
				display: flex !important;
			}
			#phonebye {
				display: none !important;
			}
			#phone h1 {
				font-size: 3vh !important;
			}
			body {
				overflow-x: hidden !important;
			}
			#bigpad {
				padding-top: 12vh !important;
			}
			.flexbox {
				display: block !important;
			}
			#counters {
				/* display: block !important;  */
				margin-right: 7vw !important;
			}
			.dispapp h1 {
				font-size: 5vh !important;
			}
			#phone h1 {
				font-size: 5vh !important;
			}
			#bigpad {
				height: 0vh !important;
			}
		</style>
	{/if}
</MediaQuery>

<MediaQuery query="(max-width: 1200px)" let:matches>
	{#if matches}
		<style>
			#vwrap {
				margin-left: 10vw;
				display: flex;
				flex-direction: column !important;
			}
			.icp {
				margin-bottom: 4vh !important;
			}
			.embla__container {
				display: grid;
				grid-auto-flow: column;
				grid-auto-columns: 100% !important;
			}
			.embla__slide p {
				padding-left: 10vw !important;
				width: 80%;
			}
			#phone h1 {
				font-size: 5vh !important;
			}
			#bmg {
				width: 100%;
				height: auto !important;
			}
		</style>
	{/if}
</MediaQuery>

<body>
	<div id="phonebye" style="position: fixed; z-index: 5;">
		<Navbar></Navbar>
	</div>
	<div id="phone" style="position: fixed; z-index: 5;">
		<Navphone></Navphone>
	</div>
	<MediaQuery query="(max-width: 1280px)" let:matches>
		<IntersectionObserver once element={elem1} let:intersecting>
			<div
				class="flexbox"
				id="bigpad"
				style="padding-top: 7vh; height: 60vh;"
				bind:this={elem1}
			>
				{#if intersecting && !matches}
					<div
						class="box"
						style="display: flex; justify-content: center; align-items: center;"
					>
						<img
							id="bmg"
							style="height: 20vw"
							src="\principleairlogo.png"
							alt=""
							transition:blur={{ delay: 400, duration: 1000 }}
						/>
					</div>
					<div class="box" style="flex-grow: 2; border-left: none;">
						<h1
							style="font-size: 5vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin-bottom: 0;"
							transition:fade={{ duration: 600 }}
						>
							Principle Air - Serving the GTA
						</h1>
						<h1
							style="font-weight: lighter; font-size: 2vw; padding-right: 15vw;"
							transition:fade={{ delay: 200, duration: 400 }}
						>
							Our community and customers come first. No matter
							the project, our team is there for you.
						</h1>
						<div
							id="counters"
							transition:fade={{ delay: 400, duration: 500 }}
						>
							<p id="capt">
								Established in 2018, with 12 years experience in
								heating, ventilation, air conditioning,
								refrigeration and air purification. Performing
								maintenance, service, installation and sales.
								The company is driven by performance and
								customer satisfaction. We proudly serve the
								residential, commercial and industrial sectors.
							</p>
							<div id="vwrap">
								<div class="wrapper">
									<div class="ic">
										<Countup value={12} />
									</div>
									<p class="icp" style="padding: 0;">Years</p>
								</div>
								<div class="wrapper">
									<div class="ic">
										<Countup value={850} />
									</div>
									<p class="icp" style="padding: 0;">
										Projects Completed
									</p>
								</div>
								<div class="wrapper">
									<div class="ic">
										<Countup value={1000} />
										<p style="margin-left: -1vw;">+</p>
									</div>
									<p class="icp" style="padding: 0;">
										Satisfied Customers
									</p>
								</div>
							</div>
						</div>
					</div>
				{/if}
			</div>
		</IntersectionObserver>
	</MediaQuery>
	<MediaQuery query="(max-width: 1280px)" let:matches>
		{#if matches}
			<div
				class="box"
				style="display: flex; justify-content: center; align-items: center;"
			>
				<img
					id="bmg"
					style="height: 20vw"
					src="\principleairlogo.png"
					alt=""
					transition:blur={{ delay: 400, duration: 1000 }}
				/>
			</div>
			<div class="box" style="flex-grow: 2; border-left: none;">
				<h1
					style="font-size: 5vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin-bottom: 0;"
					transition:fade={{ duration: 600 }}
				>
					Principle Air - Serving the GTA
				</h1>
				<h1
					style="font-weight: lighter; font-size: 2vw; padding-right: 15vw;"
					transition:fade={{ delay: 200, duration: 400 }}
				>
					Our community and customers come first. No matter the
					project, our team is there for you.
				</h1>
				<div
					id="counters"
					transition:fade={{ delay: 400, duration: 500 }}
				>
					<p id="capt">
						Established in 2018, with 12 years experience in
						heating, ventilation, air conditioning, refrigeration
						and air purification. Performing maintenance, service,
						installation and sales. The company is driven by
						performance and customer satisfaction. We proudly serve
						the residential, commercial and industrial sectors.
					</p>
					<div id="vwrap">
						<div class="wrapper">
							<div class="ic">
								<Countup value={12} />
							</div>
							<p class="icp" style="padding: 0;">Years</p>
						</div>
						<div class="wrapper">
							<div class="ic">
								<Countup value={850} />
							</div>
							<p class="icp" style="padding: 0;">
								Projects Completed
							</p>
						</div>
						<div class="wrapper">
							<div class="ic">
								<Countup value={1000} />
								<p style="margin-left: -1vw;">+</p>
							</div>
							<p class="icp" style="padding: 0;">
								Satisfied Customers
							</p>
						</div>
					</div>
				</div>
			</div>
		{/if}
	</MediaQuery>
	<IntersectionObserver once element={elem1} let:intersecting>
		{#if intersecting}
			<div transition:fade={{ delay: 800, duration: 1000 }}>
				<div style="text-align: center;">
					<h1
						style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.2vw; margin: 6vh 0vw;"
					>
						What Customers Like About Us
					</h1>
				</div>
			</div>
		{/if}
	</IntersectionObserver>
	<IntersectionObserver once element={elem2} let:intersecting>
		<div class="flexbox" style="border-top: 1px solid rgba(255, 255, 255, 0.13);">
			{#if intersecting}
				<section
					class="dispapp"
					transition:fly={{ delay: 300, duration: 1000, x: 100 }}
				>
					<img class="discon" src="/comm.webp" alt="comm" />
					<div style="position: absolute; bottom: 0; ">
						<h1 style="margin-bottom: 1vh;">Communication</h1>
					</div>
				</section>
				<div
					class="dispapp"
					transition:fly={{ delay: 400, duration: 1000, x: 100 }}
				>
					<img class="discon" src="/effi.webp" alt="effi" />
					<div style="position: absolute; bottom: 0;">
						<h1 style="margin-bottom: 1vh;">Efficiency</h1>
					</div>
				</div>
				<div
					class="dispapp"
					transition:fly={{ delay: 500, duration: 1000, x: 100 }}
				>
					<img class="discon" src="/quality.webp" alt="quality" />
					<div style="position: absolute; bottom: 0;">
						<h1 style="margin-bottom: 1vh;">Quality</h1>
					</div>
				</div>
				<div
					class="dispapp"
					transition:fly={{ delay: 600, duration: 1000, x: 100 }}
				>
					<img class="discon" src="/fair.webp" alt="hand" />
					<div style="position: absolute; bottom: 0;">
						<h1 style="margin-bottom: 1vh;">Fair Pricing</h1>
					</div>
				</div>
			{/if}
		</div>
	</IntersectionObserver>
	<div bind:this={elem2}></div>
	<Footer></Footer>
</body>

<style>
	.discon {
		width: 25%;
		padding: 5vh;
		margin-bottom: 5vh;
		display: block;
		aspect-ratio: 1/1;
	}
	.flexbox {
		position: relative;
		display: flex;
		flex-direction: row;
		width: 100%;
	}
	.box {
		display: relative;
		flex: 1 1 0px;
		flex-grow: 1;
		border: 1px solid rgba(255, 255, 255, 0.13);
		padding: 0;
		margin: 0;
	}
	h1,
	p {
		padding-left: 1vw;
	}
	#capt {
		display: flex;
		width: 50%;
		font-size: inherit;
		font-weight: inherit;
		flex: 1 1 200px;
		flex-grow: 2;
	}
	#counters {
		display: flex;
		flex-wrap: wrap;
	}
	.icp {
		margin: none;
		font-weight: lighter;
		font-size: 1vw;
		font: inherit;
		margin-top: -5vh;
	}
	.ic {
		font-size: 5vh;
		font-weight: 800;
		letter-spacing: -0.3vw;
		display: flex;
		flex-direction: row;
		flex: 1 1 100px;
		align-items: center;
		justify-content: center;
		margin-top: -5vh;
	}
	.wrapper {
		flex: 1 1 100px;
		display: flex;
		flex-direction: column;
		text-align: center;
		align-items: center;
		width: 15vw;
	}
	.embla {
		overflow: hidden;
	}
	.embla__container {
		display: grid;
		grid-auto-flow: column;
		grid-auto-columns: 66%;
	}
	.embla__slide {
		flex: 0 0 100%;
		min-width: 0;
		border: 1px solid rgba(255, 255, 255, 0.13);
		border-top: none;
		border-left: none;
		padding: 0;
		margin: 0;
		border-bottom: none;
		padding: 3vh 0vw;
	}
	.leflex {
		border: 1px solid rgba(255, 255, 255, 0.13);
	}
	.dispapp {
		flex: 1 1 0px;
		flex-grow: 1;
		border: 1px solid rgba(255, 255, 255, 0.13);
		border-right: none;
		justify-content: center;
		display: flex;
		position: relative;
		width: 100%;
		border-top: none;
		text-align: center;
	}
	.dispapp h1 {
		padding: 0;
		padding-bottom: 3vh;
		font-weight: normal;
		line-height: 0.8;
		letter-spacing: -1px;
		margin-bottom: 0;
		font-size: 1.5vw;
		display: block;
	}
	#phone {
		display: none;
	}
	#vwrap {
		display: flex;
	}
	.icp {
		margin-bottom: 10vh;
	}
	body {
		overflow-x: hidden;
	}
</style>
